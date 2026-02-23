+++
title = "zentinelsec"
template = "agent.html"
path = "zentinelsec"

[extra]
name = "zentinelsec"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-zentinelsec"
binary_name = "zentinel-zentinelsec-agent"
description = "Pure Rust ModSecurity-compatible WAF with full OWASP CRS support - no C dependencies required."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "waf", "modsecurity", "owasp", "crs", "pure-rust"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Security agents"
language = "Rust"
+++

## Overview

The zentinelsec agent is a pure Rust reimplementation of ModSecurity with full OWASP Core Rule Set compatibility. Unlike the modsec agent, it requires no C dependencies — making it easier to deploy and more secure by default.

## Key Features

- **Pure Rust** — No C dependencies or libmodsecurity required
- **Full CRS Compatibility** — Supports the complete OWASP Core Rule Set v4
- **ModSecurity Rule Language** — Parse and execute standard ModSecurity rules
- **Cross-Platform** — Compiles natively on all platforms Zentinel supports
