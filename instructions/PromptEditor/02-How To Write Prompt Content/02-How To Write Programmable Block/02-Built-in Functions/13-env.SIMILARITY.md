# env.SIMILARITY

**Function to calculate cosine similarity of embedding vectors**

## Syntax

```javascript
env.SIMILARITY(vec1, vec2)
```

| Argument | Type | Description |
|----------|------|-------------|
| `vec1` | string | Return value from [env.EMBED](03-env.EMBED.md) (JSON array string) |
| `vec2` | string | Return value from [env.EMBED](03-env.EMBED.md) (JSON array string) |

**Return value**: `number` - Cosine similarity (-1 to 1, closer to 1 means more similar)

## Formula

```
similarity = (vec1 · vec2) / (|vec1| × |vec2|)
```

- `vec1 · vec2`: Inner product (dot product)
- `|vec|`: Vector norm (magnitude)

## Behavior on Error

Returns `NaN` in the following cases (to distinguish from a valid similarity of `0`, which means orthogonal vectors):

- Arguments are not JSON arrays
- Vector dimensions do not match
- Vectors are empty
- Norm is 0 (zero vector)
- JSON parse error

`NaN` always evaluates to `false` in comparisons like `>` or `<`, so a condition like `if (score > 0.5)` safely fails. To explicitly detect errors, use `isNaN(score)`.

```javascript
@@@_
const score = env.SIMILARITY(vec1, vec2);
if (isNaN(score)) {
  env.OUTPUT("Similarity calculation error");
} else if (score > 0.8) {
  env.OUTPUT("Very similar");
} else {
  env.OUTPUT("Similarity: " + score.toFixed(3));
}
_@@@
```

## Usage Examples

### Basic Similarity Calculation

```javascript
@@@_
const vec1 = await env.EMBED("cat sitting on a chair");
const vec2 = await env.EMBED("dog lying on a sofa");
const similarity = env.SIMILARITY(vec1, vec2);
env.OUTPUT(\`Similarity: \${similarity.toFixed(3)}\`);
_@@@
```

### Conditional Branching by Similarity

```javascript
@@@_
const baseVec = await env.EMBED("fantasy medieval castle");
const testVec = await env.EMBED(await env.CI("Background"));
const score = env.SIMILARITY(baseVec, testVec);

if (score > 0.8) {
  env.OUTPUT("Very similar");
} else if (score > 0.5) {
  env.OUTPUT("Somewhat similar");
} else {
  env.OUTPUT("Low similarity");
}
_@@@
```

## Notes

- Synchronous function (`await` not needed)
- Pass the return value of [env.EMBED](03-env.EMBED.md) as-is (JSON.parse is done internally)
- Embedding vectors usually have mostly positive values, so actual similarity is often in the 0-1 range

## Related

- [Programmable Block](../README.md)
- [env.EMBED](03-env.EMBED.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
