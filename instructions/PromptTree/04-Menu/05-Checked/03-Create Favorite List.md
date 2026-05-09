# Create Favorite List

**Create Favorite List**

## When to Use

- When you want to save frequently used prompt combinations
- When you want to group specific prompts for quick recall
- When you want to use it as a [filter](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md) condition for [CategoryIdentifier](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)

## What It Does

Creates a new **favorite list** from the checked prompts. The created list can be accessed from the "Favorite List" tab in the [Advanced Panel](../../../AdvancedPanel/01-Basics/07-What%20Is%20Advanced%20Panel.md).

## What Is a Favorite List

A favorite list is a group of prompts that can be created **per category**.

- Saves a list of prompt IDs
- Managed with a name
- Quick ON/OFF with checkboxes

## How to Use

1. Check the prompts you want to add to favorites
2. Select **PromptTree > Checked > Create Favorite List** from the menu
3. Enter a list name in the dialog
4. Click **Create**

After creation, it appears in the "Favorite List" tab of the [Advanced Panel](../../../AdvancedPanel/01-Basics/07-What%20Is%20Advanced%20Panel.md).

## How to Use Favorite Lists

### Accessing from the Advanced Panel

1. Open the [Advanced Panel](../../../AdvancedPanel/01-Basics/07-What%20Is%20Advanced%20Panel.md)
2. Select the "Favorite List" tab
3. Turn ON the list's checkbox
4. The prompts in the list become checked

### Additive/Subtractive Behavior

Favorite lists work in an **additive/subtractive** manner:

- **ON**: Prompts in the list are **added** to the current checks
- **OFF**: Prompts in the list are **removed** from the current checks

Multiple lists can be used in combination.

### Using with the Filter Command

Can be specified as a parameter for the [CategoryIdentifier](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)'s [filter](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md) command:

```
@@@_Character.Filter(favoriteList=Main Characters)_@@@
```

This makes only the prompts in the favorite list "Main Characters" the output target.

## Difference from Check Presets

The [Advanced Panel](../../../AdvancedPanel/01-Basics/07-What%20Is%20Advanced%20Panel.md) has a similar feature called "Check Preset," but it works differently.

**Favorite List**:
- **Scope**: Per category
- **Saved data**: Prompts only
- **Behavior**: Additive/subtractive
- **When ON**: Added to current checks
- **When OFF**: Removed from current checks
- **Use case**: Grouping prompts
- **Use with Filter**: Possible

**Check Preset**:
- **Scope**: Global (all categories)
- **Saved data**: Prompts + category tree
- **Behavior**: Full replacement
- **When ON**: Completely replaces current checks
- **When OFF**: (No effect)
- **Use case**: Saving entire workflow state
- **Use with Filter**: Not possible

### Usage Examples

- **Favorite List**: "Background series," "Character A related," "Quality tags" — groups used in combination
- **Check Preset**: "Illustration settings complete," "Photo settings complete" — saving complete state of both categories and prompts

## Notes

- Not available when no prompts are checked
- When a prompt is deleted, it is automatically removed from favorite lists
- Lists can be edited and deleted from the Advanced Panel's right-click menu

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [Check State](../../01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [PromptTree](../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [Favorite List](../../../AdvancedPanel/02-Glossary/03-Favorite%20List.md)
- [Advanced Panel](../../../AdvancedPanel/01-Basics/07-What%20Is%20Advanced%20Panel.md)
- [Filter](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md)
