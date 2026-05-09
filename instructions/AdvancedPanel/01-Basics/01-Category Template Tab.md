# Category Template Tab

This is the per-category generation template settings tab, displayed in Category scope.

For the concept of [Category Template](../02-Glossary/01-Category Template.md), please see the glossary. Here is how to operate the tab.

## Two Input Modes

Switch input modes with the radio buttons at the top of the tab.

### Parts Mode (Recommended)

Set each process individually with 6 dropdowns.

```
┌────────────────┐  ┌────────────────┐
│ Target         │  │ Filter         │
├────────────────┤  ├────────────────┤
│ Pick           │  │ Sort           │
├────────────────┤  ├────────────────┤
│ Join           │  │ Edit           │
└────────────────┘  └────────────────┘
```

Each dropdown is an editable combo box. You can select from the list or type text directly.

### All Mode (Advanced)

Write all processes in a single text box. This is a one-line format combining all 6 items from Parts Mode.

## Clear Button

Resets all dropdowns to their default values (the first item in each list).

## Final Edit

A feature for configuring post-generation processing. Displayed in a yellow area.

1. Enable by checking the checkbox **ON**
2. Select a plugin from the dropdown (e.g., `TrimWhitespaceEachLine`, `RemoveDuplicateTags`)
3. If the LM Studio plugin is enabled, commands like `LM=default, summarize` can also be used

Final Edit is executed after all 6-stage pipeline processing is complete.

## Editing ComboBox Lists

The choices for each combo box can be edited from the menu under **Category Template > ComboBox List Setting**. Adding frequently used setting values to the list is convenient.

## Related

- [Category Template](../02-Glossary/01-Category Template.md)
- [Advanced Panel](07-What Is Advanced Panel.md)
- [Final Edit](../02-Glossary/05-Final Edit.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Target](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/01-Target.md)
- [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Pick](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/03-Pick.md)
- [Sort](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/04-Sort.md)
- [Join](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/05-Join.md)
- [Edit](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/06-Edit.md)
