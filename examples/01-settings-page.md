# Example 1: a settings page

Trimming the preferences page of a fictional SaaS, "Acme Forms" (a form builder).

## Before

```md
## Open the Preferences tab

<Steps>
### Open Settings
Click the icon in the top-right corner and choose "Settings".
### Select the "Preferences" tab
Click "Preferences" in the tabs at the top. The Preferences screen appears.
</Steps>

## Sidebar width

You can adjust the sidebar width by dragging its edge. The default is 260 pixels,
and it can range from 180 to 600 pixels. Making it narrower than 180 pixels closes it.

## Notification settings

| Item | Description |
| --- | --- |
| "Receive notifications" | Toggles whether you receive notifications. |
| "Notify by email" | Sends notifications by email. |

Turning off "Receive notifications" stops notifications from arriving.
However, billing emails are sent regardless of this setting.

## Save your changes

When you change a setting, "You have unsaved changes" appears at the bottom of the screen.
Click "Save" to save your changes, and "Settings saved" is shown.
If you leave the page without saving, your changes are lost.
```

## After

```md
Preferences are stored in your account and carry over when you sign in on another device.

## Notifications

Even with "Receive notifications" turned off, **billing emails are still sent**.

## Saving changes

<Callout type="warning">
If you leave the page without saving, your changes are lost.
</Callout>
```

## What was deleted, and why

| Deleted | Reason |
| --- | --- |
| Steps to open the Preferences tab | Traces the product's own UI; obvious from the screen |
| Sidebar width | **The cutoff.** Never shown on screen, but nobody loses anything by not knowing it |
| Notification settings table | Tautology ("Receive notifications — toggles whether you receive notifications") |
| "Turning it off stops notifications" | Tautology |
| Toast text on save | Describing the screen |

| Kept | Reason |
| --- | --- |
| Settings are stored in the account | Never appears on screen |
| Billing emails arrive even when off | "Doing A does not cause B" — a gap from expectations |
| Leaving without saving loses changes | A misunderstanding is costly |
