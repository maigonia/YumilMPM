# Category Template Practical Examples

Here are common configuration patterns for [Category Template](../02-Glossary/01-Category Template.md).

## Example 1: Pick 3 Random from Checked, Join with Comma

For categories like LoRA, when you want a different combination from checked prompts each time.

| Setting | Value |
|---------|-------|
| Target | `checked` |
| Pick | `random=3` |
| Join | `, ` |

Result: 3 prompts are randomly selected from checked prompts and joined with commas.

## Example 2: All Prompts in Name Order, Joined with Comma

For quality tag categories, when you want all checked prompts output in a fixed order.

| Setting | Value |
|---------|-------|
| Target | `checked` |
| Pick | `first=-1` (all) |
| Sort | `name=asc` |
| Join | `, ` |

## Example 3: Use Only Recently Added Prompts

| Setting | Value |
|---------|-------|
| Pick | `date=last_7days, random=2` |

Randomly selects 2 prompts from those added in the last 7 days.

## Example 4: Filter by Tag

When you want to target only prompts with a specific tag.

| Setting | Value |
|---------|-------|
| Filter | `tag=anime` |
| Pick | `random=1` |

## Example 5: Remove Duplicate Tags with Final Edit

When combining multiple prompts, the same tag may appear multiple times.

| Setting | Value |
|---------|-------|
| Target | `checked` |
| Pick | `random=3` |
| Join | `, ` |
| Final Edit | ON, `RemoveDuplicateTags` |

## Writing in All Mode

Parts Mode settings can be written together in All Mode.

**Example**: The same content as Example 1 in Parts Mode written in All Mode:

```
Target(checked).Pick(random=3).Join(, )
```

Example of a pre-made template:

```
Target(allleaves).Filter(icon=File).Pick(date=last_7days, random=3).Sort(date=desc).Join(, )
```

## Related

- [Category Template](../02-Glossary/01-Category Template.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Target](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/01-Target.md)
- [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Pick](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/03-Pick.md)
- [Sort](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/04-Sort.md)
- [Join](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/05-Join.md)
- [Edit](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/06-Edit.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Generation Rules](../../PromptTree/03-Tips/02-Changing Generation Rules.md)
