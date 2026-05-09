# PromptTree Panel Structure

## Overall Panel Layout

The PromptTree panel consists of the following 4 areas from top to bottom:

```
┌─────────────────────────────────────┐
│  Header (Title + Add Button)        │
├─────────────────────────────────────┤
│                                     │
│       Tree Display Area             │
│     (Hierarchical Prompt Display)   │
│                                     │
├─────────────────────────────────────┤
│  Control Bar (Check/Expand, etc.)   │
├─────────────────────────────────────┤
│  Search Panel (Search Box/Filters)  │
└─────────────────────────────────────┘
```

## Role of Each Area

### 1. Header

- **Panel name**: Displays "PromptTree"
- **Add button**: Blue "+" button. Adds a child prompt to the selected prompt

### 2. Tree Display Area

The main area that displays prompts in a hierarchical structure.

- Perform operations like selection, checking, expand/collapse
- Scroll to view the entire tree
- Displays "No results found" when there are no search results

See "[Tree Area](04-Tree%20Area%20Operations.md)" for details.

### 3. Control Bar

Buttons for check operations and expand/collapse are color-coded.

- **Purple Group**: Overall check operations
- **Blue Group**: Check operations based on selected node
- **Green Group**: Jump to checked nodes
- **Orange Group**: Expand/collapse operations

See "[Control Area](01-Control%20Bar%20Operations.md)" for details.

### 4. Search Panel

Area for searching and filtering prompts.

- Search box
- Search target selection (name/content/tag/path)
- Date filter
- Check operations on filter results

See "[Search Panel](02-Search%20Panel%20Operations.md)" for details.

## Getting Focus

To move keyboard focus to the prompt tree:

- Press the **Alt+2** key
- Select **PromptTree > Get Focus** from the menu

## Related

- [PromptTree](../03-Prompt%20Tree%20Overview.md)
- [Tree Area](04-Tree%20Area%20Operations.md)
- [Control Area](01-Control%20Bar%20Operations.md)
- [Search Panel](02-Search%20Panel%20Operations.md)
