# Remove Tags at Cursor

**Remove Tags at Cursor**

## What It Does

Removes the tag at the cursor position, or tags within the selection range. Useful when you want to quickly remove a specific tag from a comma-separated tag list.

## How to Use

### Remove Tag at Cursor Position

1. Place the cursor on the tag you want to remove
2. Select **Edit SelectedText with Plugins > Remove Tags at Cursor** from the menu
3. The tag at the cursor position is removed

### Remove Tags in Selection Range

1. Select a range containing the tags to remove
2. Select **Edit SelectedText with Plugins > Remove Tags at Cursor** from the menu
3. Tags within the selection range are removed

## Example

Text: `1girl, red hair, blue eyes, smile`

- Place cursor on `red hair` and execute → `1girl, blue eyes, smile`

## Notes

- Tags are recognized as comma-separated elements
- Parts enclosed in parentheses `()` or curly braces `{}` are correctly recognized as single tags

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
