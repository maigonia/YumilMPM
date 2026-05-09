# Checked Tab

This is the checked prompts list tab, displayed in Category scope.

## When Is It Useful

- When you want to see which prompts are checked in the current category
- When you want to quickly operate on checked prompts from a list
- When you want to apply plugin processing to checked prompts in bulk

## Displayed Information

Each prompt is shown on one line with the following information:

- Checkbox (click to uncheck)
- Icon (folder or file)
- Parent folder name (part of the path)
- Prompt name

Hovering shows the full path and tag information in a tooltip. Prompts with tags display the tag count on the right side when hovered.

The list is sorted by path order.

## Operations

| Operation | Result |
|-----------|--------|
| Click a prompt | Jump to the corresponding prompt in PromptTree |
| Click a checkbox | Uncheck that prompt |
| Right-click | Uncheck menu |

## Buttons

| Button | Function |
|--------|----------|
| **Clear All** | Uncheck all prompts in the current category (does not affect other categories) |
| **Bulk Edit** | Open a dialog to apply plugin processing to checked prompts in bulk |

## Bulk Edit

You can apply plugin processing to the text content of checked prompts in bulk.

1. Click the **Bulk Edit** button
2. A preview dialog opens where you select the plugin to apply
3. Preview the before and after for each prompt
4. Click "Apply" to apply in bulk

## Related

- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Advanced Panel](07-What Is Advanced Panel.md)
- [Favorite List](../02-Glossary/03-Favorite List.md)
- [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit Prompt Content with Plugins.md)
- [Bulk Suggest Names with AI](../../PromptTree/04-Menu/05-Checked/06-Bulk Suggest Names with AI.md)
- [Bulk Suggest Tags with AI](../../PromptTree/04-Menu/05-Checked/05-Bulk Suggest Tags with AI.md)
