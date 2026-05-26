# X-VPN MCP Skill

X-VPN MCP‘s usage skill for AI agents.

The Skill is agent-agnostic and works with any client supported by
[`vercel-labs/skills`](https://github.com/vercel-labs/skills). The
repository also ships a Claude Code plugin manifest, so Claude Code
users get a one-step install that bundles the MCP server.

## Prerequisite — install the X-VPN client

The Skill drives the local X-VPN client over MCP. The client is
distributed separately and must be installed first.

```sh
sh <(curl -sSf https://app.xvpncdn.com/rpc788pbdq/install.sh)
```

The installer is an interactive TUI that sets up the daemon and the
MCP bridge. After it finishes, the daemon listens on
`http://127.0.0.1:3841/mcp`.

## Install — choose one path

### Path A — As a Claude Code plugin (recommended)

Gives you the Skill **and** auto-registers the `xvpn` MCP server, so
the `xvpn_*` tools appear in your session immediately.

```
/plugin marketplace add X-VPN/xvpn-mcp-skill
/plugin install xvpn@xvpn-plugins
```

### Path B — As a standalone Skill via `npx skills`

Installs only the Skill markdown. Works with any agent supported by
[`vercel-labs/skills`](https://github.com/vercel-labs/skills) — Claude
Code, Cursor, Codex, Gemini CLI, Cline, and others. The CLI will
detect installed agents and prompt you to pick.

```sh
npx skills add X-VPN/xvpn-mcp-skill
```

## What's in this repo

```
.claude-plugin/
  plugin.json         Plugin manifest
  marketplace.json    Marketplace entry (lets users `/plugin marketplace add` this repo)
skills/
  xvpn-mcp-skill/
    SKILL.md          Router — read first
    references/       Loaded on demand by the agent
.mcp.json             MCP server registration (used by the plugin path)
```

## Author

X-VPN — support@xvpn.io — https://xvpn.io
