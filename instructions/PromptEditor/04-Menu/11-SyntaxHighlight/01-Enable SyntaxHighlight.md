# Enable SyntaxHighlight

**SyntaxHighlight > Enable**

## What It Does

Toggles the syntax highlighting feature on/off in the prompt editor. When enabled, text matching user-defined rules is displayed with colors.

## How to Use

### Enable/Disable Steps

1. Select **PromptEditor > SyntaxHighlight > Enable** from the menu
2. Checked state → Highlighting is enabled
3. Unchecked state → Highlighting is disabled

### Toggling from the Menu

- **Enable**: Click **Enable** in the menu to check it
- **Disable**: Click **Enable** again to uncheck it

## Basic Flow

1. **Create rules**: First create highlighting rules in [SyntaxHighlight Setting](02-SyntaxHighlight%20Setting.md)
2. **Enable**: Check the Enable menu
3. **Verify**: Check the coloring in the editor
4. **Adjust**: Change settings or temporarily turn off as needed

## Notes

### Setting Persistence

- The enabled/disabled state is saved when **Save Project** is executed
- After saving, settings are maintained after app restart

### Highlighting Scope

- Highlighting is visual only and does not affect prompt content
- Generated text and copy content are not changed

### Relationship with Rule Settings

- Highlighting rules can be created/edited in [SyntaxHighlight Setting](02-SyntaxHighlight%20Setting.md)
- Enable only toggles on/off; rules themselves are not deleted
- Rules are preserved even when temporarily turned off

## Tips

### Efficient Usage

- **While editing**: Usually keep it on with rules configured
- **When checking**: Temporarily turn off to see plain text
- **Performance**: If it feels slow, try temporarily turning it off

### Testing Rules

1. First create a simple rule in [SyntaxHighlight Setting](02-SyntaxHighlight%20Setting.md)
2. Turn on with Enable to check the effect
3. Add more rules as you like

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [SyntaxHighlight](../../01-Basics/01-Features/07-SyntaxHighlight.md)
- [SyntaxHighlight Setting](02-SyntaxHighlight%20Setting.md)
