# Path Repair

**Path Repair...**

## When to Use

- When you've migrated a project to a different PC or OS and the root part of paths has changed, preventing files from loading correctly
- When a drive letter has changed (e.g., `D:` → `E:`)
- When you want to clean up references to files that no longer exist

## What It Does

Detects broken file paths (images, source files, etc.) linked to prompts and allows you to delete them or batch-replace the beginning part of paths.

The main use case is batch-fixing paths when the root part has changed due to OS migration or drive letter changes. Since file paths are stored as absolute paths, root changes commonly affect many paths.

> **Caution**: This feature directly modifies file paths in the project. Do not use it if you do not understand the operation. Incorrect operations could lead to data corruption.

## How to Use

Always create a backup before using this feature.

1. Select Utility > **Path Repair...** to open the dialog
2. Choose a tab based on your needs:
   - **Remove Broken Paths**: Detect and remove broken paths
   - **Path Remapping**: Batch-replace the beginning part of paths

## Dialog Operations

### Tab 1: Remove Broken Paths

1. Click the **Scan for Broken Paths** button to start scanning
2. Scan results are displayed in a list
   - Each path shows its file type (File / Folder / Image / Source / Memo / Setting)
   - The category name or chunk name the path belongs to is also shown
3. Check the paths you want to remove (**Select All** for bulk selection)
4. Click **Clear Checked Paths** to remove the selected paths

### Tab 2: Path Remapping

1. Enter the old path prefix in **Old base path** (or click **Browse** to select)
2. Enter the new path prefix in **New base path** (or click **Browse** to select)
3. A preview is automatically shown, displaying targets and results
   - Red lines (−): Before replacement
   - Green lines (+): After replacement
4. Review the content and click **Apply Remapping** to execute the batch replacement

## Notes

- Relative paths within the project (paths starting with `Images/`) are excluded from scanning and replacement
- Path separators (`\` and `/`) are automatically converted to match the target path
- Scanning alone makes no changes (safe until you execute removal or replacement)
- Paths saved in settings (backup destination, output destination, etc.) are also included as targets

## Related

- [Data Integrity Check](12-Run Data Integrity Check.md)
- [Project](../../File/01-Basics/01-File Menu Basics.md)
- [BackUp](../../File/02-Menu/09-BackUp/README.md)
