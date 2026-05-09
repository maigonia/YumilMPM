# About Prompt Generation

Basically, it "randomly selects and outputs one checked prompt from the PromptTree of each [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)."
Prompts are output for each [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md).

## Basic Flow

1. **Choose output categories** — Check the categories you want to output in the CategoryTree
2. **Choose prompts** — Check the prompts you want as output candidates in the PromptTree
3. **Execute generation** — Execute **PromptGeneration > Once Generation** from the menu
4. **Receive results** — The generated prompt is displayed in the result window

A prompt is randomly selected from the category's prompts with each generation, so a different prompt is output each time.

## How to Receive Generation Results

Generated prompts can be received in the following ways depending on settings:

- **Result Window** — The prompt is displayed on screen (enabled by default)
- **Clipboard** — If enabled, automatically copied for immediate pasting
- **Text file** — If enabled, saved as a file in the prompt folder
- **API Server** — For On Demand Generation, text is sent directly to external applications

## 3 Generation Modes

Three generation modes are available for different use cases. See [Generation Modes](01-Generation%20Modes.md) for details.

## Related

- [Generation](03-About%20Prompt%20Generation.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Generation Modes](01-Generation%20Modes.md)
- [Generation Queue](../04-Menu/05-Generation%20Queue/README.md)
- [Result Window](04-Result%20Window.md)
- [Once Generation](../04-Menu/01-Once%20Generation.md)
- [Timer Generation Start](../04-Menu/03-Timer%20Generation/01-Timer%20Generation%20Start.md)
- [Start On Demand](../04-Menu/02-Generation%20On%20Demand/01-Start%20On%20Demand.md)
- [Final Edit](../../AdvancedPanel/02-Glossary/05-Final%20Edit.md)
