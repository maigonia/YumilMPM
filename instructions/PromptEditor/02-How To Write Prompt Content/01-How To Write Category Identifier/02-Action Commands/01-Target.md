# Target

**Action for selecting target chunks**

## Overview

The Target action, as the first step of a [Category Identifier](../README.md), specifies which prompts (chunks) on the prompt tree to target. It filters based on [Check State](../../../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md) and selection state.

## Syntax

```
@@@_CategoryName.Target(parameter)_@@@
```

When the parameter is omitted, `checked` is used by default.

```
@@@_CategoryName_@@@
↓ Equivalent to
@@@_CategoryName.Target(checked)_@@@
```

## Parameter List

### Basic Parameters

- **checked** (default): Gets chunks with [Check State](../../../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md) checked
- **unchecked**: Gets unchecked chunks
- **all**: Gets all chunks (regardless of check state)
- **selected**: Gets the currently selected chunk on the prompt tree

### Children Parameters

- **childrenOfChecked**: Gets only the direct children of checked chunks
- **childrenOfUnchecked**: Gets only the direct children of unchecked chunks
- **childrenOfSelected**: Gets only the direct children of the selected chunk

*"Direct children" refers to child elements one level below only; grandchildren and further descendants are not included.

### Leaf Node Parameters

- **allLeaves**: Gets all leaf nodes (chunks without children)
- **leavesFromChecked**: Gets leaf nodes under checked chunks
- **leavesFromUnchecked**: Gets leaf nodes under unchecked chunks
- **leavesFromSelected**: Gets leaf nodes under the selected chunk

*"Leaf nodes" refers to terminal chunks that have no child elements.

## Usage Examples

### Basic Usage

```
@@@_Character.Target(checked)_@@@
```
> Gets checked chunks from the Character category

```
@@@_Background.Target(all)_@@@
```
> Gets all chunks from the Background category

### Combining with Other Actions

```
@@@_Effects.Target(checked).Pick(random=3)_@@@
```
> Randomly select 3 from checked chunks

```
@@@_Poses.Target(all).Filter(tag=standing)_@@@
```
> Filter all chunks for those with the "standing" tag

### Using Leaf Nodes

```
@@@_Category.Target(leavesFromChecked)_@@@
```
> Gets only terminal chunks without children, under checked chunks

## Notes

- Parameters are **case insensitive** (`AllLeaves` = `allleaves` = `ALLLEAVES`)
- **Whitespace within parameters is ignored** (`children Of Checked` = `childrenOfChecked`)
- When the Target action is omitted, `checked` is applied as the default
- Invalid parameters also fall back to `checked`

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Check State](../../../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Filter](02-Filter.md)
- [Pick](03-Pick.md)
- [Sort](04-Sort.md)
- [Join](05-Join.md)
- [Edit](06-Edit.md)
