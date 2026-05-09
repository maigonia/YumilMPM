# Understanding Check State

## What Is Check State

Check state is a feature that specifies whether to include a prompt during prompt [Generation](../../../PromptGeneration/01-Basics/03-About Prompt Generation.md).

Each prompt has a checkbox that can be toggled on/off.

## Why Are Checks Needed?

Because you want to manage many prompt materials as a library while selecting only what's needed for each generation.

- Temporarily exclude materials without deleting them
- Try different combinations from the same material set
- Save and reuse states (favorite lists, check presets)

## What Check State Means

- **Checked ☑**: Included in generation processing
- **Unchecked ☐**: Excluded from generation processing

**Note**: Not all checked prompts are output. By default, one is randomly selected from checked prompts. By changing the generation rule, you can also output all of them. See [Generation Rules](../../03-Tips/02-Changing Generation Rules.md) for details.

## How to Operate Checks

### Individual Operations

- **Click checkbox**: Toggle on/off
- **Shift+Click**: Range check from last clicked position to current position
- **Ctrl+Click**: Exclusive check (uncheck all in the category, then check only the clicked prompt)

### Batch Operations (Control Bar)

- **Check All**: Check everything
- **Uncheck All**: Uncheck everything
- **Check All Leaves**: Check only leaf nodes

### Operations Based on Selected Node

Operate from right-click → **Selected: Check/Uncheck** or from the [Control Bar](../04-Panel/01-Control Bar Operations.md) based on the selected prompt.

- **Child Prompts**: Direct children
- **Sibling Prompts**: Same level siblings
- **Descendants Prompts**: All descendants
- **Leaf Prompts**: Only leaf descendants

### Operations on Search Results

For filtered search results (from **PromptTree > Search Panel** or [Search Panel](../04-Panel/02-Search Panel Operations.md) buttons):

- **Check Filtered Results**: Check all filtered results
- **Uncheck Filtered Results**: Uncheck filtered results
- **Check Filtered Leaves**: Check only filtered leaves

## Saving Check State

Check state can be saved in two ways:

### Favorite Lists

- Saves a list of checked prompt IDs within the current category
- Applied additively (added to existing checks)
- Convenient for saving material combination patterns

### Check Presets

- Batch saves the check state of all categories
- Applied by replacement (replaces existing checks)
- Convenient for recording the entire project state

## Related

- [Prompt](03-What Is a Prompt.md)
- [Check State](01-Understanding Check State.md)
- [PromptTree](../03-Prompt Tree Overview.md)
- [Output Category](../../../CategoryTree/02-Glossary/01-Output Category.md)
- [Generation](../../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Check All](../../04-Menu/06-Check All.md)
- [UnCheck All](../../04-Menu/07-Uncheck All.md)
- [Check All Leaves](../../04-Menu/08-Check All Leaves.md)
- [Favorite List](../../../AdvancedPanel/02-Glossary/03-Favorite List.md)
- [Check Preset](../../../AdvancedPanel/02-Glossary/02-Check Preset.md)
- [Control Area](../04-Panel/01-Control Bar Operations.md)
- [Selecting](../02-Operations/04-Selecting Generation Targets.md)
