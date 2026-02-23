+++
title = "denylist"
template = "agent.html"
path = "denylist"

[extra]
name = "denylist"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-denylist"
binary_name = "zentinel-denylist-agent"
description = "Block requests based on IP addresses, CIDR ranges, or custom patterns with real-time updates."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "core"
tags = ["security", "filtering", "core"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Core agents"
language = "Rust"
+++

## Overview

The denylist agent blocks requests based on IP addresses, CIDR ranges, or custom patterns. Lists can be updated in real-time without restarting Zentinel.

## Key Features

- **IP Blocking** — Block individual IPs or CIDR ranges
- **Pattern Matching** — Block requests matching custom URI or header patterns
- **Real-Time Updates** — Hot-reload blocklists without downtime
- **Multiple Sources** — Load from files, HTTP endpoints, or inline configuration
