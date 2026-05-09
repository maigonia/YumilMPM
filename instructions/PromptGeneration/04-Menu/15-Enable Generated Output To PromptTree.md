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

- [PromptTree](../../PromptTree/01-Basics/03-Prompt%20Tree%20Overview.md)
- [Add From Generated Output](../../PromptTree/04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md)
- [Once Generation](01-Once%20Generation.md)
- [env.OUTPUT](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/09-env.OUTPUT.md)
