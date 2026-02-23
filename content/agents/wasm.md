+++
title = "wasm"
template = "agent.html"
path = "wasm"

[extra]
name = "wasm"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-wasm"
binary_name = "zentinel-wasm-agent"
description = "Execute custom Wasm modules for high-performance request/response processing in any language."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "scripting"
tags = ["scripting", "wasm", "extensibility", "performance"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Scripting agents"
language = "Rust"
+++

## Overview

The wasm agent executes WebAssembly modules for high-performance request and response processing. Write custom logic in any language that compiles to Wasm — Rust, Go, C/C++, AssemblyScript, and more.

## Key Features

- **Language Agnostic** — Write modules in Rust, Go, C/C++, AssemblyScript, or any Wasm-compatible language
- **High Performance** — Near-native execution speed with Wasmtime runtime
- **Sandboxed Execution** — Wasm modules run in a secure sandbox with configurable capabilities
- **Hot Reload** — Update Wasm modules without restarting Zentinel
