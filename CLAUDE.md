# CLAUDE.md

Guidance for Claude Code when working in this repository.

## What this repo is

A question bank for Bangladeshi government / bank IT job exams, built from the last 16 years of papers.

```
written/                  22 topic files — written exam questions
  suggestion/
    written-question-count.md      count report for written/
mcq/                      24 topic files — MCQ exam questions
  suggestion/
    mcq-question-count.md          count report for mcq/
Suggestion/               exam-specific suggestion sheets
prompts/                  the original task prompts
```

Every topic file (`written/*.md`, `mcq/*.md`) has the same shape:

```
<!-- TOC START -->
**Table of Contents** — 33 subtopics · 453 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Subnetting & IP Addressing](#subnetting--ip-addressing-97) | 97 |
| 2 | [OSI & TCP/IP Reference Model](#osi--tcpip-reference-model-44) | 44 |

<!-- TOC END -->

---

## Subnetting & IP Addressing (97)

1. **Question text** **(Exam Name: Date) [compact it 123]**

2. **Another question** **(Exam Name: Date) [compact it 124]**

## OSI & TCP/IP Reference Model (44)
...
```

---

# RULE 1 — Counts must always stay in sync

**This is the rule that breaks most easily. Whenever a question is added, removed, or merged, four things must be updated together in the same commit.**

| # | What | Where |
|---|---|---|
| 1 | Count beside the subtopic heading | `## Subtopic (N)` in the topic file |
| 2 | Count in the TOC row | `| 3 | [Subtopic](#anchor) | N |` |
| 3 | **The TOC anchor link** | the anchor ends with the count, so it changes too |
| 4 | Count report | `written/suggestion/written-question-count.md` or `mcq/suggestion/mcq-question-count.md` |

**This applies to newly created topic files too.** A new `written/*.md` or `mcq/*.md` is never just a bare list of questions — from its very first commit it must already have:

- the `<!-- TOC START -->` … `<!-- TOC END -->` block at the very top, followed by `---`,
- a count in every heading (`## Subtopic (N)`),
- sections ordered by count, descending,
- its subtopics reflected in the matching `suggestion/*-question-count.md` report.

The simplest way to get this right is to write the raw sections first and then run the reference implementation below on the folder — it builds the TOC, adds the counts and sorts the file for you.

Two consequences that are easy to miss:

- **The count is part of the heading, so it is part of the anchor.** `## Stack (44)` → `#stack-44`. Add one question and the anchor becomes `#stack-45`. The TOC link **must** be regenerated or it silently 404s.
- **Sections are sorted by count, descending.** Adding questions can move a section above another, so the whole file may need reordering — content order and TOC order must always match.

The safest approach is to never hand-edit counts. Add the questions first, then regenerate the whole file mechanically with the algorithm below, then regenerate the count report.

## How a question is counted

A line is a question if, **outside a fenced code block**, it matches `^\d+\.\s`. Lines inside ``` fences never count, even if they look numbered.

## Heading and anchor rules

- Heading format is `## <Name> (<count>)`.
- When recomputing, strip an existing **bare-number** suffix first — regex `\s*\(\d+\)$`. Only a pure number is stripped, so real headings like `(Supervised vs Unsupervised)` or `(Cables & Wiring)` survive. This makes regeneration idempotent.
- The anchor is GitHub's slug of the **full heading including the count**: lowercase; keep Unicode letters, digits and combining marks (Bengali `া ি ্ ং` must survive), keep `-` and `_`; drop all other punctuation (`& ' ( ) + , . / ’`); turn each space into `-`. Note that dropping `&` between two spaces yields a double hyphen: `A & B` → `a--b`.

## Sort rule

Sections are ordered by question count, **descending**. Ties keep their existing relative order (use a stable sort). The TOC lists sections in that same order, numbered 1..n.

**Descending order must be re-established every time a question is added.** Adding a question to a subtopic can push its count above the subtopic sitting above it — when that happens the two sections swap: the subtopic that just grew moves up, and the one it overtook moves down. The section's whole body moves with its heading.

Worked example — a question is added to *Stack*, taking it from 44 to 45, while *Linked List* above it has 44:

```
before                       after
## Tree (60)                 ## Tree (60)
## Linked List (44)          ## Stack (45)      ← moved up
## Stack (44)                ## Linked List (44) ← moved down
## Hashing (12)              ## Hashing (12)
```

Then the TOC must be rebuilt too — the row order changes, the `#stack-44` anchor becomes `#stack-45`, and the `| # |` numbering shifts. Never fix only the count and leave the position: a file where counts are not in descending order is broken, and so is one where TOC order and content order disagree.

## Reference implementation

Run from the repo root, once per folder (`written`, then `mcq`). It is idempotent — running it when nothing changed produces no diff.

````python
# -*- coding: utf-8 -*-
import io, os, re, sys, unicodedata
NUM   = re.compile(r"^\d+\.\s")
CNT   = re.compile(r"\s*\(\d+\)$")
START, END = "<!-- TOC START -->", "<!-- TOC END -->"

def slug(t):
    o = []
    for ch in t.strip().lower():
        if ch == " ": o.append("-")
        elif ch in "-_": o.append(ch)
        elif unicodedata.category(ch)[0] in ("L", "N", "M"): o.append(ch)
    return "".join(o)

def process(path):
    lines = io.open(path, encoding="utf-8").read().split("\n")
    if lines and lines[0].strip() == START:              # drop old TOC
        e = lines.index(END) + 1
        while e < len(lines) and lines[e].strip() in ("", "---"): e += 1
        lines = lines[e:]
    secs, cur, fence = [], None, False                   # split into sections
    for l in lines:
        if l.startswith("```"):
            fence = not fence
            if cur: cur[1].append(l)
            continue
        if not fence and l.startswith("## "):
            cur = [CNT.sub("", l[3:].strip()), [], 0]; secs.append(cur); continue
        if cur is None: continue
        cur[1].append(l)
        if not fence and NUM.match(l): cur[2] += 1
    if not secs: return
    secs.sort(key=lambda s: -s[2])                       # stable, descending
    total = sum(s[2] for s in secs)
    out = [START,
           "**Table of Contents** — %d subtopics · %d questions" % (len(secs), total),
           "", "| # | Subtopic | Questions |", "|---|---|---|"]
    for i, s in enumerate(secs, 1):
        out.append("| %d | [%s](#%s) | %d |" % (i, s[0], slug("%s (%d)" % (s[0], s[2])), s[2]))
    out += ["", END, "", "---", ""]
    for s in secs:
        body = s[1]
        while body and body[-1].strip() == "": body.pop()
        out.append("## %s (%d)" % (s[0], s[2]))
        out.extend(body); out.append("")
    io.open(path, "w", encoding="utf-8").write("\n".join(out).rstrip("\n") + "\n")

for fn in sorted(os.listdir(sys.argv[1])):
    if fn.endswith(".md"): process(os.path.join(sys.argv[1], fn))
````

## Regenerating the count report

`written/suggestion/written-question-count.md` and `mcq/suggestion/mcq-question-count.md` list every category and subcategory with its count, sorted descending, split into **IT questions** and **General Questions**. `gk.md`, `bangla.md`, `english.md` and `math.md` are the General files; everything else is IT. Keep the existing table format and update the three totals in the header.

## Verify before committing

- Every TOC anchor resolves to a real heading slug in the same file.
- Heading counts, TOC counts and actual counted questions all agree.
- Section order is descending and matches TOC order.
- Folder total matches the total in the count report.
- No content was lost — compare the multiset of non-blank lines before and after any reordering.

---

# RULE 2 — processDaihan (adding new questions)

The recurring task. Given questions (from a docx, PDF or image), for each question:

1. **Categorize** it to a topic file. If no matching file exists, create one — and a new file must be created with a TOC, per-heading counts and count-descending section order, exactly like every existing file (see Rule 1). Otherwise append to the existing file. Never create a duplicate topic file.
2. **Subcategorize** it to a `##` subtopic inside that file. Create the subtopic if needed.
3. **Keep the question intact** — verbatim text, options, code blocks, tables, LaTeX, Bengali. Never paraphrase or retype from memory; extract it.
4. **Keep the exam tag**, including the page number, in the form `**(Exam Name: Date) [compact it 123]**`. If the source has no page number, keep the tag as the source gives it.
5. **Number within the subtopic** — 1, 2, 3…; a new question gets `last_number + 1`.
6. **Dedup:** if the same question already exists, do **not** insert it again — append the new exam tag to the end of the existing entry instead. A merge happens **only if the title and every option, including code blocks, are identical**. Anything less is a separate numbered entry. In particular, two C questions with the same title but different code are two entries.
7. Then apply **Rule 1** and regenerate counts.

## After processing

- **Commit message** = the source file's name (e.g. `question part 3.docx`).
- Move the processed source file to the **Trash**, never permanently delete:
  ```bash
  osascript -e "tell application \"Finder\" to delete POSIX file \"/abs/path/file.docx\""
  ```

---

# RULE 3 — Commits

- Commit body must say **`Committed by Daihan`**.
- **No Claude or AI reference anywhere** — no `Co-Authored-By: Claude`, no "Generated with Claude Code". This overrides the default commit trailer.
- Commit `written/` changes and `mcq/` changes as **separate commits** when a task touches both.
- Push after committing.

```bash
git commit -m "<source file name>" -m "Committed by Daihan"
```

---

# Notes

- Extraction from PDF/image is done with `pdftoppm` (poppler) to render pages, then reading them visually. Most exam PDFs are scans with no text layer.
- Bengali headings need NFC normalization when matched against existing files.
- The exam suggestion sheets in `Suggestion/` are derived from this bank; if the bank changes substantially, their statistics go stale.
