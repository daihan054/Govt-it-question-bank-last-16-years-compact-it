<!-- TOC START -->
**Table of Contents** — 14 subtopics · 152 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [SDLC Phases & Models](#sdlc-phases--models-45) | 45 |
| 2 | [Software Testing & Evaluation](#software-testing--evaluation-40) | 40 |
| 3 | [UML Diagrams (Class, Use Case, Sequence)](#uml-diagrams-class-use-case-sequence-14) | 14 |
| 4 | [Software Architecture & Design Patterns (MVC)](#software-architecture--design-patterns-mvc-13) | 13 |
| 5 | [Software Requirements Engineering](#software-requirements-engineering-10) | 10 |
| 6 | [Software Project Management & Organization](#software-project-management--organization-9) | 9 |
| 7 | [Software Design Principles (Coupling & Cohesion)](#software-design-principles-coupling--cohesion-5) | 5 |
| 8 | [Software Cost Estimation & Build vs Buy Decisions](#software-cost-estimation--build-vs-buy-decisions-4) | 4 |
| 9 | [IT Governance, Audit & Risk Management](#it-governance-audit--risk-management-4) | 4 |
| 10 | [Data Flow Diagrams (DFD)](#data-flow-diagrams-dfd-2) | 2 |
| 11 | [Code Smells & Refactoring](#code-smells--refactoring-2) | 2 |
| 12 | [Open Source Software & Licensing](#open-source-software--licensing-2) | 2 |
| 13 | [CI/CD & DevOps Methodologies](#cicd--devops-methodologies-1) | 1 |
| 14 | [UI/UX Design](#uiux-design-1) | 1 |

<!-- TOC END -->

---

## SDLC Phases & Models (45)

1. A software company has been hired to develop an Online Library Management System for a university. The librarian wants the system to be delivered in phases so that feedback from users can be incorporated after each release. As a software developer, identify the most suitable Software Development Life Cycle (SDLC) model for this project. Justify your choice by mentioning two advantages of the selected model. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Recommended model: the `Incremental model`, delivered in phases. `Agile / Scrum` is the equally acceptable answer, and the justification is the same.

   Why it fits this project
   ```
      The librarian's requirement is EXPLICIT :

        "delivered in PHASES"                -> incremental delivery
        "feedback incorporated AFTER EACH
         RELEASE"                            -> customer feedback loop

      Waterfall cannot do this - it delivers ONCE, at the very end,
      so feedback can only arrive when it is too late to act on.
   ```

   How the project would be phased
   ```
      Increment 1 : book catalogue - add , search , view
      Increment 2 : member management , issue and return
      Increment 3 : fine calculation , reservations
      Increment 4 : reports , notifications , admin dashboard

      Each increment is fully ANALYSED , DESIGNED , CODED , TESTED and
      DELIVERED as working software. The librarian uses it, gives
      feedback, and that feedback shapes the next increment.
   ```
   ```mermaid
   flowchart LR
       A[Increment 1: Catalogue] --> B[Feedback]
       B --> C[Increment 2: Issue/Return]
       C --> D[Feedback]
       D --> E[Increment 3: Fines]
   ```

   Two advantages of the chosen model

   1. Working software is delivered early, and feedback can still change the outcome
   ```
      The librarian sees a usable catalogue after increment 1 instead
      of waiting months for everything. If the search screen is wrong,
      it is corrected in increment 2 - while it is still CHEAP to fix.
      In Waterfall the same error would be found during acceptance
      testing, when the whole design has already been built on it.
   ```

   2. Requirements may change without wrecking the plan
   ```
      A university library's rules change - a new fine policy, a new
      category of member. Incremental development ABSORBS such a change
      in the next increment. Waterfall freezes requirements after the
      analysis phase, so any change means a costly formal amendment.
   ```

   Two further advantages worth one line each
   ```
      RISK IS REDUCED  - a problem shows up in one small increment,
           not in a single huge delivery.
      RETURN COMES EARLIER - the library starts using the catalogue
           while the rest is still being built.
   ```
   - The one condition to state: the `core architecture` — the database schema and the module boundaries — must be designed well in increment 1. If it is not, later increments force expensive rework. This is the standard weakness of incremental development, and it is why the first increment should carry the architectural risk.

2. What are the main phases of the Software Development Life Cycle (SDLC)? Explain each phase briefly. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: The `Software Development Life Cycle (SDLC)` is the structured process a software product goes through, from the first idea to final retirement. It splits the work into ordered phases so that quality and cost stay under control.

   The phases
   ```mermaid
   flowchart TD
       A[1. Planning] --> B[2. Requirement Analysis]
       B --> C[3. Design]
       C --> D[4. Implementation / Coding]
       D --> E[5. Testing]
       E --> F[6. Deployment]
       F --> G[7. Maintenance]
   ```

   1. Planning and feasibility study
   - Decide `what` is to be built and `whether it is worth building`. Fix the scope, the budget, the schedule and the team. The feasibility study checks whether the project is `technically`, `economically`, `operationally` and `legally` possible.
   - Output: `project plan`, feasibility report.

   2. Requirement analysis
   - Collect what the users actually need, through interviews, questionnaires, observation and study of existing documents. Separate `functional` requirements (what the system must do) from `non-functional` ones (speed, security, availability).
   - Output: `SRS` — Software Requirements Specification, signed off by the client.

   3. Design
   - Decide `how` the system will be built. `High-level design` fixes the architecture, the modules and the database schema; `low-level design` fixes each module's algorithms, interfaces and screens.
   - Output: `design document`, ER diagrams, DFDs, UML diagrams.

   4. Implementation — coding
   - Programmers write the actual code, module by module, following the design and the coding standards. This is usually the longest phase in effort, though not always in calendar time.
   - Output: `source code`, unit-tested modules.

   5. Testing
   - Find the defects before the user does. `Unit` testing checks each module, `integration` testing checks the modules together, `system` testing checks the whole product against the SRS, and `acceptance` testing is done by the customer.
   - Output: `test reports`, a defect-free build.

   6. Deployment
   - Install the system in the real environment, migrate the data, train the users and go live. Release may be `direct`, `parallel` (old and new run together), `pilot` (one branch first) or `phased`.
   - Output: the `live system`.

   7. Maintenance
   - Keep the system working after release. Four kinds:
   ```
      CORRECTIVE  - fix defects found in use
      ADAPTIVE    - adjust to a new OS , database or law
      PERFECTIVE  - add features , improve performance
      PREVENTIVE  - restructure the code to avoid future trouble
   ```
   - Maintenance typically consumes `60 to 80 per cent` of the total lifetime cost, far more than development.

   - The one fact worth adding: the `cost of fixing a defect rises sharply with the phase in which it is found`. An error caught in requirements costs almost nothing; the same error found after deployment can cost a hundred times more. This is the entire justification for having a disciplined life cycle.

3. Critically analyze the limitations of the Waterfall model and explain how Agile methodologies address those limitations. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

   Answer: Limitations of the Waterfall model

   1. Requirements must be frozen at the start
   - The model assumes the customer can state every requirement completely and correctly before any design begins. In practice users discover what they want only when they `see` something working.

   2. No working software until very late
   - The customer sees nothing until the testing phase. If the product is wrong, months of work are already spent.

   3. Change is very expensive
   ```
      Phase in which an error is found     relative cost to fix
      ------------------------------------------------------
      Requirements                                1
      Design                                      5
      Coding                                     10
      Testing                                    50
      After release                             100+

      Waterfall finds requirement errors LATE - exactly where they
      cost the most.
   ```

   4. No going back
   - Each phase must be finished and signed off before the next begins. There is no formal route back to an earlier phase, so a mistake made in analysis is carried through the whole project.

   5. Risk is discovered late
   - Technical risks — an integration that will not work, a performance target that cannot be met — surface only in testing.

   6. Poor for long or unclear projects
   - The longer the project, the more the business changes underneath it. A two-year Waterfall project can deliver exactly what was asked for and still be useless.

   7. Testing is a single phase at the end
   - Defects accumulate and arrive together in one crushing batch.

   How Agile addresses each limitation

   | Waterfall limitation | Agile answer |
   |---|---|
   | Requirements frozen early | Requirements are a `living backlog`, re-prioritised every sprint |
   | Nothing working until the end | `Working software` every 1–4 week sprint |
   | Change is expensive | "`Responding to change` over following a plan" — change is expected |
   | No going back | Every sprint repeats analysis, design, code and test |
   | Risk found late | A sprint review every few weeks exposes risk early |
   | Customer sees the product once | The customer is `present throughout` and reviews each increment |
   | Testing only at the end | `Continuous testing`, TDD and CI on every commit |

   How Agile works
   ```mermaid
   flowchart LR
       A[Product Backlog] --> B[Sprint Planning]
       B --> C[Sprint: 1-4 weeks]
       C --> D[Working increment]
       D --> E[Review + Retrospective]
       E --> A
   ```
   ```
      The four Agile values :
        Individuals and interactions  over  processes and tools
        Working software              over  comprehensive documentation
        Customer collaboration        over  contract negotiation
        Responding to change          over  following a plan

      The right-hand items have value ; the left-hand ones have MORE.
   ```

   Where Waterfall is still the better choice
   - Requirements genuinely fixed and well understood — a payroll system following a published government rule.
   - Contracts or regulators that demand a complete specification and full documentation up front.
   - Safety-critical work, where heavy formal review is mandatory.
   - Short, small projects where the ceremony of Agile costs more than it saves.

   - The fair conclusion: Agile is not universally superior. It solves Waterfall's problem — `late feedback` — but it needs a `committed customer`, a `co-located, skilled team` and tolerance for `light documentation`. Where those are absent, Agile fails in its own way.

4. What is SDLC, Steps of SDLC, in which Step user acceptance assured? *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer: What SDLC is
   - `SDLC` stands for `Software Development Life Cycle`. It is the structured process a software product passes through from the first idea to final retirement, divided into ordered phases so that cost, time and quality stay under control.

   Steps of SDLC
   ```mermaid
   flowchart TD
       A[1. Planning and feasibility] --> B[2. Requirement analysis]
       B --> C[3. Design]
       C --> D[4. Implementation / coding]
       D --> E[5. Testing]
       E --> F[6. Deployment]
       F --> G[7. Maintenance]
   ```
   ```
      1. PLANNING AND FEASIBILITY
           Fix the scope, budget, schedule and team. Check technical,
           economic, operational and legal feasibility.
           Output : project plan , feasibility report.

      2. REQUIREMENT ANALYSIS
           Gather what users need, through interviews, questionnaires
           and observation. Separate FUNCTIONAL from NON-FUNCTIONAL
           requirements.
           Output : SRS - Software Requirements Specification.

      3. DESIGN
           Decide HOW it will be built. High-level design fixes the
           architecture, modules and database ; low-level design fixes
           algorithms, interfaces and screens.
           Output : design document , ER diagram , DFD , UML.

      4. IMPLEMENTATION / CODING
           Write the code module by module, following the design and
           the coding standards.
           Output : source code , unit-tested modules.

      5. TESTING
           Unit -> integration -> system -> ACCEPTANCE testing.
           Output : test reports , a stable build.

      6. DEPLOYMENT
           Install in the live environment, migrate data, train users,
           go live.
           Output : the running system.

      7. MAINTENANCE
           Corrective , adaptive , perfective and preventive changes
           after release. Consumes 60-80 per cent of lifetime cost.
   ```

   In which step is user acceptance assured?
   ```
      USER ACCEPTANCE TESTING (UAT) - part of the TESTING phase, and
      the LAST level of testing before deployment.
   ```
   - Why it is UAT: the earlier levels are run by the `developers` and check that the software works as `built`. UAT is run by the `actual users` in a realistic environment and checks that the software does what the `business needs`. It is the customer's formal sign-off, and it is what authorises deployment.
   ```
      The four levels of testing, in order :

        UNIT         each module        by developers
        INTEGRATION  modules together   by developers
        SYSTEM       whole product      by the QA team
        ACCEPTANCE   business fitness   by the CUSTOMER   <- sign-off
   ```
   - Two forms of acceptance testing worth naming: `alpha testing`, done by users at the developer's site, and `beta testing`, done by real users in their own environment before general release.
   - A qualification: acceptance is `assured` at UAT, but it is `prepared for` much earlier — the acceptance criteria come straight from the `SRS` agreed in the requirement analysis phase. If the SRS was wrong, UAT will fail however good the code is.

5. **What is SDLC? Describe the steps of SDLC.** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)], [NPCBL Executive Trainee (Software) 26.05.2023 compact it 500 (ET: IBA)]*

   Answer: What SDLC is
   - `SDLC` stands for `Software Development Life Cycle`. It is the structured process a software product goes through from the first idea to final retirement, split into ordered phases so that cost, schedule and quality remain controllable.
   - Why it is needed: without a defined life cycle, requirements are missed, defects are found late, and the cost of correction rises steeply.
   ```
      Cost of fixing an error, by the phase where it is FOUND :

        Requirements   1        Testing        50
        Design         5        After release  100+
        Coding        10

      This is the whole justification for a disciplined process.
   ```

   The steps
   ```mermaid
   flowchart TD
       A[1. Planning and feasibility] --> B[2. Requirement analysis]
       B --> C[3. Design]
       C --> D[4. Coding]
       D --> E[5. Testing]
       E --> F[6. Deployment]
       F --> G[7. Maintenance]
   ```

   1. Planning and feasibility study
   - Fix the scope, the budget, the schedule and the team. Check `technical`, `economic`, `operational`, `schedule` and `legal` feasibility.
   - Output: project plan, feasibility report.

   2. Requirement analysis
   - Gather what the users actually need — interviews, questionnaires, observation, study of existing documents. Separate `functional` requirements (what it must do) from `non-functional` ones (speed, security, availability).
   - Output: `SRS`, signed off by the customer.

   3. Design
   - Decide how it will be built. `High-level design` fixes the architecture, modules and database schema; `low-level design` fixes each module's algorithms, interfaces and screens.
   - Output: design document, ER diagrams, DFDs, UML diagrams.

   4. Coding — implementation
   - Write the code module by module against the design, following the agreed coding standards, with version control and code review.
   - Output: source code, unit-tested modules.

   5. Testing
   ```
      UNIT         each module alone         by developers
      INTEGRATION  modules working together  by developers
      SYSTEM       whole product vs the SRS  by the QA team
      ACCEPTANCE   business fitness          by the CUSTOMER
   ```
   - Output: test reports and a stable build.

   6. Deployment
   - Install in the live environment, migrate the data, train the users and go live. The release may be `direct`, `parallel`, `pilot` or `phased`.
   - Output: the running system.

   7. Maintenance
   ```
      CORRECTIVE  fix defects found in use
      ADAPTIVE    adjust to a new OS , database or law
      PERFECTIVE  add features , improve performance
      PREVENTIVE  restructure code to avoid future trouble
   ```
   - Maintenance takes `60 to 80 per cent` of the total lifetime cost — far more than development.

   - The models that arrange these phases differently: `Waterfall` runs them strictly once in order; `Iterative` and `Incremental` repeat them per release; `Spiral` adds explicit risk analysis each round; and `Agile` compresses the whole cycle into a 1–4 week sprint, repeated continuously.

6. **Why agile model is better than waterfall model?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: Agile is better than Waterfall in the situations that dominate modern software work — changing requirements and a customer who cannot state everything in advance. The reasons follow.

   1. Early and continuous delivery
   ```
      WATERFALL : the customer sees NOTHING until testing, often
           months later. If the product is wrong, the whole effort is
           already spent.
      AGILE     : WORKING SOFTWARE every 1-4 week sprint. The customer
           uses it and reacts while change is still cheap.
   ```

   2. Change is welcomed rather than resisted
   - Waterfall freezes requirements after analysis; any later change needs a formal, costly amendment. Agile treats the requirement list as a `living backlog`, re-prioritised at every sprint. One of the four Agile values is exactly "`responding to change` over following a plan".

   3. Errors are found when they are cheap
   ```
      Cost of fixing an error, by the phase where it is FOUND :

        Requirements   1        Testing        50
        Design         5        After release  100+
        Coding        10

      Waterfall tests ONCE, at the end - the most expensive point.
      Agile tests CONTINUOUSLY, inside every sprint.
   ```

   4. Risk is exposed early
   - A sprint review every few weeks reveals technical and business risk while there is still time to act. In Waterfall an integration problem or a missed performance target surfaces only in the testing phase.

   5. The customer is involved throughout
   - Agile puts a customer representative (the `Product Owner`) with the team. Waterfall involves the customer at requirement sign-off and again at acceptance — with a long silence between.

   6. Better morale and visibility
   - Daily stand-ups, sprint reviews and retrospectives make progress visible and let the team improve its own process. Waterfall progress is measured by documents produced, which can look healthy while the product is not.

   Side by side

   | Point | Waterfall | Agile |
   |---|---|---|
   | Requirements | `Frozen` after analysis | `Evolve` every sprint |
   | Delivery | `Once`, at the end | Every `1–4 weeks` |
   | Customer contact | Start and end only | `Continuous` |
   | Testing | One phase at the end | `Every sprint` |
   | Cost of change | `Very high` | `Low` |
   | Documentation | Heavy | Light, just enough |

   Where Waterfall is still the right choice
   - Requirements genuinely fixed and well understood — a payroll system implementing a published rule.
   - Contracts or regulators that demand a full specification and documentation up front.
   - Safety-critical systems needing formal review at every stage.
   - Small, short projects where Agile's ceremonies cost more than they save.

   - The honest answer: Agile is better `for most modern projects`, not for all. It requires a committed customer, a skilled team and tolerance for light documentation. Where those are missing, Agile fails in its own way — and a well-run Waterfall project is better than a badly-run Agile one.

7. **a) What are the advantages and disadvantages of the Agile Model compared to the Waterfall Model in software development?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

   Answer: Advantages of Agile over Waterfall

   | Point | Waterfall | Agile |
   |---|---|---|
   | Requirements | `Frozen` after analysis | `Evolve` every sprint |
   | First working software | Only at the `end` | Every `1–4 weeks` |
   | Cost of change | `Very high` | `Low` |
   | Customer involvement | Start and end only | `Continuous` |
   | Testing | One phase at the end | `Inside every sprint` |
   | Risk discovery | `Late` | `Early` |
   | Documentation | Heavy and formal | Light, "just enough" |
   | Team structure | Specialised, hierarchical | `Cross-functional`, self-organising |

   - `Early delivery` — the customer sees usable software within weeks and can act on it while change is still cheap.
   - `Change is welcomed` — the backlog is re-prioritised each sprint, so a shift in business need does not wreck the plan.
   - `Defects found early` — an error costs 1 unit in requirements and over 100 after release; continuous testing catches them at the cheap end.
   - `Lower risk` — a sprint review every few weeks exposes technical and business risk in time to react.
   - `Higher customer satisfaction` — the Product Owner sits with the team, so what is built is what is wanted.
   - `Better visibility` — daily stand-ups and sprint reviews show real progress, not document counts.

   Disadvantages of Agile compared with Waterfall
   - `Weak documentation` — light documentation hurts when the team changes, or when the system must be maintained years later by other people.
   - `Cost and schedule are hard to fix in advance` — Waterfall's fixed scope allows a firm quotation; Agile's evolving scope does not, which is a genuine problem for `government tenders` and fixed-price contracts.
   - `Scope creep` — welcoming change can become never finishing, unless the Product Owner is disciplined.
   - `Needs a committed customer` — Agile assumes a customer representative is continuously available. Many organisations cannot supply one.
   - `Needs a skilled, co-located team` — self-organising teams of junior or scattered developers usually underperform.
   - `Poor fit for safety-critical or heavily regulated work`, where formal specification and traceability are mandatory.
   - `Less predictable for large systems`, where the overall architecture must be right from the start.

   Where each one wins
   ```
      USE WATERFALL when :
        requirements are fixed and fully understood
        the contract or regulator demands full documentation
        the system is safety-critical
        the project is small and short

      USE AGILE when :
        requirements are unclear or expected to change
        the customer can stay involved
        early delivery matters
        the team is skilled and cross-functional
   ```
   - The middle path used in practice is a `hybrid`: Waterfall-style planning and architecture at the start to satisfy the contract, then Agile sprints for the build. Large organisations, including banks, usually work this way rather than adopting either model in its pure form.

8. **Write down the differences between Agile model and Waterfall model in Software development. What is white box testing?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

   Answer: Differences between the Agile model and the Waterfall model

   | Point | Waterfall | Agile |
   |---|---|---|
   | Approach | `Sequential` — one phase after another | `Iterative` and incremental |
   | Requirements | `Frozen` after the analysis phase | `Evolve` — a living backlog |
   | Delivery | `Once`, at the very end | Working software every `1–4 weeks` |
   | Customer involvement | Start and end only | `Continuous` — a Product Owner in the team |
   | Testing | A single phase `at the end` | `Inside every sprint`, continuously |
   | Cost of change | `Very high` | `Low` |
   | Documentation | Heavy and formal | Light, "just enough" |
   | Team | Specialised, hierarchical | `Cross-functional`, self-organising |
   | Risk discovery | `Late` — in testing | `Early` — at each sprint review |
   | Best suited to | Fixed, well-understood requirements | Unclear or changing requirements |

   ```mermaid
   flowchart LR
       subgraph Waterfall
       A[Requirements] --> B[Design] --> C[Code] --> D[Test] --> E[Deploy]
       end
       subgraph Agile
       F[Backlog] --> G[Sprint] --> H[Increment] --> I[Review] --> F
       end
   ```

   What is white box testing
   - `White box testing` tests a program with `full knowledge of its internal code and logic`. The tester reads the source and designs cases to exercise its statements, branches and paths. It is also called `structural`, `glass box` or `clear box` testing, and it is normally done by `developers`.
   ```
      The tester can SEE INSIDE the box :

           +------------------------+
           |  if (a > b)            |   the tester writes cases to
           |      x = a;            |   force BOTH branches, not just
           |  else                  |   the one the user happens to hit
           |      x = b;            |
           +------------------------+
   ```

   Coverage criteria — what "tested" means
   ```
      STATEMENT COVERAGE  every line executed at least once
      BRANCH   COVERAGE   every if takes both the true and false path
      PATH     COVERAGE   every possible route through the code
      CONDITION COVERAGE  every sub-condition of a compound test is
                          evaluated both ways
      LOOP     COVERAGE   the loop runs 0 times , once , and many times
   ```
   ```
      Example :  if (a > 0 && b > 0)  x = 1;  else  x = 2;

      STATEMENT coverage needs 1 test  : a=1 , b=1
      BRANCH    coverage needs 2 tests : (1,1) and (1,-1)
      CONDITION coverage needs cases making a>0 both T and F, and
                b>0 both T and F.
   ```

   What it finds and what it misses
   - Finds: dead code, uncovered branches, wrong loop boundaries, logic errors, security holes such as unchecked buffers, and infinite loops.
   - Misses: `missing requirements`. If a required feature was never coded, there is no code to cover, so white box testing cannot detect its absence.

   - The contrast usually asked for: `black box` testing looks only at inputs and outputs, ignoring the code, and is done by testers from the `SRS`; `white box` testing works from the `code`. `Grey box` combines the two — partial knowledge of the internals, used heavily in security testing. The two are complements, not alternatives.

9. **You are asked to lead a team of software engineers to develop an application software system for your company and deploy it as fast as possible. You need to gather user requirements, design, develop, test and then deploy the system. Between Waterfall Approach and Incremental Approach, which software development approach will you take for your software project? Explain your answer.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 338 (ET: BIBM)]*

   Answer: Chosen approach: the `Incremental approach`.

   Why, given the constraint in the question
   ```
      The requirement is "deploy it AS FAST AS POSSIBLE".

      WATERFALL delivers ONCE - nothing is usable until the very last
      phase. The first deployment is therefore the LATEST possible
      date.

      INCREMENTAL delivers the first working version after increment
      1, and the rest follows. The first deployment is the EARLIEST
      possible date.

      The stated goal decides the answer on its own.
   ```

   How the project would run
   ```
      Increment 1 : core feature - gather requirements , design , code ,
                    test , DEPLOY.  The company starts using it.
      Increment 2 : the next most valuable feature , on the same cycle.
      Increment 3 : and so on.

      Each increment is a complete mini-SDLC producing WORKING SOFTWARE.
   ```
   ```mermaid
   flowchart LR
       A[Increment 1: core] --> B[Deploy + feedback]
       B --> C[Increment 2: next feature]
       C --> D[Deploy + feedback]
       D --> E[Increment 3]
   ```

   The reasons, stated for the examiner

   1. `Fastest route to a usable system.` Business value arrives after the first increment instead of at the end of the project.
   2. `Feedback while it still matters.` Users react to increment 1, and that shapes increment 2 — before the mistake has been built into everything.
   3. `Requirements need not be complete on day one.` Only increment 1 must be fully understood now; the rest can be settled as the project runs. Waterfall would stall until every requirement was signed off.
   4. `Lower risk.` A problem appears inside one small increment, not in a single large delivery.
   5. `Change is absorbed cheaply.` A new business need becomes an item in a later increment rather than a formal change request against a frozen specification.

   Comparison

   | Point | Waterfall | Incremental |
   |---|---|---|
   | First deployment | At the `very end` | After `increment 1` |
   | Requirements needed up front | `All` of them | Only for the current increment |
   | Cost of change | `Very high` | Low |
   | Risk | Concentrated at the end | Spread across increments |
   | Customer feedback | Once, too late | After `every` increment |

   When Waterfall would have been the right answer
   - If the requirements were fixed, fully known and unlikely to change — a payroll system implementing a published government rule.
   - If a contract or regulator demanded a complete specification and full documentation before coding.
   - If the system were safety-critical, needing formal review at every stage.

   - The one precaution to state: the `core architecture` — database schema and module boundaries — must be got right in increment 1. If it is not, later increments force rework, and that is the standard failure mode of incremental development. So increment 1 should carry the architectural risk deliberately, not just the easiest feature.

10. **(খ) Spiral Model চিত্রসহ ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What the Spiral model is
    - The `Spiral model`, proposed by Barry Boehm in 1986, combines the ordered phases of the Waterfall model with the repetition of iterative development, and adds one thing neither of them has: `explicit risk analysis in every cycle`. The project spirals outward, each loop producing a more complete product.

    Diagram
    ```
                        Determine objectives  |  Identify and RESOLVE
                        alternatives          |  RISKS  (prototype)
                        constraints           |
                  ------------------------------------------------
                                              |
                        Plan the next         |  Develop and
                        iteration             |  VERIFY this level
                                              |
    ```
    ```
            cost / progress increases OUTWARD ->

                  +---------------------------+
                  |   Quadrant 1  |  Quadrant 2|
                  |  OBJECTIVES   |    RISK    |
                  |               |  ANALYSIS  |
                  +---------------+------------+
                  |   Quadrant 4  |  Quadrant 3|
                  |     PLAN      | DEVELOP &  |
                  |  next cycle   |    TEST    |
                  +---------------------------+

       Loop 1 : concept          -> prototype 1
       Loop 2 : requirements     -> prototype 2
       Loop 3 : design           -> prototype 3
       Loop 4 : build and test   -> the release
    ```
    ```mermaid
    flowchart LR
        A[1. Objectives and alternatives] --> B[2. Risk analysis and prototype]
        B --> C[3. Develop and verify]
        C --> D[4. Plan the next iteration]
        D --> A
    ```

    The four quadrants of every loop
    ```
       1. DETERMINE OBJECTIVES
            Fix the goals, the alternatives and the constraints for this
            cycle - cost, schedule, interfaces.

       2. IDENTIFY AND RESOLVE RISKS
            THE DEFINING STEP. List the risks - unclear requirements,
            an unproven technology, a performance target. Build a
            PROTOTYPE, run a simulation or a benchmark to settle each
            one. If a risk cannot be resolved, the project may be
            STOPPED here, before more money is spent.

       3. DEVELOP AND VERIFY
            Build and test this level of the product : a prototype in
            early loops, real code in later ones.

       4. PLAN THE NEXT ITERATION
            The customer reviews the result and the next cycle is
            planned. Each loop ends with a formal review.
    ```

    Advantages
    - `Risk is handled explicitly` — the only classical model that does. Suited to large, expensive and uncertain projects.
    - Requirements may be `refined at every loop`, so they need not be complete at the start.
    - The customer `reviews after every cycle`, so feedback arrives repeatedly.
    - A doomed project can be `stopped early`, at a review, rather than after full expenditure.
    - Prototypes reduce technical uncertainty before real money is committed.

    Disadvantages
    - `Expensive` — the repeated risk analysis and prototyping cost time and money, so it is unsuitable for small projects.
    - Depends on `expert risk assessors`; a wrong risk judgement defeats the whole purpose.
    - The number of loops is `not fixed`, so cost and schedule are hard to predict.
    - `Complex to manage` and heavy in documentation.

    - The point examiners look for: the Spiral model's distinguishing feature is `risk-driven` development. Waterfall is document-driven and Agile is customer-driven; Spiral is the one that decides what to do next by asking `which risk is largest`. It is used for large, long, high-cost systems — defence, aerospace, core banking — not for ordinary applications.

11. **Write down the step of SDLC?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)], [BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

    Answer: The steps of `SDLC` — the Software Development Life Cycle.
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```

    1. Planning and feasibility study
    - Fix the scope, budget, schedule and team. Check `technical`, `economic`, `operational`, `schedule` and `legal` feasibility.
    - Output: project plan, feasibility report.

    2. Requirement analysis
    - Collect what the users need — interviews, questionnaires, observation, study of existing documents. Separate `functional` from `non-functional` requirements.
    - Output: `SRS`, signed off by the customer.

    3. Design
    - Decide how it will be built. `High-level design` fixes the architecture, modules and database schema; `low-level design` fixes algorithms, interfaces and screens.
    - Output: design document, ER diagram, DFD, UML diagrams.

    4. Coding — implementation
    - Write the code module by module against the design, following coding standards, under version control.
    - Output: source code, unit-tested modules.

    5. Testing
    ```
       UNIT         each module alone         by developers
       INTEGRATION  modules working together  by developers
       SYSTEM       whole product vs the SRS  by the QA team
       ACCEPTANCE   business fitness          by the CUSTOMER
    ```
    - Output: test reports and a stable build.

    6. Deployment
    - Install in the live environment, migrate data, train users, go live. The release may be `direct`, `parallel`, `pilot` or `phased`.
    - Output: the running system.

    7. Maintenance
    ```
       CORRECTIVE  fix defects found in use
       ADAPTIVE    adjust to a new OS , database or law
       PERFECTIVE  add features , improve performance
       PREVENTIVE  restructure to avoid future trouble
    ```
    - Maintenance takes `60 to 80 per cent` of the total lifetime cost.

    - Two facts worth adding. The `number of phases` quoted varies between books — 5, 6 or 7 — because planning and feasibility are sometimes merged, and deployment is sometimes folded into maintenance. And the same phases are arranged differently by different `models`: Waterfall runs them once in strict order, Incremental repeats them per release, Spiral adds risk analysis each loop, and Agile compresses the whole cycle into a 1–4 week sprint.

12. **Which SDLC do you prefer between Agile and waterfall model explain with example.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 522 (ET: MIST)]*

    Answer: Preferred model: `Agile`, for most modern projects — with the exception noted at the end.

    Why Agile is preferred
    ```
       1. WORKING SOFTWARE EVERY 1-4 WEEKS, not once at the end.
       2. REQUIREMENTS MAY CHANGE - the backlog is re-prioritised each
          sprint instead of being frozen.
       3. DEFECTS ARE FOUND EARLY, where they are cheap :

            error found in requirements   cost 1
            error found after release     cost 100+

       4. THE CUSTOMER IS PRESENT throughout, so what is built is what
          is wanted.
       5. RISK SURFACES EARLY, at each sprint review.
    ```

    Example — an online food-delivery application

    Under Waterfall
    ```
       Month 1-2   gather every requirement , freeze the SRS
       Month 3-4   design the whole system
       Month 5-8   code everything
       Month 9     test everything
       Month 10    deliver

       Now the customer says : "customers want LIVE TRACKING of the
       rider, and we must add bKash payment."

       Neither was in the frozen SRS. Adding them means reopening the
       design, so it is a formal change request costing months. And the
       customer sees the product for the FIRST TIME in month 10.
    ```

    Under Agile
    ```
       Sprint 1 (2 wks) : browse restaurants and menu      -> DELIVERED
       Sprint 2         : cart and order placement         -> DELIVERED
       Sprint 3         : payment - and bKash is added here, because
                          by now the need is known
       Sprint 4         : live rider tracking - added to the backlog
                          the moment the customer asks
       Sprint 5         : ratings and reviews

       The customer uses the app from week 2 and steers the product.
       The two new requirements cost ONE SPRINT EACH, not a contract
       amendment.
    ```

    Comparison

    | Point | Waterfall | Agile |
    |---|---|---|
    | Delivery | Once, at the end | Every `1–4 weeks` |
    | Requirements | `Frozen` | Evolve each sprint |
    | Cost of change | `Very high` | Low |
    | Customer contact | Start and end | `Continuous` |
    | Testing | One phase at the end | Every sprint |
    | Documentation | Heavy | Light |

    Where I would choose Waterfall instead
    ```
       A GOVERNMENT PAYROLL SYSTEM implementing a published pay scale :

         the rules are FIXED and published in a gazette
         the tender demands a complete specification and a firm price
         full documentation is required for audit
         the requirement will not change during the project

       Here Waterfall is genuinely BETTER - Agile's evolving scope
       cannot be priced in a fixed-price public tender.
    ```
    - The practical middle path most large organisations use is a `hybrid`: Waterfall-style planning, architecture and contract up front, then Agile sprints for the build. Banks and government projects in Bangladesh usually work this way rather than adopting either model in its pure form.

13. **Define SDLC? Write the steps of SDLC?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

    Answer: Definition
    - `SDLC` — the `Software Development Life Cycle` — is the structured process a software product goes through from the first idea to final retirement. The work is divided into ordered phases, each with a defined input, output and review, so that cost, schedule and quality stay controllable.
    - Why it is defined at all: without a life cycle, requirements are missed and defects surface late, when they cost the most.
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10
    ```

    The steps
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```
    ```
       1. PLANNING AND FEASIBILITY
            Scope, budget, schedule, team. Technical, economic,
            operational, schedule and legal feasibility are checked.
            Output : project plan , feasibility report.

       2. REQUIREMENT ANALYSIS
            Interviews, questionnaires, observation. FUNCTIONAL
            requirements (what it must do) are separated from
            NON-FUNCTIONAL ones (speed, security, availability).
            Output : SRS , signed off by the customer.

       3. DESIGN
            HIGH-LEVEL : architecture, modules, database schema.
            LOW-LEVEL  : algorithms, interfaces, screen layouts.
            Output : design document , ER diagram , DFD , UML.

       4. CODING
            Modules written against the design, following coding
            standards, under version control, with code review.
            Output : source code , unit-tested modules.

       5. TESTING
            UNIT -> INTEGRATION -> SYSTEM -> ACCEPTANCE.
            Acceptance testing is done by the CUSTOMER and is the
            formal sign-off before release.
            Output : test reports , a stable build.

       6. DEPLOYMENT
            Install, migrate data, train users, go live. Release may be
            DIRECT , PARALLEL , PILOT or PHASED.
            Output : the running system.

       7. MAINTENANCE
            CORRECTIVE (fix defects) , ADAPTIVE (new OS or law) ,
            PERFECTIVE (new features) , PREVENTIVE (restructure).
            Takes 60-80 per cent of total lifetime cost.
    ```
    - The same seven phases are arranged differently by different `models`: `Waterfall` runs them once in strict sequence, `Incremental` repeats them per release, `Spiral` adds risk analysis to each loop, and `Agile` compresses the whole cycle into a 1–4 week sprint that repeats continuously.

14. **What is SDLC? Write the name of 7 phase of SDLC?** *[DESCO Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

    Answer: What SDLC is
    - `SDLC` stands for `Software Development Life Cycle`. It is the structured process a software product follows from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality stay under control.

    The 7 phases
    ```
       1. PLANNING and feasibility study
       2. REQUIREMENT ANALYSIS
       3. DESIGN
       4. IMPLEMENTATION  (coding)
       5. TESTING
       6. DEPLOYMENT
       7. MAINTENANCE
    ```
    ```mermaid
    flowchart TD
        A[1. Planning] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Implementation]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```

    One line on each
    ```
       PLANNING       fix scope, budget, schedule, team ; check
                      technical, economic, operational and legal
                      feasibility.
       ANALYSIS       gather user needs ; produce the SRS.
       DESIGN         decide HOW - architecture, modules, database,
                      screens.
       IMPLEMENTATION write the code, module by module.
       TESTING        unit -> integration -> system -> acceptance.
       DEPLOYMENT     install, migrate data, train users, go live.
       MAINTENANCE    corrective, adaptive, perfective, preventive
                      changes after release.
    ```
    - Note that the phase count differs between books — some show `5` or `6` phases by merging planning with feasibility, or folding deployment into maintenance. The `7-phase` list above is the one usually expected when the question asks for seven.
    - Also worth one line: `maintenance` is the longest and costliest phase, taking `60 to 80 per cent` of the product's total lifetime cost — more than all six earlier phases together.

15. **(a) What do you understand by Agile? Mention its four values.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 486 (ET: N/A)]*

    Answer: What Agile is
    - `Agile` is an approach to software development in which the product is built in short, repeated cycles called `iterations` or `sprints`, each producing `working software`, with the customer involved throughout. It is not a single method but a `philosophy`, set out in the `Agile Manifesto` of 2001 by 17 practitioners.
    ```
       Instead of one long sequence :

            Backlog -> Sprint (1-4 weeks) -> Working increment
                 ^                                  |
                 +--- review + retrospective -------+

       Every sprint contains ANALYSIS, DESIGN, CODING and TESTING - a
       complete mini life cycle.
    ```

    Its four values
    ```
       1. INDIVIDUALS AND INTERACTIONS  over  processes and tools
            A motivated team that talks to each other beats a rigid
            process. A five-minute conversation settles what a week of
            emails would not.

       2. WORKING SOFTWARE  over  comprehensive documentation
            Progress is measured by software that runs, not by the
            number of documents produced. Document what is genuinely
            needed, no more.

       3. CUSTOMER COLLABORATION  over  contract negotiation
            Work WITH the customer continuously rather than arguing
            about what the signed contract says. A Product Owner sits
            with the team.

       4. RESPONDING TO CHANGE  over  following a plan
            A changed requirement is useful information, not a failure
            of planning. The backlog is re-prioritised each sprint.
    ```
    ```
       THE CRUCIAL QUALIFICATION, and the one candidates miss :

       "That is, while there is value in the items on the RIGHT, we
        value the items on the LEFT MORE."

       Agile does NOT say documentation, plans, tools or contracts are
       worthless. It says that when the two conflict, the left-hand
       item wins.
    ```

    The twelve principles, in brief
    - Satisfy the customer through `early and continuous delivery`; welcome changing requirements even late; deliver working software `frequently`; business people and developers work together `daily`; build around `motivated individuals`; prefer `face-to-face` conversation; `working software` is the primary measure of progress; maintain a `sustainable pace`; attend continuously to `technical excellence`; keep it `simple`; the best designs come from `self-organising teams`; and the team `reflects and adjusts` at regular intervals.

    - The frameworks that implement Agile: `Scrum` (sprints, Product Owner, Scrum Master, daily stand-up), `Kanban` (visualise the work, limit work in progress), `Extreme Programming` (pair programming, test-driven development, continuous integration) and `SAFe` for large organisations. Agile is the philosophy; these are the methods that put it into practice.

16. **(a) Write down the steps of Waterfall model.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

    Answer: The `Waterfall model` is the classical `linear sequential` model of software development. Each phase must be finished and approved before the next begins, and the output of one phase is the input to the next — so progress flows steadily downward, like a waterfall.

    The steps
    ```mermaid
    flowchart TD
        A[1. Requirement gathering and analysis] --> B[2. System design]
        B --> C[3. Implementation / coding]
        C --> D[4. Integration and testing]
        D --> E[5. Deployment]
        E --> F[6. Maintenance]
    ```
    ```
       +-------------------------+
       | 1. REQUIREMENTS         |
       +-------------------------+
                  |
                  v
           +-------------------------+
           | 2. SYSTEM DESIGN        |
           +-------------------------+
                      |
                      v
               +-------------------------+
               | 3. IMPLEMENTATION       |
               +-------------------------+
                          |
                          v
                   +-------------------------+
                   | 4. TESTING              |
                   +-------------------------+
                              |
                              v
                       +-------------------------+
                       | 5. DEPLOYMENT           |
                       +-------------------------+
                                  |
                                  v
                           +-------------------------+
                           | 6. MAINTENANCE          |
                           +-------------------------+
    ```

    1. Requirement gathering and analysis
    - Collect every requirement from the customer and record it. The `SRS` is produced and formally signed off. Nothing may change afterwards.

    2. System design
    - `High-level design` fixes the architecture, the modules and the database schema; `low-level design` fixes each module's algorithms, interfaces and screens.

    3. Implementation — coding
    - The design is translated into code, module by module, and each module is unit tested by its developer.

    4. Integration and testing
    - The modules are combined and the whole system is tested against the SRS — integration, system and finally acceptance testing by the customer.

    5. Deployment
    - The product is installed in the customer's environment, data is migrated and users are trained.

    6. Maintenance
    - Defects found in use are corrected, and the system is adapted or enhanced over its working life.

    Advantages
    - `Simple to understand and manage`; each phase has a clear deliverable and a review point.
    - `Well documented`, which suits contracts, audits and later maintenance.
    - `Easy to plan and cost`, because the scope is fixed at the start.
    - Works well when requirements are `fixed and fully understood`.

    Disadvantages
    - Requirements must be `frozen` early, which real customers cannot do.
    - `No working software until very late` — the customer sees the product only at testing.
    - `Change is very expensive`; there is no formal route back to an earlier phase.
    - `Risk is discovered late`, in the testing phase, when correction costs the most.
    - Poor for long projects, where the business changes while the project runs.

    - Where it is still the right model: fixed, published rules — a payroll system implementing a gazetted pay scale; contracts or regulators demanding a full specification up front; safety-critical systems needing formal review at every stage; and small, short projects where iteration would cost more than it saves.

17. **(খ) Software Engineering এর ক্ষেত্রে Waterfall Model বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What the Waterfall model is
    - The `Waterfall model` is the classical `linear sequential` model of software development, proposed by Winston Royce in 1970. Each phase must be completed and approved before the next begins, and the output of one phase becomes the input to the next — progress flows downward like a waterfall, with no formal way back.

    The phases
    ```mermaid
    flowchart TD
        A[1. Requirement analysis] --> B[2. System design]
        B --> C[3. Implementation]
        C --> D[4. Testing]
        D --> E[5. Deployment]
        E --> F[6. Maintenance]
    ```
    ```
       1. REQUIREMENT GATHERING AND ANALYSIS
            Every requirement is collected and recorded. The SRS is
            produced and formally SIGNED OFF - and then FROZEN.

       2. SYSTEM DESIGN
            HIGH-LEVEL : architecture, modules, database schema.
            LOW-LEVEL  : algorithms, interfaces, screen layouts.

       3. IMPLEMENTATION (CODING)
            The design is turned into code, module by module. Each
            module is unit tested by its developer.

       4. INTEGRATION AND TESTING
            Modules are combined ; the whole system is tested against
            the SRS - integration, system, then acceptance testing by
            the customer.

       5. DEPLOYMENT
            Installed at the customer's site, data migrated, users
            trained, system goes live.

       6. MAINTENANCE
            Defects corrected, and the system adapted or enhanced over
            its working life.
    ```

    Advantages
    - `Simple to understand and to manage` — every phase has a clear deliverable and a review gate.
    - `Thoroughly documented`, which suits contracts, audits and future maintenance.
    - `Easy to estimate and cost`, since the scope is fixed at the start.
    - Discipline is enforced: nothing is coded before the design is approved.
    - Works well when the requirements are `fixed and completely understood`.

    Limitations
    - Requirements must be `frozen` after analysis. Real customers discover what they want only when they see something working.
    - `No working software until the end` — the customer sees the product for the first time at testing.
    - `Change is extremely expensive`; there is no formal path back to an earlier phase.
    - `Risk surfaces late`. An integration problem or a missed performance target appears only in the testing phase.
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall finds requirement errors LATE - at the expensive end.
    ```
    - Poor for long projects, where the business changes underneath the project while it runs.
    - Testing is a single phase at the end, so defects accumulate and arrive in one crushing batch.

    - Where it is still correct to use: fixed, published rules such as a government pay scale; tenders that demand a complete specification and a firm price; safety-critical systems requiring formal review at every stage; and small, short projects where iteration costs more than it saves. For everything else, `Incremental`, `Spiral` or `Agile` models address Waterfall's central weakness — `feedback that arrives too late to act on`.

18. **(খ) Software maintenance এর সাথে কী কী বিষয় জড়িত, তা আলোচনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What software maintenance is
    - `Software maintenance` is all the work done on a software product `after it has been delivered` — correcting faults, adapting it to a changed environment, improving it, and keeping it fit to run. It is not an afterthought: it consumes `60 to 80 per cent` of a product's total lifetime cost, more than all the development phases combined.

    What maintenance involves — the four types
    ```
       1. CORRECTIVE MAINTENANCE   (about 20 %)
            Fixing defects found once the system is in use - a wrong
            calculation, a crash, a report that prints the wrong total.
            REACTIVE : it responds to a reported fault.

       2. ADAPTIVE MAINTENANCE     (about 25 %)
            Changing the software because its ENVIRONMENT changed, not
            because it is faulty :
              a new operating system or browser version
              a database upgrade
              a change in tax law or a new VAT rate
              a new hardware platform

       3. PERFECTIVE MAINTENANCE   (about 50 %)
            Adding features and improving performance or usability at
            the users' request. THE LARGEST SHARE - because a system in
            use keeps attracting new demands.

       4. PREVENTIVE MAINTENANCE   (about  5 %)
            Restructuring the code to stop future problems -
            refactoring, removing duplication, updating documentation,
            replacing an obsolete library. It fixes nothing visible
            today ; it lowers tomorrow's cost.
    ```

    The activities involved
    ```
       - understanding the existing code, often written by others
       - impact analysis - what else breaks if this is changed
       - modifying the code and the design
       - REGRESSION TESTING - proving the change broke nothing else
       - updating the SRS, the design document and the user manual
       - version and configuration management
       - re-deploying and retraining users
       - a CHANGE CONTROL process : request -> analyse -> approve ->
         implement -> test -> release
    ```

    Why maintenance is difficult and costly
    - The original developers have usually `left`, and the knowledge went with them.
    - `Documentation is out of date` or missing, so the code must be read to understand the system.
    - Years of patches leave the structure degraded — `software ageing`. Each change makes the next one harder.
    - A change in one module can `break another` in a way nobody predicted.
    - Maintenance is seen as low-prestige work, so it often gets the least experienced staff — which makes the problem worse.

    How maintenance cost is reduced
    ```
       During DEVELOPMENT :
            high COHESION and low COUPLING , so a change stays local
            clear coding standards and meaningful names
            good documentation kept with the code
            an automated test suite , so regressions are caught at once

       During MAINTENANCE :
            REFACTOR regularly instead of patching
            keep the documentation in step with the code
            use version control and a formal change process
    ```
    - Two related terms worth naming: `re-engineering` — rebuilding an old system into a better structure while keeping its function — and `reverse engineering`, recovering the design from code when the documentation is lost. Both are used when a legacy system has become too costly to maintain by ordinary means.

19. **(ক) Waterfall model বিস্তারিত বর্ণনা করুন। এই model এর সুবিধা এবং সীমাবদ্ধতাগুলো উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The Waterfall model in detail
    - The `Waterfall model` is the classical `linear sequential` model, proposed by Winston Royce in 1970. Every phase is completed and formally approved before the next begins, and the output of one phase is the input to the next. Progress flows downward only — hence the name.

    The phases
    ```mermaid
    flowchart TD
        A[1. Requirement gathering and analysis] --> B[2. System design]
        B --> C[3. Implementation]
        C --> D[4. Integration and testing]
        D --> E[5. Deployment]
        E --> F[6. Maintenance]
    ```
    ```
       1. REQUIREMENT GATHERING AND ANALYSIS
            All requirements are collected from the customer through
            interviews, questionnaires and study of existing documents.
            FUNCTIONAL requirements (what the system must do) are
            separated from NON-FUNCTIONAL ones (speed, security,
            availability).
            Output : SRS - Software Requirements Specification, signed
            off by the customer and then FROZEN.

       2. SYSTEM DESIGN
            HIGH-LEVEL DESIGN : overall architecture, module breakdown,
                 database schema, technology choices.
            LOW-LEVEL DESIGN  : each module's algorithms, data
                 structures, interfaces and screen layouts.
            Output : design document, ER diagram, DFD, UML diagrams.

       3. IMPLEMENTATION (CODING)
            Programmers translate the design into code, module by
            module, following the coding standards. Each module is
            UNIT TESTED by its own developer.
            Output : source code.

       4. INTEGRATION AND TESTING
            Modules are combined and tested together, then the whole
            system is tested against the SRS.
            INTEGRATION -> SYSTEM -> ACCEPTANCE testing (by the
            customer).
            Output : test reports, a stable build.

       5. DEPLOYMENT
            The product is installed in the customer's environment,
            data is migrated, users are trained, the system goes live.

       6. MAINTENANCE
            Corrective, adaptive, perfective and preventive changes
            over the working life of the system.
    ```

    Advantages
    - `Simple to understand and manage` — clear phases, clear deliverables, a review gate at each boundary.
    - `Well documented`, which suits contracts, audits and later maintenance by other people.
    - `Easy to estimate and price`, since the scope is fixed at the start. This is why public tenders often demand it.
    - Discipline is enforced — nothing is coded before the design is approved.
    - Works well when the requirements are `fixed and completely understood`.
    - Progress is easy to report — the phase currently under way is the status.

    Limitations
    - Requirements must be `frozen` after analysis, but customers discover what they want only when they see something working.
    - `No working software until very late`; the customer first sees the product at testing.
    - `Change is extremely expensive` — there is no formal route back to a finished phase.
    - `Risk surfaces late`. An integration failure or a missed performance target appears only in testing.
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall finds requirement errors at the EXPENSIVE end.
    ```
    - `Unsuitable for long projects`, because the business changes while the project runs — the product can match the SRS exactly and still be useless.
    - `Testing is one phase at the end`, so defects accumulate and arrive together.
    - The customer is idle through the middle of the project and cannot influence the product.

    - Where it remains the right choice: fixed, published rules such as a gazetted pay scale; contracts or regulators demanding a complete specification and firm price; safety-critical systems requiring formal review at every stage; and small, short projects. For everything else the `Incremental`, `Spiral` and `Agile` models exist precisely to fix Waterfall's central defect — `feedback that arrives too late to act on`.

20. **How does agile methodology used in software development differ from that of waterfall methodology? Explain in brief.** *[BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

    Answer: How Agile differs from Waterfall

    | Point | Waterfall | Agile |
    |---|---|---|
    | Approach | `Sequential` — one phase after another | `Iterative` and incremental |
    | Requirements | `Frozen` after analysis | A `living backlog`, re-prioritised each sprint |
    | Delivery | `Once`, at the very end | Working software every `1–4 weeks` |
    | Customer involvement | Start and end only | `Continuous` — a Product Owner in the team |
    | Testing | A single phase `at the end` | `Inside every sprint` |
    | Cost of change | `Very high` | `Low` |
    | Documentation | Heavy and formal | Light — "just enough" |
    | Team | Specialised, hierarchical | `Cross-functional`, self-organising |
    | Risk discovery | `Late`, in testing | `Early`, at each sprint review |
    | Progress measured by | Documents and phases completed | `Working software` |

    The structural difference
    ```mermaid
    flowchart LR
        subgraph Waterfall
        A[Requirements] --> B[Design] --> C[Code] --> D[Test] --> E[Deploy]
        end
        subgraph Agile
        F[Backlog] --> G[Sprint 1-4 weeks] --> H[Working increment]
        H --> I[Review] --> F
        end
    ```
    ```
       WATERFALL does each phase ONCE, for the WHOLE product.
       AGILE does ALL the phases EVERY SPRINT, for a SMALL SLICE of
       the product.

       That single structural change is the source of every other
       difference between them.
    ```

    Why it matters in practice
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall tests ONCE, at the end - the most expensive point.
       Agile tests CONTINUOUSLY, so errors are caught while cheap.
    ```

    The Agile values that drive it
    ```
       Individuals and interactions  over  processes and tools
       Working software              over  comprehensive documentation
       Customer collaboration        over  contract negotiation
       Responding to change          over  following a plan

       The right-hand items still have value ; the left-hand ones have
       MORE. Agile does not discard documentation or planning.
    ```

    - Where each one wins: `Waterfall` for fixed, published requirements, fixed-price tenders, and safety-critical or heavily regulated systems. `Agile` where requirements are unclear or changing, the customer can stay involved, and early delivery matters. Large organisations usually run a `hybrid` — Waterfall planning and contract up front, Agile sprints for the build.

21. **Software engineering এ ফিজিবিলিটি স্ট্যাড্যির ৭টি ধাপ বর্ণনা কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) A `feasibility study` decides whether a proposed software project is `worth doing` before any money is committed to it. It is carried out in the planning phase and ends in a recommendation: proceed, revise the scope, or abandon.

    The seven steps
    ```
       1. INFORMATION ASSESSMENT
            Understand the problem and the proposed system. What is
            wrong with the present arrangement, what should the new
            system do, who will use it, what are the constraints of
            budget, time and law.

       2. INFORMATION COLLECTION
            Gather the facts - interviews with users and managers,
            questionnaires, observation of the current process, study
            of existing documents and reports, and a look at similar
            systems elsewhere.

       3. REPORT WRITING - the preliminary report
            Write down the findings so far : the problem statement, the
            objectives, the scope and the alternatives being considered.

       4. GENERAL INFORMATION / PROPOSAL FORMULATION
            Draw up two or three ALTERNATIVE solutions - build in-house,
            buy a package, outsource, or upgrade the existing system.
            Each alternative is described with its technology, cost and
            timeline.

       5. FEASIBILITY ANALYSIS
            Test each alternative against the five kinds of feasibility :

              TECHNICAL   - do we have the technology and the skills ?
              ECONOMIC    - do the benefits exceed the costs ?
                            (cost-benefit analysis, ROI, payback period)
              OPERATIONAL - will the users actually accept and use it ?
              SCHEDULE    - can it be delivered in the time available ?
              LEGAL       - does it comply with law, licences and
                            data-protection rules ?

       6. EVALUATION AND COMPARISON
            Score the alternatives against these criteria, weigh the
            risks and choose the best option. Cost-benefit analysis is
            the main tool here.

       7. FINAL REPORT AND RECOMMENDATION
            Produce the FEASIBILITY REPORT : findings, the chosen
            alternative, its costs and benefits, the risks and their
            mitigation, and a clear recommendation. Management then
            decides :
                 GO       - proceed to full development
                 REVISE   - adjust scope, budget or timeline first
                 NO GO    - abandon, and consider other options
    ```

    Flow
    ```mermaid
    flowchart TD
        A[1. Information assessment] --> B[2. Information collection]
        B --> C[3. Preliminary report]
        C --> D[4. Formulate alternatives]
        D --> E[5. Feasibility analysis]
        E --> F[6. Evaluate and compare]
        F --> G[7. Final report and decision]
    ```

    - Why it matters: the feasibility study is the cheapest point at which a bad project can be stopped. Cancelling at this stage costs a few weeks of analysis; discovering the same problem after deployment costs the entire project budget.
    - Note that the number of steps varies between textbooks — some list five, some eight — because the reporting steps are sometimes merged. The `five kinds of feasibility` in step 5, however, are standard and are what examiners look for.

22. **Explain software development life cycle (SDLC).** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*

    Answer: The `Software Development Life Cycle (SDLC)` is the structured process a software product follows from the first idea to final retirement. The work is divided into ordered phases, each with a defined input, output and review, so that cost, schedule and quality remain controllable.

    Why it exists
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       A defined life cycle catches errors at the CHEAP end. That is
       its entire justification.
    ```

    The phases
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```
    ```
       1. PLANNING AND FEASIBILITY
            Scope, budget, schedule, team. Technical, economic,
            operational, schedule and legal feasibility are tested. The
            project can still be stopped here, cheaply.
            Output : project plan , feasibility report.

       2. REQUIREMENT ANALYSIS
            Interviews, questionnaires, observation. FUNCTIONAL
            requirements are separated from NON-FUNCTIONAL ones.
            Output : SRS , signed off by the customer.

       3. DESIGN
            HIGH-LEVEL : architecture, modules, database schema.
            LOW-LEVEL  : algorithms, interfaces, screens.
            Output : design document , ER diagram , DFD , UML.

       4. CODING
            Modules written against the design, following coding
            standards, under version control, with code review.
            Output : source code , unit-tested modules.

       5. TESTING
            UNIT -> INTEGRATION -> SYSTEM -> ACCEPTANCE.
            Acceptance testing is done by the CUSTOMER and is the
            formal sign-off before release.

       6. DEPLOYMENT
            Install, migrate data, train users, go live. Release may be
            DIRECT , PARALLEL , PILOT or PHASED.

       7. MAINTENANCE
            CORRECTIVE , ADAPTIVE , PERFECTIVE and PREVENTIVE changes.
            60-80 per cent of total lifetime cost.
    ```

    The models — the same phases, arranged differently
    ```
       WATERFALL    each phase once, in strict order. Simple, heavily
            documented, but requirements are frozen and feedback comes
            far too late.

       ITERATIVE / INCREMENTAL
            the cycle is repeated per release, so working software is
            delivered early and feedback shapes the next increment.

       SPIRAL       each loop adds explicit RISK ANALYSIS and a
            prototype. Used for large, costly, uncertain systems.

       PROTOTYPE    a throwaway model is built first to pin down
            unclear requirements, then the real system is built.

       V-MODEL      each development phase is paired with its
            corresponding TEST level, so testing is planned from the
            start.

       AGILE        the whole cycle is compressed into a 1-4 week
            sprint and repeated continuously, with the customer
            present throughout.
    ```
    - Which to choose depends on one question: `how well are the requirements known`. Fixed and published — Waterfall. Unclear or changing — Agile or Incremental. Large and risky — Spiral.

23. **(b) What is SDLC? Define the activities of the design phase in SDLC.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

    Answer: What SDLC is
    - `SDLC` — the `Software Development Life Cycle` — is the structured process a software product follows from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality stay under control.
    ```
       Planning -> Requirement analysis -> DESIGN -> Coding -> Testing
                -> Deployment -> Maintenance
    ```

    Activities of the design phase
    - The design phase answers `how` the system will be built, using the `SRS` from the analysis phase as its input. It is split into two levels.

    (a) High-level design — architectural design
    ```
       - choose the overall ARCHITECTURE : layered , client-server ,
         MVC , microservices
       - decompose the system into MODULES and fix what each one does
       - define the INTERFACES between modules - what each module
         exposes and what it needs
       - design the DATABASE : entities, attributes, relationships,
         normalisation, keys and indexes  -> ER DIAGRAM
       - model the data flow                -> DFD
       - choose the technology stack : language, framework, database,
         platform
       - decide how NON-FUNCTIONAL requirements are met - performance,
         security, availability, backup
    ```

    (b) Low-level design — detailed design
    ```
       - design the ALGORITHM and logic inside each module
         (flowchart , pseudocode)
       - choose the DATA STRUCTURES
       - fix the exact function signatures and parameters
       - design the SCREENS and reports - the user interface layout
       - design INPUT VALIDATION and error handling
       - specify file formats and report layouts
    ```

    Other activities that belong to the phase
    ```
       - design for TESTABILITY , and prepare the TEST PLAN so that
         test design runs alongside the design itself (the V-model
         makes this explicit)
       - a DESIGN REVIEW or walkthrough with the team and the customer
       - a TRACEABILITY MATRIX proving every SRS requirement is
         covered by some design element
       - produce the SDD - Software Design Document
    ```

    The principles the design must follow
    ```
       MODULARITY      break the system into independent pieces
       ABSTRACTION     hide the detail behind an interface
       HIGH COHESION   each module does ONE well-defined job
       LOW COUPLING    modules depend on each other as little as
                       possible, so a change stays local
       INFORMATION HIDING  internal data is not exposed
       REUSABILITY     design components that can be used again
    ```
    ```mermaid
    flowchart TD
        A[SRS from analysis] --> B[High-level design: architecture, modules, database]
        B --> C[Low-level design: algorithms, interfaces, screens]
        C --> D[Design review and SDD]
        D --> E[Coding phase]
    ```
    - Outputs of the phase: the `Software Design Document (SDD)`, ER diagrams, DFDs, UML diagrams (class, sequence, use case), the database schema, interface specifications and the test plan.
    - Why this phase carries such weight: a design error is `five times` costlier to fix than a requirement error and `ten times` costlier once it has been coded. `Low coupling and high cohesion`, decided here, are what determine how expensive the system will be to maintain for the rest of its life.

24. **(ক) Software development এর Agile পদ্ধতির মূলনীতিগুলো লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 706 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The `Agile Manifesto` (2001) states four `values` and twelve `principles`. The principles are the working rules that follow from the values.

    The four values
    ```
       Individuals and interactions  over  processes and tools
       Working software              over  comprehensive documentation
       Customer collaboration        over  contract negotiation
       Responding to change          over  following a plan

       The right-hand items still have value ; the left-hand ones have
       MORE. Agile does not discard documentation, plans or contracts.
    ```

    The twelve principles
    ```
       1. Satisfy the customer through EARLY and CONTINUOUS DELIVERY of
          valuable software.

       2. WELCOME CHANGING REQUIREMENTS, even late in development.
          Change is treated as a competitive advantage, not a failure
          of planning.

       3. DELIVER WORKING SOFTWARE FREQUENTLY - every couple of weeks
          to a couple of months, preferring the shorter interval.

       4. Business people and developers must WORK TOGETHER DAILY
          throughout the project.

       5. Build projects around MOTIVATED INDIVIDUALS. Give them the
          environment and support they need, and TRUST them to get the
          job done.

       6. FACE-TO-FACE CONVERSATION is the most efficient way of
          conveying information within a team.

       7. WORKING SOFTWARE is the primary measure of progress - not
          documents produced or phases completed.

       8. Promote SUSTAINABLE DEVELOPMENT. The team should be able to
          keep up the same pace indefinitely - no crunch, no burnout.

       9. Continuous attention to TECHNICAL EXCELLENCE and good design
          enhances agility. Poor code slows every future sprint.

      10. SIMPLICITY - maximising the work NOT done - is essential.
          Build what is needed now, not what might be needed later.

      11. The best architectures, requirements and designs emerge from
          SELF-ORGANISING TEAMS, not from a plan imposed from above.

      12. At regular intervals the team REFLECTS on how to become more
          effective, and ADJUSTS its behaviour accordingly - the
          RETROSPECTIVE.
    ```

    How they work in practice
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint: 1-4 weeks]
        C --> D[Working increment]
        D --> E[Review + Retrospective]
        E --> A
    ```
    ```
       Principle 1 and 3  -> deliver an increment every sprint
       Principle 2        -> re-prioritise the backlog each sprint
       Principle 4 and 6  -> the daily stand-up , and a Product Owner
                             sitting with the team
       Principle 7        -> the sprint review demonstrates RUNNING
                             SOFTWARE, not slides
       Principle 12       -> the retrospective at the end of each sprint
    ```
    - The frameworks built on these principles: `Scrum` (sprints, Product Owner, Scrum Master, daily stand-up), `Kanban` (visualise the work, limit work in progress), `Extreme Programming` (pair programming, TDD, continuous integration) and `SAFe` for large organisations.

25. **(খ) Software development এর Waterfall model এর অসুবিধাগুলো কী কী?** *[Software Assistant Programmer 13.10.2022 compact it 706 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Disadvantages of the Waterfall model

    1. Requirements must be frozen at the start
    - The model assumes the customer can state every requirement completely and correctly before any design begins. In practice users discover what they want only when they `see` something working.

    2. No working software until very late
    - The customer sees nothing until the testing phase, often months later. If the product is wrong, the whole effort is already spent.

    3. Change is extremely expensive
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall finds requirement errors LATE - exactly where they
       cost the most.
    ```

    4. No way back to an earlier phase
    - Each phase must be finished and signed off before the next begins. There is no formal route back, so an error made in analysis is carried through the entire project.

    5. Risk is discovered late
    - Technical risks — an integration that will not work, a performance target that cannot be met — surface only during testing, when correction is most costly.

    6. Testing happens only at the end
    - Defects accumulate through the whole project and arrive together in one crushing batch, which makes the schedule at the end of a Waterfall project notoriously unreliable.

    7. Poor for long projects
    - The longer the project runs, the more the business changes underneath it. A two-year project can deliver exactly what the SRS said and still be useless on the day it goes live.

    8. The customer is idle in the middle
    - After signing the SRS the customer has no involvement until acceptance testing, so there is no chance to correct a misunderstanding.

    9. Progress is measured by documents
    - A project can look healthy — every document delivered on time — while the product itself is in trouble.

    10. Not suited to unclear or research-type work
    - If the requirements cannot be known in advance, the model's first phase cannot even be completed.

    Where Waterfall is still correct
    ```
       requirements FIXED and published - a payroll system implementing
            a gazetted pay scale
       a TENDER demanding a full specification and a firm price
       SAFETY-CRITICAL systems needing formal review at every stage
       SMALL, SHORT projects where iteration costs more than it saves
    ```
    - The models that answer these weaknesses: `Incremental` and `Agile` deliver working software early so feedback arrives while it is still cheap; `Spiral` adds explicit risk analysis to each loop; and the `V-model` pairs each development phase with its test level, so testing is planned from the very beginning rather than left to the end.

26. **(খ) System/Model Prototype বলতে কী বুঝায়? Product ও Process এর মধ্যে সম্পর্ক কী?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What a prototype is
    - A `prototype` is a working but incomplete model of a system, built quickly so users can `see and use` it before the real system is developed. Its purpose is to settle unclear requirements — users can rarely describe what they want, but they can always react to something in front of them.
    ```mermaid
    flowchart LR
        A[Gather rough requirements] --> B[Build a quick prototype]
        B --> C[Customer evaluates it]
        C --> D{Satisfied?}
        D -->|No| E[Refine requirements] --> B
        D -->|Yes| F[Build the real system]
    ```
    ```
       The cycle : build -> show -> get feedback -> refine -> repeat
       until the requirements are clear, THEN build the real product.
    ```

    Types of prototype
    ```
       THROWAWAY (rapid) prototype
            Built only to clarify requirements, then DISCARDED. The
            real system is built properly from scratch.

       EVOLUTIONARY prototype
            Refined again and again until it BECOMES the final product.

       INCREMENTAL prototype
            Separate prototypes for separate modules, later combined.

       EXTREME prototype - for web work : a static UI first, then the
            services behind it, then the real logic.
    ```
    - Advantages: misunderstandings are caught `early`, the user is involved from the start, and missing requirements are discovered before coding begins.
    - Disadvantages: users may mistake the prototype for a finished product; the quick-and-dirty code invites poor structure if it is kept; and the cycle can run on indefinitely if nobody stops it.

    The relation between product and process
    ```
       PROCESS  =  HOW the software is built - the set of activities,
                   their order and the standards followed.
                   SDLC , Waterfall , Agile , Scrum , code review ,
                   testing procedure.

       PRODUCT  =  WHAT is produced - the software itself, together
                   with its SRS, design documents, source code, test
                   reports and user manual.
    ```
    ```
       PROCESS  ------ produces ------>  PRODUCT
          ^                                 |
          |                                 |
          +------- feedback improves -------+
            (defect data, review findings,
             retrospectives)
    ```

    The relationship, stated plainly
    ```
       1. PRODUCT QUALITY DEPENDS ON PROCESS QUALITY.
            A disciplined process - reviews, standards, testing -
            produces a better product. A chaotic process produces a
            defective one, however skilled the individuals are.

       2. THE PRODUCT MEASURES THE PROCESS.
            Defect density, rework and delivery delay are the evidence
            used to judge whether the process is working.

       3. FEEDBACK RUNS BOTH WAYS.
            Defects found in the product lead to process improvement -
            this is exactly what an Agile RETROSPECTIVE does.

       4. THE PROCESS MUST SUIT THE PRODUCT.
            A safety-critical product needs a heavy, formal process ;
            a small web application does not. Using the wrong process
            for the product damages both.
    ```
    - This is the idea behind `CMM` and `CMMI`, which rate an organisation's process maturity from level 1 (chaotic) to level 5 (continuously improving), on the premise that `a mature process yields a predictable product`. The important qualification: a good process makes a good product `likely`, not certain — a disciplined team building the wrong thing still fails.

27. **What is full meaning of SDLC?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

    Answer: `SDLC` stands for `Software Development Life Cycle`.
    - It is the structured process a software product follows from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality stay under control.
    ```
       The phases :

         1. Planning and feasibility study
         2. Requirement analysis
         3. Design
         4. Implementation (coding)
         5. Testing
         6. Deployment
         7. Maintenance
    ```
    - Some books also expand the abbreviation as `System Development Life Cycle`, which is the same idea applied to a whole information system rather than to software alone.

28. **Difference between Waterfall Model and Spiral Model.** *[BDCCL Assistant Engineer (Network) 2022 compact it 741 (ET: N/A)]*

    Answer: Difference between the Waterfall model and the Spiral model

    | Point | Waterfall model | Spiral model |
    |---|---|---|
    | Approach | `Linear sequential` — each phase once | `Iterative` — the cycle repeats in loops |
    | Risk handling | `None` explicitly | `Risk analysis in every loop` — its defining feature |
    | Requirements | `Frozen` after analysis | Refined at each loop |
    | Customer involvement | Start and end only | `After every loop`, at the review |
    | Prototypes | Not used | `Built in each loop` to resolve risk |
    | Cost | `Low` overhead | `High` — repeated analysis and prototyping |
    | Suited to | Small projects, fixed requirements | `Large, costly, high-risk` projects |
    | Documentation | Heavy and formal | Heavy, plus risk reports |
    | Change | Very expensive | Absorbed in the next loop |
    | Number of phases | Fixed | `Not fixed` — loops continue until done |
    | Proposed by | Winston Royce, 1970 | Barry Boehm, 1986 |

    Waterfall
    ```mermaid
    flowchart TD
        A[Requirements] --> B[Design] --> C[Coding] --> D[Testing] --> E[Deployment] --> F[Maintenance]
    ```
    ```
       One pass, top to bottom. No formal way back.
    ```

    Spiral — four quadrants per loop
    ```
       +---------------+------------------+
       |  1. DETERMINE |  2. IDENTIFY AND |
       |   OBJECTIVES  |   RESOLVE RISKS  |
       |               |   (prototype)    |
       +---------------+------------------+
       |  4. PLAN the  |  3. DEVELOP AND  |
       |  next loop    |     VERIFY       |
       +---------------+------------------+

       cost and progress increase OUTWARD with each loop :
         loop 1 concept -> loop 2 requirements -> loop 3 design
         -> loop 4 build and test
    ```
    ```mermaid
    flowchart LR
        A[Objectives] --> B[Risk analysis + prototype]
        B --> C[Develop and verify]
        C --> D[Plan next loop]
        D --> A
    ```

    The essential difference
    ```
       WATERFALL is DOCUMENT-DRIVEN : the next phase begins when the
            previous document is approved. Risk is not addressed at
            all, so it appears in testing - the most expensive place.

       SPIRAL is RISK-DRIVEN : what to do next is decided by asking
            WHICH RISK IS LARGEST. A prototype or benchmark settles it
            before real money is spent, and a doomed project can be
            STOPPED at a loop review.
    ```
    - Where each is used: `Waterfall` for small projects with fixed, published requirements and a fixed-price contract. `Spiral` for large, long, expensive systems where the risk of failure is itself the main problem — defence, aerospace, core banking. Its cost makes it wrong for anything small.

29. **What is the principles of agile method?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 757 (ET: N/A)]*

    Answer: The `Agile Manifesto` (2001) lists twelve principles, which follow from its four values.

    The twelve principles
    ```
       1. Satisfy the customer through EARLY and CONTINUOUS DELIVERY of
          valuable software.

       2. WELCOME CHANGING REQUIREMENTS, even late in development.
          Change is a competitive advantage, not a planning failure.

       3. DELIVER WORKING SOFTWARE FREQUENTLY - every couple of weeks
          to a couple of months, preferring the shorter interval.

       4. Business people and developers must WORK TOGETHER DAILY.

       5. Build projects around MOTIVATED INDIVIDUALS. Give them the
          environment and support they need, and TRUST them.

       6. FACE-TO-FACE CONVERSATION is the most efficient way to convey
          information within a team.

       7. WORKING SOFTWARE is the primary measure of progress - not
          documents written or phases completed.

       8. Promote SUSTAINABLE DEVELOPMENT - a pace the team can keep up
          indefinitely. No crunch, no burnout.

       9. Continuous attention to TECHNICAL EXCELLENCE and good design
          enhances agility. Poor code slows every future sprint.

      10. SIMPLICITY - maximising the work NOT done - is essential.

      11. The best architectures, requirements and designs emerge from
          SELF-ORGANISING TEAMS.

      12. At regular intervals the team REFLECTS on how to become more
          effective and ADJUSTS accordingly - the RETROSPECTIVE.
    ```

    The four values they rest on
    ```
       Individuals and interactions  over  processes and tools
       Working software              over  comprehensive documentation
       Customer collaboration        over  contract negotiation
       Responding to change          over  following a plan

       The right-hand items still have value ; the left-hand ones have
       MORE.
    ```

    How they appear in practice
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint: 1-4 weeks]
        C --> D[Working increment]
        D --> E[Review + Retrospective]
        E --> A
    ```
    ```
       Principles 1 and 3 -> an increment delivered every sprint
       Principle  2       -> the backlog is re-prioritised each sprint
       Principles 4 and 6 -> the daily stand-up ; a Product Owner
                             sitting with the team
       Principle  7       -> the sprint review demonstrates RUNNING
                             SOFTWARE, not slides
       Principle  9       -> TDD , code review , continuous integration
       Principle 12       -> the retrospective at the end of each sprint
    ```
    - The frameworks that implement these principles are `Scrum`, `Kanban`, `Extreme Programming (XP)` and `SAFe`. Agile is the philosophy; those are the methods.

30. **From the diagram write down the process of prototype development.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 758 (ET: N/A)]*

    Answer: The question refers to a diagram that was not captured with it, so the standard `prototype model` process is described. Any diagram of this model shows the same cycle.

    The process
    ```mermaid
    flowchart TD
        A[1. Requirement gathering - rough] --> B[2. Quick design]
        B --> C[3. Build the prototype]
        C --> D[4. Customer evaluation]
        D --> E{Satisfied?}
        E -->|No| F[5. Refine requirements] --> B
        E -->|Yes| G[6. Engineer the real product]
        G --> H[7. Test and deliver]
        H --> I[8. Maintenance]
    ```
    ```
       1. REQUIREMENT GATHERING - rough
            The developer and the customer agree the broad objectives
            and identify whatever requirements are already known. The
            details are deliberately left open.

       2. QUICK DESIGN
            A fast, high-level design covering only what the user will
            SEE - screens, inputs and outputs. Internal structure and
            efficiency are ignored at this stage.

       3. BUILD THE PROTOTYPE
            A working but incomplete model is built rapidly, using
            whatever tools are quickest. It need not be efficient or
            well structured.

       4. CUSTOMER EVALUATION
            The customer and the users actually USE the prototype and
            say what is wrong, missing or unnecessary. This is the
            whole point of the model - people cannot describe what
            they want, but they can react to what they see.

       5. REFINE THE PROTOTYPE
            The feedback is used to sharpen the requirements, and the
            prototype is modified.
            STEPS 2 to 5 REPEAT until the customer is satisfied.

       6. ENGINEER THE PRODUCT
            Once the requirements are clear, the REAL system is built
            properly - full design, production-quality code, standards
            and structure.

       7. TEST AND DELIVER
            Unit, integration, system and acceptance testing, then
            deployment.

       8. MAINTENANCE
            Corrective, adaptive, perfective and preventive changes.
    ```

    Types of prototype
    ```
       THROWAWAY (rapid) - built only to clarify requirements, then
            DISCARDED. The real system is built from scratch.
       EVOLUTIONARY - refined repeatedly until it BECOMES the product.
       INCREMENTAL - separate prototypes per module, later combined.
       EXTREME - for web work : static UI , then services , then logic.
    ```

    Advantages and disadvantages
    ```
       ADVANTAGES
         misunderstandings are caught EARLY, when they are cheap
         the user is involved from the beginning
         missing requirements are found before coding starts
         good where requirements are UNCLEAR or the customer cannot
           express them

       DISADVANTAGES
         the customer may mistake the prototype for a finished product
           and demand immediate delivery
         quick-and-dirty code, if kept, gives a poorly structured
           system
         the refine-and-show cycle can run on indefinitely
         the extra prototype work adds cost and time
    ```
    - When to use it: unclear requirements, a heavily interactive user interface, or a customer who has never used a system of this kind before. When not to: requirements already fixed and published, or a very small project where the prototype would cost as much as the product.

31. **From the diagram write down the software evolution.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 760 (ET: N/A)]*

    Answer: The question refers to a diagram that was not captured with it, so the standard `software evolution` process is described. Any textbook diagram of software evolution shows the same cycle.

    What software evolution is
    - `Software evolution` is the continual process of developing a software product and then `changing it repeatedly` over its working life to keep it useful. A useful system is never finished — it must change or it becomes obsolete.

    The process
    ```mermaid
    flowchart TD
        A[Existing system] --> B[Change requests]
        B --> C[Impact analysis]
        C --> D[Release planning]
        D --> E[System implementation]
        E --> F[Release the new system]
        F --> A
    ```
    ```
       1. CHANGE REQUESTS
            Requests arrive from users, from management, from changed
            law, or from defects found in operation.

       2. IMPACT ANALYSIS
            For each request : what modules are affected, what will it
            cost, what might it break. Requests that cost more than
            they are worth are rejected here.

       3. RELEASE PLANNING
            The accepted requests are grouped into a release, and the
            work is prioritised - fault repair, platform adaptation
            and system enhancement are balanced against the budget.

       4. SYSTEM IMPLEMENTATION
            The changes are designed, coded, and REGRESSION TESTED to
            prove nothing else has broken.

       5. RELEASE
            The new version is deployed, documentation updated, users
            informed.

       -> and the cycle BEGINS AGAIN with the next change requests.
    ```

    The types of change that drive evolution
    ```
       CORRECTIVE  fix defects found in use                (about 20 %)
       ADAPTIVE    adjust to a new OS , database or law    (about 25 %)
       PERFECTIVE  add features , improve performance      (about 50 %)
       PREVENTIVE  restructure to avoid future trouble     (about  5 %)
    ```
    - Note that `perfective` change is the largest share. Most evolution is not bug-fixing but responding to new demands from a system that people actually use.

    Lehman's laws — why evolution is unavoidable
    ```
       CONTINUING CHANGE
            A program used in a real environment MUST change, or it
            becomes progressively less useful.

       INCREASING COMPLEXITY
            As it changes, its structure DEGRADES - unless deliberate
            work is done to maintain it.

       CONSERVATION OF FAMILIARITY
            The amount of change per release stays roughly constant,
            because a team can only absorb so much at a time.
    ```

    The stages of a system's life
    ```
       DEVELOPMENT  -> the initial version is built
       EVOLUTION    -> regular releases add and adapt ; the team still
                       understands the system
       SERVICING    -> only essential fixes are made ; understanding
                       is fading, the structure has degraded
       PHASE-OUT    -> no further change ; the system is run until it
                       is replaced
    ```
    - What keeps a system in the `evolution` stage rather than sliding into `servicing`: `low coupling` and `high cohesion`, a maintained test suite, documentation kept in step with the code, and regular `refactoring`. When those are neglected, each change costs more than the last, and eventually `re-engineering` — rebuilding the system with the same function but a better structure — becomes cheaper than continuing to patch it.

32. **(খ) SDLC diagram সহ বর্ণনা করুন। SDLC এর মেজর phases গুলি কী?** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 779 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What SDLC is
    - `SDLC` — the `Software Development Life Cycle` — is the structured process a software product follows from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality remain controllable.

    Diagram
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
        G -.feedback.-> B
    ```
    ```
       +--------------------------+
       | 1. PLANNING / FEASIBILITY|  scope , budget , schedule
       +--------------------------+
                    |
       +--------------------------+
       | 2. REQUIREMENT ANALYSIS  |  -> SRS
       +--------------------------+
                    |
       +--------------------------+
       | 3. DESIGN                |  -> architecture , DB , screens
       +--------------------------+
                    |
       +--------------------------+
       | 4. CODING                |  -> source code
       +--------------------------+
                    |
       +--------------------------+
       | 5. TESTING               |  -> unit , integration , system ,
       +--------------------------+     acceptance
                    |
       +--------------------------+
       | 6. DEPLOYMENT            |  -> live system
       +--------------------------+
                    |
       +--------------------------+
       | 7. MAINTENANCE           |  -> corrective , adaptive ,
       +--------------------------+     perfective , preventive
    ```

    The major phases
    ```
       1. PLANNING AND FEASIBILITY
            Fix the scope, budget, schedule and team. Test technical,
            economic, operational, schedule and legal feasibility. The
            project can still be stopped here, cheaply.

       2. REQUIREMENT ANALYSIS
            Gather what users need through interviews, questionnaires
            and observation. Separate FUNCTIONAL requirements from
            NON-FUNCTIONAL ones (speed, security, availability).
            Output : SRS , signed off by the customer.

       3. DESIGN
            HIGH-LEVEL : architecture, modules, database schema.
            LOW-LEVEL  : algorithms, interfaces, screen layouts.
            Output : SDD , ER diagram , DFD , UML.

       4. CODING
            The design is turned into source code, module by module,
            following coding standards and under version control.

       5. TESTING
            UNIT -> INTEGRATION -> SYSTEM -> ACCEPTANCE.
            Acceptance testing is done by the CUSTOMER, and is the
            formal sign-off before release.

       6. DEPLOYMENT
            Install in the live environment, migrate data, train users,
            go live. Release may be DIRECT , PARALLEL , PILOT or
            PHASED.

       7. MAINTENANCE
            CORRECTIVE , ADAPTIVE , PERFECTIVE and PREVENTIVE change.
            Consumes 60-80 per cent of total lifetime cost.
    ```
    - Why the order matters: the cost of correcting an error rises steeply with the phase in which it is found — `1` in requirements, `10` in coding, `100 or more` after release. The whole point of a defined life cycle is to catch errors at the cheap end.

33. **(ii) Software development এর Agile Method সম্পর্কে আলোচনা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What the Agile method is
    - `Agile` is an approach in which software is built in short, repeated cycles called `sprints`, each producing `working software`, with the customer involved throughout. It was set out in the `Agile Manifesto` of 2001. It is a philosophy rather than a single method.
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint: 1-4 weeks]
        C --> D[Working increment]
        D --> E[Review + Retrospective]
        E --> A
    ```
    ```
       Every sprint contains ANALYSIS, DESIGN, CODING and TESTING - a
       complete mini life cycle, for a small slice of the product.
       That single structural change is what separates Agile from
       Waterfall.
    ```

    Its four values
    ```
       Individuals and interactions  over  processes and tools
       Working software              over  comprehensive documentation
       Customer collaboration        over  contract negotiation
       Responding to change          over  following a plan

       The right-hand items still have value ; the left-hand ones have
       MORE. Agile does not discard documentation or planning.
    ```

    How a sprint runs — Scrum, the commonest framework
    ```
       ROLES
         PRODUCT OWNER  - owns and prioritises the backlog ; represents
              the customer
         SCRUM MASTER   - removes obstacles and protects the process ;
              not a manager
         DEVELOPMENT TEAM - 5 to 9 people, cross-functional and
              self-organising

       EVENTS
         SPRINT PLANNING   - choose what to build this sprint
         DAILY STAND-UP    - 15 minutes : done , doing , blocked
         SPRINT REVIEW     - demonstrate WORKING SOFTWARE to the
                             customer
         RETROSPECTIVE     - how do we work better next sprint

       ARTEFACTS
         PRODUCT BACKLOG , SPRINT BACKLOG , the INCREMENT
         BURNDOWN CHART - work remaining against days left
    ```

    Advantages
    - `Working software every 1–4 weeks`, so business value arrives early.
    - `Change is welcomed` — the backlog is re-prioritised each sprint.
    - `Defects are found early`, where they are cheap: an error costs 1 unit in requirements and over 100 after release.
    - `Risk surfaces early`, at each sprint review.
    - `High customer satisfaction`, because the customer steers the product continuously.

    Disadvantages
    - `Light documentation` hurts when the team changes or the system must be maintained years later.
    - `Cost and scope cannot be fixed in advance`, which is a genuine problem for fixed-price government tenders.
    - `Scope creep` if the Product Owner is not disciplined.
    - Requires a `continuously available customer` and a `skilled, co-located team` — conditions many organisations cannot meet.

    - The frameworks built on Agile: `Scrum`, `Kanban` (visualise the work, limit work in progress), `Extreme Programming` (pair programming, TDD, continuous integration) and `SAFe` for large organisations. Large institutions typically run a `hybrid` — Waterfall planning and contract up front, Agile sprints for the build.

34. **(a) What is Agile? Mentionits four values.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

    Answer: What Agile is
    - `Agile` is an approach to software development in which the product is built in short, repeated cycles called `sprints`, each producing `working software`, with the customer involved throughout. It was defined in the `Agile Manifesto` of 2001 by 17 practitioners. It is a philosophy, not a single method.
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint: 1-4 weeks]
        B --> C[Working increment]
        C --> D[Review + Retrospective]
        D --> A
    ```
    ```
       Every sprint contains ANALYSIS, DESIGN, CODING and TESTING for a
       small slice of the product - a complete mini life cycle.
    ```

    Its four values
    ```
       1. INDIVIDUALS AND INTERACTIONS  over  processes and tools
            A motivated team that talks to each other beats a rigid
            process. A five-minute conversation settles what a week of
            emails will not.

       2. WORKING SOFTWARE  over  comprehensive documentation
            Progress is measured by software that RUNS, not by the
            number of documents produced. Document what is genuinely
            needed, no more.

       3. CUSTOMER COLLABORATION  over  contract negotiation
            Work WITH the customer continuously rather than arguing
            about what the signed contract says. A Product Owner sits
            with the team.

       4. RESPONDING TO CHANGE  over  following a plan
            A changed requirement is useful information, not a failure
            of planning. The backlog is re-prioritised every sprint.
    ```
    ```
       THE QUALIFICATION THAT IS OFTEN MISSED :

       "While there is value in the items on the RIGHT, we value the
        items on the LEFT MORE."

       Agile does NOT say documentation, tools, contracts or plans are
       worthless. It says that when the two conflict, the left-hand
       item wins.
    ```

    - The twelve principles that follow from these values include: satisfy the customer through `early and continuous delivery`; `welcome changing requirements` even late; deliver `frequently`; business and developers work together `daily`; `working software` is the primary measure of progress; maintain a `sustainable pace`; and the team `reflects and adjusts` at regular intervals.
    - The frameworks that implement Agile: `Scrum` (sprints, Product Owner, Scrum Master, daily stand-up), `Kanban` (visualise the work, limit work in progress), `Extreme Programming` (pair programming, TDD, continuous integration) and `SAFe` for large organisations.

35. **What is SDLC? List the stages involed in the SDLC process. Which stages ensures the user acceptance of the system?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

    Answer: What SDLC is
    - `SDLC` stands for `Software Development Life Cycle`. It is the structured process a software product goes through from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality remain controllable.

    The stages
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```
    ```
       1. PLANNING AND FEASIBILITY
            Scope, budget, schedule, team. Technical, economic,
            operational, schedule and legal feasibility are tested.

       2. REQUIREMENT ANALYSIS
            Interviews, questionnaires, observation. Functional and
            non-functional requirements are separated.
            Output : SRS , signed off by the customer.

       3. DESIGN
            High-level : architecture, modules, database schema.
            Low-level  : algorithms, interfaces, screens.

       4. CODING
            The design is turned into source code, module by module.

       5. TESTING
            Unit -> integration -> system -> ACCEPTANCE.

       6. DEPLOYMENT
            Install, migrate data, train users, go live.

       7. MAINTENANCE
            Corrective, adaptive, perfective and preventive change.
    ```

    Which stage ensures user acceptance of the system?
    ```
       THE TESTING STAGE - specifically USER ACCEPTANCE TESTING (UAT),
       the LAST level of testing before deployment.
    ```
    - Why UAT and not an earlier level:
    ```
       UNIT , INTEGRATION and SYSTEM testing are run by DEVELOPERS and
       the QA team. They prove the software works AS BUILT - that it
       matches the specification.

       UAT is run by the ACTUAL USERS, in a realistic environment,
       with real business data. It proves the software does what the
       BUSINESS NEEDS. It is the customer's formal SIGN-OFF, and it is
       what authorises deployment.
    ```
    ```
       The four levels of testing, in order :

         UNIT         each module           by developers
         INTEGRATION  modules together      by developers
         SYSTEM       whole product vs SRS  by the QA team
         ACCEPTANCE   business fitness      by the CUSTOMER  <- sign-off
    ```
    - Two forms of acceptance testing: `alpha testing`, done by users at the developer's site, and `beta testing`, done by real users in their own environment before general release.
    - One qualification worth adding: acceptance is `confirmed` at UAT, but it is `determined` much earlier. The acceptance criteria come straight from the `SRS` agreed during requirement analysis. If the SRS captured the wrong requirements, UAT will fail no matter how good the code is — which is why the analysis phase, not the testing phase, is where user acceptance is really won or lost.

36. **(ii) Software development এর ধাপসমূহ সংক্ষেপে বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 960 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The steps of software development — the `SDLC`.
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```

    1. Planning and feasibility study
    - Fix the scope, budget, schedule and team. Check `technical`, `economic`, `operational`, `schedule` and `legal` feasibility. A doomed project can still be stopped here, cheaply.
    - Output: project plan, feasibility report.

    2. Requirement analysis
    - Gather what users actually need — interviews, questionnaires, observation, study of existing documents. Separate `functional` requirements (what it must do) from `non-functional` ones (speed, security, availability).
    - Output: `SRS`, signed off by the customer.

    3. Design
    - Decide `how` it will be built. `High-level design` fixes the architecture, modules and database schema; `low-level design` fixes algorithms, interfaces and screens.
    - Output: design document, ER diagram, DFD, UML diagrams.

    4. Coding — implementation
    - Write the code module by module against the design, following coding standards, under version control, with code review.
    - Output: source code, unit-tested modules.

    5. Testing
    ```
       UNIT         each module alone         by developers
       INTEGRATION  modules working together  by developers
       SYSTEM       whole product vs the SRS  by the QA team
       ACCEPTANCE   business fitness          by the CUSTOMER
    ```
    - Output: test reports and a stable build.

    6. Deployment
    - Install in the live environment, migrate the data, train the users and go live. The release may be `direct`, `parallel`, `pilot` or `phased`.
    - Output: the running system.

    7. Maintenance
    ```
       CORRECTIVE  fix defects found in use
       ADAPTIVE    adjust to a new OS , database or law
       PERFECTIVE  add features , improve performance
       PREVENTIVE  restructure to avoid future trouble
    ```
    - Maintenance takes `60 to 80 per cent` of the total lifetime cost.

    - Why the sequence matters: the cost of fixing an error rises steeply with the phase in which it is found — `1` in requirements, `10` in coding, `100 or more` after release. Catching problems early is the whole purpose of a defined life cycle.

37. **What is Agile Methodology? Difference between Agile Model and Waterfall Model.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1003-1004 (ET: DU)]*

    Answer: What Agile methodology is
    - `Agile` is an approach in which software is built in short, repeated cycles called `sprints`, each producing `working software`, with the customer involved throughout. It was set out in the `Agile Manifesto` of 2001.
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint: 1-4 weeks]
        B --> C[Working increment]
        C --> D[Review + Retrospective]
        D --> A
    ```
    ```
       Every sprint contains ANALYSIS, DESIGN, CODING and TESTING for
       a small slice of the product - a complete mini life cycle.

       The four values :
         Individuals and interactions over processes and tools
         Working software            over comprehensive documentation
         Customer collaboration      over contract negotiation
         Responding to change        over following a plan
    ```

    Difference between the Agile model and the Waterfall model

    | Point | Waterfall | Agile |
    |---|---|---|
    | Approach | `Sequential` — one phase after another | `Iterative` and incremental |
    | Requirements | `Frozen` after analysis | A `living backlog`, re-prioritised each sprint |
    | Delivery | `Once`, at the very end | Working software every `1–4 weeks` |
    | Customer involvement | Start and end only | `Continuous` — a Product Owner in the team |
    | Testing | One phase `at the end` | `Inside every sprint` |
    | Cost of change | `Very high` | `Low` |
    | Documentation | Heavy and formal | Light — "just enough" |
    | Team | Specialised, hierarchical | `Cross-functional`, self-organising |
    | Risk discovery | `Late`, in testing | `Early`, at each review |
    | Progress measured by | Documents and phases completed | `Working software` |
    | Best for | Fixed, well-understood requirements | Unclear or changing requirements |

    The structural difference
    ```mermaid
    flowchart LR
        subgraph Waterfall
        A[Requirements] --> B[Design] --> C[Code] --> D[Test] --> E[Deploy]
        end
        subgraph Agile
        F[Backlog] --> G[Sprint] --> H[Increment] --> I[Review] --> F
        end
    ```
    ```
       WATERFALL does each phase ONCE, for the WHOLE product.
       AGILE does ALL the phases EVERY SPRINT, for a SMALL SLICE.

       Every other difference between the two follows from that.
    ```

    Why it matters
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall tests ONCE, at the end - the expensive point.
       Agile tests CONTINUOUSLY, so errors are caught while cheap.
    ```
    - Where each wins: `Waterfall` for fixed, published requirements, fixed-price tenders and safety-critical systems; `Agile` where requirements are unclear or changing, the customer can stay involved, and early delivery matters. Most large organisations run a `hybrid` — Waterfall planning and contract up front, Agile sprints for the build.

38. **What is SDLC? Write down the step of SDLC.** *[Bangladesh Television Assistant Programmer 2019 compact it 1066 (ET: N/A)]*

    Answer: What SDLC is
    - `SDLC` stands for `Software Development Life Cycle`. It is the structured process a software product follows from the first idea to final retirement, divided into ordered phases so that cost, schedule and quality remain controllable.

    The steps
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```
    ```
       1. PLANNING AND FEASIBILITY
            Fix the scope, budget, schedule and team. Test technical,
            economic, operational, schedule and legal feasibility.
            Output : project plan , feasibility report.

       2. REQUIREMENT ANALYSIS
            Gather user needs through interviews, questionnaires and
            observation. Separate FUNCTIONAL requirements from
            NON-FUNCTIONAL ones - speed, security, availability.
            Output : SRS , signed off by the customer.

       3. DESIGN
            HIGH-LEVEL : architecture, modules, database schema.
            LOW-LEVEL  : algorithms, interfaces, screen layouts.
            Output : SDD , ER diagram , DFD , UML diagrams.

       4. CODING (IMPLEMENTATION)
            The design is turned into source code, module by module,
            following coding standards, under version control.
            Output : source code , unit-tested modules.

       5. TESTING
            UNIT -> INTEGRATION -> SYSTEM -> ACCEPTANCE.
            Acceptance testing is done by the CUSTOMER and is the
            formal sign-off before release.
            Output : test reports , a stable build.

       6. DEPLOYMENT
            Install in the live environment, migrate the data, train
            the users, go live. Release may be DIRECT , PARALLEL ,
            PILOT or PHASED.
            Output : the running system.

       7. MAINTENANCE
            CORRECTIVE (fix defects) , ADAPTIVE (new OS or law) ,
            PERFECTIVE (new features) , PREVENTIVE (restructure).
            Takes 60-80 per cent of total lifetime cost.
    ```
    - The models that arrange these steps differently: `Waterfall` runs them once in strict order; `Incremental` repeats them per release; `Spiral` adds explicit risk analysis to each loop; `V-model` pairs each development phase with its test level; and `Agile` compresses the whole cycle into a 1–4 week sprint repeated continuously.
    - Why the order matters: an error costs about `1` unit to fix in requirements, `10` in coding and `100 or more` after release. Catching problems early is the entire purpose of a defined life cycle.

39. **(ক) Software Development Life Cycle (SDLC) এর বিভিন্ন ধাপগুলো উল্লেখ করুন ও সংক্ষেপে বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1086 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The phases of the `Software Development Life Cycle (SDLC)`.
    ```mermaid
    flowchart TD
        A[1. Planning and feasibility] --> B[2. Requirement analysis]
        B --> C[3. Design]
        C --> D[4. Coding]
        D --> E[5. Testing]
        E --> F[6. Deployment]
        F --> G[7. Maintenance]
    ```

    1. Planning and feasibility study
    - Fix the scope, budget, schedule and team, and decide whether the project is worth doing at all. Five kinds of feasibility are tested: `technical`, `economic`, `operational`, `schedule` and `legal`.
    - Output: project plan, feasibility report.

    2. Requirement analysis
    - Find out what the users actually need, through interviews, questionnaires, observation and study of existing documents. `Functional` requirements say what the system must do; `non-functional` ones cover speed, security and availability.
    - Output: the `SRS`, signed off by the customer.

    3. Design
    - Decide how the system will be built. `High-level design` fixes the architecture, the modules and the database schema; `low-level design` fixes each module's algorithms, interfaces and screens.
    - Output: SDD, ER diagram, DFD, UML diagrams.

    4. Coding — implementation
    - Programmers turn the design into source code, module by module, following the coding standards, under version control, with code review. Each module is unit tested by its own developer.
    - Output: source code.

    5. Testing
    ```
       UNIT         each module alone         by developers
       INTEGRATION  modules working together  by developers
       SYSTEM       whole product vs the SRS  by the QA team
       ACCEPTANCE   business fitness          by the CUSTOMER
    ```
    - Output: test reports and a stable build.

    6. Deployment
    - Install in the customer's environment, migrate the data, train the users and go live. The release may be `direct`, `parallel` (old and new run together), `pilot` (one branch first) or `phased`.
    - Output: the running system.

    7. Maintenance
    ```
       CORRECTIVE  fix defects found in use               (about 20 %)
       ADAPTIVE    adjust to a new OS , database or law   (about 25 %)
       PERFECTIVE  add features , improve performance     (about 50 %)
       PREVENTIVE  restructure to avoid future trouble    (about  5 %)
    ```
    - Maintenance consumes `60 to 80 per cent` of the total lifetime cost — more than all six earlier phases combined.

    - Why the sequence matters: the cost of correcting an error rises steeply with the phase in which it is found — about `1` unit in requirements, `10` in coding and `100 or more` after release. Catching problems early is the whole purpose of a defined life cycle.

40. **(খ) Software Development এর ক্ষেত্রে Agile মডেল সম্পর্কে লিখুন। অন্যান্য মডেলের তুলনায় এ মডেলের সুবিধা কি?** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1086 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The Agile model
    - `Agile` is an approach in which software is built in short, repeated cycles called `sprints`, each producing `working software`, with the customer involved throughout. It was defined in the `Agile Manifesto` of 2001.
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint: 1-4 weeks]
        C --> D[Working increment]
        D --> E[Review + Retrospective]
        E --> A
    ```
    ```
       Every sprint contains ANALYSIS, DESIGN, CODING and TESTING for
       a small slice of the product - a complete mini life cycle.

       THE FOUR VALUES
         Individuals and interactions over processes and tools
         Working software            over comprehensive documentation
         Customer collaboration      over contract negotiation
         Responding to change        over following a plan
    ```
    ```
       SCRUM, the commonest framework :

         ROLES     Product Owner , Scrum Master , Development Team
         EVENTS    Sprint Planning , Daily Stand-up , Sprint Review ,
                   Retrospective
         ARTEFACTS Product Backlog , Sprint Backlog , the Increment
    ```

    Advantages over the other models

    1. Working software arrives early
    - Waterfall, Spiral and the V-model all deliver a usable product only near the end. Agile delivers one every `1 to 4 weeks`, so business value starts immediately.

    2. Change is welcomed rather than resisted
    - Waterfall freezes requirements after analysis, so a change means a costly formal amendment. Agile re-prioritises the backlog every sprint, and one of its four values is exactly "responding to change over following a plan".

    3. Defects are caught while they are cheap
    ```
       Cost of fixing an error, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Waterfall tests ONCE, at the end. Agile tests EVERY SPRINT.
    ```

    4. Risk is exposed early
    - A sprint review every few weeks reveals technical and business risk. Spiral also handles risk, but at far higher cost — it needs repeated formal risk analysis and prototyping.

    5. The customer steers the product
    - A Product Owner sits with the team, so the product matches what the business needs rather than what the SRS happened to say months earlier.

    6. Real progress is visible
    - Progress is measured by `working software`, not by documents delivered. A Waterfall project can look healthy on paper while the product is in trouble.

    7. The team improves itself
    - The `retrospective` at the end of every sprint changes how the team works — no other classical model has a built-in improvement loop.

    - The fair qualification: Agile's advantages come with costs — light documentation, scope that cannot be fixed in advance, and a need for a continuously available customer and a skilled team. For a fixed-price government tender or a safety-critical system, `Waterfall` remains the better model, and large organisations commonly use a `hybrid` of the two.

41. **What is the SCRUM method in software development?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1116 (ET: BUET)]*

    Answer: What Scrum is
    - `Scrum` is the most widely used `Agile` framework. Work is done in fixed-length cycles called `sprints`, usually 2 to 4 weeks long, each one producing a `potentially shippable increment` of working software.
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint Backlog]
        C --> D[Sprint: 2-4 weeks<br/>daily stand-up]
        D --> E[Increment]
        E --> F[Sprint Review]
        F --> G[Retrospective]
        G --> A
    ```

    The three roles
    ```
       PRODUCT OWNER
            Owns the PRODUCT BACKLOG and decides its priority.
            Represents the customer and the business. Says WHAT is
            built and in what order - never HOW.

       SCRUM MASTER
            Protects the process and REMOVES OBSTACLES for the team.
            A facilitator and coach, NOT a manager - the team is
            self-organising and does not report to the Scrum Master.

       DEVELOPMENT TEAM
            5 to 9 people, CROSS-FUNCTIONAL (developers, testers,
            designers) and SELF-ORGANISING. The team decides HOW the
            work is done and how much it can take on.
    ```

    The five events
    ```
       SPRINT             the fixed-length cycle itself, 2-4 weeks.
                          Its length never changes mid-project.

       SPRINT PLANNING    the team pulls the highest-priority items
                          from the product backlog into the SPRINT
                          BACKLOG and agrees a sprint goal.

       DAILY SCRUM        15 minutes, standing, same time every day :
                          what I did , what I will do , what is
                          blocking me. It is a SYNCHRONISATION
                          meeting, not a status report to a manager.

       SPRINT REVIEW      the team DEMONSTRATES WORKING SOFTWARE to
                          the Product Owner and stakeholders, who give
                          feedback that reshapes the backlog.

       SPRINT RETROSPECTIVE
                          the team examines HOW IT WORKED and agrees
                          one or two concrete improvements for the
                          next sprint.
    ```

    The three artefacts
    ```
       PRODUCT BACKLOG  - the prioritised list of everything wanted,
                          written as USER STORIES :
                          "As a customer, I want to reset my password
                           so that I can log in again."
       SPRINT BACKLOG   - the items chosen for the current sprint,
                          broken into tasks.
       INCREMENT        - the working software produced this sprint,
                          meeting the DEFINITION OF DONE.
    ```

    Tracking
    ```
       BURNDOWN CHART - work remaining against days left in the sprint

         work
         left |\
              | \___
              |     \___          ideal line vs actual line ; if the
              |         \___      actual stays above the ideal, the
              +--------------->   sprint is in trouble
                      days
       VELOCITY - story points completed per sprint, used to forecast
                  how much the team can take on next time.
    ```

    - The rules that make Scrum work, and that are most often broken in practice: the `sprint scope is not changed` once the sprint has begun; the sprint `length is fixed`; the increment must meet an agreed `Definition of Done`; and the Scrum Master is a facilitator, `not a project manager`. A team that adds work mid-sprint or reports status upward at the stand-up is not running Scrum, whatever it calls itself.

42. **Show the structure model in software engineering. Phase of water fall life cycle.** *[Probashi Kallyan Bank Programmer 2019 compact it 1157 (ET: AUST)]*

    Answer: Structured model in software engineering
    - `Structured analysis and design` is the classical top-down approach: the system is broken into smaller and smaller functional modules until each one is simple enough to code. It is `process-oriented` — it asks what the system `does`, not what objects it is made of.
    ```
       TOP-DOWN DECOMPOSITION - the STRUCTURE CHART

                      +---------------------+
                      |   Payroll System    |
                      +---------------------+
                         /       |        \
                +--------+  +---------+  +----------+
                | Input  |  | Process |  |  Output  |
                | data   |  | salary  |  |  report  |
                +--------+  +---------+  +----------+
                     |          /   \          |
                +--------+ +------+ +------+ +--------+
                |Validate| |Basic | |Deduct| | Print  |
                +--------+ +------+ +------+ +--------+

       Each box is a MODULE. An arrow shows a CALL, and the data
       passed between modules is labelled on it.
    ```
    - Its tools:
    ```
       DFD - Data Flow Diagram : how data moves between processes,
             data stores and external entities. Levelled 0, 1, 2 ...
       ER DIAGRAM : the data model - entities and relationships.
       STRUCTURE CHART : the module hierarchy shown above.
       DATA DICTIONARY : the definition of every data item.
       DECISION TABLE and DECISION TREE : complex business rules.
    ```
    - The design goal is `high cohesion` (each module does one well-defined job) and `low coupling` (modules depend on each other as little as possible), because those two properties decide how expensive the system will be to change later.

    Phases of the Waterfall life cycle
    ```mermaid
    flowchart TD
        A[1. Requirement gathering and analysis] --> B[2. System design]
        B --> C[3. Implementation / coding]
        C --> D[4. Integration and testing]
        D --> E[5. Deployment]
        E --> F[6. Maintenance]
    ```
    ```
       1. REQUIREMENT GATHERING AND ANALYSIS
            All requirements are collected and recorded. The SRS is
            produced, signed off, and then FROZEN.

       2. SYSTEM DESIGN
            High-level : architecture, modules, database schema.
            Low-level  : algorithms, interfaces, screens.

       3. IMPLEMENTATION (CODING)
            The design is turned into code, module by module. Each
            module is unit tested by its developer.

       4. INTEGRATION AND TESTING
            Modules are combined and the whole system is tested
            against the SRS - integration, system, then acceptance
            testing by the customer.

       5. DEPLOYMENT
            Installed at the customer's site, data migrated, users
            trained, system goes live.

       6. MAINTENANCE
            Corrective, adaptive, perfective and preventive change.
    ```
    - The two fit together naturally: `structured analysis and design` is the technique used inside the requirement and design phases of a `Waterfall` project. Both are top-down and document-driven, which is why they were developed in the same era and are usually taught together. The modern alternative is `object-oriented analysis and design` with `UML`, which models the system as interacting objects rather than as a hierarchy of functions.

43. **Write the agile method components for Software development.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

    Answer: The components of the Agile method for software development.

    1. The four values — the foundation
    ```
       Individuals and interactions  over  processes and tools
       Working software              over  comprehensive documentation
       Customer collaboration        over  contract negotiation
       Responding to change          over  following a plan

       The right-hand items have value ; the left-hand ones have MORE.
    ```

    2. The twelve principles
    - Early and continuous delivery; welcome changing requirements; deliver frequently; business and developers work together daily; build around motivated individuals; face-to-face conversation; working software is the measure of progress; a sustainable pace; technical excellence; simplicity; self-organising teams; and regular reflection.

    3. The roles
    ```
       PRODUCT OWNER    owns and prioritises the backlog ; represents
                        the customer. Decides WHAT is built.
       SCRUM MASTER     protects the process, removes obstacles.
                        A facilitator, NOT a manager.
       DEVELOPMENT TEAM 5-9 people, cross-functional and
                        self-organising. Decides HOW.
       STAKEHOLDERS     the users and business people who give
                        feedback at each review.
    ```

    4. The artefacts
    ```
       PRODUCT BACKLOG - the prioritised list of everything wanted,
            written as USER STORIES :
            "As a customer, I want to reset my password so that I can
             log in again."
       SPRINT BACKLOG  - the items chosen for the current sprint,
            broken into tasks.
       INCREMENT       - the working software produced this sprint,
            meeting the agreed DEFINITION OF DONE.
       BURNDOWN CHART  - work remaining against days left.
    ```

    5. The events — the sprint cycle
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint Planning]
        B --> C[Sprint: 1-4 weeks<br/>daily stand-up]
        C --> D[Increment]
        D --> E[Sprint Review]
        E --> F[Retrospective]
        F --> A
    ```
    ```
       SPRINT PLANNING  choose the work and agree a sprint goal
       DAILY STAND-UP   15 minutes : done , doing , blocked
       SPRINT REVIEW    demonstrate WORKING SOFTWARE to the customer
       RETROSPECTIVE    how do we work better next sprint
    ```

    6. The engineering practices
    ```
       TEST-DRIVEN DEVELOPMENT   write the test first, then the code
       CONTINUOUS INTEGRATION    integrate and build several times a day
       REFACTORING               improve the structure without changing
                                 behaviour
       PAIR PROGRAMMING          two developers, one keyboard -
                                 continuous code review
       COLLECTIVE CODE OWNERSHIP anyone may change any code
       AUTOMATED TESTING         a regression suite run on every commit
    ```

    7. The estimation and tracking tools
    ```
       STORY POINTS  relative size, not hours
       PLANNING POKER  the team estimates together
       VELOCITY      story points completed per sprint, used to
                     forecast the next one
       DEFINITION OF DONE  the agreed standard an increment must meet
    ```

    - The frameworks that package these components: `Scrum` (the roles, events and artefacts above), `Kanban` (visualise the work, limit work in progress, no fixed sprints), `Extreme Programming` (the engineering practices) and `SAFe` for large organisations. Agile is the philosophy; these are the ways it is put into practice.

44. **Explain extreme programming.** *[NESCO Manager (Software) 2018 compact it 1208 (ET: N/A)]*

    Answer: What Extreme Programming is
    - `Extreme Programming (XP)` is an Agile method created by Kent Beck in the late 1990s. Its idea is to take the practices known to be good — code review, testing, design, integration — and apply them at an `extreme` level, continuously rather than occasionally.
    ```
       Code review is good      -> review ALL the time (PAIR PROGRAMMING)
       Testing is good          -> test BEFORE writing code (TDD)
       Integration is good      -> integrate SEVERAL TIMES A DAY (CI)
       Short iterations are good-> make them 1-2 WEEKS
       Simple design is good    -> design only for TODAY
    ```

    The five values
    ```
       COMMUNICATION  the team, and the customer, talk face to face
                      every day instead of exchanging documents.
       SIMPLICITY     build the simplest thing that works. Do not add
                      what "might be needed later".
       FEEDBACK       from the tests (seconds), from the pair
                      (minutes), from the customer (days).
       COURAGE        be willing to throw away bad code, refactor a
                      working design, or tell the customer the truth
                      about the schedule.
       RESPECT        every member's contribution matters.
    ```

    The core practices
    ```
       PAIR PROGRAMMING
            Two developers, one keyboard. One writes, the other
            reviews as it is typed. This is CONTINUOUS code review.

       TEST-DRIVEN DEVELOPMENT (TDD)
            Write the FAILING TEST FIRST, then the code that makes it
            pass, then refactor.  RED -> GREEN -> REFACTOR.
            The tests become a regression suite that never rots.

       CONTINUOUS INTEGRATION
            Integrate and build several times a day. Integration
            problems then take minutes, not weeks.

       REFACTORING
            Improve the internal structure WITHOUT changing behaviour.
            Done constantly, so the design never degrades.

       SIMPLE DESIGN
            Design for the requirement in hand, not for an imagined
            future. "You aren't gonna need it" (YAGNI).

       COLLECTIVE CODE OWNERSHIP
            Anyone may change any code. No module has a single owner
            who becomes a bottleneck.

       ON-SITE CUSTOMER
            A real customer representative sits WITH the team, full
            time, to answer questions the moment they arise.

       SMALL RELEASES
            A working version every 1-2 weeks.

       CODING STANDARDS
            One agreed style, which collective ownership and pair
            programming both require.

       SUSTAINABLE PACE (40-hour week)
            No systematic overtime. Tired programmers write defects.

       METAPHOR
            A shared, simple description of how the system works, so
            everyone uses the same vocabulary.

       PLANNING GAME
            The customer writes USER STORIES and sets priority ; the
            developers estimate. Neither side decides alone.
    ```

    The cycle
    ```mermaid
    flowchart LR
        A[User stories] --> B[Planning game]
        B --> C[Write test first]
        C --> D[Pair programming]
        D --> E[Refactor]
        E --> F[Continuous integration]
        F --> G[Small release]
        G --> A
    ```

    Strengths and weaknesses
    ```
       STRENGTHS
         very high code quality - TDD plus continuous review
         defects found in minutes, when they are cheapest
         the design stays clean, because refactoring never stops
         the customer gets exactly what is wanted

       WEAKNESSES
         pair programming looks expensive to management, and needs
           developers who can work together
         requires an ON-SITE CUSTOMER - many organisations cannot
           supply one
         little documentation, which hurts long-term maintenance
         needs a co-located, disciplined and experienced team
    ```
    - The point worth stating at the end: the twelve practices are `a system, not a menu`. Simple design is only safe because refactoring is constant; refactoring is only safe because TDD provides a regression suite; collective ownership is only safe because coding standards and pair programming keep the code uniform. Teams that adopt one or two practices in isolation usually get the cost without the benefit.

45. **Define software engineering according to IEEE. What is SDLC? Describe any two SDLC.** *[ICT Ministry Assistant Programmer 2017 compact it 1242 (ET: N/A)]*

    Answer: Software engineering according to IEEE
    ```
       IEEE Standard 610.12-1990 defines software engineering as :

       "The application of a SYSTEMATIC, DISCIPLINED, QUANTIFIABLE
        approach to the development, operation and maintenance of
        software ; that is, the application of ENGINEERING to
        software."
    ```
    - The three words carry the definition: `systematic` — a defined process, not ad-hoc coding; `disciplined` — standards, reviews and documentation are followed; `quantifiable` — progress and quality are measured, not guessed. And note that it covers `operation and maintenance`, not development alone.

    What SDLC is
    - `SDLC` — the `Software Development Life Cycle` — is the structured process a software product follows from the first idea to final retirement, split into ordered phases so that cost, schedule and quality stay controllable.
    ```
       1. Planning and feasibility    5. Testing
       2. Requirement analysis        6. Deployment
       3. Design                      7. Maintenance
       4. Coding
    ```

    Two SDLC models described

    1. The Waterfall model
    ```mermaid
    flowchart TD
        A[Requirements] --> B[Design] --> C[Coding] --> D[Testing] --> E[Deployment] --> F[Maintenance]
    ```
    - A `linear sequential` model, proposed by Winston Royce in 1970. Each phase is completed and formally approved before the next begins, and the output of one phase is the input to the next. There is no formal route back.
    ```
       ADVANTAGES
         simple to understand and manage ; clear deliverables
         heavily documented - suits contracts and audits
         easy to estimate and price, since the scope is fixed
         works well when requirements are FIXED and understood

       DISADVANTAGES
         requirements must be FROZEN after analysis
         NO working software until very late
         change is extremely expensive - no way back
         risk surfaces only in testing, the costliest point
         poor for long projects, where the business changes
    ```

    2. The Agile model
    ```mermaid
    flowchart LR
        A[Product Backlog] --> B[Sprint: 1-4 weeks] --> C[Working increment] --> D[Review] --> A
    ```
    - An `iterative and incremental` model set out in the Agile Manifesto of 2001. The product is built in short sprints, each producing working software, with the customer present throughout.
    ```
       FOUR VALUES
         Individuals and interactions over processes and tools
         Working software            over comprehensive documentation
         Customer collaboration      over contract negotiation
         Responding to change        over following a plan

       ADVANTAGES
         working software every 1-4 weeks
         requirements may change without wrecking the plan
         defects found early, where they are cheap
         the customer steers the product continuously

       DISADVANTAGES
         light documentation hurts long-term maintenance
         cost and scope cannot be fixed in advance - a problem for
           fixed-price tenders
         needs a committed customer and a skilled, co-located team
    ```

    Comparison

    | Point | Waterfall | Agile |
    |---|---|---|
    | Approach | `Sequential` | `Iterative` |
    | Requirements | `Frozen` | Evolve each sprint |
    | Delivery | Once, at the end | Every `1–4 weeks` |
    | Cost of change | `Very high` | Low |
    | Documentation | Heavy | Light |
    | Best for | Fixed requirements | Changing requirements |

    - Other models worth naming in one line: the `Spiral` model, which adds explicit `risk analysis` to every loop and suits large, costly, uncertain systems; the `V-model`, which pairs each development phase with its corresponding test level; and the `Prototype` model, which builds a throwaway model first to settle unclear requirements.

## Software Testing & Evaluation (40)

1. Explain the difference between Unit Testing and Integration Testing. [SO IT 25-07-2026]

   Answer: Difference between unit testing and integration testing

   | Point | Unit testing | Integration testing |
   |---|---|---|
   | What is tested | `One module` or function alone | `Two or more modules working together` |
   | Purpose | Does this piece work `by itself`? | Do the pieces work `together`? |
   | Who does it | `Developers` | Developers or the testing team |
   | Testing type | `White box` — the code is visible | Black box or `grey box` |
   | Isolation | Dependencies replaced by `stubs` and `drivers` | Real modules are used |
   | Faults found | Logic errors, wrong calculation, bad boundary | `Interface` errors, wrong data format, mismatched parameters |
   | When | `First`, as soon as a module is coded | `After` unit testing passes |
   | Scope | Very small | Larger, and grows with each build |
   | Cost of a defect | Lowest | Higher |

   The stubs and drivers point
   ```
      A module rarely stands alone, so unit testing fakes its
      neighbours :

           DRIVER - a dummy CALLER that invokes the module and passes
                    test data. Needed to test a lower-level module.
           STUB   - a dummy CALLED module that returns a fixed value.
                    Needed to test an upper-level module.

           +--------+        +----------+        +-------+
           | DRIVER | -----> | MODULE   | -----> | STUB  |
           | (fake  |        | UNDER    |        |(fake  |
           | caller)|        | TEST     |        | callee)|
           +--------+        +----------+        +-------+
   ```

   Integration approaches
   ```
      BIG BANG    all modules combined at once. Simple, but when it
           fails nobody knows which interface is at fault.

      TOP-DOWN    start at the top module, add lower ones gradually.
           Needs STUBS. Major control flaws are found early.

      BOTTOM-UP   start at the lowest modules and build upward.
           Needs DRIVERS. Low-level utilities are proved first, but
           the overall design is tested last.

      SANDWICH    top-down and bottom-up at the same time, meeting in
           the middle. Used on large systems.
   ```

   Example
   ```
      A banking application.

      UNIT TEST        calculateInterest() alone :
                       principal 1000 , rate 5 , time 1 -> expect 50
                       also test rate = 0 , negative principal , the
                       boundary values.

      INTEGRATION TEST calculateInterest() called by the
                       AccountModule, which in turn writes to the
                       DatabaseModule. Does the amount arrive in the
                       right FORMAT, with the right NUMBER OF DECIMAL
                       PLACES, in the right CURRENCY field ?
   ```
   - The reason both are needed: `every unit can pass its own tests and the system can still fail`. Unit tests prove each module is right on its own; integration tests prove the assumptions the modules make about each other are right. Interface mismatches are the commonest defect in large systems, and unit testing cannot detect them by definition.

2. **ফরম্যাটিভ মূল্যায়ন (Formative Evaluation) বলতে কী বুঝায়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What formative evaluation is
   - `Formative evaluation` is assessment carried out `while` a product or a process is still being developed, so that its findings can be used to `improve` it. It is done `during` the work, not after it.
   ```
      FORMATIVE  : evaluation TO IMPROVE  - done DURING development
      SUMMATIVE  : evaluation TO JUDGE    - done AT THE END
   ```
   - The distinction in one line: `formative evaluation shapes; summative evaluation grades`.

   In software engineering
   ```
      FORMATIVE evaluation                SUMMATIVE evaluation
      -----------------------------       -----------------------------
      code review , walkthrough           final acceptance testing
      unit and integration testing        system testing against the SRS
      prototype user testing              a released-product audit
      sprint review , retrospective       post-project review
      usability testing on a mock-up      the final usability report
   ```
   - Examples: a `code review` finds defects while the code is still being written, so the author can fix them cheaply. A `sprint review` in Agile shows working software to the customer every two weeks precisely so the next sprint can be corrected. A `usability test on a paper prototype` changes the design before it is built.

   Characteristics
   ```
      PURPOSE    to improve, not to grade
      TIMING     ongoing, during development
      FEEDBACK   immediate and specific, so it can be acted on
      RESULT     changes to the product or the process
      RISK       low - problems are found while they are cheap
   ```

   Why it matters
   ```
      Cost of fixing a defect, by the phase where it is FOUND :

        Requirements   1        Testing        50
        Design         5        After release  100+
        Coding        10

      FORMATIVE evaluation acts at the LEFT of this table ;
      SUMMATIVE evaluation only confirms what is already built.
   ```
   - In education, from where the term comes, `formative` assessment is the class test or assignment used to guide teaching, while `summative` assessment is the final examination that awards the grade. The software-engineering meaning is the same idea applied to a product.
   - The practical conclusion: both are needed. Formative evaluation improves the work while change is still cheap; summative evaluation is what finally certifies that the product is fit to release.

3. **Explain Verification and Validation in Software Engineering. Discuss black-box testing and white-box testing with examples.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*

   Answer: Verification and validation
   ```
      VERIFICATION : "Are we building the product RIGHT ?"
           Does the work product match its SPECIFICATION ?

      VALIDATION   : "Are we building the RIGHT product ?"
           Does the finished product meet the USER'S ACTUAL NEED ?
   ```

   | Point | Verification | Validation |
   |---|---|---|
   | Question asked | Building the product `right`? | Building the `right` product? |
   | Compared against | The `specification` — SRS, design | The `user's real need` |
   | When | `Throughout` development, at every phase | Mainly at the `end`, after the product runs |
   | Method | Reviews, walkthroughs, inspections, static analysis | Actual `testing` — the code is executed |
   | Code executed? | `No` — static | `Yes` — dynamic |
   | Who does it | The QA team and peers | The testing team and the `customer` |
   | Finds | Defects in documents and code structure | Defects in behaviour and fitness for purpose |
   | Cost of a defect found | Low | High |

   - Why both are needed: a product can pass verification completely and still fail validation. If the SRS captured the wrong requirement, the code will match the specification perfectly and still be useless. `Verification checks conformance; validation checks usefulness.`

   Black box testing
   - Tests the software `only through its inputs and outputs`, with no knowledge of the internal code. Done by testers working from the `SRS`.
   ```
           input ---->  [ ??? ]  ----> output
                      the box is CLOSED

      Techniques :
        EQUIVALENCE PARTITIONING - divide the input into classes that
             should behave alike, and test ONE value from each.
        BOUNDARY VALUE ANALYSIS  - test at and around the edges,
             where most defects live.
        DECISION TABLE - all combinations of business rules.
        STATE TRANSITION - the legal and illegal state changes.
        ERROR GUESSING - experience-based guesses.
   ```
   ```
      Example : a login field accepting a password of 8 to 16
      characters.

        EQUIVALENCE CLASSES : length < 8 (invalid) , 8-16 (valid) ,
             > 16 (invalid)
        BOUNDARY VALUES     : 7 , 8 , 9 , 15 , 16 , 17
   ```

   White box testing
   - Tests with `full knowledge of the internal code and logic`. The tester reads the source and designs cases to exercise its statements, branches and paths. Done by `developers`. Also called `structural` or `glass box` testing.
   ```
      Coverage criteria :
        STATEMENT  every line executed at least once
        BRANCH     every if takes both the true and false path
        PATH       every route through the code
        CONDITION  every sub-condition evaluated both ways
        LOOP       0 iterations , 1 iteration , many

      Example :  if (a > 0 && b > 0)  x = 1;  else  x = 2;

        STATEMENT coverage : 1 test  , a=1 , b=1
        BRANCH    coverage : 2 tests , (1,1) and (1,-1)
        CONDITION coverage : cases making a>0 both T and F, and
                             b>0 both T and F
   ```

   The difference in one line
   ```
      BLACK BOX tests WHAT the software does - from the SRS.
      WHITE BOX tests HOW it does it - from the CODE.
      GREY BOX  is in between - partial knowledge, used heavily in
                security testing.
   ```
   - They are complements, not alternatives. White box testing cannot find a `missing requirement`, because a feature that was never coded has no code to cover. Black box testing cannot find `dead code` or an untested branch. Both are needed.

4. **Difference between Alpha tests, Beta test, gamma test in software development.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

   Answer: Alpha, beta and gamma testing are the three stages of `acceptance testing`, in that order.

   | Point | Alpha testing | Beta testing | Gamma testing |
   |---|---|---|---|
   | Where | At the `developer's` site | At the `user's` own site | At the user's site |
   | Who tests | Internal staff, QA, sometimes selected users | `Real external users` | Real users |
   | Environment | Controlled, in a lab | `Real`, uncontrolled | Real |
   | Developer present? | `Yes`, watching | `No` | No |
   | Stage | `First` — before beta | After alpha | `Last` — just before release |
   | Testing type | White box + black box | `Black box` only | Black box only |
   | Purpose | Find defects before outsiders see it | Find defects in real use, gather feedback | Final check that the product is ready to ship |
   | Changes made | Many | Some | `None`, except critical fixes |
   | Also called | In-house acceptance testing | Field testing, pre-release testing | Release-candidate testing |

   Alpha testing
   ```
      Done at the DEVELOPER'S site, in a controlled environment, by
      the internal QA team and sometimes by selected customers.
      The developers WATCH and can fix defects immediately.

      Both WHITE BOX and BLACK BOX techniques are used, because the
      testers can see the code.

      Typically run in two cycles :
         cycle 1 - the QA team tests the build
         cycle 2 - after fixes, it is tested again
   ```

   Beta testing
   ```
      Done at the USER'S site, by REAL users, in the REAL environment,
      with NO developer present. The users report problems back.

      Only BLACK BOX testing is possible - the users cannot see the
      code.

      This is where a product meets conditions the developers could
      never reproduce : slow networks, old browsers, unexpected data,
      and users who click things nobody expected.
   ```

   Gamma testing
   ```
      The FINAL stage, done on the RELEASE CANDIDATE. The product is
      already complete and no new features are added.

      Its purpose is only to CONFIRM that the product is ready to
      ship, and that it meets the specified requirements. Only
      CRITICAL defects are fixed at this point.

      Note : gamma testing is NOT part of the standard ISTQB
      vocabulary. Many books stop at alpha and beta. Where it is
      taught, it means this final release-readiness check.
   ```

   The sequence
   ```mermaid
   flowchart LR
       A[System testing] --> B[Alpha: developer site, internal]
       B --> C[Beta: user site, real users]
       C --> D[Gamma: release candidate check]
       D --> E[Release]
   ```
   - The key contrast to state: `alpha testing is controlled and observed; beta testing is uncontrolled and unobserved`. That is exactly why both are needed — alpha finds the defects that careful testing reveals, and beta finds the ones only real users in real conditions can produce.

5. **What do you understand about software quality assurance (SQA)? While purchasing a software system for your company, as a SQA team leader what aspects will you look into for a quality software.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 330 (ET: BIBM)]*

   Answer: What SQA is
   - `Software Quality Assurance (SQA)` is the set of planned and systematic activities that ensure a software product and the process that builds it meet the required standards. It is `process-oriented` and `preventive` — it aims to stop defects being introduced, not merely to find them afterwards.
   ```
      SQA  vs  QC  vs  TESTING

      SQA      PROCESS oriented , PREVENTIVE. Standards, audits,
               reviews, training, process improvement.
      QC       PRODUCT oriented , DETECTIVE. Inspects the finished
               work to find defects.
      TESTING  a SUBSET of QC - executing the software to find
               failures.
   ```
   - Its activities: define standards and procedures, review the SRS and the design, run audits, verify that the process is being followed, collect defect metrics, and drive process improvement (`CMMI`, `ISO 9001`, `Six Sigma`).

   What to look for when buying software, as SQA team leader

   1. Functional fitness
   - Does it do what the business actually needs? Map every requirement in our SRS against the product's features and record the `gaps`. Insist on a demonstration with `our own data`, not the vendor's.

   2. Reliability and availability
   - Failure rate, `MTBF`, recovery time after a crash, and the vendor's published uptime record. Ask for `references` from existing customers of comparable size.

   3. Performance and scalability
   - Response time under our expected load, and behaviour at `peak` — month-end, salary day. Will it still work when our transaction volume triples? Ask for `benchmark results`, and run a `load test` during evaluation.

   4. Security
   - Authentication and role-based `authorisation`, data `encryption` at rest and in transit, an `audit trail` of who did what, patch policy, and any security certification. For a bank this is decisive.

   5. Usability
   - How long does an ordinary clerk take to learn it? Screen design, error messages, help, and language support.

   6. Maintainability and support
   - Who fixes defects, in what time, under what `SLA`? Is source code held in `escrow` if the vendor closes? How often are new versions issued, and what does an upgrade cost?

   7. Interoperability and portability
   - Does it integrate with our existing core banking system, database and reporting tools? Does it expose an `API`? Does it run on our platform, and can we move it later?

   8. Documentation and training
   - User manual, administrator guide, API documentation, and a training plan for our staff.

   9. Compliance
   - Does it satisfy Bangladesh Bank regulations, data-protection law and audit requirements? Are the `licence terms` acceptable, and what happens on renewal?

   10. Vendor evaluation
   - Financial stability, years in business, size of the support team, existing clients, and process maturity (`CMMI` level, `ISO 9001`).

   11. Total cost of ownership
   - Not the licence price alone: implementation, customisation, data migration, training, annual maintenance, and the cost of upgrades over five years.

   How to evaluate in practice
   ```
      1. Write the requirements and give each a WEIGHT.
      2. Score each candidate product against every requirement.
      3. Run a PILOT or proof of concept with OUR OWN data.
      4. Check REFERENCES - talk to existing customers directly.
      5. Compare TOTAL COST OF OWNERSHIP over 5 years, not licence
         price.
      6. Read the CONTRACT : SLA, penalties, source-code escrow,
         exit clause.
   ```
   - The single most common mistake to avoid: buying on `licence price and a demonstration`. A demonstration is prepared by the vendor with prepared data. Insist on a `pilot with our own data and our own users` before signing, and make the acceptance criteria part of the contract.

6. **Match the table:** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 396 (ET: BUET)]*

| Testing method | Topic |
|---|---|
| (i) Unit Testing | (a) the process where you test the smallest functional unit of code. |
| (ii) Integration Testing | (b) is a type of software testing in which the different units, modules or components of a software application are tested as a combined entity. |
| (iii) System Testing | (c) examines every component of an application to make sure that they work as a complete and unified whole. |
| (iv) Acceptance Testing | (d) software testing that evaluates whether a system meets its business and user requirements |
| (v) Performance Testing | (e) a testing measure that evaluates the speed, responsiveness and stability of a computer, network, software program or device under a workload. |
| (vi) Security Testing | (f) identifying and addressing security vulnerabilities in a software application. |
| (vii) Usability Testing | (g) a method of testing the functionality of a website, app, or other digital product by observing real users as they attempt to complete tasks on it. |

   Answer: The question is `incomplete` — the table to be matched was not captured, so the exact pairing cannot be given. The material such a question is normally set on is below, in the form a matching question uses.

   Testing terms and their definitions
   ```
      UNIT TESTING          test one module or function in isolation
      INTEGRATION TESTING   test two or more modules working together
      SYSTEM TESTING        test the complete product against the SRS
      ACCEPTANCE TESTING    the customer confirms business fitness
      REGRESSION TESTING    re-run old tests to prove a change broke
                            nothing
      SMOKE TESTING         a quick check that the build is stable
                            enough to test at all
      SANITY TESTING        a narrow check that one specific fix works
      ALPHA TESTING         at the developer's site, internal users
      BETA TESTING          at the user's site, real users
      STRESS TESTING        push beyond the limit until it breaks
      LOAD TESTING          behaviour under the expected load
      PERFORMANCE TESTING   speed and response time
      SECURITY TESTING      resistance to attack
      USABILITY TESTING     how easily users can use it
   ```

   Testing techniques
   ```
      BLACK BOX  test from inputs and outputs only ; from the SRS
      WHITE BOX  test with full knowledge of the code ; from the code
      GREY BOX   partial knowledge of the internals

      EQUIVALENCE PARTITIONING  divide input into classes, test one
                                value from each
      BOUNDARY VALUE ANALYSIS   test at and around the edges
      STATEMENT COVERAGE        every line executed once
      BRANCH COVERAGE           every if takes both paths
   ```

   SDLC phases and their outputs
   ```
      Planning            ->  project plan , feasibility report
      Requirement analysis->  SRS
      Design              ->  SDD , ER diagram , DFD , UML
      Coding              ->  source code
      Testing             ->  test reports
      Deployment          ->  the live system
      Maintenance         ->  updated versions
   ```

   SDLC models and their defining feature
   ```
      WATERFALL   linear sequential ; requirements frozen
      INCREMENTAL delivered in parts ; feedback after each release
      SPIRAL      RISK ANALYSIS in every loop
      PROTOTYPE   a model built first to clarify requirements
      V-MODEL     each development phase paired with its test level
      AGILE       short sprints ; the customer present throughout
   ```

   Verification and validation
   ```
      VERIFICATION  "building the product RIGHT ?"  - reviews , static
      VALIDATION    "building the RIGHT product ?"  - testing , dynamic
   ```
   - If the actual table is available, the method is the same in every case: read each item on the left, identify its `defining property`, and find the description on the right that names that property. Items that look similar — `smoke` against `sanity`, `load` against `stress`, `verification` against `validation` — are where matching questions place their traps, so those pairs are worth learning as pairs.

7. **Given scenario of software engineering (Unit test, Regression Test, Smoke Test, Integration testing, Load Testing). Write the name of the testing and whether it is functional? Non-functional or both.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

   Answer: The five named tests, with their classification.

   | Test | What it does | Functional / non-functional |
   |---|---|---|
   | Unit test | Tests one module or function in isolation | `Functional` |
   | Regression test | Re-runs old tests after a change to prove nothing else broke | `Both` |
   | Smoke test | A quick check that the build is stable enough to test at all | `Functional` |
   | Integration test | Tests two or more modules working together | `Functional` |
   | Load test | Behaviour under the expected number of users or transactions | `Non-functional` |

   The reasoning
   ```
      FUNCTIONAL testing asks  : does it do the RIGHT THING ?
           It checks BEHAVIOUR against the requirements.

      NON-FUNCTIONAL testing asks : does it do it WELL ENOUGH ?
           It checks QUALITY ATTRIBUTES - speed, load, security,
           usability, reliability.
   ```
   ```
      UNIT TEST         checks that one function returns the correct
           result. Purely behavioural.        -> FUNCTIONAL

      SMOKE TEST        runs the few critical paths - can the
           application start, can a user log in, does the main screen
           open. It checks BEHAVIOUR, only shallowly.
                                              -> FUNCTIONAL
           Also called a "build verification test". If it fails, the
           build is REJECTED and no further testing is attempted.

      INTEGRATION TEST  checks that data passes correctly across the
           interface between modules. Behavioural.
                                              -> FUNCTIONAL

      LOAD TEST         checks RESPONSE TIME and THROUGHPUT with,
           say, 1000 concurrent users. It says nothing about whether
           the answers are correct - only whether the system keeps
           up.                                -> NON-FUNCTIONAL

      REGRESSION TEST   is not a KIND of test but a REASON for
           re-running tests. The suite re-run may contain functional
           tests (does the calculation still give the right answer)
           AND non-functional ones (is the response time still under
           2 seconds).                        -> BOTH
   ```

   Related distinctions worth keeping straight
   ```
      SMOKE vs SANITY
           SMOKE  - WIDE and SHALLOW. Does the whole build work at
                    all ? Run on EVERY new build.
           SANITY - NARROW and DEEP. Does this ONE fixed defect
                    actually work now ? Run after a small change.

      LOAD vs STRESS
           LOAD   - the EXPECTED load. Does it meet the target ?
           STRESS - BEYOND the limit, until it breaks. Does it fail
                    GRACEFULLY, and does it recover ?
           Both are NON-FUNCTIONAL.
   ```
   - The rule to apply to any test named in such a question: if it checks `what the system does`, it is functional; if it checks `how well the system does it`, it is non-functional. Regression is the exception, because it describes `when` tests are run rather than what they check.

8. **(ক) Software Quality Assurance বলতে কী বোঝায়? উহার Attribute গুলো আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What Software Quality Assurance is
   - `Software Quality Assurance (SQA)` is the set of planned and systematic activities that ensure the software product and the process that builds it meet the required standards. It is `process-oriented` and `preventive` — its aim is to stop defects being introduced, not merely to find them later.
   ```
      SQA      PROCESS oriented , PREVENTIVE - standards, reviews,
               audits, training, process improvement.
      QC       PRODUCT oriented , DETECTIVE - inspects the finished
               work to find defects.
      TESTING  a SUBSET of QC - executing the software to find
               failures.
   ```
   - SQA activities: defining standards and procedures, reviewing the SRS and design, auditing that the process is followed, collecting defect metrics, and driving process improvement through `CMMI`, `ISO 9001` or `Six Sigma`.

   The quality attributes

   McCall's model groups eleven factors into three categories.
   ```
      PRODUCT OPERATION - how well it runs now
        CORRECTNESS   does it do exactly what the requirements say ?
        RELIABILITY   does it perform without failure, consistently ?
        EFFICIENCY    how much CPU, memory and storage does it need ?
        INTEGRITY     can it protect itself from unauthorised access ?
        USABILITY     how much effort does a user need to learn and
                      operate it ?

      PRODUCT REVISION - how easily it can be changed
        MAINTAINABILITY  how easily can a defect be located and fixed ?
        FLEXIBILITY      how easily can a new feature be added ?
        TESTABILITY      how easily can it be tested ?

      PRODUCT TRANSITION - how well it moves to a new environment
        PORTABILITY      can it be moved to another platform ?
        REUSABILITY      can its components be used in another system ?
        INTEROPERABILITY can it work with other systems ?
   ```

   The `ISO 9126` model, now superseded by `ISO 25010`, lists six characteristics:
   ```
      FUNCTIONALITY    does it provide the required functions,
                       accurately and securely ?
      RELIABILITY      maturity , fault tolerance , recoverability
      USABILITY        understandability , learnability , operability
      EFFICIENCY       time behaviour and resource use
      MAINTAINABILITY  analysability , changeability , stability ,
                       testability
      PORTABILITY      adaptability , installability , replaceability
   ```

   - The difference between the two models: `McCall` includes internal qualities that only developers see, while `ISO 9126` emphasises characteristics `visible to the user`. Both are used, and an examiner will accept either list.
   - The practical point: these attributes often `conflict`. Making a system faster (efficiency) may make it harder to read (maintainability); adding security checks (integrity) slows it down. Quality is therefore a matter of `deliberate trade-offs agreed with the customer`, not of maximising every attribute at once.

9. **6.5 Explain the difference between Unit Testing and Integration Testing.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: Difference between unit testing and integration testing

   | Point | Unit testing | Integration testing |
   |---|---|---|
   | What is tested | `One module` or function alone | `Two or more modules together` |
   | Question asked | Does this piece work `by itself`? | Do the pieces work `together`? |
   | Who does it | `Developers` | Developers or the testing team |
   | Technique | `White box` — the code is visible | Black box or `grey box` |
   | Isolation | Dependencies faked by `stubs` and `drivers` | Real modules are used |
   | Faults found | Logic errors, wrong calculations, bad boundaries | `Interface` errors, wrong data format, parameter mismatch |
   | When | `First`, as soon as a module is coded | `After` unit testing passes |
   | Cost of a defect | Lowest | Higher |

   Stubs and drivers
   ```
      A module rarely stands alone, so unit testing fakes its
      neighbours :

           DRIVER - a dummy CALLER that invokes the module with test
                    data. Needed to test a LOWER-level module.
           STUB   - a dummy CALLEE that returns a fixed value.
                    Needed to test an UPPER-level module.

           +--------+        +----------+        +--------+
           | DRIVER | -----> |  MODULE  | -----> |  STUB  |
           +--------+        |UNDER TEST|        +--------+
                             +----------+
   ```

   Integration approaches
   ```
      BIG BANG   everything combined at once. Simple, but when it
           fails nobody knows which interface caused it.
      TOP-DOWN   start at the top, add lower modules gradually.
           Needs STUBS. Control-flow flaws are found early.
      BOTTOM-UP  start at the lowest modules and build upward.
           Needs DRIVERS. Utilities proved first, design tested last.
      SANDWICH   both directions at once, meeting in the middle.
   ```

   Example
   ```
      Banking application.

      UNIT TEST        calculateInterest() alone :
                       principal 1000 , rate 5 , time 1 -> expect 50
                       plus rate = 0 , negative principal , boundaries.

      INTEGRATION TEST calculateInterest() called by AccountModule,
                       which writes to DatabaseModule. Does the amount
                       arrive with the right number of DECIMAL PLACES,
                       in the right CURRENCY field, in the right FORMAT?
   ```
   - The reason both are required: `every unit can pass its own tests and the system can still fail`. Unit tests prove each module is correct alone; integration tests prove the assumptions modules make about each other are correct. Interface mismatches are the commonest defect in large systems, and unit testing cannot detect them by definition.

10. **What is Software testing? Difference between Black box testing and White box testing.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

    Answer: What software testing is
    - `Software testing` is the process of running a program with the intention of `finding defects` — proving that what the software actually does differs from what it should do. It also measures quality and gives the confidence needed to release.
    ```
       Two facts that define the discipline :

       1. Testing can show the PRESENCE of defects, never their
          ABSENCE  (Dijkstra).
       2. EXHAUSTIVE testing is IMPOSSIBLE. A program with 10 inputs of
          32 bits each has more input combinations than there are atoms
          in the observable universe.

       So testing is about choosing the FEW cases most likely to find
       defects - which is exactly what the techniques below do.
    ```

    Difference between black box and white box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` — the box is closed | `Full` — the source is read |
    | Based on | The `SRS` / requirements | The `code` structure |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Level applied | System, acceptance | `Unit`, integration |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested internal paths, dead code | `Missing requirements` |
    | Programming knowledge | Not needed | `Required` |
    | Test design | Equivalence partitioning, boundary value analysis | Statement, branch, path coverage |

    Black box techniques
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       EQUIVALENCE PARTITIONING  divide the input into classes that
            should behave alike ; test ONE value from each.
       BOUNDARY VALUE ANALYSIS   test at and around the edges, where
            most defects live.
       DECISION TABLE            all combinations of business rules.
       STATE TRANSITION          legal and illegal state changes.
       ERROR GUESSING            experience-based guesses.

       Example : a password field accepting 8 to 16 characters.
            CLASSES  : <8 invalid , 8-16 valid , >16 invalid
            BOUNDARY : 7 , 8 , 9 , 15 , 16 , 17
    ```

    White box techniques
    ```
       STATEMENT COVERAGE  every line executed at least once
       BRANCH COVERAGE     every if takes both the true and false path
       PATH COVERAGE       every route through the code
       CONDITION COVERAGE  every sub-condition evaluated both ways
       LOOP COVERAGE       0 iterations , 1 , and many

       Example :  if (a > 0 && b > 0)  x = 1;  else  x = 2;
            STATEMENT : 1 test  (a=1 , b=1)
            BRANCH    : 2 tests (1,1) and (1,-1)
    ```

    - Why both are needed, stated plainly: `white box testing cannot find a missing requirement` — if a required feature was never coded, there is no code to cover, so no amount of coverage will reveal its absence. `Black box testing cannot find dead code` or an untested branch. The two are complements, and `grey box` testing, with partial knowledge of the internals, sits between them and is used heavily in security work.

11. **Define test plan and Test case.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 567 (ET: N/A)]*

    Answer: Test plan
    - A `test plan` is the document that describes the `whole testing effort` for a project — its scope, approach, resources and schedule. It answers `what will be tested, how, by whom and when`. It is written before testing begins, usually by the test manager.
    ```
       IEEE 829 contents of a test plan :

         1. Test plan identifier
         2. Introduction and objectives
         3. Test items - what software and which version
         4. FEATURES TO BE TESTED
         5. FEATURES NOT TO BE TESTED , and why
         6. APPROACH - the strategy : levels, techniques, tools
         7. Item PASS / FAIL criteria
         8. SUSPENSION criteria and resumption requirements
         9. Test DELIVERABLES - cases, scripts, reports
        10. Testing TASKS
        11. ENVIRONMENT - hardware, software, data, network
        12. Responsibilities - who does what
        13. Staffing and TRAINING needs
        14. SCHEDULE and milestones
        15. RISKS and contingencies
        16. Approvals
    ```

    Test case
    - A `test case` is a single, specific check: one set of inputs, the steps to perform, and the `expected result`. It answers `exactly what to do and what should happen`.
    ```
       Fields of a test case :

         Test case ID          TC_LOGIN_002
         Module / feature      Login
         Test case title       Login with a wrong password
         PRECONDITION          The user account exists and is active
         TEST DATA             username : rahim
                               password : wrongpass123
         STEPS                 1. Open the login page
                               2. Enter the username
                               3. Enter the wrong password
                               4. Click Login
         EXPECTED RESULT       Error message "Invalid credentials" is
                               shown ; the user stays on the login page
         ACTUAL RESULT         (filled in during execution)
         STATUS                Pass / Fail
         Priority              High
         Written by / date
    ```

    The difference

    | Point | Test plan | Test case |
    |---|---|---|
    | Scope | The `whole project` | `One specific check` |
    | Level | Strategic — what and how | Operational — exact steps |
    | Written by | `Test manager` / lead | `Test engineer` |
    | Quantity | `One` per project | `Hundreds or thousands` |
    | Written when | Before testing starts | During test design |
    | Answers | Scope, approach, schedule, resources | Input, steps, `expected result` |
    ```
       ONE test plan  ->  many TEST SUITES  ->  many TEST CASES
    ```
    - The single most important field of a test case is the `expected result`, and it must be written `before` the test is run. A test case without a pre-stated expected result is not a test — the tester will simply accept whatever the software produces.
    - Related term: a `test scenario` is a broader statement of what to verify ("verify the login functionality"), from which several concrete `test cases` are derived — valid login, wrong password, blank field, locked account.

12. **(d) What is the main difference between black box and white box testing?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)], [Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)], [Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

    Answer: The main difference is `knowledge of the internal code`.
    ```
       BLACK BOX  the tester CANNOT see the code. Testing is done
            purely through INPUTS and OUTPUTS, working from the SRS.
            It asks : does it do the RIGHT THING ?

       WHITE BOX  the tester CAN see the code. Test cases are designed
            to exercise the program's statements, branches and paths.
            It asks : does it do it the RIGHT WAY ?
    ```

    | Point | Black box | White box |
    |---|---|---|
    | Knowledge of code | `None` | `Full` |
    | Based on | The `SRS` / requirements | The `source code` |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System, acceptance testing | `Unit`, integration testing |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested paths, dead code | `Missing requirements` |
    | Test design | Equivalence partitioning, boundary values | Statement, branch, path coverage |

    Black box
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       Techniques : equivalence partitioning , boundary value
            analysis , decision tables , state transition , error
            guessing.

       Example : a password field accepting 8 to 16 characters
            CLASSES  : < 8 invalid , 8-16 valid , > 16 invalid
            BOUNDARY : 7 , 8 , 9 , 15 , 16 , 17
    ```

    White box
    ```
       The tester READS the code :

            if (a > 0 && b > 0)  x = 1;
            else                 x = 2;

       STATEMENT coverage : 1 test  (a=1 , b=1)
       BRANCH    coverage : 2 tests (1,1) and (1,-1)
       CONDITION coverage : cases making a>0 both T and F, and b>0
                            both T and F
    ```
    - The point that decides most exam answers: `white box testing cannot detect a missing requirement`. A feature that was never coded has no code to cover, so 100 per cent coverage proves nothing about it. `Black box testing cannot detect dead code` or an untested branch. The two are complements, and `grey box` testing — partial knowledge of the internals — sits between them and is used heavily in security testing.

13. **Verification and validation are two process areas at CMMI level 3. For both of these areas (a) provide a definition (b) a description of how you can fulfill these areas in your software testing activities.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 444 (ET: BIBM)]*

    Answer: (a) Definitions

    Verification (VER)
    ```
       CMMI : "to ensure that selected WORK PRODUCTS meet their
               SPECIFIED REQUIREMENTS."

       In plain terms : "Are we building the product RIGHT ?"
       It compares the work product against its SPECIFICATION.
    ```

    Validation (VAL)
    ```
       CMMI : "to demonstrate that a product or product component
               FULFILS ITS INTENDED USE when placed in its INTENDED
               ENVIRONMENT."

       In plain terms : "Are we building the RIGHT product ?"
       It compares the product against the USER'S ACTUAL NEED.
    ```

    | Point | Verification | Validation |
    |---|---|---|
    | Question | Building the product `right`? | Building the `right` product? |
    | Compared with | The `specification` — SRS, design | The `user's real need` |
    | When | `Throughout` development | Mainly at the `end`, in the real environment |
    | Method | Reviews, walkthroughs, `peer reviews`, static analysis | Actual `execution` — testing, demonstration, pilot |
    | Code executed? | `No` — static | `Yes` — dynamic |
    | Performed by | Peers and the QA team | Testers and the `customer` |

    (b) How each is fulfilled in software testing activities

    Verification — the three CMMI specific goals
    ```
       SG 1  PREPARE FOR VERIFICATION
            - select the work products to verify : SRS , design
              document , source code , test cases themselves
            - establish the verification ENVIRONMENT
            - define the verification PROCEDURES and CRITERIA -
              checklists, entry and exit criteria

       SG 2  PERFORM PEER REVIEWS
            - prepare and schedule the reviews
            - conduct INSPECTIONS and WALKTHROUGHS of the SRS, design
              and code
            - record and ANALYSE the defect data - defect density,
              where defects originate, which review type finds most

       SG 3  VERIFY SELECTED WORK PRODUCTS
            - execute the procedures , record results
            - identify CORRECTIVE ACTION and track it to closure
    ```
    ```
       In practice, our verification activities are :

         REQUIREMENT REVIEW  - is the SRS complete, consistent,
              testable, unambiguous ?
         DESIGN REVIEW       - does the design cover every SRS item ?
         CODE REVIEW and STATIC ANALYSIS - does the code follow the
              design and the coding standards ?
         TRACEABILITY MATRIX - every requirement maps to a design
              element, to code, and to at least one test case.
         UNIT and INTEGRATION TESTING - the code behaves as the
              design specifies.
    ```

    Validation — the two CMMI specific goals
    ```
       SG 1  PREPARE FOR VALIDATION
            - select the products to validate and the METHODS -
              user acceptance testing, demonstration, pilot run
            - establish the validation ENVIRONMENT : it must
              RESEMBLE PRODUCTION - real data volumes, real network,
              real hardware
            - define the validation procedures and ACCEPTANCE
              CRITERIA, agreed with the customer

       SG 2  VALIDATE PRODUCT OR PRODUCT COMPONENTS
            - perform validation and ANALYSE the results
            - record issues and feed them back
    ```
    ```
       In practice, our validation activities are :

         USER ACCEPTANCE TESTING (UAT) - real users, real business
              scenarios, real data ; the customer signs off.
         ALPHA TESTING - at our site, with internal users watching.
         BETA TESTING  - at the customer's site, real environment, no
              developer present.
         PILOT RUN     - one branch or department goes live first.
         PROTOTYPE DEMONSTRATIONS during development, so mismatches
              are found before the whole product is built.
         NON-FUNCTIONAL validation - load, performance and security
              testing under production-like conditions.
    ```

    - Why both are needed, and why CMMI treats them as separate process areas: a product can pass `verification` completely and fail `validation`. If the SRS captured the wrong requirement, the code will match the specification perfectly and still be useless to the user. Verification checks `conformance`; validation checks `usefulness`. At CMMI maturity level 3 both must be defined, planned and measured — not left to whatever the testers happen to do.

14. **অথবা, (ক) Software testing কী? উহার গুরুত্ব আলোচনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What software testing is
    - `Software testing` is the process of running a program with the intention of `finding defects` — proving that what the software actually does differs from what it should do. It also measures quality and provides the confidence needed to release.
    ```
       Two facts that define the discipline :

       1. Testing can show the PRESENCE of defects, never their
          ABSENCE (Dijkstra).
       2. EXHAUSTIVE testing is IMPOSSIBLE - the input space of even a
          small program is astronomically large.

       So testing is the art of choosing the FEW cases most likely to
       expose defects.
    ```

    Its importance

    1. Defects are cheapest to fix when found early
    ```
       Cost of fixing a defect, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       Testing at every level, not only at the end, keeps the cost at
       the left of this table.
    ```

    2. It protects money and reputation
    - A defect in a banking system can post a wrong balance, duplicate a transaction or expose customer data. The financial and legal cost of one such failure dwarfs the entire testing budget.

    3. It protects safety
    - In medical, aviation and industrial control software, an untested path can cost lives. This is why such systems are tested to `branch` or even `path` coverage, not merely to statement coverage.

    4. It verifies that the requirements are actually met
    - `Acceptance testing` is the customer's formal confirmation that the product does what the contract said. Without it there is no objective basis for accepting delivery.

    5. It gives confidence to release
    - A passing regression suite is the evidence on which a release decision is made. Without it, every release is a guess.

    6. It enables change
    - With an automated test suite, a developer can `refactor` freely, because a broken assumption shows up in minutes. Without one, every change is risky, and the system ossifies.

    7. It improves the product and the process
    - Defect data shows `where` defects arise — which module, which phase, which type — and that feeds process improvement. This is one of the main inputs to `SQA`.

    8. It is required for compliance
    - Standards such as `ISO 9001`, `CMMI` and banking regulations require documented testing with recorded results.

    The levels at which it is done
    ```
       UNIT         each module alone         by developers
       INTEGRATION  modules working together  by developers
       SYSTEM       the whole product vs SRS  by the QA team
       ACCEPTANCE   business fitness          by the CUSTOMER
    ```
    - The conclusion to state plainly: testing does not `create` quality — quality comes from good requirements, good design and good coding. Testing `measures` quality and prevents defective work from reaching the user. That is why `SQA` (preventive, process-oriented) and `testing` (detective, product-oriented) are both needed, and neither replaces the other.

15. **অথবা, (ক) Black-box এবং White-box testing এর মধ্যে পার্থক্যগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Differences between black-box and white-box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` — the box is closed | `Full` — the source is read |
    | Based on | The `SRS` / requirements | The `code` structure |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System and acceptance testing | `Unit` and integration testing |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested internal paths, dead code | `Missing requirements` |
    | Test design | Equivalence partitioning, boundary values | Statement, branch, path coverage |
    | Time to design | Less | More — the code must be studied |
    | Automation | UI and API test tools | Coverage tools and unit-test frameworks |

    Black box
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       TECHNIQUES
         EQUIVALENCE PARTITIONING  divide input into classes that
              behave alike ; test ONE value from each
         BOUNDARY VALUE ANALYSIS   test at and around the edges
         DECISION TABLE            all combinations of business rules
         STATE TRANSITION          legal and illegal state changes
         ERROR GUESSING            experience-based

       Example : a password field accepting 8 to 16 characters
            CLASSES  : < 8 invalid , 8-16 valid , > 16 invalid
            BOUNDARY : 7 , 8 , 9 , 15 , 16 , 17
    ```

    White box
    ```
       The tester READS the code and designs cases to cover it :

            if (a > 0 && b > 0)  x = 1;
            else                 x = 2;

       STATEMENT coverage : 1 test  (a=1 , b=1)
       BRANCH    coverage : 2 tests (1,1) and (1,-1)
       CONDITION coverage : cases making a>0 both T and F, and b>0
                            both T and F

       COVERAGE CRITERIA
         STATEMENT  every line executed once
         BRANCH     every if takes both paths
         PATH       every route through the code
         LOOP       0 iterations , 1 , and many
    ```

    - The point that settles most answers: `white box testing cannot detect a missing requirement`, because a feature that was never coded has no code to cover — 100 per cent coverage proves nothing about it. `Black box testing cannot detect dead code` or an untested branch. They are complements, not alternatives, and `grey box` testing — with partial knowledge of the internals — sits between them and is used heavily in security testing.

16. **What is software testing? Discuss effective and exhaustive testing.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

    Answer: What software testing is
    - `Software testing` is the process of running a program with the intention of `finding defects` — proving that what the software actually does differs from what it should do. It also measures quality and gives the confidence needed to release.
    ```
       Dijkstra's principle :
       "Testing can show the PRESENCE of defects, but never their
        ABSENCE."
    ```

    Exhaustive testing
    - `Exhaustive testing` means testing `every possible input and every possible path` through the program. It would prove the program correct — and it is `impossible` in practice.
    ```
       WHY IT IS IMPOSSIBLE

       Input space :
            a single 32-bit integer input has 2^32 = 4,294,967,296
            possible values.
            TWO such inputs give 2^64 = 1.8 * 10^19 combinations.
            At a million tests per second, that takes over
            500,000 YEARS.

       Path space :
            a loop that may run 1 to 20 times, containing a 5-way
            branch, has about 5^20 = 10^14 paths.
            At 1 ms per path : about 3,170 YEARS.

       And even exhaustive INPUT testing would not cover every
       internal STATE, timing and concurrency combination.
    ```
    - The consequence: testing must always be a `sample`. The entire craft lies in choosing the sample that is most likely to find defects.

    Effective testing
    - `Effective testing` means finding the `most defects with the fewest test cases`, by choosing cases intelligently rather than exhaustively.
    ```
       HOW EFFECTIVENESS IS ACHIEVED

       EQUIVALENCE PARTITIONING
            Inputs that should behave the same are grouped ; ONE value
            from each class is tested. Testing 5 and 6 adds nothing if
            both fall in the same class.

       BOUNDARY VALUE ANALYSIS
            Most defects live at the EDGES - off-by-one errors, wrong
            <= versus <. For a valid range 1 to 100, test
            0 , 1 , 2 , 99 , 100 , 101.

       RISK-BASED PRIORITY
            Test the modules that are most COMPLEX, most CHANGED, most
            USED, or most COSTLY to fail. In a bank, the interest
            calculation is tested harder than the help screen.

       DEFECT CLUSTERING (the PARETO principle)
            About 80 per cent of defects are found in about 20 per
            cent of the modules. Concentrate effort there.

       CODE COVERAGE as a check
            Measure statement and branch coverage to find what has NOT
            been exercised - but note that coverage is a MINIMUM, not
            a proof of correctness.

       REGRESSION AUTOMATION
            Automate the repeated checks so human effort goes into
            designing NEW tests rather than re-running old ones.
    ```

    Comparison
    ```
       +---------------+---------------------+---------------------+
       |               | EXHAUSTIVE          | EFFECTIVE           |
       +---------------+---------------------+---------------------+
       | Coverage      | every input, every  | selected classes    |
       |               | path               | and boundaries      |
       | Test cases    | astronomically many | manageable          |
       | Time and cost | infinite            | affordable          |
       | Feasible ?    | NO                  | YES                 |
       | Result        | proof of            | high confidence,    |
       |               | correctness         | not proof           |
       +---------------+---------------------+---------------------+
    ```
    - The conclusion to state: since exhaustive testing is impossible, the aim is never "test everything" but "`test the right things`". `Equivalence partitioning` reduces the number of cases; `boundary value analysis` chooses the ones most likely to fail; and `risk-based prioritisation` decides where to spend the remaining effort.

17. **How alpha testing is performed in software development?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

    Answer: What alpha testing is
    - `Alpha testing` is the first stage of `acceptance testing`. It is carried out at the `developer's own site`, in a controlled environment, by internal staff and sometimes by selected customers, with the developers `present and watching`.

    How it is performed
    ```
       1. ENTRY CRITERIA
            System testing is complete, the build is stable, and the
            product is FEATURE COMPLETE. A smoke test passes.

       2. PLAN THE ALPHA TEST
            Decide the scope, the environment, the participants and
            the exit criteria. Prepare REAL BUSINESS SCENARIOS, not
            just isolated function checks.

       3. SET UP THE ENVIRONMENT
            Configure a test environment at the developer's site that
            resembles production - similar hardware, similar data
            volumes, realistic test data.

       4. SELECT THE TESTERS
            The internal QA team, plus people from other departments
            who did NOT build the product, and sometimes a few
            friendly customers invited in.

       5. EXECUTE IN TWO CYCLES - the usual practice
            CYCLE 1 : the in-house QA team runs the full scenarios,
                 using BOTH white box and black box techniques,
                 because the code is available to them.
            Defects are logged, prioritised and FIXED.
            CYCLE 2 : after the fixes, the product is tested again,
                 this time with more emphasis on business users
                 exercising it as they actually would.

       6. LOG AND TRIAGE DEFECTS
            Every defect is recorded with severity and priority. The
            DEVELOPERS ARE PRESENT, so many are diagnosed and fixed
            immediately - this is the main advantage of alpha testing.

       7. NON-FUNCTIONAL CHECKS
            Performance, load, security and usability are exercised
            under production-like conditions.

       8. EXIT CRITERIA
            No open critical or high-severity defects ; all planned
            scenarios executed ; the product is judged fit to expose
            to outside users.

       9. SIGN OFF and move to BETA testing.
    ```

    ```mermaid
    flowchart LR
        A[System testing complete] --> B[Alpha cycle 1: QA team]
        B --> C[Fix defects]
        C --> D[Alpha cycle 2: business users]
        D --> E[Sign off]
        E --> F[Beta testing at user site]
    ```

    Alpha against beta
    ```
       ALPHA                          BETA
       -----------------------        -----------------------
       at the DEVELOPER'S site        at the USER'S site
       internal staff and invited     REAL external users
            customers
       CONTROLLED environment         REAL, uncontrolled
       developers PRESENT             developers ABSENT
       white box + black box          black box only
       many defects fixed on the      feedback collected and fixed
            spot                           in a later release
    ```
    - What alpha testing is `for`: to catch the defects that would embarrass the organisation if an outsider found them, while fixing is still cheap and the developers are on hand. What it `cannot` do is reproduce the conditions of real use — slow networks, unusual data, users behaving unexpectedly. That is exactly why `beta testing` follows it.

18. **(b) Explain block box testing and white box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 692 (ET: N/A)]*

    Answer: Black box testing
    - `Black box testing` examines the software `only through its inputs and outputs`, with no knowledge of the internal code. The tester works from the `SRS` and asks whether the system does the right thing.
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       Also called FUNCTIONAL , BEHAVIOURAL or CLOSED BOX testing.
       Done by TESTERS , at SYSTEM and ACCEPTANCE level.
       No programming knowledge is needed.
    ```
    ```
       TECHNIQUES

       EQUIVALENCE PARTITIONING
            Divide the input into classes that should behave alike,
            and test ONE value from each. Testing 5 and 6 adds nothing
            if both fall in the same class.

       BOUNDARY VALUE ANALYSIS
            Test at and around the edges, where off-by-one errors and
            wrong < versus <= live.

       DECISION TABLE   all combinations of business rules
       STATE TRANSITION legal and illegal state changes
       ERROR GUESSING   experience-based cases : empty input, zero,
                        a very long string, special characters
    ```
    ```
       Example : a field accepting an age between 18 and 60

         CLASSES  : < 18 invalid , 18-60 valid , > 60 invalid ,
                    non-numeric invalid
         BOUNDARY : 17 , 18 , 19 , 59 , 60 , 61
    ```
    - Strength: it finds `wrong or missing functionality`, and it tests the product the way a user experiences it. Weakness: it cannot tell which parts of the code were never exercised, so `dead code` and untested branches go unnoticed.

    White box testing
    - `White box testing` tests with `full knowledge of the internal code and logic`. The tester reads the source and designs cases to exercise its statements, branches and paths. It is done by `developers`, at `unit` and `integration` level. Also called `structural`, `glass box` or `clear box` testing.
    ```
       COVERAGE CRITERIA

         STATEMENT  every line executed at least once
         BRANCH     every if takes both the true and false path
         PATH       every route through the code
         CONDITION  every sub-condition evaluated both ways
         LOOP       0 iterations , 1 iteration , many
    ```
    ```
       Example :  if (a > 0 && b > 0)  x = 1;  else  x = 2;

         STATEMENT coverage : 1 test  (a=1 , b=1)
         BRANCH    coverage : 2 tests (1,1) and (1,-1)
         CONDITION coverage : cases making a>0 both T and F, and
                              b>0 both T and F
    ```
    - Strength: it finds `logic errors`, dead code, wrong loop boundaries and untested branches, and it can be measured objectively by a coverage tool. Weakness: it `cannot find a missing requirement` — a feature that was never coded has no code to cover, so 100 per cent coverage proves nothing about it.

    Comparison

    | Point | Black box | White box |
    |---|---|---|
    | Knowledge of code | `None` | `Full` |
    | Based on | `SRS` | `Source code` |
    | Done by | Testers | `Developers` |
    | Level | System, acceptance | `Unit`, integration |
    | Finds | Missing or wrong function | Logic errors, dead code |
    | Cannot find | Untested paths | `Missing requirements` |

    - They are complements, not alternatives. `Grey box` testing, with partial knowledge of the internals, sits between them and is used heavily in security testing.

19. **(a) Explain software validation, Verification and Modularity.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*

    Answer: Verification
    ```
       "Are we building the product RIGHT ?"

       Verification checks that a WORK PRODUCT matches its
       SPECIFICATION. It is STATIC - the code need not be executed.

       Methods : reviews , walkthroughs , inspections , peer review ,
                 static analysis , desk checking.
       Applied  : at EVERY phase - the SRS is verified against the
                 user's stated needs, the design against the SRS, the
                 code against the design.
       Done by  : peers and the QA team.
       Finds    : defects in documents and code structure, at the
                 LOWEST cost.
    ```

    Validation
    ```
       "Are we building the RIGHT product ?"

       Validation checks that the finished product meets the USER'S
       ACTUAL NEED, in the real environment. It is DYNAMIC - the code
       is EXECUTED.

       Methods : black box testing , system testing , user acceptance
                 testing , alpha and beta testing , pilot runs.
       Applied  : mainly at the END, once the product runs.
       Done by  : the testing team and the CUSTOMER.
       Finds    : defects in behaviour and in fitness for purpose.
    ```

    | Point | Verification | Validation |
    |---|---|---|
    | Question | Building the product `right`? | Building the `right` product? |
    | Compared with | The `specification` | The `user's real need` |
    | Code executed? | `No` — static | `Yes` — dynamic |
    | When | Throughout development | At the end |
    | By whom | Peers, QA | Testers, `customer` |

    - Why both are needed: a product can pass verification completely and still fail validation. If the SRS captured the wrong requirement, the code matches the specification perfectly and is still useless. `Verification checks conformance; validation checks usefulness.`

    Modularity
    - `Modularity` is the design principle of dividing a system into `separate, independent modules`, each with a single well-defined job and a clear interface. Each can be developed, tested and changed on its own.
    ```
                      +---------------------+
                      |   Banking System    |
                      +---------------------+
                         /       |        \
                +--------+  +---------+  +----------+
                |Account |  |Transact-|  | Report   |
                |Module  |  |ion Mod. |  | Module   |
                +--------+  +---------+  +----------+

       Each module hides its internal working and exposes only an
       INTERFACE. Another module needs to know WHAT it does, not HOW.
    ```

    The two measures of good modularity
    ```
       COHESION - HIGH is good
            How closely the things INSIDE one module belong together.
            A module that only validates a PIN has high cohesion. A
            "utility" module that validates PINs, prints reports and
            sends email has LOW cohesion.

       COUPLING - LOW is good
            How much one module depends on another. Modules that talk
            only through a small, well-defined interface are loosely
            coupled ; modules that share global variables are tightly
            coupled.

       THE RULE : HIGH COHESION , LOW COUPLING.
    ```

    Why modularity matters
    - `Maintainability` — a change stays inside one module instead of rippling through the system.
    - `Testability` — each module can be unit tested alone, with stubs and drivers standing in for its neighbours.
    - `Parallel development` — different people can build different modules at the same time.
    - `Reusability` — a well-defined module can be used in another system.
    - `Comprehensibility` — a person can understand one module without holding the whole system in mind.

    - How the three connect: `modularity` makes `verification` practical, because a small module can actually be reviewed and unit tested. And `validation` remains necessary however good the modules are, because correct modules assembled to the wrong specification still give the wrong product.

20. **(b) Explain the diference between black-box and White-box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*

    Answer: Difference between black-box and white-box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` — the box is closed | `Full` — the source is read |
    | Based on | The `SRS` / requirements | The `code` structure |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System, acceptance testing | `Unit`, integration testing |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested internal paths, dead code | `Missing requirements` |
    | Test design | Equivalence partitioning, boundary values | Statement, branch, path coverage |
    | Effort to design | Lower | Higher — the code must be studied |
    | Basis of "done" | All requirements exercised | A `coverage` percentage |

    Black box
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       TECHNIQUES
         EQUIVALENCE PARTITIONING - divide the input into classes
              that behave alike ; test ONE value from each
         BOUNDARY VALUE ANALYSIS  - test at and around the edges
         DECISION TABLE   - all combinations of business rules
         STATE TRANSITION - legal and illegal state changes
         ERROR GUESSING   - experience-based cases

       Example : a field accepting an age between 18 and 60
         CLASSES  : < 18 invalid , 18-60 valid , > 60 invalid
         BOUNDARY : 17 , 18 , 19 , 59 , 60 , 61
    ```

    White box
    ```
       The tester READS the code :

            if (a > 0 && b > 0)  x = 1;
            else                 x = 2;

       STATEMENT coverage : 1 test  (a=1 , b=1)
       BRANCH    coverage : 2 tests (1,1) and (1,-1)
       CONDITION coverage : cases making a>0 both T and F, and
                            b>0 both T and F

       COVERAGE CRITERIA
         STATEMENT  every line executed once
         BRANCH     every if takes both paths
         PATH       every route through the code
         LOOP       0 iterations , 1 iteration , many
    ```

    - The decisive point: `white box testing cannot detect a missing requirement`, because a feature that was never coded has no code to cover — even 100 per cent coverage proves nothing about it. `Black box testing cannot detect dead code` or an untested branch. The two are complements; `grey box` testing, with partial knowledge of the internals, sits between them and is used heavily in security testing.

21. **Software testing কত প্রকার ও কী কী? Testing এর ক্ষেত্রে Boundary Value Analysis (BVA) এবং Equivalence Partitioning কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Types of software testing

    By technique
    ```
       BLACK BOX  - no knowledge of the code ; tested through inputs
                    and outputs, from the SRS
       WHITE BOX  - full knowledge of the code ; statements, branches
                    and paths are exercised
       GREY BOX   - partial knowledge ; used heavily in security work
    ```

    By level
    ```
       UNIT         one module alone            by developers
       INTEGRATION  modules working together    by developers
       SYSTEM       the whole product vs SRS    by the QA team
       ACCEPTANCE   business fitness            by the CUSTOMER
                    (alpha , beta)
    ```

    By execution
    ```
       STATIC   - the code is NOT run : reviews, walkthroughs,
                  inspections, static analysis
       DYNAMIC  - the code IS run : all the levels above
    ```

    By purpose
    ```
       FUNCTIONAL      does it do the RIGHT THING ?
            smoke , sanity , regression , unit , integration , system ,
            acceptance

       NON-FUNCTIONAL  does it do it WELL ENOUGH ?
            performance , LOAD (expected load) , STRESS (beyond the
            limit) , security , usability , compatibility ,
            reliability , recovery , scalability

       MAINTENANCE
            regression testing after a change ; confirmation testing
            that a specific fix works
    ```

    By method
    ```
       MANUAL     - a human executes the cases
       AUTOMATED  - a tool executes them ; essential for regression
    ```

    Boundary Value Analysis
    - `Boundary Value Analysis (BVA)` tests at and just around the `edges` of an input range, because that is where most defects live — off-by-one errors, and `<` written where `<=` was meant.
    ```
       For a valid range  MIN  to  MAX , test :

            MIN - 1     just below      (invalid)
            MIN         the boundary    (valid)
            MIN + 1     just inside     (valid)
            MAX - 1     just inside     (valid)
            MAX         the boundary    (valid)
            MAX + 1     just above      (invalid)
    ```
    ```
       Example : a field accepting an age of 18 to 60

            17  18  19  ............  59  60  61
             ^   ^   ^                 ^   ^   ^
          invalid valid              valid   invalid

       6 test cases replace 44 - and they are the 6 most likely to
       fail.
    ```

    Equivalence Partitioning
    - `Equivalence Partitioning` divides the input into `classes whose members should all behave the same way`, and tests only `one value` from each class. If one member of a class works, the others are assumed to work too.
    ```
       Example : the same age field, 18 to 60

            CLASS 1 : age < 18          INVALID   -> test 10
            CLASS 2 : 18 <= age <= 60   VALID     -> test 35
            CLASS 3 : age > 60          INVALID   -> test 75
            CLASS 4 : non-numeric       INVALID   -> test "abc"
            CLASS 5 : empty             INVALID   -> test ""

       5 test cases instead of thousands.
    ```

    How they work together
    ```
       EQUIVALENCE PARTITIONING reduces the NUMBER of cases by
            grouping inputs that behave alike.
       BOUNDARY VALUE ANALYSIS chooses WHICH values to take - the
            ones at the edges of those classes, where defects
            concentrate.

       Used together they give small, high-yield test suites :

            Classes  : <18 , 18-60 , >60
            Boundaries : 17 , 18 , 19 , 59 , 60 , 61
            Plus one typical value from the middle : 35
    ```
    - The reason both exist: `exhaustive testing is impossible`, so the whole craft is choosing a small sample most likely to expose defects. Equivalence partitioning cuts the sample size; boundary value analysis makes the remaining cases the most productive ones.

22. **(খ) Quality Control কাকে বলে? Quality review process কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What Quality Control is
    - `Quality Control (QC)` is the set of activities that `inspect and test the finished work product` to find defects and confirm that it meets the required standards. It is `product-oriented` and `detective` — it finds defects that already exist.
    ```
       SQA      PROCESS oriented , PREVENTIVE
                standards, audits, training, process improvement.
                Aim : stop defects being INTRODUCED.

       QC       PRODUCT oriented , DETECTIVE
                inspection, review, testing of the work product.
                Aim : FIND defects that are already there.

       TESTING  a SUBSET of QC - executing the software to find
                failures.
    ```
    - QC activities: code review and inspection, walkthroughs, all levels of testing (unit, integration, system, acceptance), defect logging and tracking, and checking documents against standards.

    How the quality review process works
    ```mermaid
    flowchart LR
        A[Planning] --> B[Preparation]
        B --> C[Review meeting]
        C --> D[Rework]
        D --> E[Follow-up]
        E --> F{Exit criteria met?}
        F -->|No| B
        F -->|Yes| G[Approved]
    ```
    ```
       1. PLANNING
            Choose the work product - SRS , design document , code ,
            test cases. Appoint the roles :
                 MODERATOR - runs the review, keeps it on track
                 AUTHOR    - wrote the work product ; does NOT defend it
                 REVIEWERS - the peers who examine it
                 SCRIBE    - records every defect found
            Fix the entry criteria, the checklist and the schedule.

       2. KICK-OFF
            Distribute the document and the checklist ; explain the
            objectives.

       3. INDIVIDUAL PREPARATION
            Each reviewer studies the document ALONE and lists the
            defects found. THIS IS WHERE MOST DEFECTS ARE ACTUALLY
            FOUND - not in the meeting.

       4. REVIEW MEETING
            The findings are pooled, discussed and logged.
            THE GOLDEN RULE : the meeting FINDS defects, it does NOT
            FIX them, and it examines the PRODUCT, never the PERSON.
            A meeting that drifts into solving problems, or into
            criticising the author, has failed.

       5. REWORK
            The AUTHOR corrects the defects.

       6. FOLLOW-UP
            The moderator verifies that every logged defect has been
            addressed. If the exit criteria are not met, the review is
            repeated.
    ```

    Types of review
    ```
       INFORMAL REVIEW  a colleague reads it. Cheap, undocumented.
       WALKTHROUGH      the AUTHOR leads and explains the document to
                        the reviewers. Good for education and for
                        getting a shared understanding.
       TECHNICAL REVIEW peers with technical expertise assess it,
                        often for a design decision.
       INSPECTION       the MOST FORMAL. A trained moderator, defined
                        roles, entry and exit criteria, checklists and
                        METRICS. It finds the most defects, and is the
                        most expensive.
    ```

    Why reviews matter
    ```
       Cost of fixing a defect, by the phase where it is FOUND :

         Requirements   1        Testing        50
         Design         5        After release  100+
         Coding        10

       A review of the SRS acts at the FAR LEFT of this table. This is
       why reviewing a requirements document is the single most
       cost-effective quality activity available.
    ```
    - The metrics collected from reviews — defects found per page, defects per hour of preparation, and where in the life cycle each defect originated — feed back into `SQA` and drive process improvement. That is the link between `QC` (finding this defect) and `SQA` (stopping the next one).

23. **What is black box testing? Consider a program which computes the square root of an input integer between 0 and 5000. Determine the equivalence class test cases. Determine the test cases using boundary value analysis also.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

    Answer: What black box testing is
    - `Black box testing` examines the software `only through its inputs and outputs`, with no knowledge of the internal code. The tester works from the `SRS` and asks whether the system does the right thing.
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       Also called FUNCTIONAL , BEHAVIOURAL or CLOSED BOX testing.
       Done by TESTERS ; no programming knowledge needed.
       Techniques : equivalence partitioning , boundary value
            analysis , decision tables , state transition , error
            guessing.
    ```

    The program
    ```
       Computes the SQUARE ROOT of an input INTEGER between 0 and 5000.

            VALID input range :  0 <= n <= 5000
    ```

    Equivalence class test cases
    ```
       The input is divided into classes whose members should all
       behave the same way. ONE value is tested from each class.

       +-------+---------------------------+----------+-------------+
       | Class | Description               | Valid?   | Test value  |
       +-------+---------------------------+----------+-------------+
       |  EC1  | n < 0                     | INVALID  |   -25       |
       |  EC2  | 0 <= n <= 5000            | VALID    |  2500       |
       |  EC3  | n > 5000                  | INVALID  |  6000       |
       |  EC4  | non-integer (real number) | INVALID  |    12.7     |
       |  EC5  | non-numeric / character   | INVALID  |  "abc"      |
       |  EC6  | empty input               | INVALID  |   ""        |
       +-------+---------------------------+----------+-------------+
    ```
    ```
       EXPECTED RESULTS

         n = -25   -> error : "input must not be negative"
         n = 2500  -> 50           (sqrt of 2500)
         n = 6000  -> error : "input must not exceed 5000"
         n = 12.7  -> error : "input must be an integer"
         n = "abc" -> error : "input must be numeric"
         n = ""    -> error : "input required"

       6 test cases replace 5001 valid inputs plus every invalid one.
    ```

    Boundary value test cases
    ```
       Test at and just around the edges of the valid range, because
       that is where off-by-one errors and wrong < versus <= live.

       Valid range : MIN = 0 , MAX = 5000

       +--------+---------------+----------+---------------------+
       | Value  | Position      | Valid?   | Expected result     |
       +--------+---------------+----------+---------------------+
       |   -1   | MIN - 1       | INVALID  | error message       |
       |    0   | MIN           | VALID    | 0                   |
       |    1   | MIN + 1       | VALID    | 1                   |
       | 2500   | typical value | VALID    | 50                  |
       | 4999   | MAX - 1       | VALID    | 70.7036...          |
       | 5000   | MAX           | VALID    | 70.7107...          |
       | 5001   | MAX + 1       | INVALID  | error message       |
       +--------+---------------+----------+---------------------+
    ```
    ```
       VERIFICATION of the expected values :

            sqrt(0)    = 0
            sqrt(1)    = 1
            sqrt(2500) = 50            since 50 * 50 = 2500
            sqrt(4999) = 70.70360...
            sqrt(5000) = 70.71068...   since 70.71068^2 = 5000.0
    ```

    The two together
    ```
       EQUIVALENCE PARTITIONING reduces the NUMBER of cases by
            grouping inputs that behave alike.
       BOUNDARY VALUE ANALYSIS chooses WHICH values to use - the ones
            at the edges, where defects concentrate.

       COMBINED MINIMUM SUITE :
            -1 , 0 , 1 , 2500 , 4999 , 5000 , 5001 , 12.7 , "abc" , ""
            -> 10 test cases for a program with 5001 valid inputs.
    ```
    - The defect these cases are hunting: a programmer who wrote `if (n < 5000)` instead of `if (n <= 5000)`. The value `5000` — and only that value — exposes it. That single example is the whole argument for boundary value analysis.

24. **Definition of Gray-box testing and Unit testing.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*

    Answer: Grey-box testing
    - `Grey-box testing` is testing with `partial knowledge` of the internal structure. The tester knows the architecture, the database schema and the interfaces, but not the full source code. It sits between black box and white box.
    ```
       BLACK BOX : sees NOTHING inside      - tests from the SRS
       GREY BOX  : sees SOME of the inside  - architecture, database
                   schema, API contracts
       WHITE BOX : sees EVERYTHING          - tests from the code
    ```
    ```
       Example : testing a web login.

         BLACK BOX - type a wrong password , check the error message.
         GREY BOX  - knowing the users table has a "failed_attempts"
                     column, type a wrong password THREE times, then
                     CHECK THE DATABASE that the counter incremented
                     and the account locked.
         WHITE BOX - read the authentication function and design cases
                     to cover every branch in it.
    ```
    - Where it is used: `integration testing`, `API testing`, `database testing`, `web application testing` and above all `security testing` — a penetration tester who has been given the architecture but not the source is doing grey-box work.
    - Advantages: it combines the user's viewpoint with enough inside knowledge to design far sharper cases, and it verifies effects the user cannot see, such as database state. Disadvantage: with only partial visibility, full path coverage is impossible, so some internal paths still go untested.

    Unit testing
    - `Unit testing` tests the `smallest testable piece` of software — one function, method or class — `in isolation`, to prove it works by itself.
    ```
       Who   : the DEVELOPER who wrote it
       When  : as soon as the unit is coded, BEFORE integration
       Type  : WHITE BOX - the code is visible
       Aim   : find logic errors, wrong calculations and bad boundary
               handling at the cheapest possible point
    ```
    ```
       A unit rarely stands alone, so its neighbours are FAKED :

            DRIVER - a dummy CALLER that invokes the unit with test
                     data. Needed to test a LOWER-level unit.
            STUB   - a dummy CALLEE returning a fixed value. Needed to
                     test an UPPER-level unit.

            +--------+        +----------+        +--------+
            | DRIVER | -----> |   UNIT   | -----> |  STUB  |
            +--------+        |UNDER TEST|        +--------+
                              +----------+
    ```
    ```
       Example : calculateInterest(principal, rate, time)

            (1000 , 5 , 1)  -> expect 50
            (1000 , 0 , 1)  -> expect 0          zero rate
            (0 , 5 , 1)     -> expect 0          zero principal
            (-1000 , 5 , 1) -> expect an error   negative principal
    ```
    - Frameworks: `JUnit` for Java, `NUnit` for .NET, `pytest` for Python, `Google Test` for C++. These make the tests automatic, so the whole suite is re-run on every build as a `regression` check.
    - Why it matters most: a defect found in unit testing costs about a tenth of what the same defect costs in system testing, and a hundredth of what it costs after release. A maintained unit-test suite is also what makes `refactoring` safe — without it, developers stop improving the code and the system ossifies.

25. **Integration testing of pharmaceutical automation software?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

    Answer: What integration testing is
    - `Integration testing` checks that two or more modules `work together correctly` after each has passed its own unit tests. It finds `interface` defects — wrong data format, mismatched parameters, wrong units, bad timing — which unit testing cannot detect by definition.

    Pharmaceutical automation software — what the modules are
    ```
       +----------------+   +------------------+   +----------------+
       | Recipe / Batch |-->| Process Control  |-->|  PLC / Device  |
       | Management     |   | (weighing,mixing)|   |  Interface     |
       +----------------+   +------------------+   +----------------+
               |                     |                     |
               v                     v                     v
       +----------------+   +------------------+   +----------------+
       | Inventory      |   | Quality Control  |   | Audit Trail /  |
       | Management     |   | (QC) Module      |   | Reporting      |
       +----------------+   +------------------+   +----------------+
    ```

    The integration test cases that matter
    ```
       1. RECIPE -> PROCESS CONTROL
            Does a recipe of 250.00 mg per tablet reach the control
            module as 250.00 mg and NOT 250 g or 0.25 g ?
            UNIT MISMATCH is the classic interface defect, and in a
            pharmaceutical plant it is a patient-safety defect.

       2. PROCESS CONTROL -> PLC / DEVICE
            Is the mixing time, temperature and speed transmitted
            correctly ? Does the device ACKNOWLEDGE ? What happens if
            the acknowledgement never arrives ?

       3. SENSOR -> CONTROL MODULE
            Are temperature and weight readings received at the right
            frequency, with the right precision and the right sign ?
            Does an out-of-range reading raise an ALARM and stop the
            batch ?

       4. PROCESS -> INVENTORY
            Is raw material deducted exactly ONCE per batch ? A double
            deduction or a missed one corrupts stock records.

       5. QC MODULE -> BATCH RELEASE
            A batch that FAILS quality control must be BLOCKED from
            release. Test the negative path explicitly.

       6. ALL MODULES -> AUDIT TRAIL
            Every action must be logged with user, timestamp and old
            and new values. This is a REGULATORY requirement, not a
            convenience.

       7. ERROR AND RECOVERY PATHS
            Power failure mid-batch , network loss to the PLC ,
            database unavailable. Does the system fail SAFE - stop the
            equipment, preserve the batch record, and recover to a
            consistent state ?
    ```

    The approach
    ```
       BOTTOM-UP is usually chosen for plant automation :

            Test device drivers and the PLC interface FIRST, with
            DRIVERS standing in for the callers, because these are the
            components that touch real equipment and carry the
            greatest risk.
            Then integrate the control layer, then the management
            layer.

       Alternatives :
         TOP-DOWN  - start at recipe management, use STUBS for the
              devices. Finds control-flow flaws early.
         SANDWICH  - both at once ; used on large systems.
         BIG BANG  - unsuitable here : when it fails, nobody can tell
              which interface caused it, and the cost of a wrong
              command reaching real equipment is unacceptable.

       SIMULATORS are essential - the PLC and the equipment are
       replaced by a simulator so that a wrong command cannot damage
       machinery or waste material during testing.
    ```

    The regulatory dimension
    ```
       Pharmaceutical software falls under GxP and 21 CFR Part 11.
       Integration testing must therefore be part of a documented
       VALIDATION exercise :

            IQ - Installation Qualification : installed correctly
            OQ - Operational Qualification  : operates per
                 specification, in the intended range
            PQ - Performance Qualification  : performs consistently in
                 actual production

       Every test case, its expected result, its actual result and
       its approval must be RECORDED and RETAINED. An undocumented
       test does not exist as far as an auditor is concerned.
    ```
    - The point that distinguishes this domain: in ordinary business software an integration defect produces a wrong report; here it can produce a wrong `dose`. So the test design concentrates on `units of measurement`, `alarm and interlock paths`, `audit trail completeness` and `safe failure`, and every one of those is tested with negative cases, not merely happy paths.

26. **(ক) Software এর \alpha-version ও \beta-version কি?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Alpha version
    - The `alpha version` is the first reasonably complete build of the software, tested `inside the developer's own organisation`. It is feature-complete but still contains many known defects.
    ```
       Where    : at the DEVELOPER'S site , controlled environment
       Who      : internal QA staff, other departments, sometimes a
                  few invited customers
       Present  : the DEVELOPERS watch and fix defects on the spot
       Testing  : BOTH white box and black box, since the code is
                  available
       State    : unstable ; crashes and missing pieces are expected
       Purpose  : catch the defects that would embarrass the company
                  if an outsider found them
    ```

    Beta version
    - The `beta version` is the near-final build released to a limited number of `real users outside the organisation`, who use it in their own environment and report problems back.
    ```
       Where    : at the USER'S site , the REAL environment
       Who      : REAL external users - a public or closed beta
       Present  : NO developer is present
       Testing  : BLACK BOX only - users cannot see the code
       State    : fairly stable ; most major defects already fixed
       Purpose  : find the defects that only real conditions produce,
                  and gather feedback before general release
    ```

    Comparison

    | Point | Alpha version | Beta version |
    |---|---|---|
    | Where tested | `Developer's` site | `User's` own site |
    | Who tests | Internal staff, invited customers | `Real external users` |
    | Environment | Controlled, lab-like | `Real`, uncontrolled |
    | Developer present | `Yes` | `No` |
    | Stability | Unstable, many defects | Fairly stable |
    | Testing type | White box + black box | `Black box` only |
    | Order | `First` | After alpha |
    | Defect fixing | Immediate, on the spot | Collected, fixed in a later build |
    | Also called | In-house acceptance testing | Field testing, pre-release |

    The sequence
    ```mermaid
    flowchart LR
        A[System testing] --> B[ALPHA version: internal]
        B --> C[Fix defects]
        C --> D[BETA version: real users]
        D --> E[Fix and finalise]
        E --> F[Final release]
    ```
    - The essential contrast: `alpha testing is controlled and observed; beta testing is uncontrolled and unobserved`. That is exactly why both are needed. Alpha finds what careful testing reveals; beta finds what only real users on real networks with real data can produce — slow connections, old browsers, unexpected input, and people using the product in ways nobody anticipated.
    - Some organisations add a `gamma version` — a final release-candidate check in which no new features are added and only critical defects are fixed.

27. **(গ) Unit testing, Integration testing এবং Beta testing বলতে কি বুঝায়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Unit testing
    - `Unit testing` tests the `smallest testable piece` of software — one function, method or class — `in isolation`, to prove it works on its own.
    ```
       Who   : the DEVELOPER who wrote it
       When  : as soon as the unit is coded, BEFORE integration
       Type  : WHITE BOX - the code is visible
       Aim   : find logic errors, wrong calculations and bad boundary
               handling at the cheapest possible point
    ```
    ```
       Neighbours are FAKED so the unit stands alone :
            DRIVER - a dummy CALLER that invokes the unit
            STUB   - a dummy CALLEE returning a fixed value

       Example : calculateInterest(principal, rate, time)
            (1000 , 5 , 1)  -> expect 50
            (1000 , 0 , 1)  -> expect 0
            (-1000 , 5 , 1) -> expect an error
    ```
    - Frameworks: `JUnit`, `NUnit`, `pytest`, `Google Test`. Automated unit tests become the `regression suite` re-run on every build.

    Integration testing
    - `Integration testing` checks that two or more modules `work together correctly` after each has passed its own unit tests. It finds `interface` defects — wrong data format, mismatched parameters, wrong units — which unit testing cannot detect by definition.
    ```
       APPROACHES
         BIG BANG   everything at once. Simple, but a failure gives no
              clue which interface caused it.
         TOP-DOWN   start at the top module, add lower ones ; needs
              STUBS. Control-flow flaws found early.
         BOTTOM-UP  start at the lowest modules ; needs DRIVERS.
              Utilities proved first.
         SANDWICH   both directions at once, meeting in the middle.
    ```
    ```
       Example : calculateInterest() is called by AccountModule, which
       writes to DatabaseModule. Does the amount arrive with the right
       number of DECIMAL PLACES, in the right CURRENCY field, in the
       right FORMAT ?
    ```

    Beta testing
    - `Beta testing` is the second stage of acceptance testing. A near-final build is given to a limited number of `real users outside the organisation`, who use it in their `own environment` with `no developer present` and report problems back.
    ```
       Where   : at the USER'S site , the REAL environment
       Who     : REAL external users - a public or closed beta
       Type    : BLACK BOX only - users cannot see the code
       Purpose : find the defects that only real conditions produce -
                 slow networks, old browsers, unusual data, and users
                 behaving in ways nobody anticipated
       Follows : ALPHA testing, which is done at the developer's site
                 with the developers watching
    ```

    Where they sit in the sequence
    ```mermaid
    flowchart LR
        A[UNIT: one module] --> B[INTEGRATION: modules together]
        B --> C[SYSTEM: whole product vs SRS]
        C --> D[ACCEPTANCE: alpha then BETA]
        D --> E[Release]
    ```
    - The reason all three are needed: unit testing proves each module is right `alone`; integration testing proves the assumptions modules make about `each other` are right; and beta testing proves the finished product survives `the real world`, which no controlled test environment can reproduce.

28. **(i) Black Box testing and White Box testing এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Difference between Black Box testing and White Box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` — the box is closed | `Full` — the source is read |
    | Based on | The `SRS` / requirements | The `code` structure |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System, acceptance testing | `Unit`, integration testing |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested internal paths, dead code | `Missing requirements` |
    | Test design | Equivalence partitioning, boundary values | Statement, branch, path coverage |
    | Design effort | Lower | Higher — the code must be studied |
    | "Done" measured by | All requirements exercised | A `coverage` percentage |

    Black box
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       TECHNIQUES
         EQUIVALENCE PARTITIONING - group inputs that behave alike ;
              test ONE value from each class
         BOUNDARY VALUE ANALYSIS  - test at and around the edges
         DECISION TABLE   - all combinations of business rules
         STATE TRANSITION - legal and illegal state changes
         ERROR GUESSING   - experience-based cases

       Example : a field accepting an age of 18 to 60
            CLASSES  : < 18 invalid , 18-60 valid , > 60 invalid
            BOUNDARY : 17 , 18 , 19 , 59 , 60 , 61
    ```

    White box
    ```
       The tester READS the code :

            if (a > 0 && b > 0)  x = 1;
            else                 x = 2;

       STATEMENT coverage : 1 test  (a=1 , b=1)
       BRANCH    coverage : 2 tests (1,1) and (1,-1)
       CONDITION coverage : cases making a>0 both T and F, and
                            b>0 both T and F

       COVERAGE CRITERIA
         STATEMENT  every line executed once
         BRANCH     every if takes both paths
         PATH       every route through the code
         LOOP       0 iterations , 1 , and many
    ```

    - The decisive point: `white box testing cannot detect a missing requirement` — a feature never coded has no code to cover, so even 100 per cent coverage says nothing about it. `Black box testing cannot detect dead code` or an unexercised branch. They are complements; `grey box` testing, with partial knowledge of the internals, sits between them and is used heavily in security testing.

29. **(a) Distinguish between black box and white box testing. Give examples of both type of testing** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

    Answer: Distinction between black box and white box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` | `Full` |
    | Based on | The `SRS` / requirements | The `source code` |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System, acceptance | `Unit`, integration |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested paths, dead code | `Missing requirements` |
    | Basis of "done" | All requirements exercised | A `coverage` percentage |

    Examples of black box testing
    ```
       1. LOGIN FORM
            Enter a valid username and password  -> expect the home
                 page.
            Enter a valid username and a wrong password -> expect
                 "Invalid credentials".
            Leave both blank -> expect "Field required".
            The tester never looks at the authentication code.

       2. AGE FIELD accepting 18 to 60 - EQUIVALENCE PARTITIONING
            CLASS 1 : age < 18        invalid  -> test 10
            CLASS 2 : 18 to 60        valid    -> test 35
            CLASS 3 : age > 60        invalid  -> test 75
            CLASS 4 : non-numeric     invalid  -> test "abc"

       3. THE SAME FIELD - BOUNDARY VALUE ANALYSIS
            17 , 18 , 19 , 59 , 60 , 61
            The value 18 exposes  if (age > 18)  written where
            if (age >= 18)  was meant.

       4. ATM WITHDRAWAL
            Withdraw 500 from a balance of 1000 -> expect success,
                 balance 500.
            Withdraw 2000 from 1000 -> expect "Insufficient balance".
            Withdraw 0 , withdraw a negative amount , withdraw an
                 amount that is not a multiple of 500.
    ```

    Examples of white box testing
    ```
       1. STATEMENT AND BRANCH COVERAGE

            int grade(int m) {
                if (m >= 80)      return 1;   // A
                else if (m >= 60) return 2;   // B
                else              return 3;   // C
            }

            STATEMENT coverage needs 3 tests : m = 90 , 70 , 40
            BRANCH    coverage needs the same 3 - every if takes both
                 its true and false path across those cases.

       2. CONDITION COVERAGE

            if (a > 0 && b > 0)  x = 1;  else  x = 2;

            Cases must make  a > 0  both TRUE and FALSE, and
                             b > 0  both TRUE and FALSE :
                 (1 , 1)   (1 , -1)   (-1 , 1)

       3. LOOP COVERAGE

            for (i = 0; i < n; i++)  sum += a[i];

            Test n = 0 (loop never runs) , n = 1 (runs once) ,
                 n = 100 (runs many times).
            n = 0 is the case that exposes an uninitialised sum.

       4. DEAD CODE DETECTION
            A coverage tool reports that the else branch of a
            particular if was NEVER executed by any test - either the
            test suite is incomplete, or that branch is unreachable
            and should be deleted.
    ```

    - Why both are required: white box testing `cannot find a missing requirement`, because a feature that was never coded has no code to cover. Black box testing `cannot find dead code` or an untested branch. `Grey box` testing sits between them — partial knowledge of the architecture and database, used heavily in security and API testing.

30. **Software development এ Black Box Testing বলতে কি বুঝায়?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) What black box testing is
    - `Black box testing` examines the software `only through its inputs and outputs`, with no knowledge of the internal code. The tester works from the `SRS` and asks one question: does the system do the `right thing`?
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       Also called FUNCTIONAL , BEHAVIOURAL or CLOSED BOX testing.
       Done by TESTERS , at SYSTEM and ACCEPTANCE level.
       No programming knowledge is needed.
    ```

    Techniques
    ```
       EQUIVALENCE PARTITIONING
            Divide the input into classes that should behave alike ;
            test ONE value from each. Testing 5 and 6 adds nothing if
            both fall in the same class.

       BOUNDARY VALUE ANALYSIS
            Test at and around the edges, where off-by-one errors and
            wrong < versus <= live.

       DECISION TABLE      all combinations of business rules
       STATE TRANSITION    legal and illegal state changes
       ERROR GUESSING      experience-based : empty input, zero, a
                           very long string, special characters
       USE CASE TESTING    end-to-end business scenarios
    ```

    Example
    ```
       A field accepting an age between 18 and 60.

       EQUIVALENCE CLASSES
            < 18        invalid  -> test 10
            18 to 60    valid    -> test 35
            > 60        invalid  -> test 75
            non-numeric invalid  -> test "abc"
            empty       invalid  -> test ""

       BOUNDARY VALUES
            17 , 18 , 19 , 59 , 60 , 61

       The value 18 is what exposes  if (age > 18)  written where
       if (age >= 18)  was intended.
    ```

    Advantages
    - The tester needs `no programming knowledge`, so business users can take part.
    - It tests the product `as the user experiences it`.
    - It is independent of the implementation, so tests survive a rewrite of the code.
    - It can be designed as soon as the `SRS` exists, in parallel with coding.
    - It finds `wrong or missing functionality` — which white box testing cannot.

    Disadvantages
    - It cannot tell which parts of the code were `never exercised`, so dead code and untested branches go unnoticed.
    - Without visibility, some cases are `redundant` while others are missed.
    - `Exhaustive` input testing is impossible, so the choice of cases decides how effective it is.
    - It cannot locate the cause of a failure, only its symptom.

    - The contrast to state: `white box` testing works from the code and measures `coverage`, finding logic errors and dead code but never a missing requirement. `Grey box` testing sits between the two, with partial knowledge of the architecture and database, and is used heavily in security and API testing. Black box and white box are complements, not alternatives.

31. **Briefly describe Unit testing, Smoke testing and Stress testing in software engineering.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*

    Answer: Unit testing
    - `Unit testing` tests the `smallest testable piece` of software — one function, method or class — `in isolation`.
    ```
       Who   : the DEVELOPER who wrote it
       When  : as soon as the unit is coded, BEFORE integration
       Type  : WHITE BOX - the code is visible
       Aim   : find logic errors, wrong calculations and bad boundary
               handling at the cheapest possible point
    ```
    ```
       Neighbours are FAKED so the unit stands alone :
            DRIVER - a dummy CALLER that invokes the unit
            STUB   - a dummy CALLEE returning a fixed value

       Example : calculateInterest(1000 , 5 , 1) -> expect 50
                 calculateInterest(1000 , 0 , 1) -> expect 0
                 calculateInterest(-1000 , 5 , 1) -> expect an error
    ```
    - Frameworks: `JUnit`, `NUnit`, `pytest`, `Google Test`. The automated suite becomes the `regression` check re-run on every build, and it is what makes `refactoring` safe.

    Smoke testing
    - `Smoke testing` is a quick, shallow check that a new build is `stable enough to be worth testing at all`. It runs only the few most critical paths.
    ```
       Also called BUILD VERIFICATION TESTING.

       Characteristics : WIDE but SHALLOW - it touches many features,
            each only superficially. It takes minutes, not hours.
       Run on          : EVERY new build, before detailed testing.
       If it FAILS     : the build is REJECTED and sent back to the
            developers. No further testing is attempted, because
            detailed testing of a broken build wastes the whole team's
            day.

       Example, for a banking application :
            does the application start ?
            can a user log in ?
            does the account list load ?
            can one transaction be posted ?
    ```
    ```
       SMOKE vs SANITY - the pair examiners test

         SMOKE  : WIDE and SHALLOW. Does the whole build work at all ?
                  Run on EVERY build.
         SANITY : NARROW and DEEP. Does this ONE fixed defect actually
                  work now ? Run after a small change.
    ```
    - The name comes from hardware: switch the board on and see whether smoke comes out. If it does, there is no point measuring anything else.

    Stress testing
    - `Stress testing` pushes the system `beyond its specified limits` to find its breaking point and to check that it fails `safely` and `recovers`.
    ```
       It answers three questions :
            WHERE does it break ?
            HOW does it break - gracefully, or with data corruption ?
            Does it RECOVER when the load is removed ?

       Methods : far more concurrent users than specified ; huge data
            volumes ; starving it of memory or disk ; cutting the
            network or the database mid-transaction.

       Example : a system specified for 1000 concurrent users is
            driven to 2000 , 5000 , 10000. The findings wanted are
            that it degrades gradually, shows a clear error rather
            than corrupting data, and returns to normal once the load
            drops.
    ```
    ```
       LOAD vs STRESS - the other pair examiners test

         LOAD   : the EXPECTED load. Does it MEET the target ?
         STRESS : BEYOND the limit. Does it FAIL GRACEFULLY ?

       Both are NON-FUNCTIONAL tests.
    ```
    - How the three relate in a project's flow: `unit tests` run on every commit, a `smoke test` gates every build, and `stress testing` is done once the system is functionally stable — there is no value in stress testing a build that cannot pass its smoke test.

32. **Write different between Alpha and Beta testing.** *[BREB Assistant General Manager (IT) 2021 compact it 933-934 (ET: N/A)]*

    Answer: Difference between alpha and beta testing

    | Point | Alpha testing | Beta testing |
    |---|---|---|
    | Where | At the `developer's` site | At the `user's` own site |
    | Who tests | Internal QA staff, other departments, a few invited customers | `Real external users` |
    | Environment | `Controlled`, lab-like | `Real`, uncontrolled |
    | Developer present | `Yes`, watching | `No` |
    | Order | `First` | `After` alpha |
    | Testing type | White box + black box | `Black box` only |
    | Stability of the build | Unstable, many known defects | Fairly stable |
    | Defect fixing | Often `immediate`, on the spot | Collected and fixed in a later build |
    | Purpose | Catch defects before outsiders see the product | Find defects that only `real use` produces |
    | Reliability and usability | Not the main focus | `Checked in depth` |
    | Duration | Longer, several cycles | A few weeks of real use |
    | Also called | In-house acceptance testing | Field testing, pre-release testing |

    Alpha testing
    ```
       Done at the DEVELOPER'S site, in a controlled environment, by
       internal staff and sometimes selected customers. The developers
       WATCH, so a defect can be diagnosed and fixed at once.

       BOTH white box and black box techniques are used, because the
       testers have access to the code.

       Usually run in TWO CYCLES :
            cycle 1 - the QA team runs the full scenarios
            cycle 2 - after fixes, business users exercise it as they
                 actually would
    ```

    Beta testing
    ```
       Done at the USER'S site, by REAL users, in the REAL
       environment, with NO developer present. Users report problems
       back through a feedback channel.

       Only BLACK BOX testing is possible.

       This is where the product meets conditions the developers could
       never reproduce : slow networks, old browsers, unusual data,
       and users who do things nobody anticipated.
    ```

    The sequence
    ```mermaid
    flowchart LR
        A[System testing] --> B[ALPHA: developer site, internal]
        B --> C[Fix defects]
        C --> D[BETA: user site, real users]
        D --> E[Fix and finalise]
        E --> F[Release]
    ```
    - The essential contrast: `alpha testing is controlled and observed; beta testing is uncontrolled and unobserved`. That is precisely why both are needed — alpha finds the defects that careful, systematic testing reveals, and beta finds the ones that only real users in real conditions can produce.
    - Both are forms of `acceptance testing`, the last level before release. Some organisations add a `gamma` stage — a final check on the release candidate in which no new features are added and only critical defects are fixed.

33. **Testing is an activity that is performed to verify correct behavior of a program. Testing should be conducted in all the stages of program development. Describe different types of tests conducted in the implementation stage.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 980 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The `implementation stage` is where code is written, so the tests conducted there are the ones a developer runs on code as it is produced — before the system as a whole exists.

    The tests conducted in the implementation stage

    1. Unit testing
    ```
       Tests the smallest testable piece - one function, method or
       class - IN ISOLATION.

       Who  : the DEVELOPER who wrote it
       Type : WHITE BOX - the code is visible
       Aim  : logic errors, wrong calculations, bad boundaries

       Neighbours are FAKED :
            DRIVER - a dummy CALLER that invokes the unit
            STUB   - a dummy CALLEE returning a fixed value

       Example : calculateInterest(1000 , 5 , 1) -> expect 50
                 also rate = 0 , negative principal , boundary values
    ```

    2. Static testing — reviews and inspections
    ```
       The code is NOT executed ; it is READ.

         DESK CHECKING   the author re-reads their own code
         PEER REVIEW     a colleague reads it
         WALKTHROUGH     the author explains it to reviewers
         INSPECTION      the most formal - moderator, checklist,
                         recorded defects and metrics
         STATIC ANALYSIS a tool detects uninitialised variables,
                         unreachable code, type mismatches, memory
                         leaks

       Reviews find defects at the LOWEST cost of any technique,
       because nothing has to be built or run first.
    ```

    3. Integration testing
    ```
       Once several modules are coded, they are combined and the
       INTERFACES between them are tested - wrong data format,
       mismatched parameters, wrong units.

       APPROACHES
         BIG BANG   everything at once ; a failure gives no clue where
         TOP-DOWN   start at the top ; needs STUBS
         BOTTOM-UP  start at the bottom ; needs DRIVERS
         SANDWICH   both directions at once
    ```

    4. Regression testing
    ```
       Every time a module is changed or a defect fixed, the EXISTING
       tests are re-run to prove nothing else broke. This is the test
       that makes continuous change safe, and it is the reason unit
       tests are automated.
    ```

    5. Smoke testing
    ```
       A quick, shallow check that each new build is stable enough to
       be worth testing at all - WIDE but SHALLOW. If it fails the
       build is rejected and no detailed testing is attempted.
    ```

    6. Debugging — the related activity
    ```
       TESTING finds that a failure exists.
       DEBUGGING locates its CAUSE in the code and corrects it.
       They are different activities : testing is planned and
       systematic, debugging is investigative.
    ```

    Where these sit relative to the later stages
    ```mermaid
    flowchart LR
        A[IMPLEMENTATION<br/>unit, static, integration,<br/>regression, smoke] --> B[SYSTEM TESTING<br/>whole product vs SRS]
        B --> C[ACCEPTANCE<br/>alpha, beta, UAT]
        C --> D[MAINTENANCE<br/>regression after each change]
    ```
    ```
       IMPLEMENTATION stage : UNIT , STATIC , INTEGRATION , REGRESSION ,
            SMOKE - all by DEVELOPERS, all WHITE or GREY box.
       TESTING stage        : SYSTEM and NON-FUNCTIONAL testing - by
            the QA team, BLACK box.
       ACCEPTANCE stage     : ALPHA , BETA , UAT - by the CUSTOMER.
    ```
    - Why the implementation stage carries so much of the testing burden: a defect found by a unit test costs about a tenth of what the same defect costs in system testing and a hundredth of what it costs after release. Testing at the point of writing is not an extra activity — it is the cheapest place the work can possibly be done.

34. **How would you test an ATM in a banking system?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1052 (ET: BUET)]*
   a) Withdrawing money less than the account balance
   b) Withdrawing money greater than the account balance
   c) Withdrawing money equal to the account balance
   d) Withdrawing money from an ATM and from the internet at the same time
   e) Withdrawing money when the connection to the bank's network is lost
   f) Withdrawing money from multiple ATMs simultaneously
   g) Check the balance available
   h) Verify the error message by entering an incorrect PIN
   i) Try to enter invalid pin more than 3 times and see if the account gets locked.
   j) Verify how much time the system takes to log out.

    Answer: Testing an ATM in a banking system covers `functional`, `non-functional`, `hardware` and `security` aspects. The approach below is organised by test level.

    1. Unit testing
    ```
       Each module tested alone :
            PIN validation , amount validation , balance calculation ,
            denomination breakdown , receipt formatting.

       Example : withdraw(balance=1000 , amount=500) -> new balance 500
                 withdraw(balance=1000 , amount=2000) -> error
    ```

    2. Integration testing
    ```
       ATM  <->  card reader , keypad , cash dispenser , printer
       ATM  <->  bank SWITCH  <->  CORE BANKING SYSTEM
       ATM  <->  receipt printer and journal log

       The critical case : is the amount debited from the account
       EXACTLY ONCE for one dispense ? A double debit or a dispense
       without a debit is the worst possible defect.
    ```

    3. Functional testing — the main scenarios
    ```
       CARD HANDLING
         valid card , expired card , blocked card , damaged magnetic
         stripe , foreign bank card , card inserted the wrong way,
         card left in the machine (retain after timeout)

       PIN
         correct PIN -> proceed
         wrong PIN once , twice , THREE times -> card BLOCKED
         PIN entry timeout
         PIN change function

       WITHDRAWAL
         amount within balance          -> success
         amount above balance           -> "Insufficient balance"
         amount above the DAILY LIMIT   -> rejected
         amount not a multiple of 500   -> rejected
         amount = 0 or negative         -> rejected
         ATM has insufficient CASH      -> clear message, no debit
         exact-denomination cases : 500 , 1000 , 4500 , 20000

       OTHER TRANSACTIONS
         balance enquiry , mini statement , fund transfer , deposit ,
         bill payment , PIN change , cancel at every step
    ```

    4. Boundary value and equivalence testing
    ```
       Daily limit 50,000 ; per-transaction limit 20,000 ;
       multiples of 500.

         BOUNDARY : 499 , 500 , 501 , 19,999 , 20,000 , 20,001
                    49,500 , 50,000 , 50,500
         CLASSES  : below minimum , valid , above per-transaction
                    limit , above daily limit , non-multiple
    ```

    5. Negative and interruption testing — where ATMs actually fail
    ```
       POWER FAILURE mid-transaction, after debit but before dispense
            -> the transaction must be REVERSED automatically.
       NETWORK LOSS to the core banking system mid-transaction
            -> no debit without a dispense.
       CASH JAM in the dispenser
            -> the amount must be re-credited.
       USER WALKS AWAY leaving cash or card
            -> retract and log.
       Two withdrawals from the same account at two ATMs at the SAME
            MOMENT
            -> a CONCURRENCY test ; the balance must not go negative.
    ```
    - These are the cases that matter most, and they are all `negative` paths. An ATM that handles the happy path perfectly and mishandles a power cut is worse than useless.

    6. Non-functional testing
    ```
       PERFORMANCE  response time per transaction under 5 seconds
       LOAD         many ATMs hitting the switch at once - salary day
       STRESS       beyond the specified transaction rate
       RECOVERY     restart after power loss ; is the journal intact ?
       USABILITY    screen readability, clear prompts, Bangla and
                    English, accessibility for blind users
       COMPATIBILITY  cards from other banks, VISA and Mastercard
                    networks
    ```

    7. Security testing
    ```
       PIN must be ENCRYPTED end to end and never appear in a log or
            on the receipt
       the receipt must show a MASKED card number
       physical security : card skimmer detection , camera , tamper
            alarm
       test for brute-force PIN attempts , card cloning , man-in-the-
            middle on the network link
       AUDIT TRAIL : every transaction logged with time, ATM ID, card
            number and amount
    ```

    8. Acceptance and regression testing
    ```
       UAT   : bank staff run real business scenarios on a live-like
               ATM before rollout.
       PILOT : one branch first, then the network.
       REGRESSION : the full suite re-run after every software update,
               because an ATM update that breaks reversal handling
               costs real money.
    ```
    - The single principle worth stating: for an ATM, the test design concentrates on `what happens when something goes wrong halfway through`. Money and card are physical objects — an interrupted transaction must leave the account, the cash drawer and the journal in a `consistent` state, and proving that is the heart of ATM testing.

35. **Write code to test a sorting algorithm of array?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1056 (ET: AUST)]*

    Answer: The test program below drives a sorting function and checks `two properties` on every case: the output is in order, and it is a permutation of the input. Checking only the order is not enough — a function that returns all zeros is "sorted" but wrong.

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    /* the function under test */
    void bubbleSort(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - 1 - i; j++)
                if (a[j] > a[j + 1]) {
                    int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t;
                }
    }

    /* check 1 : is the array in non-decreasing order ? */
    int isSorted(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            if (a[i] > a[i + 1]) return 0;
        return 1;
    }

    int cmp(const void *x, const void *y) {
        int a = *(int *)x, b = *(int *)y;
        return (a > b) - (a < b);        /* no subtraction : avoids overflow */
    }

    /* check 2 : are the same elements still present ? */
    int isPermutation(int a[], int b[], int n) {
        int *p = malloc(n * sizeof(int)), *q = malloc(n * sizeof(int));
        memcpy(p, a, n * sizeof(int));
        memcpy(q, b, n * sizeof(int));
        qsort(p, n, sizeof(int), cmp);
        qsort(q, n, sizeof(int), cmp);
        int ok = memcmp(p, q, n * sizeof(int)) == 0;
        free(p); free(q);
        return ok;
    }

    int runTest(char *name, int in[], int n) {
        int *copy = malloc(n * sizeof(int) + 1);
        memcpy(copy, in, n * sizeof(int));
        bubbleSort(copy, n);
        int pass = isSorted(copy, n) && isPermutation(in, copy, n);
        printf("%-22s : %s\n", name, pass ? "PASS" : "FAIL");
        free(copy);
        return pass;
    }

    int main(void) {
        int t1[] = {5, 2, 9, 1, 7};
        int t2[] = {1, 2, 3, 4, 5};
        int t3[] = {5, 4, 3, 2, 1};
        int t4[] = {4, 4, 4, 4};
        int t5[] = {42};
        int t6[] = {-3, 0, -7, 5};
        int t7[] = {2147483647, -2147483648, 0};
        int total = 0, pass = 0;

        pass += runTest("random order",      t1, 5); total++;
        pass += runTest("already sorted",    t2, 5); total++;
        pass += runTest("reverse sorted",    t3, 5); total++;
        pass += runTest("all duplicates",    t4, 4); total++;
        pass += runTest("single element",    t5, 1); total++;
        pass += runTest("negative numbers",  t6, 4); total++;
        pass += runTest("INT_MIN / INT_MAX", t7, 3); total++;
        pass += runTest("empty array",       t1, 0); total++;

        printf("\n%d of %d tests passed\n", pass, total);
        return pass == total ? 0 : 1;
    }
    ```

    Output when run
    ```
       random order           : PASS
       already sorted         : PASS
       reverse sorted         : PASS
       all duplicates         : PASS
       single element         : PASS
       negative numbers       : PASS
       INT_MIN / INT_MAX      : PASS
       empty array            : PASS

       8 of 8 tests passed
    ```

    Why these particular test cases
    ```
       random order      the ordinary case
       already sorted    a badly written loop can UNDO a sorted array ;
                         it is also the best case for detecting an
                         infinite loop
       reverse sorted    the WORST case - every element must move
       all duplicates    exposes  a[j] >= a[j+1]  written where
                         a[j] > a[j+1]  was meant (breaks stability,
                         and can loop forever)
       single element    n = 1 : the loop must not run at all
       empty array       n = 0 : the commonest crash, because
                         n - 1 becomes -1
       negative numbers  exposes code that assumes non-negative values
       INT_MIN / INT_MAX exposes any comparator written as  a - b ,
                         which OVERFLOWS
    ```
    - The two properties checked are what make this a real test rather than an eyeball check. `isSorted` alone would pass a function that returns `{0,0,0,0,0}`; `isPermutation` alone would pass a function that does nothing. Both together are necessary and sufficient.
    - One further check worth adding for a `stable` sort: sort an array of records by one key and verify that records with equal keys keep their original relative order. Bubble sort with a strict `>` comparison is stable; changing it to `>=` silently breaks that, and only such a test would catch it.

36. **How would you test an ATM in a distributed system?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1058 (ET: AUST)]*

    Answer: A distributed ATM system has one extra problem an isolated ATM does not: `many ATMs, one shared account balance, across an unreliable network`. So the testing has all the layers of ordinary ATM testing plus a set of distributed-system concerns.

    The architecture being tested
    ```
       +--------+  +--------+  +--------+
       | ATM 1  |  | ATM 2  |  | ATM 3  |   (different branches / cities)
       +--------+  +--------+  +--------+
            \          |           /
             \         |          /
              +---- NETWORK -----+
                      |
              +----------------+
              |  BANK SWITCH   |   (routes, and talks to VISA / NPSB)
              +----------------+
                      |
              +----------------+
              | CORE BANKING   |   (the authoritative balance)
              |   DATABASE     |
              +----------------+
    ```

    1. Standard ATM functional testing
    ```
       Card handling : valid , expired , blocked , damaged stripe ,
            foreign bank card
       PIN           : correct , wrong three times -> BLOCKED , timeout
       Withdrawal    : within balance , above balance , above daily
            limit , not a multiple of 500 , zero , negative , ATM out
            of cash
       Others        : balance enquiry , mini statement , transfer ,
            deposit , PIN change , cancel at every step
       BOUNDARY      : 499 / 500 / 501 , 19,999 / 20,000 / 20,001 ,
            49,500 / 50,000 / 50,500
    ```

    2. Concurrency — the central distributed test
    ```
       THE CRITICAL CASE

       Balance 1000. Two withdrawals of 800 each, from TWO DIFFERENT
       ATMs, at the SAME INSTANT.

         WRONG behaviour : both read 1000 , both succeed , balance
              becomes -600. The bank has lost 600.
         CORRECT behaviour : the core banking database SERIALISES
              them - one succeeds, the other gets "Insufficient
              balance".

       This must be tested with a script that fires both requests
       simultaneously, not one after the other. It is a RACE
       CONDITION, and it is exactly what row-level LOCKING and ACID
       TRANSACTIONS exist to prevent.
    ```
    - Related cases: the same card used at two ATMs at once; a withdrawal at one ATM while a transfer from the same account is in flight; and the `daily limit` enforced correctly when withdrawals happen at several ATMs on the same day.

    3. Network failure and partition testing
    ```
       NETWORK LOST after the debit but BEFORE the dispense
            -> the transaction must be REVERSED automatically. Test
               that the reversal actually arrives and is applied ONCE.

       NETWORK LOST after the dispense but before the confirmation
            -> the debit must NOT be reversed. Money left the machine.

       TIMEOUT of the switch response
            -> the ATM must not guess. It must either wait for a
               definite answer or fail closed.

       DUPLICATE MESSAGE - the switch retries a request the core
            already processed
            -> IDEMPOTENCY test. The same transaction reference must
               debit the account ONCE, however many times it arrives.

       NETWORK PARTITION - a branch is cut off from the core
            -> does the ATM go OFFLINE and refuse service, or does it
               serve from stale local data ? Serving from stale data
               is how double-spending happens.
    ```
    - These reversal, idempotency and partition cases are the ones that distinguish distributed ATM testing from single-ATM testing, and they are where real money is lost.

    4. Consistency and reconciliation
    ```
       END-OF-DAY RECONCILIATION
            cash dispensed by the machine = sum of debits in the core
            banking database = the ATM journal total.
            Any mismatch is a defect, however small.

       Test with deliberately injected failures - power cuts, jams,
       network drops - and then verify the three totals still agree.
    ```

    5. Non-functional testing
    ```
       LOAD        many ATMs hitting the switch at once - salary day,
                   Eid, month end
       STRESS      beyond the specified transaction rate
       FAILOVER    kill the primary switch or database - does the
                   standby take over, and is any transaction lost ?
       LATENCY     response under 5 seconds even from a remote branch
                   on a slow link
       RECOVERY    restart after power loss ; is the journal intact ?
       SCALABILITY add more ATMs - does throughput scale ?
    ```

    6. Security testing
    ```
       PIN ENCRYPTED end to end ; never in a log, never on the receipt
       card number MASKED on the receipt
       the ATM-to-switch link ENCRYPTED - test for a man-in-the-middle
       brute-force PIN attempts blocked
       card skimming and cloning detection
       AUDIT TRAIL : every transaction logged with time, ATM ID,
            masked card number and amount
    ```

    7. Test environment
    ```
       ATM SIMULATORS are essential. Real ATMs cannot be used to test
       1000 concurrent withdrawals, and cannot safely be power-cut
       repeatedly. Simulators reproduce the card reader, dispenser and
       network so the failure cases can be driven deliberately.

       A LIVE-LIKE test core banking database with realistic data
       volumes is equally necessary - concurrency defects do not
       appear on a database with ten rows.
    ```
    - The principle that governs all of it: in a distributed system the interesting question is never "does a withdrawal work" but "`what state is everything left in when the network fails halfway through`". Every important test case therefore injects a failure at a specific point and then verifies that the account, the cash drawer and the journal still agree.

37. **What is Alpha and Beta testing?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1123 (ET: BREB)]*

    Answer: Alpha testing
    - `Alpha testing` is the first stage of `acceptance testing`, carried out at the `developer's own site` by internal staff and sometimes a few invited customers, with the developers `present and watching`.
    ```
       Where   : at the DEVELOPER'S site , a controlled environment
       Who     : internal QA staff, other departments, selected
                 customers
       Present : the DEVELOPERS watch and can fix defects on the spot
       Type    : BOTH white box and black box, since the code is
                 available
       State   : the build is feature-complete but still unstable
       Purpose : catch the defects that would embarrass the company if
                 an outsider found them
    ```
    - It is usually run in `two cycles`: the QA team tests the build, defects are fixed, and then business users exercise it as they actually would.

    Beta testing
    - `Beta testing` is the second stage. A near-final build is released to a limited number of `real users outside the organisation`, who use it in their `own environment` with `no developer present`.
    ```
       Where   : at the USER'S site , the REAL environment
       Who     : REAL external users - a public or closed beta
       Present : NO developer
       Type    : BLACK BOX only - users cannot see the code
       State   : fairly stable ; most major defects already fixed
       Purpose : find the defects that only real conditions produce,
                 and collect feedback before general release
    ```

    Comparison

    | Point | Alpha testing | Beta testing |
    |---|---|---|
    | Where | `Developer's` site | `User's` own site |
    | Who tests | Internal staff, invited customers | `Real external users` |
    | Environment | `Controlled` | `Real`, uncontrolled |
    | Developer present | `Yes` | `No` |
    | Order | `First` | After alpha |
    | Testing type | White box + black box | `Black box` only |
    | Defect fixing | Often immediate | In a later build |
    | Also called | In-house acceptance testing | Field testing, pre-release |

    The sequence
    ```mermaid
    flowchart LR
        A[System testing] --> B[ALPHA: internal, developer site]
        B --> C[Fix defects]
        C --> D[BETA: real users, own site]
        D --> E[Fix and finalise]
        E --> F[Release]
    ```
    - The essential contrast: `alpha testing is controlled and observed; beta testing is uncontrolled and unobserved`. That is why both are needed — alpha finds what systematic testing reveals, and beta finds what only real users, on real networks, with real data, and behaving unpredictably, can produce.

38. **A program sorts an array of integer. Write down the code that tests the sorting algorithm of written in a program.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1163-1164 (ET: N/A)]*

    Answer: The test program below drives the sorting function and checks `two properties` on every case: the output is in order, and it contains exactly the same elements as the input. Checking the order alone is not enough — a function returning all zeros is "sorted" but wrong.

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    /* the function under test */
    void sortArray(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - 1 - i; j++)
                if (a[j] > a[j + 1]) {
                    int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t;
                }
    }

    /* property 1 : non-decreasing order */
    int isSorted(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            if (a[i] > a[i + 1]) return 0;
        return 1;
    }

    int cmp(const void *x, const void *y) {
        int a = *(int *)x, b = *(int *)y;
        return (a > b) - (a < b);      /* not a - b : that overflows */
    }

    /* property 2 : same elements, same multiplicities */
    int isPermutation(int in[], int out[], int n) {
        int *p = malloc(n * sizeof(int)), *q = malloc(n * sizeof(int));
        memcpy(p, in,  n * sizeof(int));
        memcpy(q, out, n * sizeof(int));
        qsort(p, n, sizeof(int), cmp);
        qsort(q, n, sizeof(int), cmp);
        int ok = memcmp(p, q, n * sizeof(int)) == 0;
        free(p); free(q);
        return ok;
    }

    int runTest(char *name, int in[], int n) {
        int *copy = malloc(n * sizeof(int) + 1);
        memcpy(copy, in, n * sizeof(int));
        sortArray(copy, n);
        int pass = isSorted(copy, n) && isPermutation(in, copy, n);
        printf("%-22s : %s\n", name, pass ? "PASS" : "FAIL");
        free(copy);
        return pass;
    }

    int main(void) {
        int t1[] = {8, 3, 5, 1, 9, 2};
        int t2[] = {1, 2, 3, 4, 5};
        int t3[] = {9, 7, 5, 3, 1};
        int t4[] = {6, 6, 6, 6};
        int t5[] = {42};
        int t6[] = {-4, 0, -9, 3};
        int t7[] = {2147483647, -2147483648, 0};
        int total = 0, pass = 0;

        pass += runTest("random order",      t1, 6); total++;
        pass += runTest("already sorted",    t2, 5); total++;
        pass += runTest("reverse sorted",    t3, 5); total++;
        pass += runTest("all duplicates",    t4, 4); total++;
        pass += runTest("single element",    t5, 1); total++;
        pass += runTest("negative numbers",  t6, 4); total++;
        pass += runTest("INT_MIN / INT_MAX", t7, 3); total++;
        pass += runTest("empty array",       t1, 0); total++;

        printf("\n%d of %d tests passed\n", pass, total);
        return pass == total ? 0 : 1;
    }
    ```

    Output when run
    ```
       random order           : PASS
       already sorted         : PASS
       reverse sorted         : PASS
       all duplicates         : PASS
       single element         : PASS
       negative numbers       : PASS
       INT_MIN / INT_MAX      : PASS
       empty array            : PASS

       8 of 8 tests passed
    ```

    Why each test case is there
    ```
       random order      the ordinary case
       already sorted    a badly written loop can UNDO a sorted array
       reverse sorted    the WORST case - every element must move
       all duplicates    exposes  >=  written where  >  was meant
       single element    n = 1 : the loop must not execute
       empty array       n = 0 : the commonest crash, because n-1 = -1
       negative numbers  exposes code assuming non-negative values
       INT_MIN / INT_MAX exposes a comparator written as  a - b
    ```
    - Both properties are needed and together they are sufficient: `isSorted` alone would accept a function that returns all zeros, and `isPermutation` alone would accept a function that does nothing. Neither check on its own is a test.
    - For a `stable` sort, add one more case: sort records by a single key and verify that records with equal keys keep their original relative order. Changing the comparison from `>` to `>=` silently breaks stability, and only such a test detects it.

39. **Difference between black box and white box testing.** *[Palli Sanchay Bank Programmer 2018 compact it 1172 (ET: N/A)]*, *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

    Answer: Difference between black box and white box testing

    | Point | Black box testing | White box testing |
    |---|---|---|
    | Knowledge of code | `None` — the box is closed | `Full` — the source is read |
    | Based on | The `SRS` / requirements | The `code` structure |
    | Also called | Functional, behavioural, closed box | `Structural`, glass box, clear box |
    | Who does it | `Testers` | `Developers` |
    | Applied at | System, acceptance testing | `Unit`, integration testing |
    | Programming skill | Not needed | `Required` |
    | Finds | Wrong or missing functionality | Logic errors, dead code, untested branches |
    | Cannot find | Untested internal paths, dead code | `Missing requirements` |
    | Test design | Equivalence partitioning, boundary values | Statement, branch, path coverage |
    | Design effort | Lower | Higher — the code must be studied |
    | "Done" measured by | All requirements exercised | A `coverage` percentage |

    Black box
    ```
            input ---->  [ ??? ]  ----> output
                       the box is CLOSED

       TECHNIQUES
         EQUIVALENCE PARTITIONING - group inputs that behave alike ;
              test ONE value from each class
         BOUNDARY VALUE ANALYSIS  - test at and around the edges
         DECISION TABLE   - all combinations of business rules
         STATE TRANSITION - legal and illegal state changes
         ERROR GUESSING   - experience-based cases

       Example : a field accepting an age of 18 to 60
            CLASSES  : < 18 invalid , 18-60 valid , > 60 invalid
            BOUNDARY : 17 , 18 , 19 , 59 , 60 , 61
    ```

    White box
    ```
       The tester READS the code :

            if (a > 0 && b > 0)  x = 1;
            else                 x = 2;

       STATEMENT coverage : 1 test  (a=1 , b=1)
       BRANCH    coverage : 2 tests (1,1) and (1,-1)
       CONDITION coverage : cases making a>0 both T and F, and
                            b>0 both T and F

       COVERAGE CRITERIA
         STATEMENT  every line executed once
         BRANCH     every if takes both paths
         PATH       every route through the code
         LOOP       0 iterations , 1 , and many
    ```

    - The decisive point: `white box testing cannot detect a missing requirement` — a feature never coded has no code to cover, so even full coverage says nothing about it. `Black box testing cannot detect dead code` or an unexercised branch. They are complements, not alternatives; `grey box` testing, with partial knowledge of the architecture and database, sits between them and is used heavily in security and API testing.

40. **A program sorts an array of integer. Write down the code that tests the sorting algorithm of written** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

    Answer: The test program below drives the sorting function and checks `two properties` on every case: the result is in order, and it contains exactly the same elements as the input. Order alone is not enough — a function that returns all zeros is "sorted" but wrong.

    ```c
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>

    /* the function under test */
    void sortArray(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - 1 - i; j++)
                if (a[j] > a[j + 1]) {
                    int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t;
                }
    }

    /* property 1 : non-decreasing order */
    int isSorted(int a[], int n) {
        for (int i = 0; i < n - 1; i++)
            if (a[i] > a[i + 1]) return 0;
        return 1;
    }

    int cmp(const void *x, const void *y) {
        int a = *(int *)x, b = *(int *)y;
        return (a > b) - (a < b);      /* not a - b : that overflows */
    }

    /* property 2 : same elements, same multiplicities */
    int isPermutation(int in[], int out[], int n) {
        int *p = malloc(n * sizeof(int)), *q = malloc(n * sizeof(int));
        memcpy(p, in,  n * sizeof(int));
        memcpy(q, out, n * sizeof(int));
        qsort(p, n, sizeof(int), cmp);
        qsort(q, n, sizeof(int), cmp);
        int ok = memcmp(p, q, n * sizeof(int)) == 0;
        free(p); free(q);
        return ok;
    }

    int runTest(char *name, int in[], int n) {
        int *copy = malloc(n * sizeof(int) + 1);
        memcpy(copy, in, n * sizeof(int));
        sortArray(copy, n);
        int pass = isSorted(copy, n) && isPermutation(in, copy, n);
        printf("%-22s : %s\n", name, pass ? "PASS" : "FAIL");
        free(copy);
        return pass;
    }

    int main(void) {
        int t1[] = {7, 2, 8, 1, 4};
        int t2[] = {1, 2, 3, 4, 5};
        int t3[] = {5, 4, 3, 2, 1};
        int t4[] = {3, 3, 3, 3};
        int t5[] = {99};
        int t6[] = {-5, 0, -1, 8};
        int t7[] = {2147483647, -2147483648, 0};
        int total = 0, pass = 0;

        pass += runTest("random order",      t1, 5); total++;
        pass += runTest("already sorted",    t2, 5); total++;
        pass += runTest("reverse sorted",    t3, 5); total++;
        pass += runTest("all duplicates",    t4, 4); total++;
        pass += runTest("single element",    t5, 1); total++;
        pass += runTest("negative numbers",  t6, 4); total++;
        pass += runTest("INT_MIN / INT_MAX", t7, 3); total++;
        pass += runTest("empty array",       t1, 0); total++;

        printf("\n%d of %d tests passed\n", pass, total);
        return pass == total ? 0 : 1;
    }
    ```

    Output when run
    ```
       random order           : PASS
       already sorted         : PASS
       reverse sorted         : PASS
       all duplicates         : PASS
       single element         : PASS
       negative numbers       : PASS
       INT_MIN / INT_MAX      : PASS
       empty array            : PASS

       8 of 8 tests passed
    ```

    Why these test cases
    ```
       random order      the ordinary case
       already sorted    a badly written loop can UNDO a sorted array
       reverse sorted    the WORST case - every element must move
       all duplicates    exposes  >=  written where  >  was meant
       single element    n = 1 : the loop must not execute
       empty array       n = 0 : the commonest crash, since n-1 = -1
       negative numbers  exposes code assuming non-negative values
       INT_MIN / INT_MAX exposes a comparator written as  a - b
    ```
    - The two checks are jointly necessary: `isSorted` alone accepts a function returning all zeros, and `isPermutation` alone accepts a function that does nothing. Either one on its own is not a test.
    - The boundary cases `n = 0` and `n = 1` are the ones that actually find defects in real sorting code, because `n - 1` in the loop bound becomes `-1` when `n` is zero. Any test suite for a sorting routine that omits the empty array is incomplete.

## UML Diagrams (Class, Use Case, Sequence) (14)

1. An e-commerce platform has Customers, Orders, and Payment methods (Credit Card, Mobile Banking). Draw a **Class Diagram** showing attributes, methods, and relationships (inheritance, association). [SO IT 25-07-2026]

2. Draw a Use Case Diagram for an Online Banking System with two actors: Customer and Bank Admin. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. **Draw a class diagram for an E-commerce website where customer can view different products, can pay either by card or cash.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 401 (ET: BUET)]*

4. **Consider the following buy a product description. Customer browses catalog, selects items to buy and then goes to check out. Customer fills in shipping information (address, receive time). System presents full pricing information and customer fills in credit card information. System authorizes purchase, confirms sale and sends confirming email to customer. Draw a use case diagram for the above system.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*

5. **Library management class diagram:** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*

6. **Draw A class diagram. A token-ring based local area network (LAN) is a network consisting of nodes in which network packets are sent around. Every node has a unique name within the network, and refers to its next node. Different kinds of nodes exist: Workstations are originators of messages; servers and printers are network nodes that can receive messages. Packets contain an originator a destination and content, and are sent around on a network. A LAN is a circular configuration of nodes.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*

7. **(খ) একটি লাইব্রেরি ব্যবস্থাপনা সিস্টেম এর জন্যে Use Case Diagram অঙ্কন করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

8. **How do you model the following situation with a UML class diagram the car fleet of a car rental contains multiple cars, one car belongs to exactly one car fleet.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

9. **(ক) Typical web-based login system এর জন্য sequence diagram আঁকুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 778 (ET: N/A)]*

10. **(c) Explain different type of relationships that are used in a UML diagram.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

11. **Write down the use case diagram for ATM.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162-1163 (ET: N/A)]*

12. **Draw UML diagram of composite design pattern.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1215 (ET: N/A)]*

13. **Write the use cases of withdrawing money for ATM card.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1223-1224 (ET: N/A)]*

14. **Draw a high level use case diagram: Use case diagram for a visitor who want to login a page by using username password.** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*

## Software Architecture & Design Patterns (MVC) (13)

1. **Why is it essential to maintain proper MVC structure in web applications?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

2. **What is MVC? Write down the MVC design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*

3. **Name of few architecture in design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 503 (ET: N/A)]*

4. **What is software design pattern? What are the advantages?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 471 (ET: N/A)]*

5. **Define design pattern. Write about singleton pattern.** *[BREB Assistant Programmer 18.02.2023 compact it 469 (ET: N/A)]*

6. **We are going to create a Shape interface and concrete classes implementing the Shape interface. A facade class ShapeMaker is defined as a next step. ShapeMaker class uses the concrete classes to delegate user calls to these classes. FacadePatternDemo, our demo class, will use ShapeMaker class to show the results.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*

7. **Imagine a scenario where new child classes are introduced frequently from a basic class. The method calling sequences for every child class are the same but the implementation is different among the child classes. Here which design pattern would you like to apply? Explain the reasons with examples to support your answer.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

8. **(ক) 'ATM machine' এর Software Structure আঁকুন।** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

9. **(ii) Design the communication for the user login system for an MVC pattern framework.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

10. **(i) MVC framework কী? এর সুবিধাগুলো লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 960 (ET: N/A)]*

11. **MVC framework কী? MVC Framework এর সুবিধাসমূহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

12. **What is MVC? Write down the MVC design pattern.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175-1176 (ET: N/A)]*

13. **Explain desin pattern MVC with appropriate figure.** *[NESCO Manager (Software) 2018 compact it 1209 (ET: N/A)]*

## Software Requirements Engineering (10)

1. What is the difference between functional and non-functional requirements? What is requirement validation? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

2. **Which of the following are not needed in software Requirement Specifications (SRS)?** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*
   * (a) Functional Requirments
   * (b) Non- Functional Requirments
   * (c) Testing Requirments
   * (d) Interface Requirments

3. **(b) Which contents shoud be consider when you setup a new system?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

4. **You have been given a responsibility to elicit requirements from a customer, who tells you that he is too busy to meet with you. What should you do?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

5. **(ক) Software development এর ক্ষেত্রে কত প্রকার requirements পাওয়া যায়। উদাহরণসহ requirements সমূহ লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

6. **(খ) Software Requirement Specification (SRS) বলতে কি বুঝায়? Software Development এর কোন ধাপে SRS তৈরি করা হয়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

7. **Assume that you are going to implement an ecommerce site of “XYZ” company. The CEO of the company is Mr. X. You have to identify the following: (i) Stakeholder (ii) Functional requirements (iii) Non-functional requirements (iv) Deployment requirements** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

8. **Software Requirement Specification (SRS) বলতে কী বোঝেন? Software development -এর কোন স্তরে SRS প্রস্তুত করা হয়?** *[41th BCS 2021 compact it 881 (ET: N/A)]*

9. **(ক) Feasibility Test কী? সফটওয়্যার উন্নয়নে উহার প্রয়োজনীয়তা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

10. **(খ) Feasibility Analysis এর বিভিন্ন ধাপসমূহের সংক্ষিপ্ত বিবরণ দিন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

## Software Project Management & Organization (9)

1. **সংগঠনিক নির্দেশকগুলো কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Which you build about real life software project? What problems you faced during that time and how to solve this?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*

3. **Project management related question (what are the approaches)** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 520 (ET: MIST)]*

4. **(খ) User story ও Product backlog কী?** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

5. **Assume you are a project manager and your job is to develop an application which is similar to what you have developed is past only larger and complex. The customer has documented the requirements clearly. What team structure would you choose in this case and why?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*

6. **a) What is conflict in git? How to resolve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

7. **b) Write down the difference between Patch and Upgrade.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

8. **Qualification of a good team leader.** *[NESCO Manager (Software) 2018 compact it 1208-1209 (ET: N/A)]*

9. **Write down pros and cons over qualification candidate.** *[NESCO Manager (Software) 2018 compact it 1210-1211 (ET: N/A)]*

## Software Design Principles (Coupling & Cohesion) (5)

1. **Write concepts of Coupling and Cohesion with Example?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*

2. **Software design table matching.......** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*

3. **(ক) Modularization কী? উহার সুবিধা সম্পর্কে লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

4. **(খ) Software interface কত প্রকার ও কী কী? Interfacing এর ক্ষেত্রে কী কী error পাওয়া যেতে পারে?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

5. **What is the common mistake of UI design?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

## Software Cost Estimation & Build vs Buy Decisions (4)

1. **If you are CEO of a software company. You need to develop an ERP software from following three options (i) Buy (ii) Build (iii) Open Source Modification**
   * **a) Buy: Buy a software with cost 50 lac.**
   * **b) Building: Developed by developer cost 40 lac for easy process. 50 lac for hard process. Possibility is 30% to develop in easy process.**
   * **c) Open Source and Modification: Buy and small modifications cost 30 lac, for large modifications cost 50 lac. Possibility is 80% for large.**
   **What way you choose and why? Explain with calculation.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 292 (ET: BUET)]*

2. **Given the following values, compute function point when all complexity adjustment factor (CAF) and weighting factors are average.**
   * **User Input = 50**
   * **User Output = 40**
   * **User Inquiries = 35**
   * **User Files = 6**
   * **External Interface = 4** *[Combined Bank Assistant Programmer 09.06.2023 compact it 492 (ET: N/A)]*

3. **Your company earn a contract to develop a system for a government agency. The project team is considering whether to build the system from scratch, or reuse existing partial-experience components, or buy an available software product and modify it to meet the requirement. As analyst you have made a decision tree as a figure.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

4. **Which factors are to be consider as software pricing?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*

## IT Governance, Audit & Risk Management (4)

1. **Difference between: Policy, Guideline, Procedure; why auditor must focus on control as a system? Explain four types of risks auditor faces, Explain each of theme.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 310 (ET: BIBM)]*

2. **A bank has association with two different service providers as their payment gateways. The bank hires Mr. X to audit the payment gateway based on risk and threat detection. Which possible scenarios Mr. X will face?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 443 (ET: BIBM)]*

3. **(ক) Software risk কত প্রকার ও কী কী? Risk management process চিত্রের মাধ্যমে বুঝিয়ে লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*

4. **Draw risk analysis digram.** *[NESCO Manager (Software) 2018 compact it 1210 (ET: N/A)]*

## Data Flow Diagrams (DFD) (2)

1. **(ক) Data Flow diagram (DFD) কী? DFD- তে কী কী Symbols ব্যবহার করা হয়?** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

2. **১ জন ব্যক্তি ১টি Bank Account খোলার জন্য একটি form fillup করেন। এরপর তাতে Manager স্বাক্ষর করেন। এবার উক্ত Account-এ ঐ ব্যক্তি কিছু টাকা Deposit করলে Account সচল হয়। এই Process টি DFD এর মাধ্যমে প্রকাশ করুন।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

## Code Smells & Refactoring (2)

1. **Give examples of the following code smells:** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1366 (ET: BUET)]*
   * **(a) Feature envy**
   * **(b) Dead code**
   * **(c) Duplicate Code**
   * **(d) Shotgun surgery.**

2. **What is reverse engineering and forward engineering?** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 860-861 (ET: N/A)]*

## Open Source Software & Licensing (2)

1. **Write down the advantages and disadvantages of Open source software with example.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 549 (ET: BIBM)]*

2. **Open source এবং Proprietary Software -এর মধ্যে পার্থক্য লিখুন। একটি Open source এবং একটি Proprietary Operating system এর উদাহরণ দিন।** *[41th BCS 2021 compact it 881-882 (ET: N/A)]*

## CI/CD & DevOps Methodologies (1)

1. **What is CI/DI development model?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

## UI/UX Design (1)

1. **What is UI/UX? What is the difference between them?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1123-1124 (ET: BREB)]*
