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

