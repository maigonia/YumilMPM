# About Prompt Generation

Basically, it "randomly selects and outputs one checked prompt from the PromptTree of each [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md)."
Prompts are output for each [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md).

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

Three generation modes are available for different use cases. See [Generation Modes](01-Generation Modes.md) for details.

## Related

- [Generation](03-About Prompt Generation.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output Category.md)
- [Check State](../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category Template.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
- [Generation Modes](01-Generation Modes.md)
- [Generation Queue](../04-Menu/05-Generation Queue/README.md)
- [Result Window](04-Result Window.md)
- [Once Generation](../04-Menu/01-Once Generation.md)
- [Timer Generation Start](../04-Menu/03-Timer Generation/01-Timer Generation Start.md)
- [Start On Demand](../04-Menu/02-Generation On Demand/01-Start On Demand.md)
- [Final Edit](../../AdvancedPanel/02-Glossary/05-Final Edit.md)
