# Selection vs Check State

Items in the Prompt Tree have two states: Selection and Check.

## Selected

Only one item can be selected at a time.

## Checked

Multiple items can be checked simultaneously.

### Efficient Check Operations

- **Ctrl+click**: Exclusive check. Unchecks every other item in the category and checks only the clicked item
- **Shift+click**: Range check. Checks everything between the previously clicked item and the currently clicked item
- **Icon bar at the top of the search panel**: A row of icons for efficient check operations (check all, uncheck all, invert, etc.)
- **Check tab in the AdvancedPanel**: Turn the AdvancedPanel on to see and operate on the list of currently checked items

## Important

For batch operations on multiple items, use Check state. The "Checked" submenu in the right-click menu allows operations on all checked items.
