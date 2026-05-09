# Once Generation

**Once Generation**

## When to Use

- When you want to generate a prompt just once
- When you want to check the generation result
- When you want to manually generate a prompt

## What It Does

Generates a prompt once and outputs it as a file to the Prompt folder (if enabled).

## Processing

Based on the [Category Template](../../AdvancedPanel/02-Glossary/01-Category Template.md) of the selected category, [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)s and [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)s within the template are replaced with actual values, and the completed prompt is output.

## How to Use

1. Select a category
2. Select **PromptGeneration > Once Generation** from the menu
3. The prompt is generated
4. Depending on settings, the result is shown in the result window, copied to clipboard, or saved to a file

## Generation Result Destinations

Generated prompts are output to the following depending on settings:

- **Result Window**: When "Show ResultWindow After Generation" is ON
- **Clipboard**: When "Auto-Send Result to Clipboard" is ON
- **Text file**: When "Auto-save prompts to text files" is ON

## Notes

- Another generation cannot be started while one is in progress
- If the Category Template is in default state (not configured), one prompt is randomly selected from checked prompts
- If a Category Identifier is not found, it is output as-is

## Related

- [Generation](../01-Basics/03-About Prompt Generation.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category Template.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Result Window](../01-Basics/04-Result Window.md)
- [Stop](04-Stop.md)
- [Timer Generation Start](03-Timer Generation/01-Timer Generation Start.md)
- [Start On Demand](02-Generation On Demand/01-Start On Demand.md)
- [Final Edit](../../AdvancedPanel/02-Glossary/05-Final Edit.md)
- [Show ResultWindow After Generation](07-Show ResultWindow After Generation.md)
- [Auto-Send Result to Clipboard](11-Auto-Send Result to Clipboard.md)
- [Auto-save prompts to text files](10-Auto-save prompts to text files.md)
- [Generation Rules](../../PromptTree/03-Tips/02-Changing Generation Rules.md)
