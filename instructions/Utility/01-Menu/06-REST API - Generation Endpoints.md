# REST API - Generation Endpoints

**REST API - Generation Endpoints**

Generation-related read-system endpoints for retrieving category structure, evaluating CI expressions, generation preview, etc. (4 endpoints).

> See [REST API Reference](01-REST%20API%20Reference.md) for common specifications (authentication / request format).
>
> Actual generation is performed via a separate endpoint `POST /api/v1/generate` (see "Complete Request/Response Examples" in [REST API Reference](01-REST%20API%20Reference.md)).

## Endpoint List

| query_type | Purpose |
|---|---|
| `get_classification_outline` | Get the classification skeleton (folder/group only) of all categories in a single request |
| `get_category_structure` | Get hierarchical tree structure of a category |
| `evaluate_ci` | Evaluate a CI expression standalone (no actual generation) |
| `preview_generation` | Generation preview (not recorded in history) |

---

## get_classification_outline

- **Purpose**: Get the classification skeleton of all categories (folder/group nodes only) as indented text in a single request. Ideal as the first step when handling vague search requests, to identify which areas to drill into
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `output_enabled_only` | boolean | — | `false` | Restrict to output-enabled categories only |
| `max_depth` | number | — | unlimited | Maximum depth to walk (`0` = top-level categories only) |
| `include_ids` | boolean | — | `false` | Append `[id]` to each line |
| `category_names` | string[] | — | all categories | Restrict to specific category names |

**Request example**:

```json
{
  "query_type": "get_classification_outline",
  "params": { "max_depth": 2, "include_ids": false }
}
```

**Response example**:

```json
{
  "outline": "PositivePrompt (84)\n  i2i (43)\n  Regional Prompt (21)\nBackgrounds (34)\n  Genres (5)\n    Common (5)\n  Places (29)\nEtc (6)\n  Accessories (6)"
}
```

When `include_ids: true` is specified, each line gets a trailing `[uuid]`:

```
Backgrounds (34) [cat-id-001]
  Genres (5) [folder-id-002]
```

> **Count semantics**: The `(N)` on each node is the total descendant count of **normal prompts + file prompts** (folder/group nodes themselves are excluded). This differs from `list_categories`'s `prompt_count` which includes folder nodes
>
> **Excluded items**: Normal prompts and file prompts are not included in the output. Use `list_prompts` / `get_category_structure` if those are needed

**Errors**: None (returns `outline: ""` if no categories match)

> **When to use**: Sits between `list_categories` (top-level only) and `get_category_structure` (single category detail). For a 1,800-prompt project, calling `get_category_structure` per category becomes N+1 round-trips, but this endpoint completes in 1 request

---

## get_category_structure

- **Purpose**: Get prompts within a category as a hierarchical tree
- **Parameters**:

| Name | Type | Required | Default | Description |
|---|---|---|---|---|
| `category_name` | string | ✓ | — | Category name |
| `include_ids` | boolean | — | `true` | Include prompt IDs in response |

**Request example**:

```json
{
  "query_type": "get_category_structure",
  "params": {
    "category_name": "Quality",
    "include_ids": true
  }
}
```

**Response example**:

```json
{
  "category_name": "Quality",
  "total_prompt_count": 25,
  "structure": [
    {
      "name": "Common",
      "id": "1776662469597-aaaaaaaaa",
      "prompt_count": 12,
      "children": [
        {
          "name": "Basic",
          "id": "1776662469597-bbbbbbbbb",
          "prompt_count": 5
        }
      ]
    },
    {
      "name": "Advanced",
      "id": "1776662469597-ccccccccc",
      "prompt_count": 13
    }
  ]
}
```

> **Note**: `structure` only includes nodes that have children. Leaf nodes are counted in `prompt_count` but do not appear in the array. If you need full leaf-node info, use `list_prompts`.

**Errors**:
- `Category not found: {categoryName}`

---

## evaluate_ci

- **Purpose**: Evaluate a CI (Conditional Instruction / Category Identifier) expression standalone. Returns only the result string without actually generating
- **Parameters**:

| Name | Type | Required | Description |
|---|---|---|---|
| `expression` | string | ✓ | CI expression (do not wrap with `@@@_..._@@@`) |

**Request example**:

```json
{
  "query_type": "evaluate_ci",
  "params": {
    "expression": "Quality.Target(allLeaves).Pick(random=2)"
  }
}
```

**Response example**:

```json
{
  "expression": "Quality.Target(allLeaves).Pick(random=2)",
  "result": "masterpiece, best quality"
}
```

When Programmable Block errors occur:

```json
{
  "expression": "MyCategory",
  "result": "...",
  "programmable_errors": [
    "SIMILARITY: Vectors cannot be empty"
  ]
}
```

**Errors**:
- `CI expression must not be wrapped with @@@_..._@@@. Pass the bare expression, e.g. "Quality.Target(allLeaves).Pick(random=2)". The @@@_..._@@@ syntax is only for simple template substitution in prompt bodies.`

> **Important**: Pass the CI expression **without wrapping in `@@@_..._@@@`**. See [CI Expression](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) for details.

---

## preview_generation

- **Purpose**: Execute generation with current project state and return only the results (not recorded in history)
- **Parameters**: None

**Request example**:

```json
{ "query_type": "preview_generation", "params": {} }
```

**Response example**:

```json
[
  {
    "category_name": "Quality",
    "prompt": "masterpiece, best quality",
    "success": true,
    "error_message": null
  },
  {
    "category_name": "Style",
    "prompt": "anime style",
    "success": true,
    "error_message": null,
    "programmable_errors": [
      "SIMILARITY: Cannot compute similarity for zero vector"
    ]
  }
]
```

**Errors**: None (per-category errors are included in the result array)

> **Note**: `preview_generation` is not recorded in history. For production generation, use `POST /api/v1/generate`.

---

## Tips

### Typical CI Expression Debug Flow

```javascript
// Iteratively develop CI expressions
const result = await api({
  query_type: "evaluate_ci",
  params: { expression: "Quality.Target(checked).Pick(random=3).Join(\", \")" }
});

console.log("Result:", result.result);
if (result.programmable_errors) {
  console.error("PB errors:", result.programmable_errors);
}
```

### preview vs generate

| Comparison | `preview_generation` | `POST /api/v1/generate` |
|---|---|---|
| Records history | No | Yes |
| Saves results | No | Yes |
| Executes Programmable Block | Yes | Yes |
| Writes files | No | Per settings |
| Notifies Result Window | No | Yes |

Use `preview_generation` for development/debugging and `/generate` for production.

### Handling Programmable Block Errors

When `programmable_errors` is included in the `evaluate_ci` / `preview_generation` response, a Programmable Block ([Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)) built-in (`env.SIMILARITY` / `env.LMEDIT` / `env.CI`, etc.) failed due to invalid input or an internal error. Generation itself continues, but it's a sign of unintended behavior. Each error message is prefixed with the prompt location in `[CategoryName/PromptPath]` form.

The `SIMILARITY` function returns `NaN` and pushes a message to `programmable_errors` on invalid input. Inside PB code, detect it with `isNaN()` (the NaN value itself is not included in the final output — it is only used for comparisons or branching inside the PB).

## Related

- [REST API Reference](01-REST%20API%20Reference.md)
- [REST API - Read Endpoints](02-REST%20API%20-%20Read%20Endpoints.md)
- [REST API - Queue Endpoints](05-REST%20API%20-%20Queue%20Endpoints.md)
- [CI Expression](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Target](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/01-Target.md)
- [Pick](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/03-Pick.md)
- [Filter](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md)
