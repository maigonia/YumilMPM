# Preset Management

**Add from File System - Saving and Reusing Settings**

## Overview

Settings can be saved as presets for reuse. Additionally, the last setting is automatically saved per category.

## Preset Panel

There is a preset management panel at the top of the dialog.

### Dropdown

A list of saved presets is displayed. Select one and click the Load button to load it.

### Buttons

- **Load**: Load the settings of the selected preset
- **Save**: Save current settings as a new preset (name input required)
- **Delete**: Delete the selected preset

## Saving a Preset

1. Configure settings
2. Click the **Save** button
3. Enter a preset name
4. Save complete

If a preset with the same name exists, it is overwritten.

## Auto-Save (Per Category)

When an import is executed, the settings are automatically saved per category.

**Preset name format:** `Last Setting (AutoSaved) - {category name}`

The next time you use **Add from File System (Quick)** in the same category, these settings are used.

## Default Presets

The following presets are automatically created on first launch.

### LoRA Files (For Civitai SameNameFileSet)

For model files downloaded from Civitai.

- **FileSet Type**: SameNameFileSet
- **Target Extensions**: .safetensors
- **Memo Extensions**: .txt, .info, .json, .md, .yaml, .yml, .toml
- **Image Extensions**: .png, .jpg, .jpeg, .gif, .webp
- **Content Source**: Base File (.info)
- **Content Operation**: JSON Key Extraction
- **Operation Parameter**: modelId, images[0].meta.Model, trainedWords[0]
- **Format**: `// https://civitai.com/models/{json0}` `// (model:{json1})` `<lora:{basefile}:1>,` `{json2}`
- **Skip Options**: Content: ON, Memo: ON, Image: ON

### LoRA Files (For Civitai SameNameFileSet) Update Only Images

Same settings as above, but with **Image skip set to OFF**. Used when you want to add only new images to existing prompts.

### LoRA Files (For Civitai FolderDirectFileSet)

For managing models per folder. FileSet Type is set to **FolderDirectFileSet**.

### Video Collection (FolderDirectFileSet)

For video collections.

- **FileSet Type**: FolderDirectFileSet
- **Target Extensions**: .mp4, .mkv, .avi, .mov, .webm, .wmv, .m4v, .flv
- **Memo Extensions**: (none)
- **Image Extensions**: .png, .jpg, .jpeg, .gif, .webp
- **Content Source**: Base File Name
- **Content Operation**: Use As Is
- **Skip Options**: Content: ON, Memo: ON, Image: OFF

### Prompt and Reference Images

For importing text files as prompts with images in the same folder as reference images.

- **FileSet Type**: FolderDirectFileSet
- **Target Extensions**: .txt, .md, .text, .markdown
- **Memo Extensions**: (none)
- **Image Extensions**: .png, .jpg, .jpeg, .gif, .webp, .bmp, .tiff, .avif
- **Content Source**: Base File (Custom) (Extension: `.txt`)
- **Content Operation**: Use As Is
- **Skip Options**: Content: ON, Memo: ON, Image: ON

## Preset Storage Location

Presets are saved at the following path:

```
{data folder}/settings/plugin_data/add/AddFromFileSystem.json
```

## Cautions

- The **source folder** is also saved in the preset
- The source folder is empty in default presets
- Auto-saved presets (Last Setting) appear in the list as regular presets
- Deleting a preset does not recreate the default preset

## Back

← [addFromFileSystem](13-Add from File System.md)

## Related

- [Add From File System](13-Add from File System.md)
- [Add from File System - Content Extraction](15-Add from File System - Content Extraction.md)
- [Add from File System - FileSet Type](14-Add from File System - FileSet Type.md)
- [Add from File System - Processing Options](16-Add from File System - Processing Options.md)
