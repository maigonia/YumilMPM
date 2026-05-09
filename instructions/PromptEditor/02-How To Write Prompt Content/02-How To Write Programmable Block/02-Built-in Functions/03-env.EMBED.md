# env.EMBED

**Function to convert text into an embedding vector**

## Syntax

```javascript
await env.EMBED(text)
```

| Argument | Type | Description |
|----------|------|-------------|
| `text` | string | Text to embed |

**Return value**: `Promise<string>` - Embedding vector in JSON format (`number[]` as JSON string)

## Behavior

Calls the LM Studio Embeddings API (`http://localhost:1234/v1/embeddings`) to vectorize text.

- Timeout: 30 seconds
- Return format: `"[0.123, -0.456, 0.789, ...]"` (JSON string)
- On error: Empty string `""`

## Prerequisites

- LM Studio must be running
- An Embeddings model must be loaded

## Usage Examples

### Similarity Calculation

```javascript
@@@_
const vec1 = await env.EMBED("happy smiling face");
const vec2 = await env.EMBED("sad crying expression");
const similarity = env.SIMILARITY(vec1, vec2);
env.OUTPUT(\`Similarity: \${similarity.toFixed(3)}\`);
_@@@
```

### Search for Most Similar Chunk

```javascript
@@@_
const query = "fantasy castle";
const queryVec = await env.EMBED(query);

const chunks = await env.CI("Background.ToArray(all)");
let bestMatch = null;
let bestScore = -1;

for (const chunk of chunks) {
  const chunkVec = await env.EMBED(chunk.content);
  const score = env.SIMILARITY(queryVec, chunkVec);
  if (score > bestScore) {
    bestScore = score;
    bestMatch = chunk;
  }
}

if (bestMatch) {
  env.OUTPUT(bestMatch.content);
}
_@@@
```

## Notes

- **Async function**: `await` is required
- Pass the return value directly to [env.SIMILARITY](13-env.SIMILARITY.md) (JSON string)
- Vector dimensions depend on the loaded model
- Each API call takes time, so be careful with large amounts of text

## Related

- [Programmable Block](../README.md)
- [env.SIMILARITY](13-env.SIMILARITY.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM Studio.md)
