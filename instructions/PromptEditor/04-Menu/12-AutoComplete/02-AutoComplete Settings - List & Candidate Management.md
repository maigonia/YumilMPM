# AutoComplete Setting - List & Candidate Management

**AutoComplete > Setting**

## When to Use

- When you want to create your own autocomplete candidate lists
- When you want to add descriptions or URLs to frequently used tags
- When you want to use multiple lists for different purposes (for characters, for backgrounds, etc.)
- When you want to bulk delete duplicate candidates

**Example**: Create a list of frequently used character tags so candidates appear with descriptions in the editor.

## What It Does

Manages autocomplete candidate lists. You can create multiple lists and add custom candidates to each. Each list can be individually toggled on/off and assigned an icon.

**Main features**:
- Create and manage multiple lists
- Add, edit, and delete candidates (inline editing support)
- Set icons per list (choose from 24 types)
- Toggle lists/candidates on/off
- Clone lists

For CSV import/export, see [AutoComplete Setting - CSV](03-AutoComplete%20Settings%20-%20CSV%20Features.md).

## How to Use

### Basic Flow

1. Select **PromptEditor > AutoComplete > Setting** from the menu
2. A dialog appears (left: list view, right: candidate editing)
3. Create/select lists in the left panel
4. Edit the selected list's information and candidates in the right panel
5. Click **Save and Close** to save

### List Management (Left Panel)

#### Create New List
1. Click the **New** button
2. Enter **List Name** and **Description** in the right panel
3. Click **Save** to save

#### Enable/Disable Lists
- Click the checkbox on the left side of each list
- Candidates from disabled lists are not shown in autocomplete

#### Clone a List
1. Select the list to clone
2. Click the **Clone** button
3. A copy is created with the name "OriginalName_Copy"

#### Delete a List
1. Select the list to delete
2. Click the **Delete** button
3. Click **OK** in the confirmation dialog

### List Detail Settings (Right Panel Top)

When a list is selected, you can edit the following items:

- **List Name**: Name of the list
- **Description**: Description of the list
- **Icon**: Icon displayed during suggestions (choose from 24 types)
  - Snippet (Default), Text, Keyword, Variable, Field, Property
  - Function, Method, Class, Interface, Module, Enum, EnumMember
  - Constant, Struct, Event, Operator, Color, File, Folder
  - Reference, Value, Unit, Constructor, TypeParameter
- **Enabled**: Enable/disable the list

Click the **Save** button to save after making changes.

### Candidate Editing (Right Panel Bottom)

#### Add a Candidate
1. Click the **Add Candidate** button
2. "New Item" is added at the end of the table
3. Click each field to edit

#### Edit Candidates (Inline Editing)
Click directly on each candidate's items to edit:

- **Name**: Candidate name (displayed text, inserted string)
- **Description**: Candidate description (shown during suggestions)
- **Genre**: Genre classification (e.g., character, hair, background)
- **RelatedUrl**: Related URL (can be opened with Ctrl+Enter)
- **Enabled**: Enable/disable candidate (checkbox)

Changes are automatically saved when focus is lost.

#### Delete Candidates
1. Select the checkbox on the left side of candidates to delete
2. Click the **Delete Selected (N)** button (N is the selection count)
3. Click **OK** in the confirmation dialog

## Notes

### List and Candidate Enable/Disable
- **Disabling a list**: Hides all candidates in that list
- **Disabling a candidate**: Hides only that individual candidate
- Even if the list is enabled, disabled candidates are not shown

### Same-Name Candidates
- If candidates with the same name exist in different lists, all are displayed
- Duplicates within the same list can be removed with **Remove Duplicates**

## Tips

### Separate Lists by Purpose
Create multiple lists and manage by purpose:
- "Character tags"
- "Background tags"
- "Art style tags"
- "Pose tags"

Toggle lists on/off as needed to narrow down candidates.

### Visually Distinguish with Icons
Setting icons per list makes it easy to identify the source of candidates during suggestions:
- Character: Class icon
- Tags: Text icon
- Functions: Function icon

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [AutoComplete](../../01-Basics/01-Features/01-AutoComplete.md)
- [AutoComplete Enable](01-Enable%20AutoComplete.md)
- [AutoComplete Setting - CSV](03-AutoComplete%20Settings%20-%20CSV%20Features.md)
