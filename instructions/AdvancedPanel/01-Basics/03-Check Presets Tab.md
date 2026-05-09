# Check Presets Tab

A tab for managing [Check Preset](../02-Glossary/02-Check%20Preset.md)s.
This is displayed in Global scope for saving and restoring the check state of the entire project.

## When Is It Useful

- When you want to switch between multiple "work modes" (e.g., anime-style prompt set ↔ photo-style prompt set)
- When you want to reproduce a specific check state later
- When you want to return to a previous state after experimenting with various check states

## Basic Usage

### Saving a Preset

1. Set the check state you want to save in the PromptTree (across all categories)
2. Click the **Save Current State** button
3. The preset editing dialog opens
4. Enter a preset name and description, then click "Save"

The following information is saved:

- Checked prompts across all categories
- "Generation enabled/disabled" state for each category

### Applying a Preset

Click a preset in the list to apply it.

- If there are currently checked prompts, a confirmation dialog appears ("This will replace all current check states. Continue?")
- If there are no currently checked prompts, the preset is applied immediately

Applying a preset overwrites the check state of all categories with the preset's content.

### Managing Presets

Right-click a preset to display the management menu.

| Menu | Function |
| ---- | -------- |
| Save Current State | Create a new preset with the current check state |
| Apply | Apply the preset |
| Edit | Edit preset name and description |
| Delete | Delete the preset (with confirmation dialog) |
| Move Up / Move Down | Change display order |

### Keyboard Navigation

- **↑ / ↓**: Navigate within the list
- **Enter**: Apply the selected preset

## Display Information

Each preset shows the following:

- Preset name
- Number of saved prompts (e.g., 42 chunks)
- Updated date
- Description (if configured)

## Difference from [Favorite List](../02-Glossary/03-Favorite%20List.md)

Check Presets manages the check state of the **entire project** at once. To manage prompt combinations within a single category, use [Favorite List](../02-Glossary/03-Favorite%20List.md) in Category scope.

## Related

- [Check Preset](../02-Glossary/02-Check%20Preset.md)
- [Advanced Panel](07-What%20Is%20Advanced%20Panel.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Favorite List](../02-Glossary/03-Favorite%20List.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Save Current State](../04-Menu/08-Check%20Presets/01-Save%20Current%20State.md)
