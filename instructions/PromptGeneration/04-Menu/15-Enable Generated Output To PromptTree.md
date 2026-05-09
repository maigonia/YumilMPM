# Enable Generated Output To PromptTree

**Enable Generated Output To PromptTree**

## When to Use

- When you want to automatically add generated prompts to the prompt tree
- When you want to save and reuse generation results as new prompts
- When you want to edit generated prompts later

## What It Does

Configures whether generation results are automatically added to the prompt tree after prompt generation. When checked, generated prompts are added as new chunks to the tree.

## How to Use

1. Select **PromptGeneration > Enable Generated Output To PromptTree** from the menu
2. Set the output destination with **PromptTree > Selected: Add > Add From Generated Output**
3. Toggle with the checkmark on/off

## Notes

- A separate output destination must be configured in the **Add From Generated Output** settings dialog
- During mass generation, the tree may grow large. Adjust the maximum output count in the **Add From Generated Output** settings dialog

## Related

- [PromptTree](../../PromptTree/01-Basics/03-Prompt Tree Overview.md)
- [Add From Generated Output](../../PromptTree/04-Menu/03-Selected Add/02-Add From Generated Output.md)
- [Once Generation](01-Once Generation.md)
- [env.OUTPUT](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/09-env.OUTPUT.md)
