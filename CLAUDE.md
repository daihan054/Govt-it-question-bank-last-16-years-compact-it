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

# RULE 2 — Commits

- Commit body must say **`Committed by Daihan`**.
- **No Claude or AI reference anywhere** — no `Co-Authored-By: Claude`, no "Generated with Claude Code". This overrides the default commit trailer.
- Commit `written/` changes and `mcq/` changes as **separate commits** when a task touches both.
- Push after committing.

```bash
git commit -m "<source file name>" -m "Committed by Daihan"
```

---

# Notes

- Bengali headings need NFC normalization when matched against existing files.
- The exam suggestion sheets in `Suggestion/` are derived from this bank; if the bank changes substantially, their statistics go stale.


## answer prompt
TASK
written/ folder-er 2,673-ta question-er answer lekha.

═══════════════════════════════════════════════════════════════════
CURRENT STATE (pilot shesh)
═══════════════════════════════════════════════════════════════════
- written-answers/ folder already ache, written/ er 22-ta md file copy kora.
- written-answers/PROGRESS.md already ache (239 subtopic-er checklist).
- computer-networks.md — "Network Address Translation (NAT)" section-er 11-ta
  answer lekha ache, kintu PURONO niyome (bold ache, Q7-er answer Bangla,
  onek table).

FIRST STEP:
- Oi NAT section-ta notun rule onujayi ABAR LIKHO —
  bold shorao, Q7-er answer English koro, table kombao.
- Commit + push koro, PROGRESS.md thik rakho.
- Eta shesh hole ei prompt onujayi FULL PHASE shuru koro: written-answers/ er
  protita file-er protita ## subtopic dhore dhore, jevabe ache sei order-e.

═══════════════════════════════════════════════════════════════════
ROLE / AUDIENCE
═══════════════════════════════════════════════════════════════════
Tumi govt IT written exam-er model answer likhcho.
Uttor porbe ekjon examiner — senior engineer, kintu protita subtopic-e
specialist na — jini protita uttore ~60 second dibe.

MARK PAOA JAY jodi:
- definition thik ar porishkar hoy
- thik technical keyword thake (examiner egulo khoje)
- uttor structured hoy (bullet / step)
- diagram thik ar labeled hoy
- math-e protita step dekhano thake, shudhu final answer na

MARK HARAY jodi:
- vague ba golmele hoy
- bhul terminology thake
- structure chara ek dolar para (wall of text)
- math-e step baad jay
- ojotha lomba, question-er baire chole jay

Emon kore lekho jemon ekjon bhalo candidate exam hall-e KOLOM diye 10 minute-e
likhbe — porishkar, point-e point-e.

LIKHBE NA:
- bhumika ("This is an important topic in computer science...")
- question-er punorabritti
- "In conclusion", "To sum up" dhoroner filler
- nijer somporke kichu ("As an expert...")

═══════════════════════════════════════════════════════════════════
ANSWER FORMAT (exact)
═══════════════════════════════════════════════════════════════════
Question-er thik nicher line-e, ekta fake line diye:

    1. **Question text** *[exam tag]*

       Answer: <uttor>
       - point
       - point

INDENT (markdown-er nunotomo, extra dane sorano NA):
- Question number 1-9 hole   -> answer 3 SPACE indent
- Question number 10+ hole   -> answer 4 SPACE indent
- Kom dile list bhenge jabe, beshi dile code block hoye jabe.

BOLD:
- SHUDHU question-ta bold thakbe (jemon ache tai).
- ANSWER-ER KOTHAO KONO BOLD THAKBE NA — "Answer:" shobdo-o bold na.
- Sub-heading lagle plain text-e likho, jemon:  (a) Address limitation
- IP / port / code-e backtick use korte paro: `192.168.1.5:50000`

BULLET:
- Answer-er point "-" diye. Line-er shuru-te "1." "2." KOKHONO likhbe na.
- MCQ hole option gulor por answer boshbe; code block hole code-er por.

═══════════════════════════════════════════════════════════════════
ANSWER LENGTH (question onujayi)
═══════════════════════════════════════════════════════════════════
- Ek-line factual (port number, full form, "___ stands for")
      -> 1-3 line
- Sadharon theory question
      -> 10 mark = 250-350 shobdo
- Math / subnetting / scheduling / K-map / CRC / cache
      -> puro step-by-step solution: age sutro, tarpor number bosao,
         sesh-e final uttor alada kore
- Diagram question
      -> diagram + 3-5 line byakkha
- Focus Writing / rochona / composition
      -> 150-200 shobdo
- Translation
      -> shudhu onubad, kono byakkha na

EXAM-REALISTIC RAKHO:
- Uttor emon hobe jeta exam hall-e hate likhe shesh kora jay.
- TABLE kom use koro. Table SHUDHU tokhon jokhon question-i tulona chay
  (jemon "difference between X and Y") — tokhon table-i sobcheye sposhto.
- Baki khetre bullet point, table na.

═══════════════════════════════════════════════════════════════════
BHASHA
═══════════════════════════════════════════════════════════════════
- IT-r shob file (computer-networks, database, c-programming, oop, algorithm,
  operating-system, dld, computer-network-security, software-engineering,
  microprocessor-and-computer-architecture, data-structure, web-technology,
  cloud-computing, ai-and-ml, compiler-and-toc, electrical-and-electronics,
  image-processing, computer-fundamental)
      -> answer SHOBSHOMOY ENGLISH, question Bangla holeo.
- General-er file (math.md, gk.md, english.md, bangla.md)
      -> question Bangla hole answer BANGLA
      -> question English hole answer ENGLISH
- Technical term (pointer, deadlock, normalization, subnet) shobshomoy English.
- DIAGRAM-er bhitorer shob lekha SHOBSHOMOY ENGLISH.

═══════════════════════════════════════════════════════════════════
DIAGRAM
═══════════════════════════════════════════════════════════════════
- mermaid use koro: flowchart/graph, erDiagram, sequenceDiagram, gantt,
  stateDiagram-v2, classDiagram.
- Mermaid-e na hole (K-map, logic gate circuit, timing diagram, subnet table)
  -> markdown table ba ASCII diagram.
- Diagram-er node/edge/axis — SHOB LABEL ENGLISH-e. Bangla label DEBE NA.

═══════════════════════════════════════════════════════════════════
EDGE CASE
═══════════════════════════════════════════════════════════════════
- Question content-free / incomplete hole (jemon "SQL Query.....", khali entry,
  "প্রশ্ন সংগ্রহ করা সম্ভব হয়নি") -> SKIP koro, kono answer likhbe na.
- Answer niye 100% nishchit na hole line-er sheshe  <!-- verify -->  rekhe dao.

═══════════════════════════════════════════════════════════════════
PROCESS
═══════════════════════════════════════════════════════════════════
- Subtopic (## section) dhore dhore kaj koro.
- PROTITA ## SUBTOPIC SHESH HOLE COMMIT + PUSH.
- Commit message : "<file name> — <section name>"
  Commit body    : "Committed by Daihan"
  Claude / AI-er KONO reference thakbe na.
- Protita commit-er sathe PROGRESS.md update koro.
- Protita batch shesh hole report koro: koyta answer hoyeche, ki baki,
  koyta <!-- verify --> mark kora hoyeche.

## rewrite prompt

TASK
`written-answers/` folder-er shob IT answer ABAR LIKHO — khub shohoj English-e.
Content thik thakbe, shudhu bhasha shohoj hobe.

═══════════════════════════════════════════════════════════════════
CURRENT STATE
═══════════════════════════════════════════════════════════════════
- `written-answers/` e 22-ta md file ache, 239 subtopic, 2,673 question.
  Er moddhe 2,614-ta answer lekha ache, 59-ta content-free bole skip kora.
- `written-answers/REWRITE-PROGRESS.md` e 206-ta IT subtopic-er checklist ache.
- ai-and-ml.md — 11/11 section already rewrite kora + commit + push kora.
- Baki 195-ta IT section baki.

═══════════════════════════════════════════════════════════════════
SCOPE — kon file
═══════════════════════════════════════════════════════════════════
SHUDHU IT file (18-ta):
  ai-and-ml, algorithm, c-programming, cloud-computing, compiler-and-toc,
  computer-fundamental, computer-network-security, computer-networks,
  data-structure, database, dld, electrical-and-electronics, image-processing,
  microprocessor-and-computer-architecture, oop, operating-system,
  software-engineering, web-technology

SKIP koro (General file, 4-ta):
  math.md, gk.md, english.md, bangla.md

═══════════════════════════════════════════════════════════════════
THE LOOP
═══════════════════════════════════════════════════════════════════
subtopicCompleted = 0
while (subtopicCompleted <= 239) {
    if (subTopic is general)  { skip it }
    else {
        startRewritingTheAnswerInEasyEnglish(onCompletion: {
            commitAndPush();
            subtopicCompleted += 1;
        })
    }
}

- Ekta ## subtopic shesh -> SATHE SATHE commit + push. Batch korbe na.
- Amar command er jonno wait korbe na. Continuous cholbe jotokkhon na 239 shesh hoy.

═══════════════════════════════════════════════════════════════════
ROLE / AUDIENCE — rewrite kore-o eta thik thakbe
═══════════════════════════════════════════════════════════════════
Tumi govt IT written exam-er model answer likhcho.
Uttor porbe ekjon examiner — senior engineer, kintu protita subtopic-e
specialist na — jini protita uttore ~60 second dibe.

MARK PAOA JAY jodi:
- definition thik ar porishkar hoy
- thik technical keyword thake (examiner egulo khoje)
- uttor structured hoy (bullet / step)
- diagram thik ar labeled hoy
- math-e protita step dekhano thake, shudhu final answer na

MARK HARAY jodi:
- vague ba golmele hoy
- bhul terminology thake
- structure chara ek dolar para (wall of text)
- math-e step baad jay
- ojotha lomba, question-er baire chole jay

Emon kore lekho jemon ekjon bhalo candidate exam hall-e KOLOM diye 10 minute-e
likhbe — porishkar, point-e point-e.

LIKHBE NA:
- bhumika ("This is an important topic in computer science...")
- question-er punorabritti
- "In conclusion", "To sum up" dhoroner filler
- nijer somporke kichu ("As an expert...")
- shohoj kora mane lomba kora NA. Shohoj + choto dutoi lagbe.

═══════════════════════════════════════════════════════════════════
SOURCE — kothay theke shikhbe
═══════════════════════════════════════════════════════════════════
- Protita topic-er jonno geeksforgeeks.org poro.
- GeeksforGeeks-e na pele tutorialspoint.com poro.
- HUBHU COPY KORBE NA. Oi site theke SHIKHE nijer bhashay answer likhbe.
- Oder structure, table layout, standard example gulo follow korte paro.
- Style reference: https://www.geeksforgeeks.org/dbms/normal-forms-in-dbms/
- Copyright niye chinta korte hobe na — eta personal study material, book publish
  hobe na.

═══════════════════════════════════════════════════════════════════
WRITING STYLE — GeeksforGeeks style
═══════════════════════════════════════════════════════════════════
- Choto choto bakko. Ek bakko-e ek idea. 10-20 word per sentence.
- Shohoj shobdo:
      use (not utilise), make (not construct), need (not require),
      get (not obtain), show (not demonstrate), help (not facilitate),
      find (not ascertain), so (not therefore/hence), but (not however)
- "we" / "you" use koro. Formal academic tone na.
- Definition ekdom prothome, ek line-e, shohoj kore.
- Tarpor "In simple words:" ba "Simple example:" diye bujhao.
- Bullet point ar table beshi, ek dolar para kom.
- "Example:" label diye concrete example dao.
- Technical keyword (pointer, deadlock, normalization, subnet, pivot) English-ei
  thakbe — examiner egulo khoje, shorabe na.

LIKHBE NA:
- Lomba complex bakko, semicolon diye jora
- "It is worth noting that", "Points that distinguish", "The threat that..."
- Bhumika, "In conclusion", "To sum up"

═══════════════════════════════════════════════════════════════════
QUESTION BOUNDARY — shob cheye important
═══════════════════════════════════════════════════════════════════
- md file-e jei question ache, SHUDHU tar uttor dibe.
- Question-er boundary-r BAIRE JABE NA.
- Question ja chay ni, ta add korbe na — extra section, extra mnemonic,
  extra related topic kichui na.
- Example: question jodi shudhu "validation set er role" chay, tahole
  training/test set er tulona add korbe na.

═══════════════════════════════════════════════════════════════════
DIAGRAM
═══════════════════════════════════════════════════════════════════
- GeeksforGeeks-e relevant diagram thakle setao niye ashbe.
- Image link debe na — mermaid ba ASCII diye NIJE eke dibe, jate markdown-e
  render hoy.
- mermaid: flowchart/graph, erDiagram, sequenceDiagram, stateDiagram-v2,
  classDiagram, gantt
- mermaid-e na hole (K-map, logic gate, timing diagram, subnet table)
  -> markdown table ba ASCII art.
- Diagram-er SHOB label English-e. Bangla label debe na.

═══════════════════════════════════════════════════════════════════
ANSWER FORMAT (exact) — age jemon chilo, tai thakbe
═══════════════════════════════════════════════════════════════════
    1. **Question text** *[exam tag]*

       Answer: <uttor>
       - point
       - point

INDENT:
- Question number 1-9   -> answer 3 SPACE indent
- Question number 10+   -> answer 4 SPACE indent

BOLD:
- SHUDHU question bold thakbe.
- ANSWER-ER KOTHAO KONO BOLD NA — "Answer:" shobdo-o bold na.
- Sub-heading lagle plain text: (a) Address limitation
- IP / port / code-e backtick: `192.168.1.5:50000`

BULLET:
- "-" diye. Line-er shurute "1." "2." KOKHONO na.
- MCQ hole option-er por answer. Code block hole code-er por.

LENGTH:
- Ek-line factual -> 1-3 line
- Sadharon theory (10 mark) -> 250-350 shobdo
- Math / subnetting / scheduling / K-map / CRC / cache
      -> step-by-step: age FORMULA, tarpor number bosao, sheshe
         "Final answer:" alada kore
- Diagram question -> diagram + 3-5 line byakkha
- Exam hall-e hate likhe shesh kora jay emon rakho.

TABLE:
- Table SHUDHU tokhon jokhon question tulona chay ("difference between X and Y")
  ba ekta list-er compare lage. Baki khetre bullet.

═══════════════════════════════════════════════════════════════════
LANGUAGE
═══════════════════════════════════════════════════════════════════
- IT file-er answer SHOBSHOMOY ENGLISH, question Bangla holeo.
- NO BANGLISH kothao. Only English.
- General file (math, gk, english, bangla) skip — ogulo touch korbe na.

═══════════════════════════════════════════════════════════════════
EDGE CASE
═══════════════════════════════════════════════════════════════════
- Jei question content-free / incomplete (figure nai, code nai, "প্রশ্ন সংগ্রহ
  করা সম্ভব হয়নি") ar age skip kora hoyeche -> ekhono skip-i thakbe.
- Answer niye 100% nishchit na hole line-er sheshe  <!-- verify -->  rakho.
- Question line, exam tag, question-er nijer code block / option / table
  KOKHONO change korbe na. Shudhu "Answer:" block-ta replace hobe.

═══════════════════════════════════════════════════════════════════
VERIFY — commit-er age protibar
═══════════════════════════════════════════════════════════════════
- Heading count == asol question count
- Protita answer-er indent thik (3 for Q1-9, 4 for Q10+)
- Answer-e kono bold nai
- Code fence balanced
- Math-er number gulo Python cholie verify kora

═══════════════════════════════════════════════════════════════════
COMMIT
═══════════════════════════════════════════════════════════════════
- Ekta ## subtopic shesh -> ekta commit + push.
- Commit message : "<file name> — <section name>"
- Commit body    : "Committed by Daihan"
- Claude / AI-er KONO reference thakbe na.
- Protita commit-e REWRITE-PROGRESS.md update hobe.

```bash
git commit -m "database.md — Normalization" -m "Committed by Daihan"
git push
```

═══════════════════════════════════════════════════════════════════
REPORT
═══════════════════════════════════════════════════════════════════
Protita file shesh hole report koro:
- koyta section rewrite hoyeche
- koyta baki
- koyta <!-- verify --> mark kora
