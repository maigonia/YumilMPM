# API Server Settings

**API Server Settings...**

## When to Use

- When you want to check or copy the API key
- When you want to regenerate the API key

## What It Does

Opens the settings dialog for the local API server used for on-demand generation. You can check, copy, and regenerate the API key.

The API key is maintained within the app and is also automatically saved to the `~/.mpm/api_key` file. This file is automatically updated to the latest state when the API key is regenerated or the API server starts.

## How to Use

Select "API Server Settings..." from the menu to open the dialog.

### API Key

The API key required for external apps to connect to the API server. It can be viewed and operated even when the server is stopped.

| Operation | Description |
|-----------|-------------|
| Show/Hide toggle | Show or mask the full API key |
| Copy | Copy the API key to the clipboard |
| Regenerate | Generate a new API key (the previous key becomes invalid) |

### Automatic API Key Sharing

The API key is automatically saved to `~/.mpm/api_key`. The ExternalPromptRequester extensions used by [ComfyUI Extension](../../01-Basics/05-External App Integration/01-ComfyUI Extension.md) and [Stable Diffusion Extension](../../01-Basics/05-External App Integration/02-Stable Diffusion Extension.md) automatically read the API key from this file, eliminating the need for manual API key configuration.

## Notes

- The API server only accepts connections from localhost (127.0.0.1)
- The API key persists across sessions and can be regenerated at any time
- When the API key is regenerated, `~/.mpm/api_key` is also automatically updated

## Related

- [Start On Demand](01-Start On Demand.md)
- [ComfyUI Extension](../../01-Basics/05-External App Integration/01-ComfyUI Extension.md)
- [Stable Diffusion Extension](../../01-Basics/05-External App Integration/02-Stable Diffusion Extension.md)
