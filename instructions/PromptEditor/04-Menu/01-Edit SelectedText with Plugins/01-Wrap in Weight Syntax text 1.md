# Convert to Weight Format

**Wrap in Weight Syntax (text:1)**

## What It Does

Converts selected text to weight format `(text:1)`.

## How to Use

1. Select the text you want to weight
2. Select **Edit SelectedText with Plugins > Wrap in Weight Syntax (text:1)** from the menu
3. The selected text is converted to `(selectedText:1)` format

## Example

- Input: `red hair`
- Output: `(red hair:1)`

## Notes

- The weight value `:1` can be manually edited after conversion (e.g., `1.2`, `0.8`, etc.)
- Text already in `(text:1)` format is not converted

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
