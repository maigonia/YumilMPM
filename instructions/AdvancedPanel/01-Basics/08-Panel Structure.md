# Panel Structure

## Display Position

The Advanced Panel is displayed below the PromptTree. It occupies the lower half of the left panel area, split vertically with the PromptTree.

## Panel Layout

```
┌──────────────────────────────────────────────┐
│ Advanced Panel    [Category] [Global]        │ ← Scope switch bar
├──────────────────────────────────────────────┤
│ Checked │ Category Template │ Fav Queries │ … │ ← Tab bar
├──────────────────────────────────────────────┤
│                                              │
│              Tab content                      │
│                                              │
└──────────────────────────────────────────────┘
```

## Switching Scopes

Switch scopes using the **Category** / **Global** buttons at the top of the panel.

- Selecting **Category** displays 4 tabs in the tab bar: Checked / Category Template / Favorite Queries / Favorite Lists
- Selecting **Global** displays 3 tabs in the tab bar: Search All / Favorite Queries / Check Presets

The panel border color changes by scope:
- Category: Normal border
- Global: Indigo (blue-purple) border

## Category Scope Notes

Category scope requires a category to be selected. If no category is selected, a message "Please select a category" is displayed.

Global scope does not require category selection.

## Switching Tabs

Click each tab name to switch tabs. The active tab is highlighted with a blue (Category) or indigo (Global) underline.

## Related

- [Advanced Panel](07-What Is Advanced Panel.md)
- [Category Template](../02-Glossary/01-Category Template.md)
- [Favorite Query](../02-Glossary/04-Favorite Query.md)
- [Favorite List](../02-Glossary/03-Favorite List.md)
- [Check Preset](../02-Glossary/02-Check Preset.md)
- [Global Search](06-Global Search Search All Tab.md)
- [Show Advanced Panel](../04-Menu/01-Show AdvancedPanel.md)
