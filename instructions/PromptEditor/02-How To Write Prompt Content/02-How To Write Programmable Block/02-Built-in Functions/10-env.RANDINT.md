# env.RANDINT

**Function to generate a random number in a range (supports both integers and floats)**

## Syntax

```javascript
env.RANDINT(min, max)
```

| Argument | Type | Description |
|----------|------|-------------|
| `min` | number | Minimum value |
| `max` | number | Maximum value |

**Return value**: `number`

- **When both min and max are integers** → integer in `[min, max]` (both ends inclusive)
- **When either min or max is a float** → float in `[min, max)` (max is exclusive)
- **When min > max** → arguments are auto-swapped (no error thrown)

## Behavior

Output type changes based on argument types:

```javascript
env.RANDINT(1, 6);       // Integer: one of 1, 2, 3, 4, 5, 6
env.RANDINT(1.0, 1.5);   // Float: continuous value in [1.0, 1.5)
env.RANDINT(5, 1);       // → Same as RANDINT(1, 5) (auto-swapped)
```

> **Combining with weight syntax**: Combine with image generation prompt weight syntax to express random intensity.
> Example: `(red:RANDINT(1.0, 1.5))` → output like `(red:1.234)`

## Usage Examples

### Basic Usage

```javascript
@@@_
const dice = env.RANDINT(1, 6);
env.OUTPUT("Dice: " + dice);
_@@@
```

### Random Selection from Array

```javascript
@@@_
const colors = ["red", "blue", "green", "yellow"];
const index = env.RANDINT(0, colors.length - 1);
env.OUTPUT(colors[index]);
_@@@
```

### Random Quantity

```javascript
@@@_
const count = env.RANDINT(3, 7);
const items = [];
for (let i = 0; i < count; i++) {
  items.push(await env.CI("Item.Pick(random=1)"));
}
env.OUTPUT(items.join(", "));
_@@@
```

## Notes

- Synchronous function (`await` not needed)
- In integer mode, both min and max are included (inclusive on both ends)
- In float mode, min is included but max is excluded (`[min, max)`)
- In JavaScript, `2 === 2.0`, so writing `2.0` literally is still treated as an integer. To explicitly enter float mode, use a non-integer value like `1.5` for at least one argument
- Setting a seed with [env.SEED](12-env.SEED.md) generates a reproducible random sequence
- Uses the same random number generator as [env.RANDOM](11-env.RANDOM.md) internally

## Related

- [Programmable Block](../README.md)
- [env.RANDOM](11-env.RANDOM.md)
- [env.SEED](12-env.SEED.md)
