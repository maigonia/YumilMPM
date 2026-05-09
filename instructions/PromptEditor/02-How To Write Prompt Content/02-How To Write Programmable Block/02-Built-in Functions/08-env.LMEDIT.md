# env.LMEDIT

**Function to edit text with LM Studio**

## Syntax

```javascript
await env.LMEDIT(templateName, prompt)
await env.LMEDIT(preset, instruction, prompt)
```

### 2-Argument Pattern (Using Template)

| Argument | Type | Description |
|----------|------|-------------|
| `templateName` | string | Template name |
| `prompt` | string | Text to edit |

### 3-Argument Pattern (Direct Specification)

| Argument | Type | Description |
|----------|------|-------------|
| `preset` | string | Preset name |
| `instruction` | string | Editing instruction (acts as system prompt) |
| `prompt` | string | Text to edit |

**Return value**: `Promise<string>` - Generated text

## Prerequisites

- LM Studio must be running (`http://localhost:1234`)
- Presets must be configured in [GlobalSettings > LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
- When using templates, templates must be created in the Templates tab of the same settings

## Templates and Presets

### Templates

A template combines a **name**, **editing instruction**, and **default preset**.

- Storage: `{DataFolder}/settings/instruction_templates.json`
- Creation: [GlobalSettings > LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md) > Templates tab

### Presets

A preset is the parameter settings for LLM calls (model, temperature, max_tokens, etc.).

- Creation: [GlobalSettings > LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md) > Presets tab

## Usage Examples

### Using Templates (Recommended)

```javascript
@@@_
const story = await env.CI("Story");
const summary = await env.LMEDIT("summarize", story);
env.OUTPUT(summary);
_@@@
```

*Assumes the "summarize" template has an instruction "Please summarize" and a default preset configured

### Direct Specification

```javascript
@@@_
const text = await env.CI("Character");
const result = await env.LMEDIT(
  "creative",
  "Please translate the following text to English",
  text
);
env.OUTPUT(result);
_@@@
```

### Dynamic Instruction

```javascript
@@@_
const style = await env.CI("Style");
const content = await env.CI("Content");
const instruction = \`Please rewrite in the style of \${style}\`;
const result = await env.LMEDIT("default", instruction, content);
env.OUTPUT(result);
_@@@
```

## Internal Behavior

### Prompt Construction

instruction and prompt are combined in the following format:

```
{instruction}

{prompt}
```

### Preset Resolution

1. Searches for the specified preset name
2. Falls back to the default preset if not found

## Behavior on Error

On error, returns an error message with the original text in the following format:

```
---------- LMStudio Error ----------
Error: {error details}
Preset: {preset name used}
To adjust timeout, change the timeout value in AI Settings for this preset.
---------- Original Text ----------
{original text}
```

### Error Cases

- Template not found
- Preset not found (even after fallback to default)
- LM Studio not running
- API call timeout
- Network error

## Notes

- **Async function**: `await` is required
- Templates enable reuse of settings
- Timeout is adjustable in preset settings

## Related

- [Programmable Block](../README.md)
- [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM%20Studio.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
- [LM Studio Edit](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/13-LMStudio%20Edit.md)
- [env.EMBED](03-env.EMBED.md)
