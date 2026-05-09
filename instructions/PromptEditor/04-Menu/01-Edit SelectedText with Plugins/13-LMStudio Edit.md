# LM Studio Edit

**LM Studio Edit**

## When to Use

- When you want to translate a prompt to another language
- When you want AI to rewrite or improve text
- When you want to freely process selected text with AI instructions

## What It Does

Edits and processes selected text using AI models from LM Studio. Flexible text processing is possible, including translation, summarization, and rewriting.

## How to Use

1. Select the text to edit
2. Select **Edit SelectedText with Plugins > LM Studio Edit** from the menu
3. A dialog appears (see below for details)
4. Click **Execute** (or **Ctrl+Enter**)
5. The selected text is replaced with the AI-generated result

## Dialog Usage

The dialog has 3 tabs: **Execute**, **Templates**, and **Settings**.

### Execute Tab (Main Operation Screen)

| Item | Description |
|------|-------------|
| **Select Template** | Select a saved template. Selecting one auto-loads the Instruction and Preset. Leave as "(none)" if not using a template |
| **Select Preset** | Select the AI settings (preset) to use |
| **Instruction** | Enter instructions for the AI (e.g., "Translate to English", "Rewrite with more detail") |
| **Images (Vision)** | Attach images (only shown for Vision-compatible presets). See below for details |
| **Selected Text** | Shows the text to edit. You can also directly modify the text here |

Click the **Execute** button or press **Ctrl+Enter** when ready.

#### Adding Images (Vision Mode)

When a Vision-capable preset is selected, the **Images (Vision)** section appears. You can add images in either of these ways:

- **Add Image** button: Pick multiple files via the file dialog
- **Drag & Drop**: Drop image files or folders directly onto the dashed drop zone in the dialog. Dropping a folder recursively collects supported images inside.

Supported formats: `.jpg` / `.jpeg` / `.png` / `.webp`

**Note**: The number of images is limited by the preset's Max Images setting. Unlike Add From LM Studio (which processes one image at a time), Edit sends **all attached images simultaneously as reference images to the AI and retrieves a single result**.

#### Output Options (Vision Mode)

When in Vision mode with at least one image attached, the following options are shown:

- **Include file path in output**: When enabled, the image file paths are added to the beginning of the output as a comma-separated line
- **Format for ComfyUI MPM Parser**: When enabled, the output is converted to `###_Path(path1, path2).Text(AI-generated content)_###` format. Multiple image paths are comma-separated inside `Path()`. Enabling this automatically turns on "Include file path in output"

### Templates Tab (Template Management)

Save frequently used instructions as templates for quick access from the Execute tab.

- **Creating a template**: Select "(new template)", enter name, default preset, and Instruction, then click **Save**
- **Deleting a template**: Select the template to delete, then click **Delete**

### Settings Tab (Preset Management)

Create and edit settings (presets) related to AI behavior.

- **Model**: Select the model to use. Model list is automatically fetched from LM Studio when the dialog opens. Select "**Use currently loaded model**" to use the model currently loaded in LM Studio (default). Select "**(manual input...)**" to type a model name directly. Click "**Fetch list**" to manually refresh the model list
- **Temperature**: Generation randomness (0=deterministic, 2=random)
- **Max Tokens**: Maximum length of generated text
- **System Prompt**: Instructions always sent to the AI
- **Timeout**: Timeout duration (milliseconds)
- **Unload model after generation (free VRAM)**: When enabled, the LM Studio model is automatically unloaded from VRAM right after generation completes. Useful when running other GPU workloads such as image generation in parallel. The `vision-unload-after-generation` preset is a variant that has this enabled by default

Advanced settings such as **Top P**, **Top K**, **Repeat Penalty** can also be adjusted.

#### Apply Without Saving (Temporary)

When you change a value in the Settings tab, it is applied to the next execution **even without clicking Save Preset**. While unsaved changes exist, the footer shows "Running with temporary preset settings (changes will be discarded after execution)". Useful for trying out a different temperature or unload setting on the fly. Changes are discarded when the dialog is closed. Click **Save Preset** only when you want to persist them.

## Prerequisites

- LM Studio must be running with the API server enabled
- Presets must be configured in [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)

## Notes

- Generation may take time. Timeout can be adjusted in the Settings tab
- If an error occurs, the error message is displayed within the dialog
- Utilizing templates saves the effort of entering the same instructions each time

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [Create Yumil Parser Block](16-Create Yumil Parser Block.md)
- [env.LMEDIT](../../02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md)
