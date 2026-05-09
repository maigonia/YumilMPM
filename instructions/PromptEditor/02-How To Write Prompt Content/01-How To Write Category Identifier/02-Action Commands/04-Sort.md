# Sort

**Action for sorting chunks**

## Overview

The Sort action sorts chunks selected by [Pick](03-Pick.md) based on specified conditions. It controls the output order during prompt generation.

## Syntax

```
@@@_CategoryName.Pick(first=-1).Sort(target=order)_@@@
```

## Default Value

When the parameter is omitted (`.Sort()`) or an invalid parameter is specified, it defaults to none=asc, **no sorting** (maintains original order).

```
@@@_CategoryName.Pick(first=-1).Sort()_@@@
↓ Not sorted (original order maintained)
```

## Sort Targets

### name - Sort by Chunk Name

Sorts by chunk name (prompt name).

```
@@@_Character.Pick(first=-1).Sort(name=asc)_@@@
```

> Sort by chunk name ascending (A→Z)

### content - Sort by Chunk Content

Sorts by chunk content (prompt content).

```
@@@_Effects.Pick(first=-1).Sort(content=desc)_@@@
```

> Sort by content descending (Z→A)

### date - Sort by Creation Date

Sorts by chunk creation date.

```
@@@_Background.Pick(first=-1).Sort(date=asc)_@@@
```

> Sort oldest first

```
@@@_Background.Pick(first=-1).Sort(date=desc)_@@@
```

> Sort newest first

### random - Random Shuffle

Randomly shuffles chunks. The order parameter is ignored.

```
@@@_Effects.Pick(first=-1).Sort(random)_@@@
```

> Shuffle to random order

### none - No Sorting (Default)

Maintains original order.

```
@@@_Character.Pick(first=-1).Sort(none)_@@@
```

> No sorting (same as omitting)

## Sort Order

- **asc**: Ascending (A→Z, oldest→newest) - Default
- **desc**: Descending (Z→A, newest→oldest)

When order is omitted, `asc` (ascending) is used.

```
@@@_Character.Pick(first=-1).Sort(name)_@@@
↓ Equivalent to
@@@_Character.Pick(first=-1).Sort(name=asc)_@@@
```

## Alternative Notation

Underscore format is also supported.

```
@@@_Character.Pick(first=-1).Sort(name_asc)_@@@
↓ Equivalent to
@@@_Character.Pick(first=-1).Sort(name=asc)_@@@
```

## Usage Examples

### Output Checked Chunks in Name Order

```
@@@_Character.Pick(first=-1).Sort(name=asc)_@@@
```

### Select from All and Output in Random Order

```
@@@_Effects.Target(all).Pick(random=5).Sort(random)_@@@
```

> Randomly select 5 from all chunks, then output in random order

### Sort After Filtering

```
@@@_Poses.Target(all).Filter(tag=standing).Pick(first=-1).Sort(name=asc)_@@@
```

> Output chunks with the "standing" tag in name order

## Notes

- Target and order are **case insensitive** (`NAME=ASC` = `name=asc`)
- Sorting is skipped when there is 1 or fewer items
- When `random` is specified, the order parameter (asc/desc) is ignored
- Invalid targets fall back to `none`
- Invalid orders fall back to `asc`

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Target](01-Target.md)
- [Filter](02-Filter.md)
- [Pick](03-Pick.md)
- [Join](05-Join.md)
- [Edit](06-Edit.md)
