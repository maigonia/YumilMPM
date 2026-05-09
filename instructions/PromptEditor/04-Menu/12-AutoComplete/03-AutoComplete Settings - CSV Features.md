# AutoComplete Setting - CSV Features

**AutoComplete > Setting (CSV)**

## When to Use

- When you want to bulk import a large number of candidates like image generation tags
- When you want to backup existing candidate lists as CSV files
- When you want to flexibly map CSV columns during import

## What It Does

Bulk import/export of candidate lists using CSV files. Flexible data transformation is possible with column mapping and Virtual Columns.

## How to Use

### CSV Import
1. Click the **Import CSV** button
2. Select a CSV file
3. A preview dialog appears
4. Configure the following in the **Import Settings** section:
   - **List Name**: List name (auto-filled)
   - **Description**: Description
   - **Deduplicate by Name**: Whether to automatically remove duplicates
5. Map columns in **Column Mapping Settings**
6. Click **Import** (progress bar appears)

### Column Mapping Settings

When importing CSV, configure which CSV columns map to which fields (Name, Description, etc.).

**Basic mapping**:
- Select each CSV column via dropdown
  - `Name`: Candidate name (required)
  - `Description`: Description
  - `Genre`: Genre
  - `RelatedUrl`: Related URL
  - `RelatedFile`: Related file
  - `ImagePath`: Image path
  - `(Unused)`: Not used

**Format Feature (Advanced)**:

Using `{ColumnName}` in the Format field, you can insert and combine values from other columns.

**Example 1: Auto-generating URLs**
- CSV has `tag` and `id` columns
- Enter `https://example.com/posts/{id}` in the Format field
- Result: URLs like `https://example.com/posts/5889398` are generated with embedded ids

**Example 2: Auto-generating descriptions**
- CSV has `tag` and `category` columns
- Enter `{tag} ({category})` in the Format field
- Result: Combined tag and category like `1girl (character)`

### Virtual Column

A feature to create columns that don't exist in the CSV. Generates new values by combining existing column values.

**Usage**:
1. Click the **+ Add Virtual Column** button
2. Select a target field (Name, Description, etc.)
3. Enter a template in the **Format** field
   - Reference existing column values with `{ColumnName}`
   - Multiple columns can be combined

**Example 1: Dynamically generate URLs**
- CSV only has a `tag` column
- Create `RelatedUrl` as Virtual Column
- Format: `https://danbooru.donmai.us/posts?tags={tag}`
- Result: Danbooru links are auto-generated for each tag

**Example 2: Combine multiple columns**
- CSV has `first_name` and `last_name`
- Create `Name` as Virtual Column
- Format: `{first_name} {last_name}`
- Result: Full names like `John Smith` are generated

**Example 3: Combine with fixed text**
- CSV has a `tag` column
- Create `Description` as Virtual Column
- Format: `Tag: {tag} - Imported from database`
- Result: Descriptions like `Tag: blonde hair - Imported from database` are generated

**Tips**:
- Multiple Virtual Columns can be added
- Does not affect existing CSV columns
- Preview results before importing

### CSV Export
1. Select the list to export
2. Click the **Export CSV** button
3. Choose a save location
4. The CSV file is saved

### CSV Format
```csv
name,description,genre,relatedUrl,iconKind
1girl,A single girl,character,,Text
blonde hair,Blonde hair,hair,https://example.com/tags/blonde,Text
blue eyes,Blue eyes,eyes,,Text
```

**Column descriptions**:
- `name`: Candidate name (required)
- `description`: Description
- `genre`: Genre (default: UserDefined)
- `relatedUrl`: Related URL
- `iconKind`: Icon type (inherits list icon when omitted)

### Remove Duplicates
1. Select a list
2. Click the **Remove Duplicates** button
3. Candidates with the same `name` are deleted (only first occurrence kept)
4. The number of deletions is shown in the status bar

## Notes

### Performance
- Optimized internally even with a large number of candidates (thousands to tens of thousands)
- Progress bar is shown during CSV import
- Reducing candidates with the duplicate removal feature improves performance

### Data Storage Location
- Settings are saved in `{DataFolder}/settings/user_candidates.json.zst`
- File size is reduced 80-90% through zstd compression

## Tips

### Use CSV as Backup
- Periodically export with **Export CSV** for backup
- Reuse in other projects with **Import CSV**

## Related

- [PromptEditor](../../01-Basics/03-Prompt Editor.md)
- [AutoComplete](../../01-Basics/01-Features/01-AutoComplete.md)
- [AutoComplete Enable](01-Enable AutoComplete.md)
- [AutoComplete Setting - List](02-AutoComplete Settings - List & Candidate Management.md)
