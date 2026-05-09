# Add from LM Studio

**Generate prompts with LM Studio**

## When to Use

- When you want AI to come up with prompt ideas
- When you want AI to analyze image features and generate prompts

## What It Does

Uses [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM Studio.md)'s AI model to automatically generate prompts.

## How to Use

1. Select the parent prompt
2. Select **PromptTree > Selected: Add > Add from LM Studio** from the menu
3. A dialog appears:
   - **Template**: Optionally select an existing instruction template
   - **Preset**: Choose an AI preset
   - **Instruction**: Enter the generation instructions
   - **Requests**: Number of times to call the AI (see below)
   - **Images (Vision)**: Shown only when a Vision-capable preset is selected. Lets you attach images.
4. Click **Generate**
5. AI generates the prompts and the dialog switches to the preview screen
6. Review each generated prompt in the preview, check the ones you want to add, then click **Add**

## Requests

Requests specifies **how many times the AI is called = how many prompts are created**. Its meaning depends on the mode.

- **Text mode** (no images, or non-Vision preset): The user sets a value from 1 to 20. For example, setting it to 5 calls the AI five times with the same instruction and produces five variation prompts.
- **Vision mode** (Vision preset + images attached): Automatically fixed to the number of images. **One prompt is created per image** — the AI is given each image individually and generates a separate prompt for each.

## Adding Images (Vision Mode)

When a Vision-capable preset is selected, the **Images (Vision)** section appears. You can add images in either of these ways:

- **Add Image** button: Pick multiple files via the file dialog
- **Drag & Drop**: Drop image files or folders directly onto the dashed drop zone in the dialog. Dropping a folder recursively collects supported images inside.

Supported formats: `.jpg` / `.jpeg` / `.png` / `.webp`

## Preview Screen

After generation, the dialog switches to a preview.

- The left pane lists the generated prompts
- Each row has two checkboxes: **add checkbox** (violet) and **retry checkbox** (amber)
- The right pane shows the content
- For unsatisfactory results, check the retry box and click **Retry** to regenerate
- **Best of N**: When retrying, generate N candidates and adopt the longest
- Click **Add** to add only the prompts whose add checkbox is checked into the prompt tree

## Output Options (Vision Mode)

When in Vision mode with at least one image attached, the following options are shown.

### Include file path in output

When enabled, the image file path is added to the beginning of each generated prompt.

### Format for ComfyUI MPM Parser

When enabled, the output is converted to `###_Path(filepath).Text(AI-generated content)_###` format. This is the same format used by [Create Yumil Parser Block](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/16-Create Yumil Parser Block.md), compatible with ComfyUI's Yumil Prompt Parser node. Enabling this automatically turns on "Include file path in output".

## Created Prompt Content

- **Name**: In text mode, the first line of the AI output. In Vision mode, the image's filename (without extension).
- **Content**: The AI-generated prompt text (with output option formatting applied if enabled)
- **Image**: In Vision mode, a path reference to the source image

## Prerequisites

- LM Studio must be running and the API server must be enabled

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
- [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [Plugin](README.md)
- [Copy Dropped Images](../../../../GlobalSettings/04-Menu/12-Copy dropped images to Images folder.md)
- [Create Yumil Parser Block](../../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/16-Create Yumil Parser Block.md)
