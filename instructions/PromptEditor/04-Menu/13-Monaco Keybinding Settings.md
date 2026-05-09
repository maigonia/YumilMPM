# Monaco Keybinding Settings

**Monaco Keybinding Settings**

## When to Use

- When you want to disable the editor's default shortcuts
- When specific keybindings conflict with other shortcuts
- When you want to simplify editor operations

## What It Does

Allows you to individually enable/disable default keybindings of Monaco Editor (the foundation of the prompt editor).

## How to Use

1. Select **PromptEditor > Monaco Keybinding Settings** from the menu
2. A dialog appears
3. Expand categories and toggle each command's checkbox to enable/disable
4. Click **OK** to save

## Command Categories

Commands are classified into the following categories:

- **Basic Editing**: Basic editing operations
- **Multi-Cursor**: Multi-cursor operations
- **Line Operations**: Line operations
- **Selection**: Selection operations
- **Find and Replace**: Find and replace
- **Go to**: Jump operations
- **Folding**: Folding operations

## Default Settings

By default, all commands except those essential for basic editor operations are disabled. This provides a simple and predictable editing environment.

### Default Enabled Commands (Essential Commands)

The following commands are always enabled and cannot be disabled:

- **Find** (Ctrl+F): Find
- **Replace** (Ctrl+H): Replace
- **Cut** (Ctrl+X): Cut
- **Copy** (Ctrl+C): Copy
- **Paste** (Ctrl+V): Paste
- **Undo** (Ctrl+Z): Undo
- **Redo** (Ctrl+Y): Redo
- **Select All** (Ctrl+A): Select All

Note: **[Command Palette](../01-Basics/01-Features/02-Command%20Palette.md)** (F1) is always enabled and not configurable.

### Default Disabled Commands

All commands other than the above (Multi-Cursor, Line Operations, Folding, Format, Navigation, Refactor, etc.) are disabled by default. They can be individually enabled as needed.

## Buttons

- **Enable All**: Enable all commands
- **Disable All**: Disable all commands (except Essential Commands)
- **Reset**: Restore to default settings

## Notes

- App restart may be required after changing settings
- Basic operations (copy, paste, etc.) still work through other shortcuts even when disabled

## Related

- [PromptEditor](../01-Basics/03-Prompt%20Editor.md)
- [Shortcuts](../01-Basics/04-Keyboard%20Shortcuts.md)
- [Command Palette](../01-Basics/01-Features/02-Command%20Palette.md)
