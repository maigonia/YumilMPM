# REST API Reference

**REST API Reference**

This is the specification for this app's built-in HTTP API server. AI Auto-Operation ([AI Auto-Operation](08-AI%20Auto-Operation.md)) calls this API via the MCP protocol, but here all endpoints are exposed for developers and plugin authors who want to call them **directly via HTTP**.

> **API Status: Evolving**
>
> The v1 API is not yet considered stable, and may change in future releases. Best efforts are made to preserve backward compatibility, but no guarantees are given. When writing scripts, it is recommended to verify behavior after each app version update. Notable breaking changes will be documented in the release notes.

## When to Use

- When you want to operate this app from MCP-incompatible environments (CI scripts / custom tools / other languages)
- When you're building plugins or extension tools
- When you want to understand AI Auto-Operation's behavior (the MCP server internally calls this API)
- When you want to bulk-register or batch-edit large numbers of prompts via batch processing

## What It Does

You can read and write this app's state from external processes via HTTP requests. The provided functionality covers roughly the same scope as AI Auto-Operation, with about 51 endpoints available.

> **Relationship to MCP**: AI Auto-Operation ([AI Auto-Operation](08-AI%20Auto-Operation.md)) has a configuration where the MCP server internally calls this REST API. If you use an AI client, going through MCP is convenient, but if you call from your own scripts, direct HTTP is simpler.

## API Endpoint Categories

The 51 endpoints are categorized into 6 pages by purpose.

| Category | Count | Main Content | Link |
|---|---|---|---|
| Read (READ) | 12 | List, get, and search categories/prompts/tags | [REST API - Read Endpoints](02-REST%20API%20-%20Read%20Endpoints.md) |
| Write & Check (WRITE) | 13 | Add/edit prompts, check operations, template settings | [REST API - Write Endpoints](03-REST%20API%20-%20Write%20Endpoints.md) |
| Delete (DELETE) | 5 | Delete prompts/categories/tags (dry_run supported) | [REST API - Delete Endpoints](04-REST%20API%20-%20Delete%20Endpoints.md) |
| Queue (QUEUE) | 8 | Queue pattern management | [REST API - Queue Endpoints](05-REST%20API%20-%20Queue%20Endpoints.md) |
| Generation (GENERATION) | 4 | Classification outline, CI evaluation, generation preview, category structure retrieval | [REST API - Generation Endpoints](06-REST%20API%20-%20Generation%20Endpoints.md) |
| Instruction & History | 6 | Help reference, generation history | [REST API - Instruction Endpoints](07-REST%20API%20-%20Instruction%20Endpoints.md) |

## Setup

### Step 1: Start the API Server

Click PromptGeneration menu > **Generation On Demand**. This starts the HTTP server on localhost.

> **Important**: All external requests will fail unless the API server is running.

### Step 2: Check the Port Number and API Token

You can check these in GlobalSettings > **API Server Settings** ([API Server Settings](../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/02-API%20Server%20Settings.md)).

- **Default port**: `19720`
- **API token**: A 64-character hex random string is auto-generated on first startup. It can also be regenerated from the same screen
- **Token file**: Also written to `~/.mpm/api_key` (readable from external tools)

### Step 3: Verify Operation (curl)

```bash
# Health check (no authentication required)
curl http://127.0.0.1:19720/api/v1/health

# Response: {"ok":true}
```

```bash
# Get project info (authentication required)
curl -X POST http://127.0.0.1:19720/api/v1/query \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query_type":"get_project_info","params":{}}'
```

## Common Specifications

### Base URL

```
http://127.0.0.1:{port}/api/v1
```

`{port}` defaults to `19720`. Configurable in GlobalSettings > API Server Settings.

### Endpoint List

| Method | Path | Auth | Purpose |
|---|---|---|---|
| `GET` | `/health` | No | Server health check |
| `GET` | `/status` | Yes | Server state check |
| `POST` | `/generate` | Yes | Execute prompt generation |
| `POST` | `/query` | Yes | General-purpose endpoint for data retrieval and operations (encapsulates 51 `query_type`s) |

Most operations are performed via `POST /query`.

### Authentication

All operation endpoints require Bearer Token authentication.

```
Authorization: Bearer {API_TOKEN}
```

The token uses constant-time comparison and is resistant to timing attacks. Sending an invalid token returns `401 Unauthorized` after a 100ms delay.

### Common Request Format for `POST /query`

```json
{
  "query_type": "operation_name",
  "params": {
    "param1": "value1",
    "param2": 123
  }
}
```

- `query_type` (string, required): One of 51 types. See each endpoint-specific page for details
- `params` (object, required): Per-endpoint parameters. Specify `{}` if empty

### Response Format

**On success**: A JSON object or array that varies per endpoint.

**On error**:

```json
{
  "error": "error message"
}
```

Common error HTTP status codes:

| Status | Meaning |
|---|---|
| `400 Bad Request` | Invalid parameters / unknown `query_type` |
| `401 Unauthorized` | Invalid or missing token |
| `500 Internal Server Error` | Internal exception (details in `error` message) |

### Programmable Block Errors

CI evaluation (`evaluate_ci`) and generation preview (`preview_generation`) return Programmable Block runtime errors in a `programmable_errors` array (errors inside [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) are aggregated in this field rather than thrown).

```json
{
  "expression": "MyCategory",
  "result": "...",
  "programmable_errors": [
    "SIMILARITY: Vectors cannot be empty"
  ]
}
```

## Complete Request/Response Examples

### Example 1: Get Checked Prompts

**Request**:

```bash
curl -X POST http://127.0.0.1:19720/api/v1/query \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "query_type": "get_checked_prompts",
    "params": {
      "category_name": "Quality"
    }
  }'
```

**Response**:

```json
[
  {
    "id": "1776662469597-gefwo8qqf",
    "name": "masterpiece",
    "content": "masterpiece, best quality",
    "path": "Quality/Common/masterpiece",
    "tags": ["quality", "common"]
  }
]
```

### Example 2: Add a New Prompt

**Request**:

```bash
curl -X POST http://127.0.0.1:19720/api/v1/query \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "query_type": "add_prompt",
    "params": {
      "category_name": "Quality",
      "name": "new_prompt",
      "content": "high quality, detailed",
      "tags": ["quality"]
    }
  }'
```

**Response**:

```json
{
  "success": true,
  "prompt_id": "1776700000000-abcdef123",
  "name": "new_prompt",
  "category_name": "Quality",
  "parent_id": null
}
```

### Example 3: Execute Generation

`/generate` is a dedicated endpoint, not `/query`.

**Request**:

```bash
curl -X POST http://127.0.0.1:19720/api/v1/generate \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "session_id": "my-session-001"
  }'
```

`session_id` is optional (auto-generated as `api-{8byte hex}` if omitted).

## Security

- **localhost only**: The API server listens on `127.0.0.1` and is not accessible from external networks
- **Token authentication**: All operations require a Bearer Token
- **Token protection**: The `~/.mpm/api_key` file is under the personal user directory. On shared machines, be careful with permissions
- **Prompt injection**: Prompt content submitted via the API may be passed to AI clients. When handling data from untrusted sources, content review is recommended

## Supplementary: Choosing Between AI Auto-Operation and REST API

| Use Case | Recommended |
|---|---|
| Operating from MCP-compatible AI like Claude Code | [AI Auto-Operation](08-AI%20Auto-Operation.md) (via MCP) |
| Custom scripts / batch processing | Direct REST API call |
| Operations from other languages (Python / Go etc.) | Direct REST API call |
| Plugin / extension development | Direct REST API call |
| Checking API server specifications | This page + each subpage |

## Tips

- **Data persistence**: This app does not persist in-memory data until [Save Project](../../File/02-Menu/06-Save%20Project.md). Data submitted via the API is the same — closing the app before saving will lose the data
- **Use dry_run**: `delete_*` endpoints can preview "what will be deleted" with `dry_run: true`
- **resolve_tags option**: `list_prompts` / `get_prompt` series can return tag IDs as-is with `resolve_tags: false`. Resolve names with `list_tags` if needed to reduce round trips
- **search_prompts pagination**: Use `limit` (max 500) and `offset` to fetch large numbers of prompts in stages. `count_only: true` lets you fetch just the count first

## Related

- [AI Auto-Operation](08-AI%20Auto-Operation.md)
- [API Server Settings](../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/02-API%20Server%20Settings.md)
- [MCP Server Settings](../../GlobalSettings/04-Menu/08-MCP%20Server%20Settings.md)
- [On Demand](../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/README.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Save Project](../../File/02-Menu/06-Save%20Project.md)
- [REST API - Read Endpoints](02-REST%20API%20-%20Read%20Endpoints.md)
- [REST API - Write Endpoints](03-REST%20API%20-%20Write%20Endpoints.md)
- [REST API - Delete Endpoints](04-REST%20API%20-%20Delete%20Endpoints.md)
- [REST API - Queue Endpoints](05-REST%20API%20-%20Queue%20Endpoints.md)
- [REST API - Generation Endpoints](06-REST%20API%20-%20Generation%20Endpoints.md)
- [REST API - Instruction Endpoints](07-REST%20API%20-%20Instruction%20Endpoints.md)
