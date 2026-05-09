# AI Auto-Operation - Safe Setup Guide

**AI Auto-Operation - Safe Setup Guide**

## When to Use

- When you want to use this app with Claude Code safely
- When you want to minimize the risk of prompt injection
- When you want to create a dedicated environment for this app, separate from development work

## Why a "Safe Setup" Is Needed

Claude Code has many capabilities including file read/write, shell command execution, and web search. If malicious text (prompt injection) is included in this app's prompts, Claude Code could interpret it as an instruction and use these capabilities to perform unintended operations.

**Safe Setup** restricts Claude Code's capabilities to this app's operations only, helping to reduce the risk.

## How It Works

Claude Code has **a feature to restrict tool permissions on a per-project basis**.

By placing a configuration file inside a dedicated folder for this app, Claude Code launched from that folder is expected to behave as follows:

| Tool | Status | Description |
|------|--------|-------------|
| This app's MCP tools | Allowed | Prompt search, selection, generation, etc. |
| Bash | Blocked | Shell command execution prohibited |
| Read / Write / Edit | Blocked | File read/write prohibited |
| WebFetch / WebSearch | Blocked | Web access prohibited |

> **Note:** Including Claude Code, no AI agent currently guarantees complete protection — bugs and design issues in permission settings have been reported across all platforms. Always back up important data and exercise extra caution when handling untrusted prompts.

## Setup Steps

### Prerequisites

- **Claude Code** must be installed (VSCode extension or CLI version)
- A project must be open in this app
- Standard setup ([AI Auto-Operation](08-AI%20Auto-Operation.md)) must be completed

### Step 1: Create a Dedicated Folder for This App

Create a dedicated folder for this app's operations at any location on your PC.

Example: `C:\mpm-workspace` (name and location are up to you)

### Step 2: Launch Claude Code Once (auto-creates .claude folder)

Launching Claude Code inside the folder will automatically create a `.claude` folder.

**For VSCode extension:**

1. Open the `mpm-workspace` folder in VSCode (File > Open Folder)
2. Click the Claude Code icon in the left sidebar
3. Once the chat screen opens, you can close it for now

**For CLI version:**

1. Navigate to the `mpm-workspace` folder in a terminal
2. Run the `claude` command
3. After confirming it starts, exit with `/exit`

Verify that a `.claude` folder has been created inside the folder.

### Step 3: Create the Configuration File

Create a text file named `settings.local.json` inside the `.claude` folder, and copy & paste the following content:

```
mpm-workspace/
  └── .claude/          ← Auto-created in Step 2
      └── settings.local.json ← Create this
```

**`settings.local.json` content:**

```json
{
  "permissions": {
    "deny": [
      "Bash",
      "Read",
      "Write",
      "Edit",
      "WebFetch",
      "WebSearch"
    ],
    "allow": [
      "mcp__mpm__*"
    ]
  }
}
```

### Step 4: Restart Claude Code and Start Using

Launch Claude Code again. The configuration file will be loaded, and all operations except this app's tools will be blocked.

1. Launch Claude Code from the `mpm-workspace` folder in VSCode or terminal
2. Type "List all categories" → If this app's categories are displayed, setup is successful

> **Hint:** You can verify that file operations and shell commands are blocked by attempting them.

## Usage Guide

| Purpose | Folder to Use |
|---------|---------------|
| This app's operations (prompt management) | `mpm-workspace` (safe, restricted) |
| Regular development work | Your development project folder (standard Claude Code) |

By performing this app's operations and development work in separate folders, you can safely leverage Claude Code's capabilities for each purpose.

## Related

- [AI Auto-Operation](08-AI%20Auto-Operation.md)
- [AI Auto-Operation - Command Reference](11-AI%20Auto-Operation%20-%20Command%20Reference.md)
