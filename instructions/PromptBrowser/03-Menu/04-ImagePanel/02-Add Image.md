# Add Image

**Add Image**

## When to Use

- When you want to attach reference images to a prompt
- When you want to save generated result images
- When you want to reference image path information inside Programmable Blocks

## What It Does

Opens a file selection dialog to choose images and add them to the prompt. Selected images are **referenced by their absolute path; no copy is created in the project**. The prompt simply points at the original file location.

## How to Use

1. Select "Add Image" from the menu
2. Choose images in the file selection dialog (multiple selection is supported)

## Notes

- Supported formats: jpg, jpeg, png, gif, bmp, tiff, tif, webp, ico
- The same image cannot be added twice
- Moving or deleting the original file will break the reference and the image will no longer display

### Drag & Drop vs. Other Methods

| Method | Behavior |
|---|---|
| **Add Image** | Path reference to the original file. No copy is created in the project. |
| **Drag & drop onto the image panel** | When [Copy Dropped Images](../../../GlobalSettings/04-Menu/12-Copy%20dropped%20images%20to%20Images%20folder.md) is OFF, path reference only (same as Add Image); when ON, copied into the `Images` folder. |
| **[Paste Image From Clipboard](03-Paste%20Image%20From%20Clipboard.md)** | Copies the image into the project's `Images` folder. |
| **Drag & drop onto the [Result Window](../../../PromptGeneration/01-Basics/04-Result%20Window.md)** | Copies the image into the project's `Images` folder. |

For cases where the original file does not exist on disk (such as images dragged from a web browser), only the "copy" methods can be used. Copied images are saved under `Images/{YYYYMMDD_NNNN}/` and the file name is prefixed with the category name and prompt name (for example: `MyCategory_MyPrompt.jpg`). On collision, `_1`, `_2`, ... are appended to the file name.

**Note**: Images dragged directly from a web browser cannot be dropped onto this image panel. Due to a technical constraint, browser-dragged images must be dropped onto the [Result Window](../../../PromptGeneration/01-Basics/04-Result%20Window.md) instead. See [Result Window](../../../PromptGeneration/01-Basics/04-Result%20Window.md) for details.

## Related

- [Image](../../01-Basics/01-Image.md)
- [PromptBrowser](../../01-Basics/03-Prompt%20Browser.md)
- [Remove Image](04-Remove%20Image.md)
- [Paste Image From Clipboard](03-Paste%20Image%20From%20Clipboard.md)
- [Copy Dropped Images](../../../GlobalSettings/04-Menu/12-Copy%20dropped%20images%20to%20Images%20folder.md)
- [Extract MetaData From Image](09-Extract%20MetaData%20From%20Image.md)
