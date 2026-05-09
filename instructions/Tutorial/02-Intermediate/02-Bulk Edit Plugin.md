# Bulk Edit Plugin

Apply text transformations to multiple checked prompts at once.

## Understanding with Examples

For example, if you have 100 LoRA prompts all containing duplicate tags:
- Before: `1girl, blonde hair, blue eyes, 1girl, smile`
- After: `1girl, blonde hair, blue eyes, smile`

Manually fixing 100 prompts is tedious, but with bulk edit:
1. Check all 100 prompts
2. Select "Remove Duplicate Tags" plugin
3. Preview and apply

This fixes all 100 prompts instantly.

## Access

`PromptTree > Right-click > Checked Prompts > Edit Prompt Content with Plugins`

## Available Plugins

- Remove duplicate lines/tags
- Trim whitespace
- Normalize format
- Edit with LMStudio AI (give AI instructions like "translate to Japanese" for batch processing)
- Search and replace
