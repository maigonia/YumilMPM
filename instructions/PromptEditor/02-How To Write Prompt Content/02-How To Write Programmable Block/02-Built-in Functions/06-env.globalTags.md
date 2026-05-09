# env.globalTags

**Array of all global tag names**

## Overview

`env.globalTags` returns an array of all global tag names defined in the project.

## Type

```javascript
env.globalTags  // string[]
```

## Usage Examples

### Basic Retrieval

```javascript
@@@_
const tags = env.globalTags;
env.OUTPUT(tags.join(", "));
_@@@
```

> Output example: `character, background, style, quality, fantasy`

### Check Tag Count

```javascript
@@@_
const tags = env.globalTags;
env.OUTPUT("Registered tags: " + tags.length);
_@@@
```

### Check Tag Existence

```javascript
@@@_
const targetTag = "fantasy";
if (env.globalTags.includes(targetTag)) {
  env.OUTPUT("Tag is valid");
} else {
  env.OUTPUT("Tag not found");
}
_@@@
```

### Filter by Pattern

```javascript
@@@_
// Extract tags with a specific prefix
const styleTags = env.globalTags.filter(t => t.startsWith("style_"));
env.OUTPUT(styleTags.join(", "));
_@@@
```

### Validate Chunk Tags

Checks whether tags assigned to a chunk exist in global tags.

```javascript
@@@_
const chunkTags = env.chunk?.tags || [];
const globalTags = env.globalTags;

const validTags = chunkTags.filter(t => globalTags.includes(t));
const invalidTags = chunkTags.filter(t => !globalTags.includes(t));

if (invalidTags.length > 0) {
  env.OUTPUT("Invalid tags: " + invalidTags.join(", "));
} else {
  env.OUTPUT("All tags valid: " + validTags.join(", "));
}
_@@@
```

### Numbered Tag List

```javascript
@@@_
const tags = env.globalTags;
const list = tags.map((t, i) => \`\${i + 1}. \${t}\`).join("\n");
env.OUTPUT(list);
_@@@
```

> Output example:
```
1. character
2. background
3. style
```

## env.tagDefinitions

When you need detailed information beyond just names, such as descriptions and usage counts, use `env.tagDefinitions`.

### Type

```javascript
env.tagDefinitions  // object[]
```

### tagDefinitions Object

| Property | Type | Description |
|----------|------|-------------|
| `name` | string | Tag name |
| `description` | string? | Tag description (absent if not set) |
| `usageCount` | number | Usage count across the entire project |
| `protected` | boolean | Protection status |

### Usage Examples

```javascript
@@@_
// List tag names with descriptions
const defs = env.tagDefinitions;
const list = defs.map(t =>
  t.description ? t.name + " - " + t.description : t.name
);
env.OUTPUT(list.join("\n"));
_@@@
```

```javascript
@@@_
// Show tags sorted by usage count
const sorted = env.tagDefinitions
  .slice()
  .sort((a, b) => b.usageCount - a.usageCount);
env.OUTPUT(sorted.map(t => t.name + " (" + t.usageCount + ")").join(", "));
_@@@
```

### Scoped tagDefinitions

`env.tagDefinitions` returns all project tags. You can also get scoped definitions for chunks and categories.

| Scope | Access | Content |
|-------|--------|---------|
| Global | `env.tagDefinitions` | All tags |
| Category | `env.getCategory("X").tagDefinitions` | Tags used in that category only |
| Chunk | `env.chunk.tagDefinitions` | Tags assigned to that chunk only |

Category and chunk `tagDefinitions` are lazy-loaded — no cost when not accessed.

## Notes

- `env.globalTags` / `env.tagDefinitions` are read-only properties (`await` not needed)
- `env.globalTags` contains names only (string[]), `env.tagDefinitions` includes detailed info (object[])
- For individual chunk tags, use [env.chunk](01-env.chunk.md).tags or [env.chunk](01-env.chunk.md).tagDefinitions
- Global tags are managed in [Tag Manager](../../../../GlobalSettings/04-Menu/06-Tag%20Manager.md)

## Related

- [Programmable Block](../README.md)
- [Tag](../../../../PromptBrowser/01-Basics/04-Tag.md)
- [Tag Manager](../../../../GlobalSettings/04-Menu/06-Tag%20Manager.md)
- [env.chunk](01-env.chunk.md)
- [env.getCategory](04-env.getCategory.md)
