+++
title = "mqtt-gateway"
template = "agent.html"
path = "mqtt-gateway"

[extra]
name = "mqtt-gateway"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-mqtt-gateway"
binary_name = "zentinel-mqtt-gateway-agent"
description = "IoT protocol security for MQTT: topic-based ACLs, client authentication, payload inspection, rate limiting, and QoS enforcement."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "protocol"
tags = ["mqtt", "iot", "security", "authentication", "acl", "rate-limiting"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Protocol agents"
language = "Rust"
+++

## Overview

The mqtt-gateway agent provides security controls for MQTT traffic, making it ideal for IoT deployments. Enforce topic-based access control, authenticate clients, and inspect payloads.

## Key Features

- **Topic-Based ACLs** — Control publish/subscribe access per topic pattern
- **Client Authentication** — Validate MQTT client credentials and certificates
- **Payload Inspection** — Inspect and validate message payloads against schemas
- **QoS Enforcement** — Enforce quality of service levels and rate limits per client
