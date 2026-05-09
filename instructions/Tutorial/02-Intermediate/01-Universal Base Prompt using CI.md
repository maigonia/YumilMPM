# Universal Base Prompt using CI

A pattern for creating a "base prompt" that serves as a template by combining Category Identifiers.

## Overview of This Pattern

Image generation prompts consist of many elements: LoRA, angles, poses, characters, effects, and more. By managing each element as a separate category and combining them with Category Identifiers in one main category (e.g., PositivePrompt), you can create a flexible template.

## Understanding with Examples

### Example 1: Basic Form (Random One from Each Category)

Write the following in a PositivePrompt category prompt:

```
@@@_LoraUtility_@@@,
@@@_Angle_@@@,
@@@_Pose_@@@,

@@@_Character1_@@@,
@@@_Character1Details_@@@,

@@@_Character2_@@@,
@@@_Character2Details_@@@,

@@@_Etc_@@@,
@@@_Effects_@@@,
@@@_Style_@@@,
@@@_Quality_@@@,
```

Each `@@@_CategoryName_@@@` is replaced with one randomly selected checked prompt from that category. Fixed text not enclosed in CI is output as-is.

Since Angle, Pose, Effects, etc. change with each generation, you can easily create variations.

### Example 2: Get All Pattern (Pick=-1)

For some categories, you want "all checked items" rather than "one random". Use `Pick(first=-1)` or `Pick(random=-1)` to get all checked items.

```
@@@_LoraUtility.Pick(first=-1)_@@@,
@@@_Angle_@@@,
@@@_Pose.Edit(ShuffleTags)_@@@,

@@@_Backgrounds_@@@,

@@@_Character1_@@@,
@@@_Character1Details.Pick(random=-1)_@@@,

@@@_Character2_@@@,
@@@_Character2Details.Pick(random=-1)_@@@,

@@@_Etc_@@@,

@@@_Effects.Pick(random=-1)_@@@,
@@@_Style.Pick(first=-1)_@@@,
```

**Key Points about Pick(-1):**
- Specifying `-1` outputs **all checked items** instead of just one
- `Pick(first=-1)`: Get all in registration order (for LoRA, Style where order matters)
- `Pick(random=-1)`: Get all shuffled (for Details, Effects where order doesn't matter)

**Usage Examples:**
- LoraUtility → `first=-1` (no need to randomize; same order each time makes output easier to verify)
- Character1Details → `random=-1` (detailed descriptions are fine shuffled)
- Style → `first=-1` (style specifications should be output in intended order)
- Effects → `random=-1` (effect order is flexible)
- Angle, Pose → No Pick (want just one random selection)

## Why This Pattern Is Useful

- **Organize fragments by type**: Manage LoRA, poses, effects, etc. in separate categories
- **Easy structure changes**: Just rearrange CI order in the base prompt to change output structure
- **Variations through check operations**: Generate different prompts just by changing check states
- **Mix fixed and random**: Freely combine fixed text with random elements
- **Flexible retrieval**: Choose "random one", "all (ordered)", or "all (shuffled)" per category

## How to Create

1. **Create fragment categories**: Create categories for each element type (Angle, Pose, Character1, Effects, etc.)
2. **Register prompts**: Add prompts to each category and check the ones you want to use
3. **Create main category**: Create a category named "PositivePrompt" or similar
4. **Write base template**: Write a template with CIs arranged in the main category's prompt
5. **Configure Output**: Turn ON Output for the main category. Keep fragment categories' Output OFF (they're referenced via CI, so direct output isn't needed)

## Practical Examples

- **Same pattern for NegativePrompt**: Create a main category for negative prompts and compose with CIs similarly
- **Combine with Check Presets**: Save all category check states as presets to switch entire themes with one click

## Related

- CI Basics → Beginner "Category Identifier Basics"
- Generation Setting "Same CategoryIdentifier Output Same Result" → Controls whether same CI outputs are cached
- Restoring Check States → Intermediate "Restoring Check States"
