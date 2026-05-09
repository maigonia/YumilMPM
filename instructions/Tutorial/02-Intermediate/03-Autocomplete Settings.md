# Autocomplete Settings

Display suggestions while typing in the Prompt Editor.

## Understanding with Examples

When typing a Category Identifier, entering `@@@_` shows category names (HairColor, EyeColor, Expression, Pose, etc.) as suggestions. Just select to input `@@@_HairColor_@@@`.

Also, with frequently used tags imported from CSV:
- Type "1gi" → "1girl" appears as suggestion
- Type "mast" → "masterpiece" appears as suggestion

This prevents typos and speeds up input.

## Adding User Candidates

**Method 1: Add manually**
1. Open `GlobalSettings > User Candidates Manager`
2. Create new list with "Add List" (set name and icon)
3. Select the list and add candidates one by one with "Add Candidate"
4. Enter candidate name, URL (optional), description (optional)

**Method 2: Import from CSV**
1. Prepare CSV file (one candidate per line)
2. Open `GlobalSettings > User Candidates Manager`
3. Create new list with "Add List"
4. Import CSV with "Import CSV"

You can set icons for each list, making it easy to categorize tags by type (character, quality, style, etc.).

## URL Jump Feature

If URL is associated with a candidate, press `Ctrl+Enter` when selecting to open that URL.
Example: Associate Civitai page URL with LoRA name candidate → Select candidate and Ctrl+Enter → Civitai page opens

Check detailed pages while entering LoRA trigger words.

## Access

- `PromptEditor > AutoComplete` (checkbox to toggle ON/OFF)
- User candidates import: `GlobalSettings > User Candidates Manager`
