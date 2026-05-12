# Introduction

Yumil MPM is a prompt-management tool for AI image generation. Before diving into the Beginner tutorials, this page covers the foundational concepts that every later topic builds on.

This document is a written walkthrough of the in-app interactive tutorial (**Utility → Tutorial → 入門編 / Introduction**). The in-app version highlights real UI elements as it explains them and is the recommended starting point. This text version is for offline reading and quick reference.

## The Three Main Panels

The primary screen is divided into three connected panels.

- **Category Tree** (left): create and organize categories of prompts. Each category groups related prompts — for example, `Pose`, `Background`, `Style`.
- **Prompt Tree** (middle): lists prompts inside the currently selected category. Each prompt is a snippet of text.
- **Prompt Editor** (right): edits the content of the currently selected prompt.

You build your prompt library by populating these three panels: add categories, add prompts inside each, write the text in the editor.

## The Core Workflow

Yumil MPM generates prompts by combining selected items from selected categories. The workflow is:

1. **Check categories** in the Category Tree. Only checked categories contribute to the output.
2. **Check prompts** inside each category's Prompt Tree. Only checked prompts are candidates for selection.
3. **Run generation** (the `Once` button). Yumil MPM walks through each checked category, picks one prompt at random from its checked candidates, and assembles the picks into a single output prompt.
4. **Use the output**: copy it, save it to a file, or send it to an external tool such as ComfyUI or SD WebUI.

The mental model: each checked category is a *slot*, the checked prompts inside it are the *candidates*, and one generation picks one candidate per slot.

> Example: if `Pose` is checked with three candidate prompts and `Background` is checked with five candidates, each generation rolls 1-of-3 × 1-of-5 to produce one combined output.

## "Selected" vs "Checked"

These are two different states and are often confused at first.

- **Selected** — single-click an item. The editor or detail panel shows that item's content. Selecting does *not* influence generation.
- **Checked** — click the small checkbox next to the item. Checks mark items for generation. Generation only reads checks.

You can select one item at a time but check any number.

## Where to Find Features

Yumil MPM does not pack features into toolbar buttons or context menus. Instead, **everything lives in the top menu**.

The top menu is organized by panel:

| Menu | Scope |
|---|---|
| File | Project file operations |
| CategoryTree | Category-tree actions |
| PromptTree | Prompt-tree actions |
| PromptEditor | Editor actions |
| PromptBrowser | Selected prompt's details (image, memo, tags) |
| PromptGeneration | Generation modes and external integrations |
| AdvancedPanel | Templates, favorites, presets |
| GlobalSettings | App settings and plugins |
| Utility | REST API, AI auto-operations, integrity check, tutorials |

When you are not sure how to do something, open the top menu first and look at the panel the action would belong to.

## Three Ways to Operate

Once you know the top menu, you can drive the app three ways.

| Method | Trigger | Best for |
|---|---|---|
| **Top menu** | Click a menu item | Exploration or rare actions |
| **Command Palette** | Press `F1`, type keywords | You know what you want but not where it is |
| **Shortcut** | Custom key combo | Actions you perform often |

Three useful menu-item interactions:

- **Alt + click** a menu item → opens a dialog to assign a keyboard shortcut for that action.
- **Ctrl + click** a menu item → adds the action as a button on the side toolbar or a panel, with a chosen icon and color. Right-click the button to rearrange or remove it.
- **Right-click** a menu item → opens the in-app instruction window to that topic.

When you are just starting out, prefer the top menu over buttons. Learning the menu structure first makes shortcuts and the command palette far easier to use later.

## What's Next

You now have the foundation. The Beginner tutorials assume you understand:

- The three-panel layout (Category Tree / Prompt Tree / Prompt Editor)
- That generation reads *checked* items, not *selected* ones
- That every feature is reachable from the top menu

Continue with [Beginner](01-Beginner/) for hands-on topics: opening the sample project, designing your tree, prompt-generation modes, and external-app integration.
