+++
title = "soap"
template = "agent.html"
path = "soap"

[extra]
name = "soap"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-soap"
binary_name = "zentinel-soap-agent"
description = "SOAP-specific security controls including envelope validation, WS-Security verification, operation control, and XXE prevention."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "api-security"
tags = ["security", "soap", "xml", "api"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "API security agents"
language = "Rust"
+++

## Overview

The soap agent provides security controls designed for SOAP/XML web services. Validate SOAP envelopes, verify WS-Security tokens, control operation access, and prevent XXE attacks.

## Key Features

- **Envelope Validation** — Validate SOAP envelope structure and schema compliance
- **WS-Security** — Verify WS-Security headers, tokens, and signatures
- **Operation Control** — Allow or deny specific SOAP operations
- **XXE Prevention** — Block XML External Entity attacks in SOAP payloads
