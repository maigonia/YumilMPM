# When Add Plugin Is Difficult

## Adding Prompts Created Externally

There are cases where MPM's standard prompt addition methods (Add Plugin) are difficult to use:

- Long prompts created with **AI services like ChatGPT**
- Prompts generated from **ComfyUI**'s complex workflows
- Other prompts created with external tools or services

For such prompts, it's more efficient to output them as text files first rather than entering them directly into MPM.

## Steps

### 1. Prepare Text Files

Create prompts using external services or tools and save them as text files (.txt) in a folder.

Write one prompt per file. The filename becomes the prompt name.

### 2. Bulk Add with Add from Text File (Whole)

Right-click the parent prompt where you want to add them and select **Add from Text File (Whole)**.

Specify a folder, and all text files in the folder will be added as child prompts at once.

## For More Complex Import Configurations

If your folder and file structure is already defined, you can use [Add from File System](../04-Menu/03-Selected%20Add/01-Plugin/13-Add%20from%20File%20System.md) for more flexible imports. It allows you to import folder hierarchies directly as tree structures and specify processing methods for each file type.

Frequently used settings can be saved as presets, making it easy to reuse the same import configuration repeatedly.

## For Importing an Entire Tree Structure (For Technical Users)

If you can generate JSON files with scripts or external tools, [Add from JSON File](../04-Menu/03-Selected%20Add/01-Plugin/11-Add%20from%20JSON%20File.md) is available. A single file with nested `children` can import the tree structure, tags, memos, and image paths all at once.

This is useful when you want to programmatically shape large numbers of prompts before importing, or when automating exports from other tools.

## Key Points

- As long as you can output to text files, **prompts from any external service can be added to the tree universally**
- Large numbers of prompts can be imported in bulk, eliminating manual input
- Filename = prompt name, so using descriptive names makes organization easier

## Related

- [Add Plugin](../04-Menu/03-Selected%20Add/03-Add%20Prompt%20Plugin%20Settings.md)
- [Add from Text File (Whole)](../04-Menu/03-Selected%20Add/01-Plugin/10-Add%20from%20Text%20File%20Whole.md)
- [Add from File System](../04-Menu/03-Selected%20Add/01-Plugin/13-Add%20from%20File%20System.md)
- [Add from File System - Preset Management](../04-Menu/03-Selected%20Add/01-Plugin/17-Add%20from%20File%20System%20-%20Preset%20Management.md)
- [Add from JSON File](../04-Menu/03-Selected%20Add/01-Plugin/11-Add%20from%20JSON%20File.md)
- [PromptTree](../01-Basics/03-Prompt%20Tree%20Overview.md)
