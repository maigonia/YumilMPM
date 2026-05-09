# Filter

**Action for narrowing down chunks by conditions**

## Overview

The Filter action narrows down chunks obtained by [Target](01-Target.md) etc. based on conditions. You can filter by name, content, tags, path, and various other conditions.

## Syntax

```
@@@_CategoryName.Filter(conditionType=value)_@@@
```

Used in combination with Target:

```
@@@_CategoryName.Target(all).Filter(tag=main)_@@@
```

## Default Value

When the parameter is omitted (`.Filter()`) or an invalid parameter is specified, **no filtering** is applied (all chunks pass through as-is).

```
@@@_CategoryName.Filter()_@@@
↓ Not filtered (all chunks are targeted)
```

## Filter Types

### name - Filter by Chunk Name

Performs a partial match search on chunk names.

```
@@@_Character.Filter(name=hero)_@@@
```
> Gets chunks with "hero" in their name

### content - Filter by Chunk Content

Performs a partial match search on chunk content.

```
@@@_Effects.Filter(content=sparkle)_@@@
```
> Gets chunks with "sparkle" in their content

### tag - Filter by Tag

Filters by tags assigned to chunks. If a chunk has multiple tags, it matches if any of them match.

```
@@@_Character.Filter(tag=main)_@@@
```
> Gets chunks with the "main" tag

### treePath - Filter by Hierarchy Path

Filters by [TreePath](../../../../PromptTree/02-Glossary/01-TreePath.md) (path/hierarchy on the [PromptTree](../../../../PromptTree/01-Basics/03-Prompt Tree Overview.md)).

```
@@@_Character.Filter(treePath=Characters/Main)_@@@
```
> Gets chunks at the specified path

#### Descendant Mode (`/**`)

Adding `/**` at the end of the path gets all descendant chunks under that path.

```
@@@_Character.Filter(treePath=Characters/Main/**)_@@@
```
> Gets all chunks under "Characters/Main"

### favoriteList - Filter by Favorite List

Filters by chunks included in a [Favorite List](../../../../AdvancedPanel/02-Glossary/03-Favorite List.md). Searches by partial match on the list name.

```
@@@_Character.Filter(favoriteList=main characters)_@@@
```
> Gets chunks in favorite lists with "main characters" in the name

### favoriteQuery - Filter by Favorite Query

Filters by search results from a [Favorite Query](../../../../AdvancedPanel/02-Glossary/04-Favorite Query.md). Searches by partial match on the query name.

```
@@@_Character.Filter(favoriteQuery=frequently used)_@@@
```
> Gets search results from favorite queries with "frequently used" in the name

### memo - Filter by Memo

Filters by the content of memos attached to chunks. If a chunk has multiple memos, it matches if any of them match.

```
@@@_Character.Filter(memo=reference material)_@@@
```
> Gets chunks with "reference material" in their memos

### icon - Filter by Icon Type

Filters by the chunk's icon type.

```
@@@_Character.Filter(icon=Normal)_@@@
```

Available icon types:

- **Normal**: Regular user-created chunk
- **Group**: Group chunk
- **File**: Chunk added from a file
- **Folder**: Chunk added from a folder

## Modifiers

### Regex Mode (`*`)

Adding `*` to the condition type enables regex mode.

```
@@@_Character.Filter(name*=^Chapter\d+)_@@@
```
> Gets chunks whose name starts with "Chapter" followed by digits

You can also specify regex in `/pattern/flags` format:

```
@@@_Character.Filter(name=/smile|laugh/i)_@@@
```
> Contains "smile" or "laugh" (case insensitive)

### Exclusion Mode (`!`)

Adding `!` to the condition type keeps items that do NOT match (NOT condition).

```
@@@_Character.Filter(tag!=draft)_@@@
```
> Gets chunks that do NOT have the "draft" tag

### Combining Regex and Exclusion (`*!`)

`*` and `!` can be combined (order is `*!`).

```
@@@_Character.Filter(name*!=^temp)_@@@
```
> Gets chunks whose name does NOT start with "temp"

## Combining Multiple Conditions

Chaining multiple Filters creates AND conditions.

```
@@@_Character.Filter(tag=main).Filter(icon=Normal)_@@@
```
> Chunks that have the "main" tag AND have Normal icon

## Usage Examples

### Filter by Tag and Name

```
@@@_Character.Target(all).Filter(tag=main).Filter(name=hero)_@@@
```
> From all chunks, get those with the "main" tag and "hero" in their name

### Exclude Specific Folder

```
@@@_Background.Target(all).Filter(treePath!=Archive/**)_@@@
```
> Gets chunks outside the "Archive" folder

### Regex Pattern Matching

```
@@@_Effects.Filter(content*=\b(fire|flame|burn)\b)_@@@
```
> Gets chunks with "fire", "flame", or "burn" in their content

## Notes

- Filter types are **case insensitive** (`Name` = `name` = `NAME`)
- Normal mode uses **partial matching**, case insensitive
- If an invalid regex is specified, it automatically falls back to partial matching
- Filters with empty values (`name=`) are skipped

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category Template.md)
- [Target](01-Target.md)
- [Pick](03-Pick.md)
- [Sort](04-Sort.md)
- [Join](05-Join.md)
- [Edit](06-Edit.md)
- [TreePath](../../../../PromptTree/02-Glossary/01-TreePath.md)
- [Tag](../../../../PromptBrowser/01-Basics/04-Tag.md)
- [Favorite Query](../../../../AdvancedPanel/02-Glossary/04-Favorite Query.md)
- [Copy TreePath](../../../../PromptTree/04-Menu/04-Selected Copy Info/03-TreePath.md)
