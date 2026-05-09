# WD14 Tagger

## What Is It

WD14 Tagger is an AI feature that analyzes images and automatically assigns tags (keywords).

## About Thresholds

Each tag comes with a "confidence score" (a value from 0 to 1). By setting a threshold, you can exclude tags with low confidence.

- Setting the threshold **lower** → More tags are extracted (potential for more noise)
- Setting the threshold **higher** → Only high-confidence tags are extracted (potential for more missed tags)

## Model Used

This uses [SmilingWolf/wd-eva02-large-tagger-v3](https://huggingface.co/SmilingWolf/wd-eva02-large-tagger-v3) (HuggingFace). The model file (~890MB) is automatically downloaded on first use.

## Related

- [WD14 Tagger Settings](../04-Menu/03-EditPlugin Settings/04-WD14 Tagger.md)
- [WD14 Tagger Plugin](../../PromptEditor/04-Menu/01-Edit SelectedText with Plugins/14-WD14 Tagger.md)
- [Add From WD14](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/19-Add from WD14.md)
- [env.WD14](../../PromptEditor/02-How To Write Prompt Content/02-How To Write Programmable Block/02-Built-in Functions/14-env.WD14.md)
- [Extract MetaData From Image](../../PromptBrowser/03-Menu/04-ImagePanel/09-Extract MetaData From Image.md)
- [Tag](../../PromptBrowser/01-Basics/04-Tag.md)
- [Image](../../PromptBrowser/01-Basics/01-Image.md)
- [Plugin](../../PromptTree/04-Menu/03-Selected Add/01-Plugin/README.md)
