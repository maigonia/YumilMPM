# FileSet Type

**Add from File System - File Grouping Method**

## Overview

FileSet Type determines how files within a folder are grouped. There are two modes to choose from depending on the use case.

## SameNameFileSet

### Behavior

Groups files with the same base name into one prompt.

### Example

Folder structure:
```
Models/
├── character_A.safetensors  ← Base file
├── character_A.txt          ← Same-name memo file → Collected as memo
├── character_A.png          ← Same-name image file → Collected as image
├── character_A.civitai.info ← Same-name JSON file → Collected as memo
├── character_B.safetensors  ← Another base file
└── character_B.jpg          ← character_B's image
```

Result:
- **character_A** prompt
  - Content: Extracted based on settings
  - Memos: character_A.txt, character_A.civitai.info
  - Images: character_A.png
- **character_B** prompt
  - Images: character_B.jpg

### Use Cases

- Models downloaded from Civitai (.safetensors + .txt + .png + .civitai.info)
- File sets associated by name

## FolderDirectFileSet

### Behavior

Treats all files within a folder as one set. Prompts are created per folder.

### Example

Folder structure:
```
Videos/
├── Project_A/
│   ├── video1.mp4           ← Base file
│   ├── video2.mp4           ← Another base file (separate prompt)
│   ├── readme.txt           ← All memos in folder
│   ├── notes.md             ← All memos in folder
│   └── thumbnail.jpg        ← All images in folder
└── Project_B/
    └── ...
```

Result:
- **video1** prompt
  - Memos: readme.txt content + notes.md content (labeled)
  - Images: thumbnail.jpg
- **video2** prompt
  - Memos: Same readme.txt + notes.md (folder shared)
  - Images: Same thumbnail.jpg

### Use Cases

- Project folder management
- Video collections (video + related documents + thumbnails)
- Structure where 1 folder = 1 context

## Comparison

**SameNameFileSet**:
- **Grouping basis**: File name
- **Memo collection**: Same-name files only
- **Image collection**: Same-name files only
- **Typical use**: LoRA models, character assets
- **Memo labels**: None

**FolderDirectFileSet**:
- **Grouping basis**: Folder
- **Memo collection**: All memo files in folder
- **Image collection**: All images in folder
- **Typical use**: Projects, video collections
- **Memo labels**: File name used as label

## Extension Settings

### Target Extensions

Specify extensions recognized as base files, separated by commas.

```
.safetensors, .ckpt, .pt    # AI models
.mp4, .mov, .avi            # Videos
.psd, .ai                   # Design files
```

### Memo Extensions

Specify extensions to collect as memos.

```
.txt, .json, .info, .md, .yaml
```

Content of collected memo files is saved as the prompt's "memos."

### Image Extensions

Specify extensions to collect as images.

```
.png, .jpg, .jpeg, .gif, .webp
```

Collected images are saved as the prompt's "images." Images are automatically validated, and corrupted files are skipped.

## Memo Max Characters

Specify the maximum number of characters to read from memo files.

- **-1**: No limit (read entire file)
- **Positive integer**: Truncate at specified character count

This serves as protection against accidentally collecting large log files as memos.

## Back

← [addFromFileSystem](13-Add from File System.md)

## Related

- [Add From File System](13-Add from File System.md)
- [Add from File System - Content Extraction](15-Add from File System - Content Extraction.md)
- [Add from File System - Preset Management](17-Add from File System - Preset Management.md)
- [Add from File System - Processing Options](16-Add from File System - Processing Options.md)
