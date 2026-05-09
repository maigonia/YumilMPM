# Add from Text File (Whole)

**Add entire text files as child prompts**

## When to Use

- When you want to batch import multiple text files
- When you want to save the entire content of a file as a single prompt
- When you want to import a large number of text files output by a ComfyUI prompt creation workflow
- When you want to import config files or long text as-is

## What It Does

Selects multiple text files and adds each file's entire content as one child prompt. 1 file = 1 prompt.

## How to Use

1. Select the parent prompt
2. Select **PromptTree > Selected: Add > Add from Text File (Whole)** from the menu
3. A file selection dialog appears
4. Select text files (multiple selection possible)
5. Each file's entire content is added as an individual child prompt

## Supported File Formats

The following extensions are supported:

- `.txt` - Text file
- `.json` - JSON file
- `.csv` - CSV file
- `.md` - Markdown file
- `.xml` - XML file
- `.yaml` / `.yml` - YAML file
- `.toml` - TOML file
- `.ini` - INI file
- `.cfg` - Config file
- `.log` - Log file

Selecting "All Files" in the dialog allows other file types as well.

## Prompt Name Determination

- The file name without extension becomes the prompt name
  - Example: `character_description.txt` → Prompt name: `character_description`
- If a prompt with the same name already exists, a number is automatically appended

## Processing Details

- **Multiple file selection**: Multiple files can be selected and imported at once
- **Empty file skip**: Files with empty content are automatically skipped
- **Binary check**: Binary files (images, etc.) are rejected
- **Size limit**: Files exceeding 1MB result in an error
- **Auto-expand parent**: After adding, the parent prompt is automatically expanded to show new child prompts

## Difference from Add from Text File (Lines)

**Add from Text File (Whole)**:
- **Processing unit**: Entire file as 1 prompt
- **Multiple files**: Supported
- **Use case**: Long texts, config files

**Add from Text File (Lines)**:
- **Processing unit**: Each line as 1 prompt
- **Multiple files**: 1 file only
- **Use case**: Tag lists, word lists

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What%20Is%20a%20Prompt.md)
- [PromptTree](../../../01-Basics/03-Prompt%20Tree%20Overview.md)
- [Add From Text File](09-Add%20from%20Text%20File%20Lines.md)
- [Add From File System](13-Add%20from%20File%20System.md)
