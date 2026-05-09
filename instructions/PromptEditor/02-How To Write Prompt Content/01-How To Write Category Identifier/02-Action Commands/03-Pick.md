# Pick

**Action for selecting chunks**

## Overview

The Pick action selects from chunks narrowed down by [Target](01-Target.md) and [Filter](02-Filter.md), using a specified method and count. Selected chunks are passed to [Sort](04-Sort.md) and [Join](05-Join.md).

## Syntax

```
@@@_CategoryName.Pick(method=count)_@@@
```

## Default Value

When the parameter is omitted (`.Pick()`) or an invalid parameter is specified, it defaults to `random=1` (randomly select 1).

```
@@@_CategoryName.Pick()_@@@
↓ Equivalent to
@@@_CategoryName.Pick(random=1)_@@@
```

## Selection Methods

### random - Random Selection (Default)

Randomly selects the specified number.

```
@@@_Character.Pick(random=3)_@@@
```
> Randomly select 3

### first - Select from Beginning

Selects the specified number from the beginning.

```
@@@_Character.Pick(first=5)_@@@
```
> Select the first 5

### last - Select from End

Selects the specified number from the end.

```
@@@_Character.Pick(last=2)_@@@
```
> Select the last 2

### date - Select by Date Condition

Filters by creation date.

```
@@@_Character.Pick(date=today)_@@@
```
> Select all chunks created today

## Count Specification

- **Positive number (N > 0)**: Select N items
- **0 or negative number**: Select all

```
@@@_Character.Pick(first=-1)_@@@
```
> Select all chunks (maintaining original order)

```
@@@_Character.Pick(random=0)_@@@
```
> Select all chunks (random order)

**Number-only shorthand**:

```
@@@_Character.Pick(3)_@@@
↓ Equivalent to
@@@_Character.Pick(random=3)_@@@
```

## Date Conditions

### Relative Date Keywords

- **today**: Today
- **yesterday**: Yesterday
- **tomorrow**: Tomorrow
- **this_week**: This week (starts on Sunday)
- **last_week**: Last week
- **this_month**: This month
- **last_month**: Last month
- **this_year**: This year
- **last_year**: Last year

```
@@@_Character.Pick(date=this_month)_@@@
```
> Select chunks created this month

### Relative Patterns

- **last_Ndays**: Past N days (including today)
- **Ndays_ago**: N days ago (that single day only)

```
@@@_Character.Pick(date=last_7days)_@@@
```
> Select chunks created in the past 7 days

```
@@@_Character.Pick(date=3days_ago)_@@@
```
> Select chunks created 3 days ago

### Date Range Specification

Use tilde (`~`) to specify a range.

- **startDate~endDate**: Range specification
- **startDate~**: Everything from the start date onward
- **~endDate**: Everything up to the end date

```
@@@_Character.Pick(date=2024-01-01~2024-12-31)_@@@
```
> Select chunks created during 2024

```
@@@_Character.Pick(date=2024-06-01~)_@@@
```
> Select chunks created from June 1, 2024 onward

### Single Date

Specific dates can be specified.

- **YYYY-MM-DD**: ISO format (recommended)
- **YYYY/MM/DD**: Slash-separated
- **MM/DD/YYYY**: US format

```
@@@_Character.Pick(date=2024-12-25)_@@@
```
> Select chunks created on December 25, 2024

## Combined Conditions

Date filters can be combined with selection methods.

```
@@@_CategoryName.Pick(date=condition, method=count)_@@@
```

Processing order:
1. Filter by date condition
2. Apply method (random/first/last) to filtered chunks

```
@@@_Character.Pick(date=last_7days, random=3)_@@@
```
> Randomly select 3 from chunks in the past 7 days

```
@@@_Character.Pick(date=this_month, first=5)_@@@
```
> Select the first 5 from this month's chunks

## Usage Examples

### Randomly Select 1 (Default Behavior)

```
@@@_Character_@@@
```
> Omitting Pick defaults to `random=1`

### Get All Chunks in Original Order

```
@@@_Character.Pick(first=-1)_@@@
```

### Combine with Filter

```
@@@_Effects.Target(all).Filter(tag=fire).Pick(random=2)_@@@
```
> Randomly select 2 from chunks with the "fire" tag

### Combine with Date Filter

```
@@@_Background.Pick(date=last_30days, last=5)_@@@
```
> Select the last 5 from chunks in the past 30 days

## Notes

- Method and count are **case insensitive** (`RANDOM=3` = `random=3`)
- If the count exceeds the number of chunks, all available chunks are returned
- Invalid methods fall back to `random`
- Invalid counts fall back to `1`
- Invalid date conditions skip filtering and use all chunks

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Target](01-Target.md)
- [Filter](02-Filter.md)
- [Sort](04-Sort.md)
- [Join](05-Join.md)
- [Edit](06-Edit.md)
- [env.SEED](../../02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/12-env.SEED.md)
