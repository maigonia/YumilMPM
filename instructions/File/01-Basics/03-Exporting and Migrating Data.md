# Exporting and Migrating Data

This app does **not yet provide a dedicated export feature**. To take project data elsewhere or migrate part of it into a new project, use one of the manual workarounds below.

## Duplicating the Entire Project

The simplest and most reliable approach is to **copy the project folder** as a whole using Explorer (Finder).

- All data (categories, prompts, images, settings) is copied completely
- The copied folder can be opened directly via [Open Project](../02-Menu/02-Open%20Project.md)
- For backup purposes, also consider [Full Backup](../02-Menu/09-BackUp/01-Full%20Backup.md) / [Create Backup](../02-Menu/09-BackUp/02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md)

## Migrating Only Prompt Data into a New Project

Copy the following files/folders from the original project and **overwrite** them into the new project folder:

- `Data/` folder — categories, prompts, and chunks
- `category_tree.json` — category tree structure
- `global_tags.json` — tag list

This carries over prompts, categories, and tags only. Images (`/Images`), AI models (`/models`), generation settings, output settings, and backups (`/BackUp`) are not carried over.

### Steps

1. Quit the app (or close the target project via [Close Project](../02-Menu/05-Close%20Project.md))
2. Copy the three items above from the original project folder
3. Overwrite them at the same paths in the new project folder
4. Open the new project in the app via [Open Project](../02-Menu/02-Open%20Project.md)

> If files are modified externally while the app is running, the changes may be overwritten when the app saves. Always quit the app or close the project before performing this operation.

## Editing JSON Directly

For users who understand the JSON structure, the files inside `Data/` and `category_tree.json` / `global_tags.json` can be **edited directly** for finer-grained migration or merging.

- Always create a backup with [Create Backup](../02-Menu/09-BackUp/02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md) before editing
- Breaking the structure will cause load failures
- Watch out for ID collisions (conflicting category or tag IDs can corrupt data)

## Notes

- A dedicated export feature is not currently planned
- Folder copy or partial overwrite remains the reliable approach for taking data out
- The data location can be opened in Explorer via [Open Data Folder](../02-Menu/07-Open%20Data%20Folder.md)

## Related

- [Open Project](../02-Menu/02-Open%20Project.md)
- [New Project](../02-Menu/01-New%20Project.md)
- [Close Project](../02-Menu/05-Close%20Project.md)
- [Save Project](../02-Menu/06-Save%20Project.md)
- [Open Data Folder](../02-Menu/07-Open%20Data%20Folder.md)
- [Full Backup](../02-Menu/09-BackUp/01-Full%20Backup.md)
- [Create Backup](../02-Menu/09-BackUp/02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md)
- [Restore From Backup](../02-Menu/09-BackUp/02-Quick%20Backup/07-Restore%20From%20Backup.md)
