# Result Window

A window displayed after prompt generation for checking and copying generated prompts, and browsing past generation history.

## Screen Layout

The result window consists of three main areas.

### Category List (Left Side)

Displays a list of categories used in generation.

- **✓** (green): Generation succeeded
- **✗** (red): Generation error

Click a category name to display its generation result in the content area on the right. You can also switch categories with the up/down arrow keys.

### Content Area (Right Side)

Displays the generation result for the selected category. There are two tabs at the top.

**Result Tab**

Shows the generated prompt text. If generation failed, an error message is shown in red.

**Trace Tab**

Allows you to check the generation process. You can trace details such as which prompt was selected from which category. Not normally needed, but useful for debugging when results differ from expectations.

### Toolbar

Operation buttons are at the top of the content area.

| Button | Function |
|--------|----------|
| **Copy** | Copy the displayed prompt to the clipboard |
| **All** | Copy prompts from all successfully generated categories together |

"Copied!" is displayed on successful copy. The character count of the prompt is shown at the bottom right.

## History Feature

A "History" section is located below the category list. You can look back at past generation results.

1. Click the **History** dropdown
2. Select the history you want to view from the list showing date/time and category count
3. The history's category list is displayed, click a category to view

While viewing history, the background color changes to yellow to visually distinguish it from current results. Click a category in the upper category list to return to current results.

## Display Settings

Settings related to the result window display can be changed from the **PromptGeneration** menu.

| Setting | Effect | Default |
|---------|--------|---------|
| Show ResultWindow After Generation | Automatically show the window after generation | On |
| Activate ResultWindow After Generation | Bring the window to the front when auto-shown | On |

Closing the window does not destroy it. It will be shown again on the next generation, or you can manually open it with **PromptGeneration > Show Result Window**.

## Browser Image Drop Target

In addition to displaying generation results, the Result Window also serves as a **drop target for images dragged from a web browser**. Drop a browser image here and it will be copied into the project's `Images` folder and automatically added to the prompt currently selected in the main window.

### Why a Separate Window?

Due to a technical constraint, the main window's [Image](../../PromptBrowser/01-Basics/01-Image.md) panel cannot receive images dragged directly from a web browser. Browser-dragged images must be dropped onto the Result Window, which then forwards them to the prompt selected in the main window.

### How to Use

1. Select the target prompt in the main window first
2. Drag an image from your web browser onto the Result Window
3. The image is automatically downloaded and added to the selected prompt's image list

Clicking the "Drop Image Here" button in the toolbar opens a dialog explaining this feature.

### Notes

- Drops onto the Result Window are **always copied into the `Images` folder**. Dropping a local file here creates a duplicate.
- Copied filenames are prefixed with the category and prompt name (e.g. `MyCategory_MyPrompt.jpg`). On name collisions, `_1`, `_2`, ... are appended.
- To reference an existing local file by path without copying, drop it onto the [Image](../../PromptBrowser/01-Basics/01-Image.md) panel in the main window instead.
- If no prompt is selected in the main window, an error notification is shown when you drop.

## Notes

- Window position and size are automatically remembered
- "No results yet" is displayed if no generation has been performed
- Generation results from multiple categories can be checked individually

## Related

- [Generation](03-About Prompt Generation.md)
- [Once Generation](../04-Menu/01-Once Generation.md)
- [Show Result Window](../04-Menu/18-Show Result Window.md)
- [Show ResultWindow After Generation](../04-Menu/07-Show ResultWindow After Generation.md)
- [Activate ResultWindow After Generation](../04-Menu/08-Activate ResultWindow After Generation.md)
- [Auto-Send Result to Clipboard](../04-Menu/11-Auto-Send Result to Clipboard.md)
- [Auto-save prompts to text files](../04-Menu/10-Auto-save prompts to text files.md)
