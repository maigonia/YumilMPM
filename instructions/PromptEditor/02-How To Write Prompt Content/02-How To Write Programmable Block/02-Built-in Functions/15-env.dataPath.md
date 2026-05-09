# env.dataPath

**Path to the data folder**

## Overview

`env.dataPath` is a string property that returns the absolute path to the app's data folder.

Image paths in `env.chunk.imagePaths` are automatically converted to absolute paths when `env.dataPath` is available, so no manual conversion code is needed.

## Value Type

`string` — Absolute path to the data folder (e.g. `C:/Users/user/AppData/Roaming/com.mpm.app`)

## Usage Examples

### Get image path

The simplest way to write it:

```javascript
@@@_
env.OUTPUT(env.chunk.imagePaths[0]);
_@@@
```

If no image is registered, `imagePaths[0]` will be `undefined`, but **this does not cause an error — it outputs an empty string** and prompt generation continues normally.

Defensive style (when you want to explicitly handle the no-image case):

```javascript
@@@_
const path = (env.chunk.imagePaths || [])[0] || "";
env.OUTPUT(path);
_@@@
```

Both produce the same result. The simple style works fine.

### Combined with env.WD14

```javascript
@@@_
const path = (env.chunk.imagePaths || [])[0];
if (path) {
  const tags = await env.WD14(path);
  env.OUTPUT(tags);
}
_@@@
```

### Access env.dataPath directly

When the data folder path itself is needed:

```javascript
@@@_
env.OUTPUT(env.dataPath);
_@@@
```

## Notes

- If the data folder is not configured, `env.dataPath` will be `undefined` and relative paths will not be converted
- Image paths for file-system chunks are already stored as absolute paths, so no conversion is performed

## Related

- [Programmable Block](../README.md)
- [env.chunk](01-env.chunk.md)
- [env.WD14](14-env.WD14.md)
- [Image](../../../../PromptBrowser/01-Basics/01-Image.md)
