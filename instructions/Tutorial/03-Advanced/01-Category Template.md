# Category Template

A system to configure how to determine the "starting point (initial prompt)" for prompt generation.

In simple terms, it is the output settings for output categories. For example, in a PositivePrompt category, normally one prompt is randomly selected from checked prompts, but you can configure it to always use the selected prompt instead.

## Why Needed

To output prompts, you check the category you want to output in the CategoryTree. Checked categories start output by selecting an "initial prompt" from their own PromptTree.

If Category Template is not configured, the default rule applies:
"Randomly select one from checked prompts in the PromptTree"

Use Category Template when you want to change this default.

## Understanding with Examples

For example, if you have 100 prompts in a "LoRA" category:

**Default (not configured):**
Randomly select one from checked prompts

**With Category Template configured:**
`Target(allleaves).Filter(icon=File).Pick(random=3).Join(, )`
Select 3 random items with file icons from all Leaf nodes and join with commas. This becomes the "initial prompt".

## Important

- Category Template only works for categories with output check enabled
- Setting it on unchecked categories has no effect
- If the initial prompt contains Category Identifiers, replacement executes afterward

## Processing Flow

1. Generate initial prompt from Category Template
2. Replace Category Identifiers in initial prompt
3. Execute Programmable Blocks
4. Apply Final Edit
5. File output

## Difference from Category Identifier

- **Category Identifier**: Written in prompt content, replaces parts of the prompt
- **Category Template**: Configured in AdvancedPanel, defines the generation starting point

Both actually use the same parameter notation. Writing the same Category Identifier in a prompt and checking it achieves nearly the same result.

## Access

`AdvancedPanel > Category Template tab`

## Configurable Processing (6 stages)

- **Target**: Which prompts to target (`all`, `checked`, `allleaves`)
- **Filter**: Filter by conditions (`icon=File`, `tag=anime`)
- **Pick**: How many to select (`random=3`, `first=1`, `date=last_7days`)
- **Sort**: What order to arrange (`name=asc`, `date=desc`)
- **Join**: How to join (`,`, `\n`)
- **Edit**: Post-join processing (`TrimWhitespaceEachLine`, `RemoveDuplicateTags`)

## Two Modes

- **Parts Mode** (Recommended): Configure with 6 dropdowns. Easy with combobox presets.
- **All Mode** (Advanced): Write in one textbox.
