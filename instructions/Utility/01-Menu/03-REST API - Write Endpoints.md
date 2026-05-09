# REST API - Write Endpoints

**REST API - Write Endpoints**

Write-system endpoints for adding/editing prompts, check operations, template settings, preset application, etc. (13 endpoints).

> See [REST API Reference](01-REST%20API%20Reference.md) for common specifications (authentication / request format). Data persistence requires [Save Project](../../File/02-Menu/06-Save%20Project.md).

## Endpoint List

| query_type | Purpose |
|---|---|
| `add_prompt` | Add a new prompt |
| `edit_prompt` | Edit a prompt (content/name/tags/memos/images) |
| `check_prompt` | Check a single prompt |
| `uncheck_prompt` | Uncheck a single prompt |
| `check_all` | Check all prompts in a category |
| `uncheck_all` | Uncheck all prompts in a category |
| `set_category_output` | Toggle category output ON/OFF |
| `set_category_template` | Set category template settings |
| `set_final_edit` | Set category Final Edit settings |
| `apply_check_preset` | Apply a check preset |
| `save_check_preset` | Save current state as a preset |
| `apply_favorite_list` | Apply a favorite list (add to checks) |
| `add_category` | Add a new category |

---

## add_prompt

- **Purpose**: Create a new prompt
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `name` | string | ✓ | — | Prompt name |
| `content` | string | — | `""` | Prompt body |
| `parent_id` | string | — | — | Parent prompt ID (for nesting) |
| `tags` | string[] | — | — | Array of tag names |
| `display_type` | string | — | `"normal"` | `"group"` (folder) or `"normal"` |
| `memos` | string[] | — | — | Array of memos |
| `image_paths` | string[] | — | — | Array of image file paths |
| `create_missing_tags` | boolean | — | `false` | Auto-create non-existent tags |

**Request example**:

```json
{
  "query_type": "add_prompt",
  "params": {
    "category_name": "Quality",
    "name": "high_quality",
    "content": "high quality, detailed",
    "tags": ["quality", "common"],
    "create_missing_tags": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "prompt_id": "1776700000000-abcdef123",
  "name": "high_quality",
  "category_name": "Quality",
  "parent_id": null,
  "created_tags": ["common"]
}
```

`created_tags` includes only tags newly created by `create_missing_tags=true`.

> Duplicate names automatically get a suffix appended (`ChunkNameManager.generateSafeName`).

**Errors**:
- `Category not found: {categoryName}`
- `Parent chunk not found: {parentId}` (when `parent_id` is specified)
- `Invalid image path "{imagePath}": {error}`
- `Post-add validation failed:\n{details}` (post-add plugin validator)
- Tag resolution errors (when non-existent tags specified with `create_missing_tags=false`)

---

## edit_prompt

- **Purpose**: Update content/name/tags/memos/images of an existing prompt
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `prompt_id` | string | ✓ | — | Prompt ID |
| `content` | string | — | — | New body |
| `name` | string | — | — | New name |
| `tags` | string[] | — | — | New array of tag names (full replacement) |
| `memos` | string[] | — | — | New array of memos (full replacement) |
| `image_paths` | string[] | — | — | New array of image paths (full replacement) |
| `create_missing_tags` | boolean | — | `false` | Auto-create non-existent tags |

> At least one of `content` / `name` / `tags` / `memos` / `image_paths` is required.

**Request example**:

```json
{
  "query_type": "edit_prompt",
  "params": {
    "category_name": "Quality",
    "prompt_id": "1776662469597-gefwo8qqf",
    "content": "masterpiece, best quality, ultra detailed",
    "tags": ["quality", "premium"]
  }
}
```

**Response example**:

```json
{
  "success": true,
  "prompt_id": "1776662469597-gefwo8qqf",
  "created_tags": ["premium"]
}
```

> Unprotected tags that become unused are auto-deleted (`deleteTag` called when `usage_count <= 0`).

**Errors**:
- `Category not found: {categoryName}`
- `Prompt not found: {promptId}`
- `At least one of content, name, tags, memos, or image_paths must be provided`
- `A prompt named "{name}" already exists at this level.` (sibling name collision)
- `Invalid image path "{imagePath}": {error}`
- Validation errors (`validateChunkName`)

---

## check_prompt

- **Purpose**: Set a single prompt to checked state
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |
| `prompt_id` | string | ✓ | Prompt ID |

**Request example**:

```json
{
  "query_type": "check_prompt",
  "params": {
    "category_name": "Quality",
    "prompt_id": "1776662469597-gefwo8qqf"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "prompt_id": "1776662469597-gefwo8qqf",
  "checked": true
}
```

**Errors**:
- `Category not found: {categoryName}`
- `Prompt not found: {promptId}`

---

## uncheck_prompt

- **Purpose**: Uncheck a single prompt
- **Parameters**: Same as `check_prompt`

**Request example**:

```json
{
  "query_type": "uncheck_prompt",
  "params": {
    "category_name": "Quality",
    "prompt_id": "1776662469597-gefwo8qqf"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "prompt_id": "1776662469597-gefwo8qqf",
  "checked": false
}
```

**Errors**: Same as `check_prompt`

---

## check_all

- **Purpose**: Check all prompts in a category
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |

**Request example**:

```json
{
  "query_type": "check_all",
  "params": { "category_name": "Quality" }
}
```

**Response example**:

```json
{
  "success": true,
  "category_name": "Quality",
  "checked": true,
  "count": 25
}
```

**Errors**:
- `Category not found: {categoryName}`

---

## uncheck_all

- **Purpose**: Uncheck all prompts in a category
- **Parameters**: Same as `check_all`

**Request example**:

```json
{
  "query_type": "uncheck_all",
  "params": { "category_name": "Quality" }
}
```

**Response example**:

```json
{
  "success": true,
  "category_name": "Quality",
  "checked": false,
  "count": 25
}
```

**Errors**: Same as `check_all`

---

## set_category_output

- **Purpose**: Toggle the category's generation output ON/OFF
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |
| `enabled` | boolean | ✓ | `true` to turn output ON, `false` for OFF |

**Request example**:

```json
{
  "query_type": "set_category_output",
  "params": {
    "category_name": "Quality",
    "enabled": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "category_name": "Quality",
  "output_enabled": true
}
```

**Errors**:
- `Category not found: {categoryName}`

---

## set_category_template

- **Purpose**: Update the category's template generation settings ([Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md))
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |
| `mode` | string | — | `"parts"` or `"standard"` |
| `target` | string | — | Target mode (e.g. `"allleaves"`, `"checked"`) |
| `filter` | string | — | Filter expression |
| `pick` | string | — | Pick strategy |
| `sort` | string | — | Sort order |
| `join` | string | — | Join separator |
| `edit` | string | — | Edit plugin |
| `template_directive` | string | — | Template directive |

**Request example**:

```json
{
  "query_type": "set_category_template",
  "params": {
    "category_name": "Quality",
    "target": "checked",
    "join": ", "
  }
}
```

**Response example**:

```json
{ "success": true, "category_name": "Quality" }
```

**Errors**:
- `Category not found: {categoryName}`
- `Invalid {field} value: ...` (when UI ComboBox sentinel headers or separators are passed)

---

## set_final_edit

- **Purpose**: Set the category's Final Edit plugin
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |
| `enabled` | boolean | — | Final Edit ON/OFF |
| `plugin_name` | string | — | Plugin name |

**Request example**:

```json
{
  "query_type": "set_final_edit",
  "params": {
    "category_name": "Quality",
    "enabled": true,
    "plugin_name": "myFinalEditPlugin"
  }
}
```

**Response example**:

```json
{ "success": true, "category_name": "Quality" }
```

**Errors**:
- `Category not found: {categoryName}`

---

## apply_check_preset

- **Purpose**: Apply a saved check preset (batch-restore check states and category output states)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `preset_id` | string | ✓ | ID from `list_check_presets` |

**Request example**:

```json
{
  "query_type": "apply_check_preset",
  "params": { "preset_id": "preset-001" }
}
```

**Response example**:

```json
{
  "success": true,
  "preset_name": "Anime Style",
  "checked_count": 15
}
```

If prompts have been deleted since the preset was saved, additional fields are included:

```json
{
  "success": true,
  "preset_name": "Anime Style",
  "checked_count": 12,
  "preset_stored_count": 15,
  "missing_count": 3
}
```

**Errors**:
- `Check preset not found: {presetId}`

---

## save_check_preset

- **Purpose**: Save the current check state and category output settings as a preset
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `name` | string | ✓ | Preset name (whitespace-only not allowed) |
| `description` | string | — | Description text |

**Request example**:

```json
{
  "query_type": "save_check_preset",
  "params": {
    "name": "My Quality Set",
    "description": "Best quality presets for high-res"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "preset_name": "My Quality Set",
  "checked_count": 17
}
```

**Errors**:
- `Preset name is required` (empty or whitespace-only)

---

## apply_favorite_list

- **Purpose**: Add all items in a favorite list to the current checks (union, not replacement)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `category_name` | string | ✓ | Category name |
| `list_id` | string | ✓ | ID from `list_favorite_lists` |

**Request example**:

```json
{
  "query_type": "apply_favorite_list",
  "params": {
    "category_name": "Quality",
    "list_id": "fav-001"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "list_name": "Best Quality",
  "applied_count": 5
}
```

**Errors**:
- `Category not found: {categoryName}`
- `Favorite list not found: {listId}`

---

## add_category

- **Purpose**: Add a new category
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `name` | string | ✓ | Category name |
| `parent_name` | string | — | Parent category name (omitted = directly under root) |

**Request example**:

```json
{
  "query_type": "add_category",
  "params": {
    "name": "MyNewCategory",
    "parent_name": "Quality"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "category_id": "cat-1776700000000",
  "name": "MyNewCategory",
  "parent_name": "Quality"
}
```

**Errors**:
- `Parent category not found: {parentName}` (when `parent_name` is specified)
- Name collision / validation errors

---

## Related

- [REST API Reference](01-REST%20API%20Reference.md)
- [REST API - Read Endpoints](02-REST%20API%20-%20Read%20Endpoints.md)
- [REST API - Delete Endpoints](04-REST%20API%20-%20Delete%20Endpoints.md)
- [Save Project](../../File/02-Menu/06-Save%20Project.md)
- [Tag](../../PromptBrowser/01-Basics/04-Tag.md)
- [Check Preset](../../AdvancedPanel/02-Glossary/02-Check%20Preset.md)
- [Favorite List](../../AdvancedPanel/02-Glossary/03-Favorite%20List.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Final Edit](../../AdvancedPanel/02-Glossary/05-Final%20Edit.md)
