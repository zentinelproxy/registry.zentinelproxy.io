+++
title = "waf"
template = "agent.html"
path = "waf"

[extra]
name = "waf"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-waf"
binary_name = "zentinel-waf-agent"
description = "Pure Rust WAF with 285 detection rules, anomaly scoring, and API security."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "waf", "core", "api-security"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Core agents"
language = "Rust"
+++

## Overview

The waf agent is a pure Rust Web Application Firewall with 285 built-in detection rules. It provides anomaly scoring, API security features, and zero C dependencies for maximum portability and security.

## Key Features

- **285 Detection Rules** — Comprehensive coverage for SQL injection, XSS, RCE, LFI, and more
- **Anomaly Scoring** — Configurable scoring thresholds with per-rule weights
- **API Security** — JSON/XML body inspection, content-type enforcement, and parameter validation
- **Zero C Dependencies** — Pure Rust implementation with no libmodsecurity dependency
