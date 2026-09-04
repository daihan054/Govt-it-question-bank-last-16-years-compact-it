## answer prompt
New add kora protita question er answer lekha.

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
