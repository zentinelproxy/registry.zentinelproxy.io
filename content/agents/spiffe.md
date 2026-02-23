+++
title = "spiffe"
template = "agent.html"
path = "spiffe"

[extra]
name = "spiffe"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-spiffe"
binary_name = "zentinel-spiffe-agent"
description = "SPIFFE/SPIRE workload identity authentication agent for zero-trust service-to-service communication."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "identity"
tags = ["security", "auth", "zero-trust", "spiffe", "mtls", "identity"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Identity agents"
language = "Rust"
+++

## Overview

The spiffe agent implements SPIFFE/SPIRE workload identity for zero-trust service-to-service communication. Authenticate workloads using SPIFFE IDs and mTLS without managing certificates manually.

## Key Features

- **SPIFFE ID Verification** — Authenticate services using their SPIFFE identity
- **SPIRE Integration** — Connect to SPIRE agents for automatic SVID rotation
- **mTLS Enforcement** — Require mutual TLS with SPIFFE-based identities
- **Policy Enforcement** — Allow or deny traffic based on SPIFFE ID patterns
