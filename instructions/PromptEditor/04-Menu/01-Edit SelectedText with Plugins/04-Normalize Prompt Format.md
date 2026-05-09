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

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Remove Duplicate Tags](06-Remove Duplicate Tags.md)
- [Trim Whitespace](02-Trim Whitespace Each Line.md)
