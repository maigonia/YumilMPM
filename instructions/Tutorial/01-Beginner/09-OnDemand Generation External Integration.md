# OnDemand Generation (External Integration)

Integrate with Stable Diffusion WebUI or ComfyUI to automatically supply prompts in sync with image generation timing. Communication is handled via an API server.

## ComfyUI Integration

1. Install custom node "[ComfyUI Yumil MPM](https://github.com/maigonia/comfyui-yumil-mpm)"
2. Check the categories you want to output in CategoryTree
3. Add a ComfyUI Yumil MPM node to your workflow
4. Enter CategoryTree category names in each prompt field
5. Connect the node's outputs to Clip Text Encoder, etc.
6. Run `Generation On Demand > Start On Demand` in this app to start the server
7. Execute your ComfyUI workflow

- Supports up to 10 categories simultaneously

## Stable Diffusion WebUI Integration

1. Install extension "[SD Webui Yumil MPM](https://github.com/maigonia/sd-webui-yumil-mpm)"
2. Open "External Prompt Requester (API)" in txt2img/img2img tab
3. Check "Enable External Prompt Request"
4. Enter CategoryTree category names in Positive/Negative Prompt Category
5. Run `Generation On Demand > Start On Demand` in this app to start the server
6. Press WebUI's Generate button to generate images

- Stable Diffusion WebUI version supports Positive and Negative (2 categories)
