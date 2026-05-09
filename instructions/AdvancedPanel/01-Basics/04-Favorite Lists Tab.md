# Favorite Lists Tab

A tab for managing [FavoriteList](../02-Glossary/03-Favorite List.md)s.
This is displayed in Category scope for saving and restoring prompt combinations.

## When Is It Useful

- When you want to save frequently used prompt combinations
- When you want to switch check states with a single click
- When you want to use multiple "prompt sets" within the same category

## Basic Usage

### Creating a List

1. Check the prompts you want to save in the PromptTree
2. Click the **Create New** button
3. Enter a list name and click "Create"

The currently checked prompts are saved as a list.

### Applying a List

Click a list's checkbox to batch-check the prompts in the list. Click again to uncheck them.

Multiple lists can be checked ON simultaneously. Prompts from each list are checked additively.

### Managing Lists

Right-click a list to display the management menu.

| Menu | Function |
| ---- | -------- |
| Edit | Change the list name |
| Delete | Delete the list (with confirmation dialog) |
| Move Up / Move Down | Change display order |

### Keyboard Navigation

- **↑ / ↓**: Navigate within the list
- **Enter**: Toggle check state of the selected list

## Difference from [Check Preset](../02-Glossary/02-Check Preset.md)

Favorite Lists manages prompt combinations **within a single category**. To save and restore the check state of the entire project, use [Check Preset](../02-Glossary/02-Check Preset.md) in Global scope.

## Related

- [Favorite List](../02-Glossary/03-Favorite List.md)
- [Advanced Panel](07-What Is Advanced Panel.md)
- [Check Preset](../02-Glossary/02-Check Preset.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Create Favorite List](../../PromptTree/04-Menu/05-Checked/03-Create Favorite List.md)
