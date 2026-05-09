# Favorite Query

## Overview

A Favorite Query stores search criteria. You can execute the saved search instantly with a single click.
In Category scope, the query is sent to the PromptTree's search panel and the search is executed.

## Saved Information

| Item | Content |
| ---- | ------- |
| Query name | User-assigned name |
| Search text | Search text |
| Search target | Name / Content / Tag / Path / Icon |
| Regex | Whether to use regex |
| Exclusion search | Whether to show items that do not match the criteria |

## Category Scope and Global Scope

Favorite Query has two scopes.

|          | Category | Global |
| -------- | -------- | ------ |
| Storage | Within each category's settings | Project-wide |
| Search range | PromptTree of the selected category | All categories (Global Search) |
| Result | PromptTree is filtered | Search results appear in the Global Search tab |

## Operations

- **Left-click**: Execute search
- **Right-click**: Edit, delete, duplicate, reorder

## Can Be Set as a Parameter for [CategoryIdentifer](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)'s [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md) Command.

(Example) @@@_Backgrounds.Filter(favoritequery=indoors)_@@@

## Related

- [Favorite Queriesタブ](../01-Basics/05-Favorite Queries Tab.md)
- [Favorite List](03-Favorite List.md)
- [Advanced Panel](../01-Basics/07-What Is Advanced Panel.md)
- [Search](../01-Basics/07-What Is Advanced Panel.md)
- [Global Search](../01-Basics/06-Global Search Search All Tab.md)
- [Filter](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/02-Action Commands/02-Filter.md)
- [Category Identifier](../../PromptEditor/02-How To Write Prompt Content/01-How To Write Category Identifier/README.md)
