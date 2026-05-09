# Stable Diffusion Extension

**External Prompt Requester (API)**

## When to Use

- When you want to automatically get prompts from this app each time you generate an image in Stable Diffusion WebUI

## What It Does

When generating images in Stable Diffusion WebUI's txt2img / img2img, it automatically retrieves and applies Positive and Negative prompts from this app.

## How to Use

1. Check the categories you want to output in this app's CategoryTree
2. Open the txt2img or img2img tab in WebUI
3. Open the "**External Prompt Requester (API)**" accordion
4. Check "**Enable External Prompt Request**"
5. Enter the [Output Category Name](../../../CategoryTree/02-Glossary/01-Output Category.md)s from **CategoryTree** in Positive / Negative Prompt Category
6. Execute **Generation On Demand > Start On Demand** in this app to start the server
7. Execute image generation with the WebUI Generate button

### Settings

| Setting                        | Description                                                               |
| ------------------------------ | ------------------------------------------------------------------------- |
| Enable External Prompt Request | Toggle the feature on/off                                                 |
| Positive Prompt Category       | Category name for Positive prompts (default: PositivePrompt)             |
| Negative Prompt Category       | Category name for Negative prompts (default: NegativePrompt)             |
| Timeout (sec)                  | Request timeout in seconds (5-300, default: 30)                           |

Settings can also be changed and saved in the WebUI's **Settings** page (External Prompt Requester section).

## Notes

- Category names must exactly match the names displayed in the CategoryTree
- Supports 2 categories: Positive and Negative

## Download

- [SD Webui Yumil MPM (GitHub)](https://github.com/maigonia/sd-webui-yumil-mpm)

## Related

- [Start On Demand](../../04-Menu/02-Generation On Demand/01-Start On Demand.md)
- [API Server Settings](../../04-Menu/02-Generation On Demand/02-API Server Settings.md)
- [ComfyUI Extension](01-ComfyUI Extension.md)
- [Generation Modes](../01-Generation Modes.md)
- [Once Generation](../../04-Menu/01-Once Generation.md)
