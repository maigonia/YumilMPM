# Google Translate

**Google Translate**

## When to Use

- When you want to translate a prompt to another language
- When you want to convert an English prompt to Japanese
- When you want to convert text between multiple languages

## What It Does

Translates selected text to another language using Google Translate. It supports automatic source language detection and can translate to any other language.

## How to Use

1. Select the text to translate
2. Select **Edit SelectedText with Plugins > Google Translate** from the menu
3. A dialog appears (see below for details)
4. Click **Translate** (or **Enter**)
5. The selected text is replaced with the translation result

## Dialog Usage

| Item | Description |
|------|-------------|
| **Source Language** | Select the source language. Default is "Auto Detect" |
| **Target Language** | Select the target (translation) language. Default is "English" |

### Supported Languages

| Code | Language |
|------|----------|
| auto | Auto Detect |
| en | English |
| ja | Japanese |
| zh-CN | Chinese (Simplified) |
| zh-TW | Chinese (Traditional) |
| ko | Korean |
| fr | French |
| de | German |
| es | Spanish |
| pt | Portuguese |
| ru | Russian |
| it | Italian |
| ar | Arabic |
| hi | Hindi |
| th | Thai |
| vi | Vietnamese |
| nl | Dutch |
| pl | Polish |
| sv | Swedish |
| tr | Turkish |

## Notes

- When translating consecutively, if [Rate Limiting](../../../GlobalSettings/02-Glossary/06-Rate%20Limiting.md) is exceeded, a modal dialog appears with a countdown of remaining seconds and auto-retries when the countdown reaches 0. Cancel aborts, and **Force Reset** clears the rate-limit history and retries immediately. Delay time and request count limits can be adjusted from the gear icon in **Global Settings > EditPlugin Settings** (default: 3000ms delay, 20 requests/5 minutes)
- If no text is selected, all text in the editor becomes the translation target
- If an error occurs, the error message and original text are displayed

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [Plugin](../../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Edit SelectedText with Plugins](../../01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [Rate Limiting](../../../GlobalSettings/02-Glossary/06-Rate%20Limiting.md)
- [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
