# Timer Generation Start

**Timer Generation > Start**

## When to Use

- When you want to automatically generate prompts at regular intervals
- When you want to continuously generate random prompts
- When you want to build a continuous generation flow in conjunction with image generation software
- When you want to mass-add generation results as children under a specified node via PromptTree > Selected: Add > Add From Generated Output

## What It Does

Automatically repeats prompt generation at the configured interval. Generation continues until stopped.

## Processing

It essentially repeats the same process as **PromptGeneration > Once Generation** at regular intervals.

## How to Use

1. Select **PromptGeneration > Timer Generation > Start** from the menu
2. Timer generation starts
3. Prompts are automatically generated at each configured interval
4. Use the "Stop" menu to stop

## Notes

- The interval can be set with the "Set Intervals" menu
- The default interval is 10 seconds (10000 milliseconds)
- This menu is disabled if timer generation is already active
- Generation continues until you manually execute "Stop"

## Related

- [Generation Modes](../../01-Basics/01-Generation Modes.md)
- [Set Intervals](02-Set Intervals.md)
- [Stop](../04-Stop.md)
- [Once Generation](../01-Once Generation.md)
- [Start On Demand](../02-Generation On Demand/01-Start On Demand.md)
- [Generation Queue](../05-Generation Queue/README.md)
