<div align="center">

# Full Stack Plugins

**4 plugins. The full development process. One unified ecosystem.**

*AI design tooling · Diagramming · Code quality · Server operations — production-grade, independently installable on Codex / ZCode / Kimi.*

[![License](https://img.shields.io/badge/License-Apache%202.0-green)](LICENSE)
[![Platforms](https://img.shields.io/badge/hosts-Codex%20%C2%B7%20ZCode%20%C2%B7%20Kimi-blue)](#install)
[![Plugins](https://img.shields.io/badge/plugins-4-green)](#plugin-catalog)

[简体中文](./README.md)

[About](#about) ·
[Install](#install) ·
[Plugin Catalog](#plugin-catalog) ·
[Architecture](#architecture) ·
[Ecosystem](#ecosystem) ·
[Contributing](#contributing)

</div>

---

## About

**Full Stack Plugins** is the plugin marketplace for the software development process, covering AI design tooling, diagramming, code quality, and server operations, across the Codex, ZCode, and Kimi Code host platforms.

This repository is the plugin-side counterpart of [Full Stack Skills](https://github.com/partme-ai/full-stack-skills): the skills side captures domain knowledge ("how to think"), while the plugin side ships executable capability ("what you can do") — MCP tools, gate pipelines, and automated operations. Both follow the same domain layout within one ecosystem: Stitch pairs with stitch-skills, ProcessOn with processon-skills.

> This repository contains marketplace metadata only (catalog and per-platform manifests), not plugin runtime code. Each plugin is maintained in its own repository, aligned by `catalog.json` as the single source of truth for IDs, names, versions, categories, and repository addresses.

### Coverage

| Domain | Problem | Solution (plugins) |
|--------|---------|--------------------|
| **AI design tooling** | UI design generation and frontend implementation | stitch-design |
| **Diagramming** | Flowcharts, architecture diagrams, mind maps | processon-design |
| **Code quality** | Making AI-written code pass lint on the first try | codeguard |
| **Server operations** | Baota panel sites / databases / cron jobs | bt-linux-panel |

---

## Install

### Codex

```bash
codex plugin marketplace add full-stack-plugins/full-stack-plugins
codex plugin add bt-linux-panel@full-stack-plugins
codex plugin add codeguard@full-stack-plugins
codex plugin add processon-design@full-stack-plugins
codex plugin add stitch-design@full-stack-plugins
```

### ZCode

Open Settings → Plugins → Create → Add plugin marketplace, enter `full-stack-plugins/full-stack-plugins`, then install from the personal marketplace section.

### Kimi Code CLI

```text
/plugins marketplace https://raw.githubusercontent.com/full-stack-plugins/full-stack-plugins/main/kimi-marketplace.json
```

---

## Plugin Catalog

| Plugin | ID | Version | Focus | Repository |
|--------|----|:-------:|-------|------------|
| 🛡️ **Baota Linux Panel** | `bt-linux-panel` | 1.0.1 | Operate the Baota Linux panel via MCP | [bt-linux-panel-plugin](https://github.com/full-stack-plugins/bt-linux-panel-plugin) |
| 🔍 **Codeguard** | `codeguard` | 0.3.4 | Make AI-written code pass lint on the first try (multi-language rule sets) | [codeguard-plugin](https://github.com/full-stack-plugins/codeguard-plugin) |
| 📊 **ProcessOn Diagrams** | `processon-design` | 0.2.1 | Design polished, editable ProcessOn diagrams (flowcharts / architecture / mind maps) | [processon-design-plugin](https://github.com/full-stack-plugins/processon-design-plugin) |
| 🎨 **Google Stitch Design** | `stitch-design` | 0.7.9 | Design and build with Google Stitch | [stitch-design-plugin](https://github.com/full-stack-plugins/stitch-design-plugin) |

---

## Architecture

### How the marketplace works

`catalog.json` is the single source of truth. `scripts/sync-marketplaces.mjs` generates the three platform manifests from it and validates each plugin repository's skills directories (frontmatter, naming consistency):

```
full-stack-plugins/
├── catalog.json                        # Single source of truth: IDs / names / versions / categories / repos
├── .agents/plugins/marketplace.json    # Codex manifest (generated)
├── marketplace.json                    # ZCode manifest (generated)
├── kimi-marketplace.json               # Kimi manifest (generated)
└── scripts/                            # Sync and release tooling
```

Each independent plugin repository owns its runtime adapters: `.codex-plugin/plugin.json`, `.zcode-plugin/plugin.json`, and `kimi.plugin.json`.

### Progressive disclosure

Skills inside plugins follow the [Agent Skills specification](https://agentskills.io):

1. **At startup**: only skill names and descriptions are loaded (minimal context)
2. **On demand**: the full `SKILL.md` loads when the agent recognizes a relevant task
3. **In depth**: reference files are read only when explicitly needed

---

## Ecosystem

| Resource | Link |
|----------|------|
| **Skills hub (full stack)** | [partme-ai/full-stack-skills](https://github.com/partme-ai/full-stack-skills) |
| **Skill packages org (full stack)** | [github.com/full-stack-skills](https://github.com/full-stack-skills) |
| **AIGC-side plugin marketplace** | [github.com/full-aigc-plugins](https://github.com/full-aigc-plugins) |
| **Skills hub (AIGC)** | [partme-ai/full-aigc-skills](https://github.com/partme-ai/full-aigc-skills) |
| **Agent Skills specification** | [agentskills.io](https://agentskills.io) |
| **Skills CLI** | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) |
| **PartMe.AI** | [github.com/partme-ai](https://github.com/partme-ai) |

---

## Contributing

### Release discipline

Any plugin code change (no matter the size) requires a version bump and release; marketplaces detect updates by version number:

```bash
node scripts/bump-plugin.mjs <plugin-id> <major|minor|patch>
```

The command updates the catalog version, syncs the four manifests in the plugin repository, and regenerates the three platform manifests.

### Adding a plugin

1. Build the plugin in its own repository with the three-platform adapter layer (`.codex-plugin` / `.zcode-plugin` / `kimi.plugin.json`)
2. Register the entry in `catalog.json`
3. Run `node scripts/sync-marketplaces.mjs --write` to regenerate manifests, then commit

---

## License

Apache 2.0 — see [LICENSE](LICENSE).

---

<div align="center">

**If this project helps you, please give us a ⭐️**

Made with ❤️ by PartMe.AI Team

</div>
