# Search Panel Operations

## Overview

The search panel has a 2-row layout for searching and filtering prompts.

```
┌─────────────────────────────────────────────────────────────┐
│ [Search Box        ][×] [Target Filter▼] [✓][□][🍃]        │  ← Row 1
│ [Search Target▼] [☐Regex] [☐Exclude] [Date▼]  [Match Count]│  ← Row 2
└─────────────────────────────────────────────────────────────┘
```

When a filter is active, the background turns green.

## Row 1: Search Query and Target Filter

### Search Box

- Enter text for real-time filtering
- Case-insensitive
- Clear with "×" button or **Esc** key

**Keyboard operations**:
- **Esc**: Clear search
- **↓**: Move to first match in tree
- **↑**: Move to last match in tree

### Target Filter Dropdown

Narrow down the search targets:

- **All nodes**: All nodes (default)
- **Checked only**: Checked nodes only
- **Unchecked only**: Unchecked nodes only
- **Leaves only**: Leaf nodes (no children) only

### Filter Result Operation Buttons

Displayed when a filter is active:

- **Check Filtered Results** (✓): Check all filtered results
- **Uncheck Filtered Results** (□): Uncheck filtered results
- **Check Filtered Leaves** (🍃): Check only leaves in filtered results

## Row 2: Search Options

### Search Target Dropdown

Choose which field to search:

- **Name**: Prompt name (default)
- **Content**: Prompt content text
- **Tag**: Tags
- **TreePath**: Full path from root

### Option Checkboxes

- **Regex**: Search as regular expression (pattern matching)
- **Exclude**: Invert matches (display items that don't match)

### Date Filter Dropdown

Filter by creation date:

- **All**: No date filter (default)
- **Today**: Created today
- **Yesterday**: Created yesterday
- **Last 7 days**: Past 7 days
- **Last 30 days**: Past 30 days
- **This week**: This week
- **Last week**: Last week
- **This month**: This month
- **Last month**: Last month

### Match Count Display

When a filter is active, the number of matching nodes is displayed.

## Combining Filters

Multiple filters can be combined. Only nodes meeting all conditions are displayed.

**Examples**:
- Search "hair" by name + Checked only → Checked items with "hair" in the name
- Last 7 days + Leaves only → Leaf nodes created in the past 7 days

## Focusing the Search Panel

- Select **PromptTree > Search Panel > Get Focus** from the menu
- Click the search box

## Related

- [Search](../../../AdvancedPanel/01-Basics/07-What Is Advanced Panel.md)
- [PromptTree](../03-Prompt Tree Overview.md)
- [Favorite Query](../../../AdvancedPanel/02-Glossary/04-Favorite Query.md)
- [Check Filtered Results](../../04-Menu/15-Search Panel/02-Check Filtered Results.md)
- [Uncheck Filtered Results](../../04-Menu/15-Search Panel/03-Uncheck Filtered Results.md)
- [Check Filtered Leaves](../../04-Menu/15-Search Panel/04-Check Filtered Leaves.md)
- [Selecting](../02-Operations/04-Selecting Generation Targets.md)
