# Full Backup
**Full Backup**

## When to Use
- When you want to copy the entire project to another location
- When you want a complete backup including images and model data
- When you want to save the complete state before making major changes
- When you want to save the project to an external drive or cloud storage

## What It Does
Copies the entire project folder to a specified location. All data is included:
- Categories, prompts, settings data (/Data)
- Generated prompts (/Prompts)
- Imported images (/Images)
- AI model data (/models)
- Backup folder (/BackUp)

## How to Use
1. Select **File > BackUp > Full Backup...**
2. A dialog appears to select the backup destination folder
3. Select the destination folder
4. The backup is created and a completion message is displayed

## Notes
- This menu is unavailable if no project is open
- The previous backup destination folder is remembered and used as the default next time
- The backup is a folder copy, not a ZIP file
- May take time depending on project size, as it includes images and model data

## Tips
- It is recommended to take a full backup before and after important milestones
- For a lightweight backup, use [Create Backup](02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md) instead

## Related

- [BackUp](README.md)
- [Project](../../01-Basics/01-File%20Menu%20Basics.md)
- [Create Backup](02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md)
- [Enable Auto Backup](02-Quick%20Backup/06-Enable%20Auto%20Backup.md)
- [Restore From Backup](02-Quick%20Backup/07-Restore%20From%20Backup.md)
- [Open Backup Folder](02-Quick%20Backup/02-Open%20Backup%20Folder.md)
