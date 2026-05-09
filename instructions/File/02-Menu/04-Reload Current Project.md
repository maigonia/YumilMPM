# Reload Current Project
**Reload Current Project**

## When to Use
- When you want to reflect the latest state after editing files externally in the project folder
- When the app behavior seems off and you want to refresh the data
- When you want to discard edits and revert to the last saved state

## What It Does
Reloads the currently open project from disk. All data in memory is cleared and the latest state is loaded from files.

## How to Use
1. Select **File > Reload Current Project**
2. A confirmation dialog appears
3. Choose one of the following:
   - **Save and Reload**: Save current changes before reloading
   - **Reload without Saving**: Discard changes and reload
4. The project is reloaded

## Notes
- Choosing "Reload without Saving" will **lose all unsaved changes**
- If "Save and Reload" is chosen and [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md) is on, a backup is also created automatically after saving
- After reloading, the following settings are also reloaded:
  - Font settings
  - Editor keybinding settings
  - Window position and size

## Related

- [Project](../01-Basics/01-File%20Menu%20Basics.md)
- [Open Project](02-Open%20Project.md)
- [Save Project](06-Save%20Project.md)
- [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md)
