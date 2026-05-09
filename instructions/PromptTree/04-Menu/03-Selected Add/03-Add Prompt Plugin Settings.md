# Add Prompt Plugin Settings

**Add Prompt Plugin Settings**

## When to Use

- When you want to organize the items displayed in the **PromptTree > Selected: Add** menu
- When you want to hide unused add methods to simplify the menu
- When you want to disable specific add methods to prevent accidental operations

## What Are Add Prompt Plugins

In this application, the various methods for adding prompts are called "Add Prompt Plugins." For example:

- **Add Child**: Add an empty child prompt under the selected prompt
- **Add from Clipboard (Lines)**: Split clipboard text by lines and add
- **Add from File System**: Import prompts from folder structure
- **Add from WD14**: Extract tags from images using WD14 Tagger and add
- **Add from LM Studio**: Generate prompts using LM Studio

These plugins appear in the **PromptTree > Selected: Add** submenu.

## What It Does

Configure which plugins to display in the menu. Unchecked plugins are hidden from the menu.

## How to Use

1. Select **PromptTree > Selected: Add > AddPromptPlugin Settings** from the menu
2. A dialog opens showing a list of available plugins
3. You can view information about each plugin:
   - **Plugin name**: The name shown in the menu
   - **Plugin ID**: Internal identifier
   - **Description**: What the plugin does
4. Check the plugins you want to use
5. Click **OK** to save

## Dialog Buttons

- **Select All**: Enable all plugins
- **Deselect All**: Disable all plugins
- **Reset to Default**: Restore to initial settings
- **Cancel**: Discard changes and close
- **OK**: Save settings and close

## Available Plugins List

| Plugin Name | Description |
| --- | --- |
| Add Child | Add an empty prompt as a child of the selected prompt |
| Add Child Group | Add a group as a child of the selected prompt |
| Add with Custom Name | Add a sibling prompt with a specified name |
| Add Sibling | Add at the same level as the selected prompt |
| Add Clone | Duplicate the selected prompt as a sibling |
| Add Root Group | Add a prompt at the root level |
| Add from Clipboard (Lines) | Split clipboard text by lines and add as children |
| Add from Clipboard (Whole) | Add entire clipboard content as one child prompt |
| Add from Clipboard (Tags) | Extract tags from clipboard and add as children |
| Add from Text File (Lines) | Split text file by lines and add |
| Add from Text File (Whole) | Add entire text files as child prompts |
| Add from Civitai URL | Download model from Civitai URL and add |
| Add from File System | Import prompts from folder/file structure |
| Add from File System (Quick) | Import from file system using previous settings |
| Add from WD14 | Extract tags from images using WD14 Tagger and add |
| Add from LM Studio | Generate prompts using LM Studio |

## Notes

- Settings are reflected in the menu immediately
- Settings apply to the entire application, not per project

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Plugin](01-Plugin/README.md)
- [Add From File System](01-Plugin/13-Add from File System.md)
- [Add From LM Studio](01-Plugin/20-Add from LM Studio.md)
- [Add From WD14](01-Plugin/19-Add from WD14.md)
