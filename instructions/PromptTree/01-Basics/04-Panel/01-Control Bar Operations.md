# Control Bar Operations

## Overview

The control bar has buttons for check operations and expand/collapse, color-coded by function.

```
┌──────────────────────────────────────────────────────────────┐
│ [Purple Group] [Blue Group] [Green Group] [Orange Group]     │
└──────────────────────────────────────────────────────────────┘
```

## Purple Group: Overall Check Operations

Check operations for the entire tree.

- **Check All** (✓): Check all prompts
- **Uncheck All** (□): Uncheck everything
- **Check All Leaves** (🍃): Check only leaf nodes (prompts without children)

**Check All Leaves** is useful when you want to select only actual materials, excluding groups/folders.

## Blue Group: Check Operations Based on Selected Node

Relative check operations based on the selected prompt.

Access from menu via **PromptTree > Selected: Check/Uncheck**.

- **Child Prompts** (👶): Toggle check state of direct children
- **Sibling Prompts** (👥): Toggle check state of same level (siblings)
- **Descendants Prompts** (🌳): Toggle check state of all descendants
- **Leaf Prompts** (🍃): Toggle only leaf nodes among descendants

**Requirement**: A prompt must be selected.

## Green Group: Navigation

Jump between checked prompts.

- **Goto Checked Above** (⬆): Move to the nearest checked prompt above the current position
- **Goto Checked Below** (⬇): Move to the nearest checked prompt below the current position

**Requirement**: Checked prompts must exist.

## Orange Group: Expand/Collapse

Controls the tree display state.

- **Expand All** (📂): Expand all nodes
- **Collapse All** (📁): Collapse all nodes
- **Collapse Except Checked** (📁-): Collapse everything except paths to checked nodes

**Collapse Except Checked** is useful when you want to easily view only the checked materials.

## Button Enable/Disable

- Most buttons are disabled when the tree is empty
- Selected node-based buttons (Blue Group) are disabled when no prompt is selected
- Navigation buttons (Green Group) are disabled when there are no checked nodes

## Related

- [Check State](../01-Concepts/01-Understanding%20Check%20State.md)
- [Hierarchy](../01-Concepts/02-Understanding%20Hierarchy.md)
- [PromptTree](../03-Prompt%20Tree%20Overview.md)
- [Check All](../../04-Menu/06-Check%20All.md)
- [UnCheck All](../../04-Menu/07-Uncheck%20All.md)
- [Check All Leaves](../../04-Menu/08-Check%20All%20Leaves.md)
- [Expand All](../../../CategoryTree/03-Menu/03-Expand%20All.md)
- [Collapse All](../../../CategoryTree/03-Menu/04-Collapse%20All.md)
- [Collapse Except Checked](../../04-Menu/13-Collapse%20Except%20Checked.md)
