# Same CategoryIdentifier Output Same Result

**Same CategoryIdentifier Output Same Result**

## When to Use

- When the same [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) is used in multiple places and you want all of them to output the same result
- When you want to maintain character consistency (e.g., same hair color in multiple places)

## What It Does

Configures whether all instances of the same [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) output the same result when used multiple times.

**Example**: When `@@@_Character1_@@@` appears twice

- Enabled: Both output the same result (e.g., both "blonde hair")
- Disabled: Each outputs a different result (e.g., "blonde hair" and "black hair")

## How to Use

1. Select **PromptGeneration > Same CategoryIdentifier Output Same Result** from the menu
2. Toggle with the checkmark on/off

## Notes

- Enabled by default
- Useful for maintaining consistency across multiple attributes of a character
- Disable when you intentionally want different results

## Related

- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Once Generation](01-Once Generation.md)
- [env.SEED](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/12-env.SEED.md)
