# Prompt Tree Design Guidelines

There are no strict rules for Prompt Tree structure, but adopting the following design pattern makes it easier to use convenient features.

## Folder/File Structure Concept

- Folder equivalent: Nodes with children → Classification only (don't write prompt content)
- File equivalent: Nodes without children (Leaf) → Write actual prompt content

In this app, nodes without children are called "Leaf nodes".

## Benefits of This Structure

- Separating classification and prompt roles enables batch operations tailored to each role
- `PromptTree > Selected: Check/Uncheck > Leaf Prompts` allows batch check/uncheck of Leaves only
- Category Identifier (explained later) can target only Leaves
- Add From FileSystem feature can import folder structures directly into the tree

## Setting Group Icon

Classification nodes (folder equivalent) can have their icon changed for visual distinction:
`Right-click > Selected > Change Icon > Set as Group`
