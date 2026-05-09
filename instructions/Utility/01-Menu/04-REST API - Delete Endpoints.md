# REST API - Delete Endpoints

**REST API - Delete Endpoints**

Endpoints for deleting prompts, categories, tags, presets, etc. (5 endpoints). All support the `dry_run` option to preview "what will be deleted" beforehand.

> See [REST API Reference](01-REST%20API%20Reference.md) for common specifications (authentication / request format).

## Endpoint List

| query_type | Purpose | dry_run support |
|---|---|:-:|
| `delete_prompt` | Delete a prompt | ✓ |
| `delete_category` | Delete a category (always cascade) | ✓ |
| `delete_check_preset` | Delete a check preset | — |
| `delete_tag` | Delete a tag | ✓ |
| `bulk_delete_prompts` | Bulk delete multiple prompts | ✓ |

> **Persistence note**: Delete operations are in-memory only and not reflected in files until [Save Project](../../File/02-Menu/06-Save%20Project.md) is performed.

---

## delete_prompt

- **Purpose**: Delete a prompt (optionally including descendants)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `prompt_id` | string | ✓ | — | Prompt ID |
| `cascade` | boolean | — | `false` | `true` to also delete descendants; `false` rejects deletion if descendants exist |
| `dry_run` | boolean | — | `false` | `true` returns deletion targets without actually deleting |

**Request example (dry_run)**:

```json
{
  "query_type": "delete_prompt",
  "params": {
    "category_name": "Quality",
    "prompt_id": "1776662469597-gefwo8qqf",
    "cascade": true,
    "dry_run": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "dry_run": true,
  "prompt_id": "1776662469597-gefwo8qqf",
  "prompt_name": "Common",
  "deleted_count": 12,
  "descendant_names": [
    "masterpiece",
    "best_quality",
    "high_resolution"
  ]
}
```

`descendant_names` includes up to 20 entries.

**Errors**:
- `Category not found: {categoryName}`
- `Prompt not found: {promptId}`
- `Prompt "{name}" has {count} descendants: [names...]. Set cascade=true to delete all, or delete descendants individually first.` (when descendants exist with `cascade=false`)

---

## delete_category

- **Purpose**: Delete a category (always cascades to child categories and child prompts)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `name` | string | ✓ | — | Category name |
| `cascade` | boolean | — | `false` | Must always be `true` (deletion is always cascade, but required for explicit confirmation) |
| `dry_run` | boolean | — | `false` | `true` returns deletion targets without deleting |

> **Important**: Parameter is `name` (different from other delete endpoints which use `category_name`).

**Request example (dry_run)**:

```json
{
  "query_type": "delete_category",
  "params": {
    "name": "OldStuff",
    "cascade": true,
    "dry_run": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "dry_run": true,
  "name": "OldStuff",
  "output_enabled": true,
  "deleted_prompt_count": 87,
  "deleted_category_count": 4,
  "descendant_category_names": [
    "OldStuff/Subcat1",
    "OldStuff/Subcat2",
    "OldStuff/Subcat3"
  ]
}
```

**Errors**:
- `Category not found: {name}`
- `Category "{name}" contains {totalPromptCount} prompts and {descendantCategories.length} child categories. Deletion is always cascading. Set cascade=true to proceed. Inform the user about the exact count first.` (`cascade != true`)

---

## delete_check_preset

- **Purpose**: Delete a saved check preset
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `preset_id` | string | ✓ | ID from `list_check_presets` |

**Request example**:

```json
{
  "query_type": "delete_check_preset",
  "params": { "preset_id": "preset-001" }
}
```

**Response example**:

```json
{
  "success": true,
  "preset_id": "preset-001",
  "preset_name": "Anime Style"
}
```

**Errors**:
- `Check preset not found: {presetId}`

---

## delete_tag

- **Purpose**: Delete a global tag (optionally auto-removing from all prompts)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `tag_name` | string | ✓ | — | Tag name |
| `cascade` | boolean | — | `false` | `true` to remove from all prompts then delete; `false` rejects deletion if in use |
| `dry_run` | boolean | — | `false` | `true` returns change targets without modifying |

**Request example (dry_run)**:

```json
{
  "query_type": "delete_tag",
  "params": {
    "tag_name": "obsolete",
    "cascade": true,
    "dry_run": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "dry_run": true,
  "tag_name": "obsolete",
  "removed_from_prompts": 12
}
```

**Errors**:
- `Tag not found: {tagName}`
- `Tag "{tagName}" is protected and cannot be deleted.` (system tag)
- `Tag "{tagName}" is in use (usage_count: {count}). Set cascade=true to remove from all prompts first.` (in use with `cascade=false`)

---

## bulk_delete_prompts

- **Purpose**: Bulk-delete multiple prompts in a single request
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name (all prompts in same category) |
| `prompt_ids` | string[] | ✓ | — | Non-empty array of prompt IDs |
| `cascade` | boolean | — | `false` | `true` to also delete descendants |
| `dry_run` | boolean | — | `false` | `true` returns deletion targets without deleting |

**Request example (dry_run)**:

```json
{
  "query_type": "bulk_delete_prompts",
  "params": {
    "category_name": "Quality",
    "prompt_ids": ["id-1", "id-2", "id-3"],
    "cascade": true,
    "dry_run": true
  }
}
```

**Response example**:

```json
{
  "success": true,
  "dry_run": true,
  "deleted_prompt_count": 8,
  "deleted_prompts": [
    { "prompt_id": "id-1", "name": "old_a", "descendant_count": 3 },
    { "prompt_id": "id-2", "name": "old_b", "descendant_count": 0 },
    { "prompt_id": "id-3", "name": "old_c", "descendant_count": 2 }
  ]
}
```

**Errors**:
- `Category not found: {categoryName}`
- `prompt_ids must be a non-empty array`
- `Prompt "{promptId}" not found in category "{categoryName}". bulk_delete_prompts requires all prompts in the same category.`
- `Some prompts have descendants: "name1" (count), .... Set cascade=true to delete all, or delete descendants individually first.`

---

## Tips

### Preflight Check with dry_run

Always recommended to confirm destructive operations with `dry_run: true` first.

```javascript
// 1. Confirm deletion targets with dry_run
const preview = await api({
  query_type: "delete_category",
  params: { name: "OldStuff", cascade: true, dry_run: true }
});

console.log(`Prompts to delete: ${preview.deleted_prompt_count}`);
console.log(`Subcategories to delete: ${preview.deleted_category_count - 1}`);

// 2. Execute after user confirmation
if (await confirm()) {
  await api({
    query_type: "delete_category",
    params: { name: "OldStuff", cascade: true }
  });
}
```

### Relationship to Tag Auto-Deletion

When tags are removed via `edit_prompt` and `usage_count` becomes 0, unprotected tags are auto-deleted. You only need to explicitly call `delete_tag` when:

- You want to force-delete a tag in use (`cascade=true`)
- You want to delete a protected tag (actually impossible)

## Related

- [REST API Reference](01-REST%20API%20Reference.md)
- [REST API - Read Endpoints](02-REST%20API%20-%20Read%20Endpoints.md)
- [REST API - Write Endpoints](03-REST%20API%20-%20Write%20Endpoints.md)
- [Save Project](../../File/02-Menu/06-Save%20Project.md)
- [Tag](../../PromptBrowser/01-Basics/04-Tag.md)
- [Check Preset](../../AdvancedPanel/02-Glossary/02-Check%20Preset.md)
