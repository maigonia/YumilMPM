# Sandbox Settings
**Sandbox Settings**

## When to Use
- When you want to change the memory limit for [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- When you encounter memory shortage errors during script execution

## What It Does
Configures the memory limit for [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md) (custom JavaScript execution environment).

## Settings

**Memory Limit** — Maximum memory available during script execution

| Options |
|---------|
| 128 MB |
| 256 MB |
| **512 MB** (default) |
| 1 GB |
| 2 GB |
| 4 GB |
| 8 GB |
| 16 GB |

## How to Use
1. Select GlobalSettings > **Sandbox Settings** to open the dialog
2. Select a memory limit from the dropdown
3. Click "OK" to save

## Notes
- Script execution is interrupted if the memory limit is exceeded
- 512MB is sufficient for normal usage
- Memory is released after script execution
- "Reset to Defaults" restores the default value (512MB)

## Related

- [Programmable Block](../../PromptEditor/02-How%20To%20Write%20Prompt%20Content/02-How%20To%20Write%20Programmable%20Block/README.md)
- [Sandbox](../02-Glossary/03-Sandbox.md)
- [Initial Setup](../03-Tips/01-Recommended%20Initial%20Settings.md)
