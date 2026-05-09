# Move under Selected
**Move under Selected**

## When to Use
- When you want to move multiple checked prompts at once
- When you want to significantly reorganize the tree structure

## What It Does
Moves all checked prompts as children of the selected prompt. They are removed from their original locations after the move.

## How to Use
1. Check the prompts you want to move
2. Select the destination prompt
3. Select **PromptTree > Checked > Move under Selected** from the menu
4. Review the preview in the confirmation dialog and click **Execute**

## Notes
- Not available when no prompts are checked
- Not available when no prompt is selected
- Only checked descendants are moved. Unchecked descendants will not be moved and will be deleted
- When there are unchecked descendants, the confirmation dialog displays the items to be deleted in red as a warning
- To move all descendants, check all of them first
- If the destination is a descendant of the source, a warning is displayed and the operation cannot be executed

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Check State](../../01-Basics/01-Concepts/01-Understanding Check State.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Cut](../../../PromptEditor/04-Menu/05-Cut.md)
- [Copy under Selected](01-Copy under Selected.md)
- [Paste](../../../PromptEditor/04-Menu/06-Paste.md)
