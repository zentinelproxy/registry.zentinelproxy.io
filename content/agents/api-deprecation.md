+++
title = "api-deprecation"
template = "agent.html"
path = "api-deprecation"

[extra]
name = "api-deprecation"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-api-deprecation"
binary_name = "zentinel-api-deprecation-agent"
description = "API lifecycle management agent with RFC 8594 Sunset headers, usage tracking, automatic redirects, and migration support for graceful API deprecation."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "api-security"
tags = ["api", "deprecation", "lifecycle", "sunset", "migration"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "API security agents"
language = "Rust"
+++

## Overview

The api-deprecation agent manages the lifecycle of your API endpoints. When you need to sunset an API version, this agent handles the transition gracefully by adding RFC 8594 Sunset headers, tracking usage of deprecated endpoints, and automatically redirecting clients to newer versions.

## Key Features

- **RFC 8594 Sunset Headers** — Automatically adds `Sunset` and `Deprecation` headers to responses from deprecated endpoints
- **Usage Tracking** — Monitors traffic to deprecated endpoints so you know when it's safe to remove them
- **Automatic Redirects** — Configurable redirects from old endpoints to their replacements
- **Migration Support** — Provides migration hints in response headers to guide API consumers
