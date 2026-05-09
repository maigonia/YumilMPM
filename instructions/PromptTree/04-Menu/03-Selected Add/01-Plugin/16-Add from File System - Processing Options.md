# Processing Options

**Add from File System - Controlling Import Behavior**

## Overview

Use processing options to fine-tune import behavior.

**The default settings are generally fine.** There is no need to change them unless you have a specific reason.

Change settings in cases like:
- When repeatedly importing the same folder and wanting to update only parts of existing prompts
- When wanting to add only new files without changing existing prompts at all

## Skip Options

Controls update behavior when an existing file (same path) is found.

### Skip updating content if file already exists

- **ON**: Do not update existing prompt content
- **OFF**: Overwrite with new content

### Skip updating memos if file already exists

- **ON**: Do not update existing prompt memos
- **OFF**: Overwrite with new memos

### Skip updating images if file already exists

- **ON**: Do not update existing prompt images
- **OFF**: Overwrite with new images

### Combination Examples

- **Content: ON / Memo: ON / Image: ON** → Add only new files (do not change existing at all)
- **Content: ON / Memo: ON / Image: OFF** → Add new + update only existing images
- **Content: OFF / Memo: OFF / Image: OFF** → Full overwrite update
- **Content: ON / Memo: OFF / Image: OFF** → Keep content, update memos and images

## Remove empty folder nodes after import

### Behavior

When ON, deletes folder nodes without child prompts after import.

### Usage Example

**Import folder:**
```
Models/
├── EmptyFolder/       ← No target files
├── Character_A/
│   └── model.safetensors
└── TempFiles/
    └── readme.txt     ← Not a target extension
```

**Target extension:** `.safetensors`

**Result (ON):**
```
Models/
└── Character_A/
    └── model.safetensors
```

**Result (OFF):**
```
Models/
├── EmptyFolder/       ← Remains empty
├── Character_A/
│   └── model.safetensors
└── TempFiles/         ← Remains empty
```

## Processing Results Display

After import completes, the following statistics are displayed:

- **Processed Files**: Total number of target files scanned
- **Added Files**: Number of newly added prompts
- **Updated Files**: Number of updated existing prompts (including partial updates)
- **Processed Folders**: Number of folder nodes created/reused

### Example Result Message

```
Added 5 files, Updated 3 files
(10 files processed, 4 folders)
```

## Recommended Settings

### First Import

- Skip Content: OFF
- Skip Memo: OFF
- Skip Image: OFF
- Remove empty folders: ON

### Additional Import (New Files Only)

- Skip Content: ON
- Skip Memo: ON
- Skip Image: ON
- Remove empty folders: ON

### Image Update Only

- Skip Content: ON
- Skip Memo: ON
- Skip Image: OFF
- Remove empty folders: ON

## Back

← [addFromFileSystem](13-Add%20from%20File%20System.md)

## Related

- [Add From File System](13-Add%20from%20File%20System.md)
- [Add from File System - Content Extraction](15-Add%20from%20File%20System%20-%20Content%20Extraction.md)
- [Add from File System - FileSet Type](14-Add%20from%20File%20System%20-%20FileSet%20Type.md)
- [Add from File System - Preset Management](17-Add%20from%20File%20System%20-%20Preset%20Management.md)
