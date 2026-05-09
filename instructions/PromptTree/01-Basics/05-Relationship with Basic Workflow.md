# Relationship with Basic Workflow

## What Is the Basic Workflow

The basic flow for generating prompts in this application:

```
CategoryTree → PromptTree → PromptEditor → Check Operations → Generation → Send to External App
```

1. **CategoryTree**: Select a category
2. **PromptTree**: Manage and check prompt materials ← **Here**
3. **PromptEditor**: Edit content
4. **Check Operations**: Determine generation targets
5. **Generation**: Generate prompts
6. **Send to External App**: Send to image generation AI, etc.

## Position of PromptTree

PromptTree is the central panel for actually operating on materials classified by [Category](../../AdvancedPanel/01-Basics/01-Category Template Tab.md).

### What It Receives from the Previous Step

When you select a category in **CategoryTree**, the prompts belonging to that category are displayed in the PromptTree.

### What Is Done in This Step

- Adding, deleting, and organizing prompt materials
- Selecting generation targets using [Check State](01-Concepts/01-Understanding Check State.md)
- Selecting prompts (displaying in the editor)

### What It Passes to the Next Step

- **PromptEditor**: Displays and edits the selected prompt's content
- **Generation**: Uses checked prompts as generation targets

## Typical Work Flow

### 1. Prepare Materials

1. Select a category in CategoryTree
2. Add prompts from the "Add" button or right-click menu in PromptTree
3. Edit content in PromptEditor

### 2. Select Generation Targets

1. Turn checkboxes on/off in PromptTree
2. Or use batch check operations
3. You can also narrow down with search before checking

**Note**: Not all checked materials are output. By default, one is randomly selected from the checked materials. To output all, change the generation rule. See [Generation Rules](../03-Tips/02-Changing Generation Rules.md) for details.

### 3. Execute Generation

1. Select a generation mode in the Generation panel
2. Execute generation
3. Send results to external app

## Related

- [Prompt](01-Concepts/03-What Is a Prompt.md)
- [Category](../../AdvancedPanel/01-Basics/01-Category Template Tab.md)
- [Check State](01-Concepts/01-Understanding Check State.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [CategoryTree](../../CategoryTree/01-Basics/01-Category Tree Basics.md)
- [PromptEditor](../../PromptEditor/01-Basics/03-Prompt Editor.md)
- [PromptBrowser](../../PromptBrowser/01-Basics/03-Prompt Browser.md)
- [Advanced Panel](../../AdvancedPanel/01-Basics/07-What Is Advanced Panel.md)
- [Prompt Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
