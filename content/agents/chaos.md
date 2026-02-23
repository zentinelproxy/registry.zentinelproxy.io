+++
title = "chaos"
template = "agent.html"
path = "chaos"

[extra]
name = "chaos"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-chaos"
binary_name = "zentinel-chaos-agent"
description = "Controlled fault injection for resilience testing: latency, errors, timeouts, and more with flexible targeting and safety controls."
author = "Zentinel Core Team"
license = "MIT"
status = "stable"
category = "utility"
tags = ["chaos", "testing", "resilience", "fault-injection"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Utility agents"
language = "Rust"
+++

## Overview

The chaos agent enables controlled fault injection for resilience testing in staging and production environments. Inject latency, errors, timeouts, and connection failures to validate your system's behavior under adverse conditions.

## Key Features

- **Latency Injection** — Add configurable delays to requests and responses
- **Error Injection** — Return specific HTTP error codes at a controlled rate
- **Timeout Simulation** — Simulate upstream timeouts and connection failures
- **Safety Controls** — Rate limits, kill switches, and scope targeting to prevent unintended impact
