# Custom Plugins

## When to Use

- When you want to add custom text transformation features
- When you want to integrate with external AI services (Gemini, OpenAI, Claude, etc.)
- When you need functionality not available in existing [Plugin](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)s

## What Are Custom Plugins

Custom plugins are JavaScript files (.js) created by users. Place them in the `plugins/edit/` directory of the data folder — or in an immediate subfolder (one level deep) — and they will be automatically loaded at app startup and available as [Plugin](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)s.

Unlike [Programmable Edit](../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/18-Programmable%20Edit.md), which is for quick scripting within a project, custom plugins are complete tools with schema-based settings dialogs, usable across all projects, and distributable as `.js` files.

## Plugin File Structure

```js
// Metadata (required fields + recommended fields)
export default {
  name: "Plugin Display Name",
  pluginName: "UniquePluginId",
  tooltip: "Plugin description",
  author: "Author Name",
  version: "1.0.0",
  description: "Detailed plugin description",
}

// Main logic (required)
function edit(text, settings) {
  // Process and return text
  return text.toUpperCase();
}
```

### Metadata Fields

| Field | Required | Description |
| --- | --- | --- |
| `name` | Yes | Display name in UI |
| `pluginName` | Yes | Internal ID (must be unique) |
| `tooltip` | Yes | Plugin description |
| `author` | - | Plugin author name |
| `version` | - | Version (e.g., `"1.0.0"`) |
| `description` | - | Detailed description of the plugin |
| `context` | - | Available contexts. All contexts when omitted |
| `permissions` | - | Required permissions (any of `["network", "secret", "file"]`) |
| `secrets` | - | Secret service names to use |
| `rateLimit` | - | [Rate Limiting](../02-Glossary/06-Rate%20Limiting.md) config applied to `env.FETCH` calls (see below) |
| `settings` | - | Settings dialog schema |
| `appVersion` | - | MPM version when plugin was created (e.g., `"2.1.0"`) |
| `createdAt` | - | Date when plugin was created (e.g., `"2026-03-29"`) |
| `help` | - | Markdown text displayed in the help dialog |

### Specifying `context`

A custom plugin can be invoked from **three different places** inside the app. The `context` field is how you declare which of those places your plugin should be available in.

| `context` value | Where it is used |
| --- | --- |
| `"PromptEditor"` | When the user selects text in the prompt editor and runs the plugin ([Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)) |
| `"CategoryTemplate"` | As part of the [Category Template](../../AdvancedPanel/02-Glossary/01-Category%20Template.md) processing pipeline |
| `"CheckedChunks"` | Bulk editing of checked prompts ([Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md)) |

```js
// Available only in a specific place
context: ["PromptEditor"]

// Available in multiple places
context: ["PromptEditor", "CheckedChunks"]

// Omitted = available in all three places
```

For example, a plugin that assumes "the input is text the user has selected" should restrict itself to `["PromptEditor"]`, so it doesn't clutter the unrelated bulk-edit plugin list. Restricting `context` to the appropriate places keeps the UI uncluttered for users.

> **Note**: The `contexts` (plural) field discussed later is an entirely different concept — it controls which kind of *settings dialog* an individual input field appears in. Don't confuse it with the top-level `context` (where the plugin itself appears).

## Settings Dialog Schema

A custom plugin can have its **own dedicated settings dialog**. This is useful when you want to let users pick values like "which AI model to use", "temperature parameter", or "operation mode".

The nice part is that you do *not* have to build the dialog UI yourself in HTML or React. You simply declare the input fields you want as a list (a schema) in the `settings` field, and the app reads it and assembles the dialog automatically. Whatever values the user enters in the dialog are passed as the **second argument `settings`** to your `edit(text, settings)` function — so just read them and branch on them.

The dialog can be opened anytime from the gear icon in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md). (Some plugins can also auto-open it right before execution — see `contexts` below.)

```js
settings: [
  { key: "model", type: "text", label: "Model", default: "gemini-2.5-flash" },
  { key: "temperature", type: "number", label: "Temperature", default: 0.7,
    min: 0, max: 2, step: 0.1 },
  {
    group: "Advanced",
    fields: [
      { key: "maxTokens", type: "number", label: "Max Tokens", default: 1000 }
    ]
  }
]

// In the edit function, the values arrive as the second argument
function edit(text, settings) {
  // settings.model === "gemini-2.5-flash"
  // settings.temperature === 0.7
  // settings.maxTokens === 1000
}
```

Basic properties each item needs:

- `key` — name used to look the value up in the `settings` object (alphanumeric)
- `type` — kind of input control (see [Field Types](#field-types) below)
- `label` — label shown in the dialog
- `default` — initial default value

### Field Types

Each item in the schema is called a **field**. A field corresponds to **one input control** in the dialog. The `type` property selects what kind of control it is — text box, dropdown, number spinner, and so on.

There are six available types:

| Type | What it looks like in the dialog | Extra options |
| --- | --- | --- |
| `text` | Single-line text box | - |
| `textarea` | Multi-line text area | - |
| `number` | Number spinner | `min`, `max`, `step` |
| `select` | Dropdown | `options: [{ label, value }]` (required) |
| `checkbox` | Checkbox | - |
| `dropzone` | OS drag & drop area | `mimeTypes`, `multiple` (see below) |

Only `select` requires that you also pass an `options` array listing the choices:

```js
{ key: "mode", type: "select", label: "Action", default: "save",
  options: [
    { label: "Save current prompt", value: "save" },
    { label: "Load saved prompt", value: "load" }
  ] }
```

`label` is the text the user sees, and `value` is what actually ends up in `settings.mode`.

#### The `dropzone` field

`dropzone` is a special field that accepts files dropped from the OS file manager. **It is only functional when the plugin's `file` permission is ON; with `file` OFF the field is greyed out and drops are ignored.**

```js
{ key: "inputs", type: "dropzone", label: "Drop text files",
  mimeTypes: ["text/*"], multiple: true }
```

Options:

- `mimeTypes: string[]` (optional) — MIME patterns to accept. Wildcards are allowed (e.g., `["text/*", "image/*"]`). Omit to accept anything
- `multiple: boolean` (optional, default `true`) — allow multiple files per drop

The value passed into the plugin is an array of `PluginDropPayload`:

- `name` — file basename
- `mimeType` — MIME type inferred from the extension
- `bytes` — base64-encoded file content (decode with `atob(bytes)`)
- `path` — absolute path of the source file

```js
async function edit(text, settings) {
  const inputs = settings.inputs ?? [];
  const parts = inputs.map(f => atob(f.bytes));
  return text + "\n" + parts.join("\n---\n");
}
```

`dropzone` values are transient per dialog OK — they are not persisted as plugin settings. Reopening the same dialog starts with an empty drop list.

Only OS drops are supported; browser drags are not received due to a technical constraint.

### visibleWhen (Conditional Display)

Show/hide fields based on other field values:

```js
{ key: "model", type: "text", label: "OpenAI Model", default: "gpt-4o",
  visibleWhen: { key: "provider", value: "openai" } }
```

### contexts (Dialog Context Filter)

The settings dialog opens in three different contexts. Use `contexts` to make a field visible only in selected contexts:

| Value | Which dialog |
| --- | --- |
| `"settings"` | The standalone settings dialog opened from the gear icon in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md) (caches values only — does not run the plugin) |
| `"editor"` | The dialog shown right before running [Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md) in the editor |
| `"batch"` | The dialog shown right before running [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md) for bulk edits |

```js
// Action-style plugin whose settings change every run:
// hidden from the standalone settings dialog, shown only in the
// editor / bulk-edit dialogs that immediately precede execution.
{ key: "mode", type: "select", label: "Action",
  options: [{ label: "Save", value: "save" }, { label: "Load", value: "load" }],
  default: "save",
  contexts: ["editor", "batch"] }
```

Rules:

- Omitting `contexts` makes the field visible in every context (existing plugins are unaffected)
- A `group` itself can declare `contexts` to hide the entire group
- Empty groups (all inner fields filtered out) are dropped automatically
- If every field is filtered out for a context, the dialog is skipped and the plugin runs with its cached settings

`visibleWhen` is a runtime, value-based filter; `contexts` is a load-time, dialog-based filter. The two mechanisms are independent.

### group (Grouping)

Group fields together:

```js
{
  group: "Advanced",
  fields: [
    { key: "maxTokens", type: "number", label: "Max Tokens", default: 1000 }
  ]
}
```

## Writing Help

Add Markdown-formatted text to the `help` field, and a help icon will appear next to the plugin name in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md). Click it to open a help dialog.

```js
export default {
  name: "My Plugin",
  pluginName: "MyPlugin",
  tooltip: "Description",
  help: `# My Plugin

## Usage

1. Select text and run

## Settings

| Item | Description |
|------|------|
| **Model** | Model name to use |
`
}
```

Supports basic Markdown syntax including headings, lists, tables, links, and code blocks.

## External API Integration

### env.FETCH

Send HTTP requests to external servers or local servers. Requires declaring `permissions: ["network"]` in metadata and enabling Network Access in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md).

```js
// External server (HTTPS)
var response = await env.FETCH("https://api.example.com/v1/chat", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ prompt: text })
});
// response: { status: number, headers: object, body: string }

if (response.status === 200) {
  var data = JSON.parse(response.body);
  return data.result;
}
throw new Error("API error (HTTP " + response.status + ")");
```

External server connections support HTTPS only. Localhost connections also support HTTP.

3xx redirects are not followed automatically. When a redirect is needed, read the `Location` entry from `response.headers` and call `env.FETCH` again yourself. This restriction exists to avoid the SSRF (Server-Side Request Forgery) risk that comes from skipping re-validation on redirect targets. Typical API endpoints (LLM, translation, etc.) never return redirects, so most plugins never encounter this limit.

#### Connecting to Local Servers

You can also connect to local servers running on your PC (LM Studio, Ollama, ComfyUI, etc.). Localhost connections support HTTP as well.

```js
// Use in edit function
var response = await env.FETCH("http://localhost:1234/v1/chat/completions", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    messages: [{ role: "user", content: text }]
  })
});
```

You can also use `127.0.0.1` instead of localhost.

### env.getSecret

Retrieve API keys from the OS keychain. Requires declaring service names in the `secrets` metadata field.

```js
// Declare in metadata
secrets: ["gemini"]

// Use in edit function
var apiKey = await env.getSecret("gemini");
if (!apiKey) {
  throw new Error("API key is not configured.");
}
```

Register API keys in advance at **GlobalSettings > [API Key Settings](../04-Menu/09-API%20Key%20Settings.md)**. When a plugin declares `secrets`, the service name automatically appears in API Key Settings.

### Rate Limiting

When a plugin declares `permissions: ["network"]` or its own `metadata.rateLimit`, [Rate Limiting](../02-Glossary/06-Rate%20Limiting.md) is applied to its `env.FETCH` calls. If too many requests happen in a short window, requests beyond the limit are rejected immediately (fail-fast).

#### Resolution Order

1. **User override** — values configured from the gear icon in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
2. **`metadata.rateLimit`** — values declared by the plugin author
3. **App default** — applied to plugins that declare `network` permission but no `metadata.rateLimit` (`delayMs: 1000`, `maxRequests: 30`, `windowMinutes: 1`)

Plugins that declare neither `network` permission nor `metadata.rateLimit` are not rate-limited, and the gear icon does not appear for them in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md).

#### Declaring `metadata.rateLimit`

```js
export default {
  name: "My API Plugin",
  pluginName: "MyApiPlugin",
  permissions: ["network"],
  rateLimit: {
    delayMs: 2000,      // Minimum delay between consecutive requests (ms). 0 disables this check
    maxRequests: 10,    // Maximum requests within the window. 0 disables this check
    windowMinutes: 1,   // Sliding-window length in minutes. Must be >= 1
  },
}
```

Validation rules:

| Field | Type / constraint |
| --- | --- |
| `delayMs` | Non-negative finite number |
| `maxRequests` | Non-negative finite number |
| `windowMinutes` | Finite number >= 1 |

Invalid values cause a load-time error, which is shown at the top of [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md).

#### Behavior on Limit Exceeded

When `env.FETCH` is rejected by rate limiting, an Error is thrown inside the plugin. **Do not catch it — let it bubble up.** The host then handles it in a context-appropriate way:

- Interactive contexts ([Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md), [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md)) — a modal dialog displays a countdown of remaining seconds and auto-retries when it reaches 0. The user can pick Cancel to abort, or **Force Reset** to clear the limiter's history and retry immediately
- Automatic consecutive execution ([Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) `.Edit()`, `env.PLUGINEDIT`) — the marker `[Plugin rate limited — retry in Ns]` is embedded in the output text (Force Reset cannot reach this path, so runaway-script protection is preserved)

```js
async function edit(text, settings) {
  // Just call fetch normally. The rate-limit exception is handled by the host.
  var response = await env.FETCH("https://api.example.com/v1/chat", {
    method: "POST",
    body: JSON.stringify({ prompt: text }),
  });
  // ...
}
```

When a single `edit()` call issues multiple `env.FETCH` requests in a burst, the first few succeed and the rest throw at the moment the limit is hit. The natural pattern is to stop on the first failure rather than to retry-loop until every request succeeds.

## File Access

Declare `permissions: ["file"]` in metadata and grant File Access in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md) to read and write any file on the local filesystem. This is as powerful as `network` — only grant it to plugins you trust.

### Storage Location Rule

All data a custom plugin writes is **consolidated into a single location**. This keeps things simple for both plugin authors and users — uninstalling a plugin is just deleting one folder.

```
{projectFolder}/settings/plugin_data/edit/{pluginName}/
```

"Project folder" here means **the data folder of the project the user currently has open in the app**. When the user switches projects, the storage target switches with it, so plugin files are **automatically isolated per project**.

This path is the same tree the built-in plugins (Exclude Tags / Google Translate / WD14, etc.) use for their settings JSON, so **custom-plugin data follows the same convention as built-in plugins**.

> **Note**: `{projectFolder}/plugins/edit/` is purely the place where plugin source files (`.js`) live. No runtime data is stored there. Both config and snapshots end up under `settings/plugin_data/edit/{pluginName}/`.

### How to Write Paths

- **Relative paths** (e.g. `config.json`, `snapshots/foo.txt`) — automatically resolved to `{projectFolder}/settings/plugin_data/edit/{pluginName}/`. **This is what you should use by default.**
- **Absolute paths** (e.g. `C:/Users/...`) — passed through unchanged. Reserve this for the rare case where you genuinely need to step outside the rule.
- `env.pluginDataDir` — a property holding the absolute path of the directory above. Useful when you want to compose paths like `env.pluginDataDir + "/sub/foo.txt"`. For everyday use, plain relative paths are enough.

Any required parent directories are created automatically — no `mkdir` equivalent needed. To organize the directory, just include `/` in the relative path (`config/main.json`, `cache/v1/data.bin`, `snapshots/foo.txt`, etc.).

```js
// Config file
await env.writeFile("config.json", JSON.stringify({ model: "gpt-4o" }));

// Larger caches and user-saved data — organize with subfolders
await env.writeFile("snapshots/foo.txt", text);
await env.writeFile("cache/index.bin", binData);
```

### File API

| API | Description |
| --- | --- |
| `await env.readFile(path)` | Read a text file as a string |
| `await env.writeFile(path, content)` | Write a text file |
| `await env.readFileBinary(path)` | Read a binary file as a Base64 string |
| `await env.writeFileBinary(path, base64)` | Write a binary file from a Base64 string |
| `await env.fileExists(path)` | Check whether a file exists (`true`/`false`) |
| `await env.deleteFile(path)` | Delete a file |
| `await env.listFiles(dir?)` | List file names in a directory; returns `[]` for non-existent dirs |
| `env.pluginDataDir` | Absolute path to the plugin data directory (property; also the default base for relative paths) |

```js
export default {
  name: "Snapshot",
  pluginName: "Snapshot",
  tooltip: "Save / load the current prompt",
  permissions: ["file"],
  settings: [
    { key: "mode", type: "select", label: "Action", default: "save",
      options: [
        { label: "Save", value: "save" },
        { label: "Load", value: "load" }
      ], contexts: ["editor", "batch"] },
    { key: "name", type: "text", label: "Name", default: "",
      contexts: ["editor", "batch"] }
  ]
}

async function edit(text, settings) {
  var path = "snapshots/" + settings.name + ".txt";
  if (settings.mode === "save") {
    await env.writeFile(path, text);
    return text + "\n[saved as " + settings.name + "]";
  }
  if (await env.fileExists(path)) {
    return await env.readFile(path);
  }
  return text + "\n[not found]";
}
```

The example above uses relative paths, so files are saved under `{projectFolder}/settings/plugin_data/edit/Snapshot/snapshots/` — the same tree as built-in plugin settings.

## Permissions

Custom plugin permissions are managed individually in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md).

| Permission | Description |
| --- | --- |
| **Network Access** | Allow `env.FETCH` usage |
| **Secret Access** | Allow `env.getSecret` usage |
| **File Access** | Allow `env.readFile` / `env.writeFile` and other read/write operations across the entire filesystem, and also allow `dropzone` fields to receive files |

Permissions are disabled by default. Only permissions declared in plugin metadata are shown in the UI.

**File permission and dropzone**: The `dropzone` field type is strictly gated by the `file` permission. When the user turns `file` OFF, dropzone fields are greyed out and reject drops. This keeps the trust model consistent: turning `file` OFF disables every file-related behavior.

### Automatic Reset on File Changes

When a plugin file's contents are modified, its permissions are automatically reset and the plugin is disabled. This is detected both at app startup and when reloading plugins. To use the plugin again after changes, you must re-grant permissions and enable the checkbox in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md).

## Plugin Management

### Adding Plugins

1. Click "Open Plugin Folder" in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md) dialog
2. Place `.js` files in the folder
3. Click "Reload Plugins"

### Bundling a Plugin Set into a Folder

If you want to distribute or manage multiple custom plugins as a set, create a **single-level subfolder** directly under `plugins/edit/` and place the `.js` files inside it.

```
plugins/edit/
├── MyPlugin.js              ← loaded
└── MyPluginSet/
    ├── plugin1.js           ← loaded
    ├── plugin2.js           ← loaded
    └── deeper/
        └── nested.js        ← not loaded (two or more levels deep are ignored)
```

Deleting the folder uninstalls the whole set in one step. Loading is limited to the **immediate subfolder level** — `.js` files in any deeper nested directory are not loaded. Note that `pluginName` must still be unique across every plugin, so duplicates produce an error even when they live in separate folders.

### Hot Reload

Reload plugins without restarting the app using the "Reload Plugins" button in [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md). File additions, changes, and deletions are all reflected. Plugins with changed file contents will have their permissions reset and be disabled.

### Error Checking

Plugins that failed to load show error information at the top of the [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md) dialog.

### Runtime Error Notification

Use `throw new Error(...)` in the `edit()` function to show an error message as a toast notification at the bottom-right of the screen. Silently returning the original text with `return` will cause errors to be ignored without any user notification. Always use `throw` when an error occurs.

```js
// ✅ Recommended: Use throw to notify errors
if (!apiKey) {
  throw new Error("API key is not configured.");
}

// ❌ Not recommended: Silently return original text
if (!apiKey) {
  return text;
}
```

## Full Example

Working complete plugin examples are collected in [Custom Plugin Samples](03-Custom%20Plugin%20Samples.md). Each example focuses on a different feature set — AI integration (Gemini), file API + per-context dialog filtering (Snapshot Manager), and so on.

## Related

- [Custom Plugin Samples](03-Custom%20Plugin%20Samples.md)
- [Plugin](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [API Key Settings](../04-Menu/09-API%20Key%20Settings.md)
- [Rate Limiting](../02-Glossary/06-Rate%20Limiting.md)
- [Sandbox](../02-Glossary/03-Sandbox.md)
- [Programmable Edit](../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/18-Programmable%20Edit.md)
- [Copy Dropped Images](../04-Menu/12-Copy%20dropped%20images%20to%20Images%20folder.md)
- [Initial Setup](01-Recommended%20Initial%20Settings.md)
