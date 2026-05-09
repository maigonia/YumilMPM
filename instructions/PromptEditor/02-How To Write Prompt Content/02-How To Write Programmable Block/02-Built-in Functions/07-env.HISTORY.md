# env.HISTORY

**Function to retrieve prompts from history**

## Syntax

```javascript
env.HISTORY(index)
env.HISTORY(index, categoryName)
```

| Argument | Type | Description |
|----------|------|-------------|
| `index` | number | History index (0 = most recent, 1 = second most recent...) |
| `categoryName` | string | Category name (optional) |

**Return value**: `string | undefined`

## How History Works

- Retains up to maximum count (oldest entries auto-deleted)
- **Saved to file on project save**
- Only records successfully generated prompts

## Behavior With/Without Category

### With Category Specified

Returns only the prompts for the specified category.

```javascript
@@@_
const lastChar = env.HISTORY(0, "Character");
if (lastChar) {
  env.OUTPUT(lastChar);
}
_@@@
```

### Without Category

Results from all categories are combined in the following format:

```
=== Character ===
character prompt here

---

=== Background ===
background prompt here
```

```javascript
@@@_
const lastAll = env.HISTORY(0);
env.OUTPUT(lastAll || "No history");
_@@@
```

## Usage Examples

### Compare Previous and Current

```javascript
@@@_
const current = await env.CI("Character");
const previous = env.HISTORY(0, "Character");

if (previous && current !== previous) {
  env.OUTPUT("[Changed]\n" + current);
} else {
  env.OUTPUT(current);
}
_@@@
```

### Get Last 3 Entries

```javascript
@@@_
const results = [];
for (let i = 0; i < 3; i++) {
  const h = env.HISTORY(i, "Character");
  if (h) results.push(\`[\${i}] \${h.substring(0, 50)}...\`);
}
env.OUTPUT(results.join("\n"));
_@@@
```

## Cases Where undefined Is Returned

- Index is out of range (less than 0 or greater than/equal to history count)
- The specified category does not exist in that entry
- The history entry has no results

## Notes

- Synchronous function (`await` not needed)
- History is persisted to file only on project save
- Storage location: `{DataFolder}/Prompts/history/prompt_history.json`

## Related

- [Programmable Block](../README.md)
- [Generation](../../../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Generation Queue](../../../../PromptGeneration/04-Menu/05-Generation%20Queue/README.md)
- [Once Generation](../../../../PromptGeneration/04-Menu/01-Once%20Generation.md)
