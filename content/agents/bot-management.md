+++
title = "bot-management"
template = "agent.html"
path = "bot-management"

[extra]
name = "bot-management"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-bot-management"
binary_name = "zentinel-bot-management-agent"
description = "Comprehensive bot detection with multi-signal analysis, known bot verification, and behavioral tracking."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "bot-detection", "core"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Security agents"
language = "Rust"
+++

## Overview

The bot-management agent detects and manages bot traffic using multi-signal analysis. It verifies known bots (Googlebot, Bingbot, etc.) through reverse DNS, identifies malicious bots via behavioral patterns, and provides granular control over bot access.

## Key Features

- **Multi-Signal Analysis** — Combines user agent, IP reputation, TLS fingerprint, and behavioral signals
- **Known Bot Verification** — Reverse DNS verification for legitimate search engine crawlers
- **Behavioral Tracking** — Detects anomalous request patterns indicative of scraping or credential stuffing
- **Granular Control** — Allow, block, rate-limit, or challenge bots based on classification
