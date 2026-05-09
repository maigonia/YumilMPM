# Output Category

## Overview

An output category is a category that is included as an output target during prompt generation. It is configured using the checkbox to the left of the category name.

- **Checked**: Output category (included in generation)
- **Unchecked**: Non-output category (excluded from generation)

## Conditions for Generation

For a prompt to actually be generated, it must satisfy **both conditions**:

1. The category must be an output category (category checkbox is ON)
2. The prompt must be checked in the PromptTree

If only one condition is met, it will not be generated.

## Example

If you have three categories: "Character", "Background", and "Style":

- All three checked → Generate from all categories
- Only "Character" checked → Generate from Character only
- All unchecked → Nothing is generated

## Category Name Colors

The category name color indicates its state:

| Color | Meaning |
|-------|---------|
| **Green** | Output category + has checked prompts |
| **Red** | Output category + no checked prompts |
| **Blue** | Non-output category + has checked prompts |
| **Gray** | Non-output category + no checked prompts |

## Uses of Non-Output Categories

Non-output categories are not included in normal generation, but they can be referenced as data sources from [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) and programmable blocks. This is useful for organizing prompts that you don't normally output but want to use under specific conditions.

## How to Toggle

- **Click**: Click the checkbox to toggle
- **Shift+Click**: Select a range of multiple categories and toggle together
- **Ctrl+Click**: Exclusive check (turn OFF all other categories, turn ON only the clicked one)

## Related

- [Category](../../AdvancedPanel/01-Basics/01-Category%20Template%20Tab.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [PromptTree](../../PromptTree/01-Basics/03-Prompt%20Tree%20Overview.md)
