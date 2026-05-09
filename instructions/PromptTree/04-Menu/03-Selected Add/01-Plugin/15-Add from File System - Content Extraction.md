# Content Extraction

**Add from File System - Content Retrieval, Processing, and Formatting**

## Overview

Content extraction is performed in three steps:

1. **Content Source**: Where to get the text from
2. **Content Operation**: How to process the retrieved text
3. **Content Format**: The final output format

## Content Source

Select the source for text retrieval.

- **Base File Name**: The base file's file name (without extension)
- **Base File (.txt)**: Content of the same-named .txt file as the base file
- **Base File (.json)**: Content of the same-named .json file as the base file
- **Base File (.info)**: Content of the same-named .info file as the base file (Civitai format)
- **Base File (Custom)**: Content of a same-named file with a custom extension (specify the extension)
- **Specified Name File**: Content of a file with a specified name

### Base File Search

The "Base File (...)" options also match file names with intermediate identifiers:

```
character_A.safetensors       ← Base file
character_A.txt               ← Exact match (preferred)
character_A.civitai.txt       ← With intermediate identifier (secondary)
character_A.preview.txt       ← With intermediate identifier
```

### Base File (Custom)

Reads a same-named file with any extension you specify. Enter the extension in the Extension field.

Example: Specify `.md` → For base file `prompt.md`, reads the content of `prompt.md` itself

This is useful when the base file itself is a text file and you want to read its content directly.

### Specified Name File

Reads a file with a specific name. Only files in the same directory as the base file are targeted.

Example: Specify `readme.txt` → Reads readme.txt in each base file's directory

## Content Operation

Select how to process the retrieved text.

### Use As Is

Uses the retrieved text as-is. No processing is applied.

### JSON Key Extraction

Extracts the value of a specific key from a JSON file.

#### Basic Syntax

```
propertyName                    # Single key
propertyName.childProperty      # Nested key
arrayName[0]                    # Array element (0-based)
arrayName[*]                    # First element of array
arrayName[first]                # First element of array
arrayName[last]                 # Last element of array
```

#### Example: Civitai Info File

```json
{
  "modelId": 12345,
  "model": {
    "name": "Character Model"
  },
  "images": [
    {"url": "...", "meta": {"Model": "SD 1.5"}}
  ],
  "trainedWords": ["trigger_word", "style"]
}
```

- `modelId` → `12345`
- `model.name` → `Character Model`
- `images[0].meta.Model` → `SD 1.5`
- `trainedWords` → `trigger_word`(newline)`style`
- `trainedWords[0]` → `trigger_word`

#### Multiple Key Extraction

Specify multiple keys separated by commas, and each value is returned separated by newlines:

```
modelId, model.name, trainedWords[0]
```

Result:
```
12345
Character Model
trigger_word
```

### Extract First Line Only

Extracts only the first non-empty line of the text.

```
Input:

Title line
Description line 1
Description line 2

Output: Title line
```

### Extract with Regular Expression

Extracts text using a regular expression pattern.

- If there is a capture group: Returns the content of the first group
- If there is no capture group: Returns the entire match
- Case-insensitive
- Multiline mode supported

#### Examples

- `trigger:\\s*(.+)`: Input `trigger: word1, word2` → Output `word1, word2`
- `\\d+`: Input `Model v1.5` → Output `1`
- `(?<=version:\\s*)\\d+\\.\\d+`: Input `version: 2.0` → Output `2.0`

## Content Format

Specify the final output format using a template.

### Basic Placeholders

- `{basefile}`: Base file name (without extension)
- `{extracted}`: Entire extracted/processed text

### Placeholders for Multiple Keys

When using multiple key extraction (comma-separated), you can access each individually by index:

- `{json0}`: Value of the 1st key
- `{json1}`: Value of the 2nd key
- `{json2}`: Value of the 3rd key
- And so on (`{json3}`, `{json4}`, ...)

### Named Placeholders (Shortcuts)

Aliases for commonly used patterns:

- `{model}`: Same as `{json0}`
- `{trainedwords}`: Same as `{json1}`
- `{description}`: Same as `{json2}`
- `{trigger}`: Same as `{json3}`

### Format Examples

#### Example 1: Simple

```
{extracted}
```

Result: Extracted text output as-is

#### Example 2: Combined with File Name

```
{basefile}: {extracted}
```

Result: `character_A: trigger_word, style`

#### Example 3: Formatting Multiple Keys

Operation parameter: `model.name, trainedWords[0], description`

Format:
```
Model: {model}
Trigger: {trainedwords}
---
{description}
```

Result:
```
Model: Character Model
Trigger: trigger_word
---
This is a character model...
```

## Processing Flow Diagram

```
┌─────────────────┐
│ Content Source   │  ← Where to get?
│ (Base File Name  │
│  / .txt / .json) │
└────────┬────────┘
         │ Source text
         ▼
┌─────────────────┐
│ Content Operation│  ← How to process?
│ (Use As Is /     │
│  JSON / Regex)   │
└────────┬────────┘
         │ Extracted text
         ▼
┌─────────────────┐
│ Content Format   │  ← How to format?
│ ({basefile} /    │
│  {extracted})    │
└────────┬────────┘
         │
         ▼
    Final content
```

## Typical Configuration Examples

### Extracting Civitai Model Information

- **Source**: Base File (.info)
- **Operation**: JSON Key Extraction
- **Parameter**: `model.name, trainedWords, description`
- **Format**: `{model}\n\nTrigger: {trainedwords}`

### Using First Line of Text File as Title

- **Source**: Base File (.txt)
- **Operation**: Extract First Line Only
- **Format**: `{extracted}`

### Using Text File Content As-Is

- **Source**: Base File (Custom) (Extension: `.txt`)
- **Operation**: Use As Is
- **Format**: (empty)

### Using File Name as Content Directly

- **Source**: Base File Name
- **Operation**: Use As Is
- **Format**: `{basefile}`

## Back

← [addFromFileSystem](13-Add from File System.md)

## Related

- [Add From File System](13-Add from File System.md)
- [Add from File System - FileSet Type](14-Add from File System - FileSet Type.md)
- [Add from File System - Preset Management](17-Add from File System - Preset Management.md)
- [Add from File System - Processing Options](16-Add from File System - Processing Options.md)
