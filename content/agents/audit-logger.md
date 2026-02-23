+++
title = "audit-logger"
template = "agent.html"
path = "audit-logger"

[extra]
name = "audit-logger"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-audit-logger"
binary_name = "zentinel-audit-logger-agent"
description = "Structured audit logging agent with PII redaction, multiple formats (JSON, CEF, LEEF), and compliance templates for SOC2, HIPAA, PCI, and GDPR."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "utility"
tags = ["logging", "compliance", "security", "audit"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Utility agents"
language = "Rust"
+++

## Overview

The audit-logger agent provides structured, compliance-ready audit logging for all traffic passing through Zentinel. It automatically redacts PII, supports multiple output formats, and includes pre-built templates for common compliance frameworks.

## Key Features

- **Multiple Output Formats** — JSON, CEF (Common Event Format), LEEF (Log Event Extended Format)
- **PII Redaction** — Automatically detects and redacts sensitive data like credit cards, SSNs, and email addresses
- **Compliance Templates** — Pre-configured logging templates for SOC2, HIPAA, PCI-DSS, and GDPR
- **Structured Logging** — Every log entry includes request metadata, timing, and configurable fields
