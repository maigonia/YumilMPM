# SyntaxHighlight Setting

**SyntaxHighlight > Setting**

## When to Use

- When you want to add new highlighting rules
- When you want to edit or delete existing rules
- When you want to adjust rule priority
- When you want to highlight text with custom colors

## What It Does

Create, edit, and delete syntax highlighting rules. By specifying patterns (strings or regular expressions) and colors, text in the editor is automatically colored.

## Main Feature Details

### Pattern Matching

Two matching modes are available:

- **String mode** (default): Exact match with the specified text
  - Example: `IMPORTANT` → Matches the string "IMPORTANT"
  - Case sensitivity: Toggleable (default is case insensitive)

- **Regex mode**: Flexible matching with JavaScript regex syntax
  - Example: `@@@_.*?_@@@` → Matches all Category Identifier formats
  - Example: `#.*` → Matches entire lines starting with #
  - Example: `<.*?>` → Matches `<tag>` format tags

### Color Customization

Specify colors with hexadecimal color codes (Hex).

- Format: `#RRGGBB`
- Examples:
  - `#FF6B6B` - Red (default)
  - `#4ECDC4` - Cyan
  - `#95E1D3` - Light green
  - `#FFD93D` - Yellow
  - `#A8E6CF` - Mint green

A color picker allows intuitive color selection.

### Case Sensitivity

Configurable individually for each rule.

- **Case insensitive** (default): `important` and `IMPORTANT` are treated the same
- **Case sensitive**: `important` and `IMPORTANT` are treated differently

### Priority System

When multiple rules match the same text, **the color of the later rule takes priority**.

Example:

1. Rule 1: `category` → Red
2. Rule 2: `cat` → Blue

For the text "category":

- Rule 1 matches → Displayed in red
- Rule 2 also matches → Overwritten with blue
- **Result**: Displayed in blue

Move rules up and down in the list to adjust priority.

### Real-time Application

- **Instant reflection**: When rules are added or changed, they are immediately applied to the editor
- **Active during editing**: Highlighting auto-updates while typing
- **Performance**: Complex regular expressions or many rules may slow processing

## Basic Usage

### 1. Open the Settings Screen

Open **PromptEditor > SyntaxHighlight > Setting** from the menu.

### 2. Create a Highlighting Rule

1. Click the **Add Rule** button
2. **Pattern**: Enter the text or regular expression to match
3. **Color**: Select a color with the color picker
4. **Case Sensitive**: Check to distinguish case
5. **Use Regex**: Check to use regular expressions
6. Click **Save** to save

### 3. Adjust Priority

In the rule list on the Settings screen:

- **Up button**: Move rule up (lower priority)
- **Down button**: Move rule down (higher priority)

### 4. Edit/Delete Rules

- **Edit**: Click a rule to change its content
- **Delete**: Click the X button to delete a rule

## Usage Examples

### Example 1: Highlight Category Identifiers

```
Pattern: @@@_.*?_@@@
Color: #4ECDC4 (cyan)
Case Sensitive: No
Use Regex: Yes
```

Effect: `@@@_Character_@@@`, `@@@_Background_@@@`, etc. are all displayed in cyan

### Example 2: Gray Out Comment Lines

```
Pattern: #.*
Color: #999999 (gray)
Case Sensitive: No
Use Regex: Yes
```

Effect: Lines like `# This is a comment` are displayed in gray

### Example 3: Highlight Important Keywords in Red

```
Pattern: IMPORTANT
Color: #FF0000 (red)
Case Sensitive: Yes
Use Regex: No
```

Effect: Only uppercase "IMPORTANT" is displayed in red

### Example 4: Highlight HTML Tags in Blue

```
Pattern: <.*?>
Color: #0066CC (blue)
Case Sensitive: No
Use Regex: Yes
```

Effect: Tags like `<start>`, `<end>` are displayed in blue

## Common Regex Patterns

Frequently used patterns when using regex mode:

- `.` - Any single character
- `*` - Zero or more repetitions
- `+` - One or more repetitions
- `?` - Zero or one occurrence
- `^` - Start of line
- `$` - End of line
- `\d` - Digit
- `\w` - Alphanumeric character

## Notes

### Performance

- Having too many rules (50+) may slow down performance
- Overly complex regular expressions may slow processing
- If it feels slow, reduce rules or temporarily turn off the feature

### When Using Regular Expressions

- To search for special characters (`. * + ? ^ $ { } ( ) | [ ] \\`) literally, prefix with `\\`
  - Example: To search for `.` → Enter `\\.`
- If regex is invalid, an error is displayed on save

### About Priority

When multiple rules match the same text, **the color of rules lower in the list (later rules) takes priority**.

Example: For the text "category"

- Rule 1: `cat` → Red
- Rule 2: `category` → Blue

Result: The entire word "category" is displayed in blue (Rule 2 takes priority)

## Tips

### 1. Start Simple

Start with string matching (regex off) and use regular expressions once you're comfortable.

### 2. Choose Visible Colors

- **Dark theme**: Brighter colors are recommended
- **Light theme**: Slightly darker colors are recommended

### 3. Place Important Rules at the Bottom

When multiple rules match the same text, the color of rules at the bottom takes priority. Place more important rules at the bottom.

### 4. Temporarily Turn Off

When highlighting is not needed, simply uncheck Enable in the menu. You don't need to delete rules.

### 5. Color-Code by Category

Color-coding Category Identifiers by type makes prompt structure easier to understand.

Example:

- Character-related: Red tones
- Background-related: Blue tones
- Effect-related: Green tones

## Related

- [PromptEditor](../../01-Basics/03-Prompt%20Editor.md)
- [SyntaxHighlight](../../01-Basics/01-Features/07-SyntaxHighlight.md)
- [SyntaxHighlight Enable](01-Enable%20SyntaxHighlight.md)
