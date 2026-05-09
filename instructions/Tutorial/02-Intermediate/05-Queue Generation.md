# Queue Generation

Manage generation settings in units called "Queue Patterns" and execute sequentially or repeatedly.

## What is a Queue Pattern?

Queues are managed in units called "patterns". Patterns can have multiple snapshots (saved check states) registered.

## Pattern Types

- **Standard**: For single generation (execute one snapshot once)
- **Sequential**: Execute registered snapshots in order once each, then finish
- **Loop**: Repeat registered snapshots (specify count, 0=infinite)

## Understanding with Examples

To generate "morning, noon, night" backgrounds in order:
1. Add Sequential pattern
2. Check only "Morning" category → Add snapshot
3. Check only "Noon" category → Add snapshot
4. Check only "Night" category → Add snapshot

Execution automatically generates all three in sequence.
With Loop pattern set to 10, it generates morning→noon→night→morning→noon→night... for 30 total generations.

## Generating without Adding Patterns

If you start generation like "Once" without adding queue patterns, a Standard pattern is automatically added and executed with the current check state. In other words, regular single generation also works as part of the queue system.

## Use Cases

- **Story scene generation**: Generate sequences like "meeting→adventure→climax→ending" in order
- **Character variations**: Generate continuous expression changes for the same character like "smile→angry→sad"
- **Time variations**: Auto-generate same composition at "morning, noon, evening, night"
- **Outfit changes**: Generate continuous outfit variations like "uniform→casual→swimsuit→dress"

## Save and Load Patterns

Created queue patterns can be saved to files for later reuse.
- Save: `Queue Pattern Editor > Save Pattern`
- Load: `Queue Pattern Editor > Load Pattern`

Once you save a story sequence, you can re-execute it with different settings any number of times.

## Access

`Prompt Generation > Generation Queue > Add Sequential/Loop Pattern`
