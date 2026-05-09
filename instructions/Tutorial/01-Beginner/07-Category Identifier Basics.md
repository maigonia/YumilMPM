# Category Identifier Basics

Category Identifier is a mechanism for dynamically referencing content from other categories within a prompt.

## Understanding with a Concrete Example

Suppose you have a category called "HairColor" with the following prompts:
- blonde hair ✓ (checked)
- black hair ✓ (checked)
- red hair (unchecked)

If you write `@@@_HairColor_@@@` in a prompt, it will be randomly replaced with either "blonde hair" or "black hair" at generation time (selected from checked items).

This mechanism allows you to easily switch between hair color variations.

## Basic Syntax

`@@@_CategoryName_@@@`

## When Replacement Occurs

Category Identifier replacement is performed when prompt generation (Once/Timer/OnDemand) is executed.

## Default Replacement Rule

`@@@_CategoryName_@@@` is replaced at generation time by:
"One randomly selected from CHECKED prompts in the target category's Prompt Tree"

## Benefits of Default Rule

- Easily switch generation result variations with just check operations
- Flexible generation through UI without changing code or rules

## Input Assist (Auto-complete)

Typing `@@@_` in the Prompt Editor shows available category name suggestions. Select from suggestions to prevent typos and input quickly.

## Advanced Usage

The default replacement rule can be changed. You can target only Leaf nodes, select multiple, or filter by specific conditions. See `PromptEditor > How to write Prompt Content` for details.
