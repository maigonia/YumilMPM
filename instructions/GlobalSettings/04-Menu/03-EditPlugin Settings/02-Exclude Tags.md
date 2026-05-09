# Exclude Tags
**Exclude Tags Presets**

## When to Use
- When you want to add or edit tag filtering presets
- When you want to manage rules for bulk removal of unwanted tags

## What It Does
Manages presets used by the [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md) plugin. Each preset can be configured with a filtering mode and a list of tags.

## How to Use

1. Open [EditPlugin Settings](01-EditPlugin%20Settings.md)
2. Click the **gear icon (⚙)** on the **Exclude Tags** row
3. The Exclude Tags Presets dialog opens
4. Add, edit, or delete presets
5. Click **OK** to save

## Two Modes

| Mode | Behavior |
|--------|------|
| **Exclude** | Removes tags included in the preset |
| **Keep Only** | Keeps only tags included in the preset, removing all others |

## Preset Structure

| Field | Description |
|------|------|
| **Name** | Preset name (used in CI syntax and [env.WD14](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/14-env.WD14.md) references) |
| **Mode** | Exclude / Keep Only |
| **Tags** | Comma-separated list of tags |

## Built-in Presets

| Name | Mode | Description |
|------|--------|------|
| **Non-Pose** | Keep Only | Keeps only pose-related tags |

Built-in presets cannot be deleted, but their tag contents can be edited.

## Where Presets Are Used

- [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md) plugin (editor and bulk processing)
- [WD14 Tagger](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md) dialog's Exclude Tags Preset selection
- [Add From WD14](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md) dialog's Exclude Tags Preset selection
- [Category Identifier](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) `Edit(ExcludeTags=PresetName)` syntax
- [Programmable Block](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) `env.WD14(imagePath, "PresetName")` function

## Related

- [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md)
- [EditPlugin Settings](01-EditPlugin%20Settings.md)
- [WD14 Tagger](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md)
- [WD14 Tagger Settings](04-WD14%20Tagger.md)
- [Add From WD14](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md)
- [env.WD14](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/14-env.WD14.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
- [Category Identifier](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
