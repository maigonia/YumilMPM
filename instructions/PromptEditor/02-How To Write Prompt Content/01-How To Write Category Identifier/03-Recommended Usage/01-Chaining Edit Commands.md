# Chaining Edit Commands

The [Edit](../02-Action%20Commands/06-Edit.md) command can be stacked to apply multiple editing processes in sequence.

## Basic Chaining

```
@@@_Category.Edit(TrimWhitespaceEachLine).Edit(RemoveDuplicateTags)_@@@
```

> 1. Apply TrimWhitespaceEachLine
> 2. Apply RemoveDuplicateTags

## Chaining LM Studio (Advanced)

Using [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM%20Studio.md) in sequence enables multi-stage AI processing.

### Summarize then Translate

```
@@@_Content.Edit(LM=summarize, summarize in 3 lines).Edit(LM=translate, translate to English)_@@@
```

> Summarize a long Japanese text, then translate to English

### Generate then Proofread

```
@@@_Ideas.Edit(LM=creative, write a story from this setting).Edit(LM=editor, fix typos and errors)_@@@
```

> Create content, then proofread it

### AI Extraction then Format with Regular Plugin

```
@@@_RawData.Edit(LM=analyze, extract tags and list them).Edit(RemoveDuplicateTags)_@@@
```

> Extract with AI, then remove duplicates with a regular plugin

### Iterative Refinement

```
@@@_Draft.Edit(LM=precise, make it more specific).Edit(LM=precise, make it more concise)_@@@
```

> Refine multiple times with the same preset

## Notes

- Chaining LM calls increases API calls, so processing time will be longer
- Presets must be created in advance in [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)

## Batch Processing Recommendation

If chaining LM calls results in long processing times, batch processing using [Timer Generation](../../../../PromptGeneration/04-Menu/03-Timer%20Generation/README.md) and [Add From Generated Output](../../../../PromptTree/04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md) is recommended.

1. Set up a capture target prompt with [Add From Generated Output](../../../../PromptTree/04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md)
2. Start automatic generation with [Timer Generation](../../../../PromptGeneration/04-Menu/03-Timer%20Generation/README.md)
3. Generated results are automatically accumulated as child prompts
4. Use later with [Generation On Demand](../../../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/README.md)

This allows you to run time-consuming LM processing in advance and stock the results.

## Related

- [Edit](../02-Action%20Commands/06-Edit.md)
- [Category Identifier](../README.md)
- [LM Studio](../../../../GlobalSettings/02-Glossary/01-LM%20Studio.md)
- [LM Studio Settings](../../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
- [Timer Generation Start](../../../../PromptGeneration/04-Menu/03-Timer%20Generation/01-Timer%20Generation%20Start.md)
- [Add From Generated Output](../../../../PromptTree/04-Menu/03-Selected%20Add/02-Add%20From%20Generated%20Output.md)
- [Plugin](../../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
