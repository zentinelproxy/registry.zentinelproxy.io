+++
title = "js"
template = "agent.html"
path = "js"

[extra]
name = "js"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-js"
binary_name = "zentinel-js-agent"
description = "Write custom request/response processing logic in JavaScript using the QuickJS engine."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "scripting"
tags = ["scripting", "javascript", "extensibility"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Scripting agents"
language = "Rust"
+++

## Overview

The js agent embeds the QuickJS JavaScript engine, allowing you to write custom request and response processing logic in JavaScript. Ideal for quick transformations, custom routing logic, and prototyping.

## Key Features

- **QuickJS Engine** — Fast, lightweight JavaScript runtime with no external dependencies
- **Request/Response Access** — Full access to headers, body, URL, and method
- **Hot Reload** — Update scripts without restarting Zentinel
- **Sandboxed Execution** — Scripts run in an isolated sandbox with configurable resource limits
