+++
title = "Image Optimization"
weight = 95
template = "agent.html"
path = "image-optimization"
description = "On-the-fly JPEG/PNG to WebP/AVIF conversion with content negotiation, filesystem caching, and graceful fallback."

[extra]
name = "image-optimization"
version = "0.2.0"
repository = "zentinelproxy/zentinel-agent-image-optimization"
binary_name = "zentinel-image-optimization-agent"
description = "On-the-fly JPEG/PNG to WebP/AVIF conversion with content negotiation, filesystem caching, and graceful fallback."
author = "Zentinel Core Team"
license = "MIT/Apache-2.0"
status = "stable"
category = "utility"
tags = ["image", "optimization", "webp", "avif", "caching", "performance"]
min_zentinel_version = "26.01.0"
official = true
author_url = "https://github.com/zentinelproxy"
homepage = "https://zentinelproxy.io/agents/image-optimization/"
crate_name = "zentinel-agent-image-optimization"
bundle_included = true
bundle_group = "Utility agents"
language = "Rust"
+++

## Overview

An image optimization agent for Zentinel that converts JPEG/PNG responses to WebP/AVIF on the fly. Negotiates the best format from the client's `Accept` header, converts images via `spawn_blocking`, and caches results in a content-addressable filesystem store. Falls back to the original image on any error — the agent never makes a response worse.

## Features

- **Format Negotiation**: Parses `Accept` header quality values (RFC 7231) to pick WebP or AVIF
- **WebP Conversion**: Lossless VP8L encoding via the `image` crate
- **AVIF Conversion**: Lossy encoding with configurable quality via `ravif`
- **Filesystem Cache**: Content-addressable, two-level directory sharding, LRU eviction, configurable TTL
- **Passthrough Patterns**: Regex-based URL exclusions (e.g. skip `.gif`, `.svg`)
- **Size Guards**: Max input bytes and max pixel count to avoid OOM on huge images
- **Graceful Degradation**: Decode errors, encode failures, oversized images, and unsupported clients all pass through the original

## Installation

### Using Bundle (Recommended)

The easiest way to install this agent is via the Zentinel bundle command:

```bash
zentinel bundle install image-optimization
```

The bundle command automatically downloads the correct binary for your platform and places it in `~/.zentinel/agents/`.

### From Source

```bash
cargo install zentinel-agent-image-optimization
```

Or build manually:

```bash
git clone https://github.com/zentinelproxy/zentinel-agent-image-optimization
cd zentinel-agent-image-optimization
cargo build --release
```

## Configuration

### Command Line

```bash
zentinel-image-optimization-agent \
    --socket /tmp/image-optimization-agent.sock \
    --log-level info \
    --config /etc/zentinel/image-optimization.json
```

### CLI Options

| Option | Env Var | Description | Default |
|--------|---------|-------------|---------|
| `--socket` | `IMAGE_OPT_SOCKET` | Unix socket path | `/tmp/image-optimization-agent.sock` |
| `--grpc` | `IMAGE_OPT_GRPC` | gRPC listen address | — |
| `--config` | `IMAGE_OPT_CONFIG` | Configuration file (JSON) | — |
| `--log-level` | `IMAGE_OPT_LOG_LEVEL` | Log level | `info` |

### Zentinel Configuration

```kdl
agents {
    agent "image-optimization" type="custom" {
        unix-socket "/tmp/image-optimization-agent.sock"
        events "request_headers" "response_headers" "response_body" "request_complete"
        timeout-ms 5000
        failure-mode "open"
        response-body-mode "buffer"
        max-response-body-bytes 10485760

        config {
            formats "webp" "avif"
            quality {
                webp 80
                avif 70
            }
            max_input_size_bytes 10485760
            max_pixel_count 25000000
            eligible_content_types "image/jpeg" "image/png"
            passthrough_patterns "\\.gif$" "\\.svg$"
            cache {
                enabled #true
                directory "/var/cache/zentinel/image-optimization"
                max_size_bytes 1073741824
                ttl_secs 86400
            }
        }
    }
}

filters {
    filter "image-optimization" {
        type "agent"
        agent "image-optimization"
        timeout-ms 5000
        failure-mode "open"
    }
}

routes {
    route "images" {
        matches { path-prefix "/" }
        upstream "backend"
        filters "image-optimization"
    }
}
```

### Agent Configuration (JSON)

```json
{
  "formats": ["webp", "avif"],
  "quality": { "webp": 80, "avif": 70 },
  "max_input_size_bytes": 10485760,
  "max_pixel_count": 25000000,
  "eligible_content_types": ["image/jpeg", "image/png"],
  "passthrough_patterns": ["\\.gif$", "\\.svg$"],
  "cache": {
    "enabled": true,
    "directory": "/var/cache/zentinel/image-optimization",
    "max_size_bytes": 1073741824,
    "ttl_secs": 86400
  }
}
```

### Options

| Field | Default | Description |
|-------|---------|-------------|
| `formats` | `["webp", "avif"]` | Output formats in priority order |
| `quality.webp` | `80` | WebP quality (1–100) |
| `quality.avif` | `70` | AVIF quality (1–100) |
| `max_input_size_bytes` | `10485760` (10 MB) | Skip images larger than this |
| `max_pixel_count` | `25000000` (25 MP) | Skip images with more pixels than this |
| `eligible_content_types` | `["image/jpeg", "image/png"]` | Response content types to optimize |
| `passthrough_patterns` | `[]` | Regex patterns for URLs to skip |
| `cache.enabled` | `true` | Enable filesystem cache |
| `cache.directory` | `/var/cache/zentinel/image-optimization` | Cache root directory |
| `cache.max_size_bytes` | `1073741824` (1 GB) | Max total cache size (LRU eviction) |
| `cache.ttl_secs` | `86400` (24 h) | Time-to-live for cached entries |

## How It Works

```
Client                  Zentinel Proxy              Image Optimization Agent
  │                         │                               │
  │  GET /photo.jpg         │                               │
  │  Accept: image/webp     │                               │
  │────────────────────────►│  request_headers              │
  │                         │──────────────────────────────►│
  │                         │  (extract Accept + URI,       │
  │                         │   store per-request state)    │
  │                         │◄──────────────────────────────│
  │                         │                               │
  │                         │  (forward to upstream)        │
  │                         │                               │
  │                         │  response_headers             │
  │                         │──────────────────────────────►│
  │                         │  (check content-type,         │
  │                         │   negotiate format,           │
  │                         │   set Vary, request body)     │
  │                         │◄──────────────────────────────│
  │                         │                               │
  │                         │  response_body (chunks)       │
  │                         │──────────────────────────────►│
  │                         │  (buffer → convert → cache)   │
  │                         │◄──────────────────────────────│
  │                         │                               │
  │  200 OK                 │                               │
  │  Content-Type: image/webp                               │
  │  X-Image-Optimized: webp                                │
  │  Vary: Accept                                           │
  │◄────────────────────────│                               │
```

`Vary: Accept` is set during the `response_headers` phase. `Content-Type` and `X-Image-Optimized` are set during the `response_body` phase after conversion succeeds. On conversion failure, the original `Content-Type` is preserved so clients always receive correctly-typed content.

## Response Headers

On successful conversion, the agent sets these headers:

| Header | Value | Description |
|--------|-------|-------------|
| `Content-Type` | `image/webp` or `image/avif` | The optimized format |
| `Content-Length` | `<bytes>` | Optimized image size |
| `Vary` | `Accept` | Downstream caches vary by format |
| `X-Image-Optimized` | `webp`, `avif`, or `cache-hit` | Which format was served |
| `X-Image-Original-Size` | `<bytes>` | Original image size before conversion |

## Failure Modes

All failures result in pass-through of the original image:

| Scenario | Behavior |
|----------|----------|
| Corrupt image / decode error | Pass through original |
| Encode failure | Pass through original |
| Image too large (bytes or pixels) | Pass through original, skip processing |
| Client doesn't support WebP/AVIF | Pass through original (no conversion) |
| Cache write failure | Serve converted image, log error |
| Cache read failure | Treat as miss, convert normally |
| Config parse error | Reject config with 500 (operator error) |

The proxy-level `failure-mode "open"` setting ensures that if the agent process crashes or times out, the original response passes through unmodified.

## Cache Layout

The filesystem cache uses content-addressable storage with two-level directory sharding:

```
/var/cache/zentinel/image-optimization/
├── a3/
│   └── 7f/
│       ├── a37f...c4e2.bin          # Optimized image bytes
│       └── a37f...c4e2.meta.json    # Metadata sidecar
└── b1/
    └── 02/
        ├── b102...9af1.bin
        └── b102...9af1.meta.json
```

Cache keys are SHA-256 hashes of `"{uri}:{format}:{quality}"`.

## Performance

- **Latency**: Depends on image size; cached responses <1ms
- **Memory**: ~30MB base + buffered image size
- **Cache hit ratio**: Typically >90% for static assets

## Related Agents

| Agent | Integration |
|-------|-------------|
| **Transform** | Rewrite image URLs before optimization |
| **WAF** | Scan uploads before processing |
| **Rate Limit** | Throttle conversion-heavy requests |
