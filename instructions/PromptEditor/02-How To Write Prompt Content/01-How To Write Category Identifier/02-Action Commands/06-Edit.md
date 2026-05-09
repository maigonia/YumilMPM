# Edit

**Action for editing joined text**

## Overview

The Edit action applies an [Edit Plugin](../../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md) to the text joined by [Join](05-Join.md). It enables text formatting, duplicate removal, format conversion, and more.

## Syntax

```
@@@_CategoryName.Edit(PluginName)_@@@
```

## Default Value

When Edit is omitted or the parameter is empty (`.Edit()`), only comment removal is performed.

```
@@@_CategoryName_@@@
↓ No Edit
Only comments (after //) are removed

@@@_CategoryName.Edit()_@@@
↓ Empty parameter
Only comments (after //) are removed
```

## Available Edit Plugins

### TrimWhitespaceEachLine

Removes trailing whitespace (spaces, tabs) from each line.

```
@@@_Category.Edit(TrimWhitespaceEachLine)_@@@
```

> `"text  "` → `"text"`

### RemoveDuplicateTags

Removes duplicate tags from a comma-separated list. Keeps the first occurrence, case insensitive.

```
@@@_Category.Edit(RemoveDuplicateTags)_@@@
```

> `"a, b, a, c"` → `"a, b, c"`

### RemoveDuplicateLines

Removes duplicate lines. Keeps the first occurrence, empty lines are preserved.

```
@@@_Category.Edit(RemoveDuplicateLines)_@@@
```

> `"a\nb\na"` → `"a\nb"`

### SortLinesAlphabetically

Sorts lines alphabetically (A-Z). Case insensitive.

```
@@@_Category.Edit(SortLinesAlphabetically)_@@@
```

> `"c\na\nb"` → `"a\nb\nc"`

### NormalizePromptFormat

Normalizes STD prompt format. Unifies comma spacing, adds trailing commas to each line, fixes LoRA notation, etc.

```
@@@_Category.Edit(NormalizePromptFormat)_@@@
```

> `"tag1\ntag2, tag3"` → `"tag1,\ntag2, tag3,"`

### WrapWeightSyntax

Converts to weight format `(text:1)`.

```
@@@_Category.Edit(WrapWeightSyntax)_@@@
```

> `"cute girl"` → `"(cute girl:1)"`

### CreateDynamicPromptsFromLines

Converts newline-separated text to Dynamic Prompts format `{opt1|opt2|opt3}`.

```
@@@_Category.Edit(CreateDynamicPromptsFromLines)_@@@
```

> `"a\nb\nc"` → `"{a|b|c}"`

### EscapeAsJSString

Escapes special characters (`\\`, `"`, `'`, newlines, tabs) for JavaScript string literals. Useful when using text inside Programmable Blocks.

```
@@@_Category.Edit(EscapeAsJSString)_@@@
```

> `Hello "World"` → `Hello \\"World\\"`

### UseNameAsContent

Outputs the chunk name instead of the chunk content.

```
@@@_Category.Edit(UseNameAsContent)_@@@
```

> Chunk name `"my_prompt"` → `"my_prompt"`

### LMStudioEdit

Performs AI editing using [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM Studio.md)'s local LLM.

**Note**: Presets and templates must be created in advance in [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md).

#### Template Specification (1 argument)

```
@@@_Category.Edit(LM=templateName)_@@@
```

> Edits using the preset and instruction configured in the template

Templates have a preset and instruction (prompt text) pre-configured. It's convenient to create templates for frequently used editing patterns.

#### Preset + Instruction Specification (2 arguments)

```
@@@_Category.Edit(LM=presetName, please summarize this content)_@@@
```

> Edits by directly specifying the preset and additional instruction

### GoogleTranslate

Translates text using Google Translate. Source language is auto-detected.

```
@@@_Category.Edit(GoogleTranslate=en)_@@@
```

> Translates to the target language (English)

Specify the language code after `=` (en, ja, fr, de, es, ko, zh-CN, etc.).

#### Examples

```
@@@_Category.Edit(GoogleTranslate=ja)_@@@
```

> Translates to Japanese

```
@@@_Background.Pick(first=-1).Edit(GoogleTranslate=en)_@@@
```

> Translates joined text to English

#### Rate Limiting

Using GoogleTranslate across multiple categories causes consecutive requests. When [Rate Limiting](../../../../GlobalSettings/02-Glossary/06-Rate Limiting.md) is exceeded, the request is rejected immediately and a marker `[Plugin rate limited — retry in Ns]` is embedded in the output text (default: 3000ms delay, 20 requests/5 minutes). Settings can be changed from the gear icon in **Global Settings > EditPlugin Settings**.

## Multiple Plugins

To apply multiple Edit plugins, stack Edit commands. Like [Filter](02-Filter.md), they are applied from left to right.

```
@@@_Category.Edit(TrimWhitespaceEachLine).Edit(RemoveDuplicateTags)_@@@
```

> 1. Apply TrimWhitespaceEachLine
> 2. Apply RemoveDuplicateTags

## Usage Examples

### Remove Duplicate Tags and Format

```
@@@_Character.Pick(first=-1).Edit(RemoveDuplicateTags).Edit(TrimWhitespaceEachLine)_@@@
```

### Convert to Dynamic Prompts Format

```
@@@_Options.Pick(first=-1).Join(\n).Edit(CreateDynamicPromptsFromLines)_@@@
```

### Summarize with AI

```
@@@_Background.Pick(first=-1).Edit(LM=default, please summarize this content in 3 lines)_@@@
```

## Notes

- Applied to the joined text (after Join)
- **Comment removal**: Comments after `//` are automatically removed
- **Case insensitive**: Plugin names are case insensitive (`trimwhitespace` = `TrimWhitespaceEachLine`)
- **Invalid plugin names**: Unrecognized names output a warning and are skipped
- **Plugin enablement required**: `.Edit(pluginName)` can only invoke plugins enabled in the **Category Identifier / CT** tab of [EditPlugin Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md). This applies even when CI is called from inside [Programmable Block](../../02-How To Write Programmable Block/README.md) via `env.CI("Cat.Edit(...)")` — CI always consults the CT tab, never the PB tab
- **Direct call from Programmable Block**: The same spec string can be passed to [env.PLUGINEDIT](../../02-How To Write Programmable Block/02-Built-in Functions/17-env.PLUGINEDIT.md) (example: `env.PLUGINEDIT(text, "LM=default, please summarize")`). However, `env.PLUGINEDIT` consults the **Programmable Block** tab — independent from the CT tab

## Related

- [Category Identifier](../README.md)
- [Category Template](../../../../AdvancedPanel/02-Glossary/01-Category Template.md)
- [Target](01-Target.md)
- [Filter](02-Filter.md)
- [Pick](03-Pick.md)
- [Sort](04-Sort.md)
- [Join](05-Join.md)
- [Plugin](../../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [Rate Limiting](../../../../GlobalSettings/02-Glossary/06-Rate Limiting.md)
- [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [env.PLUGINEDIT](../../02-How To Write Programmable Block/02-Built-in Functions/17-env.PLUGINEDIT.md)
