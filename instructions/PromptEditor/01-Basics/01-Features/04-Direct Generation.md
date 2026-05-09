# Direct Generation

A feature that immediately executes generation using the editor content as a template for the selected category.

## When to Use

- When you want to quickly test if Category Identifier notation works correctly
- When you want to experiment with template variations
- When you want to quickly check generation results

## What It Does

Uses the content written in the editor directly as a template and immediately executes generation with the specified category's settings. Bypasses normal queue operations for quick testing and verification.

## How to Use

1. Enter template content in the editor (Category Identifiers, etc.)
2. Select the target category from the dropdown in the editor header
3. Click the **Direct Generation** button
4. Generation is immediately executed and results are displayed

## Notes

- Can be used in both the Editor tab and Draft tab
- The editor content becomes the template as-is
- Category Identifiers like `@@@_CategoryName_@@@` are resolved normally
- Programmable Blocks can also be used, but [env.chunk](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/01-env.chunk.md) cannot retrieve chunk information (because Direct Generation is not tied to a specific chunk)

## Related

- [PromptEditor](../03-Prompt Editor.md)
- [Draft Tab](05-Draft Tab.md)
- [Once Generation](../../../PromptGeneration/04-Menu/01-Once Generation.md)
- [Generation](../../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
