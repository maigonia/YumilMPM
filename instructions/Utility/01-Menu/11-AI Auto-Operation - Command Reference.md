# AI Auto-Operation - Command Reference
**AI Auto-Operation - Command Reference**

## When to Use
- When you want to know what you can ask Claude Code to do
- When you're not sure how to phrase specific instructions

## Available Operations

Once the AI Auto-Operation setup is complete, you can instruct the following operations via chat. Simply give instructions in natural language, and the AI will choose the appropriate tool and execute it.

### Project Information

| Operation | Example Command |
|-----------|-----------------|
| View project overview | "Show me the project info" |
| View category list | "List all categories" |
| View category details | "Show details for the Style category" |
| View category folder structure | "Show the folder hierarchy of the Quality category" |
| View tag list | "List all registered tags" |

### Browsing & Searching Prompts

| Operation | Example Command |
|-----------|-----------------|
| List prompts | "List all prompts in Quality" |
| List leaf prompts only | "Show only leaf prompts in Style" |
| View checked prompts | "Show checked prompts in Quality" |
| View prompt content | "Show me the details of perfect anatomy" |
| View multiple prompts at once | "Get the content of these prompt IDs together" |
| Search prompts | "Search for prompts containing sakura" |
| Regex search | "Search for prompts whose name starts with \"^lora\"" |
| Search by tag | "Find prompts tagged with \"landscape\"" |
| Search by path | "Find prompts with \"Best Settings\" in their path" |
| Search within category | "Search for \"anime\" in the Style category" |
| Exclusion search | "Show prompts in LoraUtility whose name doesn't contain \"test\"" |

### Adding & Editing Prompts

| Operation | Example Command |
|-----------|-----------------|
| Add a prompt | "Add a prompt called \"masterpiece\" to Quality" |
| Edit prompt content | "Change best quality's content to \"best quality, amazing\"" |
| Rename a prompt | "Rename that prompt to \"high quality\"" |
| Set tags | "Add the tag \"important\" to best quality" |
| Set memos | "Add a memo \"use again next time\" to best quality" |
| Set images | "Set a reference image path on best quality" |
| Add a category | "Create a category named \"Effects\"" |

### Selecting Prompts

| Operation | Example Command |
|-----------|-----------------|
| Check a specific prompt | "Check best quality in Quality" |
| Uncheck a specific prompt | "Uncheck perfect anatomy" |
| Check all in category | "Check all prompts in Style" |
| Uncheck all in category | "Uncheck all in Quality" |

### Check Presets

| Operation | Example Command |
|-----------|-----------------|
| View preset list | "List check presets" |
| Apply a preset | "Apply the \"Base\" preset" |
| Save current state as preset | "Save the current check state as \"My Favorite Set\"" |

### Favorite Lists

| Operation | Example Command |
|-----------|-----------------|
| View favorite lists | "Show favorite lists for the Style category" |
| Apply a favorite list | "Apply that favorite list to check prompts" |

### Category Output & Template Settings

| Operation | Example Command |
|-----------|-----------------|
| Enable category output | "Turn on output for the Style category" |
| Disable category output | "Disable output for Quality" |
| Check template settings | "Show all category template settings" |
| Change template | "Set Style's target to allleaves and pick to random=3" |
| Configure Final Edit | "Enable Final Edit with TrimWhitespaceEachLine for Style" |

### Queue Patterns

Queue patterns let you register multiple check states in advance and execute generation in sequence.

| Operation | Example Command |
|-----------|-----------------|
| View pattern list | "List queue patterns" |
| View pattern details | "Show details of that pattern" |
| Create Standard pattern | "Create a Standard pattern with the current check state" |
| Create Sequential pattern | "Create a Sequential pattern named \"Character Variations\"" |
| Create Loop pattern | "Create a Loop pattern with 3 loops" |
| Add a snapshot | "Add the current check state as \"Setting A\" to that pattern" |
| Remove a snapshot | "Remove the 2nd item from the pattern" |
| Select a pattern | "Select that pattern" |
| Deselect a pattern | "Deselect the pattern" |
| Reset a pattern | "Reset the pattern's progress" |
| Delete a pattern | "Delete that pattern" |

**Pattern Type Differences:**
- **Standard**: Inserts the current check state once. Auto-removed after generation
- **Sequential**: Executes multiple check states in order. One at a time, top to bottom
- **Loop**: Executes multiple check states repeatedly. Loops a specified number of times

**Typical Usage (Sequential):**
1. Apply Check Preset A → Add to pattern
2. Apply Check Preset B → Add to pattern
3. Select pattern → Execute generation (1st run uses A, 2nd run uses B)

### Generation

| Operation | Example Command |
|-----------|-----------------|
| Generation preview (dry run) | "Preview the generation results" |
| Generate prompts | "Execute generation" |
| Evaluate CI expression | "Evaluate Quality.Target(allLeaves).Pick(random=3)" |
| View generation history | "Show recent generation history" |

### Instruction Reference

Tools for the AI to investigate this app's features and specifications on its own. Users rarely use these directly, but the AI automatically uses them when performing advanced operations (such as creating CI expressions or Programmable Blocks).

| Operation | Example Command |
|-----------|-----------------|
| View instruction types | "List what kinds of instructions are available" |
| View instruction tree | "Show the instruction structure for promptGeneration" |
| Read instruction content | "Read the instruction on how to use CI" |
| Search instructions | "Search instructions for Programmable Block" |

## Combined Instructions

You can also give multiple operations at once:

- "I want a 3-part story. Create a Sequential pattern, add the \"Introduction\", \"Development\", and \"Climax\" presets in order, then generate"
- "Review the generation history, come up with the next scene as a continuation, and run generation 5 times in a row"

## Advanced Usage Example: Automated Scene Generator Creation

AI can use the instruction reference feature to investigate CI and Programmable Block specifications on its own and automatically create advanced prompts.

### User's Instruction

> Use CI and Programmable Blocks to create a single prompt in the PositivePrompt category that can generate various cases

### Steps Taken by AI

1. **Investigated instructions** — Referenced specifications for Category Identifier, Programmable Block, Filter, Pick, etc.
2. **Analyzed project structure** — Understood the folder structure and prompt content of all categories
3. **Designed & implemented** — Created a Programmable Block with 5 scene types (portrait / action / fantasy / everyday / dramatic)
4. **Verified** — Executed generation multiple times and confirmed consistent output for each scene

### How the AI-Created Prompt Works

- `env.RANDINT()` randomly selects one of 5 scene types
- Follows a constraint map defined per scene to select **thematically consistent elements** from each category
- Passes **dynamically constructed CI expressions** to `env.CI()` (e.g., replacing folder names with variables)
- Uses `Target(allLeaves)` + `Filter(treePath=folder name/**)` to leverage folder structure as filters
- Uses `Filter(name*=regex)` to narrow down clothing and accessories matching the scene

### Code Created by AI

```
@@@_
const S=["portrait","action","fantasy","everyday","dramatic"];
const s=S[env.RANDINT(0,S.length-1)];
function pk(a){return a[env.RANDINT(0,a.length-1)];}
async function ci(cat,path,ex,n){
let q=cat+".Target(allLeaves)";
if(path)q+=".Filter(treePath=Root/"+path+"/**)";
if(ex)q+=".Filter(name*="+ex+")";
q+=".Pick(random="+(n||1)+")";
if(n>1)q+=".Join(, )";
return await env.CI(q);
}
const q=await ci("Quality","Base Quality",0,2);
const r=await ci("Quality","Resolution");
const d=await ci("Quality","Detail",0,2);
const hc=await ci("Character","Hair Color");
const hs=await ci("Character","Hair Style");
const ec=await ci("Character","Eye Color");
const C={
portrait:[0,0,["Upper Body"],["Happy","Cool","Shy"],["Indoor","Abstract"],
  ["Natural Light","Studio"],["Anime Style (1)","Realistic"],
  "portrait|upper body|close-up"],
action:[0,"",["Action"],["Intense"],["Outdoor"],["Dramatic"],
  ["Anime Style (1)"],"dynamic|wide|full body"],
fantasy:["armor|kimono|gothic","wings|gloves|choker",
  ["Standing (1)","Action"],["Cool","Intense"],["Fantasy"],["Dramatic"],
  ["Anime Style (1)","Artistic"],0],
everyday:["school uniform|hoodie|white dress|maid",
  "ribbon|glasses|scarf|hair ornament",["Standing (1)","Sitting (1)"],
  ["Happy","Shy"],["Indoor","Outdoor"],["Natural Light"],
  ["Anime Style (1)"],0],
dramatic:[0,0,["Standing (1)","Sitting (1)","Lying","Action"],
  ["Sad","Cool","Intense"],0,["Dramatic"],
  ["Realistic","Artistic"],"cinematic|depth|bokeh"]
};
const c=C[s];
const cl=await ci("Character","Clothing",c[0]);
const ac=c[1]===""?"":await ci("Character","Accessories",c[1]);
const po=await ci("Pose",pk(c[2]));
const ex=await ci("Expression",pk(c[3]));
const bg=c[4]?await ci("Background",pk(c[4])):await ci("Background");
const li=await ci("Lighting",pk(c[5]));
const st=await ci("Style",pk(c[6]));
const co=c[7]?await ci("Quality","Composition",c[7])
  :await ci("Quality","Composition");
env.OUTPUT([q,r,st,"1girl",hc,hs,ec,cl,ac,ex,po,bg,li,d,co]
  .filter(p=>p&&p.trim()!=="").join(", "));
_@@@
```

> **Note**: This example was executed with Claude Code (Claude Opus). The output quality of AI Auto-Operation depends heavily on the AI client and model performance used. Advanced code generation and CI expression design require a model with sufficient reasoning capability.

## Notes

- Instructions can be given in natural language. The table above is just examples
- AI uses prompt IDs internally, but users can give instructions using prompt names
- If the AI is unsure about something, it will ask you
- Operation results are displayed in the chat and reflected in this app's UI in real-time

## Related

- [AI Auto-Operation](08-AI%20Auto-Operation.md)
- [Generation](../../PromptGeneration/01-Basics/03-About%20Prompt%20Generation.md)
- [On Demand](../../PromptGeneration/04-Menu/02-Generation%20On%20Demand/README.md)
