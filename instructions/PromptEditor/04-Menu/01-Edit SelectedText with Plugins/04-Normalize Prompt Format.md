# Normalize Prompt Format

**Normalize Prompt Format**

## What It Does

Unifies the prompt format for StableDiffusion. Adds a space after commas, cleans up extra whitespace and duplicate commas.

## How to Use

1. Select the text to normalize
2. Select **Edit SelectedText with Plugins > Normalize Prompt Format** from the menu
3. The format is unified

## Example

- Input: `red hair,blue eyes,  smile,,`
- Output: `red hair, blue eyes, smile,`

## Processing Details

- Adds one space after commas
- Removes extra whitespace
- Removes empty tags (comma-only parts)
- Adds a trailing comma to each line
- Preserves the `BREAK` keyword as-is
- Auto-fixes minor errors in LoRA notation `<lora:name:weight>`

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [Remove Duplicate Tags](06-Remove%20Duplicate%20Tags.md)
- [Trim Whitespace](02-Trim%20Whitespace%20Each%20Line.md)
