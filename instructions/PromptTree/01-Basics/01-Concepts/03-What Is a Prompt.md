# What Is a Prompt

## Overview

A prompt (chunk) is the smallest unit of text material used for AI image generation.

It is managed within a tree, and prompts selected with [Check State](01-Understanding%20Check%20State.md) are combined to [Generation](../../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md) the final prompt.

## Prompt Components

Each prompt has the following information:

- **Name**: The identifying name displayed in the tree
- **Content**: The actual prompt text
- **Tags**: Classification labels (multiple allowed)
- **Memos**: Supplementary descriptions
- **Images**: Reference images (multiple allowed)

Name is required, but everything else including content is optional.

## Types of Prompts

Prompts are distinguished by their display icon.

### Normal Prompt

- **Icon**: Gray/white file icon
- **Purpose**: Standard prompt material
- **Features**: Basic element that holds text content

### Group Prompt

- **Icon**: Green folder icon
- **Purpose**: Folder for grouping related prompts
- **Features**: For organization. Can also have content

### File Prompt

- **Icon**: Purple file icon
- **Purpose**: Prompts added from the file system
- **Features**: Maintains association with the original file (base file)


### Folder Prompt

- **Icon**: Orange folder icon
- **Purpose**: Folders added from the file system
- **Features**: Reflects directory structure


## Difference Between Name and Content

- **Name**: For identification on the tree. Assign a human-readable name
- **Content**: The text actually used in generation. The actual prompt passed to AI

**Example**:
- Name: "Blonde Long"
- Content: `blonde hair, long hair, flowing hair`

## Changing Icons

Normal prompts and group prompts can have their type (icon) changed later.

1. Right-click the prompt
2. Select the **Change Icon** submenu
3. Select **Set as Normal Prompt** or **Set as Group**

**Note**: File prompts and folder prompts cannot have their icons changed.

## Related

- [Prompt](03-What%20Is%20a%20Prompt.md)
- [Check State](01-Understanding%20Check%20State.md)
- [Hierarchy](02-Understanding%20Hierarchy.md)
- [PromptTree](../03-Prompt%20Tree%20Overview.md)
- [PromptEditor](../../../PromptEditor/01-Basics/03-Prompt%20Editor.md)
- [PromptBrowser](../../../PromptBrowser/01-Basics/03-Prompt%20Browser.md)
