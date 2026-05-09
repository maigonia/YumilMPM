# Cannot Drop Browser Images Directly

## Symptom

You cannot drag and drop images from a browser directly onto the image panel in the main window.

## Current Behavior

| Action | Behavior |
|---|---|
| **Add Image** button | Opens file dialog, references path (no copy) |
| **Local file D&D** | With [Copy Dropped Images](../../GlobalSettings/04-Menu/12-Copy dropped images to Images folder.md) OFF, references the path (no copy); with ON, copies to the Images folder |
| **Browser image D&D** | Drop onto Result Window → transferred to main window |
| **Paste** (Ctrl+V) | Copies to Images folder |

Browser images must first be dropped onto the Result Window.

## Cause

Due to a technical limitation in Tauri v2's drag and drop handling, it is not possible to simultaneously support local file path retrieval and browser image URL retrieval. The current behavior is a workaround for this limitation.
