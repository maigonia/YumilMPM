# WD14 Tagger
**WD14 Tagger Settings**

## When to Use
- When you want to adjust the threshold for tags automatically extracted from images
- When you want to limit the number of extracted tags
- When you want to adjust character recognition sensitivity

## What It Does
Adjusts the threshold settings for [WD14 Tagger](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md) (AI that automatically extracts tags from images).

## Settings

| Setting | Range | Default | Description |
|---------|-------|---------|-------------|
| General Threshold | 0.00-1.00 | 0.35 | Extraction threshold for general tags |
| Character Threshold | 0.00-1.00 | 0.85 | Extraction threshold for character tags |
| Max Tags | Any integer | Unlimited | Maximum number of tags to extract |
| Exclude Tags Preset | Preset selection | None | Filter tags with an [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md) preset |

**About thresholds**: Lower values extract more tags, while higher values extract only tags with high confidence.

## How to Use
1. Open [EditPlugin Settings](01-EditPlugin%20Settings.md) and click the **gear icon (⚙)** on the **WD14 Tagger** row
2. Adjust each threshold using sliders or numeric input
3. Set **Max Tags** if needed (leave empty for unlimited)
4. Optionally select an **Exclude Tags Preset** for tag filtering (gear icon opens preset management)
5. Click "OK" to save

## Notes
- Settings apply to all WD14 Tagger operations
- "Reset to Defaults" restores default values
- Changes are not saved until you click "OK"

## Related

- [WD14 Tagger](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md)
- [Add From WD14](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md)
- [WD14 Tagger Plugin](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md)
- [env.WD14](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/02-Built-in%20Functions/14-env.WD14.md)
- [Exclude Tags](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md)
- [Exclude Tags Presets](02-Exclude%20Tags.md)
- [EditPlugin Settings](01-EditPlugin%20Settings.md)
- [Extract MetaData From Image](../../../PromptBrowser/03-Menu/04-ImagePanel/09-Extract%20MetaData%20From%20Image.md)
- [Initial Setup](../../03-Tips/01-Recommended%20Initial%20Settings.md)
