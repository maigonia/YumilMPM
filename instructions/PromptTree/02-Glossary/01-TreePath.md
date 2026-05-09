# TreePath

## Overview

TreePath is a string that represents the position of a prompt within the prompt tree.

It expresses the hierarchy from the root, separated by "/" (slash).

## Format

```
parentPromptName/childPromptName/grandchildPromptName
```

## Example

If the tree structure is as follows:

```
Hair Color
├── Blonde
│   ├── Long
│   └── Short
└── Black
```

The TreePath for each prompt is:

- **Hair Color** → `Hair Color`
- **Blonde** → `Hair Color/Blonde`
- **Long** → `Hair Color/Blonde/Long`
- **Short** → `Hair Color/Blonde/Short`
- **Black** → `Hair Color/Black`

## Usage Scenarios

### Search

Set the search target to **TreePath** in the search panel to search by path.

**Examples**:
- `Hair Color/Blonde` → Matches "Blonde" under "Hair Color" and its descendants
- `Blonde` → Matches everything containing "Blonde" in the TreePath

### Copy

You can copy the TreePath of the selected prompt to the clipboard with **PromptTree > Selected: Copy Info > TreePath**.

### CategoryIdentifier

In [CategoryIdentifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) notation, you can use TreePath to filter prompts with the [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) action.

#### Basic Format (Exact Match)

Targets only prompts that exactly match the specified TreePath.

```
@@@_CategoryName.Filter(TreePath=Hair Color/Blonde)_@@@
```

#### Target All Descendants (`/**`)

Adding `/**` at the end of the path targets all descendants under the specified path.

```
@@@_CategoryName.Filter(TreePath=Hair Color/Blonde/**)_@@@
```

**Example**: `Hair Color/Blonde/**` matches:
- `Hair Color/Blonde/Long`
- `Hair Color/Blonde/Short`
- `Hair Color/Blonde/Long/Straight` (grandchildren included)

#### Regex Mode (`TreePath*=`)

Adding `*` to the condition type enables regex pattern matching.

```
@@@_CategoryName.Filter(TreePath*=^Hair Color/.*)_@@@
```

Or using `/pattern/flags` format:
```
@@@_CategoryName.Filter(TreePath=/Blonde|Black/i)_@@@
```

#### Exclusion Mode (`TreePath!=`)

Adding `!` to the condition type keeps items that do not match.

```
@@@_CategoryName.Filter(TreePath!=Hair Color/Blonde)_@@@
```

See [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) for details.

## Important Notes

- "/" cannot be used in prompt names (it conflicts with the path separator)
- Since prompts with the same name cannot exist under the same parent, TreePaths are unique
- Moving a prompt also changes its TreePath
- **Regex mode uses partial matching**. If there are similar names at the same level (e.g., `Blonde` and `Blonde Long`), `TreePath*=Blonde` matches both. Use `^` and `$` anchors for exact matching (e.g., `TreePath*=Blonde$`)

## Related

- [Hierarchy](../01-Basics/01-Concepts/02-Understanding Hierarchy.md)
- [PromptTree](../01-Basics/03-Prompt Tree Overview.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Search](../../AdvancedPanel/01-Basics/07-What Is Advanced Panel.md)
- [Copy TreePath](../04-Menu/04-Selected Copy Info/03-TreePath.md)
