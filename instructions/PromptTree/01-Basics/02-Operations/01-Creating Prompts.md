# Creating Prompts

## Overview

This explains how to create new prompts.

From basic adding to importing from external sources, there are various methods.

## Basic Add Methods

### 1. Header Add Button

Click the blue "+" button at the top of the panel to add a new prompt as a child of the selected prompt.

**Steps**:
1. Select the parent prompt (or select nothing to add at root)
2. Click the "+" button
3. Created with the name "new item"
4. Rename as needed (F2)

### 2. Add from Right-Click Menu

Right-click a prompt and select from the add menu.

- **Add Child**: Add a child prompt under the selected item
- **Add Child Group**: Add a group (folder) under the selected item
- **Add Sibling**: Add at the same level as the selected item
- **Add Root Group**: Add at root
- **Add Clone**: Create a copy of the selected item

### 3. Add with Custom Name

Using **Add with Custom Name**, you can specify the name at creation time.

**Steps**:
1. Right-click → **Selected: Add > Add with Custom Name**
2. Enter name in dialog
3. Confirm

## Adding from External Sources

### From Clipboard

- **Add from Clipboard (Lines)**: Split clipboard text by lines and add
- **Add from Clipboard (Whole)**: Add entire clipboard as one prompt
- **Add from Clipboard (Tags)**: Parse tag-format text and add

### From Files

- **Add from Text File (Lines)**: Split text file by lines and add
- **Add from Text File (Whole)**: Add entire file as one prompt
- **Add from File System**: Import including folder structure

### From AI and Services

- **Add from LM Studio**: Generate with LM Studio
- **Add from Civitai URL**: Get LoRA trigger words from Civitai model page
- **Add from WD14**: Extract from images with WD14 Tagger

## After Adding

Added prompts are automatically selected.

You can then continue with:
- **F2**: Rename
- **Edit in editor**: Enter content

## Notes

- Prompts with the same name cannot be created at the same level
- Some characters cannot be used in names (`/`, `\\`, etc.)
- Adding as a group gives it a green folder icon

## Related

- [Prompt](../01-Concepts/03-What Is a Prompt.md)
- [Hierarchy](../01-Concepts/02-Understanding Hierarchy.md)
- [PromptTree](../03-Prompt Tree Overview.md)
- [Add Root Group](../../04-Menu/09-Add Root Group.md)
- [Add Child](../../04-Menu/03-Selected Add/01-Plugin/01-Add Child.md)
- [Add Sibling](../../04-Menu/03-Selected Add/01-Plugin/04-Add Sibling.md)
- [Add Child Group](../../04-Menu/03-Selected Add/01-Plugin/02-Add Child Group.md)
- [Add Clone](../../04-Menu/03-Selected Add/01-Plugin/05-Add Clone.md)
- [Add From Clipboard](../../04-Menu/03-Selected Add/01-Plugin/06-Add from Clipboard Lines.md)
- [Add From Text File](../../04-Menu/03-Selected Add/01-Plugin/09-Add from Text File Lines.md)
- [Add From File System](../../04-Menu/03-Selected Add/01-Plugin/13-Add from File System.md)
- [Add From LM Studio](../../04-Menu/03-Selected Add/01-Plugin/20-Add from LM Studio.md)
- [Add From WD14](../../04-Menu/03-Selected Add/01-Plugin/19-Add from WD14.md)
- [Add From Civitai URL](../../04-Menu/03-Selected Add/01-Plugin/12-Add from Civitai URL.md)
