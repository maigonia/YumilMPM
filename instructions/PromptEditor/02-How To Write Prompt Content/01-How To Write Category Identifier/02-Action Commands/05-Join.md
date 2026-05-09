# Join

**Action for joining chunks**

## Overview

The Join action joins chunks selected by [Pick](03-Pick.md) with a specified separator into a single string.

## Syntax

```
@@@_CategoryName.Join(separator)_@@@
```

## Default Value

When Join is omitted, chunks are joined with `,\n` (comma and newline).

```
@@@_CategoryName_@@@
↓ Equivalent to
@@@_CategoryName.Join(,\n)_@@@
```

When an empty parameter (`.Join()`) is specified, chunks are joined without any separator.

```
@@@_CategoryName.Join()_@@@
```
> Chunks are directly concatenated (no separator)

## Escape Sequences

The Join action supports the following escape sequences:

- `\n` → Newline
- `\t` → Tab

```
@@@_Character.Join(\n)_@@@
```
> Separated by newlines

```
@@@_Character.Join(\t)_@@@
```
> Separated by tabs

**Note**: Escape sequences are only needed for the **Join action**. In other parts of Category Identifiers (Target, Filter, Pick, Sort, Edit), characters can be written directly without special notation.

## Usage Examples

### Separate with Comma and Space

```
@@@_Character.Join(, )_@@@
```
> `Chunk1, Chunk2, Chunk3`

### Separate with Newlines

```
@@@_Character.Join(\n)_@@@
```
> Each chunk on a separate line

### Separate with Comma and Newline

```
@@@_Character.Join(,\n)_@@@
```
> Comma followed by newline

### Join Without Separator

```
@@@_Character.Join()_@@@
```
> `Chunk1Chunk2Chunk3`

### Separate with Arrow

```
@@@_Character.Join( -> )_@@@
```
> `Chunk1 -> Chunk2 -> Chunk3`

### Decorative Separator

```
@@@_Character.Join(\n====================\n)_@@@
```
> A divider line between each chunk

## Notes

- Any string can be specified as a separator
- Unicode characters can also be used (e.g., `Join(★★★)`)
- For a single chunk, no separator is inserted
- For an empty chunk array, an empty string is returned

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Target](01-Target.md)
- [Filter](02-Filter.md)
- [Pick](03-Pick.md)
- [Sort](04-Sort.md)
- [Edit](06-Edit.md)
