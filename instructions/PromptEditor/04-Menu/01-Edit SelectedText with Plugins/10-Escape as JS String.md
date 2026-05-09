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

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [Programmable Block](../../02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
