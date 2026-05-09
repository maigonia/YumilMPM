# AI Auto-Operation - Disconnect & Reconnect

**AI Auto-Operation - Disconnect & Reconnect**

## Is Disconnection Necessary?

Usually, disconnection is not necessary. If this app's connection info is already set in `.mcp.json`, Claude Code will automatically connect on startup.

However, when an MCP server is connected, its tool definitions consume Claude Code's context (tokens). If you're concerned about context pressure during work that doesn't use this app, disconnecting can reduce token consumption.

## Temporary Disconnection

Run the `/mcp` command in the Claude Code chat to open the MCP server list. Select mpm and choose **Disconnect** (or **Disable**) to disconnect for the current session only. Since the entry remains in `.mcp.json`, it will automatically reconnect on the next session startup.

## Permanent Disconnection

Remove this app's entry from `.mcp.json` to prevent automatic reconnection in future sessions. Ask Claude Code "Remove the mpm entry from .mcp.json," or manually open `.mcp.json` in the project folder root in VSCode, delete the `"mpm"` entry, and save the file. Then run the `/mcp` command to disconnect the current session.

## How to Reconnect

Run **Developer: Reload Window** from the VSCode command palette (Ctrl+Shift+P). If the JSON was re-obtained from [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP Server Settings.md) and `.mcp.json` was updated, Reload Window applies the new settings.

> **Note**: The Reconnect / Enable buttons in the `/mcp` menu sometimes fail to pick up `.mcp.json` updates. Use **Developer: Reload Window** for reliable application of the config.

**On Demand** must be running in this app (PromptGeneration > Generation On Demand).

## Related

- [AI Auto-Operation](08-AI Auto-Operation.md)
- [On Demand](../../PromptGeneration/04-Menu/02-Generation On Demand/README.md)
- [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP Server Settings.md)
