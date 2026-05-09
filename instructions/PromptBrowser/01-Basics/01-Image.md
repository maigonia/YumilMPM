# Image

You can attach and manage reference images for prompts.

## Adding Images

| Method | Operation | Storage |
|--------|-----------|---------|
| File selection | Menu → [Add Image](../03-Menu/04-ImagePanel/02-Add Image.md) | Path reference (no copy) |
| Drag & drop a local image | Drop image files onto the image panel | Path reference (no copy) |
| Clipboard | Ctrl+V (when the image panel has focus) → [Paste Image From Clipboard](../03-Menu/04-ImagePanel/03-Paste Image From Clipboard.md) | Copied into the `Images` folder |
| Drag & drop a browser image | Drop the image onto the [Result Window](../../PromptGeneration/01-Basics/04-Result Window.md) | Copied into the `Images` folder |

Images dragged directly from a web browser cannot be received by this image panel due to a technical constraint. Drop them onto the [Result Window](../../PromptGeneration/01-Basics/04-Result Window.md) instead and they will be forwarded to the prompt currently selected in the main window.

## Basic Operations

| Operation | Method |
|-----------|--------|
| Switch images | ◀ ▶ buttons, or ← → keys |
| Delete | Delete key, or [Remove Image](../03-Menu/04-ImagePanel/04-Remove Image.md) |
| Full screen | Double-click, or Enter key |
| Zoom | Mouse wheel |
| Pan | Middle-click + drag |

## Metadata

Images created by AI image generation tools may have generation parameters embedded in them. You can check them with [Extract MetaData From Image](../03-Menu/04-ImagePanel/09-Extract MetaData From Image.md).

## Related

- [Image](01-Image.md)
- [PromptBrowser](03-Prompt Browser.md)
- [Add Image](../03-Menu/04-ImagePanel/02-Add Image.md)
- [Remove Image](../03-Menu/04-ImagePanel/04-Remove Image.md)
- [Next Image](../03-Menu/04-ImagePanel/05-Next Image.md)
- [Before Image](../03-Menu/04-ImagePanel/06-Before Image.md)
- [Move Up Image](../03-Menu/04-ImagePanel/07-Move Up.md)
- [Move Down Image](../03-Menu/04-ImagePanel/08-Move Down.md)
- [Paste Image From Clipboard](../03-Menu/04-ImagePanel/03-Paste Image From Clipboard.md)
- [Extract MetaData From Image](../03-Menu/04-ImagePanel/09-Extract MetaData From Image.md)
- [Full Screen Image](../03-Menu/04-ImagePanel/01-Full Screen Image.md)
- [WD14 Tagger](../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/14-WD14 Tagger.md)
