# Understanding Hierarchy

## Overview

In the prompt tree, prompts are managed in a hierarchical (tree) structure.

This allows you to group related prompts and manage materials in an organized state.

## Hierarchy Terminology

```
Root
├── Parent A
│   ├── Child A-1        ← "Child" of Parent A, "Sibling" of Child A-2
│   ├── Child A-2        ← "Child" of Parent A, "Sibling" of Child A-1
│   │   └── Grandchild A-2-1  ← "Child" of Child A-2, "Descendant" of Parent A, Leaf
│   └── Child A-3        ← Leaf
└── Parent B
    └── Child B-1        ← Leaf
```

- **Root**: Top-level prompts (no parent)
- **Parent**: A prompt that has children
- **Child**: A prompt directly under a parent
- **Sibling**: Prompts that share the same parent
- **Descendant**: All lower-level prompts: children, grandchildren, great-grandchildren, etc.
- **Leaf**: A prompt with no children (terminal node)

## Benefits of Hierarchical Structure

### 1. Easy to Organize

Related materials can be grouped like folders.

**Example**:
```
Hair Color
├── Blonde
├── Black
├── Brown
└── Red
```

### 2. Easy Batch Operations

You can specify ranges using the hierarchy.

- Check all descendants of "Hair Color"
- Check only leaves under "Hair Color"

### 3. Better Visibility with Expand/Collapse

You can expand only the parts you need to display.

## Hierarchy-Related Operations

### Check Operations

Operate from right-click → **Selected: Check/Uncheck** or from the [Control Bar](../04-Panel/01-Control Bar Operations.md).

- **Child Prompts**: Direct children only
- **Sibling Prompts**: Siblings (children of the same parent)
- **Descendants Prompts**: All descendants
- **Leaf Prompts**: Only leaves among descendants

### Expand/Collapse

- **Expand All**: Expand everything
- **Collapse All**: Collapse everything
- **Collapse Except Checked**: Collapse everything except paths to checked items

### Add Operations

Add from right-click → **Selected: Add**.

- **Add Child**: Add as a child under the selected item
- **Add Sibling**: Add at the same level as the selected item
- **Add Root Group**: Add at the root

## TreePath

[TreePath](../../02-Glossary/01-TreePath.md) is a string representing the position of a prompt. It separates the hierarchy from the root with "/".

**Example**: `Hair Color/Blonde/Long`

See [TreePath](../../02-Glossary/01-TreePath.md) for details.

## Related

- [Prompt](03-What Is a Prompt.md)
- [Hierarchy](02-Understanding Hierarchy.md)
- [TreePath](../../02-Glossary/01-TreePath.md)
- [PromptTree](../03-Prompt Tree Overview.md)
- [Move Up](../../../CategoryTree/03-Menu/01-Selected Category/05-Move Up.md)
- [Move Down](../../../CategoryTree/03-Menu/01-Selected Category/06-Move Down.md)
- [Expand All](../../../CategoryTree/03-Menu/03-Expand All.md)
- [Collapse All](../../../CategoryTree/03-Menu/04-Collapse All.md)
