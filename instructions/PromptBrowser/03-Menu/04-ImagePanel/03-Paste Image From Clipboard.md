# Paste Image From Clipboard
**Paste Image From Clipboard**

## When to Use
- When you want to paste a screenshot directly
- When you want to quickly add a copied image

## What It Does
Adds an image from the clipboard to the prompt.

## How to Use
1. Copy an image to the clipboard (PrintScreen, Ctrl+C, etc.)
2. Select "Paste Image From Clipboard" from the menu

## Shortcuts
- **Ctrl+V**: Paste (when the image panel has focus)

## Notes
- A warning about lost metadata is displayed on first use
- Clipboard images do not contain EXIF or other metadata, so the metadata extraction feature cannot be used
- Pasted images are copied into the project's `Images` folder (saved in `YYYYMMDD_NNNN` format subfolders, auto-numbered as `img_001`, `img_002`, ...)
- Unlike [Add Image](02-Add%20Image.md), pasting always copies the image — it never stores a path reference

## Related

- [Image](../../01-Basics/01-Image.md)
- [PromptBrowser](../../01-Basics/03-Prompt%20Browser.md)
- [Add Image](02-Add%20Image.md)
