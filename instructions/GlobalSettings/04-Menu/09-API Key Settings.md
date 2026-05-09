# API Key Settings
**API Key Settings**

## When to Use
- When you want to configure API keys for external services
- When you want to update or delete configured API keys

## What It Does
Saves and manages API keys for external services in the OS keyring (secure credential storage).

Supported services:
- **Civitai** — AI model platform

## How to Use
1. Select GlobalSettings > **API Key Settings** to open the dialog
2. Enter the API key in the field for the target service
3. Click the **Save** button to save

## Dialog Operations

The following operations are available for each service:

- **Key input field**: Enter the API key. Displayed in password format (hidden)
- **Eye icon**: Click to toggle visibility of the entered key
- **Save**: Saves the entered key. A checkmark is displayed for 2 seconds on success
- **Trash icon**: Deletes the saved key (only shown when a key is configured)

Configured services show a green checkmark and "Configured" label.

## Notes
- API keys are stored in the OS's secure credential storage (Windows: Credential Manager, macOS: Keychain)
- They are NOT stored in the app's project files, so they are not included in backups or exports
- Keys are saved individually (there is no overall "Save" button)

## Related

- [Add From Civitai URL](../../PromptTree/04-Menu/03-Selected%20Add/01-Plugin/12-Add%20from%20Civitai%20URL.md)
- [URL Whitelist Manager](05-URL%20Whitelist%20Manager.md)
- [Initial Setup](../03-Tips/01-Recommended%20Initial%20Settings.md)
