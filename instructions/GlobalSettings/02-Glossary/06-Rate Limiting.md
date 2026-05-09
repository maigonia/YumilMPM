# Rate Limiting

**Rate Limiting**

## What Is It

Rate limiting is a mechanism that controls the frequency of requests to external services. Since sending too many requests in a short time can result in being blocked by external services, requests that would exceed the limit are rejected immediately (**fail-fast**).

## Two Limiting Methods

### Request Delay

The minimum number of milliseconds that must elapse between consecutive requests. For example, if set to 3000ms, any subsequent request that arrives within 3 seconds of the previous one is rejected.

### Sliding Window (Max Requests / Window)

The number of requests allowed within a fixed time window. For example, if set to "20 requests / 5 minutes," any new request is rejected when 20 requests have already occurred in the past 5 minutes, until the oldest request falls outside the window.

Both limits operate independently, and a request is rejected if either limit is reached.

## Behavior on Rejection

When a request is rejected, the handling depends on the context.

| Context | Behavior on rejection |
| --- | --- |
| [Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md) | A modal dialog appears (countdown of remaining seconds + Cancel + Force Reset). Auto-retries when the countdown reaches 0 |
| [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md) | A modal dialog appears (same as above). Cancel aborts the bulk operation |
| [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) Edit syntax | A marker `[Plugin rate limited — retry in Ns]` is embedded in the output text |
| `env.PLUGINEDIT` in [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) | The same marker string is returned as the result |

The dialog form lets interactive operations wait without losing context; the marker form keeps automated consecutive execution moving while still surfacing that the limit was hit.

### Modal Dialog Actions

| Button / Event | Behavior |
| --- | --- |
| Countdown reaches 0 | Auto-retries (the safe path) |
| **Cancel** | Aborts the operation. In Bulk Edit, remaining prompts are skipped |
| **Force Reset** | Clears the rate-limit history (timestamps) and retries immediately. Useful when burst-testing a plugin and the wait is intentional rather than warranted |

Force Reset is an **explicit user choice** and is only offered in interactive contexts. Automated consecutive execution (CI, Programmable Block) keeps using the marker text path, where Force Reset cannot reach — runaway-script protection from fail-fast is preserved.

## Applicable Plugins

Rate limiting applies to built-in plugins that declare `defaultRateLimitConfig`, and to [Custom Plugin](../03-Tips/02-Custom%20Plugins.md)s with the `permissions: ['network']` declaration.

| Plugin | Default Settings |
| --- | --- |
| **Google Translate** | 3000ms delay, 20 requests / 5 minutes |
| **LMStudio Edit** | Unlimited (0/0; opt-in via user settings) |
| [Custom Plugin](../03-Tips/02-Custom%20Plugins.md)s with the network permission | App default (or `metadata.rateLimit` if the plugin declares one) |

LMStudio is unlimited by default because it is typically used against a local server. Configure it explicitly when used over the cloud, etc.

## When Applied

| Context | Applied | Reason |
| --- | --- | --- |
| [Category Identifier](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/README.md) Edit syntax | Yes | Automatically executed consecutively during prompt generation |
| [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md) | Yes | Bulk processing of multiple prompts |
| [Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md) | Yes | Prevents exceeding the limit on rapid clicks |
| `env.PLUGINEDIT` in [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) | Yes | Repeated calls from a script can hit the limit |

## How to Change Settings

1. Open **Global Settings > EditPlugin Settings**
2. Click the **gear icon** on the rate-limit-capable plugin row
3. Change the setting values
4. Click **OK** to save

## Notes

- For built-in plugins, Reset restores the plugin's `defaultRateLimitConfig` (the values declared by the plugin)
- For custom plugins, Reset restores `metadata.rateLimit` (or the app default if the plugin does not declare one)
- Setting Delay = 0 disables the delay check
- Setting Max Requests = 0 disables the window check

## Related

- [EditPlugin Settings](../04-Menu/03-EditPlugin%20Settings/01-EditPlugin%20Settings.md)
- [Google Translate](../../PromptEditor/04-Menu/01-Edit%20SelectedText%20with%20Plugins/15-Google%20Translate.md)
- [Google Translate Settings](../04-Menu/03-EditPlugin%20Settings/03-Google%20Translate%20Settings.md)
- [Edit](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/01-How%20To%20Write%20Category%20Identifier/02-Action%20Commands/06-Edit.md)
- [Edit Prompt Content with Plugins](../../PromptTree/04-Menu/05-Checked/04-Edit%20Prompt%20Content%20with%20Plugins.md)
- [Edit SelectedText with Plugins](../../PromptEditor/01-Basics/01-Features/06-Edit%20SelectedText%20with%20Plugins.md)
- [Plugin](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/README.md)
- [Custom Plugin](../03-Tips/02-Custom%20Plugins.md)
