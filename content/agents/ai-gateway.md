+++
title = "ai-gateway"
template = "agent.html"
path = "ai-gateway"

[extra]
name = "ai-gateway"
version = "0.2.0"
repository = "zentinelproxy/zentinel-agent-ai-gateway"
binary_name = "zentinel-ai-gateway-agent"
description = "AI/LLM gateway agent with provider routing, token rate limiting, prompt inspection, and cost tracking for OpenAI, Anthropic, and other LLM APIs."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "api-security"
tags = ["ai", "llm", "gateway", "openai", "anthropic", "rate-limiting"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = false
language = "Rust"
+++

## Overview

The ai-gateway agent provides a unified gateway for AI and LLM API traffic. Route requests across providers, enforce token-based rate limits, inspect prompts for sensitive data, and track costs across your organization.

## Key Features

- **Provider Routing** — Route to OpenAI, Anthropic, and other LLM providers with automatic failover
- **Token Rate Limiting** — Rate limit based on token count, not just request count
- **Prompt Inspection** — Detect and block PII, secrets, or prohibited content in prompts
- **Cost Tracking** — Track API spend per team, project, or user with real-time dashboards
