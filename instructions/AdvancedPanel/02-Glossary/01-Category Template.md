## Category Template

**What Is It**: A mechanism for configuring how the "starting point (initial prompt)" for prompt generation is determined

**Background: Why Is It Needed**

To output prompts, you check the categories you want to output in the CategoryTree.
Checked categories select an "initial prompt" from their own PromptTree and begin output.

If Category Template is not configured, the following default rule applies:

> "Randomly select 1 prompt from the checked prompts in the PromptTree"

Use Category Template when you want to change this default.

**Understanding Through Examples**:

For example, suppose you have 100 prompts in a "LoRA" category.

Default (not configured):

- Randomly select 1 from checked prompts

With Category Template configured:

```
Target(allleaves).Filter(icon=File).Pick(random=3).Join(, )
```

- Randomly select 3 file-icon items from all leaf nodes and join with commas
- This becomes the "initial prompt"

**Key Points**:

- Category Template is **only effective for categories with output check enabled**
- Setting it on a category without output check enabled has no effect
- If the initial prompt contains Category Identifiers, substitution is executed afterward

**How to Access**:

```
AdvancedPanel > Category Template tab
```

**Processing Flow**:

```
1. Generate initial prompt from Category Template
2. Substitute Category Identifiers in the initial prompt
3. Execute Programmable Blocks
4. Apply Final Edit (global editing)
5. Output
```

**Difference from Category Identifier**:

| Item | Category Identifier | Category Template |
| ---- | ------------------- | ----------------- |
| Where written | In prompt content | Set in AdvancedPanel |
| Role | Substitutes part of the prompt | Defines the starting point for generation |
| Processing timing | After initial prompt generation | Executed first |
| Visibility | Shown in the prompt | Internal setting |

Category Template and Category Identifier actually use the same parameter notation method.
If you write a single identical Category Identifier in a prompt and check it, you can achieve nearly the same thing.
The difference is whether it's "a setting for determining the initial prompt" or "a string to substitute within a prompt."

**Configurable Processing (6 Stages)**:

| Process | Role | Examples |
| ------- | ---- | -------- |
| Target | Which prompts to target | `all`, `checked`, `allleaves` |
| Filter | Filter by conditions | `icon=File`, `tag=anime`, `name=character` |
| Pick | How many to select | `random=3`, `first=1`, `date=last_7days` |
| Sort | What order to arrange | `name=asc`, `date=desc` |
| Join | How to combine | `,`, `\n` |
| Edit | Post-join processing | `TrimWhitespaceEachLine`, `RemoveDuplicateTags` |

**Two Modes**:

Parts Mode (recommended):

- Set each process individually with 6 dropdowns
- Easy configuration with combo box presets

All Mode (advanced):

- Write all processes in a single text box
- Example: `Target(allleaves).Filter(icon=File).Pick(random=3).Join(, )`

## Related

- [Category Templateタブ](../01-Basics/01-Category%20Template%20Tab.md)
- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Advanced Panel](../01-Basics/07-What%20Is%20Advanced%20Panel.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Target](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/01-Target.md)
- [Filter](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md)
- [Pick](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/03-Pick.md)
- [Sort](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/04-Sort.md)
- [Join](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/05-Join.md)
- [Edit](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/06-Edit.md)
- [Final Edit](05-Final%20Edit.md)
- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Generation Rules](../../PromptTree/03-Tips/02-Changing%20Generation%20Rules.md)
