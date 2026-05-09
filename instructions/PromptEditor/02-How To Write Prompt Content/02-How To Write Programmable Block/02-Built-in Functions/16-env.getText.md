# env.getText

**Function to get the text being edited (Programmable Edit only)**

## Syntax

```javascript
env.getText()
```

**Return value**: `string` - The text being edited

## Behavior

Retrieves the text targeted for editing in the [Programmable Edit](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/18-Programmable%20Edit.md) plugin.

- When text is selected in the editor: Returns the selected text
- When nothing is selected: Returns all text in the editor
- When called via CI syntax `Edit(ProgrammableEdit=preset)`: Returns the Edit target text

## Usage Examples

### Text Transformation

```javascript
@@@_
const text = env.getText();
env.OUTPUT(text.toUpperCase());
_@@@
```

### Remove Duplicate Tags

```javascript
@@@_
const text = env.getText();
const tags = text.split(",").map(t => t.trim());
const unique = [...new Set(tags)];
env.OUTPUT(unique.join(", "));
_@@@
```

### Translate with AI

```javascript
@@@_
const text = env.getText();
const translated = await env.LMEDIT("translate to English", text);
env.OUTPUT(translated);
_@@@
```

## Notes

- Synchronous function (`await` not needed)
- **Programmable Edit only**: Returns `undefined` in regular generation pipeline Programmable Blocks
- The basic pattern is to get text with `env.getText()`, process it, and output with `env.OUTPUT()`

## Related

- [Programmable Edit](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/18-Programmable%20Edit.md)
- [Programmable Block](../README.md)
- [env.OUTPUT](09-env.OUTPUT.md)
- [env.CI](02-env.CI.md)
- [env.LMEDIT](08-env.LMEDIT.md)
