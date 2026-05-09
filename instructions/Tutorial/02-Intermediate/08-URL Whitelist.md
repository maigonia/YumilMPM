# URL Whitelist

A security feature that restricts which external URLs can be opened in an external browser when a user clicks a link inside the app.

## Understanding with Examples

LoRA info files downloaded from Civitai contain model page URLs:
`https://civitai.com/models/12345/my-awesome-lora`

To click and open this URL from within the app, you need to enable URL whitelist and allow `civitai.com`.

URLs from non-allowed domains (e.g., `malicious-site.com`) cannot be opened. This keeps you safe even if malicious URLs are embedded.

## Scope

This setting only takes effect **when a user clicks a link in the UI**. Specifically, it controls opening links shown in the Prompt Editor and Memo Viewer in an external browser.

On the other hand, **this setting does not affect** the app's internal network activity listed below. These use fixed domains hardcoded in the app and cannot be added to or changed by users:

- Fetching Civitai model info and file downloads (civitai.com)
- Google Translate API (translate.googleapis.com)
- LM Studio integration (local)
- Custom plugin communication (separate rule: HTTPS required, localhost allowed)

In other words, URL Whitelist is a safeguard against "accidentally clicking a suspicious embedded link and opening it," not an app-wide network restriction.

## Caution: Links inside Custom Plugin Help

Links inside help pages provided by custom plugins (plugin-specific documentation shown in the instruction viewer) are opened directly in an external browser **without going through URL Whitelist**. If you install a plugin from an untrusted source, links inside its help page may not be safe either — review URLs carefully before clicking.

## Default

Enabled (major domains are allowed by default; can be disabled if needed)

## Access

`GlobalSettings > URL Whitelist Settings...`

## Default Allowed Domains

- civitai.com (AI model sharing site)
- huggingface.co (AI/ML platform)
- github.com (Source code management)
- danbooru.donmai.us (Tag database)

## Tips

- Subdomains auto-allowed (api.civitai.com → OK)
- Spoofed URL detection (civitai.com.attacker.com → Blocked)
