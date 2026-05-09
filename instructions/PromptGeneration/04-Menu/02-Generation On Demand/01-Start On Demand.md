# Start On Demand

**Generation On Demand > Start On Demand**

## When to Use

- When you want to automate prompt generation in conjunction with external apps (ComfyUI, Stable Diffusion WebUI, etc.)

## What It Does

By installing a dedicated extension in external apps (ComfyUI, Stable Diffusion WebUI, etc.) and configuring output categories on the extension side, it automatically generates and sends prompts in response to prompt requests from external apps.

(Launches as a local API server)

# Processing

It essentially performs the same processing as **PromptGeneration > Once Generation** each time an external app makes a request.

## How to Use

1. Select **Generation On Demand > Start On Demand** from the menu
2. The API server starts and begins accepting requests

## Integration Flow

```
External App → Sends HTTP request → API server receives → Generates prompt → Returns result
```

To send requests from an external app, an **API key** is required. The API key can be checked in the [API Server Settings](02-API%20Server%20Settings.md) dialog.

## Using from External Apps

### Request

Send a request with an API key to `POST http://127.0.0.1:19720/api/v1/generate`.

```
POST /api/v1/generate
Authorization: Bearer {API key}
Content-Type: application/json
```

### Response

Generation results are returned in JSON format.

```json
{
  "session_id": "api-d4e5f6a7b8c9d0e1",
  "results": [
    {
      "category_name": "Category Name",
      "prompt": "Generated prompt text",
      "success": true,
      "has_changed": true,
      "error_message": null
    }
  ],
  "generated_at": "2025-02-08T15:30:45.123456Z"
}
```

- `results` contains generation results for each category
- `prompt` is the generated prompt text
- `has_changed` indicates whether the result differs from the previous generation

### Other Endpoints

| Endpoint             | Auth     | Description                                          |
| -------------------- | -------- | ---------------------------------------------------- |
| `GET /api/v1/health` | Not required | Server health check                              |
| `GET /api/v1/status` | Required | Project load state and generation status check       |

## Notes

- The server starts on port 19720
- Use the **Stop** menu to stop
- This menu is disabled if on-demand mode is already active
- Once Generation can still be executed during on-demand mode
- Cannot be used simultaneously with Timer Generation. Stop on-demand first to use the timer

## Related

- [Generation Modes](../../01-Basics/01-Generation%20Modes.md)
- [API Server Settings](02-API%20Server%20Settings.md)
- [Stop](../04-Stop.md)
- [Once Generation](../01-Once%20Generation.md)
- [Timer Generation Start](../03-Timer%20Generation/01-Timer%20Generation%20Start.md)
- [ComfyUI Extension](../../01-Basics/05-External%20App%20Integration/01-ComfyUI%20Extension.md)
- [Stable Diffusion Extension](../../01-Basics/05-External%20App%20Integration/02-Stable%20Diffusion%20Extension.md)
