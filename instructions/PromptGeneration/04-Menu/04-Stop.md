# Stop

**Stop**

## When to Use

- When you want to interrupt prompt generation in progress
- When you want to stop timer generation
- When you want to stop on-demand generation

## What It Does

Stops all currently running generation processes. The following states can be stopped:

- Once Generation processing
- Timer generation auto-execution
- On-demand generation (API server)

## How to Use

1. Select **PromptGeneration > Stop** from the menu
2. The running generation stops

## Notes

- This menu is disabled when no generation is in progress
- If stopped mid-generation, partially generated results are not preserved
- To resume timer or on-demand generation after stopping, restart from each respective menu

## Related

- [Once Generation](01-Once%20Generation.md)
- [Timer Generation Start](03-Timer%20Generation/01-Timer%20Generation%20Start.md)
- [Start On Demand](02-Generation%20On%20Demand/01-Start%20On%20Demand.md)
- [Generation Queue](05-Generation%20Queue/README.md)
