+++
title = "transform"
template = "agent.html"
path = "transform"

[extra]
name = "transform"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-transform"
binary_name = "zentinel-transform-agent"
description = "Advanced request and response transformation with URL rewriting, header manipulation, and JSON body transforms."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "utility"
tags = ["transformation", "rewriting", "core"]
protocol_version = "v2"
min_zentinel_version = "25.12.0"
bundle_included = true
bundle_group = "Utility agents"
language = "Rust"
+++

## Overview

The transform agent provides powerful request and response transformation capabilities. Rewrite URLs, manipulate headers, and transform JSON bodies using a declarative configuration.

## Key Features

- **URL Rewriting** — Rewrite request paths, query parameters, and host headers
- **Header Manipulation** — Add, remove, rename, or modify request and response headers
- **JSON Body Transforms** — Transform JSON request and response bodies using JSONPath expressions
- **Conditional Transforms** — Apply transformations based on request conditions
