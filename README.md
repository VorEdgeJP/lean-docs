# lean-docs

A Claude Code skill for trimming product documentation and tutorials down to what readers actually need.

## What it is

A lot of product documentation ends up narrating the screen. It rephrases button names, copies toast messages,
and repeats the same fact in body text, tables, steps, and callouts. Readers skip it, writers can't keep it
all up to date, and sooner or later some copy goes stale.

This skill gives Claude a focused set of criteria and a procedure, in two modes.

**Reference mode** — for pages about a feature, a screen, or a list. One idea: **write only what the screen leaves unsaid**.

- The cutoff: if readers lose nothing by not knowing it, leave it out, even if it is accurate
- Three reasons to keep something: it never appears on screen / a misunderstanding is costly / it is reference data
- Judging reference data: does the screen show the whole set, or only the one case that happened?

**Tutorial mode** — for walkthroughs that take a reader to one working result. One idea: **the shortest path, with a guiding voice**.

- The cutoff: would a first-timer get stuck, or give up, without it?
- Keep the minimal path, steps outside the product, a "try it" step, gaps on the path, and silent failures
- Lean is not curt: keep the why and the what-next, use everyday words in prose, and put screen labels only in quotes

Both modes share "one fact, one place" and "verify against the product, not older docs".

## Contents

| File | Contents |
| --- | --- |
| `SKILL.md` | Choosing the mode, the criteria and procedure for each, and the shared rules |
| `examples/01-settings-page.md` | Reference: trimming a settings page |
| `examples/02-error-table.md` | Reference: keeping an error list and making its remedies specific |
| `examples/03-tutorial.md` | Tutorial: over-explained → over-trimmed → lean with a guiding voice |

## Installation

Place the repository as-is in Claude Code's skills directory.

```bash
git clone https://github.com/VorEdgeJP/lean-docs.git ~/.claude/skills/lean-docs
```

To use it in a single project, place it at `<project>/.claude/skills/lean-docs` instead.

## Background

The reference criteria were built up from the feedback and corrections received during a full rewrite of a real SaaS
product's documentation (85 files, about 21,000 lines), which was written in Japanese. Pages shrank by 50–80%.

Tutorial mode came from writing the first tutorial for the same product. The first draft (about 5,200 Japanese
characters) was rejected as too long to read. Cutting it with the reference rules brought it to about 1,600 characters
but made it read stiff and curt. Putting the why and the guiding voice back settled it at about 2,200 characters,
which read well. Along the way, the existing reference page for the feature turned out to be out of date, which is
where the "verify against the product" rule comes from.

The skill itself is language-agnostic and works on documentation in any language.

## License

Released under the [MIT License](LICENSE).
