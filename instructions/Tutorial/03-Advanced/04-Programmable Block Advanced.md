# Programmable Block Advanced

## env.CI - Execute CI Expression

Execute Category Identifier expressions within JavaScript and get results.

```
@@@_
const result = await env.CI("Character.Target(checked).Pick(random=1)");
env.OUTPUT(result);
_@@@
```

- `await` is required (async operation)
- Returns result as string
- Returns empty string on error

## ToArray - Get as Array

Add `.ToArray()` to CI expression to get ChunkInfo array.

```
@@@_
// Get array of names
const names = await env.CI("Character.Target(checked).ToArray(name)");
for (const name of names) {
  env.OUTPUT("- " + name);
}

// Get ChunkInfo object array
const chunks = await env.CI("Character.Target(checked).ToArray(all)");
for (const chunk of chunks) {
  env.OUTPUT(chunk.name + ": " + chunk.content);
}
_@@@
```

ToArray arguments:
- name - Array of names
- content - Array of contents
- all - Array of ChunkInfo objects

## Conditional Branching

Change output based on conditions.

```
@@@_
const count = env.chunk.children.length;

if (count === 0) {
  env.OUTPUT("No child chunks");
} else if (count === 1) {
  env.OUTPUT("Child chunk: " + env.chunk.children[0].name);
} else {
  env.OUTPUT("Child count: " + count);
}
_@@@
```

## Loop Processing

Process arrays with loops.

```
@@@_
const children = env.chunk.children;

env.OUTPUT("Child chunks:");
for (const child of children) {
  env.OUTPUT("- " + child.name);
}
_@@@
```

## Using Random Numbers

env.RANDINT() generates random integers.

```
@@@_
const dice = env.RANDINT(1, 6);
env.OUTPUT("Dice roll: " + dice);
_@@@
```

env.RANDOM() generates 0-1 random:

```
@@@_
if (env.RANDOM() < 0.5) {
  env.OUTPUT("heads");
} else {
  env.OUTPUT("tails");
}
_@@@
```

## Editing with LLM (env.LMEDIT)

Use LM Studio to generate/edit text.

```
@@@_
const text = env.chunk.content;
const improved = await env.LMEDIT("default", "Improve this text: " + text);

if (improved) {
  env.OUTPUT(improved);
} else {
  env.OUTPUT(text);  // Fallback when LM Studio not connected
}
_@@@
```

## Editing with Plugins (env.PLUGINEDIT)

Apply any Edit plugin to arbitrary text. The argument syntax is identical to CI's `.Edit(...)`.

```
@@@_
const tags = "  zebra , apple , zebra , mango  ";
let result = await env.PLUGINEDIT(tags, "TrimWhitespaceEachLine");
result = await env.PLUGINEDIT(result, "RemoveDuplicateTags");
env.OUTPUT(result);
_@@@
```

→ `apple, mango, zebra`

The CI argument forms work as-is:

```
@@@_
const text = await env.CI("Story");
const summary = await env.PLUGINEDIT(text, "LM=default, please summarize this content");
env.OUTPUT(summary);
_@@@
```

Custom plugins can also be invoked as long as they are enabled in the Programmable Block context:

```
@@@_
const result = await env.PLUGINEDIT("a, c, b", "CustomSortTags");
env.OUTPUT(result);
_@@@
```

### Which Plugins Can Be Called

`env.PLUGINEDIT` can only invoke plugins that are **enabled** in the **Programmable Block** tab of EditPlugin Settings. Not every Edit plugin is available in PB.

- **Plugins not present in the PB tab**: `LMStudioEdit` (use `env.LMEDIT` instead), `WD14 Tagger` (use `env.WD14`), `Programmable Edit` (excluded to avoid PB-in-PB nesting), and dialog-driven plugins like `ReplaceText` and `RemoveTagsAtCursor`
- **Plugins present in the PB tab but disabled**: `env.PLUGINEDIT` errors when called for them

If you instead invoke a plugin via `env.CI("Cat.Edit(pluginName)")`, the **Category Identifier / CT** tab settings apply (managed independently from the PB tab).
