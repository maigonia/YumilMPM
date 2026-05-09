# Add Standard Pattern

**PromptGeneration > Generation Queue > Add Standard Pattern**

The simplest queue pattern.

## What It Does

When you execute the menu, a standard pattern is immediately added to the [Queue Pattern List](README.md) in the Generation Controller panel as a snapshot of the current check state. No editor opens and there are no configuration options.

Changes to the tree's check state after adding do not affect the snapshot in the already added standard pattern.

## Relationship with Normal Generation

When generation (Once Generation, etc.) is executed with an empty queue pattern list, a standard pattern is automatically created and executed. In other words, normal generation performed without thinking about queues internally uses this standard pattern.

Manually adding from the menu works the same way. A queue pattern for one generation is added using the check state at the time of addition.

## Standard Pattern Characteristics

- Always has exactly one queue (a snapshot of the check state at the time of addition)
- Executing generation performs one generation and automatically removes it from the queue pattern list
- Cannot be edited in the editor (the edit button in the Generation Controller panel is disabled)
- Can be reset or deleted

## Related

- [Generation Queue](README.md)
- [Sequential Pattern](02-Add%20Sequential%20Pattern.md)
- [Loop Pattern](03-Add%20Loop%20Pattern.md)
- [Once Generation](../01-Once%20Generation.md)
- [Output Category](../../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Check State](../../../PromptTree/01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
