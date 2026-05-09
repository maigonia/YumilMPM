# REST API - Instruction Endpoints

**REST API - Instruction Endpoints**

Endpoints for referencing instructions (in-app help) and retrieving generation history (6 endpoints).

> See [REST API Reference](01-REST API Reference.md) for common specifications (authentication / request format).

## Endpoint List

| query_type | Purpose |
|---|---|
| `list_instruction_types` | List instruction types (12 types) |
| `get_instruction_tree` | Get node hierarchy for a specified type |
| `get_instruction_content` | Get full content from a node ID |
| `search_instructions` | Full-text search of instructions |
| `list_history` | List of generation history |
| `get_history_entry` | Full content of a history entry |

---

## list_instruction_types

- **Purpose**: Get all 12 available instruction types
- **Parameters**: None

**Request example**:

```json
{ "query_type": "list_instruction_types", "params": {} }
```

**Response example**:

```json
[
  { "type": "file", "title": "File Operations" },
  { "type": "categoryTree", "title": "Category Tree" },
  { "type": "promptTree", "title": "Prompt Tree" },
  { "type": "promptEditor", "title": "Prompt Editor" },
  { "type": "promptBrowser", "title": "Prompt Browser" },
  { "type": "promptGeneration", "title": "Prompt Generation" },
  { "type": "advancedPanel", "title": "Advanced Panel" },
  { "type": "globalSettings", "title": "Global Settings" },
  { "type": "utility", "title": "Utility" },
  { "type": "instructionPortal", "title": "Instruction Portal" },
  { "type": "tutorial", "title": "Tutorial" },
  { "type": "faq", "title": "FAQ" }
]
```

**Errors**: None

---

## get_instruction_tree

- **Purpose**: Get the node hierarchy tree for a specified type
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `instruction_type` | string | ✓ | Type from `list_instruction_types` |

**Request example**:

```json
{
  "query_type": "get_instruction_tree",
  "params": { "instruction_type": "utility" }
}
```

**Response example**:

```json
{
  "type": "utility",
  "title": "Utility",
  "nodes": [
    {
      "id": "utility.menu",
      "label": "Menu Description",
      "has_content": false,
      "children": [
        {
          "id": "utility.menu.restApiReference",
          "label": "REST API Reference",
          "has_content": true
        },
        {
          "id": "utility.menu.aIAutoOperation",
          "label": "AI Auto-Operation",
          "has_content": true
        }
      ]
    }
  ]
}
```

**Errors**:
- `Instruction type not found: {instructionType}`

---

## get_instruction_content

- **Purpose**: Get full content (Markdown) from a node ID
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `node_id` | string | ✓ | ID from `get_instruction_tree` |

**Request example**:

```json
{
  "query_type": "get_instruction_content",
  "params": { "node_id": "utility.menu.restApiReference" }
}
```

**Response example**:

```json
{
  "node_id": "utility.menu.restApiReference",
  "label": "REST API Reference",
  "content": "# REST API Reference\n\n**REST API Reference**\n\nThis is the specification for this app's built-in HTTP API server...",
  "has_children": false,
  "instruction_type": "utility"
}
```

**Errors**:
- `Instruction type not found for node: {nodeId}\n\nDid you mean one of these?\n- {suggestions...}\n\nHint: use get_instruction_tree("<type>") to see all node IDs for a type.` (suggests similar IDs on typo)
- `Instruction node not found: {nodeId}\n\n...`

---

## search_instructions

- **Purpose**: Full-text search of instructions (supports both label and content)
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `query` | string | ✓ | — | Search term |
| `target` | string | — | `"label"` | `"label"` or `"content"` |
| `instruction_type` | string | — | — | Limit to single type |
| `use_regex` | boolean | — | `false` | Case-insensitive regex |
| `exclude` | boolean | — | `false` | NOT search |
| `limit` | number | — | `30` | Max items (limit 100) |
| `offset` | number | — | `0` | Pagination offset |
| `count_only` | boolean | — | `false` | Return only count |

**Request example**:

```json
{
  "query_type": "search_instructions",
  "params": {
    "query": "tag",
    "target": "label",
    "limit": 10
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
      "instruction_type": "promptEditor",
      "node_id": "promptEditor.menu.tagEditor",
      "label": "Tag Editor",
      "breadcrumb": "Prompt Editor > Menu Description > Tag Editor",
      "match_in": "label",
      "content_preview": "## When to Use\n- When you want to edit tags of prompts..."
    }
  ]
}
```

> Results are ranked by `match_in` order (`label` > `heading` > `body`).

**Errors**:
- `Invalid instruction_type: {instructionType}. Valid types: {list}`

---

## list_history

- **Purpose**: Get list of generation history
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `limit` | number | — | Return only top N entries (newest first) |

**Request example**:

```json
{
  "query_type": "list_history",
  "params": { "limit": 5 }
}
```

**Response example**:

```json
{
  "total_count": 42,
  "entries": [
    {
      "index": 0,
      "timestamp": "1729612345678",
      "generated_at": "2026-04-20T10:32:25.678Z",
      "category_names": ["Quality", "Style"],
      "result_count": 2,
      "prompt_lengths": [
        {
          "category_name": "Quality",
          "length": 35,
          "preview": "masterpiece, best quality, ultra detailed"
        },
        {
          "category_name": "Style",
          "length": 12,
          "preview": "anime style"
        }
      ]
    }
  ]
}
```

> `preview` is truncated to 100 characters. Use `get_history_entry` for full text.

**Errors**: None

---

## get_history_entry

- **Purpose**: Get the full prompt text of a history entry
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `index` | number | ✓ | Index from `list_history` |
| `category_name` | string | — | Get only results for a single category |

**Request example (all categories)**:

```json
{
  "query_type": "get_history_entry",
  "params": { "index": 0 }
}
```

**Response example (all categories)**:

```json
{
  "index": 0,
  "timestamp": "1729612345678",
  "generated_at": "2026-04-20T10:32:25.678Z",
  "results": [
    { "category_name": "Quality", "prompt": "masterpiece, best quality, ultra detailed" },
    { "category_name": "Style", "prompt": "anime style" }
  ]
}
```

**Request example (single category)**:

```json
{
  "query_type": "get_history_entry",
  "params": { "index": 0, "category_name": "Quality" }
}
```

**Response example (single category)**:

```json
{
  "index": 0,
  "timestamp": "1729612345678",
  "generated_at": "2026-04-20T10:32:25.678Z",
  "category_name": "Quality",
  "prompt": "masterpiece, best quality, ultra detailed"
}
```

**Errors**:
- `History index out of range: {index}. Valid range: 0-{max} ({total} entries available)`
- `Category "{categoryName}" not found in history entry {index}. Available categories: {list}.` (when `category_name` is specified)

---

## Tips

### Importing Instructions into External Tools

Example of importing this app's full help into external tools (Slack bot / custom LLM helper tool, etc.):

```javascript
// 1. Get all types
const types = await api({ query_type: "list_instruction_types", params: {} });

// 2. Recursively get tree for each type
async function fetchAll(type) {
  const tree = await api({ query_type: "get_instruction_tree", params: { instruction_type: type } });
  const contents = [];
  async function walk(nodes) {
    for (const node of nodes) {
      if (node.has_content) {
        const c = await api({ query_type: "get_instruction_content", params: { node_id: node.id } });
        contents.push({ id: node.id, label: c.label, content: c.content });
      }
      if (node.children) await walk(node.children);
    }
  }
  await walk(tree.nodes);
  return contents;
}

const allDocs = [];
for (const t of types) {
  allDocs.push(...await fetchAll(t.type));
}
```

### Did-you-mean Suggestion Feature

`get_instruction_content` suggests similar IDs by Levenshtein distance when you specify an incorrect node_id. Don't give up on typos — try the displayed suggestions.

## Related

- [REST API Reference](01-REST API Reference.md)
- [REST API - Read Endpoints](02-REST API - Read Endpoints.md)
- [Instruction Portal](../../InstructionPortal/01-Table of Contents/01-Instruction Index.md)
- [FAQ](../../FAQ/01-Unresolved Issues/README.md)
- [History](../../PromptGeneration/04-Menu/17-Set Max History Entries.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
