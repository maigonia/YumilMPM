# Tag Manager

**Tag Manager**

## When to Use

- When you want to see a list of all tags in the project
- When you want to organize (delete/merge) unnecessary tags
- When you want to understand tag usage
- When you want to rename tags or edit descriptions
- When you want to see tags used in a specific category

## What It Does

Displays all tags in the project and provides management operations including add, delete, rename, description editing, and merge. The left pane category tree allows filtering to a specific category's view.

## Dialog Layout

### Category Tree (Left Pane)

The left pane displays a category tree.

- Selecting **All Categories** shows all tags in the project (default)
- Selecting a specific category shows only tags used in that category's direct chunks
- A badge next to each category name shows the number of unique tags used in that category

### Tag List Table (Right Pane)

| Column          | Content                                                            |
| --------------- | ------------------------------------------------------------------ |
| Checkbox        | Select for operations (header checkbox for select all/deselect all) |
| Name            | Tag name. Double-click to rename                                   |
| Description     | Tag description. Double-click to open a multi-line text area for editing. Ctrl+Enter to confirm, Esc to cancel |
| Protected       | Protection status. Check to prevent deletion when usage count is 0 |
| Usage           | Number of prompts using this tag (shows category-specific count when a category is selected) |
| Created         | Tag creation date                                                  |

Tags are displayed in order of usage count (most used first).

### Toolbar

| Button          | Operation                      | Condition         |
| --------------- | ------------------------------ | ----------------- |
| **Add**         | Add a new tag                  | —                 |
| **Delete**      | Delete selected tags           | 1 or more selected |
| **Merge**       | Merge selected tags into one   | 2 or more selected |
| **Recalculate** | Recalculate usage counts       | —                 |
| **Search box**  | Filter by tag name             | —                 |

## Main Operations

### Adding Tags

1. Click the **Add** button
2. Enter the tag name in the text field
3. Press Enter or click "Add" to add

### Renaming Tags

1. Double-click the tag name
2. Enter the new name
3. Press Enter to confirm, Esc to cancel

### Editing Tag Descriptions

1. Double-click the Description column
2. A multi-line text area appears
3. Ctrl+Enter to confirm, Esc to cancel
4. Clicking outside (blur) also saves

**Tips**: Writing descriptions helps AI understand what each tag means. When using [Suggest Tags with AI](../../PromptTree/04-Menu/01-Selected/08-Suggest Tags with AI.md) to get tag suggestions, or when referencing tag information from [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) to have AI organize or create tags, descriptions lead to more accurate results.

### Deleting Tags

1. Select tags to delete using checkboxes
2. Click the **Delete** button
3. A confirmation dialog appears
   - If tags are in use, a warning is shown that tags will also be removed from associated prompts

### Merging Tags

1. Select 2 or more tags using checkboxes
2. Click the **Merge** button
3. Select the target tag in the merge dialog
4. Optionally change the merged tag name
5. Confirm to replace all source tags with the target tag

### Recalculating Usage Counts

Click the **Recalculate** button to recount tag usage from actual prompt data.
(Provided for repair in case counts become out of sync due to bugs.)

## Category-Scoped Operations

When a category is selected in the left pane, the behavior of **Delete** and **Merge** changes.

### Category-Scoped Delete

- Instead of deleting tags from the entire project, tags are **removed only from chunks in the selected category**
- If a tag's project-wide usage count reaches 0 as a result, it is also automatically deleted from the registry
- Tags still used in other categories remain in the registry

### Category-Scoped Merge

- Source tags are replaced with the target tag only in chunks within the selected category
- Tag renaming is applied globally

## Notes

- Operation results are shown in the status bar (below the selection/total count)
- Duplicate tag names are not allowed (case-insensitive)
- Changes are applied in real-time (no Save button needed)
- Descriptions can be referenced from [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) via `env.tagDefinitions` / `env.chunk.tagDefinitions` / `env.getCategory("X").tagDefinitions`

## Related

- [Tag](../../PromptBrowser/01-Basics/04-Tag.md)
- [env.globalTags](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/06-env.globalTags.md)
- [Suggest Tags with AI](../../PromptTree/04-Menu/01-Selected/08-Suggest Tags with AI.md)
- [Bulk Suggest Tags with AI](../../PromptTree/04-Menu/05-Checked/05-Bulk Suggest Tags with AI.md)
