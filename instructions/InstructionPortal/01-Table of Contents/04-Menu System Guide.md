# Menu System Guide

## 1. The Role of Menus in This App

In Yumil MPM, menus are the starting point for all operations.

MPM's operation system has a unified design where **each command has 4 access methods**:

| Access Method | How to Open | Feature |
|---|---|---|
| Top Menu | Click the menu bar | Browse all commands |
| Context Menu | Right-click on a panel | Quick access to panel-related commands |
| Command Palette | F1 key | Find commands quickly via text search |
| Shortcut Keys | Press assigned keys | Execute commands fastest |

All of these execute the same command. Whether you select "Copy" from the top menu, choose it from the context menu, run it from the command palette, or press a shortcut key, the result is the same.

The natural way to use the app is to learn operations from the top menu first, then assign shortcut keys to frequently used operations.

## 2. Menu Structure

The menu bar at the top of the screen has 9 top-level menus, each corresponding to a panel or feature in the app.

| Menu | Corresponding Panel/Feature | Main Operations |
|---|---|---|
| **File** | Entire project | Create, save, open, backup |
| **CategoryTree** | Category tree | Add, delete, move, rename categories |
| **PromptTree** | Prompt tree | Add, delete, check, expand prompts |
| **PromptEditor** | Prompt editor | Copy, search, plugins, syntax highlight |
| **PromptGeneration** | Prompt generation | Once generation, timer, API, output settings |
| **BrowseSelectedPrompt** | Image/memo/tag panel | Panel display toggle, image operations, tag management |
| **AdvancedPanel** | Advanced panel | Category template, favorites, search |
| **GlobalSettings** | App settings | Language, theme, API key, window settings |
| **Utility** | Utility | Tutorial, debug, data check |

### Menu Item Types

Menus contain the following types of items:

- **Normal items**: Clicking executes the command
- **Checkable items**: Toggle items that switch ON/OFF (e.g., dark mode, syntax highlight)
- **Submenus**: Hovering over items with a ▶ mark reveals more items
- **Separators**: Dividing lines showing boundaries between item groups

## 3. Context Menu

Right-clicking on each panel displays a context menu with operations related to that panel.

Context menu contents are the same as the top menu. It's efficient because you can operate without moving focus to the panel and requires less mouse movement.

### Reserved Shortcuts

Context menus may display reserved shortcuts. These are shown in blue text and cannot be changed:

| Key | Operation |
|---|---|
| F1 | Command Palette |
| F2 | Rename |
| Delete | Delete |
| Ctrl+C | Copy |
| Ctrl+V | Paste |
| Ctrl+X | Cut |
| Ctrl+Z | Undo |
| Ctrl+Y | Redo |
| Ctrl+A | Select All |
| Ctrl+F | Find |
| Ctrl+H | Replace |

These keys are processed locally by each panel, so they cannot be assigned as top menu shortcuts.

## 4. Command Palette

Press the **F1** key to open the Command Palette. You can call it with **F1** regardless of where focus is in the app.

The Command Palette is a tool for searching and quickly executing commands via text input. All commands that exist in menus can also be used from the Command Palette.

### How to Use

1. Press the **F1** key
2. Type part of the command name (e.g., "save", "copy", "dark")
3. Select the target command from the candidate list
4. Press Enter to execute

### Features

- **Fuzzy search**: Search by partial command name
- **State display**: Toggle items show their current ON/OFF state
- **Fast access**: Operate with keyboard only, without opening menus

## 5. Shortcut Keys

You can assign shortcut keys to frequently used operations.

### How to Set Shortcuts

1. Open the top menu
2. **Alt+click** the item you want to set a shortcut for
3. The shortcut setting dialog opens
4. Press the desired key combination (e.g., Ctrl+Shift+S)
5. Click "OK"

### Key Combinations

The following modifier key and regular key combinations are available:

- **Ctrl** + key
- **Alt** + key
- **Shift** + key
- **Ctrl+Shift** + key
- **Ctrl+Alt** + key
- Other modifier key combinations

### Conflict Detection

When you try to set a key combination that's already in use, the conflict is detected. You can choose to replace the existing shortcut or select a different key.

### Removing Shortcuts

1. **Alt+click** the target item in the top menu
2. Click "Clear" in the shortcut setting dialog
3. Click "OK"

### Shortcut Display

Assigned shortcuts are displayed on the right side of menu items.

## 6. Accessing Instructions

If you want to learn more about how to use each menu, you can access instructions (help) in two ways.

### Method 1: Menu "Instruction" Item

At the bottom of each top menu, there is an "**Instruction**" item. Click it to open the instruction window for that menu.

### Method 2: Right-Click

**Right-click** a menu item to directly open the instruction for that item.

For example, right-clicking "Find" in the PromptEditor menu will display the instruction on how to use Find.

This method lets you quickly check help for any operation you're curious about.
