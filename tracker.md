# Task Tracker — MCQ → Theory pass

**Purpose of this file:** record exactly where the long-running task paused, so that a new session can resume without re-deriving anything.

---

## The task

For every file in **`mcq-answers/`**:

1. Read **all** questions **with their answers and explanations** for a subtopic.
2. List the theories those questions come from.
3. **Check whether the theory is ALREADY COVERED** in `all-theories-with-previous-questions-attached/` — if covered, **SKIP it**; if not, **write it**.
4. Write the new theory into the **corresponding `.md` file**, under the **corresponding `##` subtopic section** (creating the section if none fits).
5. At the end of **every** theory, add a bold **`**Previous Year MCQ List from this Topic:**`** block listing the question texts as **clickable deep links** into `mcq-answers/`.
6. Regenerate the TOC, then **commit and push** (message body `Committed by Daihan`, **no AI/Claude reference**).

The earlier `written-answers/` pass is **already complete** — those files carry a
`**Previous Year Question List from this Topic:**` block. **Both blocks coexist:** written first, MCQ second.

---

## Tooling (scratchpad — recreate if the session directory is gone)

`/private/tmp/claude-501/-Users-daihan-Documents-Learning-projects-Govt-it-question-bank-last-16-years-compact-it/537e679f-b611-4deb-8f26-e3af253702eb/scratchpad/`

| Script | Purpose |
|---|---|
| `mcqdump.py <file.md> [section]` | Dump MCQs as `Qn / line / question / ANS / EXP` |
| `theoryidx.py [file.md]` | List every `##` subtopic and `###` theory of a theory file |
| `addtheory.py <file.md> "<## section>" <fragment.md>` | Insert a `###` theory at the end of a section; **refuses duplicates** |
| `mcqlink.py <file.md> <map.json>` | Attach the **MCQ** question-link block (idempotent) |
| `qlink.py <file.md> <map.json>` | Attach the **written-answers** question-link block (idempotent) |
| `gentoc.py <file.md \| folder>` | Regenerate the nested TOC; reports `subtopics / theories` |

Map JSON format: `{ "<exact ### theory heading>": ["<MCQ Section Name>::<question number>", ...] }`
A new `##` section is created by appending a fragment starting with `\n---\n\n## Section` directly to the theory file.

---

## Progress — 19 of 24 files done

| # | File | Status | New theories | Note |
|---|---|---|---|---|
| 1 | cloud-computing.md | ✅ done | 2 | architecture/SOA+EDA, colocation & DR |
| 2 | compiler-and-toc.md | ✅ done | 2 | regex parity patterns, pushdown automata |
| 3 | ai-and-ml.md | ✅ done | 3 | local search/GA, hyperparameters, AI languages |
| 4 | algorithm.md | ✅ done | **0** | **already fully covered — links only** |
| 5 | data-structure.md | ✅ done | 2 | tree counting formulas, queue variants |
| 6 | database.md | ✅ done | 8 | +3 new subtopics (architecture, warehousing, indexing/connectivity) |
| 7 | operating-system.md | ✅ done | 4 | +1 new subtopic (file systems) |
| 8 | ms-office.md | ✅ done | 4 | +1 new subtopic (Word/PowerPoint/Access) |
| 9 | programming-languages.md | ✅ done | 3 | +2 new subtopics (Python, Android) |
| 10 | mechanical-engineering.md | ✅ done | 11 | **whole file created — no written-answers counterpart** |
| 11 | software-engineering.md | ✅ done | 2 | metrics, requirements & scheduling |
| 12 | web-technology.md | ✅ done | 3 | PHP syntax, web servers/CMS, XML/XSLT |
| | **REMAINING (11 files)** | | | |
| 14 | c-programming.md | ✅ done | 4 | data types/identifiers, escape sequences, arrays, pointer decls |
| 15 | computer-fundamental.md | ✅ done | 4 | display/output devices, PC internals, early machines & units, software categories |
| 16 | computer-network-security.md | ✅ done | 4 | steganography/ciphers, virus types, cyber ethics/law, secure protocols |
| 17 | computer-networks.md | ⬜ pending | | 340 MCQs, 13 subtopics — **largest IT file** |
| 18 | dld.md | ✅ done | 2 | bitwise ops/masking, character encoding & data units |
| 19 | electrical-and-electronics.md | ✅ done | 5 | transformers, DC/synchronous machines, semiconductor physics, signals/filters, power systems |
| 20 | microprocessor-and-computer-architecture.md | ✅ done | 3 | memory-mapped I/O, Intel generations, machine code/assembler |
| 21 | oop.md | ✅ done | 2 | Java operators/wrappers/strings, multithreading |
| 22 | math.md | ⬜ pending | | 186 MCQs, 15 subtopics |
| 23 | english.md | ⬜ pending | | 286 MCQs, 5 subtopics |
| 24 | bangla.md | ⬜ pending | | 310 MCQs, 9 subtopics |
| 25 | gk.md | ⬜ pending | | 555 MCQs, 6 subtopics — **largest overall** |

> **`image-processing.md`** exists in the theories folder but has **no `mcq-answers` counterpart** — nothing to do for it.

---

## ▶ RESUME HERE

**Next file: `math.md`.**

The per-file loop:

```
python3 <scratchpad>/mcqdump.py <file>.md | grep -v '^        EXP'   # read questions+answers
python3 <scratchpad>/theoryidx.py <file>.md                          # what already exists
grep -ic '<keyword>' all-theories-with-previous-questions-attached/<file>.md   # coverage check
#   → write ONLY the uncovered theories into the right ## section
python3 <scratchpad>/addtheory.py <file>.md "<## section>" frag.md
python3 <scratchpad>/mcqlink.py  <file>.md mmap-<x>.json
python3 <scratchpad>/gentoc.py   <file>.md
git add -A all-theories-with-previous-questions-attached
git commit -m "<file>.md — theories from MCQ bank (...)" -m "Committed by Daihan"
git push origin main
```

---

## Corrections found in the source MCQ bank (reported, not silently propagated)

| File | Question | Issue |
|---|---|---|
| `mcq-answers/compiler-and-toc.md` | Q5, "regex for odd number of 1s" | The key gives **`0*(10*1)*10*`**, which is **WRONG** — it rejects `1101`, `10101`, `11001`, `11010`. Correct: **`0*(10*10*)*10*`**. Verified exhaustively over all binary strings up to length 14. The theory note documents the counterexample. |
| `mcq-answers/operating-system.md` | Deadlock Q1 | Already flagged `<!-- verify -->` in the bank. Correct reasoning: safe while `R ≥ N(max−1)+1`, so N ≤ 5 is safe and **N = 6** can deadlock — none of the printed options (1,2,3,4) is right. |

**Neither MCQ file was edited** — changing `mcq-answers/` is outside this task's scope and those files carry their own count/TOC invariants (see `CLAUDE.md`).

---

## Final verification to run when all 24 are done

```bash
python3 <scratchpad>/gentoc.py all-theories-with-previous-questions-attached
# then the integrity script: 0 bad anchors, 0 theories missing a question block,
# 0 bad line targets, for BOTH ../written-answers/ and ../mcq-answers/ links
```
