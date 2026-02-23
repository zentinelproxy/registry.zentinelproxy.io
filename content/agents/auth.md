+++
title = "auth"
template = "agent.html"
path = "auth"

[extra]
name = "auth"
version = "0.2.0"
repository = "zentinelproxy/zentinel-agent-auth"
binary_name = "zentinel-auth-agent"
description = "Authentication and authorization agent supporting JWT validation, OAuth 2.0 token introspection, API key management, and RBAC policies."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "identity"
tags = ["auth", "jwt", "oauth", "rbac", "api-key", "identity"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = false
language = "Rust"
+++

## Overview

The auth agent provides comprehensive authentication and authorization for your services. Validate JWTs, introspect OAuth 2.0 tokens, manage API keys, and enforce role-based access control at the proxy layer.

## Key Features

- **JWT Validation** — Validate JWT tokens with configurable JWKS endpoint support
- **OAuth 2.0 Introspection** — Token introspection against any RFC 7662 compliant provider
- **API Key Management** — Authenticate requests using API keys in headers, query params, or cookies
- **RBAC Policies** — Define role-based access control policies for fine-grained authorization
