# Undo / Redo

Features for cancelling editing operations or restoring cancelled operations.

## Operation List

| Operation | Menu | Shortcut (Windows) | Shortcut (Mac) |
|-----------|------|---------------------|----------------|
| Undo | PromptEditor > Undo | Ctrl+Z | Cmd+Z |
| Redo | PromptEditor > Redo | Ctrl+Y | Cmd+Shift+Z |

## Notes

- Executing multiple times reverts further back (or restores more)
- Making new edits after undoing clears the redo history
- Switching prompts resets the history

## Related

- [PromptEditor](../03-Prompt Editor.md)
- [Undo](../../04-Menu/09-Undo.md)
- [Redo](../../04-Menu/10-Redo.md)
