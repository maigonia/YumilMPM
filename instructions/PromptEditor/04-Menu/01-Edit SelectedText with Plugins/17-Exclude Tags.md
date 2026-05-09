# Exclude Tags

**Exclude Tags**

## What It Does

Filters tags in prompts based on saved presets. Can be used for bulk removal of unwanted tags or extraction of specific tags only.

## Two Modes

| Mode | Behavior |
|------|----------|
| **Exclude** | Removes tags included in the preset |
| **Keep Only** | Keeps only tags included in the preset and removes all others |

## How to Use (Editor)

1. Select the text you want to filter (if nothing is selected, all text is targeted)
2. Select **Edit SelectedText with Plugins > Exclude Tags** from the menu
3. Choose a preset and mode in the dialog
4. Click **OK** to replace the text with the filtered result

## Preset Management

Presets can be managed in the **Exclude Tags Presets** dialog.

- Open from the gear icon in [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- Can also be opened from the gear icon next to Exclude Tags Preset in [WD14 Tagger Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/04-WD14%20Tagger.md)

### Preset Structure

| Item | Description |
|------|-------------|
| **Name** | Preset name (used for CI syntax and env.WD14 specification) |
| **Mode** | Exclude / Keep Only (keep only specified tags) |
| **Tags** | Comma-separated list of tags |

### Built-in Presets

| Name | Mode | Description |
|------|------|-------------|
| **Non-Pose** | Keep Only | Keeps only pose-related tags |

Built-in presets cannot be deleted, but their tag content can be edited.

## Usage in CI Syntax

The following syntax can be used within [Category Identifier](../../02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md):

```
@@@_CategoryName.Edit(ExcludeTags)_@@@
@@@_CategoryName.Edit(ExcludeTags=Non-Pose)_@@@
```

- No argument: Uses the first preset
- `=presetName`: Uses the specified preset

## Usage in Programmable Block

By passing a preset name as the second argument of [env.WD14](../../02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/14-env.WD14.md), automatic filtering can be applied during tag extraction:

```javascript
@@@_
const tags = await env.WD14(imagePath, "Non-Pose");
env.OUTPUT(tags);
_@@@
```

## Related

- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [WD14 Tagger](14-WD14%20Tagger.md)
- [WD14 Tagger Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/04-WD14%20Tagger.md)
- [env.WD14](../../02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/14-env.WD14.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
- [Category Identifier](../../02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
