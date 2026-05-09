# Add From FileSystem

If you're managing many files like LoRA files, you can auto-generate a tree from existing folder structures instead of building manually.

`PromptTree > Selected: Add > Add from File System`

## Features

- Converts folder/file structure under specified folder to Prompt Tree
- Specify any extension as base file and collect related information
- Can optionally import memo and image information together

## Example: .safetensors files

The following is an example when base file extension is set to .safetensors:

- my_lora.safetensors → Base file (registered as tree node)
- my_lora.txt → Extracted as prompt string
- my_lora.png → Imported as related image
- my_lora.json → Imported as memo information

The information extracted as prompt content can be flexibly configured from related files or base file names.

## Re-import Behavior

- When the same base file path is found in subsequent Add From FileSystem operations, the add process is skipped
- However, if you want to update only content/memo/images, you can turn off skip mode for each item
- When skip mode is off, current content/memo/images are deleted and new information is fetched from scratch
- To update only specific items, turn off skip mode for only those items
- Example: If images have increased, turning off only image skip mode will process only image additions

## Important Notes

- Moving files or folders changes the path, causing tracking to be lost
- Since the design relies on file paths, strongly recommend deciding folder location and structure beforehand
- Prepare necessary files (like Civitai info files) before importing
- Prompts added via Add From FileSystem cannot have their icons changed (file/folder icons are forced)
