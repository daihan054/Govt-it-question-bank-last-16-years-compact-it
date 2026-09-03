
## rewrite prompt

TASK
`written-answers/` folder-er shob IT answer COMPLETE REWRITE koro — khub shohoj English-e.

EI TA SHOB CHEYE JORURI:
- Eta shudhu bhasha shohoj kora NA. Eta COMPLETE REWRITE.
- Protita question-er jonno AGE geeksforgeeks.org poro, sekhan theke SHIKHO,
  tarpor sei shikha theke uttor-ta NOTUN kore likho.
- Purono answer-ta dekhe shudhu shobdo bodlabe na. Purono answer bhule jao,
  GfG theke shikhe notun kore lekho.
- Decision order:
      GeeksforGeeks-e ache?          -> sekhan theke shikhe likho
      GfG-te nai ba bhalo na?        -> tutorialspoint.com theke shikhe likho
      dutotei nai?                   -> nijer gyan theke likho
- Structure, explanation-er dhoron, example, table layout — shob GfG-r moto
  hobe. Kintu lekha nijer bhashay, hubhu copy na.

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
