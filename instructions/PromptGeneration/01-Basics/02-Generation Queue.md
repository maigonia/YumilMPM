# Generation Queue

A system for registering multiple generation configurations in advance and executing them one by one in order.

## When It's Useful

Normal generation (Once Generation) generates using the current tree's check state as-is. However, queues are useful in the following cases:

- When you want to generate multiple times while changing check states and prompt combinations
- When you want to prepare different setting patterns in advance and execute them together
- When you want to repeatedly generate with the same settings

## Terminology

| Term | Description |
|------|-------------|
| **Snapshot** | A saved copy of the tree's check state at a certain point |
| **Queue** | A single generation session using a snapshot. Multiple can be registered in a queue pattern |
| **Queue Pattern** | A collection of queues with rules for execution method (sequential, loop, etc.) |

The relationships:

```
Queue Pattern List (Generation Controller Panel)
├── Queue Pattern A (Sequential Pattern)
│   ├── Queue 1 (uses snapshot)
│   ├── Queue 2 (uses snapshot)
│   └── Queue 3 (uses snapshot)
├── Queue Pattern B (Loop Pattern)
│   ├── Queue 1
│   └── Queue 2
└── ...
```

Queue patterns are added to the Queue Pattern List in the Generation Controller panel. The key point is that it's the queue pattern itself, not individual queues, that gets added to the list. Queue patterns in the list are processed sequentially — when a queue pattern finishes all its queues, it's automatically removed and execution moves to the next queue pattern.

Each queue generates using the check state saved in its snapshot, so changing the current tree does not affect registered snapshots.

## Types of Queue Patterns

There are 3 types of queue patterns.

### Standard Pattern

A pattern that works without thinking about queues. When a generation trigger like Once Generation is executed with no queue patterns present, a queue pattern is automatically created and executed with the current state. Normal generation without manually added queue patterns uses this.

### Sequential Pattern

Registers multiple queues and advances to the next queue with each generation. When all are complete, it's automatically removed from the queue pattern list (or optionally kept with settings).

**Example**: With 3 queues registered

- Generation 1 → Execute queue 1
- Generation 2 → Execute queue 2
- Generation 3 → Execute queue 3 → Complete

See [Sequential Pattern](../04-Menu/05-Generation%20Queue/02-Add%20Sequential%20Pattern.md) for details.

### Loop Pattern

Registers multiple queues and repeats from the beginning after all are executed. You can specify a loop count or shuffle the order each cycle.

See [Loop Pattern](../04-Menu/05-Generation%20Queue/03-Add%20Loop%20Pattern.md) for details.

## Creating Queue Patterns

1. Select the pattern type to add from **PromptGeneration > Generation Queue** menu
2. The pattern editor opens
3. Arrange the tree's check states then click "**Add Current Snapshot**" to add a queue
4. Change check states and add more queues as needed
5. Click "**Add to Queue**" to confirm

In the pattern editor, you can reorder queues (up/down buttons), rename them (double-click), and delete them.

## Executing Queue Patterns

Select the queue pattern you want to execute from the Generation Controller panel dropdown, then execute generation with Once / Timer / On Demand buttons.

- **Once**: Execute one queue per button press
- **Timer**: Automatically execute queues in order at set intervals
- **On Demand**: Execute in order upon requests from external apps

Progress (progress bar, current queue name) is displayed below the dropdown during execution.

## Managing Queue Patterns

Use the buttons beside the dropdown.

| Button  | Function                                       |
| ------- | ---------------------------------------------- |
| Edit    | Open the pattern editor to change settings     |
| Reset   | Return progress to the beginning               |
| Delete  | Delete the queue pattern                       |

Created queue patterns can be saved to files and reused. Save with the "Save" button in the pattern editor, then load from saved patterns when the editor is opened next time.

## Related

- [Generation](03-About%20Prompt%20Generation.md)
- [Standard Pattern](../04-Menu/05-Generation%20Queue/01-Add%20Standard%20Pattern.md)
- [Sequential Pattern](../04-Menu/05-Generation%20Queue/02-Add%20Sequential%20Pattern.md)
- [Loop Pattern](../04-Menu/05-Generation%20Queue/03-Add%20Loop%20Pattern.md)
- [Conditional Pattern](../04-Menu/05-Generation%20Queue/04-Add%20Conditional%20Pattern.md)
- [All Patterns Pattern](../04-Menu/05-Generation%20Queue/05-Add%20AllPatterns%20Pattern.md)
- [Once Generation](../04-Menu/01-Once%20Generation.md)
- [Timer Generation Start](../04-Menu/03-Timer%20Generation/01-Timer%20Generation%20Start.md)
