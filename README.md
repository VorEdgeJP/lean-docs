# lean-docs

A Claude Code skill for trimming product documentation down to what the UI does not already tell the reader.

## What it is

A lot of product documentation ends up narrating the screen. It rephrases button names, copies toast messages,
and repeats the same fact in body text, tables, steps, and callouts. Readers skip it, writers can't keep it
all up to date, and sooner or later some copy goes stale.

This skill gives Claude a focused set of criteria and a procedure built around one idea: **write only what the screen leaves unsaid**.

- The cutoff: if readers lose nothing by not knowing it, leave it out, even if it is accurate
- Three reasons to keep something: it never appears on screen / a misunderstanding is costly / it is reference data
- Judging reference data: does the screen show the whole set, or only the one case that happened?

## Contents

| File | Contents |
| --- | --- |
| `SKILL.md` | The decision ladder, what to delete, the procedure, and exceptions |
| `examples/` | Before/after pairs on a fictional product |

## Installation

Place the repository as-is in Claude Code's skills directory.

```bash
git clone https://github.com/VorEdgeJP/lean-docs.git ~/.claude/skills/lean-docs
```

To use it in a single project, place it at `<project>/.claude/skills/lean-docs` instead.

## Background

The criteria were built up from the feedback and corrections received during a full rewrite of a real SaaS
product's documentation (85 files, about 21,000 lines), which was written in Japanese. Pages shrank by 50–80%.
The skill itself is language-agnostic and works on documentation in any language.

## License

Released under the [MIT License](LICENSE).
