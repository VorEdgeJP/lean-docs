# Example 2: making the remedies in an error list specific

A list of reasons an integration can fail, from the fictional SaaS "Acme Forms".
This is an example where **the list itself stays**. The screen only shows the reason for the one failure that occurred, so the documentation is the only source for the full list.

## Before

| Reason | Remedy | Button |
| --- | --- | --- |
| The API key is invalid | Re-enter the key | "Re-enter key" |
| The sending limit has been reached | Wait for the limit to lift | "Retry in 24 hours" (display only) |
| The integration rejected authentication | Check the integration's settings | "Contact support" |
| Internal error | This problem requires attention | "Contact support" |

## After

| Reason | Remedy |
| --- | --- |
| The API key is invalid | Reissue the key in the integration's admin console, then paste it via "Re-enter key". Reissuing invalidates the previous key. |
| The sending limit has been reached | This limit is imposed by the integration. Please wait up to about a day for it to lift. We cannot resolve this on our side. Sending retries automatically once the limit lifts. |
| The integration rejected authentication | In the integration's admin console, check that access for Acme Forms is enabled. Changing settings in Acme Forms alone will not enable it. |
| Internal error | This is a problem on the Acme Forms side. There is nothing you can do to fix it; please contact support. |

## What changed

- **Removed the "Button" column** — it copied text from the screen, where the buttons are already shown. Button names that matter now appear inside the remedy text
- **Each remedy says who can fix it** — readers can tell apart the three cases: they can fix it, it resolves by waiting, or the operator must act
- **Kept the list** — the screen shows single cases. The full list is the only place to learn "what failures exist, and which can I fix myself?"
