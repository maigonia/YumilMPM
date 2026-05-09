# Programmable Block Practice

## Built-in Functions List

**Output:**
- env.OUTPUT(text) - Output text

**Chunk/Category:**
- env.chunk - Current chunk info
- env.getCategoryNames() - Get category names
- env.getCategory(name) - Get category info

**CI Execution:**
- await env.CI(expr) - Execute CI expression (async)

**History:**
- env.HISTORY(index, category?) - Past generation results

**LLM Integration:**
- await env.LMEDIT(preset, prompt) - LLM edit (async)
- await env.EMBED(text) - Generate embedding vector
- env.SIMILARITY(vec1, vec2) - Cosine similarity
- await env.AI_TAGGING(text) - AI tagging

**Image:**
- await env.WD14(imagePath) - WD14 tag extraction (async)

**Plugin Invocation:**
- await env.PLUGINEDIT(text, spec) - Call an Edit plugin directly (same argument syntax as CI's `.Edit(...)`)

**Random:**
- env.SEED(n) - Set seed
- env.RANDOM() - Random 0-1
- env.RANDINT(min, max) - Random integer

**Other:**
- env.globalTags - Global tags array

## Example 1: Probabilistic Element Addition

```
@@@_
let output = env.chunk.content;

// 30% chance to add effect
if (env.RANDOM() < 0.3) {
  output += ", glowing effect";
}

env.OUTPUT(output);
_@@@
```

## Example 2: Conditional Child Chunk Output

```
@@@_
const children = env.chunk.children;

if (children.length === 0) {
  env.OUTPUT("(no items)");
} else if (children.length === 1) {
  env.OUTPUT(children[0].content);
} else {
  children.forEach((chunk, i) => {
    env.OUTPUT(`[${i + 1}] ${chunk.name}: ${chunk.content}`);
  });
}
_@@@
```

## Example 3: Tag Filtering

```
@@@_
const filtered = env.chunk.children.filter(
  child => child.tags.includes("favorite")
);

for (const child of filtered) {
  env.OUTPUT(child.content);
}
_@@@
```

## Common Mistakes

**Forgetting await:**
- ❌ `const result = env.LMEDIT("default", "...");`
- ✅ `const result = await env.LMEDIT("default", "...");`

**Using console.log:**
- ❌ `console.log("debug");` // Does not work
- ✅ `env.OUTPUT("debug");` // Use this instead
