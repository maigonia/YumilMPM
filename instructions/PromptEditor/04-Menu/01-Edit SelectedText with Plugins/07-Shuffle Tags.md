# Shuffle Tags

**Shuffle Tags**

## When to Use

- When image generation keeps producing similar outputs from the same prompt
- When introducing variation to generated images by changing tag order is desired
- When shuffling a multi-line tag list as a whole is needed

## What It Does

Randomly reorders comma-separated tags to create variation in image generation results. Even a simple reorder shifts which elements the model emphasizes, which can change the overall tendency of the output.

- Performs both **within-line tag shuffle** and **line order shuffle** across the sub-range in a single pass
- `//` comment lines and blank lines act as **anchors** that stay in place (they divide the shuffle into sub-ranges)
- Trailing comma presence is pinned to the **line position** (so patterns like "no trailing comma on the last line only" are preserved)
- Dynamic Prompts `{A|B|C}` blocks are handled specially:
  - Each `|`-separated section's **position is fixed** (the A/B/C order never changes)
  - Only the comma-separated tags inside each section are shuffled
  - Block-level count prefixes like `{N$$ ...}` and option-level weight prefixes like `{0.1::A|...}` are preserved in place
  - Range-count variants `{1-2$$ ...}` / `{-2$$ ...}` / `{1-$$ ...}` are preserved as a unit
  - Custom-separator form `{N$$ sep $$ ...}` keeps the `sep` part intact (e.g. `{3$$ and $$A|B|C}`)

## How to Use

1. Select the target text
2. Select **Edit SelectedText with Plugins > Shuffle Tags** from the menu
3. Tag order and line order are shuffled

## Examples

### Simple Comma-Separated

- Input: `1girl, smile, outdoor, cafe, sunny day`
- Output example: `cafe, sunny day, 1girl, smile, outdoor`

### Multi-line (one tag per line)

- Input:
  ```
  1girl,
  smile,
  outdoor
  ```
- Output example:
  ```
  smile,
  outdoor,
  1girl
  ```
  The trailing comma presence is tied to the **line position**, so the "no trailing comma on the last line" shape is preserved.

### Across Comment and Blank Lines

- Input:
  ```
  // quality
  masterpiece, best quality

  // subject
  1girl, smile, outdoor
  ```
- Output example: `//` comment lines and blank lines stay in place; only content within each sub-block is shuffled

### Dynamic Prompts

- Input: `{2$$ a,b|c,d|e,f}`
- Output example: `{2$$ b,a|d,c|f,e}`
  Section positions and the `2$$` prefix are fixed; only tags inside each section are shuffled.
- Weighted form like `{0.1::a,b|0.2::c,d}` keeps each `0.1::` / `0.2::` prefix in place and shuffles only the inner tags.
- Range count: `{1-2$$ a,b|c,d|e,f}` → `{1-2$$ b,a|d,c|f,e}` (`1-2$$` is preserved).
- Custom separator: `{3$$ and $$a,b|c,d|e,f}` → `{3$$ and $$b,a|d,c|f,e}` (`3$$ and $$` is preserved).

## Notes

- The shuffle algorithm is Fisher-Yates (Durstenfeld), producing a uniform distribution
- Because `//` comment lines and blank lines act as anchors, shuffling can be applied while keeping headers or section dividers in place
- Also available in [Category Identifier](../../02-How To Write Prompt Content/01-How To Write Category Identifier/README.md) Edit syntax:
  ```
  @@@_CategoryName.Edit(ShuffleTags)_@@@
  ```

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Remove Duplicate Tags](06-Remove Duplicate Tags.md)
- [Sort Lines Alphabetically](08-Sort Lines Alphabetically.md)
- [Create Dynamic Prompts from Lines](03-Create Dynamic Prompts from Lines.md)
- [Category Identifier](../../02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
