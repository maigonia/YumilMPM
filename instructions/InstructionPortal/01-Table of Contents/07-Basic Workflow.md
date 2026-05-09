# Basic Workflow

This guide explains the basic workflow for using this app.

## Step 1: Create Categories

Create categories with **CategoryTree > [Add Root Category](../../CategoryTree/03-Menu/02-Add Root Category.md)**.

Categories are classifications for prompts. Examples:

- **Quality** — Quality-related prompts (masterpiece, best quality, ...)
- **Character** — Character traits (hair color, eye color, ...)
- **Background** — Background specifications (indoor, outdoor, ...)

## Step 2: Add Prompts

Select a category and add prompts from the prompt tree's right-click menu.

There are several ways to add prompts:

| Method | Description |
|--------|-------------|
| [Add Child](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/01-Add Child.md) | Add one at a time by entering a name |
| [Add From Clipboard Tags](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/08-Add from Clipboard Tags.md) | Bulk add tags from clipboard |
| [Add From Text File](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/09-Add from Text File Lines.md) | Bulk add from text files |
| [Add From File System](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/13-Add from File System.md) | Bulk add files from a folder |

## Step 3: Edit Prompt Content

Select a prompt in the PromptTree and its content appears in the [PromptEditor](../../PromptEditor/01-Basics/03-Prompt Editor.md) on the right. You can directly edit the prompt text here.

## Step 4: Check Prompts

Check the prompts you want to use. Click a prompt in the tree or press **Space** to toggle its check state.

Only checked prompts are used in generation.

## Step 5: Set Output Categories

Enable the [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md) setting for categories you want included in the generation result. Double-click a category name in the category tree to toggle output ON/OFF.

## Step 6: Generate

Run a single generation with **PromptGeneration > [Once Generation](../../PromptGeneration/04-Menu/01-Once Generation.md)**.

Checked prompts are combined per category, and the final prompt text is generated. Results are displayed in the [Result Window](../../PromptGeneration/01-Basics/04-Result Window.md).

## Related

- [About This App](03-About This App.md)
- [Menu System Guide](04-Menu System Guide.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md)
