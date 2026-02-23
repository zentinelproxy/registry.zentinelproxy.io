+++
title = "modsec"
template = "agent.html"
path = "modsec"

[extra]
name = "modsec"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-modsec"
binary_name = "zentinel-modsec-agent"
description = "Full OWASP Core Rule Set (CRS) support via libmodsecurity with 800+ detection rules."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "waf", "modsecurity", "owasp", "crs"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Security agents"
language = "Rust"
+++

## Overview

The modsec agent integrates libmodsecurity to provide full OWASP Core Rule Set (CRS) support. Over 800 detection rules protect against SQL injection, XSS, command injection, and more.

## Key Features

- **OWASP CRS Support** — Full compatibility with the OWASP Core Rule Set v4
- **800+ Rules** — Comprehensive detection for SQL injection, XSS, RCE, LFI, and more
- **Anomaly Scoring** — Configurable scoring thresholds for detection sensitivity
- **Custom Rules** — Write and load custom ModSecurity rules alongside the CRS
