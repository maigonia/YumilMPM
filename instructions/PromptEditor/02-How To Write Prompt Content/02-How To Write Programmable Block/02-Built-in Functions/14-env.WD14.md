# env.WD14

**Function to extract tags from an image**

## Syntax

```javascript
await env.WD14(imagePath);
await env.WD14(imagePath, presetName);
```

| Argument | Type | Required | Description |
|----------|------|----------|-------------|
| `imagePath` | string | Yes | Absolute path to the image file |
| `presetName` | string | | [Exclude Tags](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md) preset name. No filtering when omitted |

**Return value**: `Promise<string>` - Comma-separated tag string

## Overview

Uses the WD14 tagger to extract Danbooru/anime-style tags from images. Inference is performed locally using Rust ONNX Runtime.

## First-Time Model Download

The WD14 model is automatically downloaded on first use.

- Download may take **several minutes**
- The model is saved in the `{DataFolder}/models/wd14/` folder
- From the second use onward, the downloaded model is used for immediate execution

## Supported Image Formats

- `.jpg` / `.jpeg`
- `.png`
- `.webp`

*Images undergo validation

## Tag Inference Settings

Settings can be changed in [GlobalSettings > WD14 Tagger Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/04-WD14%20Tagger.md).

| Setting | Default | Description |
|---------|---------|-------------|
| generalThreshold | 0.35 | Confidence threshold for general tags |
| characterThreshold | 0.85 | Confidence threshold for character tags |
| maxTags | Unlimited | Maximum number of tags |

## Usage Examples

### Basic Usage

```javascript
@@@_
const imagePath = env.chunk.imagePaths[0];
if (imagePath) {
  const tags = await env.WD14(imagePath);
  env.OUTPUT(tags);
}
_@@@
```

> Output example: `1girl, solo, long hair, blue eyes, school uniform, smile`

### Apply Exclude Tags Preset

```javascript
@@@_
const imagePath = env.chunk.imagePaths[0];
if (imagePath) {
  const tags = await env.WD14(imagePath, "Non-Pose");
  env.OUTPUT(tags);
}
_@@@
```

> The "Non-Pose" preset (Keep Only mode) is applied, returning only pose-related tags.

### Manually Filter Tags

```javascript
@@@_
const imagePath = env.chunk.imagePaths[0];
if (imagePath) {
  const allTags = await env.WD14(imagePath);
  const tagArray = allTags.split(", ");
  const filtered = tagArray.filter(t => !t.includes("background"));
  env.OUTPUT(filtered.join(", "));
}
_@@@
```

### Process Multiple Images

```javascript
@@@_
const results = [];
for (const path of env.chunk.imagePaths) {
  const tags = await env.WD14(path);
  if (tags) results.push(tags);
}
env.OUTPUT(results.join("\n---\n"));
_@@@
```

## Behavior on Error

Returns an empty string `""` in the following cases:

- Model not downloaded
- Image file does not exist
- Unsupported image format
- Image data is corrupted

## Prerequisites

- WD14 model must be downloaded (see above)

## Notes

- **Async function**: `await` is required
- Tags are returned sorted by confidence (highest first)
- Processing time depends on image size and PC specs (several hundred ms to several seconds)
- If a non-existent preset name is specified for `presetName`, filtering is skipped

## Related

- [Programmable Block](../README.md)
- [WD14 Tagger](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/14-WD14%20Tagger.md)
- [WD14 Tagger Settings](../../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/04-WD14%20Tagger.md)
- [Exclude Tags](../../../04-Menu/01-Edit%20SelectedText%20with%20Plugins/17-Exclude%20Tags.md)
- [Exclude Tags Presets](../../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/02-Exclude%20Tags.md)
- [Image](../../../../PromptBrowser/01-Basics/01-Image.md)
- [Tag](../../../../PromptBrowser/01-Basics/04-Tag.md)
- [env.chunk](01-env.chunk.md)
