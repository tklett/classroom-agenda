# CLAUDE.md — Classroom Agenda (Public Site) Operating Instructions

This is Tom's **public-facing** student site — a GitHub Pages site built
from the private `tklett/curriculum` repo, which is where all the real
planning, corrections, and teacher-only notes live. This repo only ever
holds the clean, student-safe version of that content.

**This repo is never the source of truth.** If something here disagrees
with `tklett/curriculum`, the private repo wins — this site just hasn't
been resynced yet.

## 1. What this site is for

Two jobs, one per course page:

1. **"Next Class"** — a pinned box at the top of each course page showing
   the plan for the upcoming class day. This replaces Tom writing five
   agendas on his whiteboard every morning. It must go up **before**
   school starts, not after — timing matters here in a way it doesn't
   for the archive below.
2. **The week/day archive** — what actually happened, reverse-
   chronological, grouped by week. The point is so a student who missed
   a day (or wants to find a journal prompt again) can look it up
   without asking Tom directly.

## 2. The curation rule — the only thing that really matters here

A public page only ever gets:
- what activities ran (or are planned to run)
- verbatim prompts students were already given (journal questions, exit
  tickets, discussion prompts)

It **never** gets anything from the private repo's other layers:
teacher rationale, "actual vs. planned" corrections, open items, quiz
answer keys, or internal debates about pacing/sequencing. Keep this
mechanical, not a judgment call per entry — that's what makes minimal
intervention from Tom safe.

## 3. The two update triggers (piggyback workflow)

Both of these ride on conversations that already happen in the private
`tklett/curriculum` repo's session — Tom doesn't do anything extra to
trigger either one.

**A. When Tom gives a next-day (or same-day) plan** — the same kind of
message that updates the private repo's `agenda-log.md` "planned"
entries — also update this repo's **"Next Class"** box for each course
mentioned, replacing whatever was there before. Label stays "Plan — not
yet confirmed."

**B. When Tom reports what actually happened** — the same message that
produces the private repo's `agenda-log.md` "Actual" entry — fold that
day into the correct course page's **current week's `<details>` block**
(create a new week block if it's a new calendar week), in the right
place for reverse-chronological order (newest day first within the
week, newest week first on the page). The "Next Class" box then either
clears to the placeholder or gets overwritten by whatever's given for
the day after.

If a day's actual delivery differs from what was in "Next Class,"
publish the actual version — don't leave the stale plan sitting in the
archive.

## 4. Structure

```
_config.yml                     — site title, description (shows in footer)
_includes/footer.html           — overrides minima's default footer (removes
                                   the duplicate title Jekyll normally repeats)
index.md                        — homepage, links to the CURRENT term's
                                   course pages only
terms/2026-fall/
  ai-literacy.md
  ap-lang-dmacc-comp.md
  dystopian-lit.md
  senior-capstone.md
  computer-science.md
```

Each course page's shape, top to bottom:
```
# <Course> — Agenda

[← Back to all classes](../../index.html)

## Next Class
*Plan — not yet confirmed...*
- ...

---

<details markdown="1" open>
<summary><strong>Week N (dates)</strong></summary>

### Weekday, Month Day
- activities
  > verbatim prompt, as a blockquote

</details>

<details markdown="1">
<summary><strong>Week N-1 (dates)</strong></summary>
...
</details>
```

**Collapsible weeks:** every week is a `<details markdown="1">` block.
Exactly one is ever `open` at a time — the most recent week. When a new
week starts, add `open` to its block and remove it from the previous
one.

**Kramdown gotcha:** any run of 2+ underscores or asterisks in a
prompt's text (e.g. a fill-in-the-blank "___") will get parsed as
markdown emphasis and silently italicize a chunk of the sentence.
Escape them (`\_\_\_`) before publishing.

## 5. Archiving by term

When a term ends, **don't move or delete anything.** Just update
`index.md`'s links to point at the new term's `terms/<term>/` files
instead. The old term's pages stay exactly where they are — reachable
by direct URL or by browsing the repo, just no longer linked from the
homepage. This is deliberate: "there for someone hunting, not on the
homepage."

## 6. Site settings

- Pull requests and Issues are disabled (Settings → General → Features)
  — this repo has no collaboration workflow, so leaving them on just
  invites spam.
- Jekyll theme: `minima`, left plain on purpose — this site is for fast
  lookup on a phone, not visual polish. Don't add styling/theme changes
  unless Tom asks.
