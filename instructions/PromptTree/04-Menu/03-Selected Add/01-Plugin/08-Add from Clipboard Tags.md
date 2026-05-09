# Add from Clipboard (Tags)

**Extract tags from clipboard and add as child prompts**

## When to Use

- When you want to break down image generation AI output tags (comma-separated) into individual prompts
- When you want to copy a comma-separated tag list and make 1 tag = 1 prompt

## What It Does

Extracts tags (comma-separated elements) from the clipboard text and adds each as a child prompt.

## How to Use

1. Copy a tag list (comma-separated) to the clipboard
2. Select the parent prompt
3. Select **PromptTree > Selected: Add > Add from Clipboard (Tags)** from the menu
4. Each tag is added as an individual child prompt

## Example

If the clipboard contains the following text:

```
1girl, red hair, blue eyes, smile
```

Four child prompts are created: "1girl", "red hair", "blue eyes", "smile"

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Tag](../../../../PromptBrowser/01-Basics/04-Tag.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
- [Add From Clipboard](06-Add from Clipboard Lines.md)
- [Add From Clipboard Whole](07-Add from Clipboard Whole.md)
