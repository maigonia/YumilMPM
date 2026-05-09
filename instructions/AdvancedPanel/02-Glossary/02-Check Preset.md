# Check Preset

## Overview

A Check Preset is a complete snapshot of the "check state" across the entire project.

By simply clicking a saved preset, you can restore the check state of all categories at once.

## Saved Information

| Item | Content |
| ---- | ------- |
| Preset name | User-assigned name |
| Description | Optional notes |
| Checked prompts | List of checked prompts across all categories |
| Category generation state | "Generation enabled/disabled" state for each category |
| Created/updated date | Automatically recorded |

## Difference from [Favorite List](03-Favorite List.md)

|          | Check Preset | Favorite List |
| -------- | ------------ | ------------- |
| Scope | Entire project (all categories) | Single category only |
| Scope level | Global | Category |
| On apply | Overwrites check state of all categories | Toggles checks for that category |
| Use case | Switching entire work mode | Managing combinations within a category |

## Cannot Be Used as [CategoryIdentifer](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) Parameter

Unlike FavoriteList and FavoriteQuery, CheckPreset cannot be used as a [CategoryIdentifer](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) parameter.

## Related

- [Check Presetsタブ](../01-Basics/03-Check Presets Tab.md)
- [Favorite List](03-Favorite List.md)
- [Advanced Panel](../01-Basics/07-What Is Advanced Panel.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md)
- [Save Current State](../04-Menu/08-Check Presets/01-Save Current State.md)
- [Workflow Switching](../03-Tips/03-Switching Work Modes with Check Presets.md)
