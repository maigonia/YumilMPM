# Add from Civitai URL

**Download model from Civitai URL and add**

## When to Use

- When you want to download a LoRA model from Civitai and immediately use it as a prompt
- When you want to complete model download and prompt creation at once

## What It Does

Downloads model files and related information from a Civitai model page URL and creates a LoRA prompt entry.

## Downloaded Files

- **Model file**: .safetensors file
- **Preview images**: Up to 4 images
- **Metadata file**: Text file containing model information
- **.civitai.info**: Detailed information from the Civitai API (JSON)

## How to Use

1. Copy the Civitai model page URL to the clipboard
   - Example: `https://civitai.com/models/12345`
   - Example: `https://civitai.com/models/12345?modelVersionId=67890`
2. Select the parent prompt
3. Select **PromptTree > Selected: Add > Add from Civitai URL** from the menu
4. The clipboard URL is automatically read
5. A dialog to select the save destination folder appears
6. A download progress dialog appears; wait for completion
7. A prompt entry is created and automatically selected

## Created Prompt Content

- **Name**: Downloaded file name (without extension)
- **Content**:
  ```
  // https://civitai.com/models/12345
  // (model:SD 1.5)
  <lora:model_name:1>,
  trigger_word
  ```
- **Memos**:
  - Model description, trigger word list, creator information, etc.
  - Raw data from .civitai.info (JSON)
- **Images**: Downloaded preview images (up to 4)
- **Base file**: Path to the downloaded .safetensors file

## Save Destination Folder Default

The initial folder is determined by the following priority:

1. The selected prompt's folderPath
2. The selected prompt's sourceFolderPath
3. The parent folder of the selected prompt's baseFilePath
4. The folder last used by this plugin

## About Civitai API Keys

To download models that require login (NSFW, early access, etc.), a Civitai API key is required.

### How to Set Up the API Key

1. Create an account at [Civitai](https://civitai.com/)
2. Generate a key in Settings → API Keys
3. Register the key in **GlobalSettings > API Key Settings** in this app

## Error Cases

- No valid Civitai URL in the clipboard
- The same file already exists in the category
- The same file already exists in the save destination folder
- The model has no .safetensors file
- Network error or API error

## Notes

- If the URL does not include a version ID, the latest version is downloaded
- The download folder is remembered as the default for next time

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
- [API Key Settings](../../../../GlobalSettings/04-Menu/09-API Key Settings.md)
- [URL Whitelist Manager](../../../../GlobalSettings/04-Menu/05-URL Whitelist Manager.md)
- [Image](../../../../PromptBrowser/01-Basics/01-Image.md)
