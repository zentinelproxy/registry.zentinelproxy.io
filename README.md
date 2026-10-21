<p align="center">
  <a href="https://zentinelproxy.io">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/zentinelproxy/design/main/marks/lockup/zentinel-lockup-dark.svg">
      <img alt="Zentinel" src="https://raw.githubusercontent.com/zentinelproxy/design/main/marks/lockup/zentinel-lockup-light.svg" height="52">
    </picture>
  </a>
</p>

<h3 align="center">Zentinel agent registry</h3>

<p align="center">The source of registry.zentinelproxy.io: one page per Zentinel agent, with what it does, how to install it and how to configure it.</p>

<p align="center">
  <a href="https://registry.zentinelproxy.io">registry.zentinelproxy.io</a> &middot;
  <a href="https://docs.zentinelproxy.io">Docs</a> &middot;
  <a href="https://github.com/zentinelproxy">All repositories</a>
</p>

A [Zola](https://www.getzola.org/) site. The index lists every agent with a
search field and a category filter; each agent has its own page at
`https://registry.zentinelproxy.io/<name>/`, which is the agent's reference
(the docs site has no per-agent pages). The machine-readable counterpart is
[api.zentinelproxy.io](https://github.com/zentinelproxy/api.zentinelproxy.io).

## Adding an agent page

Create `content/agents/<name>.md`. The `agents` section is transparent and not
rendered itself, so `path` sets the page's URL. The front matter drives the
card on the index and the header, install box and metadata on the agent page;
the Markdown body is the page's documentation.

```toml
+++
title = "WAF (Web Application Firewall)"
weight = 10
template = "agent.html"
path = "waf"
description = "Pure Rust WAF with 285 detection rules, anomaly scoring and API security."

[extra]
name = "waf"
version = "0.3.0"
repository = "zentinelproxy/zentinel-agent-waf"
binary_name = "zentinel-waf-agent"
install_cmd = "zentinel bundle install waf"
protocol_version = "v2"
description = "Pure Rust WAF with 285 detection rules, anomaly scoring and API security."
author = "Zentinel Core Team"
author_url = "https://github.com/zentinelproxy"
license = "Apache-2.0"
status = "stable"
category = "security"
tags = ["security", "waf", "core", "api-security"]
min_zentinel_version = "26.01.0"
official = true
bundle_included = true
bundle_group = "Core agents"
language = "Rust"
+++

## Overview
...
```

| Field | Meaning |
|---|---|
| `name` | short name; the index sorts by it |
| `version`, `min_zentinel_version` | current release of the agent, and the oldest Zentinel it supports |
| `repository` | `owner/repo` on GitHub; source link |
| `binary_name` | the installed executable |
| `install_cmd` | command shown in the install box. If unset and `bundle_included = true`, the page shows `zentinel bundle install <name>`; if neither, no install box |
| `crate_name` | optional; adds a crates.io link. Agent crates are not on crates.io today, so leave it unset unless the crate is published |
| `protocol_version` | `v2` for every current agent |
| `status` | `stable`, `beta` or `deprecated` (rendered as a badge; any other value is shown as plain text) |
| `category` | `security`, `api-security`, `identity`, `scripting`, `protocol`, `utility` or `core` (the index filter) |
| `tags` | searchable on the index; each links to the index searched for that tag |
| `official` | adds the "Official" badge |
| `author`, `author_url`, `license`, `language` | shown in the metadata list; `language` also marks non-Rust agents on their card |
| `bundle_included`, `bundle_group` | whether `zentinel bundle` installs it, and under which group |

Install commands must work today: an agent that is not in the bundle
(`curl -s https://api.zentinelproxy.io/v1/bundle/`) gets `cargo install --git
https://github.com/zentinelproxy/<repo>` only if it builds that way, otherwise
a pointer to its release binaries. Check every configuration example against
the agent's code; KDL drops unknown keys silently. When an agent is added or
its version changes, update its record in `api.zentinelproxy.io` too.

## Development

```bash
zola serve          # http://127.0.0.1:1111
zola build          # into public/
```

There is no `mise.toml` here; use the same zola as the other sites (0.19).
`config.toml` uses zola 0.22's class-based highlighting, which 0.19 ignores, so
code on agent pages builds without highlighting until the sites move to 0.22
([zentinelproxy.io#51](https://github.com/zentinelproxy/zentinelproxy.io/issues/51));
`sass/_syntax.scss` already styles the 0.22 output.

`static/_headers` sets the security headers and the Content Security Policy
(`script-src 'self' 'unsafe-inline'`); third-party scripts do not load.

**Design tokens are vendored, not edited.** These files are copied from
[zentinelproxy/design](https://github.com/zentinelproxy/design) (`dist/scss/`
and `fonts/`, the same mapping zentinelproxy.io uses) and must not be edited by
hand here: `sass/_tokens.scss`, `sass/_fonts.scss`, `sass/_frame.scss` and
`static/fonts/`. Change `tokens.json` in the design repository, rebuild, and
copy the new files in; the design repository's `sync` script does not cover
this site yet. The registry's own styles are `sass/style.scss` and
`sass/_syntax.scss`.

## Deploy

Cloudflare Pages builds and serves the site from this repository: every merge
to `main` deploys to registry.zentinelproxy.io, and pull requests get a preview
deployment. There are no GitHub Actions workflows.

## Related

- [zentinel](https://github.com/zentinelproxy/zentinel): the proxy and its `bundle` command
- [api.zentinelproxy.io](https://github.com/zentinelproxy/api.zentinelproxy.io): the same agent metadata as JSON
- [Agent docs](https://docs.zentinelproxy.io/agents/): how agents work and agent protocol v2
- [design](https://github.com/zentinelproxy/design): the design tokens this site vendors

## License

This repository has no `LICENSE` file yet. The typefaces in `static/fonts/` are
under the SIL Open Font License 1.1 (the `*-OFL.txt` files next to them).

---

<p align="center">
  <sub>Part of <a href="https://zentinelproxy.io">Zentinel</a>, the security-first reverse proxy. The shisa guards the gate.</sub>
</p>
