# Suggest Tags with AI

**AI Tag**

## When to Use

- When you want to automatically assign appropriate tags to a prompt
- When you want to reduce the effort of manual tagging

## What It Does

Uses AI to automatically suggest tags appropriate for the content of the selected prompt.

## How to Use

1. Select the prompt you want to tag
2. Select **PromptTree > Selected > Suggest Tags with AI...** from the menu
3. A dialog opens

### Dialog Operations

1. **Select a preset** (optional): Choose a preset from the dropdown at the top
2. **Edit in the editor** (optional): Edit the template in the left editor
3. **Click the execute button**: Click the "Execute" button in the right panel
4. **Review the suggested tags**: A tag list appears in the right panel
5. **Select tags to apply**: Use checkboxes to select/deselect tags you want to apply
6. **Apply**: Click the "Apply" button

### Dialog Layout

- **Left side (Editor)**: Display and edit template text
- **Right side (Result Panel)**: Suggested tag list and execute button
- **Preset Toolbar**: Preset selection, save, and delete

### Preset Management

- **Save**: Overwrite save the edited code to the current preset
- **Save As**: Save as a new preset
- **Delete**: Delete the selected preset (default cannot be deleted)

## Notes

- When calling an AI API within a programmable block, the [API Key Settings](../../../GlobalSettings/04-Menu/09-API%20Key%20Settings.md) corresponding to the AI being used is required
- When using [LM Studio](../../../GlobalSettings/02-Glossary/01-LM%20Studio.md), the server must be running
- The suggested tags can be applied after review
- Tags are added to existing tags (not overwritten)
- The last used preset is remembered per category

### How Editor Content Is Processed

The text entered in the editor is used directly as the output.

**Basic behavior:**
- The text in the editor is used as-is as the result
- If a [Programmable Block](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) (`@@@_..._@@@`) is included, that portion is replaced with the block's execution result, and the surrounding text remains unchanged
- Example: `preceding text` + `@@@_..._@@@` + `following text` → `preceding text` + `block output` + `following text`
- It also works as plain text without using programmable blocks

**Output processing:**
The final text is split by **commas (,) or newlines**, and each part is recognized as a tag.

- Example: Plain text `"fantasy, battle, serious"` → 3 tags
- Example: Plain text `"fantasy\nbattle\nserious"` → 3 tags

**Default template example:**

```javascript
@@@_
// === Default Tag Suggester ===
// Suggests tags for a chunk using LM Studio.
// Uses tag names only (env.globalTags) to keep context small.
//
// Customize tips:
//   - For richer tag info, use env.tagDefinitions (includes descriptions)
//   - For category-scoped tags, use env.getCategory("Name").tags
//   - Adjust the number of suggested tags in the instruction below

// --- Gather chunk info ---
const chunk = env.chunk;
const sections = [];
sections.push("[Name] " + chunk.name);
if (chunk.treepath) sections.push("[Path] " + chunk.treepath);
sections.push("[Content]\n" + chunk.content);
if (chunk.tags.length > 0) sections.push("[Current Tags] " + chunk.tags.join(", "));
if (chunk.memos.length > 0) sections.push("[Memos]\n" + chunk.memos.join("\n"));

// --- Available tags in the project (names only, lightweight) ---
const allTags = env.globalTags;
if (allTags.length > 0) sections.push("[Available Tags]\n" + allTags.join(", "));

// --- Instruction ---
const instruction =
  "You are a tag classifier for creative prompt materials.\n" +
  "Suggest tags for the chunk below.\n" +
  "Rules:\n" +
  "- STRONGLY prefer tags from [Available Tags]\n" +
  "- Only suggest a new tag if no existing tag fits\n" +
  "- Do NOT repeat tags from [Current Tags]\n" +
  "- Suggest 3-8 tags\n" +
  "- Output ONLY comma-separated tag names, nothing else";

const result = await env.LMEDIT("tag-suggest", instruction, sections.join("\n\n"));
env.OUTPUT(result);
_@@@
```

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [Tag](../../../PromptBrowser/01-Basics/04-Tag.md)
- [PromptTree](../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM%20Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM%20Studio/01-Settings.md)
- [Suggest Name with AI](09-Suggest%20Name%20with%20AI.md)
- [Bulk Suggest Tags with AI](../05-Checked/05-Bulk%20Suggest%20Tags%20with%20AI.md)
- [Tag Manager](../../../GlobalSettings/04-Menu/06-Tag%20Manager.md)
- [Programmable Block](../../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
