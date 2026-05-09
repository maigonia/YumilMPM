# How To Write Prompt Content

**How to Write Prompt Content**

## When to Use

- When you want to use special syntax in prompt content
- When you want to dynamically generate content by referencing other prompts
- When you want to check Category Identifier syntax

## What It Does

Explains the special syntax that can be used in prompt content. Selecting this menu item opens the instruction window where you can reference detailed documentation.

## Main Syntax

### Category Identifier (CI)

A notation for referencing prompts from other categories during generation.

```
@@@_CategoryName_@@@
```

Example: `@@@_Character_@@@, @@@_Background_@@@`

### Command Chain

Commands can be added to CI to customize behavior.

```
@@@_CategoryName.Target("all").Pick(random=3).Join(, )_@@@
```

## How to Use

1. Select **PromptEditor > How to Write Prompt Content** from the menu
2. The instruction window opens
3. Reference detailed explanations for each syntax

## Related

- [PromptEditor](../01-Basics/03-Prompt Editor.md)
- [Category Identifier](../02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Programmable Block](../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
