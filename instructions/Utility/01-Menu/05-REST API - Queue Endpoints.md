# REST API - Queue Endpoints

**REST API - Queue Endpoints**

Endpoints for [Queue Pattern](../../PromptGeneration/04-Menu/05-Generation%20Queue/README.md) (queue pattern) operations (8 endpoints). Manages 3 types of patterns: Standard / Sequential / Loop.

> See [REST API Reference](01-REST%20API%20Reference.md) for common specifications (authentication / request format).

## Endpoint List

| query_type | Purpose |
|---|---|
| `list_queue_patterns` | List all queue patterns |
| `get_queue_pattern` | Single queue pattern details (with queue_items) |
| `create_queue_pattern` | Create a new queue pattern |
| `add_queue_item` | Add an item to a sequential/loop pattern |
| `remove_queue_item` | Remove a queue item by index |
| `select_queue_pattern` | Select pattern to use for generation |
| `reset_queue_pattern` | Reset pattern to initial state |
| `delete_queue_pattern` | Delete a pattern |

## 3 Pattern Types

| Type | Characteristics |
|---|---|
| `standard` | Holds a single snapshot of the current state at creation. Items cannot be appended later |
| `sequential` | Executes multiple items in order (top→bottom or bottom→top) |
| `loop` | Executes multiple items in a loop (specify count, optional reset per loop, shuffle) |

---

## list_queue_patterns

- **Purpose**: Get list of all queue patterns
- **Parameters**: None

**Request example**:

```json
{ "query_type": "list_queue_patterns", "params": {} }
```

**Response example**:

```json
[
  {
    "id": "pat-001",
    "name": "Standard 1",
    "type": "standard",
    "status": "idle",
    "progress": {},
    "queue_item_count": 1,
    "can_edit": false,
    "created_at": "2026-04-12T10:00:00.000Z",
    "last_executed_at": null,
    "is_selected": true
  },
  {
    "id": "pat-002",
    "name": "My Loop",
    "type": "loop",
    "status": "idle",
    "progress": {},
    "queue_item_count": 5,
    "can_edit": true,
    "created_at": "2026-04-12T11:00:00.000Z",
    "last_executed_at": "2026-04-15T14:30:00.000Z",
    "is_selected": false
  }
]
```

**Errors**: None

---

## get_queue_pattern

- **Purpose**: Get details of a single queue pattern (including queue_items array)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | ✓ | ID from `list_queue_patterns` |

**Request example**:

```json
{
  "query_type": "get_queue_pattern",
  "params": { "pattern_id": "pat-002" }
}
```

**Response example**:

```json
{
  "id": "pat-002",
  "name": "My Loop",
  "type": "loop",
  "status": "idle",
  "progress": {},
  "can_edit": true,
  "created_at": "2026-04-12T11:00:00.000Z",
  "last_executed_at": "2026-04-15T14:30:00.000Z",
  "is_selected": false,
  "queue_items": [
    {
      "index": 0,
      "id": "item-001",
      "name": "Variant A",
      "status": "completed",
      "category_count": 8,
      "created_at": "2026-04-12T11:01:00.000Z",
      "has_results": true
    }
  ]
}
```

**Errors**:
- `Queue pattern not found: {patternId}`

---

## create_queue_pattern

- **Purpose**: Create a new queue pattern
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `pattern_type` | string | ✓ | — | `"standard"` / `"sequential"` / `"loop"` |
| `name` | string | — | auto-generated | Display name |
| `sequential_settings` | object | — | — | Sequential-only settings |
| `sequential_settings.execution_order` | string | — | — | `"topToBottom"` or `"bottomToTop"` |
| `loop_settings` | object | — | — | Loop-only settings |
| `loop_settings.loop_count` | number | — | `1` | Number of loops |
| `loop_settings.reset_to_first_after_loop` | boolean | — | `true` | Reset index after loop |
| `loop_settings.shuffle_each_loop` | boolean | — | `false` | Shuffle each loop |

**Request example**:

```json
{
  "query_type": "create_queue_pattern",
  "params": {
    "pattern_type": "loop",
    "name": "Variations",
    "loop_settings": {
      "loop_count": 5,
      "shuffle_each_loop": true
    }
  }
}
```

**Response example**:

```json
{
  "success": true,
  "pattern_id": "pat-003",
  "name": "Variations",
  "type": "loop"
}
```

> Newly created patterns are auto-selected (common behavior across all 3 types).

**Errors**:
- `Invalid pattern_type: {patternType}. Must be 'standard', 'sequential', or 'loop'`

---

## add_queue_item

- **Purpose**: Add a snapshot of the current state as an item to a sequential / loop pattern
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | ✓ | Pattern ID |
| `item_name` | string | — | Item display name |

> Cannot add to standard patterns (returns `Pattern type 'standard' does not support add_queue_item ...` error).

**Request example**:

```json
{
  "query_type": "add_queue_item",
  "params": {
    "pattern_id": "pat-002",
    "item_name": "Variant B"
  }
}
```

**Response example**:

```json
{
  "success": true,
  "pattern_id": "pat-002",
  "item_count": 6
}
```

**Errors**:
- `Queue pattern not found: {patternId}`
- `Pattern type '{type}' does not support add_queue_item. Only 'sequential' and 'loop' patterns accept items; 'standard' patterns take a single snapshot at creation time and cannot be appended to. Create a sequential or loop pattern via create_queue_pattern if you need multiple items.`

---

## remove_queue_item

- **Purpose**: Remove an item by index
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | ✓ | Pattern ID |
| `item_index` | number | ✓ | 0-based index in `queue_items` |

**Request example**:

```json
{
  "query_type": "remove_queue_item",
  "params": {
    "pattern_id": "pat-002",
    "item_index": 2
  }
}
```

**Response example**:

```json
{
  "success": true,
  "pattern_id": "pat-002",
  "item_count": 5
}
```

**Errors**:
- `Queue pattern not found: {patternId}`
- `This pattern type does not support removing queue items` (standard pattern)
- `Invalid item_index: {itemIndex}. Must be 0-{max}`

---

## select_queue_pattern

- **Purpose**: Select the pattern to use for generation (or deselect)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | — | Pattern ID. Omit or pass `null` to deselect |

**Request example (select)**:

```json
{
  "query_type": "select_queue_pattern",
  "params": { "pattern_id": "pat-002" }
}
```

**Request example (deselect)**:

```json
{
  "query_type": "select_queue_pattern",
  "params": { "pattern_id": null }
}
```

**Response example**:

```json
{
  "success": true,
  "selected_pattern_id": "pat-002"
}
```

**Errors**:
- `pattern_id must not be an empty string. Omit the field or pass null to deselect, or pass a valid pattern ID from list_queue_patterns.`
- `Queue pattern not found: {patternId}. Use list_queue_patterns to see available patterns (note: pattern_id expects the ID, not the display name).`

---

## reset_queue_pattern

- **Purpose**: Reset a pattern to initial state (status / progress reinitialized)
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | ✓ | Pattern ID |

**Request example**:

```json
{
  "query_type": "reset_queue_pattern",
  "params": { "pattern_id": "pat-002" }
}
```

**Response example**:

```json
{
  "success": true,
  "pattern_id": "pat-002"
}
```

**Errors**:
- `Queue pattern not found: {patternId}`

---

## delete_queue_pattern

- **Purpose**: Delete a pattern
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `pattern_id` | string | ✓ | Pattern ID |

**Request example**:

```json
{
  "query_type": "delete_queue_pattern",
  "params": { "pattern_id": "pat-002" }
}
```

**Response example**:

```json
{
  "success": true,
  "pattern_id": "pat-002"
}
```

> If the deleted pattern was selected, it is automatically deselected.

**Errors**:
- `Queue pattern not found: {patternId}`

---

## Tips

### Typical Loop Pattern Creation Flow

```javascript
// 1. Create a Loop pattern
const { pattern_id } = await api({
  query_type: "create_queue_pattern",
  params: {
    pattern_type: "loop",
    name: "Daily Variations",
    loop_settings: { loop_count: 10, shuffle_each_loop: true }
  }
});

// 2. Add item with current check state
await api({
  query_type: "add_queue_item",
  params: { pattern_id, item_name: "Set A" }
});

// 3. Change check state
await api({ query_type: "uncheck_all", params: { category_name: "X" } });
await api({ query_type: "check_prompt", params: { ... } });

// 4. Add another item
await api({
  query_type: "add_queue_item",
  params: { pattern_id, item_name: "Set B" }
});

// 5. Select pattern (usually unnecessary since auto-selected at creation)
await api({
  query_type: "select_queue_pattern",
  params: { pattern_id }
});
```

### Standard vs Sequential/Loop Differences

- **Standard**: Saves only one snapshot of "the current check state". Cannot be modified later
- **Sequential / Loop**: Holds multiple snapshots, executed sequentially / repeatedly
- All restore check state from snapshots at generation time

## Related

- [REST API Reference](01-REST%20API%20Reference.md)
- [REST API - Generation Endpoints](06-REST%20API%20-%20Generation%20Endpoints.md)
- [Queue Pattern](../../PromptGeneration/04-Menu/05-Generation%20Queue/README.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Standard Pattern](../../PromptGeneration/04-Menu/05-Generation%20Queue/01-Add%20Standard%20Pattern.md)
- [Sequential Pattern](../../PromptGeneration/04-Menu/05-Generation%20Queue/02-Add%20Sequential%20Pattern.md)
- [Loop Pattern](../../PromptGeneration/04-Menu/05-Generation%20Queue/03-Add%20Loop%20Pattern.md)
