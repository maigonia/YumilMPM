# Remove Duplicate Lines

**Remove Duplicate Lines**

## What It Does

Removes duplicate lines within the selected text, keeping only the first occurrence.

## How to Use

1. Select text containing duplicates
2. Select **Edit SelectedText with Plugins > Remove Duplicate Lines** from the menu
3. Duplicate lines are removed

## Example

- Input:
```
red hair
blue eyes
red hair
smile
```
- Output:
```
red hair
blue eyes
smile
```

## Notes

- Comparison ignores leading/trailing whitespace (`red hair` and `  red hair  ` are treated as the same line)
- Empty lines are not removed and are kept as-is

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Remove Duplicate Tags](06-Remove Duplicate Tags.md)
- [Sort Lines Alphabetically](08-Sort Lines Alphabetically.md)
