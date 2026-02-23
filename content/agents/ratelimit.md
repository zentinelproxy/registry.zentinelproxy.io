+++
title = "ratelimit"
template = "agent.html"
path = "ratelimit"

[extra]
name = "ratelimit"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-ratelimit"
binary_name = "zentinel-ratelimit-agent"
description = "Token bucket rate limiting with configurable windows and limits per route, IP, or custom keys."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "deprecated"
category = "core"
tags = ["security", "traffic", "deprecated"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Core agents"
language = "Rust"
+++

## Overview

The ratelimit agent provides token bucket rate limiting with configurable windows. Rate limit by route, client IP, API key, or custom header values. **This agent is deprecated** — rate limiting is now built into Zentinel core.

## Key Features

- **Token Bucket Algorithm** — Smooth rate limiting with burst capacity
- **Flexible Keys** — Rate limit by IP, route, header value, or custom expressions
- **Configurable Windows** — Set rate limits per second, minute, hour, or custom intervals
- **Response Headers** — Adds standard `RateLimit-*` headers to responses
