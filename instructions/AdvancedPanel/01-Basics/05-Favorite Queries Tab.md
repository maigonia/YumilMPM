# Favorite Queries Tab

A tab for managing [FavoriteQuery](../02-Glossary/04-Favorite%20Query.md)s.
This allows you to save search criteria and re-execute them with a single click. Available in both Category scope and Global scope.

## When Is It Useful

- When you use the same search criteria repeatedly
- When you want to quickly filter prompts with specific tags or keywords

## Basic Usage

### Adding a Query

1. Click the **Add New** button (or select "Add New" from the right-click menu)
2. The query editing dialog opens
3. Configure the following and save:

| Setting | Description |
| ------- | ----------- |
| Query name | Display name |
| Search text | Search text |
| Search target | Name / Content / Tag / Path / Icon |
| Regex | Whether to search as a regular expression |
| Exclusion search | Whether to show items that do "not" match the criteria |

### Executing a Query

Click a query in the list to execute the search with the saved criteria.

- **Category scope**: The PromptTree is filtered, showing only prompts matching the criteria
- **Global scope**: Switches to the Global Search (Search All) tab and displays cross-category search results

### Managing Queries

Right-click a query in the list to display the management menu.

| Menu | Function |
| ---- | -------- |
| Edit | Edit the query's search criteria |
| Delete | Delete the query |
| Clone | Duplicate the query |
| Move Up / Move Down | Change display order |

### Keyboard Navigation

- **↑ / ↓**: Navigate within the list
- **Enter**: Execute the selected query

## Difference Between Category Scope and Global Scope

|          | Category | Global |
| -------- | -------- | ------ |
| Storage | Within category settings | Project-wide |
| Search range | PromptTree of the selected category | All categories |
| Result | PromptTree filtering | Global Search results display |

## Related

- [Favorite Query](../02-Glossary/04-Favorite%20Query.md)
- [Advanced Panel](07-What%20Is%20Advanced%20Panel.md)
- [Search](07-What%20Is%20Advanced%20Panel.md)
- [Global Search](06-Global%20Search%20Search%20All%20Tab.md)
- [Filter](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/02-Filter.md)
