# WD14 Tagger

**WD14 Tagger**

## What It Does

Extracts tags from an image using the WD14 Tagger and inserts them into the editor. Useful when you want to automatically generate tags from image content.

## How to Use

1. Place the cursor where you want to insert tags (or select existing text)
2. Select **Edit SelectedText with Plugins > WD14 Tagger** from the menu
3. A dialog appears (see below for details)
4. Select an image and click **Execute WD14**
5. Tags appear in the Result field
6. Click **OK** to insert the tags into the editor

## Dialog Usage

### WD14 Tagger Settings

| Item | Description |
|------|-------------|
| **General Threshold** | Detection threshold for general tags. Adjust with the slider. Lower values detect more tags; higher values keep only high-confidence tags |
| **Character Threshold** | Detection threshold for character tags. Adjusts character recognition accuracy |
| **Max Tags** | Maximum number of tags to extract. Leave as "No limit" for unlimited extraction |
| **Exclude Tags Preset** | Select an [Exclude Tags](17-Exclude%20Tags.md) preset to apply filtering to extracted tags. "None" returns all tags without filtering. The gear icon (⚙) next to the label opens preset management for adding/editing presets |
| **Reset** | The Reset button at the top right resets all settings to default values |

### Image (Image Selection)

Two ways to select an image:

- **Drag & Drop**: Drag and drop an image file onto the dashed area
- **Select Image button**: Click the button to open a file selection dialog

### Include file path in output

When checked, the file path is included in the output result.

### Format for ComfyUI Yumil Parser

When checked, the output is converted to `###_Path(filepath).Text(tags)_###` format. This format is used by ComfyUI's Yumil Prompt Parser node.

Enabling this option automatically turns on "Include file path in output".

### Execute WD14

Click the **Execute WD14** button after selecting an image. Tag extraction runs and results appear in the **Result** field.

### Result

Extracted tags are displayed as comma-separated values. You can review the results here and manually edit them if needed.

Click **OK** to apply the results to the editor.

## Notes

- If text was selected, the selected text is replaced with extracted tags
- If no text was selected, tags are inserted at the cursor position
- WD14 Tagger must be configured
- Lowering Threshold values detects more tags but may include less accurate ones

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [WD14 Tagger Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/04-WD14%20Tagger.md)
- [Exclude Tags](17-Exclude%20Tags.md)
- [Exclude Tags Presets](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/02-Exclude%20Tags.md)
- [Create Yumil Parser Block](16-Create%20Yumil%20Parser%20Block.md)
- [Image](../../../PromptBrowser/01-Basics/01-Image.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
