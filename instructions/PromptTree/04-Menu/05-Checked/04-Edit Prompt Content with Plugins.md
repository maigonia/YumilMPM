# Edit Prompt Content with Plugins

**Edit Prompt Content with Plugins**

## When to Use

- When you want to batch process the content of multiple prompts
- When you want to use text transformation plugins for bulk processing
- When you want to apply search and replace to multiple prompts
- When you want to batch edit prompt content using AI

## What It Does

Batch edits the content of all checked prompts using plugins. You can preview changes before applying.

## How to Use

1. Check the prompts you want to edit
2. Select **PromptTree > Checked > Edit Prompt Content with Plugins** from the menu
3. A dialog opens

### Dialog Operations

1. **Select a plugin**: Choose the plugin to use from the dropdown
2. **Run preview**: Click the "Run Preview" button
3. **Settings dialog**: Some plugins display a settings screen (first time only)
4. **Review changes**: Check changed prompts in the left list, compare before/after in the right side
5. **Apply**: Click "Apply Changes" to batch apply changes

## Dialog Layout

The dialog has a 2-panel layout:

| Panel | Content |
| --- | --- |
| **Left (Chunk List)** | Checked prompts list and change state |
| **Right (Preview)** | Before/after comparison for selected prompt |

### Change State Display

- **[Modified]** (green): Prompts with changes
- **[No Change]** (gray): Prompts without changes

## Available Plugins

### Text Transformation Plugin Examples

| Plugin Name | Function |
| --- | --- |
| **Wrap in Weight Syntax** | Convert prompt weights to (text:1) format |
| **Trim Whitespace** | Remove leading/trailing whitespace |
| **Create Dynamic Prompts** | Convert to DynamicPrompts format |
| **Normalize Prompt Format** | Normalize prompt format |
| **Remove Duplicate Lines** | Remove duplicate lines |
| **Remove Duplicate Tags** | Remove duplicate tags |
| **Sort Lines Alphabetically** | Sort lines alphabetically |
| **Escape as JS String** | Escape for JavaScript string |

### Special Plugins

| Plugin Name | Function | Settings Dialog |
| --- | --- | --- |
| **Replace Text** | Search and replace (regex supported) | Yes |
| **LM Studio Edit** | Edit with local LLM | Yes |
| **Google Translate** | Translate text with Google Translate | Yes |
| **Use Name as Content** | Set prompt name as content | - |

## Replace Text Plugin

A plugin that performs search and replace.

### Settings

- **Search**: The string to search for
- **Replace**: The replacement string
- **Use Regex**: Whether to use regular expressions

### Usage Examples

- Replace commas with newlines: `Search: ,` → `Replace: \n`
- Remove specific tag: `Search: masterpiece,` → `Replace: ` (empty)
- Remove numbers with regex: `Search: \d+` → `Replace: ` (Use Regex ON)

## LM Studio Edit Plugin

Edits prompt content using a locally running LLM.

### Prerequisites

- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md) must be installed and the server must be running
- The server URL must be configured in [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)

### Processing Flow

1. Select a preset or instruction in the settings dialog
2. Each prompt is processed sequentially by the LLM
3. Progress is displayed during processing (cancellable)

## Google Translate Plugin

Translates prompt content to another language using Google Translate.

### Settings

- **Source Language**: Source language (default: Auto Detect)
- **Target Language**: Target language (default: English)

### Processing Flow

1. Select source and target languages in the settings dialog
2. Each prompt is translated sequentially
3. When [Rate Limiting](../../../GlobalSettings/02-Glossary/06-Rate Limiting.md) is exceeded, a modal dialog opens with a countdown of remaining seconds (default: 3000ms delay, 20 requests/5 minutes)

### About Rate Limiting

Since Google Translate is an external service, sending too many requests in a short time may result in blocking. Rate limiting provides protection through two mechanisms:

- **Request delay**: Minimum delay required between consecutive requests (default 3 seconds)
- **Window limit**: Number of requests within a time window (default 20 requests/5 minutes)

When the limit is exceeded, the modal dialog displays a countdown and auto-retries when it reaches 0. Cancel aborts the bulk operation, and **Force Reset** clears the rate-limit history and retries immediately (useful when you intentionally want to skip the wait). Settings can be changed from the ⚙ icon in **Global Settings > EditPlugin Settings**.

## Processing Details

### Preview Processing

1. Get the selected plugin
2. Display settings dialog if needed (once only)
3. Execute plugin for each prompt
4. Save before/after content
5. Display results in preview

### Apply Processing

- When "Apply Changes" is clicked, only **prompts with changes** are updated
- Prompts without changes are skipped
- On completion, "X chunks updated successfully" is displayed

### Error Handling

- Processing continues even if errors occur during plugin execution
- Prompts with errors retain their original content
- Error count is displayed in the status bar

### Cancel

- Asynchronous processing (LM Studio, Google Translate, etc.) can be cancelled midway
- On cancellation, processed results are retained

## Notes

- Not available when no prompts are checked
- Plugins disabled in settings are not shown in the dropdown
- Plugin enable/disable can be changed in **GlobalSettings > EditPlugin Settings**
- The settings dialog is only shown during the first prompt processing; the same settings are reused afterward

## Related

- [Prompt](../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [Check State](../../01-Basics/01-Concepts/01-Understanding Check State.md)
- [PromptTree](../../01-Basics/03-Prompt Tree Overview.md)
- [Plugin](../03-Selected Add/01-Plugin/README.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [Edit SelectedText with Plugins](../../../PromptEditor/01-Basics/01-Features/06-Edit SelectedText with Plugins.md)
- [LM Studio](../../../GlobalSettings/02-Glossary/01-LM Studio.md)
- [LM Studio Settings](../../../GlobalSettings/04-Menu/04-LM Studio/01-Settings.md)
- [Rate Limiting](../../../GlobalSettings/02-Glossary/06-Rate Limiting.md)
- [PromptEditor](../../../PromptEditor/01-Basics/03-Prompt Editor.md)
