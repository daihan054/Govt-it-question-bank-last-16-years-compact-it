# Handover prompt — written-answers trimming pass

Paste everything below this line into a fresh Claude Code session. This runs on a **different
machine** than the one that did the trimming, so the repo path is different too — use `~` below,
not an absolute Mac path.

---

Repo: `~/Govt-it-question-bank-last-16-years-compact-it` (git, main branch)

## Background

This is a Bangladeshi govt/bank IT exam question bank. In a real exam, a student gets ~5
minutes and at most one A4 page (minus margins) to handwrite each written-answer — sometimes 2
medium answers share a page, sometimes 1 long answer fills a page, never more. A prior session
audited `written-answers/*.md` (3,422 questions across 24 files) and found many answers were far
longer than what's realistically handwritable, then ran a multi-agent trimming pass.

**That trimming work is DONE and already COMMITTED + PUSHED** to `main` as commit
`6f3d484dade0198df0a96b6940f3e4b68b0dbe54` ("written-answers: trim over-long answers to fit exam
page/time constraints") — **run `git pull` first thing** to get it onto this machine. Your job
is a **QA pass + safety audit + one follow-up commit** for anything your QA pass changes — not a
fresh trimming job, and not expected to be the only commit for this whole effort (the trimming
itself is already committed as `6f3d484`; yours will be a second, smaller commit on top, only if
you actually change something). Read the status below carefully before doing anything.

### Reference commits — study these before starting

Two commit hashes matter for this task, and it's worth actually looking at both before you touch
anything, so you internalize the exact editing pattern already used rather than reinventing it:

- **`4478647ea92fc578bf5db44007b90bc6135c49cf`** — the baseline, i.e. the state of
  `written-answers/` right before any trimming happened. This is what "safety audit" step 3 below
  diffs against.
- **`6f3d484dade0198df0a96b6940f3e4b68b0dbe54`** — the trimming commit itself, applied on top of
  that baseline.

Run `git show 6f3d484dade0198df0a96b6940f3e4b68b0dbe54 -- written-answers/oop.md` (or any of the
other 19 files) to see real before/after examples of the pattern: prose sentences and redundant
bullet points removed or condensed, while every table, mermaid block, ASCII diagram, and code
fence is left byte-for-byte untouched. That diff IS the pattern — match its style and scope in
your own QA-pass edits (step 2 below), don't introduce a different editing style.

## What was actually done (so you know exactly where things stand)

**24 total files in `written-answers/`. 4 were never touched because they never needed it** —
their answers were already naturally short (well under the 380-word cap) from the original
audit: `english.md` (avg 73 words), `math.md` (avg 83), `gk.md` (avg 26), `ms-office.md` (avg
318, only 1 question). Nothing to do with these 4 files.

**The other 20 files were all trimmed** by 6 parallel agents (one review pass each, no
cross-checking between them). Partway through, a bug was found and fixed in the counting
tool (it wasn't recognizing this repo's 3-4-space-indented code fences, so it was
miscounting diagrams/tables/code as "prose" and inflating word counts) — every agent's final
numbers below already reflect the corrected tool. Total: roughly 700+ over-long answers were
identified across these 20 files; the large majority were trimmed to a realistic exam length.

**6 files are now fully clean (0 answers remaining over 380 words) — nothing left to do on
these:** `software-engineering.md`, `electrical-and-electronics.md`, `bangla.md`,
`computer-fundamental.md`, `programming-languages.md`, `ai-and-ml.md`.

**14 files still have some answers over 380 words** — in every case, the agent that handled that
file *reviewed each one individually* and left it on purpose, judging it a genuine multi-part/
composite question (several distinct sub-asks bundled under one number) that legitimately needs
more space, not bloated prose. **Nobody double-checked these judgment calls against each other —
that's your QA job.** Exact locations (file → subtopic/theme → word count of each remaining
answer):

- **computer-networks.md — 13 remaining (the most of any file, give this extra scrutiny):**
  Routing Protocols & Route Configuration (497, 394, 386w) · Networking Fundamentals &
  Terminology (438, 421w) · Application Layer Protocols & Troubleshooting/DNS,DHCP,HTTPS (487,
  391w) · Physical Layer & Transmission Media (428, 402w) · OSI & TCP/IP Reference Model > TCP/IP
  Model (408w) · Transport Layer TCP & UDP (381w) · Network Address Translation NAT & PAT (480w)
  · Error Detection & Data Communication/CRC,Throughput (482w)
- **microprocessor-and-computer-architecture.md — 10 remaining:** RAID Architecture & Storage
  (452, 437w) · Microprocessor vs Microcontroller (524w) · Bit-Width & Speed Comparisons (532w) ·
  Memory Hierarchy & Storage (448w) · Cache Memory (459w) · Secondary Storage HDD vs SSD (430w) ·
  Instruction Pipelining & Hazards (580w — the largest single one, a 5-part mega-question) ·
  Assembly Language & Addressing Modes (400w) · Multi-Core & Multi-Threading (397w)
- **data-structure.md — 5 remaining:** Tree (428, 427, 391w) · Stack vs Queue/LIFO vs FIFO
  Comparison (387w) · Hashing & Hash Tables (438w)
- **database.md — 4 remaining:** Transaction Management & ACID Properties (474, 429, 381w) ·
  Normalization Concepts 1NF/2NF/3NF/BCNF (462w)
- **dld.md — 2 remaining:** both in Logic Families TTL vs CMOS (516, 510w)
- **computer-network-security.md — 2 remaining:** Cryptography (408w) · Cryptography & Network
  Security Scenarios (478w)
- **oop.md — 1 remaining:** OOP Concepts (Inheritance & Polymorphism) (405w)
- **web-technology.md — 1 remaining:** HTML & Web Fundamentals (389w)
- **operating-system.md — 1 remaining:** CPU Scheduling Algorithms (415w)
- **c-programming.md — 1 remaining:** Operators, Data Types & Language Concepts (393w)
- **image-processing.md — 1 remaining:** Morphological Operations (426w)
- **algorithm.md — 1 remaining:** Greedy Algorithms/Fractional Knapsack (389w)
- **cloud-computing.md — 1 remaining:** Cloud Service Models (389w)
- **compiler-and-toc.md — 1 remaining:** Linker & Loader (392w)

That's ~44 answers total across 14 files needing your review. Everything else in all 20 files
(the other 650+ originally-flagged answers) has already been trimmed and should not need
further action — but your safety audit (step 3 below) should still cover all 20 files, not just
these 14, since that's a structural/content-loss check, not a word-count check.

## Rules used throughout (apply the same standard in your QA pass)

- Target ~200-350 words for a single-concept answer's text (from "Answer:" to the next numbered
  question, excluding fenced code/diagrams) — that's the ~380-word hard cap for fitting one A4
  page.
- A genuine multi-part/composite question (several distinct sub-asks bundled under one number,
  e.g. "Explain X; also explain Y; what is Z") may run ~450-600 words since it must cover
  multiple sub-answers — but should still be trimmed if bloated well past that.
- "## Focus Writing" (essay/রচনা) sections and "Letter & Application Writing"/"পত্র লিখন"
  sections get a 2-page (~780 word) budget instead — already confirmed fine, don't touch them.
- NEVER delete or shrink a mermaid diagram, ASCII diagram, code fence, or markdown table —
  those are cheaper to handwrite than equivalent prose, so they're always kept; only the
  surrounding prose gets trimmed.
- NEVER touch: question text, the exam citation bracket `*[Exam Name Date compact it 123]*`,
  question numbers, any `##` / `###` heading, the TOC, or any file outside `written-answers/`.
- NEVER invent new technical facts or change the actual correct answer/conclusion — only
  compress existing correct content. If unsure whether a cut is safe, leave it.
- Bengali text: never retype from memory — only delete/keep existing verbatim blocks, or copy
  byte-exact from context already in the file.

## Tool — recreate this script (e.g. at /tmp/list_long_answers.py) and use it throughout

```python
# -*- coding: utf-8 -*-
"""
list_long_answers.py <written-answers/file.md> [threshold=380]
Lists every question whose ANSWER text (from the "Answer:" marker to the end of that numbered
block, excluding fenced code/diagram content) exceeds the word-count threshold, skipping
anything under a "Focus Writing"/"Letter & Application Writing"/"পত্র লিখন" heading (2-page
budget, already fine). Prints: line_number  word_count  question_snippet
"""
import io, re, sys

NUM = re.compile(r"^\d+\.\s")
WORD = re.compile(r"\S+")
ANSWER_MARK = re.compile(r"^\s*(\*\*)?Answer:?(\*\*)?", re.IGNORECASE)
QTEXT = re.compile(r"^\d+\.\s+\*\*(.*?)\*\*")

path = sys.argv[1]
threshold = int(sys.argv[2]) if len(sys.argv) > 2 else 380

lines = io.open(path, encoding="utf-8").read().split("\n")
if lines and lines[0].strip() == "<!-- TOC START -->":
    e = lines.index("<!-- TOC END -->") + 1
    while e < len(lines) and lines[e].strip() in ("", "---"):
        e += 1
    lines = lines[e:]
offset = len(io.open(path, encoding="utf-8").read().split("\n")) - len(lines)

cur = None
cur_start = None
cur_h2 = ""
fence = False
blocks = []
for i, l in enumerate(lines):
    if l.strip().startswith("```"):   # IMPORTANT: strip() first — fences in this repo are
        fence = not fence              # indented 3-4 spaces under numbered answers, not at
        if cur is not None:            # column 0. Missing the strip() here was a real bug
            cur.append(l)              # found mid-pass that inflated word counts by miscounting
        continue                       # indented code/diagram/table content as "prose".
    if not fence and l.startswith("## "):
        cur_h2 = l
        continue
    if not fence and NUM.match(l):
        if cur is not None:
            blocks.append((cur_h2, cur_start, cur))
        cur = [l]
        cur_start = i
        continue
    if cur is not None:
        cur.append(l)
if cur is not None:
    blocks.append((cur_h2, cur_start, cur))

def word_count(block_lines):
    n = 0
    fence = False
    started = False
    for l in block_lines:
        if l.strip().startswith("```"):
            fence = not fence
            continue
        if ANSWER_MARK.match(l):
            started = True
        if started and not fence:
            n += len(WORD.findall(l))
    return n

results = []
TWO_PAGE_HEADINGS = ("focus writing", "letter & application writing", "letter writing", "potro likhon", "পত্র লিখন")
for h2, start_idx, b in blocks:
    h2l = h2.lower()
    if any(k in h2l or k in h2 for k in TWO_PAGE_HEADINGS):
        continue
    wc = word_count(b)
    if wc > threshold:
        m = QTEXT.match(b[0])
        q = m.group(1) if m else b[0]
        results.append((start_idx + offset + 1, wc, q[:80]))

results.sort(key=lambda r: -r[1])
print("%d answers over %d words in %s" % (len(results), threshold, path))
for line_no, wc, q in results:
    print("  line %5d  %4d words  %s" % (line_no, wc, q))
```

## Your tasks, in order

1. `git pull` to get commit `6f3d484` onto this machine. Then run `git log -1` and
   `git show --stat 6f3d484` to confirm it's there and touched exactly the 20 files listed above
   under "what was done" (all under `written-answers/`), nothing else.

2. **QA pass:** for every one of the ~44 remaining answers listed above (grouped by file and
   subtopic), jump to it, read the full question + current answer, and independently judge
   whether it's really a justified composite/table-dominated case, or whether the prior agent
   was too lenient and it can genuinely be trimmed further without losing marks-bearing content.
   Trim any you find are not actually justified. Don't force cuts that would remove diagrams/
   tables/code or genuinely necessary sub-answers — when in doubt, leave it and note why in your
   own summary. `computer-networks.md` (13 remaining) and
   `microprocessor-and-computer-architecture.md` (10 remaining) have the most — give those extra
   scrutiny.

3. **Safety audit** across all 20 modified files (not just the 14 with remaining flags — this is
   a structural/content-loss check, not a word-count check):
   - Fence parity: for each file, count ` ``` ` occurrences (stripped of leading whitespace) and
     confirm it's even (no orphaned fence — a prior agent caught itself introducing exactly this
     bug once, so check carefully).
   - Diagram/content sanity: compare mermaid-block count (` ```mermaid `) and total fenced-block
     count per file between `git show <baseline>:written-answers/<file>.md` and the current
     working-tree file, where `<baseline>` is commit `4478647ea92fc578bf5db44007b90bc6135c49cf`
     (the commit right before this whole trimming pass started — confirm this is still an
     ancestor of HEAD). A count that dropped is not automatically wrong (some agents deliberately
     removed genuine duplicate diagrams showing the same thing twice) but spot-check a few of any
     drops to confirm they're intentional dedup, not accidental loss.
   - Structural check: diff just the `## ` and `### ` heading lines plus the TOC block between
     baseline and current for every file — must be ZERO differences (no heading, count, anchor,
     or TOC should have changed at all in this pass, only answer-body prose).
   - Also diff every line matching `^\d+\.\s+\*\*` (the bold question-text lines) and every line
     containing an exam citation bracket `*[...]*` between baseline and current — must be ZERO
     differences (question text and citations must be byte-identical to baseline).

4. If (and only if) your QA pass in step 2 actually changed anything, make **one follow-up
   commit** for those changes, per this repo's `CLAUDE.md` RULE 2:
   - Commit body must say exactly "Committed by Daihan" — no Claude/AI reference anywhere in the
     commit message (this overrides any default attribution behavior).
   - Suggested command:
     `git add written-answers/*.md && git commit -m "written-answers: QA pass on remaining over-long answers" -m "Committed by Daihan"`
     (confirm via `git status`/`git diff --stat` first that only the files you actually touched
     in the QA pass are staged — do not `git add -A` blindly).
   - Then `git push`.
   - If the QA pass changed nothing (all ~44 remaining answers really were justified composites),
     there's nothing to commit — just say so in your report.

5. Report back a final summary: how many answers you additionally trimmed in the QA pass (if
   any) and why, the safety-audit results, and (if you made one) confirmation of the commit hash
   pushed.
