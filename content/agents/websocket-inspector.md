+++
title = "websocket-inspector"
template = "agent.html"
path = "websocket-inspector"

[extra]
name = "websocket-inspector"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-websocket-inspector"
binary_name = "zentinel-websocket-inspector-agent"
description = "Security analysis for WebSocket frames: content filtering, schema validation, and attack detection for real-time connections."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "protocol"
tags = ["websocket", "security", "real-time", "inspection"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Protocol agents"
language = "Rust"
+++

## Overview

The websocket-inspector agent provides security analysis for WebSocket connections. Inspect frames for malicious content, validate payloads against schemas, and detect attacks on real-time communication channels.

## Key Features

- **Frame Inspection** — Analyze WebSocket text and binary frames for malicious content
- **Schema Validation** — Validate message payloads against JSON Schema definitions
- **Attack Detection** — Detect injection attacks, oversized frames, and protocol abuse
- **Content Filtering** — Filter or transform WebSocket messages based on configurable rules
