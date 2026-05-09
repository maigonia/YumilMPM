# AI Image Recognition (WD14 / LM Vision)

Two AI image recognition features available, use based on purpose.

## WD14 Tagger

Automatically extracts tags (words) from images.

Example:
- Input: character.png
- Output: `girl, long_hair, blue_eyes, smile, school_uniform`

**Configurable parameters:**
- General Threshold (0.35): Detection threshold for general objects
- Character Threshold (0.85): Detection threshold for character attributes
- Max Tags: Maximum number of tags to output

**Access:**
- For adding: `PromptTree > Selected: Add > Add from WD14`
- For editing: `PromptEditor > Edit SelectedText with Plugins > WD14 Tagger`

## LM Studio Vision

Freely analyze and interpret images using LLM.

Example:
- Input image: fantasy_scene.png
- Prompt: "Generate detailed prompt from this image"
- Output: `epic fantasy scene, dragon flying over castle, sunset lighting, dramatic clouds, highly detailed, masterpiece quality`

**Access:**
`PromptEditor > Edit SelectedText with Plugins > LMStudio Edit`
→ Select Preset: vision
→ Add images to Images field

**Prerequisites:**
- LM Studio running locally
- Vision-compatible model loaded (qwen2-vl, etc.)

## Choosing Between Them

**Choose WD14 when:**
- Fast processing needed
- Extract known tag sets
- Batch process many images

**Choose LM Vision when:**
- Detailed analysis/interpretation needed
- Natural language descriptions wanted
- Analyze relationships between multiple images

## Using in Programmable Block

```
@@@_
$tags = await env.WD14("C:/images/character.png")
env.OUTPUT("Tags: " + $tags)

$desc = await env.LMEDIT("vision", "Describe in detail", "C:/images/character.png")
env.OUTPUT("Description: " + $desc)
_@@@
```
