# Restoring Check States

A set of features to restore previously saved check states.

In prompt generation, "which prompts are checked" determines the result. By saving frequently used check patterns, you can avoid manually re-checking every time.

## Favorite List

Save and restore check states within a specific category by name.

Example: If you have 10 prompts in an "Expression" category and want to switch between "Calm Expression Set" and "Intense Expression Set", save them as Favorite Lists. Then just select a list to instantly switch check states.

**How to use:**
1. Check prompts in the category as desired
2. Open `AdvancedPanel > Favorite Lists tab`
3. Click "Create New List" to save current check state
4. Click a list to restore

**Features:**
- Managed per category (Category A's lists only work in Category A)
- Create multiple lists
- Edit, delete, and reorder lists

**Using as Category Identifier Parameter:**
Favorite List can be set as a Category Identifier Filter command.
Syntax: `@@@_CategoryName.Filter(FavoriteList=ListName)_@@@`
Example: `@@@_Expression.Filter(FavoriteList=SmileSet)_@@@`

## Favorite Query

Save search conditions and batch-check search results.

Example: If you have 100 prompts in a "LoRA" category and only want to use those tagged "anime", save the search condition as a Favorite Query. Next time, one click runs the same search → batch check.

**How to use:**
1. Open `AdvancedPanel > Favorite Queries tab`
2. Click "Add New Query"
3. Enter query name and search condition, then save
4. Click saved query to run the search
5. Batch check/uncheck search results

**Difference from Favorite List:**
- Favorite List: Specify "this prompt and that prompt" explicitly
- Favorite Query: Specify "anything matching this condition" dynamically

Even if prompts are added or removed, Favorite Query automatically targets matching ones.

**Using as Category Identifier Parameter:**
Favorite Query can also be set as a Category Identifier Filter command.
Syntax: `@@@_CategoryName.Filter(FavoriteQuery=QueryName)_@@@`
Example: `@@@_LoRA.Filter(FavoriteQuery=animeStyle)_@@@`

## Check Presets

Save and restore check states across all categories at once.

Example: When "Fantasy Illustration" and "Cyberpunk Illustration" have different check settings across multiple categories, Check Presets lets you switch all category check states with one click.

**How to use:**
1. Set desired check states across all categories
2. Open `AdvancedPanel > Check Presets tab`
3. Click "Save Current State" to save
4. Click a preset to restore

**Difference from Favorite List:**
- Favorite List: Check states within one category
- Check Presets: Manage check states across all categories together

## Choosing Between the Three Features

- **Favorite List**: Switch variations within one category
- **Favorite Query**: Dynamic selection based on conditions
- **Check Presets**: Switch entire generation themes

**Combined example:**
1. Select "Fantasy" theme with Check Presets (overall setting)
2. Change "Expression" category to "Calm Set" with Favorite List (partial adjustment)
3. Generate

Use Check Presets for broad settings, Favorite List or Favorite Query for fine adjustments.
