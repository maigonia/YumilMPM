# Add from JSON File

**Import chunks with their tree structure from a JSON file**

## When to Use

- When you have generated chunk definitions in JSON format with an external tool or script and want to import them in bulk
- When you want to manage nested prompt tree structures in a single file
- When you also want to import accompanying information such as tags, memos, and image paths

## What It Does

Selects a JSON file in a simple format and imports the defined chunks into the tree. Nested `children` are also expanded recursively.

## How to Use

1. Select the parent prompt
2. Select **PromptTree > Selected: Add > Add from JSON File** from the menu
3. Choose a `.json` file in the file selection dialog
4. The contents are validated and, if there are no problems, the chunks are added

## JSON Format

The root must be an array, and each entry has the following fields:

- `name` (required, string): Chunk name
- `content` (required, string): Prompt body
- `displayType` (optional): Only `"normal"` or `"group"`. Anything else falls back to `normal`
- `tags` (optional, string array): Tags
- `memos` (optional, string array): Memos
- `imagePaths` (optional, string array): Image file paths
- `memoPaths` (optional, string array): Memo file paths
- `sourceFilePath` (optional, string): Source file path reference
- `sourceFolderPath` (optional, string): Source folder path reference
- `children` (optional, array): Nested child chunks

## Notes

- Internal-use fields such as `baseFilePath`, `folderPath`, `isFile`, `isFolder`, and `id` cannot be specified (validation error)
- If validation fails, nothing is added and an error message is shown
- If a name collides with a sibling chunk, it is automatically uniquified

## Related

- [Add From Text File](09-Add from Text File Lines.md)
- [Add From File System](13-Add from File System.md)
- [Plugin](README.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
