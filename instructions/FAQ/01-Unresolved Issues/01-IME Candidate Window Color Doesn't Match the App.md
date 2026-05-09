# IME Candidate Window Color Doesn't Match the App

## Symptom

The IME (Input Method Editor) candidate window may appear in an unexpected color.

## Possible Cause

The IME candidate window is a Windows system UI element and cannot be controlled from within the app. The Windows "app mode" setting may be affecting its appearance.

## What to Try

1. Open Windows **Settings**
2. Go to **Personalization > Colors**
3. Try changing the **"Choose your mode"** setting
   - If set to "Custom", also check the **"Choose your default app mode"** setting

## Note

This issue can occur in desktop applications that use WebView2. There is currently no known app-side workaround.
