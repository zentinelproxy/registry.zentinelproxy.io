+++
title = "grpc-inspector"
template = "agent.html"
path = "grpc-inspector"

[extra]
name = "grpc-inspector"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-grpc-inspector"
binary_name = "zentinel-grpc-inspector-agent"
description = "Comprehensive security controls for gRPC services: method authorization, rate limiting, metadata inspection, and reflection control."
author = "Zentinel Core Team"
license = "MIT"
status = "stable"
category = "api-security"
tags = ["grpc", "security", "authorization", "rate-limiting"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "API security agents"
language = "Rust"
+++

## Overview

The grpc-inspector agent provides security controls tailored for gRPC services. Authorize methods, inspect metadata, control reflection, and apply rate limits at the gRPC layer.

## Key Features

- **Method Authorization** — Allow or deny specific gRPC methods based on metadata
- **Rate Limiting** — Per-method rate limiting for gRPC calls
- **Metadata Inspection** — Inspect and validate gRPC metadata headers
- **Reflection Control** — Enable or disable gRPC server reflection per environment
