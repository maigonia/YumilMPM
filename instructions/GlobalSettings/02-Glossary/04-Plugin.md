# Plugin

## What Is It

Plugins are small programs that perform prompt addition and text processing.

## Two Types of Plugins

| Type                              | Purpose                      | Configuration Location                          |
| --------------------------------- | ---------------------------- | ----------------------------------------------- |
| Edit Plugins (EditPlugin)         | Text editing/transformation  | GlobalSettings > EditPlugin Settings            |
| Add Prompt Plugins (AddPromptPlugin) | Processing when adding prompts | PromptTree right-click > AddPromptPlugin Settings |

## Edit Plugin Contexts

Edit plugins can be used in three scenarios:

- **PromptEditor** — Applied when editing text in the editor
- **CategoryTemplate** — Applied during [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md) processing
- **Bulk Edit** — Applied during bulk processing of checked prompts

You can individually configure which plugins are enabled for each context.

## Custom Plugins

User-created JavaScript plugins. Place `.js` files in `plugins/edit/` in the data folder to use them. Supports external API integration and schema-based settings dialogs.

See [Custom Plugin](../03-Tips/02-Custom%20Plugins.md) for details.

## Key Points

- Plugins are processed in order from top to bottom as enabled
- Disabling unnecessary plugins can reduce processing overhead
- Each plugin shows a description of its processing, so you can understand its purpose
- Plugins using external services (like Google Translate) can have [Rate Limiting](06-Rate%20Limiting.md) configured

## Related

- [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [Rate Limiting](06-Rate%20Limiting.md)
- [Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md)
- [AddPromptPlugin Settings](../../PromptTree/04-Menu/03-Selected%20Add/03-Add%20Prompt%20Plugin%20Settings.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [LM Studio](01-LM%20Studio.md)
- [WD14 Tagger](../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md)
