# What is Category Identifier

**What is Category Identifier**

## What Is This?

Category Identifier (CI) is a special notation for referencing and substituting category prompts during generation. When written in prompt content, it is replaced with the corresponding prompt.

You can reference prompts from any category, regardless of whether it is an output category or not.

## Basic Format

```
@@@_CategoryName_@@@
```

A notation that starts with `@@@_` and ends with `_@@@`, with the category name written inside.

## Usage Examples

Write the following in a template:

```
@@@_Character_@@@, @@@_Background_@@@
```

Generated result (example):

```
1girl, blue eyes, long hair, forest, sunset
```

## Action Commands

CIs are processed in the following order:

1. **Target**: Which prompts to target
2. **Filter**: Keep only those matching conditions
3. **Pick**: How many to select
4. **Sort**: How to arrange them
5. **Join**: How to combine them
6. **Edit**: Post-process the text

### Syntax

```
@@@_CategoryName.Target(state).Filter(condition).Pick(method).Sort(sortMethod).Join(separator).Edit(editMethod)_@@@
```

### Default Values

A shorthand like `@@@_Character_@@@` is actually equivalent to:

```
@@@_Character.Target(checked).Filter().Pick(random=1).Sort(none=asc).Join(,\n).Edit()_@@@
```

> "Select one random prompt from checked prompts, output with comma + newline separator"

Each command has default values that are applied when omitted or when invalid parameters are given. Therefore `@@@_Character_@@@` is the basic form using all commands with defaults.

### Command List

| Command | Role | Example |
|---------|------|---------|
| [Target](02-Action%20Commands/01-Target.md) | How to select target prompts | `.Target(all)` |
| [Filter](02-Action%20Commands/02-Filter.md) | Filtering by conditions | `.Filter(tag=main)` |
| [Pick](02-Action%20Commands/03-Pick.md) | Selection method and count | `.Pick(random=3)` |
| [Sort](02-Action%20Commands/04-Sort.md) | Sorting | `.Sort(name=asc)` |
| [Join](02-Action%20Commands/05-Join.md) | Specifying separator | `.Join(, )` |
| [Edit](02-Action%20Commands/06-Edit.md) | Text editing/processing | `.Edit(TrimWhitespaceEachLine)` |

### Processing Order

Commands are processed in the order listed above, **regardless of the order they are written**.

## Basic Writing Rules

### Parameters Can Be Written Directly

CI parameters do not need to be enclosed in quotation marks (`"` or `'`). They can be written directly.

```
@@@_Category.Filter(tag=main character)_@@@
```

> Values containing spaces like `tag=main character` can be written as-is

### Case Insensitive

Command names and parameter names are case insensitive.

```
@@@_Category.FILTER(TAG=main)_@@@
@@@_Category.filter(tag=main)_@@@
@@@_Category.Filter(Tag=main)_@@@
```

> All have the same meaning

### Commands Are Optional

All commands have default values and can be omitted.

```
@@@_CategoryName_@@@
```

> Equivalent to:

```
@@@_CategoryName.Target(checked).Pick(random=1).Join(,\n)_@@@
```

### Stacking Commands

[Filter](02-Action%20Commands/02-Filter.md) and [Edit](02-Action%20Commands/06-Edit.md) can be used multiple times.

```
@@@_Category.Filter(tag=A).Filter(tag=B)_@@@
```

> Keep only those with both tag A and tag B

```
@@@_Category.Edit(TrimWhitespaceEachLine).Edit(RemoveDuplicateTags)_@@@
```

> Remove whitespace, then remove duplicate tags

## Common Usage Patterns

### Output Checked Prompts (Most Basic)

```
@@@_Character_@@@
```

### Random Selection from All

```
@@@_Options.Target(all).Pick(random=3)_@@@
```

### Filter by Tag and Output

```
@@@_Poses.Filter(tag=standing)_@@@
```

### Output with Newline Separator

```
@@@_Descriptions.Join(\n)_@@@
```

### Edit with AI

```
@@@_Content.Edit(LM=default, summarize).Edit(LM=default, translate)_@@@
```

## Related

- [Category Identifier](README.md)
- [Category Template](../../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Generation](../../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Target](02-Action%20Commands/01-Target.md)
- [Filter](02-Action%20Commands/02-Filter.md)
- [Pick](02-Action%20Commands/03-Pick.md)
- [Sort](02-Action%20Commands/04-Sort.md)
- [Join](02-Action%20Commands/05-Join.md)
- [Edit](02-Action%20Commands/06-Edit.md)
- [Programmable Block](../02-How%20To%20Write%20Programmable%20Block/README.md)
- [Output Category](../../../CategoryTree/02-Glossary/01-Output%20Category.md)
