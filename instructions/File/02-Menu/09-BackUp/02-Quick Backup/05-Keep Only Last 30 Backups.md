# Keep Only Last 30 Backups
**Keep Only Last 30 Backups**

## When to Use
- When you want to keep the number of backups constant
- When you want to save storage space
- When you want to clean up the backup folder

## What It Does
Keeps the 30 most recent backup files and deletes older ones. Useful when you want to manage by count rather than date.

## How to Use
1. Select **File > BackUp > Quick Backup > Keep Only Last 30 Backups**
2. A confirmation dialog appears
3. Click **Clean Up** to execute

## Notes
- A confirmation dialog is always displayed before deletion
- The number of deleted files is shown in the status bar
- Backup files are sorted by creation date, and the newest 30 are kept
- If there are 30 or fewer backups, nothing is deleted
- **This operation cannot be undone**

## Tips
- Combine with [Delete Older Than 30 Days](04-Delete Older Than 30 Days.md) for more effective backup management
- If [Enable Auto Backup](06-Enable Auto Backup.md) is active, it is recommended to periodically clean up with this feature

## Related

- [BackUp](../README.md)
- [Delete Older Than 30 Days](04-Delete Older Than 30 Days.md)
- [Enable Auto Backup](06-Enable Auto Backup.md)
- [Create Backup](01-Create Backup Quick Backup.md)
- [Backup Folder Settings](03-Backup Folder Settings.md)
- [Open Backup Folder](02-Open Backup Folder.md)
