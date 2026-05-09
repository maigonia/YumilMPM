# Handling Sensitive Information

All project data in this app, except for external service API keys (stored in the OS keyring), is saved locally in **plain text**.

## What Is Stored in Plain Text

- Prompt content
- Category and template settings
- Image paths, memos, tags
- General project settings

## Handling Sensitive Information

It is not recommended to include passwords, API keys, personal information, encryption keys, or other sensitive data in your prompts or settings.

For managing such information, please use **dedicated applications**:

- **Password managers** (e.g., 1Password, Bitwarden)
- **OS keyring / credential manager**
- **Encrypted storage**

Since data other than OS keyring entries is stored without encryption, anyone with access to the project folder can view its contents.

## Summary

This app is a tool specialized for prompt management. It is not suitable for storing sensitive information, so please use dedicated tools for that purpose.
