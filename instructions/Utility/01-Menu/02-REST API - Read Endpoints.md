# REST API - Read Endpoints

**REST API - Read Endpoints**

Endpoints dedicated to data retrieval and search (12 endpoints). Do not modify state.

> See [REST API Reference](01-REST API Reference.md) for common specifications (authentication / request format / error format).

## Endpoint List

| query_type | Purpose |
|---|---|
| `list_categories` | Hierarchical list of all categories |
| `get_category_info` | Detailed info for a single category |
| `list_prompts` | List of prompts within a category |
| `get_prompt` | Complete content of a single prompt |
| `get_prompts_batch` | Batch get multiple prompts by ID array |
| `get_checked_prompts` | List of checked prompts |
| `get_project_info` | Project summary |
| `search_prompts` | Full-text search (regex / exclusion search supported) |
| `list_tags` | List of global tags |
| `get_all_category_templates` | Template settings for all categories |
| `list_check_presets` | List of saved check presets |
| `list_favorite_lists` | List of favorite lists within a category |

---

## list_categories

- **Purpose**: Get hierarchical list of all categories with summary counts
- **Parameters**: None

**Request example**:

```json
{ "query_type": "list_categories", "params": {} }
```

**Response example**:

```json
[
  {
    "name": "Quality",
    "depth": 0,
    "parent_name": null,
    "output_enabled": true,
    "prompt_count": 25,
    "checked_count": 3
  },
  {
    "name": "Common",
    "depth": 1,
    "parent_name": "Quality",
    "output_enabled": true,
    "prompt_count": 12,
    "checked_count": 1
  }
]
```

**Errors**: None (returns empty array if no categories)

---

## get_category_info

- **Purpose**: Get detailed info for a single category (including template settings)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |

**Request example**:

```json
{
  "query_type": "get_category_info",
  "params": { "category_name": "Quality" }
}
```

**Response example**:

```json
{
  "name": "Quality",
  "output_enabled": true,
  "prompt_count": 25,
  "checked_count": 3,
  "is_parts_mode": false,
  "target": "checked",
  "filter": "",
  "pick": "",
  "sort": "",
  "join": ", ",
  "edit": "",
  "template_directive": "",
  "final_edit_enabled": false
}
```

Unset fields are omitted.

**Errors**:
- `Category not found: {categoryName}`

---

## list_prompts

- **Purpose**: List prompts in a category (rich filter options)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `leaf_only` | boolean | — | `false` | Return only leaf nodes (no children) |
| `parent_id` | string | — | — | Return only direct children of specified prompt |
| `descendants_of` | string | — | — | Return descendants (subtree) of specified prompt |
| `resolve_tags` | boolean | — | `true` | Convert tag IDs to names |

**Request example**:

```json
{
  "query_type": "list_prompts",
  "params": {
    "category_name": "Quality",
    "leaf_only": true,
    "resolve_tags": true
  }
}
```

**Response example**:

```json
[
  {
    "id": "1776662469597-gefwo8qqf",
    "name": "masterpiece",
    "content": "masterpiece, best quality, ultra detailed...",
    "checked": true,
    "is_folder": false,
    "is_file": true,
    "path": "Quality/Common/masterpiece",
    "tags": ["quality", "common"],
    "created_at": "2026-04-12T10:23:45.123Z"
  }
]
```

> `content` is truncated to 200 characters with a trailing `...`. Use `get_prompt` for full content.

**Errors**:
- `Category not found: {categoryName}`
- `Prompt not found: {descendantsOf}` (when `descendants_of` is specified)

---

## get_prompt

- **Purpose**: Get a single prompt with full content (memos optional)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `prompt_id` | string | ✓ | — | Prompt ID |
| `include_memos` | boolean | — | `true` | Include memos |
| `resolve_tags` | boolean | — | `true` | Convert tag IDs to names |

**Request example**:

```json
{
  "query_type": "get_prompt",
  "params": {
    "category_name": "Quality",
    "prompt_id": "1776662469597-gefwo8qqf"
  }
}
```

**Response example**:

```json
{
  "id": "1776662469597-gefwo8qqf",
  "name": "masterpiece",
  "content": "masterpiece, best quality, ultra detailed, 8k uhd, ...",
  "checked": true,
  "is_folder": false,
  "is_file": true,
  "path": "Quality/Common/masterpiece",
  "tags": ["quality", "common"],
  "created_at": "2026-04-12T10:23:45.123Z",
  "memos": ["Source: stable-diffusion wiki"]
}
```

**Errors**:
- `Category not found: {categoryName}`
- `Prompt not found: {promptId}`

---

## get_prompts_batch

- **Purpose**: Batch get multiple prompts in a single request (reduce round trips)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name (all prompts in same category) |
| `prompt_ids` | string[] | ✓ | — | Array of prompt IDs |
| `include_memos` | boolean | — | `true` | Include memos |
| `resolve_tags` | boolean | — | `true` | Convert tag IDs to names |

**Request example**:

```json
{
  "query_type": "get_prompts_batch",
  "params": {
    "category_name": "Quality",
    "prompt_ids": ["id-1", "id-2", "id-3"]
  }
}
```

**Response example**: Array of objects with the same structure as `get_prompt`.

> Non-existent IDs are silently filtered out (no error).

**Errors**:
- `Category not found: {categoryName}`

---

## get_checked_prompts

- **Purpose**: Get only the checked prompts within a category
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `resolve_tags` | boolean | — | `true` | Convert tag IDs to names |

**Request example**:

```json
{
  "query_type": "get_checked_prompts",
  "params": { "category_name": "Quality" }
}
```

**Response example**:

```json
[
  {
    "id": "1776662469597-gefwo8qqf",
    "name": "masterpiece",
    "content": "masterpiece, best quality",
    "path": "Quality/Common/masterpiece",
    "tags": ["quality"]
  }
]
```

**Errors**:
- `Category not found: {categoryName}`

---

## get_project_info

- **Purpose**: Get a summary of the entire project
- **Parameters**: None

**Request example**:

```json
{ "query_type": "get_project_info", "params": {} }
```

**Response example**:

```json
{
  "project_path": "C:/Users/me/Documents/MyProject",
  "category_count": 8,
  "total_prompts": 432,
  "checked_prompts": 17
}
```

**Errors**: None

---

## search_prompts

- **Purpose**: Full-text search (flexible filtering + pagination)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `query` | string | ✓ | — | Search term (empty string returns 0 results) |
| `target` | string | — | `"name"` | Search target: `name` / `content` / `tag` / `path` |
| `category_name` | string | — | — | Limit to a single category |
| `use_regex` | boolean | — | `false` | Treat as case-insensitive regex |
| `exclude` | boolean | — | `false` | NOT search (return non-matches) |
| `limit` | number | — | `50` | Max items per page (max 500) |
| `offset` | number | — | `0` | Pagination offset |
| `count_only` | boolean | — | `false` | Return only the count |

**Request example**:

```json
{
  "query_type": "search_prompts",
  "params": {
    "query": "masterpiece",
    "target": "name",
    "limit": 20,
    "use_regex": false
  }
}
```

**Response example**:

```json
{
  "total_count": 5,
  "returned_count": 5,
  "has_more": false,
  "results": [
    {
      "category_name": "Quality",
      "id": "1776662469597-gefwo8qqf",
      "name": "masterpiece",
      "content": "masterpiece, best quality...",
      "checked": true,
      "path": "Quality/Common/masterpiece"
    }
  ]
}
```

When `count_only=true`:

```json
{ "total_count": 5 }
```

**Errors**:
- `Category not found: {categoryName}` (when `category_name` is specified)

> Regex compilation errors silently fall back to literal matching.

---

## list_tags

- **Purpose**: Get list of global tags (with usage counts)
- **Parameters**: None

**Request example**:

```json
{ "query_type": "list_tags", "params": {} }
```

**Response example**:

```json
[
  { "name": "quality", "usage_count": 25 },
  { "name": "system", "usage_count": 8, "protected": true }
]
```

`protected: true` is included only for tags that cannot be manually deleted.

**Errors**: None

---

## get_all_category_templates

- **Purpose**: Batch get template settings for all categories
- **Parameters**: None

**Request example**:

```json
{ "query_type": "get_all_category_templates", "params": {} }
```

**Response example**:

```json
[
  {
    "name": "Quality",
    "output_enabled": true,
    "is_parts_mode": false,
    "target": "checked",
    "join": ", "
  },
  {
    "name": "Style",
    "output_enabled": false
  }
]
```

> Default-value fields are omitted (same rule as `get_category_info`).

**Errors**: None

---

## list_check_presets

- **Purpose**: Get list of saved check presets
- **Parameters**: None

**Request example**:

```json
{ "query_type": "list_check_presets", "params": {} }
```

**Response example**:

```json
[
  {
    "id": "preset-001",
    "name": "Anime Style",
    "description": "Anime-focused checked items",
    "checked_count": 15,
    "category_states_count": 8,
    "created_at": "2026-04-10T08:00:00.000Z",
    "updated_at": "2026-04-15T12:30:00.000Z"
  }
]
```

**Errors**: None

---

## list_favorite_lists

- **Purpose**: Get list of favorite lists within a category
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |

**Request example**:

```json
{
  "query_type": "list_favorite_lists",
  "params": { "category_name": "Quality" }
}
```

**Response example**:

```json
[
  { "id": "fav-001", "name": "Best Quality", "chunk_count": 5 }
]
```

**Errors**:
- `Category not found: {categoryName}`

---

## Related

- [REST API Reference](01-REST API Reference.md)
- [REST API - Write Endpoints](03-REST API - Write Endpoints.md)
- [REST API - Delete Endpoints](04-REST API - Delete Endpoints.md)
- [REST API - Generation Endpoints](06-REST API - Generation Endpoints.md)
- [Tag](../../PromptBrowser/01-Basics/04-Tag.md)
- [Check Preset](../../AdvancedPanel/02-Glossary/02-Check Preset.md)
- [Favorite List](../../AdvancedPanel/02-Glossary/03-Favorite List.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category Template.md)
