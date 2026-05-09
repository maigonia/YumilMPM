# Favorite List

## Overview

A Favorite List stores a list of prompt IDs. By clicking the checkbox, you can batch check/uncheck the prompts in the list.

## Restoring Check State

Open the Advanced Panel, click the Category tab, and open the Favorite Lists panel.
A list of created FavoriteLists is displayed. Click each item to toggle its check state on and off.

## Saved Information

| Item | Content |
| ---- | ------- |
| List name | User-assigned name |
| Prompt ID list | List of prompt IDs to check |

## Behavior

- **Check ON**: All prompts in the list become checked
- **Check OFF**: All prompts in the list become unchecked
- Multiple lists can be checked ON simultaneously, each operating additively

## Scope

Favorite List is a Category-scope feature, with each category having its own lists.

To save the check state of the entire project, use [Check Preset](02-Check Preset.md).

## Operations

- **Left-click (checkbox)**: Toggle check state
- **Right-click**: Edit, delete, reorder

## Can Be Set as a Parameter for [CategoryIdentifer](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)'s [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) Command.

(Example) @@@_Backgrounds.Filter(favoritelist=indoors)_@@@

## Related

- [Favorite Listsタブ](../01-Basics/04-Favorite Lists Tab.md)
- [Check Preset](02-Check Preset.md)
- [Advanced Panel](../01-Basics/07-What Is Advanced Panel.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Create Favorite List](../../PromptTree/04-Menu/05-Checked/03-Create Favorite List.md)
- [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Workflow Switching](../03-Tips/03-Switching Work Modes with Check Presets.md)
