# env.chunk

**Current chunk information object**

## Overview

`env.chunk` is an object that retrieves information about the chunk itself where the Programmable Block is written.

## Properties

### Basic Properties

| Property | Type | Description |
|----------|------|-------------|
| `id` | string | Unique chunk ID |
| `name` | string | Chunk name |
| `categoryName` | string | Name of the category it belongs to |
| `content` | string | Chunk content (full text) |
| `memos` | string[] | Memo array |
| `tags` | string[] | Tag name array |
| `tagDefinitions` | object[] | Tag definition object array (lazy-loaded) |
| `isRoot` | boolean | Whether it's a root chunk |

### Tree Navigation Properties

| Property | Type | Description |
|----------|------|-------------|
| `parent` | ChunkInfo | Parent chunk |
| `children` | ChunkInfo[] | Child chunk array |
| `siblings` | ChunkInfo[] | Sibling chunk array (excluding self) |
| `ancestors` | ChunkInfo[] | Ancestor chunk array (up to root) |
| `descendants` | ChunkInfo[] | Descendant chunk array (all levels) |
| `leaves` | ChunkInfo[] | Leaf chunk array (those without children) |

### Extended Properties

| Property | Type | Description |
|----------|------|-------------|
| `imagePaths` | string[] | Image path array |
| `memoPaths` | string[] | Memo file path array |
| `selected` | boolean | UI selection state (whether highlighted) |
| `createdAt` | string | Creation date (ISO format) |
| `treepath` | string | Tree path (e.g., `Parent/Child/Name`) |
| `displayType` | string | Display type (`normal`, `group`, `fileFolder`, `fileItem`) |
| `baseFilePath` | string | Base file path |

## Usage Examples

### Basic Retrieval

```javascript
@@@_
const { name, tags, content } = env.chunk;
env.OUTPUT(\`Name: \${name}, Tags: \${tags.join(", ")}\`);
_@@@
```

### Conditional Branching by Tag

```javascript
@@@_
if (env.chunk.tags.includes("fantasy")) {
  env.OUTPUT(await env.CI("FantasyContent"));
} else {
  env.OUTPUT(await env.CI("DefaultContent"));
}
_@@@
```

### Getting Tag Details

```javascript
@@@_
const defs = env.chunk.tagDefinitions;
const info = defs.map(t =>
  t.description ? t.name + ": " + t.description : t.name
);
env.OUTPUT(info.join("\n"));
_@@@
```

### Referencing Parent Chunk

```javascript
@@@_
const parentName = env.chunk.parent?.name || "Root";
env.OUTPUT(\`Parent: \${parentName}\`);
_@@@
```

### Listing Child Chunks

```javascript
@@@_
const children = env.chunk.children || [];
const names = children.map(c => c.name);
env.OUTPUT(names.join(", "));
_@@@
```

### Traversing Ancestors

```javascript
@@@_
const ancestors = env.chunk.ancestors || [];
const path = ancestors.map(a => a.name).join(" > ");
env.OUTPUT(path);
_@@@
```

## Notes

- Tree navigation properties are lazily loaded
- Returns `undefined` if not present, so use optional chaining (`?.`)
- `tags` and `tagnames` have the same content (tag name string arrays)
- `tagDefinitions` is an object array including descriptions and usage counts. See [env.globalTags](06-env.globalTags.md) for details

## Related

- [Programmable Block](../README.md)
- [Prompt](../../../../PromptTree/01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [Hierarchy](../../../../PromptTree/01-Basics/01-Concepts/02-Understanding%20Hierarchy.md)
- [TreePath](../../../../PromptTree/02-Glossary/01-TreePath.md)
- [env.getCategory](04-env.getCategory.md)
