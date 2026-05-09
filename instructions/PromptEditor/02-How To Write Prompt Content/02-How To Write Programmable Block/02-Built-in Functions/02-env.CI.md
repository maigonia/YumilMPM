# env.CI

**Function to execute a Category Identifier expression**

## Syntax

```javascript
await env.CI(expression);
```

| Argument | Type | Description |
|----------|------|-------------|
| `expression` | string | Category Identifier expression |

**Return value**: `string | ChunkInfo[]`

- Normal: Joined text (string)
- With `.ToArray()`: Chunk array (ChunkInfo[])

## Basic Usage

```javascript
@@@_
const result = await env.CI("Character");
env.OUTPUT(result);
_@@@
```

> Equivalent to `@@@_Character_@@@`

## String Escaping Notes

Since CI expressions are passed as JS strings, be careful with escape sequences like `\n`.

### Recommended: Use String.raw

Using `String.raw` passes escape sequences as-is without processing.

```javascript
@@@_
// Using String.raw (recommended)
// \n is passed as-is as two characters to CI
const result = await env.CI(String.raw\`Character.Join(\n)\`);
_@@@
```

## Using Action Commands

Action commands available in [Category Identifier](../../01-How To Write Category Identifier/README.md) can be written directly.

```javascript
@@@_
// Target, Filter, Pick, Sort, Join, Edit are available
const result = await env.CI("Character.Target(all).Filter(tag=main).Pick(random=3)");
env.OUTPUT(result);
_@@@
```

## ToArray - Get as Array

Using `.ToArray(mode)` returns chunk information as an array before joining.

### Mode List

| Mode | Return Value | Description |
|------|-------------|-------------|
| `name` | string[] | Array of chunk names |
| `content` | string[] | Array of chunk contents |
| `tags` | string[] | Array of tag names (flat) |
| `all` | ChunkInfo[] | Array of objects with all information |

### ToArray Examples

```javascript
@@@_
// Get array of names
const names = await env.CI("Character.Target(all).ToArray(name)");
env.OUTPUT(names.join(" / "));
_@@@
```

```javascript
@@@_
// Get all information and loop through
const chunks = await env.CI("Character.Target(checked).ToArray(all)");
for (const chunk of chunks) {
  env.OUTPUT(\`\${chunk.name}: \${chunk.tags.join(", ")}\n\`);
}
_@@@
```

## Dynamic CI Expression Construction

Variables can be used to dynamically build CI expressions.

```javascript
@@@_
const categoryName = "Character";
const tagFilter = "main";
const result = await env.CI(\`\${categoryName}.Filter(tag=\${tagFilter})\`);
env.OUTPUT(result);
_@@@
```

### Usage in Loops

```javascript
@@@_
const categories = ["Character", "Background", "Effect"];
const results = [];

for (const cat of categories) {
  const content = await env.CI(\`\${cat}.Pick(random=1)\`);
  results.push(content);
}
env.OUTPUT(results.join(", "));
_@@@
```

## Error Handling

Returns an empty string when an error occurs, such as with a non-existent category.

```javascript
@@@_
const result = await env.CI("NonExistent");
if (result) {
  env.OUTPUT(result);
} else {
  env.OUTPUT("Category not found");
}
_@@@
```

### With Regular Strings

```javascript
@@@_
// Regular string - \n is converted to a newline character
const result = await env.CI("Character.Join(\n)");

// To pass \n as a literal, escape with \\
const result2 = await env.CI("Character.Join(\\n)");
_@@@
```

When CI expressions contain `\n`, `\t`, etc., using `String.raw` is recommended.

## Notes

- **Async function**: `await` is always required
- Executes the same processing as regular [Category Identifier](../../01-How To Write Category Identifier/README.md)
- Use ToArray when you want to access data before joining

## Related

- [Programmable Block](../README.md)
- [Category Identifier](../../01-How To Write Category Identifier/README.md)
- [env.OUTPUT](09-env.OUTPUT.md)
- [env.chunk](01-env.chunk.md)
- [Target](../../01-How To Write Category Identifier/02-Action Commands/01-Target.md)
- [Filter](../../01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Pick](../../01-How To Write Category Identifier/02-Action Commands/03-Pick.md)
- [Sort](../../01-How To Write Category Identifier/02-Action Commands/04-Sort.md)
- [Join](../../01-How To Write Category Identifier/02-Action Commands/05-Join.md)
- [Edit](../../01-How To Write Category Identifier/02-Action Commands/06-Edit.md)
