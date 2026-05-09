# Selecting Generation Targets

## Overview

This explains how to select prompts to include in [Generation](../../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md) using [Check State](../01-Concepts/01-Understanding%20Check%20State.md).

Use different check strategies depending on your purpose.

## Basic Check Operations

### Individual Check

Click a checkbox to toggle on/off.

### Range Check

**Shift+Click** to batch toggle from the last checked position to the current position.

### Exclusive Check

**Ctrl+Click** to uncheck all in the category and check only the clicked prompt. Useful when you want to select just one.

## Batch Check Strategies

### Check/Uncheck All

- **Check All**: Select everything first, then remove what's unnecessary
- **Uncheck All**: Reset once, then select only what's needed

### Check Leaves Only

**Check All Leaves** selects only the actual materials, excluding groups/folders.

**Use case**: When groups also have content and you want to target only leaves (terminals)

### Check Using Hierarchy

Specify ranges based on the selected prompt. Operate from right-click → **Selected: Check/Uncheck** or from the [Control Bar](../04-Panel/01-Control%20Bar%20Operations.md).

- **Child Prompts**: Direct children (toggle one level below only)
- **Sibling Prompts**: Siblings (batch toggle same level)
- **Descendants Prompts**: Descendants (toggle entire branch)
- **Leaf Prompts**: Descendant leaves (terminals of the branch only)

**Example**: Select the "Hair Color" group and use **Selected: Check/Uncheck > Descendants Prompts** → Check all hair-color related items

## Checking in Conjunction with Search

Select only prompts matching specific criteria.

### Search and Check

1. Enter criteria in the search box (e.g., "blonde")
2. Click the **Check Filtered Results** button
3. Matching prompts are checked

### Combining with Filters

In addition to search, the following filters can also be used:

- **Checked only**: Narrow down from checked items
- **Unchecked only**: Narrow down from unchecked items
- **Leaves only**: Target only leaves
- **Date filter**: Narrow down by creation date

**Example**: "Last 7 days" filter + **Check Filtered Leaves** → Check recently added leaves

## Saving Check State

Frequently used check patterns can be saved.

### Favorite Lists

Save checked prompts within a category.

1. Create the desired check combination
2. Right-click → **Checked > Create Favorite List**
3. Name and save

**Features**:
- Saved per category
- Added to existing checks on apply (additive)

### Check Presets

Batch save check state across all categories.

**Features**:
- Records entire project state
- Replaces existing checks on apply (replacement)

## Navigation Between Checked Nodes

Navigate while reviewing checked prompts. Operate from menu **PromptTree > Goto Checked Above/Below** or from the [Control Bar](../04-Panel/01-Control%20Bar%20Operations.md).

- **Goto Checked Above**: To the nearest checked item above
- **Goto Checked Below**: To the nearest checked item below

## Tidying the Display

To make only checked items easily visible:

Use **PromptTree > Collapse Except Checked** to collapse everything except paths to checked nodes.

## Related

- [Check State](../01-Concepts/01-Understanding%20Check%20State.md)
- [PromptTree](../03-Prompt%20Tree%20Overview.md)
- [Check All](../../04-Menu/06-Check%20All.md)
- [UnCheck All](../../04-Menu/07-Uncheck%20All.md)
- [Check All Leaves](../../04-Menu/08-Check%20All%20Leaves.md)
- [Child Prompts](../../04-Menu/02-Selected%20Check%20Uncheck/02-Child%20Prompts.md)
- [Sibling Prompts](../../04-Menu/02-Selected%20Check%20Uncheck/03-Sibling%20Prompts.md)
- [Leaf Prompts](../../04-Menu/02-Selected%20Check%20Uncheck/05-Leaf%20Prompts.md)
- [Descendants Prompts](../../04-Menu/02-Selected%20Check%20Uncheck/04-Descendants%20Prompts.md)
- [Search Panel](../04-Panel/02-Search%20Panel%20Operations.md)
- [Favorite List](../../../AdvancedPanel/02-Glossary/03-Favorite%20List.md)
