# Add Sequential Pattern

**PromptGeneration > Generation Queue > Add Sequential Pattern**

A pattern that registers multiple snapshots and advances to the next queue with each generation.

## When to Use

For example, if you want to sequentially generate prompts for Character A's standing pose, Character B's standing pose, and a group shot of both characters. Register each check state as a snapshot, then combine with timer or on-demand generation to automatically run all 3 frames.

Ideal for when you want to output prompts in a fixed number and fixed order, like a story.

## What It Does

Registers multiple check states (snapshots) in advance, and consumes one queue in order with each generation execution. Completion occurs when all queues are consumed.
Created patterns can be saved and loaded.

## Pattern Editor Usage

The pattern editor opens when you execute the menu.

### Adding Queues

1. Set up the tree's check states to match the content you want to generate first
2. Click "**Add Current Snapshot**" to add the current check state as a queue to the list
3. Change the tree's check states and click "Add Current Snapshot" again
4. Repeat as many times as needed

### Queue Operations

Queues added to the list support the following operations:

| Operation    | Method                                    |
| ------------ | ----------------------------------------- |
| Rename       | Double-click the queue name to edit       |
| Reorder      | Use up/down buttons to change order       |
| Delete       | Use the delete button to remove the queue |
| Select       | Click to select                           |

The list shows queue number, name, category count, and creation date.

### Settings

A setting is at the bottom of the pattern editor.

**Execution Order**

| Setting                     | Behavior                           |
| --------------------------- | ---------------------------------- |
| Top to Bottom (default)     | Executes from the top of the list  |
| Bottom to Top               | Executes from the bottom of the list |

When all queues are consumed, the pattern is automatically removed from the Queue Pattern List. If you want to repeat execution, use [Loop Pattern](03-Add%20Loop%20Pattern.md).

### Save and Load

The "**Save**" button at the top of the pattern editor saves the created pattern to a file. When the editor is opened next time, a list of saved patterns is displayed and can be loaded by clicking.

### Confirm

After adding queues and configuring settings, click "**Add to Queue**". The pattern is added to the [Queue Pattern List](README.md).

When editing an existing pattern, the button shows "**Update Pattern**" and clicking it applies the changes.

## Execution Flow

Select a sequential pattern from the Generation Controller panel dropdown and execute generation.

1. Generation 1 → Generate with the 1st queue's snapshot
2. Generation 2 → Generate with the 2nd queue's snapshot
3. Subsequent generations advance to the next queue each time
4. When the last queue completes, the pattern is automatically removed

Progress (progress bar, current queue name) is displayed below the dropdown during execution.

## Notes

- If an error occurs mid-queue, the next queue continues to execute
- Resetting restores progress to the beginning and allows re-execution

## Related

- [Generation Queue](README.md)
- [Standard Pattern](01-Add%20Standard%20Pattern.md)
- [Loop Pattern](03-Add%20Loop%20Pattern.md)
- [Once Generation](../01-Once%20Generation.md)
- [Output Category](../../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Check State](../../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
