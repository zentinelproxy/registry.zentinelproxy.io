+++
title = "policy"
template = "agent.html"
path = "policy"

[extra]
name = "policy"
version = "0.1.0"
repository = "zentinelproxy/zentinel-agent-policy"
binary_name = "zentinel-policy-agent"
description = "Policy engine agent with a Haskell-based DSL for expressing complex access control, routing, and transformation policies."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "beta"
category = "identity"
tags = ["policy", "access-control", "haskell", "dsl", "authorization"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = false
language = "Haskell"
+++

## Overview

The policy agent provides a powerful policy engine with a Haskell-based DSL for expressing complex access control rules. Define fine-grained policies that combine request attributes, external data sources, and custom logic.

## Key Features

- **Haskell DSL** — Expressive, type-safe policy language for complex rules
- **Composable Policies** — Combine and layer policies with logical operators
- **External Data Sources** — Query databases, APIs, or caches during policy evaluation
- **Audit Trail** — Every policy decision is logged with full context for compliance
