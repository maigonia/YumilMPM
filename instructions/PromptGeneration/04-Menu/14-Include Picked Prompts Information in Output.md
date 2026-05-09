# Include Picked Prompts Information in Output

**Include Picked Prompts Information in Output**

## When to Use

- When you want to record which prompts were selected in the generation result
- When you want to analyze or reproduce generation results later
- When you want to store selection information as metadata

## What It Does

Configures whether to include metadata about picked (selected) prompts in generation results in JSON format. When checked, information about which prompts were selected from which categories is added.

## How to Use

1. Select **PromptGeneration > Include Picked Prompts Information in Output** from the menu
2. Toggle with the checkmark on/off

## Notes

- Metadata is output in JSON format
- Useful for reproducing and analyzing generation results
- Recommended to disable when sending directly to image generation AI

## Related

- [Pick](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/03-Pick.md)
- [Auto-save prompts to text files](10-Auto-save%20prompts%20to%20text%20files.md)
- [Once Generation](01-Once%20Generation.md)
