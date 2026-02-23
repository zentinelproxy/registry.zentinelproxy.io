+++
title = "mock-server"
template = "agent.html"
path = "mock-server"

[extra]
name = "mock-server"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-mock-server"
binary_name = "zentinel-mock-server-agent"
description = "A mock server agent that intercepts requests and returns configurable stub responses with support for templating, latency simulation, and fault injection."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "utility"
tags = ["mock", "testing", "development", "stubs", "api"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Utility agents"
language = "Rust"
+++

## Overview

The mock-server agent intercepts requests and returns configurable stub responses, making it ideal for development, testing, and API prototyping. Supports response templating, latency simulation, and fault injection.

## Key Features

- **Configurable Stubs** — Define responses for specific routes with status codes, headers, and bodies
- **Response Templating** — Use templates to generate dynamic responses based on request data
- **Latency Simulation** — Add realistic delays to mock responses
- **Fault Injection** — Simulate errors and timeouts for resilience testing
