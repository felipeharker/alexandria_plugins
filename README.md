# alexandria_plugins

Alexandria's connectors as plugins, for Claude and Grok. Nothing else is here: a Claude plugin is one command, which starts a server Alexandria's installer has already put on the PC, and the Grok plugin is a skill's text.

| Plugin | In | Reaches | Needs on the PC |
|---|---|---|---|
| `rhino-mcp-platform` | Claude | Rhino 8 and Grasshopper | Rhino 8 with McNeel's Rhino-MCP-Platform package |
| `coreldraw-live` | Claude | The document open in CorelDRAW | CorelDRAW |
| `squarecoil` | Claude | Aria's SquareCoil, read-only | Your own SquareCoil login, stored by the installer |
| `squarecoil` (skill) | Grok | Aria's SquareCoil, read-only, through its command line on your PC | The same, and Grok's desktop app with local execution on |

Grok starts a plugin's server on its own cloud computer, which has none of these servers and nobody's login, so Grok gets SquareCoil as a skill instead: it runs SquareCoil's command line on your PC. Rhino and CorelDRAW have no Grok plugin.

## Before a plugin works

Run **Alexandria Setup** or **Install Connectors** on Rhino's Alexandria Tools tab once, or `Install AI Connectors.cmd` from the shared Alexandria packages folder on a PC without Rhino. That installs the servers and SquareCoil's command line, and asks for your SquareCoil login. A plugin without them says so and stops.

## Adding it to Claude

They are the organization's plugins: an owner adds them in the organization's plugin settings, and members get them in Claude Desktop and Claude Code.

## Adding it to Grok

Dashboard, Plugins, Marketplaces, Add marketplace, Import from a repository, with this repository's address:

```
https://github.com/felipeharker/alexandria_plugins
```

Then each person, in Grok's desktop app on their Windows PC: Settings, Computer, Execution on this computer, Ask every time (Grok asks before each command) or Always allow. If the skill doesn't show, paste `plugins/squarecoil-grok/skills/squarecoil/SKILL.md` into a new skill and publish it to the team.

The repository is public, so nobody needs to be given access to it. It holds no code and no data.

## Don't edit here

This repository is written by a workflow from Alexandria's private management repository, where the plugins are edited (`agent_connectors/plugins/`), each time that repository's main branch changes. A change made here is overwritten by the next one.

Each client reads its own list of plugins at the root: `.claude-plugin/marketplace.json` for Claude, and `.grok-plugin/` and `.cursor-plugin/` (the importer in Grok's dashboard is Cursor's) for Grok.
