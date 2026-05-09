# Keyboard User Guide

This app is designed so you can operate it efficiently with just the keyboard.

## Moving Between Panels

Press **F6** to cycle focus between panels. The focused panel is highlighted.

| Panel | Description |
|-------|-------------|
| Category Tree | Select and manage categories |
| Prompt Tree | Select and check prompts |
| Prompt Editor | Edit prompt content |
| Generation Controller | Execute and control generation |

## Get Focus Menu

Each menu has a **Get Focus** command that moves focus directly to a specific panel or tab. Unlike F6 cycling, this jumps straight to the target panel.

| Menu | Get Focus Target |
|------|------------------|
| CategoryTree | Category Tree |
| PromptTree | Prompt Tree |
| PromptTree > Search Panel | Search Panel |
| PromptEditor | Prompt Editor |
| PromptGeneration | Generation Controller |
| BrowseSelectedPrompt > Image / Memo / Tag | Each browser panel |
| AdvancedPanel > Each tab | Specific tab in Advanced Panel |

Assign shortcut keys to Get Focus commands for quick keyboard-only panel switching.

## Command Palette

Press **F1** to open the Command Palette. It can be invoked from anywhere in the app.

1. Press **F1**
2. Type part of the command name (e.g., "save", "check", "dark")
3. Select from candidates and press **Enter** to execute

All menu commands can be used from the Command Palette.

## Tree Operations

In the Category Tree and Prompt Tree, the following key operations are available:

| Key | Operation |
|-----|-----------|
| ↑ / ↓ | Move selection |
| ← | Collapse folder / move to parent |
| → | Expand folder |
| Space | Check / uncheck |
| F2 | Rename |
| Delete | Delete |

## Editor Operations

In the Prompt Editor, in addition to the [Command Palette](../../PromptEditor/01-Basics/01-Features/02-Command Palette.md), the following operations are available:

| Key | Operation |
|-----|-----------|
| Ctrl+Z | Undo |
| Ctrl+Y | Redo |
| Ctrl+F | Find |
| Ctrl+H | Replace |
| Ctrl+A | Select All |

## Setting Shortcut Keys

**Alt+click** a menu item to assign a shortcut key to that operation. Assign shortcuts to frequently used operations.

See the Shortcut Keys chapter in [Menu System Guide](04-Menu System Guide.md) for details.

## Related

- [Menu System Guide](04-Menu System Guide.md)
- [Command Palette](../../PromptEditor/01-Basics/01-Features/02-Command Palette.md)
- [Shortcuts](../../PromptEditor/01-Basics/04-Keyboard Shortcuts.md)
