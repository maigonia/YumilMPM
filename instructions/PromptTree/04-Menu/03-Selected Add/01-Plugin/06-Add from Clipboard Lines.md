# Add from Clipboard (Lines)

**Add from clipboard line by line**

## When to Use

- When you want to batch import a list written in another tool or notepad
- When you want to turn newline-separated text into individual prompts

## What It Does

Splits the clipboard text by lines and adds each line as a child prompt.

## How to Use

1. Copy multi-line text to the clipboard
2. Select the parent prompt
3. Select **PromptTree > Selected: Add > Add from Clipboard (Lines)** from the menu
4. Each line is added as an individual child prompt

## Example

If the clipboard contains the following text:

```
red hair
blue eyes
white dress
```

Three child prompts are created, with each line's text in the content.

## Notes

- Empty lines are ignored
- Prompt names are auto-generated from the line content (truncated if long)

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [PromptTree](../../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [Add From Clipboard Tags](08-Add%20from%20Clipboard%20Tags.md)
- [Add From Clipboard Whole](07-Add%20from%20Clipboard%20Whole.md)
- [Add From Text File](09-Add%20from%20Text%20File%20Lines.md)
- [Paste](../../../../PromptEditor/04-Menu/06-Paste.md)
