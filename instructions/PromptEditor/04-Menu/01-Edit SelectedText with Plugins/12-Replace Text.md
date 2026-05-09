# Replace Text

**Replace Text**

## What It Does

Performs batch text replacement within selected text using search and replacement strings specified in a dialog.

## Important

For text replacement within the PromptEditor, using **PromptEditor > Replace** (Ctrl+H) is recommended. The Replace Text plugin is intended for batch processing (bulk replacement across multiple prompts) via **PromptTree > Checked > Edit Prompt Content with Plugins**.

## How to Use

1. Select the text to replace
2. Select **Edit SelectedText with Plugins > Replace Text** from the menu
3. A replacement dialog appears
4. Enter the following:
   - **Search**: String to search for
   - **Replace**: Replacement string
   - **Use Regex**: Check to use regular expressions
5. Click **OK** to execute the replacement

## Example

- Search: `red` / Replace: `blue`
- Input: `red hair, red eyes`
- Output: `blue hair, blue eyes`

## Notes

- All matching locations within the selected text are replaced
- In regex mode, more flexible pattern matching is possible

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Replace](../08-Replace.md)
