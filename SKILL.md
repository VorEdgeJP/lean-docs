---
name: lean-docs
description: Trims product documentation and tutorials down to what readers actually need. Reference mode cuts docs to what the UI leaves unsaid; tutorial mode cuts a walkthrough to the shortest path to one working result while keeping a warm, guiding voice. Use when rewriting or auditing docs for redundancy, writing new reference pages or tutorials, or when a page feels over-explained, reads like a click-by-click manual, repeats the same fact, or reads curt after trimming.
---

# Lean docs

## First, pick the mode

| | Reference | Tutorial |
| --- | --- | --- |
| Reader | Already has the product open and wants one answer | Has not done this yet and wants one result |
| Page is about | A feature, a screen, a setting, a list | A goal: "make X work" |
| Read | Looked up, skimmed, revisited | Read once, top to bottom, while doing it |
| Cutoff question | Does not knowing it cost the reader anything? | Would a first-timer get stuck, or give up, without it? |
| Voice | Plain and neutral | Plain, but guiding: says why, and what happens next |

If a request mixes both ("a getting-started page that also lists every option"), split it: a tutorial that links to a reference page.

Both modes share three rules: **one fact, one place**, **verify against the product**, and **the reduction rate is a result, not a goal**.

---

## Reference mode

### Principle

**Do not document what a reader can learn after using the UI two or three times.**

Documentation is not a narration of the screen. It covers only what the screen leaves unsaid.

### The decision ladder

#### The cutoff: does not knowing it cost the reader anything?

Ask this of everything first. **If readers lose nothing by not knowing it, leave it out — even if it is accurate.**

This takes priority over every condition below. Even a behavior that never appears on screen is unnecessary if nobody is hurt by not knowing it.

> Counterexample: "The sidebar defaults to 250px and can be resized between 150px and 640px. Dragging it narrower than 150px closes it, and grabbing and releasing it counts as a click and closes it."
> — The drag behavior never shows on screen, but nobody is worse off for not knowing it. Delete the whole section.

"Overly detailed specs" usually fail here: pixel values, where settings are stored internally, branching display conditions, how long temporary state is remembered.

#### Three reasons to keep something

For whatever passes the cutoff, ask these in order. Keep it if any answer is yes.

1. **Does it never appear on screen?** — Keyboard shortcuts, the start date of a billing period, internal precedence rules. Users can work with the product forever and never notice them.
2. **Is a misunderstanding costly?** — "Apply" does not save, a deletion is irreversible, something affects billing. Getting it wrong costs the reader.
3. **Is it reference data?** — Per-plan limits, lists of error reasons, lists of permissions. Things readers look up rather than memorize.

Delete everything else. "Correct, but doesn't need to be written" is the most common case.

#### The 80% test

When in doubt, ask: "Could 80% of this product's users use it fully without knowing this?"
If yes, delete it. Accuracy is not a reason to keep something.

#### Judging reference data: does the screen show the whole set or a single case?

Before deciding "it's on screen, so it's unnecessary," check **whether the screen shows the whole set, or just the one case that happened**.

> Counterexample: a list of 11 reasons a bot can fail to start. The screen shows the reason and remedy for the one failure that occurred.
> But what users want to know — "what failures exist, and which can I fix myself?" — can never be learned from the screen.
> When a screen only ever shows single cases, the documentation is the only source for the full list.

The same misjudgment happens with permission lists, error code tables, and per-plan limits.

#### Writing reference data: make remedies specific

If you keep a list, write each row's remedy so readers know what to do next.
In particular, state **who can fix it**.

| Type | Example wording |
| --- | --- |
| The user can fix it | "Reissue the key under 'API keys' in the admin console, then paste it via 'Re-enter key'." |
| It resolves by waiting | "This limit is imposed by the provider. Please wait up to about a day for it to lift. We cannot resolve this on our side." |
| Needs action from the operator | "This is a problem on our side. There is nothing you can do to fix it; please contact support." |

One-word remedies like "Remedy: retry" or "Remedy: contact support" don't help readers.
A column that only lists the screen's button names isn't needed either (the buttons are on the screen).

### What to delete

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

### Procedure

1. **Eliminate cross-page duplication first** — it pays off more than line-level editing. If the same fact lives on another page, replace it here with a single link.
2. **Drop whole sections** — deleting sections is faster and more accurate than trimming sentences.
3. **Run the ladder on what remains** — one sentence at a time.
4. **Restructure** — abandon the "open → operate → save" order of operations and organize by behavior, so the page reads as a reference rather than a manual.
5. **Fill the gaps** — cutting the redundancy exposes information specific to the screen that was never written down. Add it now.

As a rough guide, existing product docs often shrink by 50–80%.

### What is worth keeping

There is no need to fear cutting too much, but do not delete these:

- Warnings about irreversible actions
- "Doing A does not cause B" statements (gaps between expectation and behavior)
- Announcements of features users would never discover (the fact that the feature exists, not how to use it)
- Numeric limits, lookup tables, start dates
- Full lists for screens that only show single cases (see above)

### Exception: onboarding pages in a reference set

In getting-started and setup chapters, "learn by using it" doesn't hold: readers haven't reached the screen yet.
Relax the rules for this one point only:

- **Keep steps that leave the product** — actions in an external service's console, OAuth authorization flows. No amount of using the product teaches these.
- **Still delete steps that trace the product's own UI** — the "click a button → a screen opens → wait" kind.

If the page's whole job is to walk someone to a result, it is a tutorial; switch to tutorial mode.

---

## Tutorial mode

### Principle

**A tutorial gets one reader to one working result by the shortest path, and leaves them confident enough to come back.**

It is not a reference with steps added. Anything that does not help a first-timer reach the result, or understand what just happened, belongs in a reference page and gets a link.

### The cutoff: would a first-timer get stuck without it?

Ask this of every sentence. "Accurate" and "on screen" do not decide it; "would someone doing this for the first time stall, take a wrong turn, or give up?" does.

- If the screen makes the next move obvious, one short sentence is enough. Don't narrate the click.
- If the next move is not obvious, or the reader has to leave the product, spell it out.
- If a mistake here fails silently, warn about it before the step, not in a troubleshooting section at the end.

### What to keep

| Kind | Why | Example |
| --- | --- | --- |
| The minimal path | It is the whole point | 3–5 steps, each one meaningful action ("create", "add", "place"), not one per click |
| Steps outside the product | The product's UI can't teach them | Platform permissions, role order, an external console |
| A "try it" step | The reader needs to know they are done | "Press the button yourself. If the role appears, and disappears on a second press, you're done." |
| Gaps on the path | Readers will hit them in their first hour | "Changing the look does not update the posted panel until you press 'Publish'." |
| Silent failures | The screen can't explain what it doesn't show | "A panel posted with no roles has no buttons; add roles and they appear." |
| Limits that change the plan | Readers decide before they build | A short per-plan table, only the rows that matter for this goal |

### What to cut

Everything in reference mode's "What to delete", plus:

| Kind | Why |
| --- | --- |
| Every option and variant | One path. Mention alternatives in one short section, or link to the reference |
| Troubleshooting for errors whose message already says the fix | The reader will see the message; the tutorial adds nothing |
| A second explanation of a prerequisite | Say it once in "Before you start"; troubleshooting points back to it |
| Screen states the reader sees anyway | "A confirmation message appears", "the status changes to 'Placed'" |
| Field-by-field tables | Name only the fields this goal needs, in the step that needs them |

### Shape

1. **Outcome first** — one image or sentence of the finished result, framed as what the reader gets ("Let members pick their own roles"), not what the feature is.
2. **Before you start** — prerequisites, especially the ones outside the product. Put the one most likely to bite in bold.
3. **Steps** — headings are short verbs ("Create the panel"). Each step: what to do, then what you should now see, only if it is not obvious.
4. **Try it** — the step that tells the reader they are finished.
5. **Afterwards** — only the expectation gaps the reader will hit when they change things later.
6. **Variations and limits** — short; link for the rest.
7. **When it doesn't work** — only failures with no message, or whose message doesn't say what to do.

A short tutorial does not need a "Next steps" list; one link at the point where it is useful is better.

### Voice: lean is not curt

Cutting a tutorial hard tends to strip the connective tissue, and the result reads like a terse manual. Readers find that cold, and a cold tutorial reads longer than it is. After trimming, put back:

- **Why, in a clause** — "…because the bot can only assign roles below its own", "the name is only for you to tell panels apart, so anything short works".
- **What happens next** — "At this point, members can't see anything yet."
- **An invitation at the key moments** — "Try pressing it yourself", "Let's let members pick their own roles". Use it at the start and at the "try it" step; elsewhere stay plain.
- **Everyday words in prose; screen labels only in quotes** — write "press 'Place' and pick a channel; the panel is posted there", not "execute placement to publish the panel". The quoted label must match the screen exactly; the sentence around it should not sound like the screen.

Don't confuse warmth with padding: no marketing claims, no "simply"/"just", no praise of the feature, no preamble about what the tutorial will cover. Softening a trimmed draft can add up to about a third more length, and that is fine.

### Procedure

1. **Verify the path against the product** — walk it, or read the code that renders it. Note every label exactly and every place the reader might stall.
2. **Write the minimal path** with the shape above.
3. **Cut** with the cutoff question and "What to cut". Move anything a reference reader would want into a reference page or link.
4. **Restore the voice** — read it aloud once; wherever it sounds like a list of commands, add the why or the what-next.
5. **Check it fits** — tables of more than three columns rarely fit a phone; prefer two or three.

---

## Shared rules

### One fact, one place

Write each fact in exactly one place per page and per site, and link to its heading from everywhere else.

Duplication is not a length problem; the problem is that **one copy goes stale**. In one real case, the same permission-evaluation order was written on two pages, and one of them ended up missing a step.

In a tutorial, the usual duplicate is a prerequisite repeated in troubleshooting. Keep it in "Before you start" and point back.

### Verify against the product, not older docs

Existing docs drift. Before keeping a label, a mode name, a limit, or a "this updates automatically" claim, confirm it in the product or its source. In one real case, a reference page still listed a display type that had been renamed, two modes that no longer existed, and said role changes needed a manual refresh when they now applied automatically. A tutorial built from that page would have sent readers looking for buttons that aren't there.

### Verification

- Check that no other page still links to an anchor in a deleted section
- Check that hiding a page did not leave dangling "see this page" pointers
- Run the link checker if the project has one

## Examples

Before/after pairs on a fictional product. Compare them when a call is hard to make.

- [examples/01-settings-page.md](examples/01-settings-page.md) — reference: trimming a settings page (the cutoff, tautologies, describing the screen)
- [examples/02-error-table.md](examples/02-error-table.md) — reference: keeping an error list and making its remedies specific (whole set vs. single case)
- [examples/03-tutorial.md](examples/03-tutorial.md) — tutorial: from an over-explained walkthrough, through an over-trimmed one, to a lean tutorial with a guiding voice
