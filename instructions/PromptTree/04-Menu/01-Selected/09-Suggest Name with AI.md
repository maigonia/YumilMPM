# Suggest Name with AI

**AI Name**

## When to Use

- When you want to automatically assign an appropriate name to a prompt
- When you want a descriptive name that matches the content

## What It Does

Uses AI to automatically suggest a name appropriate for the content of the selected prompt.

## How to Use

1. Select the prompt you want to rename
2. Select **PromptTree > Selected > Suggest Name with AI...** from the menu
3. A dialog opens

### Dialog Operations

1. **Select a preset** (optional): Choose a preset from the dropdown at the top
2. **Edit in the editor** (optional): Edit the template in the left editor
3. **Click the execute button**: Click the "Execute" button in the right panel
4. **Review the suggested name**: The suggested name appears in the right panel
5. **Apply**: Click the "Apply" button if the name is acceptable

### Dialog Layout

- **Left side (Editor)**: Display and edit template text
- **Right side (Result Panel)**: Suggested name and execute button
- **Preset Toolbar**: Preset selection, save, and delete

### Preset Management

- **Save**: Overwrite save the edited code to the current preset
- **Save As**: Save as a new preset
- **Delete**: Delete the selected preset (default cannot be deleted)

## Notes

- When calling an AI API within a programmable block, the [API Key Settings](../../../GlobalSettings/04-Menu/09-API%20Key%20Settings.md) corresponding to the AI being used is required
- When using [LM Studio](../../../GlobalSettings/02-Glossary/01-LM%20Studio.md), the server must be running
- The suggested name can be applied after review
- If a prompt with the same name exists at the same level, it is automatically renamed
- The last used preset is remembered per category

### How Editor Content Is Processed

The text entered in the editor is used directly as the output.

**Basic behavior:**

- The text in the editor is used as-is as the result
- If a [Programmable Block](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) (`@@@_..._@@@`) is included, that portion is replaced with the block's execution result, and the surrounding text remains unchanged
- Example: `preceding text` + `@@@_..._@@@` + `following text` → `preceding text` + `block output` + `following text`
- It also works as plain text without using programmable blocks

**Output processing:**
Only the **first line** of the final text is used as the suggested name. Even if there are multiple lines, only the first line is adopted.

**Example:**

- Plain text "Character Setting" → becomes the suggested name as-is

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [PromptTree](../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM%20Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
- [Suggest Tags with AI](08-Suggest%20Tags%20with%20AI.md)
- [Bulk Suggest Names with AI](../05-Checked/06-Bulk%20Suggest%20Names%20with%20AI.md)
- [Rename](../../../CategoryTree/03-Menu/01-Selected%20Category/04-Rename.md)
- [Programmable Block](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
