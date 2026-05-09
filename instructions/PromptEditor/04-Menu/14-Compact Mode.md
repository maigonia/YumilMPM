# Compact Mode

**Compact Mode**

## When to Use

- When you want to focus only on editing prompts
- When you want to save screen space
- When you want to work side by side with other applications
- When you want to quickly input prompts and generate
- When you want to display the editor in a small size on a multi-display setup

## What It Does

Switches the window to a small display showing only the prompt editor. The following features provide a focused editing environment.

### Main Features

1. **Minimal UI**: Shows only the editor area
2. **Automatic window size adjustment**: Defaults to a compact 600x200px size
3. **State memory**: Saves window size and position separately for normal mode and compact mode
4. **High DPI support**: Accurate size adjustment considering display scaling settings
5. **Footer operations**: Access to main operations through the compact mode footer

### Hidden UI Elements

In compact mode, the following elements are hidden:

- Menu bar
- Category tree
- Chunk tree
- Chunk browser
- Generation controller
- Advanced category panel

## How to Use

### Entering Compact Mode

You can enable it using any of the following methods:

1. **From the menu**:
   - Select **PromptEditor > Compact Mode**
   - A checkmark appears when active

2. **First-time behavior**:
   - Window size changes to 600x200px (default)
   - Window is centered on screen
   - Normal mode window size and position are automatically saved

3. **Subsequent uses**:
   - Previous compact mode window size and position are restored
   - If you manually resize the window, that state is remembered

### Operations During Compact Mode

During compact mode, you can perform main operations from the footer:

- **Category selection**: Switch to a different category via dropdown
- **Gen button**: Generate prompts
- **Copy button**: Copy editor content to clipboard
- **Maximize button**: Return to normal mode

### Exiting Compact Mode

You can exit using any of the following methods:

1. **From the menu**:
   - Select **PromptEditor > Compact Mode** again
   - The checkmark is removed

2. **From the maximize button**:
   - Click the **maximize button** at the top right of the editor

3. **Exit behavior**:
   - Compact mode window size and position are automatically saved
   - Normal mode window size and position are restored

## Technical Details

### Window Size Management

Compact mode performs accurate window size management considering display scaling (High DPI).

- **Physical Pixels**: Physical pixel count (display's actual resolution)
- **Logical Pixels**: Logical pixel count (display unit in the OS)
- **Conversion**: Physical to Logical conversion ensures the same display size across different display environments

### Default Size

- **Width**: 600px (logical pixels)
- **Height**: 200px (logical pixels)
- **Position**: Automatically centered on screen

### State Saving

Two independent states are saved:

1. **Normal mode state**: Size and position before entering compact mode
2. **Compact mode state**: Size and position used in compact mode

This mechanism preserves window placement for each mode when switching.

## Notes

### Window Resizing

- The window can be freely resized during compact mode
- Resized dimensions are automatically saved and restored next time you enter compact mode

### Prompt Editing Features

- During compact mode, prompt selection and auto-saving of editing content work normally
- [AutoComplete](../01-Basics/01-Features/01-AutoComplete.md) is available
- Monaco Editor features (find, replace, etc.) are also available

### Multi-Display Environment

- Window position is saved in screen coordinates, so it's accurately restored in multi-display environments
- Position is remembered even when moving the window between different displays

### Recommended Usage

- **Quick input**: When you want to quickly input and generate prompts while working on other tasks
- **Partial screen placement**: Place the editor on the edge while keeping your main work area wide
- **Float display**: Use in combination with compact mode for always-on-top display

## Tips

1. **Adjusting initial size**: After first launch, resize to your preferred size and it will automatically launch at that size next time
2. **Fixing position**: Place the window at a frequently used position then switch modes to remember that position
3. **Quick operations from footer**: Category switching and the generate button allow working without displaying the tree
4. **Using both modes**: Use normal mode for complex editing and compact mode for simple input for maximum efficiency

## Related

- [PromptEditor](../01-Basics/03-Prompt%20Editor.md)
- [AutoComplete](../01-Basics/01-Features/01-AutoComplete.md)
