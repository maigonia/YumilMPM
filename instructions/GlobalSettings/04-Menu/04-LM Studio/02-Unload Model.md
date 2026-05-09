# LM Studio Unload Model
**LM Studio Unload Model**

## When to Use
- When you want to free VRAM after batch operations such as [Add From LM Studio](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md) or [Bulk Suggest Tags with AI](../../../PromptTree/04-Menu/05-Checked/05-Bulk%20Suggest%20Tags%20with%20AI.md) finish
- When you run LM Studio alongside other GPU workloads (e.g. image generation) and want to manually unload the model from VRAM
- When you want to trigger an unload instantly from a keyboard shortcut or command palette

## What It Does
Immediately unloads all models currently loaded in LM Studio. The result is shown in the status bar (for example `LM Studio: unloaded 1 model(s)` or `LM Studio: no models loaded`).

This action does not require opening the [LM Studio Settings](01-Settings.md) dialog, so you can quickly free VRAM from the menu, a shortcut, or the command palette.

## How to Use
- Menu: **GlobalSettings > LM Studio > Unload Model**
- Command palette: `settings: LM Studio > Unload Model`
- Shortcut: assign a key to `GlobalSettings_LMStudio_UnloadModel` in the shortcut settings

## Compared to the `unloadAfterGeneration` Preset Option

[LM Studio Settings](01-Settings.md) presets have an `unloadAfterGeneration` option that automatically unloads the model after each generation. Which one to use depends on the workflow:

- **Single AI edits** (such as one-off [LM Studio Edit](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/13-LMStudio%20Edit.md) runs): a preset with `unloadAfterGeneration` enabled (e.g. `vision-unload-after-generation`) is convenient — every generation is followed by an automatic unload
- **Batch processing** ([Add From LM Studio](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md), [Bulk Suggest Tags with AI](../../../PromptTree/04-Menu/05-Checked/05-Bulk%20Suggest%20Tags%20with%20AI.md), [Bulk Suggest Names with AI](../../../PromptTree/04-Menu/05-Checked/06-Bulk%20Suggest%20Names%20with%20AI.md), etc., which loop and generate many times internally): enabling `unloadAfterGeneration` is inefficient because it forces a load/unload on every iteration. Run with a normal preset and call this **Unload Model** action once after the whole batch finishes

## Notes
- LM Studio must be running locally
- The endpoint follows the default preset (typically `http://localhost:1234/v1/chat/completions`)
- If LM Studio is not running or the connection fails, an error message is shown in the status bar

## Related

- [LM Studio](../../02-Glossary/01-LM%20Studio.md)
- [LM Studio Settings](01-Settings.md)
- [LM Studio Edit](../../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/13-LMStudio%20Edit.md)
- [Add From LM Studio](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/20-Add%20from%20LM%20Studio.md)
- [Bulk Suggest Tags with AI](../../../PromptTree/04-Menu/05-Checked/05-Bulk%20Suggest%20Tags%20with%20AI.md)
- [Bulk Suggest Names with AI](../../../PromptTree/04-Menu/05-Checked/06-Bulk%20Suggest%20Names%20with%20AI.md)
