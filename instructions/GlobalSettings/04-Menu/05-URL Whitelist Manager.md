# URL Whitelist Manager

**URL Whitelist Manager**

## When to Use

- When you want to enable opening external URLs from the app
- When you want to add or change allowed domains
- When you want to restrict to only trusted domains for security

## What It Does

Manages which domains are allowed when opening external URLs in a browser from within the app.

By default, the ability to open external URLs is **enabled**, with major domains pre-allowed. You can disable it or edit the allowed domains as needed.

## How to Use

1. Select GlobalSettings > **URL Whitelist Manager** to open the dialog
2. Enable the whitelist feature using the **checkbox**
3. Add, edit, or delete domains
4. Click "Save" to save

## Dialog Operations

### Whitelist Enable/Disable

Toggle using the checkbox at the top of the dialog. When disabled, no external URLs can be opened.

### Domain List Table

Manage domains in a 3-column table:

| Column      | Content             | Editing               |
| ----------- | ------------------- | --------------------- |
| Domain      | Allowed domain name | Double-click to edit  |
| Description | Domain description  | Double-click to edit  |
| Added Date  | Date added (auto)   | Not editable          |

### Operation Buttons

- **Add**: Add a new domain (enters edit mode immediately after adding)
- **Delete**: Delete the selected domain
- **Reset to Default**: Restore the default domain list (with confirmation dialog)

### Default Domains

- civitai.com
- huggingface.co
- github.com
- arxiv.org
- wikipedia.org
- danbooru.donmai.us

## Notes

- Subdomains are automatically allowed (e.g., `api.civitai.com` is allowed by registering `civitai.com`)
- Empty domains are automatically removed when saving
- Press Enter or Esc to confirm while editing a cell

## Related

- [Add From Civitai URL](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/12-Add%20from%20Civitai%20URL.md)
- [API Key Settings](09-API%20Key%20Settings.md)
- [Initial Setup](../03-Tips/01-Recommended%20Initial%20Settings.md)
