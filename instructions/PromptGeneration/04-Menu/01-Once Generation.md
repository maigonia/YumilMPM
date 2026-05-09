# Once Generation

**Once Generation**

## When to Use

- When you want to generate a prompt just once
- When you want to check the generation result
- When you want to manually generate a prompt

## What It Does

Generates a prompt once and outputs it as a file to the Prompt folder (if enabled).

## Processing

Based on the [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md) of the selected category, [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)s and [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)s within the template are replaced with actual values, and the completed prompt is output.

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

- [Generation](../01-Basics/03-About%20Prompt%20Generation.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Result Window](../01-Basics/04-Result%20Window.md)
- [Stop](04-Stop.md)
- [Timer Generation Start](03-Timer%20Generation/01-Timer%20Generation%20Start.md)
- [Start On Demand](02-Generation%20On%20Demand/01-Start%20On%20Demand.md)
- [Final Edit](../../AdvancedPanel/02-Glossary/05-Final%20Edit.md)
- [Show ResultWindow After Generation](07-Show%20ResultWindow%20After%20Generation.md)
- [Auto-Send Result to Clipboard](11-Auto-Send%20Result%20to%20Clipboard.md)
- [Auto-save prompts to text files](10-Auto-save%20prompts%20to%20text%20files.md)
- [Generation Rules](../../PromptTree/03-Tips/02-Changing%20Generation%20Rules.md)
