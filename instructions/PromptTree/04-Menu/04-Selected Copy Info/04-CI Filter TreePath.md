# CI Filter (TreePath)

**CI Filter (TreePath)**

## When to Use

- When you want to reference a specific prompt using [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) with a tree path filter
- When you need a ready-to-paste CI notation

## What It Does

Copies a complete [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) for the selected prompt to the clipboard. The copied text includes the category name, Target, and Filter — ready to paste directly into prompt content.

## How to Use

1. Select a prompt
2. Select **PromptTree > Selected: Copy Info > CI Filter (TreePath)** from the menu

## Copied Format

```
@@@_CategoryName.Target(all).Filter(treePath=TreePath)_@@@
```

### Example

When selecting a prompt at "Main/Hero" in the "Character" category:

```
@@@_Character.Target(all).Filter(treePath=Main/Hero)_@@@
```

`Target(all)` is included so the prompt is retrieved regardless of check state.

## Difference from TreePath

- **TreePath**: Copies only the path string (e.g., `Main/Hero`)
- **CI Filter (TreePath)**: Copies the full CI notation (e.g., `@@@_Character.Target(all).Filter(treePath=Main/Hero)_@@@`)

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [TreePath](../../02-Glossary/01-TreePath.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Copy TreePath](03-TreePath.md)
- [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Target](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/01-Target.md)
- [Filter](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
