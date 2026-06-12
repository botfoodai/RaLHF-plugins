> [!IMPORTANT]
> **This marketplace has moved.** Bot Food's Claude Code and Codex plugins are now
> served from a single consolidated marketplace: **[`botfoodai/marketplace`](https://github.com/botfoodai/marketplace)**.
>
> ```
> /plugin marketplace add botfoodai/marketplace
> /plugin install ralhf
> ```
>
> This repository remains available for existing installs but is no longer the
> canonical source. Please switch to `botfoodai/marketplace`.

# Bot Food Claude Code Plugins

The official directory of public [Bot Food](https://botfood.ai) plugins for Claude Code.

This is a [Claude Code plugin marketplace](https://code.claude.com/docs/en/plugin-marketplaces) — a catalog that lets Claude Code discover and install our plugins with a single command.

## Plugins

| Plugin | Description | Status |
|---|---|---|
| **[ralhf](https://github.com/botfoodai/RaLHF)** | Personal context engineer — assembles relevant context from your RaLHF wiki, memory, files, and connected apps before every task | ✅ v1.0.0 |

## Install

In Claude Code, add this marketplace and install any plugin:

```
/plugin marketplace add botfoodai/RaLHF-plugins
/plugin install ralhf
```

Or use our one-line installer:

```bash
curl -fsSL install.ralhf.ai | bash
```

## How this works

This repository is structured as a Claude Code marketplace. The catalog lives at [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) and points at the actual plugin repos.

When you run `/plugin marketplace add botfoodai/RaLHF-plugins`, Claude Code clones this repo, reads `marketplace.json`, and lists the plugins available for install. Each plugin is then fetched from its own dedicated repo on demand.

## Adding a plugin

To list a new plugin in this marketplace:

1. Publish the plugin in its own repo (e.g., `botfoodai/<plugin-name>`)
2. Add an entry to `.claude-plugin/marketplace.json`:
   ```json
   {
     "name": "<plugin-name>",
     "description": "...",
     "author": { "name": "Bot Food Corporation", "url": "https://botfood.ai" },
     "category": "productivity",
     "source": {
       "source": "git",
       "url": "https://github.com/botfoodai/<plugin-name>.git",
       "ref": "main"
     },
     "homepage": "https://...",
     "license": "Apache-2.0",
     "keywords": [...]
   }
   ```
3. Commit and push to `main`. Users on `/plugin marketplace update` will see the new plugin.

## License

Marketplace catalog: [Apache License, Version 2.0](./LICENSE).

Each plugin in the marketplace is independently licensed — see the plugin's own `LICENSE` file. The current entries are:

| Plugin | License |
|---|---|
| ralhf | Apache-2.0 |

## Trademark

"RaLHF" and "Bot Food" are trademarks of Bot Food Corporation. The Apache 2.0 license does not grant rights to use these marks. See [the trademark policy in the RaLHF repo](https://github.com/botfoodai/RaLHF/blob/main/TRADEMARK.md) for details.

## Author

Built by [Bot Food Corporation](https://botfood.ai). For questions or to report issues, open an issue here or reach out at [ralhf.ai](https://ralhf.ai).
