# Add from WD14

**Create prompts by extracting tags from images with WD14 Tagger**

## When to Use

- When you want AI to automatically extract tags from images to create prompts
- When you want to batch tag a large number of images into prompts
- When you want to verbalize character and composition features

## What It Does

Analyzes images with AI (WD14 Tagger) and automatically fills prompt content with extracted tags. One prompt is created per image.

## What Is WD14 Tagger

WD14 Tagger is an AI model that automatically extracts anime/illustration-oriented tags from images.

- **Model**: WD EVA02 Large Tagger v3 (provided by HuggingFace)
- **Model size**: Approximately 890MB
- **Automatically downloaded on first use**

Extracted tag categories:
- **General**: `1girl`, `blonde hair`, `blue eyes`, `standing`, etc.
- **Character**: Known character names
- **Rating**: `general`, `sensitive`, etc.

## How to Use

1. Select the parent prompt
2. Select **PromptTree > Selected: Add > Add from WD14** from the menu
3. A dialog appears
4. Select images (one of the following):
   - **Select Files**: Select multiple image files
   - **Select Folder**: Select a folder (recursively scans images inside)
   - **Drag & Drop**: Drop files or folders (the original file path is used as-is. When "Include file path in output" is enabled, the original path is also included in the output)
5. Adjust settings as needed
6. Click **Execute**
7. A prompt is created for each image

## Supported Image Formats

- `.jpg` / `.jpeg`
- `.png`
- `.webp`

* Images are content-validated (magic byte check), so files with forged extensions are rejected.

## Settings

### General Threshold

- **Default**: 0.35
- **Range**: 0.0 - 1.0
- **Lowering** the value extracts more tags
- **Raising** the value extracts only high-confidence tags

### Character Threshold

- **Default**: 0.85
- **Range**: 0.0 - 1.0
- Character recognition has many false positives, so it defaults to a high (strict) value

### Max Tags

- **Default**: No limit
- Set if you want to limit the number of tags

### Exclude Tags Preset

- **Default**: None (no filtering)
- Select an [Exclude Tags](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/17-Exclude Tags.md) preset to apply filtering to the extracted tags
- Presets have an Exclude mode and a Keep Only (keep only specified tags) mode
- You can add/edit presets from the gear icon (⚙) next to the label

### Include file path in output

- When ON, the file path is added before the tags

### Format for ComfyUI Yumil Parser

- When ON, the output is converted to `###_Path(filepath).Text(tags)_###` format
- This format is used by ComfyUI's Yumil Prompt Parser node
- Enabling this automatically turns on "Include file path in output"

## Created Prompts

For each image, a prompt is created with the following content:

- **Name**: Image file name (without extension)
- **Content**: Extracted tags (comma-separated)
- **Image**: Reference to the original image file

### Example

Processing image `character_illustration.png`:

- **Name**: `character_illustration`
- **Content**: `1girl, solo, blonde hair, long hair, blue eyes, smile, standing, outdoors`
- **Image**: `C:\\Images\\character_illustration.png`

## Processing Flow

```
Image file
  ↓
Image validation (format/size check)
  ↓
Resize to 448×448 (maintaining aspect ratio with padding)
  ↓
WD14 model inference
  ↓
Extract tags above threshold
  ↓
Sort by confidence
  ↓
Register as prompt
```

## First Use

On first use, the AI model (approximately 890MB) is automatically downloaded.

**Save location**: `{data folder}/Models/wd14/`

Progress is displayed during download. Once downloaded, it is automatically loaded thereafter.

## Limitations

- **Maximum file size**: 100MB/image
- Network connection: Required only for initial model download

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Tag](../../../../PromptBrowser/01-Basics/04-Tag.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
- [WD14 Tagger](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/14-WD14 Tagger.md)
- [WD14 Tagger Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/04-WD14 Tagger.md)
- [Exclude Tags](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/17-Exclude Tags.md)
- [Exclude Tags Presets](../../../../GlobalSettings/04-Menu/03-EditPlugin Settings/02-Exclude Tags.md)
- [Create Yumil Parser Block](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/16-Create Yumil Parser Block.md)
- [Image](../../../../PromptBrowser/01-Basics/01-Image.md)
- [Copy Dropped Images](../../../../GlobalSettings/04-Menu/12-Copy dropped images to Images folder.md)
- [Plugin](README.md)
