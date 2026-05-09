# AutoComplete

An assistance feature that automatically displays candidates during prompt input.

## When to Use

- When you want to quickly and accurately enter tags and words
- When you want to enter Category Identifier parameters
- When you want to reference existing chunk names or category names

## What It Does

Automatically displays registered tags, chunk names, category names, command parameters, and other candidates while typing. Selecting a candidate allows fast and accurate input.

## Basic Operations

- **Up/Down keys**: Navigate within the candidate list
- **Enter / Tab**: Confirm the selected candidate
- **Esc**: Close the candidate list
- **Ctrl+Enter**: Open URL if the candidate has a URL configured
- **Alt+Enter**: For chunk candidates, insert content instead of name

## Automatic Display

Candidates are automatically displayed when the following characters are typed:

- **`.` (dot)**: For Category Identifier commands (`.Target`, `.Filter`, etc.)
- **`@`**: For category references (`@@@_CategoryName_@@@`)
- **`_`**: Input assistance for various identifiers

## Enable/Disable

Can be toggled from **PromptEditor > AutoComplete > Enable**.

## Related

- [PromptEditor](../03-Prompt%20Editor.md)
- [AutoComplete Enable](../../04-Menu/12-AutoComplete/01-Enable%20AutoComplete.md)
- [AutoComplete Setting](../../04-Menu/12-AutoComplete/02-AutoComplete%20Settings%20-%20List%20&%20Candidate%20Management.md)
