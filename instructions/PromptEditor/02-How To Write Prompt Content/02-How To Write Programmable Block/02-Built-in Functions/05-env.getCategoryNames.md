# env.getCategoryNames

**Function to get all category names**

## Syntax

```javascript
env.getCategoryNames()
```

**Return value**: `string[]` - Array of all category names

## Usage Examples

### Basic Retrieval

```javascript
@@@_
const names = env.getCategoryNames();
env.OUTPUT(names.join(", "));
_@@@
```

> Output example: `Character, Background, Settings`

### Filter by Specific Prefix

```javascript
@@@_
const names = env.getCategoryNames();
const effectCategories = names.filter(n => n.startsWith("Effect"));
env.OUTPUT(effectCategories.join(", "));
_@@@
```

### Process All Categories in Sequence

```javascript
@@@_
const names = env.getCategoryNames();
const results = [];

for (const name of names) {
  const cat = env.getCategory(name);
  if (cat && cat.allChunks.length > 0) {
    results.push(\`\${name}: \${cat.allChunks.length} items\`);
  }
}
env.OUTPUT(results.join("\n"));
_@@@
```

### Check Category Existence

```javascript
@@@_
const names = env.getCategoryNames();
if (names.includes("Character")) {
  env.OUTPUT(await env.CI("Character"));
} else {
  env.OUTPUT("Character category does not exist");
}
_@@@
```

## Notes

- Synchronous function (`await` not needed)
- Empty categories are also included
- Often used in combination with [env.getCategory](04-env.getCategory.md)

## Related

- [Programmable Block](../README.md)
- [env.getCategory](04-env.getCategory.md)
- [Category](../../../../AdvancedPanel/01-Basics/01-Category%20Template%20Tab.md)
