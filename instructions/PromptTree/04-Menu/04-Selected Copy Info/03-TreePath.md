# TreePath

**Tree Path**

## When to Use

- When you want to confirm or share the hierarchical position of a prompt
- When you want to use it in the [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)'s [Filter](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) command

## What It Does

Copies the tree path (e.g., "Group A / Subgroup / Prompt Name") of the selected prompt to the clipboard.

## How to Use

1. Select a prompt
2. Select **PromptTree > Selected: Copy Info > TreePath** from the menu

## Usage Examples

The copied tree path can be used as a parameter for the [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)'s [Filter](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) command.

```
@@@_CategoryName.Filter(TreePath=copied tree path)_@@@
```

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [TreePath](../../02-Glossary/01-TreePath.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Copy Name](01-Name.md)
- [Copy Content](02-Content.md)
- [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Filter](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
