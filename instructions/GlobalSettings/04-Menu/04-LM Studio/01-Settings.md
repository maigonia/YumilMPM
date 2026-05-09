# LM Studio Settings
**LM Studio Settings**

## When to Use
- When you want to prepare settings before using [LM Studio](../../02-Glossary/01-LM Studio.md) for AI text processing
- When you want to save frequently used AI instructions as templates
- When you want to adjust AI response parameters (presets)

## What It Does
Manages templates and presets used for integration with [LM Studio](../../02-Glossary/01-LM Studio.md). When opened from GlobalSettings, two tabs are displayed: **Templates** and **Settings**.

## Templates Tab

Manages instruction templates. A template is a feature that **saves a preset (model parameter settings) and an instruction together as a set**. Since model settings and instructions are integrated, selecting a template automatically applies both the appropriate settings and instructions at once.

### Creating a Template
1. Select "(new template)" from the template dropdown or click the **New** button
2. Enter a template name and click "Create"
3. Write the AI instruction in the **Instruction** field
4. Select the preset for this template in **Default Preset**
5. Click **Save Template** to save

### Editing/Deleting Templates
- Select an existing template from the dropdown to load its contents
- Click **Save Template** to overwrite after making changes
- Click the **Delete** button to delete the selected template (a confirmation dialog is shown)

## Settings Tab

Manages AI presets (combinations of parameter settings).

### Initial Presets

| Preset | Characteristics |
|--------|-----------------|
| default | General purpose (Temperature: 0.7, Max Tokens: 500) |
| creative | For creative output (Temperature: 1.0, Max Tokens: 1000) |
| precise | For accurate, concise output (Temperature: 0.2, Max Tokens: 300) |
| vision | For image analysis (Vision-capable, Timeout: 120s) |
| vision-unload-after-generation | Same as vision, but automatically unloads the model after generation (frees VRAM) |

### Basic Settings

- **Model**: Select the model to use. "(use loaded model)" uses the model currently loaded in LM Studio. **Fetch Models** retrieves the model list from LM Studio
- **Temperature** (0-2): Lower values produce more consistent output, higher values produce more diverse output
- **Max Tokens** (1-10000): Maximum number of tokens the AI can generate
- **System Prompt**: Prompt that specifies the AI's overall behavior

### Advanced Settings

- **Top-P** (0-1): Controls output diversity (optional)
- **Top-K** (1-100): Limits candidate word count (optional)
- **Repeat Penalty** (1-2): Suppresses repetition (optional)
- **Timeout** (1000-300000ms): Response wait timeout. Default is 30 seconds
- **Unload model after generation (free VRAM)**: When enabled, automatically unloads the loaded model from VRAM immediately after generation completes. Useful when running LM Studio alongside other GPU workloads such as image generation. Recommended for presets that only run AI processing occasionally
- **Supports Vision**: Enables image input. When enabled, you can set **Max Images** (1-10, default 4)

### Preset Operations
- **New**: Create a new preset with default values
- **Delete**: Delete the selected preset (initial presets cannot be deleted)
- **Reset**: Revert changes to pre-save state
- **Save Preset**: Save current settings

### Temporary Changes (Run Without Saving)
When you change a value in the Settings tab, it is applied to the next execution **even without clicking Save Preset**. While unsaved changes exist, the footer shows "Running with temporary preset settings (changes will be discarded after execution)". Useful for quickly trying out a different temperature or unload setting without permanently overwriting the preset. Changes are discarded when the dialog is closed.

## Notes
- LM Studio must be running locally
- Default endpoint is `http://localhost:1234/v1/chat/completions`
- Preset names can only contain alphanumeric characters, hyphens, and underscores
- Initial presets (default, creative, precise, vision, vision-unload-after-generation) cannot be deleted

## Related

- [LM Studio](../../02-Glossary/01-LM Studio.md)
- [LM Studio Edit](../../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/13-LMStudio Edit.md)
- [LM Studio Unload Model](02-Unload Model.md)
- [Add From LM Studio](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/20-Add from LM Studio.md)
- [Suggest Name with AI](../../../PromptTree/04-Menu/01-Selected/09-Suggest Name with AI.md)
- [Suggest Tags with AI](../../../PromptTree/04-Menu/01-Selected/08-Suggest Tags with AI.md)
- [Bulk Suggest Names with AI](../../../PromptTree/04-Menu/05-Checked/06-Bulk Suggest Names with AI.md)
- [Bulk Suggest Tags with AI](../../../PromptTree/04-Menu/05-Checked/05-Bulk Suggest Tags with AI.md)
- [env.LMEDIT](../../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/08-env.LMEDIT.md)
- [Initial Setup](../../03-Tips/01-Recommended Initial Settings.md)
