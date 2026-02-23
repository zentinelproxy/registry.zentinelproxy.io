+++
title = "ip-reputation"
template = "agent.html"
path = "ip-reputation"

[extra]
name = "ip-reputation"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-ip-reputation"
binary_name = "zentinel-ip-reputation-agent"
description = "IP threat intelligence with AbuseIPDB integration, file-based blocklists, and Tor exit node detection."
author = "Zentinel Core Team"
license = "MIT"
status = "stable"
category = "security"
tags = ["ip-reputation", "threat-intelligence", "security", "blocklist", "tor"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Security agents"
language = "Rust"
+++

## Overview

The ip-reputation agent enriches requests with threat intelligence from IP reputation sources. Automatically block or flag traffic from known malicious IPs, Tor exit nodes, and abuse-reported addresses.

## Key Features

- **AbuseIPDB Integration** — Real-time IP reputation lookups against the AbuseIPDB database
- **File-Based Blocklists** — Load and auto-refresh IP blocklists from files or URLs
- **Tor Exit Node Detection** — Identify and optionally block traffic from Tor exit nodes
- **Reputation Scoring** — Assign risk scores to requests based on IP intelligence
