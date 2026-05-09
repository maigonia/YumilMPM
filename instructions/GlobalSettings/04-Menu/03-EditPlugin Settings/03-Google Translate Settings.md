# Google Translate Settings

**Google Translate Settings**

## When to Use

- When the language picker dialog should be skipped on every translation
- When the default target language should be fixed (for example, "always translate to English")
- When the default source language should be changed

## What It Does

Configures the **default source / target languages** for the [Google Translate](../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/15-Google Translate.md) plugin and **whether to skip the language picker dialog**.

When skip is enabled, invoking Google Translate in the [PromptEditor](../../../PromptEditor/01-Basics/03-Prompt Editor.md) no longer shows the language picker — translation runs immediately using the saved defaults.

> [Rate Limiting](../../02-Glossary/06-Rate Limiting.md) is configured separately, from the gear icon (⚙) on the Google Translate row in [EditPlugin Settings](01-EditPlugin Settings.md).

## How to Use

1. Select **Global Settings > Google Translate**
2. Set the default languages and the "skip language dialog" toggle
3. Click **OK** to save

Because this setting is opened from a menu, it is also reachable from the command palette and shortcut keys.

## Settings

| Item | Description | Default |
| --- | --- | --- |
| **Default source language** | Default source language | Auto Detect |
| **Default target language** | Default target language | English |
| **Skip language dialog when both defaults are set** | Skip the language picker and translate immediately when both defaults are set | OFF |

### Skip language dialog behavior

- Checkbox ON **and both Default source / target are set** → no dialog; translates with the defaults
- Checkbox OFF, or either default is unset → falls back to the language picker dialog

## Scope

| Context | Effect of default languages / skip |
| --- | --- |
| [Edit SelectedText with Plugins](../../../PromptEditor/01-Basics/01-Features/06-Edit SelectedText with Plugins.md) ([PromptEditor](../../../PromptEditor/01-Basics/03-Prompt Editor.md)) | Skip ON bypasses the language picker |
| [Edit Prompt Content with Plugins](../../../PromptTree/04-Menu/05-Checked/04-Edit Prompt Content with Plugins.md) | Bulk Edit takes per-invocation languages from its preview dialog; this setting has no effect there |
| [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) Edit syntax | The language is specified inline (such as `Edit(GoogleTranslate=en)`); this setting has no effect |
| [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) `env.PLUGINEDIT` | Same as above — the language is specified inline |

## Notes

- "Reset to Defaults" resets only the language settings ([Rate Limiting](../../02-Glossary/06-Rate Limiting.md) settings are left untouched)
- Settings are saved when the project is saved

## Related

- [Google Translate](../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/15-Google Translate.md)
- [EditPlugin Settings](01-EditPlugin Settings.md)
- [Rate Limiting](../../02-Glossary/06-Rate Limiting.md)
- [Edit SelectedText with Plugins](../../../PromptEditor/01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [Edit Prompt Content with Plugins](../../../PromptTree/04-Menu/05-Checked/04-Edit Prompt Content with Plugins.md)
- [Edit](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/06-Edit.md)
