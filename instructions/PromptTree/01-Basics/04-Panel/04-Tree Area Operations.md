# Tree Area Operations

## Node Display Structure

Each prompt is displayed with the following elements:

```
[Checkbox] [Expand/Collapse ▶/▼] [Icon] [Output Dest ↓] [Name]
```

- **Checkbox**: Whether to include in generation processing
- **Expand/Collapse**: Only shown when there are children (▶ collapsed, ▼ expanded)
- **Icon**: Indicates the prompt type (see [Prompt](../01-Concepts/03-What%20Is%20a%20Prompt.md) for details)
- **Output destination mark**: Green ↓ icon (when set as output destination with [Add From Generated Output](../../04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md))
- **Name**: The prompt's identifying name

## Mouse Operations

### Click

- **Left click**: Select the prompt (blue highlight)
- **Shift+Click**: Range check (batch toggle from last checked position to current)
- **Ctrl+Click**: Exclusive check (uncheck all others in the category, check only the clicked prompt)
- **Expand button (▶/▼) click**: Toggle expand/collapse
- **Checkbox click**: Toggle check state
- **Right-click**: Display context menu (automatically selected)

### Drag & Drop

Drag a prompt to move it under a different parent.

**Note**: Reordering between siblings (changing order within the same parent) has limitations with drag & drop. Use **Move Up / Move Down** menu for reordering.

During dragging, the item is displayed with a semi-transparent yellow background.

## Keyboard Operations

Available when the tree has focus.

### Navigation

- **↑ (Up arrow)**: Move to previous prompt
- **↓ (Down arrow)**: Move to next prompt
- **← (Left arrow)**: Collapse
- **→ (Right arrow)**: Expand

### Check Operations

- **Space**: Toggle check state

### Edit Operations

- **F2**: Rename
- **Delete**: Delete selected prompt
- **Ctrl+C**: Copy
- **Ctrl+X**: Cut
- **Ctrl+V**: Paste

## Visual States

### Selection State

The selected prompt has:
- Blue background
- Blue border on the left side

### Output Destination Node

Nodes set as output destinations with [Add From Generated Output](../../04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md) have:
- Light green background
- Green border on the left side
- Green ↓ icon displayed

### Search Match

Nodes matching the search have:
- Name displayed in green

### During Drag

The node being dragged has:
- 50% opacity
- Yellow background

## Context Menu

The menu displayed by right-clicking includes the following operations:

- **Selected operations**: Rename, delete, copy, cut, paste, move
- **Check operations**: Toggle check for children/siblings/descendants/leaves
- **Add operations**: Various add methods
- **Info copy**: Copy name/content/path to clipboard
- **Checked operations**: Create favorites, bulk edit, AI operations
- **Overall operations**: Check/uncheck all, expand/collapse

## Related

- [Prompt](../01-Concepts/03-What%20Is%20a%20Prompt.md)
- [Check State](../01-Concepts/01-Understanding%20Check%20State.md)
- [Hierarchy](../01-Concepts/02-Understanding%20Hierarchy.md)
- [PromptTree](../03-Prompt%20Tree%20Overview.md)
- [PromptEditor](../../../PromptEditor/01-Basics/03-Prompt%20Editor.md)
- [PromptBrowser](../../../PromptBrowser/01-Basics/03-Prompt%20Browser.md)
