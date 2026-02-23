+++
title = "graphql-security"
template = "agent.html"
path = "graphql-security"

[extra]
name = "graphql-security"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-graphql-security"
binary_name = "zentinel-graphql-security-agent"
description = "GraphQL-specific security controls including query depth limiting, complexity analysis, introspection control, and field-level authorization."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "api-security"
tags = ["security", "graphql", "api"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "API security agents"
language = "Rust"
+++

## Overview

The graphql-security agent provides comprehensive security controls designed specifically for GraphQL APIs. Prevent abuse through query depth limiting, complexity analysis, and introspection control.

## Key Features

- **Query Depth Limiting** — Prevent deeply nested queries that could overwhelm your resolvers
- **Complexity Analysis** — Assign costs to fields and reject queries exceeding thresholds
- **Introspection Control** — Disable or restrict introspection queries in production
- **Field Authorization** — Control access to sensitive fields based on request context
