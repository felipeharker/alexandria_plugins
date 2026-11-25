# alexandria_plugins

Alexandria's connectors as plugins, for a client that takes plugins from a Git repository. Nothing else is here: each plugin is one command, which starts a server Alexandria's installer has already put on the PC.

| Plugin | Reaches | Needs on the PC |
|---|---|---|
| `rhino-mcp-platform` | Rhino 8 and Grasshopper | Rhino 8 with McNeel's Rhino-MCP-Platform package |
| `coreldraw-live` | The document open in CorelDRAW | CorelDRAW |
| `squarecoil` | Aria's SquareCoil, read-only | Your own SquareCoil login, stored by the installer |

## Before a plugin works

Run **Alexandria Setup** or **Install Connectors** on Rhino's Alexandria Tools tab once, or `Install Claude Connectors.cmd` from the shared Alexandria packages folder on a PC without Rhino. That installs the servers, and asks for your SquareCoil login. A plugin without them says so and stops.

## Adding it to Grok

Dashboard, Plugins, Marketplaces, Add marketplace, Import from a repository, with this repository's address:

```
https://github.com/felipeharker/alexandria_plugins
```

The repository is public, so nobody needs to be given access to it. It holds no code and no data.

## Don't edit here

This repository is written from Alexandria's private management repository, where the plugins are edited (`agent_connectors/plugins/`, by `agent_connectors/sync_plugins.py`). A change made here is overwritten by the next one.

The lists of plugins are at the root under three names, because each client reads its own: `.grok-plugin/`, `.cursor-plugin/` and `.claude-plugin/`, each with a `marketplace.json`. Each plugin in `plugins/` has its command twice for the same reason, as `.mcp.json` and `mcp.json`.
