# New Project
**New Project...**

## When to Use
- When you want to start a new prompt collection
- When you want to manage prompts for a different theme or purpose
- When you want to work in an environment independent of existing projects

## What It Does
Creates a new empty project. A project includes data such as [Category](../../AdvancedPanel/01-Basics/01-Category%20Template%20Tab.md), [Prompt](../../PromptTree/01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md), [Tag](../../PromptBrowser/01-Basics/04-Tag.md), [Memo](../../PromptBrowser/01-Basics/02-Memo.md), and [Image](../../PromptBrowser/01-Basics/01-Image.md).

## How to Use
1. Select **File > New Project...** (or shortcut `Ctrl+N`)
2. A folder selection dialog appears
3. Click the "Browse..." button
4. Select an **empty folder** (a new folder can also be created)
5. Click the "Create Project" button
6. The new project is created and work can start immediately

## Notes
- The selected folder **must be empty**
- If a folder with an existing project is selected, a warning is displayed
- The following folder structure is automatically generated when creating a project:
  - `/Data` - Categories, chunks, settings, and other data
  - `/Prompts` - Output destination for generated prompts
  - `project_state.json` - Project marker file
- If a project is currently open, [AutoSave on Application Close](08-AutoSave%20on%20Application%20Close.md) / [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md) (when enabled) silently save and back up the previous project before switching (no dialog)

## Related

- [Project](../01-Basics/01-File%20Menu%20Basics.md)
- [Open Project](02-Open%20Project.md)
- [Close Project](05-Close%20Project.md)
- [Save Project](06-Save%20Project.md)
- [Initial Setup](../../GlobalSettings/03-Tips/01-Recommended%20Initial%20Settings.md)
- [AutoSave on Application Close](08-AutoSave%20on%20Application%20Close.md)
- [Enable Auto Backup](09-BackUp/02-Quick%20Backup/06-Enable%20Auto%20Backup.md)
