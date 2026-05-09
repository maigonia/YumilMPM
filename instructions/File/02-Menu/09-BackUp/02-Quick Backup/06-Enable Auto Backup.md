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
- When switching projects via [New Project](../../01-New%20Project.md) / [Open Project](../../02-Open%20Project.md)
- When choosing "Save" in the confirmation dialog of [Reload Current Project](../../04-Reload%20Current%20Project.md) / [Close Project](../../05-Close%20Project.md)

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
- If "Without Saving" is chosen in [Reload Current Project](../../04-Reload%20Current%20Project.md) / [Close Project](../../05-Close%20Project.md), no backup is created either (save and backup are treated as a pair)

## Tips
- Combining with [AutoSave on Application Close](../../08-AutoSave%20on%20Application%20Close.md) ensures better data protection
- If auto backup is enabled, it is recommended to periodically clean up with [Delete Older Than 30 Days](04-Delete%20Older%20Than%2030%20Days.md) or [Keep Only Last 30 Backups](05-Keep%20Only%20Last%2030%20Backups.md)

## Related

- [BackUp](../README.md)
- [AutoSave on Application Close](../../08-AutoSave%20on%20Application%20Close.md)
- [Create Backup](01-Create%20Backup%20Quick%20Backup.md)
- [Full Backup](../01-Full%20Backup.md)
- [Restore From Backup](07-Restore%20From%20Backup.md)
- [Backup Folder Settings](03-Backup%20Folder%20Settings.md)
- [Delete Older Than 30 Days](04-Delete%20Older%20Than%2030%20Days.md)
- [Keep Only Last 30 Backups](05-Keep%20Only%20Last%2030%20Backups.md)
