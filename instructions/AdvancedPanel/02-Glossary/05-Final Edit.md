## 2. Final Edit

**What Is It**: A feature that applies editing processing to each category's final output. It is an independent final editing step, separate from Category Template and Category Identifier.

**Background: Why Is It Needed**

The Edit processing of Category Template and Category Identifier has important limitations:

- CI's Edit processing only acts on the result of that substitution
- It does not affect CIs newly found after substitution
- Each CI is processed independently, and results are not carried over to the next CI

In other words, CI/CT Edit cannot edit the "entire final output."

**Understanding Through Examples**:

The problem arises in **hierarchical structures**. This is when prompts expanded by CI contain further CIs within them.

For example, suppose a prompt in the Character category is defined as follows:

```
girl, @@@_Hair_@@@, smile
```

Initial prompt:

```
@@@_Character.Edit(RemoveDuplicateTags)_@@@
```

Processing flow:

1. Character CI is processed → expanded to `girl, @@@_Hair_@@@, smile`
2. Edit(RemoveDuplicateTags) is executed (no duplicates at this point)
3. Child CI `@@@_Hair_@@@` is processed → substituted with `long hair, blonde`
4. Final result: `girl, long hair, blonde, smile`

What if the Hair CI result contained `girl`?
→ `girl` could appear duplicated in the final result
→ But the parent CI's Edit has already been executed, so the duplication is not removed

**Key Points**:

- Category Template is always executed first
- If the initial prompt contains even one CI, it becomes a hierarchical structure
- Child CIs are executed after the parent CI/CT Edit
- Therefore, Edit does not reach child CI results

Final Edit allows you to apply editing to the entire final output after all hierarchical processing is complete.

**Processing Flow (Review)**:

```
1. Generate initial prompt from Category Template
2. Substitute Category Identifiers in the initial prompt (each CI processed independently)
3. Execute Programmable Blocks
4. Apply Final Edit (global editing) ← Edit the entire output here
5. File output
```

**How to Access**:

```
AdvancedPanel > Category tab > Final Edit checkbox
```

**Use Cases**:

- Apply duplicate tag removal to the final output
- Apply whitespace cleanup to the entire output
- Sort tags against the final result
- Format output results from all categories together

**Difference from CI/CT Edit**:

| Item | CI/CT Edit | Final Edit |
| ---- | ---------- | ---------- |
| Target | Each substitution's result | Entire final output |
| Processing timing | Immediately after substitution | After all processing is complete |
| Scope | Independent, limited | Entire output |

---

## Related

- [Category Templateタブ](../01-Basics/01-Category Template Tab.md)
- [Category Template](01-Category Template.md)
- [Advanced Panel](../01-Basics/07-What Is Advanced Panel.md)
- [Generation](../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [Edit](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/06-Edit.md)
- [Plugin](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Programmable Block](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/README.md)
