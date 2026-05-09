# Add Loop Pattern

**PromptGeneration > Generation Queue > Add Loop Pattern**

A pattern that registers multiple snapshots and repeats from the beginning after all have been executed.

## When to Use

For example, if you want to alternate between generating "daytime background" and "nighttime background" patterns continuously. Register each check state as a snapshot and set the loop count to 0 (infinite), then combine with timer or on-demand generation to automatically repeat day→night→day→night... Enabling shuffle randomizes the order with each cycle.

Ideal for when you want to repeatedly generate the same combination of patterns.

## What It Does

Registers multiple check states (snapshots) in advance, and after all queues are executed, returns to the beginning and executes again. You can specify a loop count or let it repeat infinitely until manually stopped.

## Pattern Editor Usage

The pattern editor opens when you execute the menu.

### Adding and Managing Queues

Queues can be added and managed with the same operations as [Sequential Pattern](02-Add Sequential Pattern.md).

1. Set up the tree's check states and click "**Add Current Snapshot**" to add a queue
2. Repeat as many times as needed

Queue name editing (double-click), reordering (up/down buttons), and deletion work the same way.

### Settings

Loop-specific settings are at the bottom of the pattern editor.

**Loop Count**

| Value           | Behavior                                                 |
| --------------- | -------------------------------------------------------- |
| Numeric value 1+ | Repeats the entire queue the specified number of times  |
| 0               | Infinite loop. Repeats until manually stopped            |

Default is 1.

**Queue Reset**

When enabled, all queue states are reset at the start of each loop before execution. Enabled by default.

**Shuffle**

When enabled, the execution order of queues is randomized from the 2nd loop onward. The 1st loop always executes in the registered order. Disabled by default.

### Save, Load, and Confirm

Same as [Sequential Pattern](02-Add Sequential Pattern.md): "Save" saves to a file, saved patterns can be loaded, and "Add to Queue" confirms.

## Execution Flow

Example: 3 queues registered with loop count of 2

- Generation 1 → Execute queue 1 (loop 1)
- Generation 2 → Execute queue 2
- Generation 3 → Execute queue 3 → Loop 1 complete
- Generation 4 → Execute queue 1 (loop 2)
- Generation 5 → Execute queue 2
- Generation 6 → Execute queue 3 → Loop 2 complete → Done

When shuffle is enabled, the execution order in loop 2 is randomized (e.g., queue 3→queue 1→queue 2).

During execution, a progress bar and display like "Loop 1/2 - Queue Name" shows the current state. For infinite loops, only the loop count is shown like "Loop 1".

## After Completion

When the specified number of loops is complete, the pattern status becomes "completed". Unlike [Sequential Pattern](02-Add Sequential Pattern.md), it is not automatically removed. Reset to re-execute or delete manually.

For infinite loops, it never completes until manually stopped.

## Notes

- If an error occurs mid-queue, the next queue continues to execute
- Resetting restores the loop count and progress to the beginning

## Related

- [Generation Queue](README.md)
- [Standard Pattern](01-Add Standard Pattern.md)
- [Sequential Pattern](02-Add Sequential Pattern.md)
- [Once Generation](../01-Once Generation.md)
- [Output Category](../../../CategoryTree/02-Glossary/01-Output Category.md)
- [Check State](../../../PromptTree/01-Basics/01-Concepts/01-Understanding Check State.md)
