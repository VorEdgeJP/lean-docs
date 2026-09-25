---
name: lean-docs
description: Trims product documentation down to what readers cannot learn by using the UI. Use when rewriting pages, auditing docs for redundancy, or writing new pages — especially when docs feel over-explained, read like click-by-click manuals, or repeat the same fact in several places.
---

# Lean docs

## Principle

**Do not document what a reader can learn after using the UI two or three times.**

Documentation is not a narration of the screen. It covers only what the screen leaves unsaid.

## The decision ladder

### The cutoff: does not knowing it cost the reader anything?

Ask this of everything first. **If readers lose nothing by not knowing it, leave it out — even if it is accurate.**

This takes priority over every condition below. Even a behavior that never appears on screen is unnecessary if nobody is hurt by not knowing it.

> Counterexample: "The sidebar defaults to 250px and can be resized between 150px and 640px. Dragging it narrower than 150px closes it, and grabbing and releasing it counts as a click and closes it."
> — The drag behavior never shows on screen, but nobody is worse off for not knowing it. Delete the whole section.

"Overly detailed specs" usually fail here: pixel values, where settings are stored internally, branching display conditions, how long temporary state is remembered.

### Three reasons to keep something

For whatever passes the cutoff, ask these in order. Keep it if any answer is yes.

1. **Does it never appear on screen?** — Keyboard shortcuts, the start date of a billing period, internal precedence rules. Users can work with the product forever and never notice them.
2. **Is a misunderstanding costly?** — "Apply" does not save, a deletion is irreversible, something affects billing. Getting it wrong costs the reader.
3. **Is it reference data?** — Per-plan limits, lists of error reasons, lists of permissions. Things readers look up rather than memorize.

Delete everything else. "Correct, but doesn't need to be written" is the most common case.

### The 80% test

When in doubt, ask: "Could 80% of this product's users use it fully without knowing this?"
If yes, delete it. Accuracy is not a reason to keep something.

### Judging reference data: does the screen show the whole set or a single case?

Before deciding "it's on screen, so it's unnecessary," check **whether the screen shows the whole set, or just the one case that happened**.

> Counterexample: a list of 11 reasons a bot can fail to start. The screen shows the reason and remedy for the one failure that occurred.
> But what users want to know — "what failures exist, and which can I fix myself?" — can never be learned from the screen.
> When a screen only ever shows single cases, the documentation is the only source for the full list.

The same misjudgment happens with permission lists, error code tables, and per-plan limits.

### Writing reference data: make remedies specific

If you keep a list, write each row's remedy so readers know what to do next.
In particular, state **who can fix it**.

| Type | Example wording |
| --- | --- |
| The user can fix it | "Reissue the key under 'API keys' in the admin console, then paste it via 'Re-enter key'." |
| It resolves by waiting | "This limit is imposed by the provider. Please wait up to about a day for it to lift. We cannot resolve this on our side." |
| Needs action from the operator | "This is a problem on our side. There is nothing you can do to fix it; please contact support." |

One-word remedies like "Remedy: retry" or "Remedy: contact support" don't help readers.
A column that only lists the screen's button names isn't needed either (the buttons are on the screen).

## What to delete

| Kind | Example |
| --- | --- |
| Repeating the same fact | Structures that cover it four times: body → table → steps → callout → summary |
| Duplication across pages | Restating a whole page's content when a link to that page would do |
| Describing the screen | Toasts, empty states, placeholders, badge colors, element layout, loading indicators |
| Tautologies | "Click 'Save' to save." "'Module': filters by module." |
| Idle steps | A "click 'X' in the sidebar" step whose only purpose is to "open the X screen" |
| Preambles | "This page explains…", "The following items are shown from top to bottom" |
| Callout overuse | Boxing obvious content, which buries the real warnings |
| Implementation details | Internal URL paths, query parameters, internal jargon, rate-limit intervals in seconds |
| Excessive specs | Pixel ranges, where settings are stored, fine-grained display conditions, expiry of temporary state |
| Exhaustive listings | Tables that list every item when each row just restates its label |

## Procedure

1. **Eliminate cross-page duplication first** — it pays off more than line-level editing. If the same fact lives on another page, replace it here with a single link.
2. **Drop whole sections** — deleting sections is faster and more accurate than trimming sentences.
3. **Run the ladder on what remains** — one sentence at a time.
4. **Restructure** — abandon the "open → operate → save" order of operations and organize by behavior, so the page reads as a reference rather than a manual.
5. **Fill the gaps** — cutting the redundancy exposes information specific to the screen that was never written down. Add it now.

The reduction rate is a result, not a goal. As a rough guide, existing product docs often shrink by 50–80%.

## One fact, one place

Write each fact in exactly one place per page and per site, and link to its heading from everywhere else.

Duplication is not a length problem; the problem is that **one copy goes stale**. In one real case, the same permission-evaluation order was written on two pages, and one of them ended up missing a step.

## What is worth keeping

There is no need to fear cutting too much, but do not delete these:

- Warnings about irreversible actions
- "Doing A does not cause B" statements (gaps between expectation and behavior)
- Announcements of features users would never discover (the fact that the feature exists, not how to use it)
- Numeric limits, lookup tables, start dates
- Full lists for screens that only show single cases (see above)

## Exception: onboarding

In getting-started and setup chapters, "learn by using it" doesn't hold: readers haven't reached the screen yet.
Relax the rules for this one point only:

- **Keep steps that leave the product** — actions in an external service's console, OAuth authorization flows. No amount of using the product teaches these.
- **Still delete steps that trace the product's own UI** — the "click a button → a screen opens → wait" kind.

## Verification

- Check that no other page still links to an anchor in a deleted section
- Check that hiding a page did not leave dangling "see this page" pointers
- Run the link checker if the project has one

## Examples

Before/after pairs on a fictional product. Compare them when a call is hard to make.

- [examples/01-settings-page.md](examples/01-settings-page.md) — trimming a settings page (the cutoff, tautologies, describing the screen)
- [examples/02-error-table.md](examples/02-error-table.md) — keeping an error list and making its remedies specific (whole set vs. single case)
