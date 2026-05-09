# Programmable Edit

**Programmable Edit**

## When to Use

- When you want to freely process and transform text with JavaScript code
- When you need complex text operations that other Edit plugins can't handle
- When you want to save custom edit logic as presets for reuse

## What It Does

Transforms selected text using [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) code. Use `env.getText()` to get the target text and `env.OUTPUT()` to output the result. All [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) built-in functions (`env.CI()`, `env.LMEDIT()`, `env.WD14()`, etc.) are available.

## How to Use

1. Select the text to edit (if nothing is selected, all text is targeted)
2. Select **Edit SelectedText with Plugins > Programmable Edit** from the menu
3. The dialog opens
4. Write transformation code in the code editor
5. Click **Execute** (or **Ctrl+Enter**)
6. Review the result preview, then click **OK** to apply

## Dialog Usage

### Code Editor

Edit code using Monaco Editor. The same JavaScript syntax as [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) is available.

Basic pattern:

```javascript
const text = env.getText();
// Process the text
const result = text.toUpperCase();
env.OUTPUT(result);
```

### Preset Management

| Action | Description |
|--------|-------------|
| **Preset selection** | Switch presets from the dropdown |
| **Save** | Overwrite save code to the current preset |
| **Save As...** | Save as a new preset with a name |
| **Delete** | Delete the selected preset (default preset cannot be deleted) |

The last used preset is remembered per category.

### Result Preview

After executing, the result text is displayed in the preview area. Review the content before applying with **OK**.

## Using with Category Identifier

The following syntax can be used within [Category Identifier](../../02-How To Write Prompt Content/01-How To Write Category Identifier/README.md):

```
@@@_CategoryName.Edit(ProgrammableEdit)_@@@
@@@_CategoryName.Edit(ProgrammableEdit=MyPreset)_@@@
```

- No argument: Uses the default preset
- `=PresetName`: Uses the specified preset

When used via CI syntax, the dialog is not shown and the preset code is executed automatically.

## Code Examples

### Sort Tags

```javascript
const text = env.getText();
const tags = text.split(",").map(t => t.trim()).sort();
env.OUTPUT(tags.join(", "));
```

### Rewrite with AI

```javascript
const text = env.getText();
const result = await env.LMEDIT("rewrite naturally", text);
env.OUTPUT(result);
```

### Reference Other Categories

```javascript
const text = env.getText();
const style = await env.CI("Style");
env.OUTPUT(text + ", " + style);
```

## Relationship with Programmable Block

Programmable Edit uses the same execution environment (QuickJS sandbox) as [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md). Almost all `env` functions are shared.

The only difference is [env.getText](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/16-env.getText.md). This function is exclusive to Programmable Edit and retrieves the text being edited. It is not available in regular generation pipeline Programmable Blocks.

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Programmable Block](../../02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
- [env.getText](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/16-env.getText.md)
- [env.OUTPUT](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/09-env.OUTPUT.md)
- [env.CI](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/02-env.CI.md)
- [env.LMEDIT](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md)
- [Category Identifier](../../02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
