# MCP Server Settings
**MCP Server Settings**

## When to Use
- When you want to change the range of tools used in AI Auto-Operation
- When you want to restrict the MCP tools exposed to AI clients (such as Claude Code)

## What It Does
Selects the set of tools (profile) that the MCP server exposes to AI clients. When you click OK, the MCP configuration (JSON) for the AI client is copied to the clipboard.

## Profiles

| Profile | Description |
|---------|-------------|
| **Full** | All tools (48 tools, ~7.5K tokens) |
| **Custom** | Select tools individually |

## How to Use
1. Select GlobalSettings > **MCP Server Settings** to open the dialog
2. Select **Full** (exposes all tools) or **Custom** (select tools individually)
3. Click **OK** → MCP configuration (JSON) is copied to the clipboard
4. Paste the JSON into the AI client's MCP configuration file (e.g., `.mcp.json`) and save
5. Restart the AI client's session

## Custom Tool Categories

Selecting Custom lets tools be toggled on/off per category.

| Category | Examples |
|---|---|
| Browsing | `list_categories`, `get_prompt`, `search_prompts` |
| Operations | `check_prompt`, `generate`, `preview_generation` |
| Instructions | `list_instruction_types`, `get_instruction_content` |
| Presets & Favorites | `list_check_presets`, `apply_favorite_list` |
| Info | `get_project_info`, `get_category_info` |
| Editing | `edit_prompt`, `add_prompt`, `add_category` |
| Templates | `set_category_template`, `set_final_edit` |
| Other | `list_tags`, `evaluate_ci` |
| Queue Patterns | `create_queue_pattern`, `add_queue_item` |
| Deletion | `delete_prompt`, `delete_category`, `bulk_delete_prompts` |

**Deletion** groups destructive operations. Turn this category off to prevent AI from performing delete actions.

## Dialog Operations

- **Profile selection**: Choose from Full / Custom
- **Tool list**: Checkboxes for each tool (individual toggling only available when Custom is selected)
- **Estimated tokens**: Displays the number of selected tools and estimated token consumption

## Notes
- JSON is copied to the clipboard via the OK button only when the profile has been changed
- More tools means higher AI token consumption. Reducing unnecessary tools can lower costs

## Related

- [AI Auto-Operation](../../Utility/01-Menu/08-AI Auto-Operation.md)
- [On Demand](../../PromptGeneration/04-Menu/02-Generation On Demand/README.md)
- [API Server Settings](../../PromptGeneration/04-Menu/02-Generation On Demand/02-API Server Settings.md)
