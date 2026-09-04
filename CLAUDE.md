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
'/Users/daihan/Documents/Insurance/govt-it-question-answer/all-questions/written'
folder-er protita question-er answer lekha.

Question count HARDCODE korbe na. Koyta question ache seta shobshomoy ei file
theke dekhe nibe (eta update hote thake):
    all-questions/written/suggestion/written-question-count.md

═══════════════════════════════════════════════════════════════════
0. WORKSPACE SETUP (kaj shuru korar AGE — ekbar)
═══════════════════════════════════════════════════════════════════
- Project root-e ekta folder banao:  written-answers/
- all-questions/written/ -er SHOBGULA .md file (suggestion/ shoho)
  written-answers/ -e COPY koro. File-er nam ohoto rakho.

      mkdir -p written-answers
      cp -R all-questions/written/. written-answers/

- Answer SHUDHU written-answers/ -er copy-te lekhba.
- all-questions/written/ -er original file KOKHONO edit korba na —
  oita question-er source of truth, oita ohoto thakbe.
- Copy ekbar-i hobe. Kaj majhe thamle, abar cp diye overwrite korba NA
  (age lekha answer muche jabe). Kono file missing thakle SHUDHU sei file copy koro.

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

Emon kore lekho jemon ekjon bhalo candidate exam hall-e KOLOM diye likhbe —
porishkar, point-e point-e.

LIKHBE NA:
- bhumika ("This is an important topic in computer science...")
- question-er punorabritti
- "In conclusion", "To sum up" dhoroner filler
- nijer somporke kichu ("As an expert...")

═══════════════════════════════════════════════════════════════════
1. ANSWER LENGTH — LIMITED SPACE (GURUTTOPURNO)
═══════════════════════════════════════════════════════════════════
Written exam-er khata-y duita question-er majhe LIMITED jayga thake — oitukur
moddhei answer likhte hoy. Tai answer ojotha lomba hobe na, kintu ETO CHHOTO-O
NA je point miss hoye jay.

Target: MAIN POINT gulo puro-puri thakbe, kintu bhorat-bhorti kotha thakbe na.
Question-ta jotota chay tototai — beshi na, kom-o na.

Question type onujayi:

- Ek-line factual (port number, full form, "___ stands for")
      -> 1-3 line

- Sadharon theory / definition / "what is X" / "explain X"
      -> 1-2 line definition + 5-8 bullet point
      -> MOT 130-200 shobdo. 220 shobdo-r beshi jabe na.

- Boro theory question (10 mark, "explain in detail", "discuss")
      -> definition + type/step/component + ekta chhoto example
      -> MOT 200-280 shobdo

- "Difference between X and Y"
      -> 5-7 row-er table

- Math / subnetting / scheduling / K-map / CRC / cache
      -> PURO step-by-step. Ekhane kicchu katbe na.
         formula -> number bosao -> hisheb -> final answer alada line-e
      -> shudhu byakkha-r para bad dao, kaj-er step shob thakbe

- Diagram question
      -> diagram + 3-5 line byakkha

- Focus Writing / rochona / composition
      -> 150-200 shobdo

- Translation
      -> shudhu onubad, kono byakkha na

JA BADD DIBE (jayga bachanor jonno):
- Bhumika ar background — "X is very important in modern computing" type line.
- History / "why it was invented" / kar aabishkar — question na chaile na.
- Ekoi kotha ghuriye duibar lekha.
- Ojotha lomba example. Example dile chhoto ar to-the-point.

JA BADD DIBE NA:
- Kono main point. Point kome gele mark kome.
- Math-er step.
- Diagram — diagram jayga bachay ar mark ane, tai diagram lagle DIBE.

═══════════════════════════════════════════════════════════════════
2. LEKHAR STYLE — EASY ENGLISH (GeeksforGeeks style)
═══════════════════════════════════════════════════════════════════
Answer-er English hobe SHOJA ar SHOHOJ — thik jemon GeeksforGeeks-e lekha hoy.
Style-ta bujhte ei page-ta ekbar pore nao (WebFetch diye):
    https://www.geeksforgeeks.org/dbms/normal-forms-in-dbms/

Ei style mane:
- Chhoto, direct bakko. Ek bakko-e ekta kotha.
- Age plain-English-e ki jinish, tarpor technical term.
      thik : "A deadlock is when two processes wait for each other forever."
      bhul : "Deadlock denotes a circular wait condition arising among a set
              of processes each holding a non-preemptable resource..."
- Academic / textbook bhari shobdo bad dao (utilize -> use, in order to -> to,
  facilitates -> helps, comprises of -> has).
- Passive voice kom, active voice beshi.
- Term-ta introduce korar shomoy ek line-e mane bole dao.
- Technical keyword thik-thak likhbe — shoja mane bhul na, shoja mane porishkar.

═══════════════════════════════════════════════════════════════════
3. RESEARCH — answer ber korar poddhoti
═══════════════════════════════════════════════════════════════════
Jevabe ekjon manush hate likhto, tumio thik shei vabe korba:

Step 1 — question-ta WebSearch diye search dao.
Step 2 — first result-ta WebFetch diye poro.
Step 3 — aro 2-3 ta link (GeeksforGeeks, TutorialsPoint, Wikipedia, official doc)
         theke pore cross-check koro.
Step 4 — jeta bujhle, seta NIJER bhashay GeeksforGeeks style-e likho,
         ANSWER LENGTH section-er limit-er moddhe.

Niyom:
- KOPI-PASTE korba na. Pore, bujhe, nijer bhashay chhoto kore likhbe.
- Duita source alada kotha bolle 3rd source diye milao. Tarpor-o na mille
  line-er sheshe  <!-- verify -->  rekhe dao.
- Internet-e answer BHALO NA, ba answer-i NAI, ba question-ta Bangladesh-er
  local context (BB / BCS / bank exam) — tokhon NIJER KNOWLEDGE theke likho.
  Ei khetre-o tag lagabe na jodi tumi nishchit hou; nishchit na hole
  <!-- verify --> dao.
- Simple factual question (jemon "HTTP port number koto") — search-er dorkar nai,
  shoja likhe dao. Search shudhu tokhon jokhon sotti dorkar.

═══════════════════════════════════════════════════════════════════
4. Answer writing flow ta erokom:
═══════════════════════════════════════════════════════════════════
1. search the question in internet
2. pick some articles.
3. read them
4. Learn
5. Now write in Geeks for geeks style

═══════════════════════════════════════════════════════════════════
ANSWER FORMAT (exact)
═══════════════════════════════════════════════════════════════════
Question-er thik nicher line-e, ekta faka line diye:

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

EXAM-REALISTIC RAKHO:
- Uttor emon hobe jeta exam hall-e limited jayga-y hate likhe shesh kora jay.
- TABLE kom use koro. Table SHUDHU tokhon jokhon question-i tulona chay
  (jemon "difference between X and Y") — tokhon table-i sobcheye sposhto.
- Baki khetre bullet point, table na.

═══════════════════════════════════════════════════════════════════
BHASHA
═══════════════════════════════════════════════════════════════════
Answer-er bhasha thik hobe FILE dekhe, question-er bhasha dekhe NA (general
file chhara). Duita rule, byotikrom nai:

RULE A — IT FILE  ->  ANSWER SHOBSHOMOY ENGLISH
    Question English thakuk ba Bangla thakuk, TATE KICCHU JAY ASE NA.
    IT file-er answer 100% ENGLISH-e hobe.

    IT file (20 ta):
      ai-and-ml.md, algorithm.md, c-programming.md, cloud-computing.md,
      compiler-and-toc.md, computer-fundamental.md, computer-network-security.md,
      computer-networks.md, data-structure.md, database.md, dld.md,
      electrical-and-electronics.md, image-processing.md,
      microprocessor-and-computer-architecture.md, ms-office.md, oop.md,
      operating-system.md, programming-languages.md, software-engineering.md,
      web-technology.md

    Udahoron:
      Q: **সাবনেটিং কী? উদাহরণসহ ব্যাখ্যা কর।**
      A: Answer: Subnetting is the process of dividing one large network into
         smaller networks called subnets. ...          <- ENGLISH, Bangla NA

RULE B — GENERAL FILE  ->  QUESTION-ER BHASHA-TEI ANSWER
    General file (4 ta): math.md, gk.md, english.md, bangla.md

      question BANGLA-y lekha   -> answer BANGLA-y
      question ENGLISH-e lekha  -> answer ENGLISH-e

    Ekoi file-e duirokom question thakte pare — protita question ALADA kore
    dekhe tar nijer bhasha-y answer dibe. Puro file ek bhasha kore felbe na.

    Udahoron:
      Q: **বাংলাদেশের প্রথম রাষ্ট্রপতি কে?**
      A: Answer: শেখ মুজিবুর রহমান।                    <- BANGLA

      Q: **Who is the current Governor of Bangladesh Bank?**
      A: Answer: ...                                   <- ENGLISH

    General file-er choto khuti-nati:
      - english.md — grammar / vocabulary / correction-er answer English-e.
        Bangla -> English translation chaile shudhu onubad, byakkha na.
      - math.md — question-er bhasha onujayi step lekhbe, kintu formula,
        number, unit ar variable name shobshomoy ENGLISH/numeral-e.

DUI RULE-EI PROJOJJO:
- Technical term (pointer, deadlock, normalization, subnet, algorithm)
  SHOBSHOMOY ENGLISH — Bangla answer-er bhitore-o English-e likhbe.
- DIAGRAM-er bhitorer shob label SHOBSHOMOY ENGLISH — file jai hok,
  question-er bhasha jai hok.
- Code, SQL, command SHOBSHOMOY English.

═══════════════════════════════════════════════════════════════════
DIAGRAM
═══════════════════════════════════════════════════════════════════
NIYOM: AGE MERMAID chesta koro. Mermaid-e na hole, emon bhabe ako jate
DEKHEI BOJHA JAY — mane ashol khata-y oi diagram-ta hate ki bhabe akbo,
seta jeno porei bujhi.

1) PROTHOM CHOICE — MERMAID
   Ei gulo mermaid-e bhalo ashe:
     - flowchart / graph        -> process, algorithm, protocol flow
     - sequenceDiagram          -> handshake, request-response (TCP, HTTP, DNS)
     - erDiagram                -> ER diagram, table relation
     - stateDiagram-v2          -> process state, TCP state, FSM/DFA
     - classDiagram             -> OOP class, inheritance
     - gantt                    -> scheduling timeline

   ```mermaid
   flowchart LR
       A[Client] -->|SYN| B[Server]
       B -->|SYN-ACK| A
       A -->|ACK| B
   ```

2) MERMAID-E JA HOY NA — tokhon table ba ASCII
   Egulo mermaid-e jor kore banabe na, kharap ashe:
     - K-map                    -> markdown table
     - Logic gate circuit       -> ASCII
     - Timing / waveform        -> ASCII
     - Subnet / address chart   -> markdown table
     - Memory layout, stack     -> ASCII box
     - Tree / B-tree / heap     -> ASCII (mermaid tree kharap dekhay)
     - Binary / bit pattern     -> plain text row

   Kemon hobe — dekhei bojha jay emon:

   K-map (4 variable):

       AB\CD   00   01   11   10
        00      0    1    1    0
        01      1    1    0    0
        11      1    0    0    1
        10      0    1    1    1

   Logic gate:

       A ----|\
             | )----- Y = (A . B)'
       B ----|/  o

   Timing:

       CLK   __|‾‾|__|‾‾|__|‾‾|__
       DATA  ____|‾‾‾‾‾‾|________

   Tree:

              50
            /    \
          30      70
         /  \    /  \
       20   40  60   80

   Memory / stack:

       +------------+ 0xFFFF
       |   Stack    |  (grows down)
       +------------+
       |    Heap    |  (grows up)
       +------------+
       |    Data    |
       +------------+ 0x0000

3) SHOB DIAGRAM-ER JONNO
   - CHHOTO rakho — 5-8 node. Bishal flowchart na, exam-e ata aka jabe na.
   - SHOB LABEL ENGLISH-e. Bangla label DEBE NA, answer Bangla holeo.
   - Protita box / arrow / axis-e label thakbe. Naam chara khali box na.
   - ASCII-te alignment thik rakho — space diye milao, tab NA.
   - ASCII / K-map / timing SHOBSHOMOY ``` code fence-er bhitore dibe,
     na hole markdown-e space bhenge giye diagram noshto hoye jabe.
   - Diagram-er por 3-5 line-e byakkha — kon part ki kaj kore.
   - Diagram-ta jate ekjon manush khata-y hubohu tule likhte pare —
     eta-i ashol test.

═══════════════════════════════════════════════════════════════════
EDGE CASE
═══════════════════════════════════════════════════════════════════
- Question content-free / incomplete hole (jemon "SQL Query.....", khali entry,
  "প্রশ্ন সংগ্রহ করা সম্ভব হয়নি") -> SKIP koro, kono answer likhbe na.
- Answer niye 100% nishchit na hole line-er sheshe  <!-- verify -->  rekhe dao.

═══════════════════════════════════════════════════════════════════
THE LOOP (execution driver)
═══════════════════════════════════════════════════════════════════
SHOB subtopic-er answer likhte hobe — IT ar General (math, gk, english, bangla)
DUITAI. Kono file skip na.

SUB_TOPIC_COUNT HARDCODE korbe na. Kaj shuru korar age ei command diye
count-report theke ber koro:

    grep -c "^| | " all-questions/written/suggestion/written-question-count.md

(Ei muhurte: 243 — IT 210 + General 33.)

Cross-check (duita number ek hote hobe, na hole count-report stale):

    grep -c "^## " written-answers/*.md   # shob file-er jog, kicchu baad na

LOOP:

SUB_TOPIC_COUNT   = <upor-er command-er output>
    subtopicCompleted = 0

    while (subtopicCompleted < SUB_TOPIC_COUNT) {
        subTopic = next unanswered "## section"
        writeAnswers(subTopic)                // section-er PROTITA question
        commitAndPush()                       // sathe sathe, ekhon-i
        subtopicCompleted += 1
        updateProgressFile()
    }

    func writeAnswers(subTopic) {
        for question in subTopic {
            1. question-ta internet-e SEARCH koro
            2. koyekta article PORO
            3. bujhe LEARN koro
            4. GeeksforGeeks style-e answer LIKHO
            5. Internet-e na pele NIJE likho
            // bhasha: dekho BHASHA section
            // length: dekho ANSWER LENGTH section
        }
    }

RESEARCH BAAD DEOA JABE NA:
- Ei 5 ta step protita question-er jonno. "Ami eta jani" bole search skip
  korba NA — eta-i shob theke boro bhul.
- Ekoi section-e onek question ekoi topic-er hote pare. Tokhon topic-ta ekbar
  search kore shob article pore nao, tarpor oi topic-er protita question
  alada kore likho. Ekoi jinish barbar search korte hobe na.
- SHUDHU ei khetre search skip: port number, full form, "X stands for" — mane
  ek line-er fixed fact.

func writeAnswers() {
  for question in subTopic {
   1. Search the question in the internet
2. read several articles
3. Learn
4. Write the answer in geeks for geeks style
5. If not found in internet then write by yourself
  }
}

TRAVERSAL ORDER (deterministic rakho, jate resume kora jay):

PHASE 1 — AGE SHOB IT FILE (20 ta), alphabetical order-e:
    ai-and-ml.md, algorithm.md, c-programming.md, cloud-computing.md,
    compiler-and-toc.md, computer-fundamental.md, computer-network-security.md,
    computer-networks.md, data-structure.md, database.md, dld.md,
    electrical-and-electronics.md, image-processing.md,
    microprocessor-and-computer-architecture.md, ms-office.md, oop.md,
    operating-system.md, programming-languages.md, software-engineering.md,
    web-technology.md

PHASE 2 — TARPOR GENERAL FILE (4 ta), alphabetical order-e:
    bangla.md, english.md, gk.md, math.md

- Phase 1 puro shesh na houa porjonto Phase 2 dhorba NA.
- Protita file-er bhitore section gulo file-e jei order-e ache sei order-e
  (TOC order = count descending) — upor theke niche.

NIYOM:
- Ekta ## subtopic shesh -> SATHE SATHE commit + push. BATCH KORBE NA.
- Amar command-er jonno WAIT KORBE NA. Permission chaibe na, "next koro?"
  jiggesh korbe na. Jotokkhon na shob subtopic shesh, CONTINUOUS cholbe.
- Ekta section-er MAJHKHANE thambe na — section-er shob question shesh kore
  tarpor commit.
- Kono question-e atke gele: <!-- verify --> diye rekhe egiye jao, thambe na.
- Kono file-e error hole sei file skip kore porer file-e jao, ar sheshe report-e
  bolo kon file baad porlo.

RESUME (session bhenge gele ba abar shuru korle):
- PROGRESS.md poro -> kon file, kon section porjonto hoyeche ber koro.
- Sekhan theke abar loop chalu koro. Age kora section abar likhbe na.
- PROGRESS.md na thakle: written-answers/ -e jei section-e "Answer:" nai,
  seta theke shuru.
═══════════════════════════════════════════════════════════════════
PROCESS
═══════════════════════════════════════════════════════════════════
- Kaj SHUDHU written-answers/ folder-e.
- Loop-er niyom THE LOOP section-e — oitai follow koro.

PROTITA SUBTOPIC-ER COMMIT:
- git add written-answers/<file>.md PROGRESS.md
- Commit message : "<file name> — <section name>"
  Commit body    : "Committed by Daihan"
  Claude / AI-er KONO reference thakbe na. Co-Authored-By line DEBE NA.
- Commit-er por SATHE SATHE push.

      git add written-answers/<file>.md PROGRESS.md
      git commit -m "<file name> — <section name>" -m "Committed by Daihan"
      git push

PROGRESS.md (project root-e):
- Protita commit-er sathe update koro.
- Rakhbe: subtopicCompleted / SUB_TOPIC_COUNT, ekhon kon file + kon section,
  ar mot koyta <!-- verify --> ache.

REPORT:
- Protita FILE shesh hole ek line report: file-er nam, koyta section, koyta
  answer, koyta <!-- verify -->. Report dite giye loop thamabe na.
- Puro kaj shesh hole final report: mot answer, skip kora question,
  <!-- verify --> -er list, ar baad pora file (jodi thake).

COUNT NIYE (CLAUDE.md RULE 1):
- Answer lekhay question count BADLAY NA. Tai TOC / heading count / section order
  regenerate korar dorkar NAI.
- Kintu commit-er age check koro: written-answers/ -er protita file-er question
  count age jemon chilo ekhono temoni ache (answer-er "-" bullet line ke
  question hisebe gona jay na — question mane `^\d+\.\s`, ar answer indented).
- Count mile na mane tumi bhul kore question line bhenge felecho — thik koro.
