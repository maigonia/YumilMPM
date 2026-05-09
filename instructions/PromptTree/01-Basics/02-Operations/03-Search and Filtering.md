# Search and Filtering

## Overview

This explains how to search and filter prompts to easily find the materials you need.

## Basic Search

### Text Search

1. Enter text in the search box
2. Matching prompts are filtered in real time
3. Names of matching prompts are displayed in green

Search is case-insensitive.

### Clearing the Search

- Click the "×" button in the search box
- Press the **Esc** key

## Selecting Search Target

You can choose which field to search.

- **Name**: Prompt name (e.g., search for prompts with "blonde" in the name)
- **Content**: Content (e.g., search for prompts containing "blonde" in content)
- **Tag**: Tag (e.g., search for prompts with "hair" tag)
- **[TreePath](../../02-Glossary/01-TreePath.md)**: Path from root (e.g., search by path "Hair Color/Blonde")

## Search Options

### Regex

When the **Regex** checkbox is on, you can search using regular expression patterns.

**Examples**:
- `^hair` → Items starting with "hair"
- `color$` → Items ending with "color"
- `hair|head` → Items containing "hair" or "head"

### Exclusion Search (Exclude)

When the **Exclude** checkbox is on, items that do NOT match are displayed.

**Example**: Exclusion search for "NSFW" → Shows only items not containing NSFW

## Filter

In addition to search, you can filter by conditions.

### Target Filter

- **All nodes**: All (default)
- **Checked only**: Checked only
- **Unchecked only**: Unchecked only
- **Leaves only**: Leaf nodes only

### Date Filter

Filter by creation date.

- **Today**: Created today
- **Yesterday**: Created yesterday
- **Last 7 days**: Past 7 days
- **Last 30 days**: Past 30 days
- **This week**: This week
- **Last week**: Last week
- **This month**: This month
- **Last month**: Last month

## Combining Filters

Multiple filters can be combined. Only items meeting all conditions are displayed.

**Examples**:
- "hair" + Checked only → Checked items with "hair" in the name
- Last 7 days + Leaves only → Leaves created in the past 7 days

## Operations on Filter Results

When a filter is active, check operations can be performed on the results.

- **Check Filtered Results**: Check all filtered results
- **Uncheck Filtered Results**: Uncheck filtered results
- **Check Filtered Leaves**: Check only leaves in filtered results

**Usage example**:
1. Search for "hair"
2. Click **Check Filtered Results**
3. All hair-related prompts are checked

## Filter State Display

- When a filter is active, the search panel background turns green
- The number of matching prompts is displayed

## Keyboard Operations

While the search box has focus:

- **Esc**: Clear search
- **↓**: Move to first match in tree
- **↑**: Move to last match in tree

## Related

- [Prompt](../01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../03-Prompt Tree Overview.md)
- [Search Panel](../04-Panel/02-Search Panel Operations.md)
- [Favorite Query](../../../AdvancedPanel/02-Glossary/04-Favorite Query.md)
- [Global Search](../../../AdvancedPanel/01-Basics/06-Global Search Search All Tab.md)
- [Check Filtered Results](../../04-Menu/15-Search Panel/02-Check Filtered Results.md)
- [Uncheck Filtered Results](../../04-Menu/15-Search Panel/03-Uncheck Filtered Results.md)
- [Check Filtered Leaves](../../04-Menu/15-Search Panel/04-Check Filtered Leaves.md)
