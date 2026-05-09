# Draft Tab

Click the **Draft** tab at the top of the editor to switch to a free memo/draft space.

## When to Use

- When you want to temporarily jot down prompt ideas
- When you want to draft a template and test it with direct generation
- When you want to temporarily save prompt content elsewhere

## What It Does

Provides a Draft tab separate from the normal Editor tab where you can freely write text. It is an independent space that has no effect on normal generation.

## How to Use

1. Click the **Draft** tab at the top of the editor
2. Write text freely
3. Click the **Editor** tab to return to the normal editor

## Differences from Editor Tab

| | Editor Tab | Draft Tab |
|---|---|---|
| Content saving | Auto-saved | **Not saved** (lost on app close) |
| Generation impact | Used for normal generation | No impact on normal generation |
| Direct generation | Available | Available |
| AutoComplete | Available | Available |
| SyntaxHighlight | Available | Available |
| Command Palette (F1) | Available | Available |

## Combining with Direct Generation

The Draft tab is convenient when combined with [Direct Generation](04-Direct Generation.md).
Direct Generation sends the text displayed in the current tab directly to the generation result.

1. Freely draft templates in the Draft tab
2. Select a category and test with **Direct Generation**
3. Check results, and copy to Editor tab when satisfied

This allows experimenting with templates without changing normal prompt content.

In Direct Generation, Category Identifiers can be used, but Programmable Blocks have some limitations - env.chunk cannot retrieve chunk information.

## Caution

- **Text is not saved**: Draft tab content is lost when the app is closed
- Use it as a temporary memo/draft space only

## Related

- [PromptEditor](../03-Prompt Editor.md)
- [Direct Generation](04-Direct Generation.md)
