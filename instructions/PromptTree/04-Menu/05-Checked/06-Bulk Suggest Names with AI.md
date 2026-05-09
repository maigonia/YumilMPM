# Bulk Suggest Names with AI

**Bulk Suggest Names with AI**

## When to Use

- When you want to rename multiple prompts at once
- When you want to automatically assign content-appropriate names using AI
- When you want to efficiently rename a large number of prompts

## What It Does

Bulk suggests names using AI for all checked prompts. It analyzes each prompt's content and automatically generates appropriate names. Suggested names can be individually reviewed and you can choose to apply or skip each one before batch applying.

## How to Use

1. Check the prompts you want to rename
2. Select **PromptTree > Checked > Bulk Suggest Names with AI...** from the menu
3. A dialog opens

### Dialog Operations

1. **Select a preset** (optional): Choose a preset from the dropdown at the top
2. **Edit in the editor** (optional): Edit the template in the left editor
3. **Click the execute button**: Processing starts sequentially for all prompts
4. **Review results**: Suggested names for each prompt appear in the center list
5. **Select apply/skip**: Choose "Apply" or "Skip" for each prompt
6. **Batch apply**: Click "Apply All (N)" to batch apply selected names

## Dialog Layout

The dialog has a 3-panel layout:

| Panel | Content |
| --- | --- |
| **Left (Editor)** | Display and edit preset code |
| **Center (Chunk List)** | Checked prompts list and status |
| **Right (Preview)** | Original name and suggested name for selected prompt |

### Status Icons

Each item in the chunk list shows an icon indicating its processing state:

| Icon | State |
| --- | --- |
| Gray circle | Unprocessed |
| Blue spinning icon | Processing |
| Green check | Scheduled for apply |
| Yellow sparkle | Suggestion available (undecided) |
| Gray skip | Skipped |
| Red alert | Error occurred |

## Processing Flow

### Sequential Processing

Prompts are processed **one at a time in order**:

1. The selected preset code is executed
2. AI suggests a name for each prompt
3. Suggested names are automatically set to "Apply" state
4. The user reviews and skips as needed
5. Click "Apply All" to batch apply items in apply state

### Processing Status Display

- The status bar shows "Processing X/Y: [prompt name]..."
- On completion: "Completed: X succeeded, Y failed"
- Can be cancelled midway (processed results are retained)

### Error Handling

- Processing continues even if errors occur
- Prompts with errors are shown with a red icon
- Error details can be viewed in the right panel

## Apply/Skip Operations

### Default Behavior

Suggested names are **automatically set to "Apply" state**. Change prompts you don't want to rename individually to "Skip."

### How to Operate

- **Change to Skip**: Click the "Skip" button in the right panel
- **Revert to Apply**: Click the "Apply" button to return a skipped item to apply state
- **Batch Apply**: Click "Apply All (N)" in the footer to apply all items in apply state

## Presets

### Selecting a Preset

- Select a preset from the dropdown at the top
- The last used preset is remembered per category
- The default preset is always available

### Default Preset Behavior

The default preset uses [LMEDIT](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md) to suggest appropriate names from the prompt's name and content. Only the first line of the output is used as the suggested name.

> **Note**: Presets cannot be edited or saved within this dialog. To edit presets, use the single [aiName](../01-Selected/09-Suggest Name with AI.md) feature.

## Notes

- When calling an AI API within a programmable block, the [API Key Settings](../../../GlobalSettings/04-Menu/09-API Key Settings.md) corresponding to the AI being used is required
- When using [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md), the server must be running
- Not available when no prompts are checked
- Processing runs sequentially, so it takes time when there are many prompts
- If a prompt with the same name already exists, it will be overwritten as-is

### How Editor Content Is Processed

The text entered in the editor is processed and used as output.

**Basic behavior:**

- The text in the editor is used as-is as the result
- If a [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) (`@@@_..._@@@`) is included, that portion is replaced with the block's execution result, and the surrounding text remains unchanged
- It also works as plain text without using programmable blocks

**Output processing:**

Only the **first line** of the final text is used as the suggested name. Even if there are multiple lines, only the first line is adopted.

## Comparison with Single AI Name Suggestion

| Item | Bulk Name Suggestion | Single Name Suggestion |
| --- | --- | --- |
| **Target** | Multiple checked prompts | One selected prompt |
| **Preset editing** | Selection only (no editing) | Edit and save possible |
| **Default state** | Suggestions auto-set to "Apply" | Manual apply after review |
| **Use case** | Bulk rename operations | Working through one at a time |

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Check State](../../01-Basics/01-Concepts/01-Understanding Check State.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [Suggest Name with AI](../01-Selected/09-Suggest Name with AI.md)
- [Bulk Suggest Tags with AI](05-Bulk Suggest Tags with AI.md)
- [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
