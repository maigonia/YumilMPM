# Create Backup (Quick Backup)
**Create Backup (Quick Backup)**

## When to Use
- When you want to quickly create a lightweight backup
- When you want to save only settings and prompt data
- When you want to perform regular backups efficiently
- When you want to save storage space while backing up

## What It Does
Creates a lightweight ZIP backup containing only essential project data.

The following folders and files are backed up:
- `/Data` - Categories, prompts, and settings data
- `/QueuePatterns` - Queue pattern data
- `/settings` - Application settings
- `api_server.json` - API server settings
- `category_tree.json` - Category tree structure
- `global_tags.json` - Global tags
- `project_state.json` - Project state

Other folders (Images, models, etc.) are not included.

## How to Use
Select **File > BackUp > Quick Backup > Create Backup**

On first use, an explanation dialog about backed up items is displayed.

## Notes
- This menu is unavailable if no project is open
- The current project is automatically saved before backup creation
- Backup files are saved in the `/BackUp` folder within the project folder
- File names use the format `backup_YYYYMMDD_HHmmss.zip` (e.g., `backup_20240315_143022.zip`)
- If a custom backup folder is configured, backups are saved there

## Tips
- For a complete backup, use [Full Backup](../01-Full%20Backup.md) instead
- [Enable Auto Backup](06-Enable%20Auto%20Backup.md) creates this format of backup when the app closes
- Clean up old backups with [Delete Older Than 30 Days](04-Delete%20Older%20Than%2030%20Days.md) or [Keep Only Last 30 Backups](05-Keep%20Only%20Last%2030%20Backups.md)

## Related

- [BackUp](../README.md)
- [Full Backup](../01-Full%20Backup.md)
- [Enable Auto Backup](06-Enable%20Auto%20Backup.md)
- [Restore From Backup](07-Restore%20From%20Backup.md)
- [Open Backup Folder](02-Open%20Backup%20Folder.md)
- [Backup Folder Settings](03-Backup%20Folder%20Settings.md)
- [Delete Older Than 30 Days](04-Delete%20Older%20Than%2030%20Days.md)
- [Keep Only Last 30 Backups](05-Keep%20Only%20Last%2030%20Backups.md)
