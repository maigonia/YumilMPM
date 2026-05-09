# env.PLUGINEDIT

**Function that calls an Edit plugin to transform text**

Uses the same syntax as CI's `.Edit(...)`, letting you apply any Edit plugin to an arbitrary string.

## Syntax

```javascript
await env.PLUGINEDIT(text, strategySpec)
```

| Argument | Type | Description |
|----------|------|-------------|
| `text` | string | Text to transform |
| `strategySpec` | string | Plugin name or CI `.Edit(...)`-compatible spec |

**Return value**: `Promise<string>` — Transformed text

## How to Write strategySpec

The spec format is identical to CI's `.Edit(...)`. There is no new syntax to learn.

| Form | Example | Description |
|------|---------|-------------|
| Plugin name | `"TrimWhitespaceEachLine"` | Sync plugin with no args |
| Plugin name | `"NormalizePromptFormat"` | Same |
| `LM=preset, instruction` | `"LM=default, Please summarize"` | Calls LMStudioEdit |
| `GoogleTranslate=lang` | `"GoogleTranslate=en"` | Calls Google Translate |

## Prerequisites

- The plugin must be enabled in the **Programmable Block** tab of [EditPlugin Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- For LMStudioEdit, GoogleTranslate, and other external service plugins, the same prerequisites apply (LM Studio running, API keys configured, etc.)

> **Important**: Not every Edit plugin is callable from `env.PLUGINEDIT`. Only the plugins listed in the **Programmable Block** tab of [EditPlugin Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md) — and enabled there — are eligible.

## Plugins That Cannot Be Called From PB

The following plugins are intentionally excluded from the **Programmable Block** tab and cannot be invoked via `env.PLUGINEDIT`.

| Plugin | Use this instead | Reason |
|---|---|---|
| `LMStudioEdit` | [env.LMEDIT](08-env.LMEDIT.md) | Direct PB-native API exists |
| `WD14 Tagger` | [env.WD14](14-env.WD14.md) | Input is an image path; does not fit the Edit-plugin signature |
| `Programmable Edit` | (just write PB directly) | Nesting PB inside PB would be confusing |

Dialog-driven plugins like `ReplaceText` and `RemoveTagsAtCursor` are also not registered in the PB context.

## Difference From CI Inside PB

When you call `env.CI("Cat.Edit(pluginName)")` from PB, that is still a CI execution, and the **Category Identifier / CT** tab determines which plugins are enabled. The **Programmable Block** tab settings used by `env.PLUGINEDIT` are independent.

| Call site | Tab consulted for enablement |
|---|---|
| `env.PLUGINEDIT(text, spec)` | **Programmable Block** |
| `env.CI("Cat.Edit(spec)")` | **Category Identifier / CT** |

## Usage Examples

### Simple cleanup

```javascript
@@@_
const raw = "  apple ,  banana  ,  cherry  ";
const cleaned = await env.PLUGINEDIT(raw, "TrimWhitespaceEachLine");
env.OUTPUT(cleaned);
_@@@
```

### LMStudio integration

```javascript
@@@_
const story = await env.CI("Story");
const summary = await env.PLUGINEDIT(story, "LM=default, Summarize this in one sentence.");
env.OUTPUT(summary);
_@@@
```

### Translation

```javascript
@@@_
const tags = await env.CI("Tags");
const translated = await env.PLUGINEDIT(tags, "GoogleTranslate=en");
env.OUTPUT(translated);
_@@@
```

### Chaining plugins

```javascript
@@@_
const raw = await env.CI("Source");
let result = await env.PLUGINEDIT(raw, "TrimWhitespaceEachLine");
result = await env.PLUGINEDIT(result, "NormalizePromptFormat");
result = await env.PLUGINEDIT(result, "RemoveDuplicateTags");
env.OUTPUT(result);
_@@@
```

## env.CI vs env.PLUGINEDIT

| Aspect | env.CI | env.PLUGINEDIT |
|--------|--------|----------------|
| Input | Category name (looks up prompt) | Arbitrary text |
| Editing | Possible via `.Edit(...)` | Plugin applied directly |
| Use case | Full prompt-generation pipeline | Programmatic text transformation |

If you only need to edit a category's prompt, `env.CI("Category.Edit(...)")` is sufficient. But if you want to transform an **arbitrary string** — for example the result of `env.LMEDIT` or `env.HISTORY` — `env.PLUGINEDIT` is the cleaner choice.

## env.chunk integration

Chunk-aware plugins (e.g., `UseNameAsContent`) automatically receive `env.chunk`. As long as `env.chunk` is available in the Programmable Block context, you don't need to pass it explicitly.

## Error Behavior

- **Plugin not found**: Logged to `programmable_errors`, returns empty string
- **Plugin disabled**: Errors when the plugin is disabled in the Programmable Block context
- **Plugin runtime error**: Logged, returns empty string

## Notes

- **Async function**: `await` is required
- Argument parsing reuses CI logic, so any spec that works in CI works here too

## Related

- [Programmable Block](../README.md)
- [env.CI](02-env.CI.md)
- [env.LMEDIT](08-env.LMEDIT.md)
- [EditPlugin Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
