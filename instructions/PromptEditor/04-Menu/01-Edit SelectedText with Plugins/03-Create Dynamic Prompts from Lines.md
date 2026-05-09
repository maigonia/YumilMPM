# Create Dynamic Prompts from Lines

**Create Dynamic Prompts from Lines**

## What It Does

Converts multi-line text to Dynamic Prompts format `{option1|option2|option3}`.

## How to Use

1. Select multi-line text
2. Select **Edit SelectedText with Plugins > Create Dynamic Prompts from Lines** from the menu
3. Each line is converted to a format separated by `|`

## Example

- Input:
```
red hair
blue hair
green hair
```
- Output: `{red hair|blue hair|green hair}`

## What Are Dynamic Prompts

An extension for Stable Diffusion where writing in `{A|B|C}` format randomly selects one during generation. Useful for easily creating variations.

Supported extensions:

- [sd-dynamic-prompts](https://github.com/adieyal/sd-dynamic-prompts) (for Stable Diffusion WebUI)
- [comfyui-dynamicprompts](https://github.com/adieyal/comfyui-dynamicprompts) (for ComfyUI)

## Notes

- Empty lines are automatically excluded

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
