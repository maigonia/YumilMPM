# AI Auto-Operation

**AI Auto-Operation (Claude Code)**

> **Note: AI Auto-Operation is an experimental feature.**

## When to Use

- When you want AI (Claude Code) to automatically search, select, and generate prompts
- When you want AI to select from a large number of prompts based on given conditions
- When you want to operate this app just by giving chat instructions

## What It Does

Provides guidance on how to connect an AI assistant (Claude Code) with this app via the MCP protocol. Clicking this menu displays setup instructions and usage information (this instruction page).

After setup, Claude Code can perform the following operations just through chat instructions:

- View category lists, search prompts (supports regex and exclusion search)
- View, add, and edit prompts (content, name, tags)
- Check/uncheck prompts (individual and bulk)
- List, apply, and save check presets
- List and apply favorite lists
- Toggle category output ON/OFF, configure templates, configure Final Edit
- Execute prompt generation

> **Important Security Note**: AI processes the content of prompts received from this app as data, but if malicious text is included in prompts, it could influence the AI's behavior (prompt injection). When using prompt data obtained from external sources, please review the content in advance. It is also recommended not to set Claude Code's operation approval dialog to auto-approve.

## MCP Server Connection Management

Connecting, disconnecting, and applying settings changes to the MCP server are all done on the **AI client side**. This app is only responsible for "starting the API server" and "generating the MCP configuration JSON (connection info)".

| Operation | Where | How |
|-----------|-------|-----|
| Connect | AI client side | Paste JSON into MCP config file, then reload VSCode (Ctrl+Shift+P → Developer: Reload Window) |
| Disconnect | AI client side | In `/mcp`, Disconnect or Disable mpm |
| Apply settings changes | AI client side | Re-copy JSON from [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP Server Settings.md), update the config file, then reload VSCode (Ctrl+Shift+P → Developer: Reload Window) |

For detailed steps, see [AI Auto-Operation - Disconnect & Reconnect](10-AI Auto-Operation - Disconnect & Reconnect.md).

## Supported AI Tools

This feature is based on the standard MCP protocol (Model Context Protocol) specification, so any MCP-compatible AI tool can connect. The config JSON is output in **stdio transport** format (`command` + `args` to launch a process and communicate via standard I/O).

The setup steps below use **VSCode + Claude Code** as an example, but other MCP clients can connect in the same way.

- Claude Code (VSCode extension) — Tested. Explained in this instruction. Paid service (as of March 2026)
- Google Antigravity — May offer a free tier
- Cline (VSCode extension)
- LM Studio
- Cursor, Windsurf, etc.

Please check each tool's official site for the latest pricing and plan information.

Each AI tool has different approaches to tool execution approval and permission restrictions. Please review the security settings of your chosen AI tool before use.

## Setup Steps

### Step 1: Get MCP Config JSON from This App

1. Click PromptGeneration > **Generation On Demand** to start the API server
2. Open GlobalSettings > **MCP Server Settings**, select a profile, and press **OK**
3. The MCP config (JSON) is copied to the clipboard

### Step 2: Install VSCode

VSCode (Visual Studio Code) is a free text editor. Skip to Step 3 if already installed.

- Download and install from the official site https://code.visualstudio.com/

### Step 3: Create and Open a Project Folder in VSCode

Claude Code operates on a per-project-folder basis. Create a dedicated folder for this app.

1. Create a new folder anywhere on your PC (e.g., `C:\mpm-workspace`)
2. Open VSCode and use **File > Open Folder** to open the created folder

### Step 4: Install the Claude Code Extension

Claude Code is a tool that lets you work while chatting with AI. Skip to Step 5 if already installed.

> **Prerequisite**: Claude Code requires **Git**. If it is not installed, download it from https://git-scm.com/.

1. Click the square icon (Extensions) on the left side of VSCode
2. Type "Claude Code" in the search box
3. **Install** "Claude Code"
4. After installation, sign in with your Anthropic account

### Step 5: Paste JSON into the MCP Config File

1. Create a new `.mcp.json` file in the project folder root in VSCode
2. Paste the JSON copied to the clipboard in Step 1 and save
3. Run **Developer: Reload Window** from the VSCode command palette (Ctrl+Shift+P)

> **Note**: The Connect / Reconnect actions in Claude Code's `/mcp` menu sometimes fail to pick up `.mcp.json` changes. Use **Developer: Reload Window** for reliable application of the config.

### Step 6: Start Chatting with Claude Code

1. The Claude Code icon appears in VSCode's left sidebar
2. Click it to open the chat screen
3. Make sure the **Generation On Demand** button is turned on in this app
4. Just give instructions in natural language, like "Check all prompts in the Quality category"

> Please also see [AI Auto-Operation - Safe Setup Guide](09-AI Auto-Operation - Safe Setup Guide.md).

### Subsequent Use

Setup is only needed once. From then on:

1. Start On Demand in this app (PromptGeneration > Generation On Demand)
2. You can operate this app simply by chatting normally in Claude Code

## Notes

- This feature uses the MCP protocol (Model Context Protocol) to connect AI with this app
- Communication between this app and the AI client is done locally (localhost). However, please note that the AI client (e.g., Claude Code) sends prompt content to the AI service's API, meaning your prompt content will be transmitted to the AI service provider
- API tokens are randomly generated on first startup and the same token is reused thereafter. You can also manually regenerate it from [API Server Settings](../../PromptGeneration/04-Menu/02-Generation On Demand/02-API Server Settings.md)
- If you regenerate the token, re-copy the JSON from [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP Server Settings.md) and update the MCP config file

## Related

- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [On Demand](../../PromptGeneration/04-Menu/02-Generation On Demand/README.md)
- [API Server](../../PromptGeneration/04-Menu/02-Generation On Demand/02-API Server Settings.md)
- [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP Server Settings.md)
