# EditPlugin Settings

## When to Use

- When you want to disable a specific [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- When you want to choose which plugins to use per context
- When you want to check plugin descriptions and behavior examples

## What It Does

Configures which [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)s are enabled/disabled for text editing, organized by four contexts (usage scenarios).

| Tab                      | Target                                                                                                         |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Prompt Editor            | Plugins applied during text editing in the editor                                                              |
| Category Identifier / CT | Plugins applied during [Category Template](../../../AdvancedPanel/02-Glossary/01-Category Template.md) Edit processing and invoked by `.Edit(...)` in [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) |
| Bulk Edit                | Plugins applied during bulk processing of checked prompts                                                      |
| Programmable Block       | Plugins invoked from [Programmable Block](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md) via `env.PLUGINEDIT(text, spec)`                                   |

## How to Use

1. Select GlobalSettings > **EditPlugin Settings** to open the dialog
2. Switch contexts using the tabs at the top
3. Enable/disable each plugin using its checkbox
4. Click "OK" to save

## Dialog Operations

**Plugin List**:

- Each plugin shows a checkbox, name, ID, and description
- [Custom Plugin](../../03-Tips/02-Custom Plugins.md)s also display author, version, detailed description, and file name
- The Category Identifier / CT tab also shows input/output examples for each plugin

**Bulk Operation Buttons** (apply to the current tab):

- **Select All**: Enable all plugins
- **Select None**: Disable all plugins
- **Reset to Default**: Restore default settings

## Gear Icon (⚙)

A gear icon appears on rows for plugins that support [Rate Limiting](../../02-Glossary/06-Rate Limiting.md). Clicking it expands a [Rate Limiting](../../02-Glossary/06-Rate Limiting.md) settings panel inline.

| Item | Description |
| --- | --- |
| **Request Delay** | Delay between consecutive requests (milliseconds). 0 disables this check |
| **Max Requests / Window** | Maximum requests within the time window (minutes). Max=0 disables this check |
| **Reset** | Restore the plugin's default values |

The gear is shown on these plugins:

- **Google Translate** (default: 3000ms / 20 per 5 minutes)
- **LMStudio Edit** (default: 0/0 = unlimited; configure when used via cloud, etc.)
- [Custom Plugin](../../03-Tips/02-Custom Plugins.md)s with the network permission

Plugin-specific settings (such as default languages) are NOT opened from this gear. Open them from the GlobalSettings menu instead — for example, [Google Translate Settings](03-Google Translate Settings.md), [WD14 Tagger Settings](04-WD14 Tagger.md), [Exclude Tags Presets](02-Exclude Tags.md).

## Custom Plugin Management

When using [Custom Plugin](../../03-Tips/02-Custom Plugins.md)s, the following management buttons appear at the bottom of the dialog.

**Open Plugin Folder**: Opens the `plugins/edit/` directory in the data folder in the file explorer. Place new plugin files (.js) here.

**Reload Plugins**: Re-scans the plugin folder without restarting the app to load new plugins. File additions, changes, and deletions are all reflected. Plugins with changed file contents will have their **permissions automatically reset and the plugin disabled** for security. To re-enable, you must re-grant permissions and check the enable checkbox.

**Error Display**: If plugins failed to load, error information is shown above the plugin list. You can check the file name and error message.

**Permission Settings**: [Custom Plugin](../../03-Tips/02-Custom Plugins.md)s that require network, secret, or file access display permission toggles. Permissions are automatically reset when plugin file contents change. This is detected both at app startup and when reloading plugins.

## Notes

- Enabled plugins are processed in order from top to bottom
- Each tab has independent settings. Changes in one tab do not affect others
- Changes are not saved until you click "OK"
- A plugin whose checkbox is OFF will not run — neither from the UI plugin-picker nor from a `.Edit(...)` expression in [Category Identifier](../../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md). Use the checkbox when you want to fully stop a plugin from executing (the permission toggles only restrict what the plugin can do internally; they do not stop the plugin itself from running)
- The **Programmable Block** tab does not list plugins that have a dedicated `env.*` function in PB. `LMStudioEdit` is exposed as [env.LMEDIT](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md), `WD14 Tagger` as [env.WD14](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/14-env.WD14.md), and `Programmable Edit` is excluded because nesting PB inside PB would be confusing

## Related

- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Rate Limiting](../../02-Glossary/06-Rate Limiting.md)
- [Edit SelectedText with Plugins](../../../PromptEditor/01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [Edit Prompt Content with Plugins](../../../PromptTree/04-Menu/05-Checked/04-Edit Prompt Content with Plugins.md)
- [Category Template](../../../AdvancedPanel/02-Glossary/01-Category Template.md)
- [Google Translate Settings](03-Google Translate Settings.md)
- [WD14 Tagger Settings](04-WD14 Tagger.md)
- [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/17-Exclude Tags.md)
- [Custom Plugin](../../03-Tips/02-Custom Plugins.md)
- [Initial Setup](../../03-Tips/01-Recommended Initial Settings.md)
