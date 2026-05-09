# LM Studio

## What Is It

LM Studio is an application for running AI language models on your local PC. It integrates with LM Studio to perform AI text processing.

## Uses in This App

- Edit and transform prompt text using AI
- Automatically generate prompts using AI
- Analyze image content with AI to generate tags (Vision-capable models)

## Templates and Presets

Integration with LM Studio involves two configuration concepts:

- **Preset**: A set of AI behavior parameters (Temperature, Max Tokens, etc.). Use different presets for different purposes

- **Template**: A saved combination of a preset and an instruction for the AI. Saving frequently used instructions as templates eliminates the need to type them each time

## Prerequisites

- LM Studio must be running locally
- A model must be loaded in LM Studio
- Default endpoint is `http://localhost:1234/v1/chat/completions`

## Related

- [LM Studio Settings](../04-Menu/04-LM Studio/01-Settings.md)
- [LM Studio Edit](../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/13-LMStudio Edit.md)
- [Add From LM Studio](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/20-Add from LM Studio.md)
- [env.LMEDIT](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md)
- [Suggest Name with AI](../../PromptTree/04-Menu/01-Selected/09-Suggest Name with AI.md)
- [Suggest Tags with AI](../../PromptTree/04-Menu/01-Selected/08-Suggest Tags with AI.md)
- [Bulk Suggest Names with AI](../../PromptTree/04-Menu/05-Checked/06-Bulk Suggest Names with AI.md)
- [Bulk Suggest Tags with AI](../../PromptTree/04-Menu/05-Checked/05-Bulk Suggest Tags with AI.md)
- [Plugin](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
