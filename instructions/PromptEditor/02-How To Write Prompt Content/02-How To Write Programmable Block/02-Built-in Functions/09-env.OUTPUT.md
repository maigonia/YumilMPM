# env.OUTPUT

**Function to output text**

## Syntax

```javascript
env.OUTPUT(text)
```

| Argument | Type | Description |
|----------|------|-------------|
| `text` | string | Text to output |

**Return value**: None

## Basic Usage

```javascript
@@@_
const result = await env.CI("Character");
env.OUTPUT(result);
_@@@
```

## Multiple Calls

Calling `env.OUTPUT()` multiple times joins each text with a newline (`\n`).

```javascript
@@@_
env.OUTPUT("Line 1");
env.OUTPUT("Line 2");
env.OUTPUT("Line 3");
_@@@
```

> Output:
```
Line 1
Line 2
Line 3
```

### Joining Without Newlines

Concatenate strings and output at once.

```javascript
@@@_
const parts = [];
parts.push(await env.CI("Character"));
parts.push(await env.CI("Background"));
env.OUTPUT(parts.join(", "));
_@@@
```

## Important Notes

- **Output required**: Nothing is output from the Programmable Block unless `env.OUTPUT()` is called
- **Synchronous function**: `await` is not needed
- **Empty string**: Passing an empty string outputs an empty line

## Related

- [Programmable Block](../README.md)
- [env.CI](02-env.CI.md)
- [Generation](../../../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Once Generation](../../../../PromptGeneration/04-Menu/01-Once Generation.md)
- [Add From Generated Output](../../../../PromptTree/04-Menu/03-Selected Add/02-Add From Generated Output.md)
