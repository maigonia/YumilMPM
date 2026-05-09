# Add From Generated Output

**Add From Generated Output**

## When to Use

- When you want to reuse previously generated prompts
- When you want to save generation results as prompt material
- When prompt generation takes time due to AI usage
- When you want to generate a large number of prompts with [Timer Generation](../../../PromptGeneration/04-Menu/03-Timer%20Generation/README.md) and use them later with [Generation On Demand](../../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/README.md)

## What It Does

Sets the selected prompt as the "capture destination" for generated output. After setting, each time generation occurs from the specified [Output Category](../../../CategoryTree/02-Glossary/01-Output%20Category.md), the output is automatically added as a child prompt.

## How to Use

1. Select the prompt to be the capture destination
2. Select **PromptTree > Selected: Add > Add From Generated Output** from the menu
3. Select the [Output Category](../../../CategoryTree/02-Glossary/01-Output%20Category.md) to capture from in the dialog
4. Set the auto-stop count (0 = unlimited)
5. Click **OK**

## Important

**PromptGeneration > Enable Generated Output To PromptTree** must be enabled, or generated output will not be captured.

## Verifying After Setup

After setting up in the dialog, **Output Destination** appears at the bottom of the **Generation panel**. There you can:

- Check the capture destination prompt name
- Toggle **Enable Generated Output To PromptTree** on/off with a button

## Notes

- If there are no categories with generation enabled, no choices are shown
- If another node is already set, a warning is shown (the setting is overwritten)
- The auto-stop count is reset with a new session
- Clicking OK without selecting a category clears the setting

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [PromptTree](../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [Generation](../../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Once Generation](../../../PromptGeneration/04-Menu/01-Once%20Generation.md)
- [Enable Generated Output To PromptTree](../../../PromptGeneration/04-Menu/15-Enable%20Generated%20Output%20To%20PromptTree.md)
- [env.OUTPUT](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/09-env.OUTPUT.md)
