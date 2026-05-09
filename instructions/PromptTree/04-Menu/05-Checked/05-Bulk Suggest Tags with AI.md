# Bulk Suggest Tags with AI

**Bulk Suggest Tags with AI**

## When to Use
- When you want to add tags to multiple prompts at once
- When you want to tag efficiently using AI
- When you want to batch apply specific tags without using AI

## What It Does
Bulk suggests tags using AI for all checked prompts. Suggested tags can be applied after review.

You can also batch apply specific tags by simply entering comma-separated tags in the editor without using programmable blocks.

## How to Use
1. Check the prompts you want to tag
2. Select **PromptTree > Checked > Bulk Suggest Tags with AI...** from the menu
3. A dialog opens

### Dialog Operations

1. **Select a preset** (optional): Choose a preset from the dropdown at the top
2. **Edit in the editor** (optional): Edit the template in the left editor
3. **Click the execute button**: Processing starts sequentially for all chunks
4. **Review results**: Suggested tags for each prompt appear in the center list
5. **Select apply/skip**: Choose "Apply" or "Skip" for each prompt
6. **Apply**: Click the "Apply All" button to batch apply selected tags

### Dialog Layout

The dialog has a 3-panel layout:

- **Left (Editor)**: Display and edit preset code
- **Center (Chunk List)**: Checked prompts list and status
- **Right (Tag Preview)**: Suggested tag list for selected prompt

### Processing Status
- Processing progress is shown in the status bar
- Processing can be cancelled midway
- Success/failure counts are displayed on completion

## Notes
- When calling an AI API within a programmable block, the [API Key Settings](../../../GlobalSettings/04-Menu/09-API Key Settings.md) corresponding to the AI being used is required
- When using [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md), the server must be running
- Not available when no prompts are checked
- Processing runs sequentially, so it takes time when there are many prompts
- You can select apply/skip individually before batch applying

### How Editor Content Is Processed

The text entered in the editor is used directly as output.

- The text in the editor is used as-is as the result
- If a [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) (`@@@_..._@@@`) is included, that portion is replaced with the block's execution result, and the surrounding text remains unchanged
- It also works as plain text without using programmable blocks
- The final text is split by **commas or newlines**, and each part is recognized as a tag

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
- [Check State](../../01-Basics/01-Concepts/01-Understanding Check State.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [Suggest Tags with AI](../01-Selected/08-Suggest Tags with AI.md)
- [Bulk Suggest Names with AI](06-Bulk Suggest Names with AI.md)
- [Tag Manager](../../../GlobalSettings/04-Menu/06-Tag Manager.md)
- [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
