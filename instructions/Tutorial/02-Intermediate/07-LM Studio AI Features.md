# LM Studio AI Features

Edit text using locally running AI (LM Studio).

## Understanding with Examples

To improve English prompts:
- Selected text: `girl, hair, eyes, smile`
- Instruction: "Expand these tags into detailed, high-quality prompt"
- Result: `1girl, long flowing blonde hair, sparkling blue eyes, gentle smile, soft lighting`

Translation from Japanese to English:
- Selected text: 夕焼けの海辺で佇む少女
- Instruction: "Translate to English prompt tags"
- Result: `girl standing, beach, sunset, ocean, golden hour lighting`

## Prerequisites

LM Studio running locally with server active (default: localhost:1234)

**How to start LM Studio server:**
1. Launch LM Studio app
2. Select "Power User" or "Developer" mode at the bottom of the screen
3. Click the green "Developer" icon in the left sidebar
4. Select a model to use
5. Click the toggle next to "Status: Stopped" to change it to "Status: Running"

## Where LM Studio AI Can Be Used

- `PromptTree > Selected > Suggest Tags with AI...` → Suggest tags from selected node content
- `PromptTree > Selected > Suggest Name with AI...` → Suggest name from selected node content
- `PromptTree > Checked Prompts > Bulk Suggest Tags with AI...` → Bulk suggest tags for checked prompts
- `PromptTree > Checked Prompts > Bulk Suggest Names with AI...` → Bulk suggest names for checked prompts
- `PromptTree > Checked Prompts > Edit Prompt Content with Plugins` → Select LMStudio AI plugin for bulk edit
- `PromptEditor > Edit SelectedText with Plugins > LMStudio Edit` → AI edit selected text in editor
- Category Identifier Edit command → `@@@_Category.Edit(LM=preset, "instruction")_@@@`
- Programmable Block LM function → AI call within QuickJS scripts

## Presets

- **default**: Balanced settings
- **creative**: Creative output (higher Temperature)
- **precise**: Accurate, consistent output (lower Temperature)
- **vision**: Describe images (requires compatible model)

## System Prompt vs Instruction

Presets can have a "System Prompt" configured. Understanding the difference between this and "Instruction" helps you use AI more effectively.

- **System Prompt**: Define AI's "role" or "persona" (preset setting)
  Example: "You are an SD/NAI prompt expert"
- **Instruction**: Specific "work request" (dialog or template)
  Example: "Translate to Japanese"

Actual API call image:
```
[System] You are a prompt expert. Always respond with English tags.
[User] Translate
Content: 夕焼けの海辺で佇む少女
```

## Usage Guidelines

- **System Prompt**: Preconditions you want always applied ("respond with English tags only", "no extra explanations", etc.)
- **Instruction**: Work content that changes each time ("translate", "add tags", etc.)

## Template Feature

Templates are sets of "preset" and "instruction". Save frequently used combinations ("translate to English", "expand tags", etc.) as templates for one-click access.

## Preset and Template Settings

You can create and edit presets and templates in `GlobalSettings > LM Studio Settings`.

**Presets Tab:** Add, edit, and delete presets
- Name: Preset name
- Temperature: Output randomness (0.0-2.0)
- Max Tokens: Maximum output tokens
- System Prompt: AI role definition
- Timeout: Timeout in milliseconds

**Templates Tab:** Add, edit, and delete templates
- Name: Template name
- Default Preset: Preset to use
- Instruction: Instruction text

## Using the Dialog

The Edit plugin dialog has a "Reference Text" textbox. This is reference text sent to AI along with the instruction, pre-filled with the text selected in the editor.

This text is freely editable. You don't need to use the selected text as-is.

## Important: Common Mistake

- Instruction: "Translate to Japanese"
- Reference Text: `1girl, blonde hair, blue eyes` (forgot to edit)
→ Unexpected translation result

**Correct Usage:**
- Instruction: "Translate to Japanese"
- Reference Text: `A girl standing on the beach at sunset` (edit before sending)
→ Expected translation result

Make it a habit to check Reference Text content before sending.
