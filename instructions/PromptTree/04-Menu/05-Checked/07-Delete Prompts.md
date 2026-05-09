# Delete Prompts

**Delete Prompts**

## When to Use

- When you want to delete multiple prompts at once
- When you want to batch clean up unnecessary prompts
- When you want to delete including folders

## What It Does

Batch deletes all checked prompts. Descendant prompts are also deleted.

## How to Use

1. Check the prompts you want to delete
2. Select **PromptTree > Checked > Delete Prompts** from the menu
3. Review the deletion targets in the confirmation dialog
4. Click **Delete**

## Confirmation Dialog

A confirmation dialog is displayed before deletion.

### Display Content

- **List of top-level prompts to be deleted**
- **Number of descendants** for each prompt
- **Total number of prompts to be deleted** (including descendants)

### Safety Features

- **Cancel button is auto-focused** (prevents accidental operation)
- Can be cancelled with the Esc key
- Warning message "This operation cannot be undone"

## How Deletion Works

### Top-Level Only Processing

When both a parent and child are checked, only the **parent** is listed as a deletion target. Children are automatically deleted when the parent is deleted.

```
Example:
☑ Folder A          ← Listed as deletion target
  ☑ Prompt 1        ← Not shown in list (deleted with parent)
  ☑ Prompt 2        ← Not shown in list (deleted with parent)
☑ Prompt 3          ← Listed as deletion target
```

### Processing During Deletion

The following processing is performed automatically:

1. **Remove from prompt tree** - Delete selected prompts and descendants
2. **Update tag usage counts** - Decrement tag counts for deleted prompts
3. **Clear check state** - Uncheck deleted prompts

## Behavior During Cut & Paste

After cutting and pasting prompts, a dialog asks whether to delete the original prompts.

- **Delete Original**: Delete the original prompts
- **Keep Original**: Keep the original prompts (same behavior as copy)

## Cautions

- **Deletion cannot be undone**
- Not available when no prompts are checked
- Deleting a prompt with descendants also deletes all descendants

## Related

- [Check State](../../01-Basics/01-Concepts/01-Understanding Check State.md)
- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Delete Prompts](../01-Selected/02-Delete Prompts.md)
- [Delete Chunk and Files](../01-Selected/03-Delete Chunk and Files.md)
