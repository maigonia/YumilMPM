# Menu to Button

Menu items can be placed as **icon buttons** on panels or on the leftmost vertical toolbar. This feature lets you invoke frequently used operations with a single click.

## 1. Two Placement Locations

Button-ized menus are placed in one of two locations:

| Location | Position | Eligible Menus |
|---|---|---|
| **Panel Button Row** | Directly below each panel's header (horizontal row) | Menus corresponding to that panel |
| **Global Vertical Toolbar** | Leftmost edge of the screen (vertical column) | Any menu |

A panel button row is hidden when it has no buttons. The global toolbar is likewise hidden when empty.

### Panel Mapping

The corresponding panel is auto-detected from the menu ID prefix:

| Menu | Corresponding Panel |
|---|---|
| CategoryTree | Category Tree |
| PromptTree (including plugins under "Add to Selected Prompt") | Prompt Tree |
| PromptEditor (including Edit plugins) | Prompt Editor |
| BrowseSelectedPrompt | Image/Memo/Tag panel |
| PromptGeneration | Prompt Generation |
| AdvancedPanel | Advanced Panel |
| File / GlobalSettings / Utility | No corresponding panel → can only be placed on the global toolbar |

## 2. Adding a Button

1. Open a top menu
2. **Ctrl+click** the menu item you want to button-ize
3. The icon picker dialog opens
4. Choose the placement:
   - **"Place on toolbar" checkbox OFF** (default): Added to the corresponding panel's button row
   - **Checkbox ON**: Added to the global vertical toolbar at the leftmost edge
5. Choose a color (15 colors available)
6. Choose an icon (searchable)
7. Click "Add"

For menus that have no corresponding panel (items under File, GlobalSettings, Utility), the checkbox is **forced ON** and the button can only be placed on the global toolbar.

## 3. Operating a Button

### Click

Clicking a button executes the same command as the original menu item.

When the original menu item is disabled (grayed out), the button automatically grays out and becomes disabled.

### Hover

Hovering shows the menu item name as a tooltip.

### Right-Click

Right-clicking a button opens a context menu with the following options:

- **Move Left / Move Right** (panel button rows): Swap the button with an adjacent one
- **Move Up / Move Down** (global vertical toolbar): Swap the button with an adjacent one
- **Delete this button**: Remove the button (the menu item itself is unaffected)

Move options in an edge direction are hidden for buttons at the leftmost/topmost or rightmost/bottommost position.

## 4. Saving and Restoring

Button placements, colors, icons, and ordering are saved to the **project file**.

This app is designed to persist all changes only when "Save Project" is run. Immediately after adding, removing, or reordering buttons, the changes are **not yet saved**. Run Save Project from the File menu to restore the same configuration on next startup.

## 5. Usage Examples

- **Image-editor-style toolbar**: Line up frequently used operations on the global vertical toolbar for constant access
- **Panel-specific mini toolbars**: Place per-panel frequent operations directly under each panel's header so you don't need to look away from the panel
- **Color-coded classification**: Use green for adding, red for deleting, blue for settings — colors make the purpose immediately recognizable

## Related

- [Menu System Guide](04-Menu%20System%20Guide.md)
- [Keyboard User Guide](06-Keyboard%20User%20Guide.md)
- [Save Project](../../File/02-Menu/06-Save%20Project.md)
