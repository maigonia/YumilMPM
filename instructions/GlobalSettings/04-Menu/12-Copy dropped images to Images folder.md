# Copy Dropped Images to Images Folder
**Copy dropped images to Images folder**

## When to Use
- When you want dropped images to be absorbed into the project's Images folder instead of being referenced by absolute paths in external folders
- When you want image links to survive moving the project to another machine
- When you want prompts to keep their images even if the original files are moved or deleted

## What It Does

Toggles the behavior when images are dropped.

- **OFF (default)**: The absolute path of the dropped file is recorded as-is. No file is copied
- **ON**: The dropped image is copied to `Images/{YYYYMMDD_seq}/` under the project folder, and is subsequently referenced as a relative path into that copy

The three drop routes affected by this toggle are:

- Image panel drops (the same panel as [Add Image](../../PromptBrowser/03-Menu/04-ImagePanel/02-Add%20Image.md))
- [Add From WD14](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md) dialog drop zone
- [Add From LM Studio](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md) dialog drop zone

## How to Use

Click GlobalSettings > **Copy dropped images to Images folder** to toggle ON/OFF. A checkmark indicates the toggle is enabled.

## Notes

- Default is OFF (same as the legacy behavior)
- The setting is saved to the project and persists when reopening the project
- [Paste Image From Clipboard](../../PromptBrowser/03-Menu/04-ImagePanel/03-Paste%20Image%20From%20Clipboard.md) always copies to the Images folder and is not affected by this toggle
- Copy destination folders are auto-partitioned as `{projectFolder}/Images/{date_seq}/`

### Copied Filename

The naming rule differs by drop route.

- **Drop onto the image panel (same panel as [Add Image](../../PromptBrowser/03-Menu/04-ImagePanel/02-Add%20Image.md))**: `{CategoryName}_{PromptName}.ext`. This is the same naming convention as [Paste Image From Clipboard](../../PromptBrowser/03-Menu/04-ImagePanel/03-Paste%20Image%20From%20Clipboard.md), so it is clear at a glance in Explorer which prompt each image belongs to. If the category name or prompt name cannot be resolved (e.g. either is empty), the filename falls back to `img_001.ext`, `img_002.ext`, ... numbering
- **Drop onto the [Add From WD14](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md) / [Add From LM Studio](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md) dialog drop zone**: the original image filename (basename without extension) is used as-is. The generated prompt name is also taken from the original filename, so the prompt name and the image filename stay aligned

In every route, when a file with the same name already exists, a suffix `_1`, `_2`, ... is appended.

## Related

- [Add Image](../../PromptBrowser/03-Menu/04-ImagePanel/02-Add%20Image.md)
- [Add From WD14](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md)
- [Add From LM Studio](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md)
- [Paste Image From Clipboard](../../PromptBrowser/03-Menu/04-ImagePanel/03-Paste%20Image%20From%20Clipboard.md)
- [Image](../../PromptBrowser/01-Basics/01-Image.md)
