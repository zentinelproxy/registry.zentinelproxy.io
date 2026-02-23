+++
title = "content-scanner"
template = "agent.html"
path = "content-scanner"

[extra]
name = "content-scanner"
version = "0.4.0"
repository = "zentinelproxy/zentinel-agent-content-scanner"
binary_name = "zentinel-content-scanner-agent"
description = "Malware scanning agent using ClamAV daemon for file upload protection."
author = "Zentinel Core Team"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["content-scanner", "malware", "clamav", "security", "file-upload"]
protocol_version = "v2"
min_zentinel_version = "26.01.0"
bundle_included = true
bundle_group = "Security agents"
language = "Rust"
+++

## Overview

The content-scanner agent integrates with ClamAV to scan file uploads for malware, viruses, and malicious content before they reach your backend services.

## Key Features

- **ClamAV Integration** — Connects to a ClamAV daemon for real-time file scanning
- **Upload Protection** — Scans multipart form uploads and raw body content
- **Configurable Actions** — Block, quarantine, or flag detected threats
- **Size Limits** — Configurable maximum file sizes and scan timeouts
