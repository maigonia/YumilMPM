# Basic Workflow

This guide explains the basic workflow for using this app.

## Step 1: Create Categories

Create categories with **CategoryTree > [Add Root Category](../../CategoryTree/03-Menu/02-Add%20Root%20Category.md)**.

Categories are classifications for prompts. Examples:

- **Quality** — Quality-related prompts (masterpiece, best quality, ...)
- **Character** — Character traits (hair color, eye color, ...)
- **Background** — Background specifications (indoor, outdoor, ...)

## Step 2: Add Prompts

Select a category and add prompts from the prompt tree's right-click menu.

There are several ways to add prompts:

| Method | Description |
|--------|-------------|
| [Add Child](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/01-Add%20Child.md) | Add one at a time by entering a name |
| [Add From Clipboard Tags](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/08-Add%20from%20Clipboard%20Tags.md) | Bulk add tags from clipboard |
| [Add From Text File](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/09-Add%20from%20Text%20File%20Lines.md) | Bulk add from text files |
| [Add From File System](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/13-Add%20from%20File%20System.md) | Bulk add files from a folder |

## Step 3: Edit Prompt Content

Select a prompt in the PromptTree and its content appears in the [PromptEditor](../../PromptEditor/01-Basics/03-Prompt%20Editor.md) on the right. You can directly edit the prompt text here.

## Step 4: Check Prompts

Check the prompts you want to use. Click a prompt in the tree or press **Space** to toggle its check state.

Only checked prompts are used in generation.

## Step 5: Set Output Categories

Enable the [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md) setting for categories you want included in the generation result. Double-click a category name in the category tree to toggle output ON/OFF.

## Step 6: Generate

Run a single generation with **PromptGeneration > [Once Generation](../../PromptGeneration/04-Menu/01-Once%20Generation.md)**.

Checked prompts are combined per category, and the final prompt text is generated. Results are displayed in the [Result Window](../../PromptGeneration/01-Basics/04-Result%20Window.md).

## Related

- [About This App](03-About%20This%20App.md)
- [Menu System Guide](04-Menu%20System%20Guide.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
