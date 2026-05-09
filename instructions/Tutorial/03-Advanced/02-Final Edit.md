# Final Edit

A feature that applies edit processing to the final output of each category. It is an independent final editing step, separate from Category Template and Category Identifier.

## Why Needed

Category Template and Category Identifier Edit processing have important constraints:

- CI's Edit processing only affects that replacement result
- It does not affect child CIs expanded after replacement
- Parent CI's Edit executes before child CIs are processed

In other words, CI/CT Edit cannot edit the "entire final output".

## Understanding with Examples

The problem occurs with hierarchical structures - when a CI's expanded result contains another CI inside it.

For example, if a prompt in the Character category is defined as:
`girl, @@@_Hair_@@@, smile`

Initial prompt:
`@@@_Character.Edit(RemoveDuplicateTags)_@@@`

Processing flow:
1. Character CI is processed → expands to `girl, @@@_Hair_@@@, smile`
2. Edit(RemoveDuplicateTags) executes (no duplicates at this point)
3. Child CI `@@@_Hair_@@@` is processed → replaced with `long hair, blonde`
4. Final result: `girl, long hair, blonde, smile`

What if Hair CI's result contained `girl`?
→ `girl` would appear duplicated in the final result
→ But parent CI's Edit has already executed, so duplicates are not removed

## Important

- Category Template always executes first
- If the initial prompt contains even one CI, it becomes a hierarchical structure
- Parent CI/CT's Edit executes before child CIs are processed
- Therefore, Edit cannot affect child CI results

With Final Edit, you can apply editing to the entire final output after all hierarchy levels complete.

## Access

`AdvancedPanel > Category tab > Final Edit checkbox`

## Use Cases

- Apply duplicate tag removal to final output
- Apply whitespace cleanup to entire output
- Sort tags on final result
- Format all hierarchy level outputs together

## Difference from CI/CT Edit

- **CI/CT Edit**: Only affects own replacement result, does not reach child CIs
- **Final Edit**: Applies to final output after all hierarchy levels complete
