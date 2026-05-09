# Enable Auto Backup
**Enable Auto Backup**

## When to Use
- When you want automatic backups when closing the app
- When you tend to forget manual backups
- When you want to save the trouble of regular backups
- When you want a backup before switching projects, just in case

## What It Does
When this setting is enabled, a backup is automatically created at the following moments:

- When the application is closed
- When switching projects via [New Project](../../01-New Project.md) / [Open Project](../../02-Open Project.md)
- When choosing "Save" in the confirmation dialog of [Reload Current Project](../../04-Reload Current Project.md) / [Close Project](../../05-Close Project.md)

A toggle menu with a checkmark shows the current state:
- ✓ Checked: Auto backup is enabled
- Unchecked: Auto backup is disabled

## How to Use
Click **File > BackUp > Quick Backup > Enable Auto Backup** to toggle

On first activation, an explanation dialog about backed up items is displayed.

## Notes
- Auto backups are created in the "quick backup" format
- Complete backups (including images/models) are not created automatically
- Backups are saved in the `/BackUp` folder within the project folder (or a custom configured folder)
- This does not run on a fixed interval (only at exit / project switch moments)
- If "Without Saving" is chosen in [Reload Current Project](../../04-Reload Current Project.md) / [Close Project](../../05-Close Project.md), no backup is created either (save and backup are treated as a pair)

## Tips
- Combining with [AutoSave on Application Close](../../08-AutoSave on Application Close.md) ensures better data protection
- If auto backup is enabled, it is recommended to periodically clean up with [Delete Older Than 30 Days](04-Delete Older Than 30 Days.md) or [Keep Only Last 30 Backups](05-Keep Only Last 30 Backups.md)

## Related

- [BackUp](../README.md)
- [AutoSave on Application Close](../../08-AutoSave on Application Close.md)
- [Create Backup](01-Create Backup Quick Backup.md)
- [Full Backup](../01-Full Backup.md)
- [Restore From Backup](07-Restore From Backup.md)
- [Backup Folder Settings](03-Backup Folder Settings.md)
- [Delete Older Than 30 Days](04-Delete Older Than 30 Days.md)
- [Keep Only Last 30 Backups](05-Keep Only Last 30 Backups.md)
