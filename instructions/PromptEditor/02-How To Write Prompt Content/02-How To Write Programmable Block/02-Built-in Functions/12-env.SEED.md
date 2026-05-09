# env.SEED

**Function to set the random seed**

## Syntax

```javascript
env.SEED(n)
```

| Argument | Type | Description |
|----------|------|-------------|
| `n` | number | Seed value (any number) |

**Return value**: None

## Overview

Setting a seed value causes subsequent [env.RANDOM](11-env.RANDOM.md) / [env.RANDINT](10-env.RANDINT.md) calls to generate a reproducible random sequence. Internally uses the Mulberry32 algorithm.

## Seed Persistence

- The seed persists **across the entire app session**
- Maintained between different blocks and different generations
- Reset on app restart
- To get the same result every time with the same seed, explicitly set it at the beginning of the block

## Usage Examples

### Reproducible Random Numbers

```javascript
@@@_
env.SEED(12345);
const a = env.RANDINT(1, 100);
const b = env.RANDINT(1, 100);
env.OUTPUT(\`\${a}, \${b}\`);
_@@@
```

> Same seed produces the same result every time

### Date-Based Seed

```javascript
@@@_
// Same day, same result
const today = new Date().toISOString().slice(0, 10);
const seed = today.split("-").reduce((a, b) => a * 100 + Number(b), 0);
env.SEED(seed);
env.OUTPUT(await env.CI("DailyQuote.Pick(random=1)"));
_@@@
```

## Notes

- Synchronous function (`await` not needed)
- Without a seed, `Math.random()` is used (non-reproducible)
- The seed is internally updated with each call (setting the same seed repeatedly restarts the same sequence)

## Related

- [Programmable Block](../README.md)
- [env.RANDOM](11-env.RANDOM.md)
- [env.RANDINT](10-env.RANDINT.md)
- [Same CI Output Same Result](../../../../PromptGeneration/04-Menu/12-Same CategoryIdentifier Output Same Result.md)
