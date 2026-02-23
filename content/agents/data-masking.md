+++
title = "data-masking"
template = "agent.html"
path = "data-masking"

[extra]
name = "data-masking"
version = "0.5.4"
repository = "zentinelproxy/zentinel"
binary_name = "zentinel-data-masking-agent"
description = "Real-time data masking and tokenization for PII, credentials, and sensitive fields in request and response bodies."
author = "Zentinel Core Team"
license = "MIT/Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "privacy", "pii", "masking", "tokenization", "gdpr"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = false
language = "Rust"
+++

## Overview

The data-masking agent provides real-time masking and tokenization of sensitive data in HTTP traffic. Automatically detect and redact PII, credentials, and other sensitive fields before they reach your logging, analytics, or third-party services.

## Key Features

- **Automatic PII Detection** — Detect credit card numbers, SSNs, emails, phone numbers, and more
- **Configurable Masking** — Choose from full redaction, partial masking, or tokenization
- **JSON Path Targeting** — Mask specific fields in JSON request and response bodies
- **GDPR Compliance** — Help meet data protection requirements by preventing PII leakage
