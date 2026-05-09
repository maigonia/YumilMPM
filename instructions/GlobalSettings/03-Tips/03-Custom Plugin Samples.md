# Custom Plugin Samples

A collection of working, complete example plugins for [Custom Plugin](02-Custom Plugins.md) development. Each example focuses on a different feature set.

| Sample | Features covered |
| --- | --- |
| **AI Rewrite (Gemini)** | `permissions: ["network"]` / `secrets` / `env.FETCH` / `env.getSecret` / `group` / `text` + `textarea` + `number` fields |
| **Prompt Snapshot Manager** | `permissions: ["file"]` / full file API / `select` field / `help` field |
| **Context Filter Demo** | How to configure all three dialogs (settings / editor / batch) separately using `contexts` |
| **Dropzone Test** | `type: "dropzone"` file receipt / `mimeTypes` filter / `multiple` / strict `file` permission gating / payload shape (`name` / `mimeType` / `bytes` / `path`) |

## AI Rewrite (Gemini)

A typical AI integration plugin that rewrites text using the Google Gemini API. Uses both `network` and `secret` permissions; the API key is managed safely through [API Key Settings](../04-Menu/09-API Key Settings.md).

```js
export default {
  name: "AI Rewrite (Custom)",
  pluginName: "CustomAIRewrite",
  tooltip: "Rewrite text using Google Gemini API",
  author: "MPM Team",
  version: "1.0.0",
  description: "Rewrites text using Google Gemini API",
  context: ["PromptEditor", "CheckedChunks"],
  permissions: ["network"],
  secrets: ["gemini"],
  settings: [
    { key: "model", type: "text", label: "Model", default: "gemini-2.5-flash" },
    { key: "instruction", type: "textarea", label: "Instruction",
      default: "Rewrite the following text to be more concise and clear." },
    {
      group: "Advanced",
      fields: [
        { key: "temperature", type: "number", label: "Temperature",
          default: 0.7, min: 0, max: 2, step: 0.1 },
        { key: "maxTokens", type: "number", label: "Max Output Tokens",
          default: 1000, min: 1, max: 8192, step: 100 }
      ]
    }
  ]
}

async function edit(text, settings) {
  var apiKey = await env.getSecret("gemini");
  if (!apiKey) {
    throw new Error("Gemini API key is not configured.");
  }

  var model = settings.model || "gemini-2.5-flash";
  var url = "https://generativelanguage.googleapis.com/v1beta/models/"
    + model + ":generateContent?key=" + apiKey;

  var response = await env.FETCH(url, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({
      contents: [{ role: "user", parts: [{ text: settings.instruction + "\n\n" + text }] }],
      generationConfig: {
        temperature: settings.temperature || 0.7,
        maxOutputTokens: settings.maxTokens || 1000
      }
    })
  });

  if (response.status !== 200) {
    throw new Error("Gemini API error (HTTP " + response.status + ")");
  }

  var data = JSON.parse(response.body);
  if (data.candidates && data.candidates[0] && data.candidates[0].content) {
    return data.candidates[0].content.parts[0].text;
  }
  return text;
}
```

### Highlights

- Declare `permissions: ["network"]` and grant Network Access in [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md) before use
- Declaring `secrets: ["gemini"]` makes a "gemini" row appear automatically in [API Key Settings](../04-Menu/09-API Key Settings.md) where you store the API key
- `group: "Advanced"` collapses temperature / max-tokens into a tidier dialog
- API errors are surfaced via `throw new Error(...)` (toast) instead of silently returning the original text
- The fields do **not** declare `contexts`, so the same field set is shown in all three dialogs (standalone settings, editor pre-run, bulk-edit pre-run). Unlike action-style plugins such as Snapshot Manager, values like model name and instruction are settings you configure once and reuse, so showing the same fields in every context is the natural choice

## Prompt Snapshot Manager

A lightweight version-control plugin: save / load / list / delete the current prompt by name. A complete example for the `file` permission and the full file API.

```js
export default {
  name: "Prompt Snapshot Manager",
  pluginName: "PromptSnapshotManager",
  tooltip: "Save / load / list / delete the current prompt by name",
  description: "Lightweight version control. Only `load` replaces the prompt.",
  context: ["PromptEditor"],
  permissions: ["file"],
  help: `# Prompt Snapshot Manager

Save the current prompt to a file and recall it later — a lightweight version control system.

## Modes

| Mode | Behavior |
|------|------|
| **Save** | Save the current prompt under the given name |
| **Load** | Replace the editor with the saved prompt |
| **List** | List all saved snapshots |
| **Delete** | Delete the named snapshot |

Files are saved under \`{pluginDataDir}/snapshots/\`.
`,
  settings: [
    // Action-style plugin: hide from the standalone settings dialog and only
    // show in the editor pre-run dialog. Top-level context is ["PromptEditor"]
    // only, so "batch" is unreachable — "editor" alone is sufficient.
    {
      key: "mode",
      type: "select",
      label: "Action",
      default: "save",
      options: [
        { label: "Save current prompt", value: "save" },
        { label: "Load saved prompt (replaces current)", value: "load" },
        { label: "List all snapshots", value: "list" },
        { label: "Delete snapshot", value: "delete" }
      ],
      contexts: ["editor"]
    },
    {
      key: "name",
      type: "text",
      label: "Snapshot name (ignored for List)",
      default: "",
      contexts: ["editor"]
    }
  ]
}

var SNAPSHOT_DIR = "snapshots";

function sanitizeName(raw) {
  return String(raw || "").replace(/[^a-zA-Z0-9_-]/g, "_");
}

function snapshotPath(name) {
  return SNAPSHOT_DIR + "/" + name + ".txt";
}

async function edit(text, settings) {
  var mode = (settings && settings.mode) || "save";
  var name = sanitizeName(settings && settings.name);

  if (mode === "save") {
    if (!name) return text + "\n[Snapshot: name required]";
    var path = snapshotPath(name);
    var existed = await env.fileExists(path);
    await env.writeFile(path, text);
    return text + "\n[Snapshot: " + (existed ? "overwritten" : "saved") + " as '" + name + "']";
  }

  if (mode === "load") {
    if (!name) return text + "\n[Snapshot: name required]";
    var path = snapshotPath(name);
    if (!(await env.fileExists(path))) {
      return text + "\n[Snapshot: '" + name + "' not found]";
    }
    return await env.readFile(path);
  }

  if (mode === "list") {
    var entries = await env.listFiles(SNAPSHOT_DIR);
    var names = entries
      .filter(function(f) { return /\.txt$/.test(f); })
      .map(function(f) { return f.replace(/\.txt$/, ""); });
    if (names.length === 0) {
      return text + "\n[Snapshot: no snapshots yet. Save dir: " +
        env.pluginDataDir + "/" + SNAPSHOT_DIR + "]";
    }
    return text + "\n[Snapshots (" + names.length + "): " + names.join(", ") + "]";
  }

  if (mode === "delete") {
    if (!name) return text + "\n[Snapshot: name required]";
    var path = snapshotPath(name);
    if (!(await env.fileExists(path))) {
      return text + "\n[Snapshot: '" + name + "' not found]";
    }
    await env.deleteFile(path);
    return text + "\n[Snapshot: deleted '" + name + "']";
  }

  return text + "\n[Snapshot: unknown mode '" + mode + "']";
}
```

### Highlights

- Declares `permissions: ["file"]`. The user must grant File Access in [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md) before it can run
- Exercises six file APIs in one plugin: `writeFile`, `readFile`, `fileExists`, `deleteFile`, `listFiles`, plus the `pluginDataDir` property
- Paths are written as relative paths (`snapshots/foo.txt`), so they automatically resolve under `{projectFolder}/settings/plugin_data/edit/PromptSnapshotManager/snapshots/`. All plugin data is consolidated into the same tree as built-in plugin settings, so uninstalling a plugin is just deleting one folder
- The `help` field provides a Markdown help dialog reachable from the help icon in [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- A `select` field with `options: [{ label, value }]` switches between the four modes
- `context: ["PromptEditor"]` makes the plugin appear only in the PromptEditor tab — intentionally not exposed to bulk edit
- The fields declare `contexts: ["editor"]` to hide them from the standalone settings dialog. Action-style plugins have no reason to cache settings, so it's enough to ask for values in the dialog that opens right before execution

## Context Filter Demo

The settings dialog opens in three different forms (see the "contexts" section of [Custom Plugin](02-Custom Plugins.md)):

- `settings` — the standalone settings dialog opened from the gear icon in [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- `editor` — the dialog shown right before running in the editor
- `batch` — the dialog shown right before running in bulk edit

This sample is a **teaching plugin** that demonstrates how to use the `contexts` property to control which dialog each field (or whole group) appears in. The plugin itself does nothing meaningful — `edit()` simply dumps the settings it received into the editor. Install it and open each dialog to confirm that fields appear and disappear exactly as declared.

```js
export default {
  name: "Context Filter Demo",
  pluginName: "ContextFilterDemo",
  tooltip: "Verifies the settings.contexts filter",
  description: "Each field is shown / hidden according to the contexts it declares",
  context: ["PromptEditor", "CheckedChunks"],
  permissions: [],
  settings: [
    // 1. No contexts → visible in every dialog (backward compat)
    {
      key: "everywhere",
      type: "text",
      label: "Everywhere (no contexts)",
      default: "all"
    },

    // 2. Visible only in the standalone settings dialog
    {
      key: "settingsOnly",
      type: "text",
      label: "Settings-only field",
      default: "s",
      contexts: ["settings"]
    },

    // 3. Visible only in the editor pre-run dialog
    {
      key: "editorOnly",
      type: "text",
      label: "Editor-only field",
      default: "e",
      contexts: ["editor"]
    },

    // 4. Visible only in the bulk-edit pre-run dialog
    {
      key: "batchOnly",
      type: "text",
      label: "Batch-only field",
      default: "b",
      contexts: ["batch"]
    },

    // 5. Visible in two dialogs (the canonical action-style pattern:
    //    hidden from the standalone settings dialog)
    {
      key: "editorAndBatch",
      type: "text",
      label: "Editor + Batch field",
      default: "eb",
      contexts: ["editor", "batch"]
    },

    // 6. A whole group restricted to a single dialog by putting `contexts`
    //    on the group itself
    {
      group: "Settings-only group (whole group hidden in editor/batch)",
      contexts: ["settings"],
      fields: [
        { key: "groupSettingsA", type: "text", label: "A", default: "ga" },
        { key: "groupSettingsB", type: "text", label: "B", default: "gb" }
      ]
    },

    // 7. The group is universal but its inner fields opt out individually
    {
      group: "Mixed group (group is universal, fields opt out individually)",
      fields: [
        { key: "mixedAll", type: "text", label: "Mixed all-contexts", default: "ma" },
        {
          key: "mixedEditor",
          type: "text",
          label: "Mixed editor-only",
          default: "me",
          contexts: ["editor"]
        },
        {
          key: "mixedSettings",
          type: "text",
          label: "Mixed settings-only",
          default: "ms",
          contexts: ["settings"]
        }
      ]
    }
  ]
}

async function edit(text, settings) {
  var seen = settings ? Object.keys(settings).sort() : [];
  var report =
    "[ContextFilterDemo] Fields received in this context:\n" +
    JSON.stringify(seen, null, 2) + "\n" +
    "Values: " + JSON.stringify(settings || {}, null, 2);
  return text + "\n\n" + report;
}
```

### What appears in each dialog

After filtering by the declared `contexts`, you should see:

| Field | settings dialog | editor dialog | batch dialog |
| --- | :---: | :---: | :---: |
| `everywhere` | ○ | ○ | ○ |
| `settingsOnly` | ○ | — | — |
| `editorOnly` | — | ○ | — |
| `batchOnly` | — | — | ○ |
| `editorAndBatch` | — | ○ | ○ |
| Settings-only group (`groupSettingsA` / `groupSettingsB`) | ○ | — | — |
| Mixed group: `mixedAll` | ○ | ○ | ○ |
| Mixed group: `mixedEditor` | — | ○ | — |
| Mixed group: `mixedSettings` | ○ | — | — |

### Highlights

- **Omitting `contexts` makes a field visible in every dialog** (`everywhere` / `mixedAll`). Existing plugins are unaffected by the new feature
- **Per-field** filtering: write `contexts: ["editor"]` and the field disappears from the other two dialogs
- **Per-group** filtering: declare `contexts` on a `group` to hide the entire group at once
- A group can stay universal while its inner fields opt out individually (`Mixed group`)
- `context: ["PromptEditor", "CheckedChunks"]` makes the plugin appear in both the PromptEditor tab and the bulk-edit tab, so you can actually open all three dialogs and compare them side by side

## Dropzone Test

A verification plugin that lines up three `dropzone` fields side by side so you can compare MIME filtering, single-vs-multiple acceptance, the `file` permission gate, and the payload shape all in one place.

```js
export default {
  name: "Dropzone Test",
  pluginName: "DropzoneTest",
  tooltip: "drop zone field behavior verification",
  description: "Verify payload / filter / transient behavior of the file-permission-gated dropzone",
  context: ["PromptEditor"],
  permissions: ["file"],
  settings: [
    {
      key: "textInputs",
      type: "dropzone",
      label: "Text files (text/* only, multiple)",
      mimeTypes: ["text/*"],
      multiple: true
    },
    {
      key: "imageInputs",
      type: "dropzone",
      label: "Image files (image/* only, single)",
      mimeTypes: ["image/*"],
      multiple: false
    },
    {
      key: "anyInputs",
      type: "dropzone",
      label: "Any file (no mime filter, multiple)",
      multiple: true
    },
    {
      key: "note",
      type: "text",
      label: "Optional note (persisted across runs)",
      default: ""
    }
  ]
}

async function edit(text, settings) {
  var summarize = function (list) {
    if (!list || list.length === 0) return [];
    return list.map(function (f) {
      return {
        name: f.name,
        mimeType: f.mimeType,
        path: f.path,
        bytesLength: f.bytes ? f.bytes.length : 0,
        hasPath: typeof f.path === "string" && f.path.length > 0
      };
    });
  };

  var report = {
    note: settings && settings.note ? settings.note : "",
    textInputs: summarize(settings && settings.textInputs),
    imageInputs: summarize(settings && settings.imageInputs),
    anyInputs: summarize(settings && settings.anyInputs)
  };

  var preview = "";
  var first = settings && settings.textInputs && settings.textInputs[0];
  if (first && first.bytes) {
    try {
      var decoded = atob(first.bytes);
      preview = "\n---\n[preview of " + first.name + "]\n" + decoded.slice(0, 200);
    } catch (e) {
      preview = "\n---\n[atob failed: " + (e && e.message ? e.message : String(e)) + "]";
    }
  }

  return text + "\n\n[DropzoneTest]\n" + JSON.stringify(report, null, 2) + preview;
}
```

### How to Try It

1. Open [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md) and turn the `DropzoneTest` **file permission OFF**, then open its dialog
   - All three dropzones appear greyed out with the "Enable file permission..." message
   - Drops have no effect
2. Turn the file permission **ON** and reopen the dialog
   - The dropzones become active
   - Drop a text file (`.txt` / `.md` / `.json`) onto "Text files" — it appears in the list as `name · size`
   - Drop an image (`.png` / `.jpg`) onto "Image files" — single-replace mode (a new drop replaces the previous file)
   - "Any file" accepts anything regardless of extension
   - Intentionally drop a PNG onto "Text files" — the MIME filter rejects it
3. Click **OK** and a JSON report is inserted into the editor
   - Each dropzone outputs the `name` / `mimeType` / `path` / `bytesLength` / `hasPath` of the files it received
   - The first 200 characters of the first text file are decoded with `atob(bytes)` and shown as a preview
4. Reopen the dialog — the drop list is empty again while the `note` field still retains its value (transient behavior)

### Takeaways From This Sample

- **Strict `file` permission gating**: turning `file` OFF disables the dropzone completely
- **MIME filter supports wildcards**: `["text/*"]` / `["image/*"]` / omit (accept all) can be compared side by side in the same plugin
- **`multiple: false`** behaves as replace-on-drop (only one file kept even if several are dropped)
- **Four-part payload**: `name` / `mimeType` / `bytes` (base64) / `path` (absolute) are all populated
- **Transient**: `dropzone` values are transient per dialog OK, so large binaries never accumulate in the plugin settings
- **Coexists with regular fields**: `text` fields like `note` persist as before, so dropzones and ordinary settings can be mixed in the same plugin

## Related

- [Custom Plugin](02-Custom Plugins.md)
- [EditPlugin Settings](../04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md)
- [API Key Settings](../04-Menu/09-API Key Settings.md)
