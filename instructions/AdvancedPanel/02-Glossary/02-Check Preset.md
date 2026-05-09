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

## Difference from [Favorite List](03-Favorite%20List.md)

|          | Check Preset | Favorite List |
| -------- | ------------ | ------------- |
| Scope | Entire project (all categories) | Single category only |
| Scope level | Global | Category |
| On apply | Overwrites check state of all categories | Toggles checks for that category |
| Use case | Switching entire work mode | Managing combinations within a category |

## Cannot Be Used as [CategoryIdentifer](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) Parameter

Unlike FavoriteList and FavoriteQuery, CheckPreset cannot be used as a [CategoryIdentifer](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) parameter.

## Related

- [Check Presetsタブ](../01-Basics/03-Check%20Presets%20Tab.md)
- [Favorite List](03-Favorite%20List.md)
- [Advanced Panel](../01-Basics/07-What%20Is%20Advanced%20Panel.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Save Current State](../04-Menu/08-Check%20Presets/01-Save%20Current%20State.md)
- [Workflow Switching](../03-Tips/03-Switching%20Work%20Modes%20with%20Check%20Presets.md)
