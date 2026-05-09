# Syntax Highlighting Settings

Add custom rules to color-code text patterns in the editor.

*Basic syntax like LoRA `<lora:...>` and Category Identifier `@@@_..._@@@` are highlighted by default. Here you can add your own custom rules.

## Understanding with Examples

To highlight a specific character name:
- Pattern: `son goku`
- Color: Orange
- Regex: OFF

This displays `son goku` in orange, making it easy to find in long prompts.

Another example: Highlight quality tags in green:
- Pattern: `(masterpiece|best quality|high resolution)`
- Color: Green
- Regex: ON

## Access

`PromptEditor > Syntax Highlight > Setting...`

## Tips

- Rules at the bottom of the list take priority (last wins)
- Complex patterns possible with regex
- Basic syntax (LoRA, Category Identifier, etc.) needs no configuration
