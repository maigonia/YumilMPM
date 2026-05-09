# Programmable Block Basics

JavaScript code written between `@@@_` and `_@@@` is executed during prompt generation.

## Safe Sandbox Environment

Programmable blocks run in a QuickJS sandbox.

**What you can do:**
- Execute JavaScript (ES2020+)
- Use `env.*` functions
- Array/object manipulation
- JSON processing, regular expressions
- Math functions, async/await

**What you cannot do (directly from PB code):**
- File read/write
- Internet access
- System command execution
- External module imports

### Exception: Access via Plugins

When a PB calls a plugin through CI's `.Edit(plugin name)` or `env.PLUGINEDIT(text, "plugin name")`, that plugin can access files or networks within the scope of permissions it has been granted.

For example, calling a translation plugin that has network permission causes external communication to occur, even though the PB code itself cannot connect to the network.

What a called plugin can do is determined by the permissions previously granted by the user in the Plugin settings. Permissions that have not been granted are not used through PB either.

## Basics: Output

Use `env.OUTPUT()` to output text.

```
@@@_
env.OUTPUT("This will be output");
_@@@
```

Multiple calls are joined with newlines.

## Categories and Chunks

Get category list:

```
@@@_
const names = env.getCategoryNames();
for (const name of names) {
  env.OUTPUT("- " + name);
}
_@@@
```

Get category info:

```
@@@_
const cat = env.getCategory("Character");
if (cat) {
  env.OUTPUT("Chunk count: " + cat.allChunks.length);
}
_@@@
```

## Current Chunk Info (env.chunk)

When running inside chunk content, `env.chunk` accesses current chunk information.

```
@@@_
env.OUTPUT("Chunk name: " + env.chunk.name);
env.OUTPUT("Category: " + env.chunk.categoryName);
env.OUTPUT("Tags: " + env.chunk.tags.join(", "));
_@@@
```

## ChunkInfo Properties

**Basic properties:**
- id - Unique identifier
- name - Chunk name
- categoryName - Category name
- content - Full content
- memos - Array of memos
- tags - Array of tag names
- isRoot - Is root chunk

**Extended properties:**
- tagnames - Tag names array (same as tags)
- imagePaths - Image paths array
- memoPaths - Memo source file paths
- selected - Check state
- expanded - Expanded state
- createdAt - Creation date (ISO string)
- isFolder - Is folder chunk
- isFile - Is file chunk
- displayType - Display type
- treepath - Tree path
- parentId - Parent chunk ID

**File system properties:**
- baseFilePath - Base file path
- sourceFilePath - Source file path
- folderPath - Folder path
- sourceFolderPath - Source folder path

**Tree navigation (lazy-loaded):**
- parent - Parent chunk
- children - Child chunks array
- siblings - Sibling chunks (excluding self)
- descendants - All descendants flat array
- ancestors - All ancestors (parent to root)
- leaves - Leaf descendants only

Output child chunks:

```
@@@_
const children = env.chunk.children;
for (const child of children) {
  env.OUTPUT(child.content);
}
_@@@
```
