# What is Programmable Block

**What is Programmable Block**

## What Is This?

Programmable Block (PB) is a feature that allows you to execute JavaScript code within prompts. It uses the same `@@@_` ... `_@@@` notation as [Category Identifier](../01-How To Write Category Identifier/README.md), but by writing JavaScript code inside, more advanced processing becomes possible.

## Auto-Detection

It uses the same notation as [Category Identifier](../01-How To Write Category Identifier/README.md), but when a **line starts** with the following keywords or symbols, it is executed as a PB:

`const` `let` `var` `function` `async` `await` `env.` `export` `for` `while` `if` `try` `class` `switch` `do` `return` `throw` `//` `/*`

> **Category name restrictions**: Names that exactly match these keywords (e.g., `try`, `return`) or that begin with one of them followed by a space and other characters (e.g., `try this`, `for me`) cannot be used as category names. Such names would break the auto-detection between CI expressions and PBs.

## Basic Syntax

```
@@@_
const result = await env.CI("Character");
env.OUTPUT(result);
_@@@
```

- `env.CI()` - Executes a Category Identifier expression
- `env.OUTPUT()` - Outputs the result

## Execution Environment

Programmable Blocks are executed in a sandboxed environment using QuickJS (WebAssembly).

- No file system or network access from the PB code itself
- Timeout protection (prevents infinite loops)
- Memory limit

### Exception: Access via Plugins

When a PB calls a plugin through [Category Identifier](../01-How To Write Category Identifier/README.md)'s `.Edit(...)` or [env.PLUGINEDIT](02-Built-in Functions/17-env.PLUGINEDIT.md), that plugin can access files or networks within the scope of permissions it has been granted.

For example, calling a translation plugin that has network permission causes external communication to occur, even though the PB code itself cannot connect to the network.

What a called plugin can do is determined by the permissions previously granted by the user in the [Plugin](../../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md) settings. Permissions that have not been granted are not used through PB either.

## env Object

The `env` object provides access to app features.

> **Naming convention**: UPPERCASE (`OUTPUT`, `CI`, `WD14`, etc.) are **functions that perform actions**, while lowercase/camelCase (`chunk`, `dataPath`, etc.) are **properties for reading data**.

### Core Functions

| Function | await | Description |
|----------|:-----:|-------------|
| [env.CI](02-Built-in Functions/02-env.CI.md) `CI(expression)` | **Required** | Executes a Category Identifier expression |
| [env.OUTPUT](02-Built-in Functions/09-env.OUTPUT.md) `OUTPUT(text)` | Not needed | Outputs text |
| [env.chunk](02-Built-in Functions/01-env.chunk.md) | - | Current chunk information object |

### Data Access

| Function | await | Description |
|----------|:-----:|-------------|
| [env.getCategory](02-Built-in Functions/04-env.getCategory.md) `getCategory(name)` | Not needed | Gets category information |
| [env.getCategoryNames](02-Built-in Functions/05-env.getCategoryNames.md) `getCategoryNames()` | Not needed | Gets all category names |
| [env.globalTags](02-Built-in Functions/06-env.globalTags.md) | - | Array of all global tag names |
| [env.HISTORY](02-Built-in Functions/07-env.HISTORY.md) `HISTORY(index, category?)` | Not needed | Gets prompt from history |

### Random Numbers

| Function | await | Description |
|----------|:-----:|-------------|
| [env.RANDOM](02-Built-in Functions/11-env.RANDOM.md) `RANDOM()` | Not needed | Random number 0-1 |
| [env.RANDINT](02-Built-in Functions/10-env.RANDINT.md) `RANDINT(min, max)` | Not needed | Random number in range (supports integers and floats) |
| [env.SEED](02-Built-in Functions/12-env.SEED.md) `SEED(n)` | Not needed | Set random seed |

### AI Features

| Function | await | Description |
|----------|:-----:|-------------|
| [env.LMEDIT](02-Built-in Functions/08-env.LMEDIT.md) `LMEDIT(...)` | **Required** | Edit text with LM Studio |
| [env.EMBED](02-Built-in Functions/03-env.EMBED.md) `EMBED(text)` | **Required** | Get text embedding vector |
| [env.SIMILARITY](02-Built-in Functions/13-env.SIMILARITY.md) `SIMILARITY(vec1, vec2)` | Not needed | Calculate cosine similarity |
| [env.WD14](02-Built-in Functions/14-env.WD14.md) `WD14(imagePath)` | **Required** | Extract tags from image |

### Plugin Invocation

| Function | await | Description |
|----------|:-----:|-------------|
| [env.PLUGINEDIT](02-Built-in Functions/17-env.PLUGINEDIT.md) `PLUGINEDIT(text, spec)` | **Required** | Call an Edit plugin directly (CI-compatible syntax) |

> **Plugin enablement required**: `env.PLUGINEDIT` can only invoke plugins that are enabled in the **Programmable Block** tab of [EditPlugin Settings](../../../GlobalSettings/04-Menu/03-EditPlugin Settings/01-EditPlugin Settings.md). `LMStudioEdit`, `WD14 Tagger`, and `Programmable Edit` are not registered in the PB context at all (use [env.LMEDIT](02-Built-in Functions/08-env.LMEDIT.md) / [env.WD14](02-Built-in Functions/14-env.WD14.md) instead). When you invoke an Edit plugin via `env.CI("Cat.Edit(...)")`, the **Category Identifier / CT** tab settings apply — the PB tab is independent.

## Usage Examples

### Basic Output

```javascript
@@@_
const character = await env.CI("Character");
const background = await env.CI("Background");
env.OUTPUT(character + ", " + background);
_@@@
```

### Conditional Branching

```javascript
@@@_
const tags = env.chunk.tags;
if (tags.includes("outdoor")) {
  env.OUTPUT(await env.CI("OutdoorBackground"));
} else {
  env.OUTPUT(await env.CI("IndoorBackground"));
}
_@@@
```

### Random Selection

```javascript
@@@_
const options = ["happy", "sad", "angry", "surprised"];
const index = env.RANDINT(0, options.length - 1);
env.OUTPUT(options[index] + " expression");
_@@@
```

### Loop Processing

```javascript
@@@_
const categories = env.getCategoryNames();
let results = [];
for (const cat of categories) {
  if (cat.startsWith("Effect")) {
    results.push(await env.CI(cat));
  }
}
env.OUTPUT(results.join(", "));
_@@@
```

### AI Editing

```javascript
@@@_
const content = await env.CI("Story");
const summary = await env.LMEDIT("summarize", content);
env.OUTPUT(summary);
_@@@
```

## Important Notes

### Functions That Require await

The following functions are asynchronous and require `await`:

- `env.CI()` - Category Identifier execution
- `env.LMEDIT()` - LM Studio editing
- `env.EMBED()` - Embedding vector retrieval
- `env.WD14()` - Image tag extraction
- `env.PLUGINEDIT()` - Edit plugin invocation

```javascript
// Correct
const result = await env.CI("Character");

// Wrong (returns a Promise object)
const result = env.CI("Character");
```

### Other

- **Output required**: Nothing is output unless `env.OUTPUT()` is called
- **Timeout**: Long-running processes are interrupted by timeout
- **Error handling**: Errors can be handled with try-catch

## Related

- [Programmable Block](README.md)
- [Sandbox](../../../GlobalSettings/02-Glossary/03-Sandbox.md)
- [Sandbox Settings](../../../GlobalSettings/04-Menu/07-Sandbox Settings.md)
- [Category Identifier](../01-How To Write Category Identifier/README.md)
- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [Generation](../../../PromptGeneration/01-Basics/03-About Prompt Generation.md)
- [env.CI](02-Built-in Functions/02-env.CI.md)
- [env.OUTPUT](02-Built-in Functions/09-env.OUTPUT.md)
- [env.chunk](02-Built-in Functions/01-env.chunk.md)
- [env.LMEDIT](02-Built-in Functions/08-env.LMEDIT.md)
- [env.EMBED](02-Built-in Functions/03-env.EMBED.md)
- [env.PLUGINEDIT](02-Built-in Functions/17-env.PLUGINEDIT.md)
