# Set Max History Entries

**Set Max History Entries**

## When to Use

- When you want to increase the number of history entries to reference more past generation results
- When you want to reduce the number of history entries to save memory
- When you want to adjust the range of history accessible via `env.HISTORY()`

## What It Does

Sets the maximum number of generation history entries to keep. Each time prompt generation is executed, the result is added to the history. When the number exceeds the configured limit, older entries are automatically removed.

History is accessible via the `env.HISTORY()` function in [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)s, allowing you to reference past generation results.

## How to Use

1. Select **PromptGeneration > Set Max History Entries** from the menu
2. Enter the number of entries to keep (0-100)
3. Click OK

## Notes

- The default value is 0 (no history kept)
- The current setting value is displayed in the menu item
- The setting is saved to the project
- Reducing the value will trim existing history entries on the next generation
- History can also be viewed from the History section in the [Result Window](../01-Basics/04-Result%20Window.md)

## Related

- [Result Window](../01-Basics/04-Result%20Window.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Set Max Recursion Depth](16-Set%20Max%20Recursion%20Depth.md)
- [Once Generation](01-Once%20Generation.md)
- [Generation](../01-Basics/03-About%20Prompt%20Generation.md)
