# ComfyUI Extension

**ExternalPromptRequester Node**

## When to Use

- When you want to automatically get prompts from this app each time you generate an image in ComfyUI
- When you want to automatically supply different prompts with each workflow execution

## What It Does

By adding the ExternalPromptRequester node to a ComfyUI workflow, you can automatically retrieve prompts from this app timed with image generation. Up to 10 categories of prompts can be received simultaneously.

## How to Use

1. Check the categories you want to output in this app's **CategoryTree**
2. Add the **ExternalPromptRequester** node to the ComfyUI workflow
3. Enter CategoryTree category names in each prompt field
4. Connect the ExternalPromptRequester node outputs to Clip Text Encoder node prompt inputs
5. Execute **Generation On Demand > Start On Demand** in this app to start the server
6. Run the workflow in ComfyUI

### Node Settings

| Setting         | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| timeout_seconds | Request timeout in seconds (5-300, default: 30)              |
| prompt_1        | Category name to retrieve (default: Positive)                |
| prompt_2        | Category name to retrieve (default: Negative)                |
| prompt_3        | Category name to retrieve (default: Pose)                    |
| prompt_4-10     | Additional category names (optional, ignored if empty)       |

Enter CategoryTree category names in each field to get the generation results from the corresponding outputs.

## Notes

- Category names must exactly match the names displayed in the **CategoryTree**
- New prompts are generated with each ComfyUI workflow execution

## Download

- [ComfyUI Yumil MPM (GitHub)](https://github.com/maigonia/comfyui-yumil-mpm)

## Related

- [Start On Demand](../../04-Menu/02-Generation%20On%20Demand/01-Start%20On%20Demand.md)
- [API Server Settings](../../04-Menu/02-Generation%20On%20Demand/02-API%20Server%20Settings.md)
- [Stable Diffusion Extension](02-Stable%20Diffusion%20Extension.md)
- [Generation Modes](../01-Generation%20Modes.md)
- [Once Generation](../../04-Menu/01-Once%20Generation.md)
