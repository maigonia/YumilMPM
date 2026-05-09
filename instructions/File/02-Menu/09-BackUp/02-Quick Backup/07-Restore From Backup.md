# Restore From Backup
**Restore from Backup**

## When to Use
- When you accidentally deleted data
- When you want to revert to a previous state
- When data may be corrupted
- When you want to restore a specific point in time

## What It Does
Restores project data from a backup file. Categories, prompts, settings, and other data are reverted to the state at the time of backup.

## How to Use
1. Select **File > BackUp > Quick Backup > Restore From Backup...**
2. A restore dialog appears
3. Select a backup using one of the following methods:
   - **Select from list**: Choose from the list of files in the backup folder
   - **Browse**: Select a ZIP file from an external location
4. Click "Restore"
5. Click "OK" in the confirmation dialog
6. Restoration completes and the project is automatically reloaded

## Notes
- **Restoring will overwrite current data** — if you have important data, [Create Backup](01-Create%20Backup%20Quick%20Backup.md) first
- When restoring from a quick backup, image and model folders remain as-is
- The backup list is displayed in creation date order (newest first)
- File sizes are also shown in the list to help select the appropriate backup

## Tips
- It is recommended to use [Create Backup](01-Create%20Backup%20Quick%20Backup.md) to back up the current state before restoring
- Check the date in the file name (`backup_YYYYMMDD_HHmmss.zip`) to select the backup from the desired point in time

## Related

- [BackUp](../README.md)
- [Project](../../../01-Basics/01-File%20Menu%20Basics.md)
- [Create Backup](01-Create%20Backup%20Quick%20Backup.md)
- [Full Backup](../01-Full%20Backup.md)
- [Enable Auto Backup](06-Enable%20Auto%20Backup.md)
- [Open Backup Folder](02-Open%20Backup%20Folder.md)
- [Open Project](../../02-Open%20Project.md)
