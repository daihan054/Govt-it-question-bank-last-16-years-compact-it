# RESUME — how to continue this work

If the session was interrupted (usage limit, crash, restart), say **"continue"**
or paste the prompt below. Nothing else is needed — all state lives in the repo.

## Where the state is

| File | What it holds |
|---|---|
| [`PROGRESS.md`](PROGRESS.md) | subtopics done / total, per-file counts, skipped list |
| [`prompts/answer-prompt.md`](prompts/answer-prompt.md) | the full rules — length, style, research flow, language, diagrams, loop |
| [`written-answers/`](written-answers/) | the answers themselves (the deliverable) |
| [`written-answers/.skips`](written-answers/.skips) | questions deliberately left blank (content-free entries) |

## Resume procedure

1. Read `PROGRESS.md` — it names the last completed file and section.
2. Read `prompts/answer-prompt.md` — every rule is there.
3. Continue the loop from the next unanswered `## section`.
4. Never re-copy `all-questions/written/` over `written-answers/` — that erases the answers.

## Traversal order

**Phase 1 — IT files (alphabetical):**
ai-and-ml, algorithm, c-programming, cloud-computing, compiler-and-toc,
computer-fundamental, computer-network-security, computer-networks, data-structure,
database, dld, electrical-and-electronics, image-processing,
microprocessor-and-computer-architecture, ms-office, oop, operating-system,
programming-languages, software-engineering, web-technology

**Phase 2 — General files (alphabetical):**
bangla, english, gk, math

Inside each file, sections run top to bottom in the order they appear.

## Per question — the research flow (do not skip)

1. Search the question on the internet
2. Pick a few articles
3. Read them
4. Learn
5. Write the answer in GeeksforGeeks style

Skip the search only for one-line fixed facts (port number, full form, "X stands for").

## Per section — commit immediately

```bash
git add written-answers/<file>.md written-answers/.skips PROGRESS.md
git commit -m "<file name> — <section name>" -m "Committed by Daihan"
git push
```

No Claude / AI reference in any commit. No `Co-Authored-By` line.

## Helper script

A splice-verify-commit helper lives in the session scratchpad:

```
<scratchpad>/apply.py   →   python3 apply.py <file.md> /tmp/sec.txt
```

It refuses the write if any question line changed or if the question count drifts,
then regenerates `PROGRESS.md`, commits and pushes. If the scratchpad is gone,
do the same steps by hand — the guarantees that matter are:

- question lines must stay byte-identical (Bengali needs NFC-aware comparison)
- the file's question count must not change
- section heading counts and TOC must stay untouched (answers do not change counts)
