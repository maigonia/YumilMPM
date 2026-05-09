# Generation Settings (PromptGeneration Settings)

Control file output and behavior during prompt generation.

## Show ResultWindow After Generation

Whether to show result window after generation completes.
- ON: Generation results shown in popup
- OFF: Result window not shown (for background generation)

## Activate ResultWindow After Generation

Whether to bring result window to foreground after generation.
- ON: Window comes to front when generation completes
- OFF: Doesn't interrupt other work

## Auto-save prompts to text files

Whether to automatically save generated prompts as text files.
- ON: Auto-save to specified folder (sequential filenames)
- OFF: Don't save files (clipboard only)

## Auto-Send Result to Clipboard

Whether to automatically copy generation results to clipboard.
- ON: Ready for Ctrl+V paste immediately after generation
- OFF: Manual copy required

## Same CategoryIdentifier Output Same Result

Behavior when same Category Identifier appears multiple times.
- ON (Cache enabled): `@@@_HairColor_@@@, @@@_HairColor_@@@` → blonde hair, blonde hair
- OFF (Cache disabled): `@@@_HairColor_@@@, @@@_HairColor_@@@` → blonde hair, black hair (random each time)

Use ON to unify hair color for same character, OFF for variations.

## Enable CommentOut

Whether to process `//` comments in prompts.
- ON: Everything after // is excluded from output
- OFF: // is output as-is

Example: `1girl, // this is a comment` → With ON, only `1girl,` is output

## Include Picked Prompts Information in Output

Whether to include metadata (which prompts were selected) in output.
- ON: JSON-format metadata added at start of output
- OFF: Prompt content only

Useful for debugging and reproducibility verification.

## Enable Generated Output To PromptTree

Enable/disable auto-adding generation results to PromptTree.
- ON: Auto-add generation results as children of specified node
- OFF: Don't add

For workflows accumulating generation results with Timer generation.

## Set Max Recursion Depth

Set max depth for Category Identifier nested expansion.
Example: `@@@_Main_@@@` → `@@@_Sub_@@@` → `@@@_Detail_@@@` → ...
Default: 10 levels
Safety measure to prevent infinite loops. Increase for deep nesting structures.

## Access

`Prompt Generation > Each menu item`
