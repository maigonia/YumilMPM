# Escape as JS String

**Escape as JS String**

## What It Does

Escapes text to be safely used as a JavaScript string. Useful when you want to treat text as a string in a Programmable Block.

## How to Use

1. Select the text to escape
2. Select **Edit SelectedText with Plugins > Escape as JS String** from the menu
3. Special characters are escaped

## Escaped Characters

| Original | Converted |
|----------|-----------|
| `"` | `\"` |
| `'` | `\'` |
| `\\` | `\\\\` |
| Newline | `\n` |
| Tab | `\t` |

## Example

- Input: `She said "hello"`
- Output: `She said \\"hello\\"`

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
