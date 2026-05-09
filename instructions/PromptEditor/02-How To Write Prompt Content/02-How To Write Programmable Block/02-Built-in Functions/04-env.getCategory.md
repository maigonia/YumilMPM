# env.getCategory

**Function to get category information**

## Syntax

```javascript
env.getCategory(name)
```

| Argument | Type | Description |
|----------|------|-------------|
| `name` | string | Category name |

**Return value**: `CategoryInfo | undefined`

## CategoryInfo Object

| Property | Type | Description |
|----------|------|-------------|
| `name` | string | Category name |
| `allChunks` | ChunkInfo[] | All chunks in the category (flat array) |
| `tags` | string[] | Tag names used in this category (deduplicated, sorted) |
| `tagDefinitions` | object[] | Tag definition objects for this category's tags (lazy-loaded) |
| `promptCount` | number | Total chunk count |
| `checkedCount` | number | Checked chunk count |
| `parent` | CategoryInfo | Parent category |
| `children` | CategoryInfo[] | Child category array |

### tagDefinitions Object

| Property | Type | Description |
|----------|------|-------------|
| `name` | string | Tag name |
| `description` | string? | Tag description (absent if not set) |
| `usageCount` | number | Usage count across the entire project |
| `protected` | boolean | Protection status |

## Usage Examples

### Basic Retrieval

```javascript
@@@_
const cat = env.getCategory("Character");
if (cat) {
  env.OUTPUT(\`Category: \${cat.name}\`);
}
_@@@
```

### List All Chunks

```javascript
@@@_
const cat = env.getCategory("Character");
if (cat) {
  const names = cat.allChunks.map(c => c.name);
  env.OUTPUT(names.join(", "));
}
_@@@
```

### Get Chunk Content

```javascript
@@@_
const settings = env.getCategory("Settings");
if (settings && settings.allChunks.length > 0) {
  env.OUTPUT(settings.allChunks[0].content);
}
_@@@
```

### Category Tags

```javascript
@@@_
const cat = env.getCategory("Character1");
if (cat) {
  env.OUTPUT(\`Tags: \${cat.tags.join(", ")}\`);
}
_@@@
```

### Using Tag Descriptions

```javascript
@@@_
const cat = env.getCategory("Character1");
if (cat) {
  const info = cat.tagDefinitions.map(t =>
    t.description ? t.name + " (" + t.description + ")" : t.name
  );
  env.OUTPUT(info.join(", "));
}
_@@@
```

### Reference Parent Category

```javascript
@@@_
const cat = env.getCategory("SubCategory");
const parentName = cat?.parent?.name || "None";
env.OUTPUT(\`Parent: \${parentName}\`);
_@@@
```

### List Child Categories

```javascript
@@@_
const cat = env.getCategory("Character");
const children = cat?.children || [];
const names = children.map(c => c.name);
env.OUTPUT(names.join(", "));
_@@@
```

### Build Category Path

```javascript
@@@_
function getCategoryPath(category) {
  const path = [];
  let current = category;
  while (current) {
    path.unshift(current.name);
    current = current.parent;
  }
  return path.join(" > ");
}

const cat = env.getCategory("LeafCategory");
env.OUTPUT(getCategoryPath(cat));
_@@@
```

> Output example: `Root > Middle > LeafCategory`

## Notes

- Returns `undefined` if a non-existent category name is specified
- Each chunk in `allChunks` is the same `ChunkInfo` type as [env.chunk](01-env.chunk.md)
- `parent` / `children` can be accessed recursively
- `tags` contains only tag names used in direct chunks of this category (child categories not included)
- `tagDefinitions` is lazy-loaded — no cost until accessed
- `allChunks` is also lazy-loaded — fast when only using `tags` or `name`

## Related

- [Programmable Block](../README.md)
- [env.getCategoryNames](05-env.getCategoryNames.md)
- [env.chunk](01-env.chunk.md)
- [Category](../../../../AdvancedPanel/01-Basics/01-Category%20Template%20Tab.md)
