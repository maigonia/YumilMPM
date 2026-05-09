# Project Slots Settings
**Project Slots Settings**

## When to Use
- When you want to switch quickly to projects opened often
- When you want to skip opening the folder selection dialog every time
- When you want to manage project groups by purpose (e.g., Portrait, Anime)

## What It Does

### Slot Sets

App-wide link lists for project switching can be created. Each link list is called a **slot set**.

For example, an "image projects" slot set that gathers image-related projects, a "video projects" set, and so on — multiple project lists can be created. Up to **20 slots** fit inside a single set.

Slot sets, once created, are shared across all projects.

### Assigning Slot Sets

Existing slot sets can be assigned to the current project. Once assigned, the projects in those sets appear as menu items under **File > Project Slots**. Multiple sets can be assigned at the same time.

The menu, keyboard shortcuts, command palette, and toolbar buttons make it easy to jump between projects.

```
File > Project Slots >
  [project 1 from image set]
  [project 2 from image set]
  ────
  [project 1 from video set]
  ────
  Settings...
```

### When You Want a Similar Project

If the goal is "create a new themed project based on an existing one" or "duplicate an existing project as a derivative," this app does not yet provide a dedicated export feature, but folder copy or partial overwrite can be used. See [Exporting and Migrating Data](../../01-Basics/03-Exporting and Migrating Data.md) for details.

## How to Use

### First-time Use
1. Choose **File > Project Slots > Settings...**
2. The "No slot sets have been created yet" prompt appears
3. Enter a set name (e.g., `Portrait`) and press **New Set**
4. The dialog switches to the normal layout with the new set created and automatically assigned to this project

### Add a Slot
1. Make sure the target set is checked under "Sets shown in this project" at the top
2. Pick the set to edit from the dropdown in the middle
3. Press **Register Slot** to add an empty row
4. Press the **folder icon** to choose the project folder
5. The name is auto-filled with the folder name when empty. It can be replaced with any name
6. Press **OK** to confirm

### Create Another Set
1. Press the **+** (New Set) button next to the dropdown
2. Enter the set name → create
3. The new set joins the dropdown
4. Optionally check it under the assignment section to assign to this project

### Assign a Set to Another Project
Slot sets are shared app-wide, so opening another project and the settings dialog shows the same set list. Toggle the checkboxes to change assignments.

### Unregister a Slot
1. Press the **✕ button** on the right of the row in the dialog
2. Press **OK** to confirm

### Delete a Set
1. Pick the target set in the dropdown
2. Press the **trash icon** → confirm in the dialog
3. Press **OK** to confirm

### Change a Display Name
Edit the name input directly in the dialog and press **OK** to save.

### Rename a Set
Press the **pencil icon** next to the dropdown → inline-edit → confirm with Enter or OK.

## Notes

- Slot set changes (add, rename, delete) are saved when **OK** is pressed
- When a slot is clicked to switch projects, the currently open project is automatically saved and backed up first (when [AutoSave on Application Close](../08-AutoSave on Application Close.md) / [Enable Auto Backup](../09-BackUp/02-Quick Backup/06-Enable Auto Backup.md) are enabled)
- If a slot's folder is deleted or moved outside the app, clicking that slot shows an error and cannot open the project. Either unregister the slot in settings or pick the correct folder again
- Deleting a slot set does not affect other projects. If a deleted set was assigned to another project, that project will simply drop the assignment the next time it is opened
- A single slot set can hold up to **20** slots. There is no limit on how many slot sets can be created

### Changing PCs or Using on Another PC

Slot sets are stored in the **user settings folder of the current PC** (`%APPDATA%\YumilMPM\` on Windows, `~/Library/Application Support/YumilMPM/` on Mac). When moving to a new PC or wanting to use the same slot sets on another PC, this file can be copied to carry them over.

Pressing the **"Open File Location"** button at the bottom-left of the settings dialog opens the storage location in Explorer (Finder on Mac). A file named `slot_sets.json` is in that folder.

Steps:

1. On the old PC, press "Open File Location" → copy `slot_sets.json`
2. On the new PC, press "Open File Location" the same way → paste it into the same folder (replace the existing `slot_sets.json` if any)
3. Restart the app on the new PC → slot sets are restored

> Carrying only the project folder does not carry slot sets (only the assignment — which sets to use — is recorded inside the project). Always copy `slot_sets.json` together with the project folder.

## Tips
- Pick a set name that conveys the purpose (e.g., `Portrait`, `Work`)
- A shared "Common" set assigned to all projects is a convenient pattern for frequently used projects
- Per-purpose groups can be expressed by assigning specific sets to specific projects only

## Related

- [New Project](../01-New Project.md)
- [Open Project](../02-Open Project.md)
- [Close Project](../05-Close Project.md)
- [Save Project](../06-Save Project.md)
- [AutoSave on Application Close](../08-AutoSave on Application Close.md)
- [Enable Auto Backup](../09-BackUp/02-Quick Backup/06-Enable Auto Backup.md)
- [Exporting and Migrating Data](../../01-Basics/03-Exporting and Migrating Data.md)
