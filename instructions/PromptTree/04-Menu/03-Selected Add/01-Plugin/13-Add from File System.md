# Add from File System

**Create prompts by collecting related information starting from base files**

## When to Use

- When you want to batch import a collection of LoRA models (.safetensors + .txt + .png)
- When you want to organize files scattered in folders into prompts grouped by related files
- When you want to automatically convert model information downloaded from Civitai (.info) into content
- When you want to manage video files with their associated thumbnails and descriptions as a set

## What It Does

Finds files with specified extensions (**base files**) and automatically collects related files (memos, images) to create prompts.

### Note: Consistency of File Structure Is Important

This feature assumes that **files in the folder are organized in a consistent pattern**.

**Solution**: Import groups with different file structures separately and apply different settings.

## What Is a Base File

The core of this feature is the "base file."

A **base file** is the file that becomes the source of a prompt. Among files in a folder, those with specified extensions (target extensions) are recognized as base files, and **1 base file = 1 prompt**.

```
Models/
├── character_A.safetensors  ← Base file → Prompt "character_A"
├── character_A.txt          ← Related file (collected as memo)
├── character_A.png          ← Related file (collected as image)
└── character_B.safetensors  ← Base file → Prompt "character_B"
```

## Processing Flow

1. **Base file detection**: Find files with target extensions (e.g., `.safetensors`)
2. **Related information collection**: Starting from the base file, collect related memo files and images
3. **Content extraction**: Generate prompt content based on settings
4. **Prompt creation**: Add to the prompt tree preserving the folder structure

## What Is Collected

For each base file, the following information is collected:

| Collected Item | Description | Settings |
| --- | --- | --- |
| **Content** | Prompt body text | Content source, string operation, format |
| **Memos** | Content of related text files | Memo extensions |
| **Images** | Related image files | Image extensions |

## Detail Pages

Detailed explanations of each setting are available on the following pages:

- [Add from File System - Content Extraction](15-Add from File System - Content Extraction.md) — Content extraction, processing, and formatting
- [Add from File System - FileSet Type](14-Add from File System - FileSet Type.md) — File grouping methods
- [Add from File System - Preset Management](17-Add from File System - Preset Management.md) — Saving and reusing settings
- [Add from File System - Processing Options](16-Add from File System - Processing Options.md) — Import behavior control

## Related

- [Prompt](../../../01-Basics/01-Concepts/03-What Is a Prompt.md)
- [PromptTree](../../../01-Basics/03-Prompt Tree Overview.md)
- [Add from File System (Quick)](18-Add from File System Quick.md)
- [Add From Text File](09-Add from Text File Lines.md)
- [AddPromptPlugin Settings](../03-Add Prompt Plugin Settings.md)
