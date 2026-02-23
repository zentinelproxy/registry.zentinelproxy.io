+++
title = "lua"
template = "agent.html"
path = "lua"

[extra]
name = "lua"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-lua"
binary_name = "zentinel-lua-agent"
description = "Embed custom Lua scripts for flexible request/response processing and header manipulation."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "scripting"
tags = ["scripting", "extensibility", "core"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Scripting agents"
language = "Rust"
+++

## Overview

The lua agent provides a Lua scripting environment for custom request/response processing. Familiar to users of OpenResty and nginx Lua modules, it offers a lightweight way to extend Zentinel's behavior.

## Key Features

- **Lua 5.4 Runtime** — Full Lua 5.4 environment with standard library
- **Header Manipulation** — Read, modify, add, or remove request and response headers
- **Body Processing** — Access and transform request and response bodies
- **Familiar API** — Similar API conventions to OpenResty for easy migration
