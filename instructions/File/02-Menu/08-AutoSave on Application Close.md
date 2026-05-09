# AutoSave on Application Close
**AutoSave on Application Close**

## When to Use
- When you want to prevent forgetting to save when closing the application
- When you want changes to be automatically saved when you finish working
- When you want to save the trouble of manual saving
- When you want to avoid losing unsaved changes when switching projects

## What It Does
When this setting is enabled, the project is automatically saved when the application is closed. It also saves the previous project automatically when switching projects via [New Project](01-New%20Project.md) or [Open Project](02-Open%20Project.md).

A toggle menu with a checkmark shows the current state:
- ✓ Checked: Auto-save is enabled
- Unchecked: Auto-save is disabled (manual save required)

## How to Use
Click **File > AutoSave on Application Close** to toggle

## Notes
- This is an application-wide setting, not per-project
- When enabled, the current project state is automatically saved at the following moments:
  - When the window is closed
  - When switching projects via [New Project](01-New%20Project.md) / [Open Project](02-Open%20Project.md)
- When disabled, a warning is displayed on app exit if there are unsaved changes
- For [Reload Current Project](04-Reload%20Current%20Project.md) / [Close Project](05-Close%20Project.md), saving only happens when the confirmation dialog's "Save" option is chosen (independent of this setting)

## Tips
- It is also recommended to use manual save (`Ctrl+S` / `Cmd+S`) during important work
- Combining with [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md) provides better data protection

## Related

- [Project](../01-Basics/01-File%20Menu%20Basics.md)
- [Save Project](06-Save%20Project.md)
- [Close Project](05-Close%20Project.md)
- [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md)
- [Create Backup](09-BackUp/02-Quick%20Backup/01-Create%20Backup%20Quick%20Backup.md)
- [BackUp](09-BackUp/README.md)
