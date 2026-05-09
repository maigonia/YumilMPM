# Create Yumil Parser Block

**Create Yumil Parser Block**

## When to Use

- When you want to send reference image paths to ComfyUI via ControlNet or IPAdapter
- When you want to send parameters (strength, mode, etc.) along with image paths
- When you want to combine file paths, parameters, and text into a single block for parsing by ComfyUI's Yumil Prompt Parser node

## What It Does

Converts text to `###_Path().Value().Text()_###` parser block format. This format is parsed by ComfyUI's Yumil Prompt Parser node.

You can freely combine three elements — Path (paths), Value (parameters), and Text (text) — and omit any that are not needed.

## Input Format

Input follows a fixed line order. Each line is optional; an empty line means the element is omitted.

```
Line 1: Paths (comma-separated for multiple)
Line 2: Parameters (key=value format, comma-separated)
Line 3+: Text (multi-line supported)
```

## Output Examples

### All Elements

Input:
```
C:\Images\sample.png,C:\Images\ref.png
strength=0.8,mode=ipadapter
1girl, solo, blonde hair, smile
```

Output:
```
###_Path(C:\Images\sample.png,C:\Images\ref.png).Value(strength=0.8,mode=ipadapter).Text(1girl, solo, blonde hair, smile)_###
```

### Path and Text Only (Value Omitted)

Input:
```
C:\Images\sample.png

1girl, solo, blonde hair, smile
```

Output:
```
###_Path(C:\Images\sample.png).Text(1girl, solo, blonde hair, smile)_###
```

### Path Only

Input:
```
C:\Images\sample.png
```

Output:
```
###_Path(C:\Images\sample.png)_###
```

## How to Use

1. Enter or select the content to convert in the editor
2. Select **Edit SelectedText with Plugins > Create Yumil Parser Block** from the menu
3. The selected text is converted to `###_Path().Value().Text()_###` format

## Using with Category Identifier

Can also be used with [Category Identifier](../../02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) Edit syntax:

```
@@@_Category.Edit(CreateYumilParserBlock)_@@@
```

## Notes

- On the ComfyUI side, a single prompt can contain multiple `###_..._###` blocks, and each one is recognized individually
- The [WD14 Tagger](14-WD14%20Tagger.md) dialog also has a "Format for ComfyUI Yumil Parser" checkbox that automatically applies Path and Text conversion
- Omitted elements are excluded from the output (empty `.Value()` etc. will not appear)

## Download

Yumil Prompt Parser is included in **ComfyUI Yumil MPM**.

- [ComfyUI Yumil MPM (GitHub)](https://github.com/maigonia/comfyui-yumil-mpm)

## Related

- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [WD14 Tagger](14-WD14%20Tagger.md)
- [Add From WD14](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/19-Add%20from%20WD14.md)
- [Category Identifier](../../02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md)
