# Changing Generation Rules

## Default Generation Rule

How checked prompts are handled during generation is determined by the "generation rule."

**Default**: One prompt is **randomly selected** from the checked prompts.

This is useful when you want to generate random variations from multiple options (e.g., hair color, pose, background).

## When You Want to Change the Rule

There are cases where you want to use a rule other than the default, such as outputting all checked prompts or filtering by specific conditions.

There are two ways to change the rule:

### Method 1: Change the Output Category Settings

In [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md), you can change the generation rule using [CategoryTemplate](../../AdvancedPanel/02-Glossary/01-Category%20Template.md) (in the Advanced Panel).

### Method 2: Use CategoryIdentifier Notation

In [Non-Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md), you can specify rules using [CategoryIdentifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) notation.

For example, you can retrieve all checked prompts by writing:

```
@@@_Style.Pick(first=-1)_@@@
```

## Commonly Used Rules

- Randomly select one (default)
- Output all checked prompts
- Output the first N prompts
- Randomly select N prompts

## Usage Examples

### Output All Character Traits

When you want to output all checked items such as hair color, eye color, and clothing, change to the "output all" rule.

### Randomly Select from Backgrounds

When you want to select a different background each time from multiple candidates, keep the default and check multiple backgrounds.

## Related

- [Check State](../01-Basics/01-Concepts/01-Understanding%20Check%20State.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
- [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md)
- [Output Category](../../CategoryTree/02-Glossary/01-Output%20Category.md)
- [PromptTree](../01-Basics/03-Prompt%20Tree%20Overview.md)
