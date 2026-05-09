# Remove Duplicate Tags

**Remove Duplicate Tags**

## What It Does

Removes duplicate tags from a comma-separated tag list. Keeps only the first occurrence.

## How to Use

1. Select a tag list
2. Select **Edit SelectedText with Plugins > Remove Duplicate Tags** from the menu
3. Duplicate tags are removed

## Example

- Input: `1girl, red hair, blue eyes, 1girl, smile`
- Output: `1girl, red hair, blue eyes, smile`

## Notes

- Case insensitive (`Red Hair` and `red hair` are treated as the same tag)

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [Remove Duplicate Lines](05-Remove%20Duplicate%20Lines.md)
- [Normalize Prompt Format](04-Normalize%20Prompt%20Format.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
