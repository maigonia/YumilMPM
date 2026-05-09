# Set Max Recursion Depth

**Set Max Recursion Depth**

## When to Use

- When you want to adjust the expansion depth of nested [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)s
- When you want to prevent infinite loops
- When you need deeper hierarchy prompt expansion

## What It Does

Sets the maximum depth for recursive expansion of [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)s. When one [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) contains another [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md), it is expanded up to the specified depth.

**Example**: With depth of 3

- Level 1: `{{Character}}` → `{{HairColor}}, {{EyeColor}}`
- Level 2: `{{HairColor}}` → `blonde`
- Level 3: Expansion ends

## How to Use

1. Select **PromptGeneration > Set Max Recursion Depth** from the menu
2. Enter the depth value
3. Click OK

## Notes

- The default value is sufficient for normal usage
- Setting the value too high may increase processing time
- This setting prevents infinite loops when circular references exist

## Related

- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Once Generation](01-Once%20Generation.md)
