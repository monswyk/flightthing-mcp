<div align="center">

<a href="https://flightthing.com">
  <img src="https://flightthing.com/mimes/logos/flightthing-logo-with-text.png" alt="" width="320">
</a>

# The Flight Thing AI/MCP

### MCP bridge & client configs

<p>
  <a href="https://github.com/monswyk/flightthing-mcp"><img src="https://img.shields.io/badge/GitHub-monswyk%2Fflightthing--mcp-181717?logo=github&logoColor=white" alt="Repository on GitHub"></a>
  &nbsp;
  <a href="https://flightthing.com"><img src="https://img.shields.io/badge/flightthing.com-app-4f46e5" alt="The Flight Thing"></a>
</p>

Wire **Cursor**, **Claude Desktop**, and other MCP clients to [The Flight Thing](https://flightthing.com).  
Hosted MCP endpoint: `https://flightthing.com/api/mcp`

</div>

---

## What this repo contains
- Bridge
  - `bridge/flightthing-bridge.js`: Node bridge that forwards MCP JSON-RPC to the hosted MCP endpoint for The Flight Thing.
- Config (general)
  - Templates for MCP clients, plus concrete examples below.

## Quick start
1. Copy the bridge script and make it executable:
   - `bridge/flightthing-bridge.js`
2. Choose a config approach (general or example below).
3. Add your token.
4. Start your MCP client.

## Config (general)
You can configure any MCP client in one of two ways:
- Direct URL config:
  - `url`: `https://flightthing.com/api/mcp`
  - `headers`: `x-mcp-token: YOUR_TOKEN_HERE`
- Bridge config (for clients that require a local command):
  - `command`: `node`
  - `args`: path to `bridge/flightthing-bridge.js`
  - `env`: `FLIGHTTHING_TOKEN=YOUR_TOKEN_HERE`

Templates:
- `configs/general/direct-url.json`
- `configs/general/bridge-command.json`
- `configs/general/curl.txt`

## Claude Desktop
Use the OS-specific templates:
- `configs/claude-desktop/claude_desktop_config.macos.json`
- `configs/claude-desktop/claude_desktop_config.windows.json`
- `configs/claude-desktop/claude_desktop_config.linux.json`

Update the bridge path and set `FLIGHTTHING_TOKEN` in your environment.

## Cursor setup
1. Copy `configs/cursor/mcp.json` into your Cursor MCP config.
2. Paste your token into the `x-mcp-token` header.
3. Save and restart Cursor.

## Configuration details
The bridge forwards requests to:
- `https://flightthing.com/api/mcp`

The token is sent as:
- `x-mcp-token` header

## Security notes
- Treat the token like a password.
- Never commit tokens to git.
- Revoke tokens you no longer need.

## Development
The bridge is a plain Node script and does not require build steps.

## Docs
- `docs/paths.md`: Common config paths by OS.
- `docs/troubleshooting.md`: Typical issues and fixes.
- `docs/howto.md`: cURL examples and tool calling pattern.
- `docs/functions.md`: Short descriptions of all MCP tools.
