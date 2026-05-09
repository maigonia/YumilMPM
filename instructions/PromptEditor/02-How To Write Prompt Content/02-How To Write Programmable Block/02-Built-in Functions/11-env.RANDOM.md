# env.RANDOM

**Function to generate a random number between 0 and 1**

## Syntax

```javascript
env.RANDOM()
```

**Return value**: `number` - Floating-point number from 0 (inclusive) to 1 (exclusive) `[0, 1)`

## Behavior

- **Without seed**: Uses `Math.random()` (non-reproducible)
- **With seed**: Uses the Mulberry32 algorithm (reproducible)

## Usage Examples

### Basic Usage

```javascript
@@@_
const r = env.RANDOM();
env.OUTPUT(String(r));
_@@@
```

> Output example: `0.7234567890123456`

### Probability Branching

```javascript
@@@_
if (env.RANDOM() < 0.3) {
  env.OUTPUT("Selected with 30% probability");
} else {
  env.OUTPUT("Selected with 70% probability");
}
_@@@
```

### Random Selection from Array

```javascript
@@@_
const options = ["red", "blue", "green"];
const index = Math.floor(env.RANDOM() * options.length);
env.OUTPUT(options[index]);
_@@@
```

*For integer random numbers, using [env.RANDINT](10-env.RANDINT.md) is simpler

## Notes

- Synchronous function (`await` not needed)
- Setting a seed with [env.SEED](12-env.SEED.md) generates a reproducible random sequence
- In the QuickJS sandbox, `Math.random()` is not available, so use this function instead

## Related

- [Programmable Block](../README.md)
- [env.RANDINT](10-env.RANDINT.md)
- [env.SEED](12-env.SEED.md)
