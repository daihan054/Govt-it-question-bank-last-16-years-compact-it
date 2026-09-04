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

   Answer: Class diagram
   ```mermaid
   classDiagram
       class Customer {
           -int customerId
           -String name
           -String email
           +register()
           +login()
           +placeOrder()
       }
       class Order {
           -int orderId
           -Date orderDate
           -double totalAmount
           -String status
           +calculateTotal()
           +cancelOrder()
       }
       class PaymentMethod {
           <<abstract>>
           -int paymentId
           -double amount
           +pay()
           +refund()
       }
       class CreditCard {
           -String cardNumber
           -Date expiryDate
           -String cvv
           +pay()
           +validateCard()
       }
       class MobileBanking {
           -String mobileNumber
           -String provider
           +pay()
           +sendOtp()
       }
       Customer "1" --> "0..*" Order : places
       Order "1" --> "1" PaymentMethod : paid by
       PaymentMethod <|-- CreditCard
       PaymentMethod <|-- MobileBanking
   ```
   ```
      +---------------------+          +---------------------+
      |      Customer       |  1    0..*|       Order        |
      +---------------------+----------+---------------------+
      | -customerId : int   |  places  | -orderId : int      |
      | -name : String      |          | -orderDate : Date   |
      | -email : String     |          | -totalAmount:double |
      +---------------------+          | -status : String    |
      | +register()         |          +---------------------+
      | +login()            |          | +calculateTotal()   |
      | +placeOrder()       |          | +cancelOrder()      |
      +---------------------+          +---------------------+
                                                 | 1
                                                 | paid by
                                                 | 1
                                       +---------------------+
                                       |  PaymentMethod      |
                                       |   {abstract}        |
                                       +---------------------+
                                       | -paymentId : int    |
                                       | -amount : double    |
                                       +---------------------+
                                       | +pay()              |
                                       | +refund()           |
                                       +---------------------+
                                                /_\
                                                 |  inheritance
                                       +---------+---------+
                                       |                   |
                          +---------------------+  +---------------------+
                          |    CreditCard       |  |   MobileBanking     |
                          +---------------------+  +---------------------+
                          | -cardNumber:String  |  | -mobileNumber:String|
                          | -expiryDate : Date  |  | -provider : String  |
                          | -cvv : String       |  +---------------------+
                          +---------------------+  | +pay()              |
                          | +pay()              |  | +sendOtp()          |
                          | +validateCard()     |  +---------------------+
                          +---------------------+
   ```

   Explanation
   ```
      NOTATION
        -  private attribute      +  public method
        ---------->               ASSOCIATION , with multiplicity
        ------|>   /_\            INHERITANCE (generalisation)
        {abstract}                an abstract class - cannot be
                                  instantiated on its own
   ```
   - `Customer –– Order` is an `association` with multiplicity `1 to 0..*`: one customer may place many orders, and each order belongs to exactly one customer.
   - `Order –– PaymentMethod` is an association `1 to 1`: each order is settled by one payment.
   - `CreditCard` and `MobileBanking` `inherit` from `PaymentMethod`. Each overrides `pay()` with its own implementation — this is `polymorphism`: the Order calls `pay()` without knowing which kind of payment it holds.
   - Making `PaymentMethod` `abstract` is the important design point. A new method — bKash, Nagad, cash on delivery — is added as a new subclass, and `Order` needs no change at all. That is the `open–closed principle`.

2. Draw a Use Case Diagram for an Online Banking System with two actors: Customer and Bank Admin. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Use case diagram for an online banking system
   ```
      +==============================================================+
      |                    ONLINE BANKING SYSTEM                     |
      |                                                              |
      |     (  Login  )                                              |
      |                                                              |
      |     (  Check Balance      )                                  |
      |                                                              |
      |     (  Transfer Funds     )                                  |
      |                                                              |
      |     (  Pay Bills         )                                   |
      |                                                              |
      |     (  View Statement    )                                   |
      |                                                              |
      |     (  Change Password   )                                   |
      |                                                              |
      |     (  Manage Accounts   )                                   |
      |                                                              |
      |     (  Approve Loan      )                                   |
      |                                                              |
      |     (  Generate Reports  )                                   |
      |                                                              |
      |     (  Block / Unblock Account )                             |
      +==============================================================+

           O                                              O
          -|-   CUSTOMER                                 -|-  BANK ADMIN
          / \                                            / \

      CUSTOMER  ----> Login , Check Balance , Transfer Funds ,
                      Pay Bills , View Statement , Change Password

      BANK ADMIN ---> Login , Manage Accounts , Approve Loan ,
                      Generate Reports , Block / Unblock Account
   ```
   ```mermaid
   flowchart LR
       C(("Customer")) --- UC1(["Login"])
       C --- UC2(["Check Balance"])
       C --- UC3(["Transfer Funds"])
       C --- UC4(["Pay Bills"])
       C --- UC5(["View Statement"])
       A(("Bank Admin")) --- UC1
       A --- UC6(["Manage Accounts"])
       A --- UC7(["Approve Loan"])
       A --- UC8(["Generate Reports"])
       UC3 -.->|includes| UC9(["Verify OTP"])
       UC4 -.->|includes| UC9
   ```

   The relationships shown
   ```
      ASSOCIATION      a plain line from an actor to a use case -
                       "this actor performs this use case".

      <<include>>      one use case ALWAYS uses another.
                       Transfer Funds  <<include>>  Verify OTP
                       Pay Bills       <<include>>  Verify OTP
                       The included behaviour is mandatory and is
                       factored out to avoid repeating it.

      <<extend>>       OPTIONAL behaviour added under a condition.
                       Transfer Funds  <<extend>>  Apply Charge
                       (only when the transfer is to another bank)

      GENERALISATION   an actor inherits another actor's use cases.
                       Bank Admin could be shown as a specialisation
                       of Bank Staff.
   ```

   Explanation
   ```
      THE SYSTEM BOUNDARY - the rectangle - separates what is inside
           the system from the actors outside it. Everything the
           system does is drawn inside ; actors are always outside.

      ACTORS are ROLES, not people. One person may be both a Customer
           and an Admin ; that is still two actors.

      Login is SHARED by both actors, so both have a line to it.

      Each OVAL is a complete goal the actor achieves, expressed from
           the ACTOR'S point of view - "Transfer Funds", not
           "Update the balance table".
   ```
   - The commonest mistake in drawing one of these is turning it into a flowchart. A use case diagram shows `what` the system does and `who` uses it, `not the order` in which things happen. Sequence is shown by a `sequence diagram`; internal logic by an `activity diagram`.

3. **Draw a class diagram for an E-commerce website where customer can view different products, can pay either by card or cash.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 401 (ET: BUET)]*

   Answer: Class diagram
   ```mermaid
   classDiagram
       class Customer {
           -int customerId
           -String name
           -String email
           +viewProducts()
           +addToCart()
           +placeOrder()
       }
       class Product {
           -int productId
           -String name
           -double price
           -int stock
           +getDetails()
           +checkStock()
       }
       class Order {
           -int orderId
           -Date orderDate
           -double total
           +calculateTotal()
       }
       class Payment {
           <<abstract>>
           -int paymentId
           -double amount
           +pay()
       }
       class CardPayment {
           -String cardNumber
           -Date expiry
           +pay()
           +authorize()
       }
       class CashPayment {
           -String collectedBy
           +pay()
           +issueReceipt()
       }
       Customer "1" --> "0..*" Order : places
       Order "1" --> "1..*" Product : contains
       Order "1" --> "1" Payment : settled by
       Payment <|-- CardPayment
       Payment <|-- CashPayment
   ```
   ```
      +--------------------+  1    0..* +--------------------+
      |     Customer       |-----------|       Order         |
      +--------------------+  places   +--------------------+
      | -customerId : int  |           | -orderId : int      |
      | -name : String     |           | -orderDate : Date   |
      | -email : String    |           | -total : double     |
      +--------------------+           +--------------------+
      | +viewProducts()    |           | +calculateTotal()   |
      | +addToCart()       |           +--------------------+
      | +placeOrder()      |             1 |          | 1
      +--------------------+      contains |          | settled by
                                      1..* |          | 1
                           +--------------------+  +--------------------+
                           |      Product       |  |     Payment        |
                           +--------------------+  |    {abstract}      |
                           | -productId : int   |  +--------------------+
                           | -name : String     |  | -paymentId : int   |
                           | -price : double    |  | -amount : double   |
                           | -stock : int       |  +--------------------+
                           +--------------------+  | +pay()             |
                           | +getDetails()      |  +--------------------+
                           | +checkStock()      |           /_\
                           +--------------------+            |
                                           +-----------------+-------------+
                                           |                               |
                             +--------------------+          +--------------------+
                             |    CardPayment     |          |    CashPayment     |
                             +--------------------+          +--------------------+
                             | -cardNumber:String |          | -collectedBy:String|
                             | -expiry : Date     |          +--------------------+
                             +--------------------+          | +pay()             |
                             | +pay()             |          | +issueReceipt()    |
                             | +authorize()       |          +--------------------+
                             +--------------------+
   ```

   Explanation
   ```
      NOTATION
        -  private attribute       +  public method
        -------->                  ASSOCIATION with multiplicity
        ------|>   /_\             INHERITANCE
        {abstract}                 abstract class
   ```
   - `Customer` to `Order` is `1 to 0..*` — a customer may place many orders (or none yet), and each order belongs to one customer.
   - `Order` to `Product` is `1 to 1..*` — an order must contain at least one product. In a fuller model this would be an `association class` called `OrderItem`, carrying the quantity and the unit price at the time of sale.
   - `Payment` is `abstract`; `CardPayment` and `CashPayment` inherit from it and each overrides `pay()`. This is `polymorphism` — the `Order` calls `pay()` without knowing which kind of payment it holds.
   - Why making `Payment` abstract matters: adding bKash, Nagad or cash on delivery means adding one new subclass, with `no change to Order` at all. That is the `open–closed principle` in a diagram.

4. **Consider the following buy a product description. Customer browses catalog, selects items to buy and then goes to check out. Customer fills in shipping information (address, receive time). System presents full pricing information and customer fills in credit card information. System authorizes purchase, confirms sale and sends confirming email to customer. Draw a use case diagram for the above system.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*

   Answer: Use case diagram
   ```
      +===============================================================+
      |                  ONLINE SHOPPING SYSTEM                       |
      |                                                               |
      |    (  Browse Catalog  )                                       |
      |                                                               |
      |    (  Select Items / Add to Cart  )                           |
      |                                                               |
      |    (  Check Out  )                                            |
      |            :                                                  |
      |            : <<include>>                                      |
      |            v                                                  |
      |    (  Enter Shipping Information  )                           |
      |            :                                                  |
      |            : <<include>>                                      |
      |            v                                                  |
      |    (  Display Full Pricing  )                                 |
      |            :                                                  |
      |            : <<include>>                                      |
      |            v                                                  |
      |    (  Enter Credit Card Information  )                        |
      |            :                                                  |
      |            : <<include>>                                      |
      |            v                                                  |
      |    (  Authorize Payment  ) - - - - - - - - - - - - - - - -+   |
      |            :                                              |   |
      |            : <<include>>                                  |   |
      |            v                                              |   |
      |    (  Confirm Sale  )                                     |   |
      |            :                                              |   |
      |            : <<include>>                                  |   |
      |            v                                              |   |
      |    (  Send Confirmation Email  ) - - - - - - - - - - -+   |   |
      +=======================================================+===+===+
                                                              |   |
           O                                                  |   |
          -|-  CUSTOMER                                       |   |
          / \                                                 v   v
                                               +----------------+ +----------------+
                                               | EMAIL SERVICE  | | CREDIT CARD    |
                                               |  (secondary    | | AUTHORIZATION  |
                                               |   actor)       | |    SERVICE     |
                                               +----------------+ +----------------+
   ```
   ```mermaid
   flowchart LR
       C(("Customer")) --- U1(["Browse Catalog"])
       C --- U2(["Select Items"])
       C --- U3(["Check Out"])
       U3 -.->|include| U4(["Enter Shipping Info"])
       U3 -.->|include| U5(["Display Pricing"])
       U3 -.->|include| U6(["Enter Card Info"])
       U3 -.->|include| U7(["Authorize Payment"])
       U3 -.->|include| U8(["Confirm Sale"])
       U3 -.->|include| U9(["Send Email"])
       U7 --- CC(("Card Auth Service"))
       U9 --- ES(("Email Service"))
   ```

   The use cases, taken from the description
   ```
      Browse Catalog                  "Customer browses catalog"
      Select Items / Add to Cart      "selects items to buy"
      Check Out                       "then goes to check out"
      Enter Shipping Information      "fills in shipping information
                                       (address, receive time)"
      Display Full Pricing            "System presents full pricing
                                       information"
      Enter Credit Card Information   "customer fills in credit card
                                       information"
      Authorize Payment               "System authorizes purchase"
      Confirm Sale                    "confirms sale"
      Send Confirmation Email         "sends confirming email"
   ```

   The actors
   ```
      PRIMARY actor    : CUSTOMER - initiates the whole flow and
                         receives the benefit.
      SECONDARY actors : CREDIT CARD AUTHORIZATION SERVICE and
                         EMAIL SERVICE - external systems the system
                         calls on to complete the goal. They are
                         still actors, because they lie OUTSIDE the
                         system boundary.
   ```

   The relationships
   ```
      ASSOCIATION   a plain line - "this actor performs this use case"
      <<include>>   Check Out ALWAYS includes shipping entry, pricing
                    display, card entry, authorisation, confirmation
                    and the email. All of it is MANDATORY, so
                    <<include>> is correct, not <<extend>>.
      <<extend>>    would be used for OPTIONAL behaviour, such as
                    "Apply Discount Coupon" extending Check Out.
   ```
   - One point worth stating: the description reads like a sequence of steps, and it is tempting to draw arrows showing the order. `A use case diagram must not show sequence.` It shows only `what` the system does and `who` is involved. The step-by-step order in the description belongs in the use case's `textual description` (main flow and alternative flows), or in a `sequence diagram`.

5. **Library management class diagram:** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*

   Answer: Class diagram for a library management system
   ```mermaid
   classDiagram
       class Library {
           -String name
           -String address
           +addBook()
           +removeBook()
       }
       class Book {
           -String isbn
           -String title
           -String author
           -int totalCopies
           -int availableCopies
           +isAvailable()
           +reserve()
       }
       class Member {
           <<abstract>>
           -int memberId
           -String name
           -String phone
           -int maxBooks
           +borrowBook()
           +returnBook()
       }
       class Student {
           -String department
           -String session
           +getMaxBooks()
       }
       class Teacher {
           -String designation
           +getMaxBooks()
       }
       class Loan {
           -int loanId
           -Date issueDate
           -Date dueDate
           -Date returnDate
           +calculateFine()
           +isOverdue()
       }
       class Librarian {
           -int staffId
           -String name
           +issueBook()
           +acceptReturn()
           +collectFine()
       }
       Library "1" *-- "0..*" Book : contains
       Member <|-- Student
       Member <|-- Teacher
       Member "1" --> "0..*" Loan : has
       Book "1" --> "0..*" Loan : issued in
       Librarian "1" --> "0..*" Loan : processes
   ```
   ```
      +------------------+  1    0..* +--------------------------+
      |     Library      |*----------|          Book            |
      +------------------+ contains  +--------------------------+
      | -name : String   |           | -isbn : String           |
      | -address : String|           | -title : String          |
      +------------------+           | -author : String         |
      | +addBook()       |           | -totalCopies : int       |
      | +removeBook()    |           | -availableCopies : int   |
      +------------------+           +--------------------------+
                                     | +isAvailable()           |
                                     | +reserve()               |
                                     +--------------------------+
                                               1 |
                                    issued in    | 0..*
      +------------------+  1    0..* +--------------------------+
      |     Member       |-----------|          Loan            |
      |   {abstract}     |    has    +--------------------------+
      +------------------+           | -loanId : int            |
      | -memberId : int  |           | -issueDate : Date        |
      | -name : String   |           | -dueDate : Date          |
      | -phone : String  |           | -returnDate : Date       |
      | -maxBooks : int  |           +--------------------------+
      +------------------+           | +calculateFine()         |
      | +borrowBook()    |           | +isOverdue()             |
      | +returnBook()    |           +--------------------------+
      +------------------+                   0..* |
             /_\                                  | processes
              |                                 1 |
      +-------+--------+              +--------------------------+
      |                |              |        Librarian         |
   +-----------+ +-----------+        +--------------------------+
   |  Student  | |  Teacher  |        | -staffId : int           |
   +-----------+ +-----------+        | -name : String           |
   |-department| |-designat- |        +--------------------------+
   |-session   | | ion       |        | +issueBook()             |
   +-----------+ +-----------+        | +acceptReturn()          |
   |+getMaxBo- | |+getMaxBo- |        | +collectFine()           |
   | oks()     | | oks()     |        +--------------------------+
   +-----------+ +-----------+
   ```

   Explanation
   ```
      NOTATION
        -  private attribute      +  public method
        -------->                 ASSOCIATION with multiplicity
        ------|>  /_\             INHERITANCE (generalisation)
        *-------                  COMPOSITION - the filled diamond
        {abstract}                abstract class
   ```
   - `Library –◆– Book` is a `composition`, drawn with a filled diamond: the books belong to the library, and if the library is dissolved its catalogue entries go with it.
   - `Loan` is the key class in the design. A member borrowing a book is a `many-to-many` relationship, and a many-to-many association must be resolved into a separate class. `Loan` holds what belongs to the borrowing event itself — issue date, due date, return date and the fine.
   - `Student` and `Teacher` `inherit` from `Member` and each overrides `getMaxBooks()`, because a teacher may usually borrow more books than a student. This is `polymorphism`.
   - `Librarian` is modelled as a class rather than an actor here, because the system stores which staff member issued each loan. In the `use case diagram` the same librarian appears as an `actor` — the two diagrams show different views of the same person.
   - `calculateFine()` sits on `Loan`, not on `Member`, because the fine depends on `dueDate` and `returnDate`, which are `Loan`'s own attributes. Putting a method where its data lives is what `high cohesion` means in practice.

6. **Draw A class diagram. A token-ring based local area network (LAN) is a network consisting of nodes in which network packets are sent around. Every node has a unique name within the network, and refers to its next node. Different kinds of nodes exist: Workstations are originators of messages; servers and printers are network nodes that can receive messages. Packets contain an originator a destination and content, and are sent around on a network. A LAN is a circular configuration of nodes.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*

   Answer: Class diagram for a token-ring LAN
   ```mermaid
   classDiagram
       class LAN {
           -String name
           +addNode()
           +removeNode()
           +sendPacket()
       }
       class Node {
           <<abstract>>
           -String name
           +receivePacket()
           +forwardPacket()
       }
       class Workstation {
           -String userName
           +originatePacket()
           +receivePacket()
       }
       class Server {
           -String service
           -int capacity
           +receivePacket()
       }
       class Printer {
           -String model
           -int queueLength
           +receivePacket()
           +print()
       }
       class Packet {
           -String content
           +isDelivered()
       }
       LAN "1" *-- "3..*" Node : consists of
       Node "1" --> "1" Node : next
       Node <|-- Workstation
       Node <|-- Server
       Node <|-- Printer
       Workstation "1" --> "0..*" Packet : originates
       Packet "1" --> "1" Node : destination
       LAN "1" --> "0..*" Packet : carries
   ```
   ```
      +--------------------+  1     3..*  +--------------------------+
      |        LAN         |*------------|          Node            |
      +--------------------+ consists of +--------------------------+
      | -name : String     |             | -name : String {unique}  |
      +--------------------+             +--------------------------+
      | +addNode()         |             | +receivePacket()         |
      | +removeNode()      |             | +forwardPacket()          |
      | +sendPacket()      |             +--------------------------+
      +--------------------+                 |          /_\
           | 1                          next |           |
           | carries                    1    |           |
           | 0..*                       +----+           |
      +--------------------------+                       |
      |         Packet           |          +------------+------------+
      +--------------------------+          |            |            |
      | -content : String        |   +-------------+ +---------+ +---------+
      +--------------------------+   | Workstation | | Server  | | Printer |
      | +isDelivered()           |   +-------------+ +---------+ +---------+
      +--------------------------+   |-userName    | |-service | |-model   |
         1 | originator              |             | |-capacity| |-queue   |
           |          +--------------+-------------+ +---------+ +---------+
         1 | destination             |+originate-  | |+receive-| |+receive-|
           v                         |  Packet()   | | Packet()| | Packet()|
      ( a Node )                     |+receive-    | +---------+ |+print() |
                                     |  Packet()   |             +---------+
                                     +-------------+
   ```

   The circular structure — how the ring is modelled
   ```
      The self-association  Node --> Node  with the role name "next"
      is what makes it a RING. Each node refers to exactly ONE next
      node, and following the chain returns to the start.

           Node A ---next---> Node B ---next---> Node C
             ^                                     |
             +----------------next-----------------+

      MULTIPLICITY on that association is  1 to 1  : every node has
      exactly one successor, and is the successor of exactly one node.

      The circularity itself is a CONSTRAINT, not something the
      notation can enforce, so it is written on the diagram :

           {the next-links form a single closed cycle}
   ```

   Explanation of each element
   ```
      LAN               a network. COMPOSITION (filled diamond) to
                        Node : the nodes make up the LAN, and a
                        minimum of 3..* keeps it a meaningful ring.

      Node {abstract}   the general concept. It carries the UNIQUE
                        name required by the description, and the
                        "next" reference. It is ABSTRACT because
                        every real node is one of the three kinds
                        below.

      Workstation       ORIGINATES messages - so it alone has
                        originatePacket().
      Server , Printer  can only RECEIVE messages. They inherit
                        receivePacket() and add their own behaviour.

      Packet            has three parts required by the description :
                        an ORIGINATOR (a Node, in practice a
                        Workstation), a DESTINATION (a Node) and
                        CONTENT. The originator and destination are
                        modelled as ASSOCIATIONS to Node rather than
                        as plain string attributes, because they
                        really are references to nodes.
   ```
   - Two design points worth stating. First, the description says a workstation `originates` and a server or printer `receives`, so `originatePacket()` belongs only on `Workstation` while `receivePacket()` is inherited by all three — the difference in capability is expressed by `where the operation is placed`, not by a flag. Second, `{unique}` on `Node.name` records the description's requirement that every node has a unique name within the network; a constraint in braces is the standard UML way to state a rule the box-and-line notation cannot capture.

7. **(খ) একটি লাইব্রেরি ব্যবস্থাপনা সিস্টেম এর জন্যে Use Case Diagram অঙ্কন করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Use case diagram for a library management system
   ```
      +===============================================================+
      |                 LIBRARY MANAGEMENT SYSTEM                     |
      |                                                               |
      |     (  Search Book  )                                         |
      |                                                               |
      |     (  View Book Details  )                                   |
      |                                                               |
      |     (  Borrow Book  ) - - - <<include>> - - -> ( Check        |
      |                                                  Eligibility )|
      |                                                               |
      |     (  Return Book  ) - - - <<extend>> - - -> ( Pay Fine )    |
      |                                                               |
      |     (  Reserve Book  )                                        |
      |                                                               |
      |     (  Renew Book  )                                          |
      |                                                               |
      |     (  Login  )                                               |
      |                                                               |
      |     (  Add / Remove Book  )                                   |
      |                                                               |
      |     (  Manage Member  )                                       |
      |                                                               |
      |     (  Issue Book  )                                          |
      |                                                               |
      |     (  Collect Fine  )                                        |
      |                                                               |
      |     (  Generate Report  )                                     |
      +===============================================================+

           O                    O                       O
          -|-  MEMBER          -|-  LIBRARIAN          -|-  ADMIN
          / \                  / \                     / \

      MEMBER    ---> Login , Search Book , View Book Details ,
                     Borrow Book , Return Book , Reserve Book ,
                     Renew Book

      LIBRARIAN ---> Login , Search Book , Issue Book , Accept Return ,
                     Collect Fine , Add / Remove Book

      ADMIN     ---> Login , Manage Member , Add / Remove Book ,
                     Generate Report
   ```
   ```mermaid
   flowchart LR
       M(("Member")) --- U1(["Search Book"])
       M --- U2(["Borrow Book"])
       M --- U3(["Return Book"])
       M --- U4(["Reserve Book"])
       L(("Librarian")) --- U5(["Issue Book"])
       L --- U6(["Collect Fine"])
       L --- U7(["Add/Remove Book"])
       A(("Admin")) --- U8(["Manage Member"])
       A --- U9(["Generate Report"])
       A --- U7
       U2 -.->|include| U10(["Check Eligibility"])
       U3 -.->|extend| U6
   ```

   The relationships
   ```
      ASSOCIATION      a plain line from an actor to a use case -
                       "this actor performs this use case".

      <<include>>      MANDATORY sub-behaviour, always performed.
                       Borrow Book  <<include>>  Check Eligibility
                       (the member's borrowing limit and any existing
                        overdue book must ALWAYS be checked)

      <<extend>>       OPTIONAL behaviour, added only under a
                       condition.
                       Return Book  <<extend>>  Pay Fine
                       (a fine arises ONLY if the book is overdue)

      GENERALISATION   an actor inherits another's use cases.
                       Librarian and Admin could both be shown as
                       specialisations of a Staff actor, since both
                       share Login and Add / Remove Book.
   ```

   Explanation
   ```
      THE SYSTEM BOUNDARY - the rectangle - separates what the system
           does from the actors, who are always OUTSIDE it.

      ACTORS are ROLES, not individuals. The same person may be both
           a Member and a Librarian ; that is still two actors.

      Shared use cases - Login , Search Book , Add / Remove Book -
           have a line from EVERY actor that performs them.

      Each OVAL is a complete GOAL, named from the ACTOR's point of
           view : "Borrow Book", not "Update the loan table".
   ```
   - The mistake to avoid is drawing the diagram as a flow of steps. A use case diagram shows `what` the system does and `who` uses it, `never the sequence`. Sequence belongs in a `sequence diagram`, and the step-by-step main flow and alternative flows belong in the use case's `written description`.

8. **How do you model the following situation with a UML class diagram the car fleet of a car rental contains multiple cars, one car belongs to exactly one car fleet.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

   Answer: The situation is modelled as a `composition` — the filled-diamond relationship — with multiplicity `1` on the fleet side and `1..*` on the car side.
   ```mermaid
   classDiagram
       class CarFleet {
           -int fleetId
           -String location
           +addCar()
           +removeCar()
           +getAvailableCars()
       }
       class Car {
           -String registrationNo
           -String model
           -String status
           +isAvailable()
           +assignToRental()
       }
       CarFleet "1" *-- "1..*" Car : contains
   ```
   ```
      +--------------------------+            +--------------------------+
      |        CarFleet          |  1    1..* |           Car            |
      +--------------------------+*----------+--------------------------+
      | -fleetId : int           |  contains  | -registrationNo : String |
      | -location : String       |            | -model : String          |
      +--------------------------+            | -status : String         |
      | +addCar()                |            +--------------------------+
      | +removeCar()             |            | +isAvailable()           |
      | +getAvailableCars()      |            | +assignToRental()        |
      +--------------------------+            +--------------------------+

           the FILLED DIAMOND  *  sits at the CarFleet end
   ```

   How the two statements in the question map onto the notation
   ```
      "a car fleet contains MULTIPLE cars"
           -> multiplicity  1..*  at the CAR end
              (use 0..* instead if an empty fleet is allowed)

      "one car belongs to EXACTLY ONE car fleet"
           -> multiplicity  1  at the FLEET end
              This is the phrase that makes it a COMPOSITION rather
              than a plain association : a part that belongs to
              exactly one whole.
   ```

   Why composition and not aggregation or association
   ```
      ASSOCIATION  ----------    a plain relationship. It would allow
           a car to belong to several fleets, or to none. That
           contradicts "exactly one".

      AGGREGATION  <>--------    HOLLOW diamond. A "has-a" in which
           the part can exist INDEPENDENTLY and can be SHARED - a
           Department and its Teachers, where a teacher may belong to
           two departments and survives the department closing.

      COMPOSITION  *--------     FILLED diamond. A STRONG "owns-a" :
           - the part belongs to EXACTLY ONE whole
           - the part is NOT SHARED
           - the whole controls the part's lifetime

      The phrase "exactly one car fleet" rules out sharing, so
      COMPOSITION is the correct choice.
   ```
   - One qualification worth stating. Composition in its strictest reading means the part is `destroyed with the whole`, and a real car obviously survives the closing of a rental branch — it would be transferred to another fleet. So many modellers would draw this as an `aggregation` (hollow diamond) with multiplicity `1`, which captures "belongs to exactly one" without claiming the car ceases to exist.
   ```
      BOTH answers are defensible, and the multiplicity is what
      actually carries the requirement :

           CarFleet  1  *--------  1..*  Car     (strict reading)
           CarFleet  1  <>-------  1..*  Car     (car outlives fleet)

      What must NOT be drawn is  0..*  at the fleet end, or a plain
      association with no multiplicity - either would fail to state
      "exactly one".
   ```

9. **(ক) Typical web-based login system এর জন্য sequence diagram আঁকুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 778 (ET: N/A)]*

   Answer: Sequence diagram for a web-based login system
   ```mermaid
   sequenceDiagram
       actor User
       participant Browser
       participant WebServer
       participant AuthController
       participant Database
       User->>Browser: enter username, password
       Browser->>WebServer: POST /login
       WebServer->>AuthController: validate(username, password)
       AuthController->>Database: SELECT user WHERE username=?
       Database-->>AuthController: user record + password hash
       AuthController->>AuthController: hash(password) and compare
       alt credentials valid
           AuthController->>Database: create session
           AuthController-->>WebServer: success + session ID
           WebServer-->>Browser: 302 redirect + Set-Cookie
           Browser-->>User: home page
       else credentials invalid
           AuthController->>Database: increment failed attempts
           AuthController-->>WebServer: failure
           WebServer-->>Browser: 401 + error message
           Browser-->>User: "Invalid username or password"
       end
   ```
   ```
      User      Browser    WebServer   AuthCtrl    Database
       |           |           |           |           |
       |  enter    |           |           |           |
       |  user/pwd |           |           |           |
       |---------->|           |           |           |
       |           | POST      |           |           |
       |           | /login    |           |           |
       |           |---------->|           |           |
       |           |           | validate  |           |
       |           |           |---------->|           |
       |           |           |           | SELECT    |
       |           |           |           | user      |
       |           |           |           |---------->|
       |           |           |           |<- - - - - |
       |           |           |           |  record + |
       |           |           |           |  hash     |
       |           |           |           |           |
       |           |           |     [hash & compare]  |
       |           |           |           |           |
       |           |           |           | create    |
       |           |           |           | session   |
       |           |           |           |---------->|
       |           |           |<- - - - - |           |
       |           |           | success + |           |
       |           |           | sessionID |           |
       |           |<- - - - - |           |           |
       |           | 302 +     |           |           |
       |           | Set-Cookie|           |           |
       |<- - - - - |           |           |           |
       | home page |           |           |           |
       |           |           |           |           |

      ------>  synchronous call (solid arrowhead)
      - - ->   return message  (dashed line)
      [ ]      a self-call, drawn as a small loop on the lifeline
   ```

   The notation
   ```
      ACTOR / OBJECT     the boxes across the top. An actor is drawn
                         as a stick figure, an object as a rectangle.
      LIFELINE           the vertical dashed line below each box -
                         the object's existence over time. TIME RUNS
                         DOWNWARD.
      ACTIVATION BAR     the thin rectangle on a lifeline while that
                         object is doing work.
      SYNCHRONOUS MESSAGE  solid line, filled arrowhead. The caller
                         WAITS for the reply.
      RETURN MESSAGE     dashed line, open arrowhead.
      SELF MESSAGE       an arrow from a lifeline back to itself -
                         here, hashing the password.
      alt FRAGMENT       a box labelled "alt" divided by a dashed
                         line, showing the two alternative outcomes.
   ```

   Explanation of the flow
   ```
      1. The user submits the form ; the browser sends a POST.
      2. The web server hands the credentials to the authentication
         controller.
      3. The controller fetches the stored PASSWORD HASH - never the
         password itself, which is not stored anywhere.
      4. It hashes the submitted password with the stored SALT and
         compares. A constant-time comparison is used, so the time
         taken does not reveal how much of the password was right.
      5. VALID   : a session record is created, and the session ID
                   goes back as an HttpOnly, Secure cookie. The
                   browser is redirected to the home page.
         INVALID : the failed-attempt counter is incremented -
                   three failures lock the account - and a single
                   generic message is returned.
   ```
   - The security detail worth one line: the error message must be `"Invalid username or password"`, never "no such user" or "wrong password". Distinguishing the two tells an attacker which usernames exist, which is `user enumeration`.
   - Where each UML diagram fits: the `sequence diagram` above shows the `order` of interactions over time; a `use case diagram` would show only that a Visitor performs Login; and an `activity diagram` would show the internal decision logic. All three describe the same login from different viewpoints.

10. **(c) Explain different type of relationships that are used in a UML diagram.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

    Answer: UML class diagrams use `six` kinds of relationship. They differ in how strongly the two classes depend on each other.

    1. Association
    ```
       A structural link : one class knows about another and keeps a
       reference to it.

            Student  ------------  Course
                     enrolled in

       With MULTIPLICITY and a role name :

            Student "1..*" ------ "1..*" Course

       Multiplicity values :  1 , 0..1 , 1..* , 0..* , 3..5 , *

       NAVIGABILITY : an arrowhead shows one-way navigation.
            Order --------> Product      Order knows its products,
                                         but a Product does not know
                                         which Orders contain it.
    ```

    2. Aggregation — "has-a", the weak whole–part
    ```
            Department  <>------------  Teacher
                        HOLLOW diamond at the WHOLE end

       The part can exist INDEPENDENTLY and can be SHARED :
         a teacher survives the department being closed, and may
         belong to two departments at once.
    ```

    3. Composition — "owns-a", the strong whole–part
    ```
            House  *------------  Room
                   FILLED diamond at the WHOLE end

       The part belongs to EXACTLY ONE whole, is NOT SHARED, and its
       LIFETIME is controlled by the whole : destroy the house and
       the rooms cease to exist.

       AGGREGATION vs COMPOSITION - the test to apply :
            Can the part belong to two wholes ?      -> aggregation
            Can the part outlive the whole ?         -> aggregation
            Neither ?                                -> composition
    ```

    4. Generalisation — inheritance, "is-a"
    ```
            Payment
               /_\                  hollow triangle pointing at the
                |                   PARENT class
         +------+------+
         |             |
      CreditCard   CashPayment

       The child inherits the parent's attributes and operations and
       may OVERRIDE them. An {abstract} parent cannot be instantiated.
    ```

    5. Realisation — implementing an interface
    ```
            <<interface>>
              Printable
                 /_\
                  :                  DASHED line , hollow triangle
                  :
              Invoice

       The class promises to provide the operations the interface
       declares. Same triangle as inheritance, but a DASHED line -
       the difference is inheriting IMPLEMENTATION versus implementing
       a CONTRACT.
    ```

    6. Dependency — "uses"
    ```
            OrderService  - - - - - >  EmailSender
                          DASHED line , open arrowhead

       The WEAKEST relationship : one class uses another temporarily -
       as a method parameter, a local variable, or a static call - but
       does not keep a reference to it. A change in EmailSender may
       force a change in OrderService, and that is all the coupling
       there is.
    ```

    Summary
    ```
       +----------------+------------------+-------------------------+
       | Relationship   | Notation         | Meaning                 |
       +----------------+------------------+-------------------------+
       | Association    | ----------       | knows about             |
       | Aggregation    | <>---------      | has-a , part is shared  |
       |                |                  | and independent         |
       | Composition    | *---------       | owns-a , part dies with |
       |                |                  | the whole               |
       | Generalisation | ------|>  /_\    | is-a , inheritance      |
       | Realisation    | - - - -|> /_\    | implements an interface |
       | Dependency     | - - - - ->       | uses temporarily        |
       +----------------+------------------+-------------------------+

       STRENGTH OF COUPLING , weakest to strongest :
            dependency < association < aggregation < composition
    ```
    - The three relationships found in `other` UML diagrams, worth naming: `<<include>>` and `<<extend>>` between use cases in a use case diagram, and `message` arrows between lifelines in a sequence diagram. Those are not class relationships and should not be mixed into a class diagram.
    - The distinction examiners test most is `aggregation against composition`. The deciding question is not how the classes feel but whether the part can be `shared` or can `outlive` the whole. If it can, the diamond is hollow.

11. **Write down the use case diagram for ATM.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162-1163 (ET: N/A)]*

    Answer: Use case diagram for an ATM
    ```
       +===============================================================+
       |                          ATM SYSTEM                           |
       |                                                               |
       |     (  Insert Card  )                                         |
       |                                                               |
       |     (  Authenticate PIN  )                                    |
       |                                                               |
       |     (  Withdraw Cash  ) - - <<include>> - -> ( Authenticate   |
       |                                                    PIN     )  |
       |                                                               |
       |     (  Deposit Cash  )                                        |
       |                                                               |
       |     (  Check Balance  )                                       |
       |                                                               |
       |     (  Transfer Funds  )                                      |
       |                                                               |
       |     (  Mini Statement  )                                      |
       |                                                               |
       |     (  Change PIN  )                                          |
       |                                                               |
       |     (  Print Receipt  )  <- - <<extend>> - -  Withdraw Cash   |
       |                                                               |
       |     (  Refill Cash  )                                         |
       |                                                               |
       |     (  Maintain ATM  )                                        |
       +======================================+========================+
                                              |
            O                    O            |            O
           -|-  CUSTOMER        -|- BANK      |           -|- TECHNICIAN
           / \                  / \  OFFICER  |           / \
                                              v
                                  +--------------------------+
                                  |    BANK SERVER /         |
                                  |    CORE BANKING SYSTEM   |
                                  |    (secondary actor)     |
                                  +--------------------------+

       CUSTOMER   ---> Insert Card , Authenticate PIN , Withdraw Cash ,
                       Deposit Cash , Check Balance , Transfer Funds ,
                       Mini Statement , Change PIN

       TECHNICIAN ---> Refill Cash , Maintain ATM

       BANK OFFICER -> Refill Cash , view transaction log

       BANK SERVER --> takes part in every transaction that needs
                       authorisation or a balance update
    ```
    ```mermaid
    flowchart LR
        C(("Customer")) --- U1(["Insert Card"])
        C --- U2(["Authenticate PIN"])
        C --- U3(["Withdraw Cash"])
        C --- U4(["Deposit Cash"])
        C --- U5(["Check Balance"])
        C --- U6(["Transfer Funds"])
        C --- U7(["Change PIN"])
        T(("Technician")) --- U8(["Refill Cash"])
        T --- U9(["Maintain ATM"])
        U3 -.->|include| U2
        U3 -.->|extend| U10(["Print Receipt"])
        U3 --- B(("Bank Server"))
        U6 --- B
    ```

    The relationships
    ```
       ASSOCIATION    a plain line - "this actor performs this use
                      case".

       <<include>>    MANDATORY sub-behaviour, always performed.
                      Withdraw Cash , Deposit Cash , Check Balance ,
                      Transfer Funds all  <<include>>  Authenticate
                      PIN - no transaction happens without it, so the
                      behaviour is factored out instead of repeated in
                      every use case.

       <<extend>>     OPTIONAL behaviour under a condition.
                      Withdraw Cash  <<extend>>  Print Receipt
                      (only if the customer asks for a receipt)
                      Withdraw Cash  <<extend>>  Apply Service Charge
                      (only for another bank's card)

       The arrow direction is the point candidates get wrong :
            <<include>>  points FROM the base use case TO the included
                         one.
            <<extend>>   points FROM the extending use case TO the
                         base one.
    ```

    Explanation
    ```
       THE SYSTEM BOUNDARY - the rectangle - contains everything the
            ATM system does. Actors always sit OUTSIDE it.

       PRIMARY actor    : CUSTOMER - initiates the transaction and
            receives the benefit.
       SECONDARY actor  : BANK SERVER - an external system the ATM
            calls on to authorise and to update the balance. It is
            still an actor, because it lies outside the boundary.
       SUPPORTING actors: TECHNICIAN and BANK OFFICER - they use the
            system, but for maintenance rather than banking.

       Each OVAL is a complete GOAL named from the actor's viewpoint -
            "Withdraw Cash", not "Decrement the balance field".
    ```
    - The commonest error is drawing arrows between the ovals to show the order — insert card, then PIN, then choose transaction. `A use case diagram never shows sequence.` The order belongs in the use case's `written description` or in a `sequence diagram`.

12. **Draw UML diagram of composite design pattern.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1215 (ET: N/A)]*

    Answer: UML diagram of the Composite design pattern
    ```mermaid
    classDiagram
        class Component {
            <<abstract>>
            +operation()
            +add(Component c)
            +remove(Component c)
            +getChild(int i)
        }
        class Leaf {
            +operation()
        }
        class Composite {
            -List~Component~ children
            +operation()
            +add(Component c)
            +remove(Component c)
            +getChild(int i)
        }
        class Client
        Component <|-- Leaf
        Component <|-- Composite
        Composite "1" o-- "0..*" Component : children
        Client --> Component : uses
    ```
    ```
       +----------+          +----------------------------------+
       |  Client  |--------->|          Component               |
       +----------+   uses   |          {abstract}              |
                             +----------------------------------+
                             | +operation()                     |
                             | +add(Component c)                |
                             | +remove(Component c)             |
                             | +getChild(int i)                 |
                             +----------------------------------+
                                           /_\
                                            |
                              +-------------+-------------+
                              |                           |
                  +--------------------+      +--------------------------+
                  |       Leaf         |      |       Composite          |
                  +--------------------+      +--------------------------+
                  |                    |      | -children : List         |
                  +--------------------+      +--------------------------+
                  | +operation()       |      | +operation()             |
                  +--------------------+      | +add(Component c)        |
                                              | +remove(Component c)     |
                                              | +getChild(int i)         |
                                              +--------------------------+
                                                  |  0..*
                                                  |  children
                                                  +---------------+
                                                                  |
                                              back to Component ---+
                                              (HOLLOW diamond o---
                                               at the Composite end)
    ```

    The three participants
    ```
       COMPONENT  {abstract}
            Declares the interface COMMON to both single objects and
            groups. This is the key to the pattern : the CLIENT talks
            only to Component and never needs to know whether it holds
            one object or a whole tree.

       LEAF
            A single object with NO children. It implements
            operation(). The child-management methods (add, remove)
            either do nothing or throw an exception, since a leaf has
            no children.

       COMPOSITE
            Holds a COLLECTION of Components - which may be Leaves or
            other Composites. Its operation() DELEGATES to every child
            in turn, and this recursion is what makes the tree work.
    ```

    How operation() works
    ```
       Leaf.operation()        do the work for this one object.

       Composite.operation()   for each child in children :
                                    child.operation();
                               - and each child may itself be a
                               Composite, so the call recurses down
                               the whole tree.
    ```

    Example — a file system
    ```
            Component  = FileSystemEntry
            Leaf       = File          (has a size of its own)
            Composite  = Folder        (contains Files and Folders)

                             Folder "root"
                            /      |       \
                  File a.txt   Folder "docs"   File b.jpg
                                  /      \
                           File c.pdf   Folder "old"
                                              |
                                        File d.doc

       getSize() on the root walks the whole tree recursively and
       returns the total. The CLIENT calls getSize() once, on one
       object, and does not care how deep the tree is.
    ```
    - Other real uses: a GUI where a `Panel` contains `Buttons` and other `Panels`, and both answer `draw()`; an organisation chart where a `Manager` contains `Employees` and other `Managers`; and an arithmetic expression tree where a `Number` is a leaf and an `Operator` is a composite.
    - The design point the pattern exists for: `it lets a client treat a single object and a group of objects identically`. Without it, every client would need an `if` to distinguish a file from a folder — and that `if` would have to be repeated everywhere. The one trade-off is that putting `add()` and `remove()` on `Component` gives `Leaf` methods that are meaningless for it; the alternative, putting them only on `Composite`, makes the interfaces differ and forces the client to check the type again. Both variants are documented, and the first is the one usually drawn.

13. **Write the use cases of withdrawing money for ATM card.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1223-1224 (ET: N/A)]*

    Answer: Use case: `Withdraw Money`

    The use case specification
    ```
       USE CASE NAME    Withdraw Money
       PRIMARY ACTOR    Customer (ATM card holder)
       SECONDARY ACTOR  Bank Server / Core Banking System
       GOAL             The customer obtains cash, and the account is
                        debited by exactly the same amount.
       PRECONDITION     The ATM is switched on and has cash. The
                        customer holds a valid, active card.
       TRIGGER          The customer inserts the card.
       POSTCONDITION    Cash is dispensed, the account is debited once,
                        and the transaction is written to the journal.
    ```

    Main success flow
    ```
       1.  Customer inserts the ATM card.
       2.  System reads the card and verifies it is valid and active.
       3.  System prompts for the PIN.
       4.  Customer enters the PIN.
       5.  System sends the PIN to the bank server for verification.
       6.  Bank server confirms the PIN is correct.
       7.  System displays the transaction menu.
       8.  Customer selects "Withdraw Cash".
       9.  System prompts for the amount.
       10. Customer enters the amount.
       11. System checks : amount is a valid multiple , within the
           per-transaction limit , within the daily limit , and the
           ATM holds enough cash.
       12. System sends a debit request to the bank server.
       13. Bank server checks the balance and DEBITS the account.
       14. Bank server returns approval.
       15. System dispenses the cash.
       16. System asks whether a receipt is wanted.
       17. System returns the card.
       18. System writes the transaction to its journal.
    ```

    Alternative and exception flows — where the marks are
    ```
       3a. CARD INVALID , EXPIRED or BLOCKED
             -> display a message , RETAIN or return the card , end.

       6a. WRONG PIN
             -> re-prompt. After THREE failures, BLOCK the card and
                end the use case.

       6b. PIN ENTRY TIMEOUT
             -> return the card and end.

       11a. INSUFFICIENT BALANCE
             -> "Insufficient balance" , return to the menu.
                NOTHING is debited.

       11b. AMOUNT EXCEEDS THE DAILY LIMIT
             -> message , return to the menu.

       11c. AMOUNT NOT A VALID MULTIPLE (e.g. 1,250)
             -> message , re-prompt.

       11d. ATM HAS INSUFFICIENT CASH
             -> "Cannot dispense this amount" , return to the menu.
                NOTHING is debited.

       12a. NETWORK FAILURE before the debit
             -> cancel , return the card , NO debit.

       14a. NETWORK FAILURE AFTER the debit but BEFORE the dispense
             -> THE CRITICAL CASE. The system must send a REVERSAL so
                the debit is undone. Money must never leave the
                account without leaving the machine.

       15a. CASH JAM in the dispenser
             -> re-credit the account , log the fault , notify the
                branch.

       17a. CUSTOMER DOES NOT TAKE THE CARD
             -> RETRACT the card after the timeout and log it.

       17b. CUSTOMER DOES NOT TAKE THE CASH
             -> retract the cash , re-credit the account , log it.
    ```

    Use case diagram
    ```
       +===============================================================+
       |                          ATM SYSTEM                           |
       |                                                               |
       |   (  Withdraw Money  ) - - <<include>> - -> ( Validate Card ) |
       |          :        :                                           |
       |          :        : - - <<include>> - -> ( Authenticate PIN )  |
       |          :        :                                           |
       |          :        : - - <<include>> - -> ( Debit Account )    |
       |          :                                                    |
       |          : <<extend>>                                         |
       |          v                                                    |
       |   (  Print Receipt  )                                         |
       |                                                               |
       |   (  Reverse Transaction  )   <- on failure after debit       |
       +======================================+========================+
                                              |
            O                                 v
           -|-  CUSTOMER            +--------------------------+
           / \                       |      BANK SERVER        |
                                     |   (secondary actor)     |
                                     +--------------------------+
    ```
    ```mermaid
    flowchart LR
        C(("Customer")) --- W(["Withdraw Money"])
        W -.->|include| V(["Validate Card"])
        W -.->|include| A(["Authenticate PIN"])
        W -.->|include| D(["Debit Account"])
        W -.->|extend| R(["Print Receipt"])
        D --- B(("Bank Server"))
        A --- B
    ```
    - Why `Validate Card`, `Authenticate PIN` and `Debit Account` use `<<include>>`: they happen on `every` withdrawal without exception, so the behaviour is factored out rather than repeated inside each transaction use case. `Print Receipt` uses `<<extend>>` because it happens only if the customer asks.
    - The point that distinguishes a good answer: the `exception flows` matter more than the main flow. Cash and card are physical, so an interrupted transaction must leave the `account`, the `cash drawer` and the `journal` in a consistent state. Step 14a — reversal after debit but before dispense — is where real money is lost, and any serious use case description must state it.

14. **Draw a high level use case diagram: Use case diagram for a visitor who want to login a page by using username password.** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*

    Answer: High-level use case diagram — visitor login
    ```
       +===============================================================+
       |                        WEB APPLICATION                        |
       |                                                               |
       |          (  Login  )                                          |
       |             :   :                                             |
       |             :   : - - - <<include>> - - -> ( Validate         |
       |             :   :                            Credentials )    |
       |             :                                                 |
       |             : <<extend>>                                      |
       |             v                                                 |
       |          (  Reset Password  )                                 |
       |                                                               |
       |          (  Register  )                                       |
       |                                                               |
       |          (  Logout  )                                         |
       +=======================================+=======================+
                                               |
            O                                  v
           -|-   VISITOR              +--------------------------+
           / \                        |     USER DATABASE        |
                                      |   (secondary actor)      |
                                      +--------------------------+

       VISITOR ---> Login , Register , Reset Password , Logout
    ```
    ```mermaid
    flowchart LR
        V(("Visitor")) --- L(["Login"])
        V --- R(["Register"])
        V --- O(["Logout"])
        L -.->|include| VC(["Validate Credentials"])
        L -.->|extend| RP(["Reset Password"])
        VC --- DB(("User Database"))
    ```

    The use case specification
    ```
       USE CASE NAME  Login
       ACTOR          Visitor
       GOAL           Gain access to the protected part of the site.
       PRECONDITION   The visitor has a registered account.
       TRIGGER        The visitor opens the login page.
       POSTCONDITION  A session is created and the visitor is
                      redirected to the home page.

       MAIN FLOW
         1. Visitor opens the login page.
         2. System displays the username and password fields.
         3. Visitor enters username and password and submits.
         4. System validates that neither field is empty.
         5. System looks up the username in the user database.
         6. System hashes the submitted password and compares it with
            the stored hash.
         7. Credentials match -> system creates a SESSION and sets a
            session cookie.
         8. System redirects the visitor to the home page.

       ALTERNATIVE FLOWS
         4a. A FIELD IS EMPTY
               -> "This field is required" , stay on the page.
         6a. USERNAME NOT FOUND , or PASSWORD WRONG
               -> "Invalid username or password" - ONE generic
                  message for BOTH cases.
         6b. THREE CONSECUTIVE FAILURES
               -> lock the account temporarily , notify by email.
         6c. ACCOUNT NOT ACTIVATED or SUSPENDED
               -> the appropriate message ; no session created.
         6d. Visitor clicks "Forgot password"
               -> the Reset Password use case (an <<extend>>).
    ```

    The relationships
    ```
       ASSOCIATION    a plain line - the Visitor performs Login.

       <<include>>    Login ALWAYS validates credentials, so that
                      behaviour is factored out and shared with any
                      other use case needing it.

       <<extend>>     Reset Password happens ONLY IF the visitor has
                      forgotten the password - optional, conditional
                      behaviour, so the arrow points FROM Reset
                      Password TO Login.

       SECONDARY ACTOR  the USER DATABASE sits outside the system
                      boundary and is called on to complete the goal.
    ```
    - One security point that belongs in the answer: step 6a must return a `single generic message` for both a wrong username and a wrong password. Saying "no such user" tells an attacker which usernames exist, which is `user enumeration`.
    - What "high-level" means here: only the actor, the system boundary and the goal-level use cases are shown, with no internal steps. The step-by-step flow above belongs in the `written specification` or in a `sequence diagram` — a use case diagram never shows sequence.

## Software Architecture & Design Patterns (MVC) (13)

1. **Why is it essential to maintain proper MVC structure in web applications?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

   Answer: What MVC is
   - `MVC (Model–View–Controller)` splits an application into three parts: the `Model` holds the data and business rules, the `View` displays them, and the `Controller` handles user input and connects the two.
   ```mermaid
   flowchart LR
       U[User] -->|request| C[Controller]
       C -->|update / query| M[Model]
       M -->|data| C
       C -->|selects| V[View]
       V -->|response| U
   ```

   Why maintaining the structure properly matters

   1. Separation of concerns
   ```
      MODEL      data , validation , business rules , database access
      VIEW       HTML , templates , formatting - PRESENTATION ONLY
      CONTROLLER receives the request , calls the model , chooses
                 the view

      Each layer has ONE job. When SQL queries are written inside a
      view template, the separation is gone and every benefit below
      is lost with it.
   ```

   2. Maintainability
   - A change stays in one layer. Redesigning the user interface touches only `views`; changing a business rule touches only the `model`. Without the separation, one change ripples through the whole application.

   3. Testability
   - The `model` can be unit tested with no browser and no HTTP request, because it has no dependency on the view. Business logic buried inside a template can only be tested by driving the UI, which is slow and fragile.

   4. Parallel development
   - A front-end developer works on views while a back-end developer works on models and controllers, at the same time, with the interface between them fixed.

   5. Reusability
   - One `model` serves a web page, a mobile app and an API — three views over the same business logic. If the logic lives in the view, it must be written three times.

   6. Security
   - Input validation and authorisation belong in the `model` and `controller`. Scattering them through views is how checks get missed. A single, known place for validation is what makes it auditable.

   7. Team discipline and onboarding
   - A new developer knows where to look, because the framework's conventions say where each kind of code belongs. This is the practical reason frameworks enforce the structure.

   What goes wrong when it is not maintained
   ```
      FAT CONTROLLER   business logic creeping into the controller,
           so it cannot be reused or tested independently.
      LOGIC IN THE VIEW  SQL or calculations inside a template - the
           classic sign of a broken MVC application.
      ANAEMIC MODEL    a model that is only a data holder, with all
           the rules elsewhere.

      The result in every case is the same : code that cannot be
      changed safely, cannot be tested, and cannot be reused.
   ```
   - The rule of thumb worth stating: `views should contain no decisions and controllers should contain no business rules`. A controller should read as a short list of calls — validate the request, ask the model, pick a view. Anything longer means logic has leaked out of the model.

2. **What is MVC? Write down the MVC design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*

   Answer: What MVC is
   - `MVC` stands for `Model–View–Controller`. It is an architectural pattern that divides an application into three connected parts, so that the data, the display and the input handling are kept separate.

   The three components
   ```
      MODEL
           The DATA and the BUSINESS LOGIC. It handles validation,
           calculation and database access. It knows nothing about
           how it will be displayed.
           Example : User , Account , Order classes ; the rule that
           a withdrawal may not exceed the balance.

      VIEW
           The PRESENTATION - what the user sees. HTML templates,
           forms, reports. It only DISPLAYS data ; it contains no
           business rules.
           Example : login.html , dashboard.jsp , invoice template.

      CONTROLLER
           The INPUT HANDLER. It receives the user's request,
           validates it, calls the appropriate model, and chooses
           which view to return.
           Example : LoginController , OrderController.
   ```

   The pattern
   ```mermaid
   flowchart LR
       U[User] -->|1. request| C[Controller]
       C -->|2. update or query| M[Model]
       M -->|3. data| C
       C -->|4. selects with data| V[View]
       V -->|5. rendered page| U
   ```
   ```
                   +----------------+
                   |    CONTROLLER  |
           request |  - handles     | selects view
         --------->|    input       |------------+
                   |  - calls model |            |
                   +----------------+            |
                       |        ^                v
           update /    |        | data     +-----------+
           query       v        |          |   VIEW    |
                   +----------------+      |  display  |
                   |     MODEL      |      +-----------+
                   |  - data        |            |
                   |  - business    |            v
                   |    rules       |        to the USER
                   |  - database    |
                   +----------------+
   ```

   Flow of one request — a login
   ```
      1. The user submits the login form.
      2. The CONTROLLER receives POST /login and reads the fields.
      3. The controller calls the MODEL : User.authenticate(u, p).
      4. The MODEL checks the database and returns success or
         failure.
      5. On success the controller selects the DASHBOARD VIEW ; on
         failure it selects the LOGIN VIEW with an error message.
      6. The VIEW renders HTML and it is returned to the user.
   ```

   Advantages
   - `Separation of concerns` — each part has one responsibility, so a change stays in one place.
   - `Maintainability` — redesigning the UI touches only views; changing a business rule touches only the model.
   - `Testability` — the model can be unit tested with no browser and no HTTP request.
   - `Parallel development` — front-end and back-end developers work at the same time.
   - `Reusability` — one model serves a web page, a mobile app and an API.

   Disadvantages
   - More files and more structure, which is overhead for a very small application.
   - A learning curve, and a tendency toward `fat controllers` if business logic is put in the wrong layer.
   - Navigating the layers is harder for someone new to the codebase.

   - Frameworks that implement it: `Spring MVC` and `Struts` (Java), `ASP.NET MVC` (.NET), `Laravel` and `CodeIgniter` (PHP), `Django` (Python, which calls it MTV — Model, Template, View), `Ruby on Rails`.
   - Two variants worth naming: `MVP (Model–View–Presenter)`, where the presenter holds all the display logic and the view is passive, used in Android; and `MVVM (Model–View–ViewModel)`, which adds two-way `data binding`, used in Angular, Vue and WPF.

3. **Name of few architecture in design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 503 (ET: N/A)]*

   Answer: Architectural patterns
   ```
      1. LAYERED (n-tier)
           Presentation -> Business logic -> Data access -> Database.
           Each layer talks only to the one below it.
           Used in : most enterprise and banking applications.

      2. CLIENT-SERVER
           A client requests, a server responds.
           Used in : web applications, email, database systems.

      3. MVC (Model-View-Controller)
           Data , presentation and input handling kept separate.
           Used in : Spring MVC , Laravel , Django , ASP.NET MVC.

      4. MICROSERVICES
           The application is split into small, independently
           deployable services, each with its own database,
           communicating over the network.
           Used in : Netflix , Amazon , Uber.

      5. MONOLITHIC
           The whole application built and deployed as ONE unit.
           Simple, and still correct for small systems.

      6. EVENT-DRIVEN (publish-subscribe)
           Components emit EVENTS ; others subscribe and react. The
           producer does not know who the consumers are.
           Used in : Kafka , message queues , GUI toolkits.

      7. PIPE AND FILTER
           Data flows through a chain of independent processing
           stages, each transforming it.
           Used in : UNIX pipes , compilers , ETL pipelines.

      8. REPOSITORY (data-centred)
           All components share one central data store.
           Used in : IDEs , CASE tools , information systems.

      9. BROKER
           A broker sits between clients and distributed servers and
           routes the requests.
           Used in : CORBA , message brokers.

     10. SERVICE-ORIENTED ARCHITECTURE (SOA)
           Coarse-grained business services, usually over an
           enterprise service bus.

     11. PEER-TO-PEER
           Every node is both client and server.
           Used in : BitTorrent , blockchain.

     12. MASTER-SLAVE
           A master divides work among slaves and combines the
           results.
           Used in : database replication , parallel processing.
   ```

   Design patterns — the GoF classification, for contrast
   ```
      CREATIONAL   how objects are created
           Singleton , Factory Method , Abstract Factory , Builder ,
           Prototype

      STRUCTURAL   how objects are composed
           Adapter , Bridge , Composite , Decorator , Facade ,
           Flyweight , Proxy

      BEHAVIOURAL  how objects interact
           Observer , Strategy , Command , Iterator , State ,
           Template Method , Chain of Responsibility , Mediator ,
           Memento , Visitor , Interpreter
   ```

   The distinction worth stating
   ```
      ARCHITECTURAL PATTERN
           System-wide. Decides the STRUCTURE of the whole
           application - how it is divided and deployed.
           Chosen ONCE, at the start, and expensive to change.
           Example : layered , microservices , MVC.

      DESIGN PATTERN
           Class-level. Solves a RECURRING problem inside one part
           of the code.
           Many are used within a single application.
           Example : Singleton , Observer , Factory.
   ```
   - Where the two meet: `MVC` is usually called an architectural pattern, because it organises the whole application, but it is built out of design patterns — the `Observer` pattern connects model to view, `Strategy` selects a controller action, and `Composite` builds the view hierarchy. That is why some books list MVC under both headings.

4. **What is software design pattern? What are the advantages?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 471 (ET: N/A)]*

   Answer: What a software design pattern is
   - A `design pattern` is a general, reusable `solution to a recurring design problem`. It is not code that can be pasted in — it is a described `structure of classes and their interactions` that can be adapted to a particular situation.
   ```
      The idea comes from Christopher Alexander's work on building
      architecture and was brought into software by the "Gang of
      Four" - Gamma, Helm, Johnson and Vlissides - in DESIGN
      PATTERNS (1994), which documented 23 patterns.

      A pattern is documented with four parts :
           NAME      - so designers can name the idea in one word
           PROBLEM   - when to use it
           SOLUTION  - the classes and their relationships
           CONSEQUENCES - what it costs
   ```

   The three categories
   ```
      CREATIONAL   how objects are CREATED
           Singleton , Factory Method , Abstract Factory , Builder ,
           Prototype

      STRUCTURAL   how objects are COMPOSED
           Adapter , Bridge , Composite , Decorator , Facade ,
           Flyweight , Proxy

      BEHAVIOURAL  how objects INTERACT
           Observer , Strategy , Command , Iterator , State ,
           Template Method , Chain of Responsibility , Mediator ,
           Memento , Visitor
   ```

   Advantages

   1. Proven solutions
   - The pattern has already been tried in many systems, so its strengths and weaknesses are known. Inventing a design from scratch means discovering those weaknesses in production.

   2. A shared vocabulary
   - Saying "use a `Factory` here" conveys in one word what would otherwise take a page of explanation. This is arguably the single biggest practical benefit — patterns give designers a language.

   3. Maintainability and flexibility
   - Patterns are built around `programming to an interface`, so a new variant is added as a new class rather than by editing existing code. That is the `open–closed principle`.
   ```
      Without a pattern :
           if (type == "card")      payByCard();
           else if (type == "cash") payByCash();
           else if (type == "bkash") payByBkash();   <- edit every
                                                        time
      With STRATEGY :
           payment.pay();     <- a new method is a NEW CLASS ;
                                 this line never changes
   ```

   4. Reusability
   - The same structure applies across domains. `Observer` serves a GUI button, a stock-price feed and a database trigger equally well.

   5. Faster development, and better communication
   - A designer who knows the catalogue reaches a workable design faster, and a reviewer recognises the intent immediately from the pattern name.

   6. Easier testing
   - Patterns that use interfaces make it simple to substitute a `mock` object, so units can be tested in isolation.

   Disadvantages, which a complete answer should mention
   ```
      OVER-ENGINEERING - the commonest misuse. Applying a pattern
           where a simple function would do adds classes, indirection
           and confusion for no benefit.
      COMPLEXITY - more classes to understand.
      LEARNING CURVE - the code is unreadable to someone who does not
           know the pattern.
      NOT A SUBSTITUTE FOR DESIGN - a pattern answers a specific
           question ; it does not tell you what to build.
   ```
   - The rule to state at the end: `a pattern should be applied when the problem it solves has actually appeared`, not in anticipation. Patterns are a response to a recurring problem, and using one before the problem exists is how simple code becomes complicated.

5. **Define design pattern. Write about singleton pattern.** *[BREB Assistant Programmer 18.02.2023 compact it 469 (ET: N/A)]*

   Answer: Definition of a design pattern
   - A `design pattern` is a general, reusable `solution to a recurring design problem`. It is not code to be pasted in but a described `structure of classes and their interactions`, which is adapted to the situation at hand. The catalogue of 23 patterns from the `Gang of Four` (1994) divides them into `creational`, `structural` and `behavioural`.

   The Singleton pattern
   - `Singleton` is a `creational` pattern that ensures a class has `exactly one instance` and provides a single global point of access to it.
   ```
      THE PROBLEM it solves : some resources must exist only once -
      a database connection pool, a configuration object, a logger,
      a print spooler. Creating several would waste resources or
      produce inconsistent state.
   ```

   Structure
   ```mermaid
   classDiagram
       class Singleton {
           -static Singleton instance
           -Singleton()
           +static getInstance() Singleton
           +doSomething()
       }
       Singleton --> Singleton : holds its own instance
   ```
   ```
      +--------------------------------------+
      |             Singleton                |
      +--------------------------------------+
      | -static instance : Singleton         |
      +--------------------------------------+
      | -Singleton()          <- PRIVATE     |
      | +static getInstance() : Singleton    |
      | +doSomething()                       |
      +--------------------------------------+
   ```

   The three essential parts
   ```
      1. A PRIVATE CONSTRUCTOR
           so no other class can write  new Singleton()

      2. A PRIVATE STATIC FIELD
           holding the single instance

      3. A PUBLIC STATIC METHOD  getInstance()
           which creates the instance on first call and returns the
           same one every time afterwards
   ```

   Implementation
   ```java
      // LAZY initialisation - created on first use
      public class Logger {
          private static Logger instance;
          private Logger() { }                       // private

          public static Logger getInstance() {
              if (instance == null)
                  instance = new Logger();
              return instance;
          }
          public void log(String msg) {
              System.out.println(msg);
          }
      }

      // usage
      Logger.getInstance().log("started");
   ```
   ```java
      // THREAD-SAFE version - double-checked locking
      public class Logger {
          private static volatile Logger instance;
          private Logger() { }

          public static Logger getInstance() {
              if (instance == null) {
                  synchronized (Logger.class) {
                      if (instance == null)
                          instance = new Logger();
                  }
              }
              return instance;
          }
      }
   ```
   - Why the plain lazy version is unsafe: two threads can both find `instance == null` and both create an object, so two instances exist. `volatile` plus the second check inside the lock fixes it. In Java the simplest correct form is an `enum` singleton, which the language guarantees to be single and thread-safe.

   Where it is used
   ```
      database CONNECTION POOL      one pool for the application
      CONFIGURATION object          one set of settings
      LOGGER                        one log file, written in order
      CACHE                         one shared cache
      PRINT SPOOLER                 one queue for the printer
      java.lang.Runtime             a real Singleton in the JDK
   ```

   Advantages and criticisms
   ```
      ADVANTAGES
        guarantees ONE instance
        a single global access point
        saves memory and resources
        LAZY creation - built only when first needed

      CRITICISMS - and they are serious
        it is GLOBAL STATE in disguise, which couples every user of
             it to the class
        it makes UNIT TESTING hard : the instance cannot easily be
             replaced by a mock, and state leaks between tests
        it hides DEPENDENCIES - a class using Logger.getInstance()
             does not declare that it needs a logger
        it VIOLATES the single-responsibility principle : the class
             controls both its own logic and its own lifetime
        it needs care in a MULTI-THREADED program, and breaks under
             serialisation and reflection unless guarded
   ```
   - The modern alternative worth naming: `dependency injection`. The object is created once by a container and `passed in` to whoever needs it. This gives the same single instance while keeping the dependency visible and replaceable in tests — which is why Singleton is often described as the pattern most frequently misused.

6. **We are going to create a Shape interface and concrete classes implementing the Shape interface. A facade class ShapeMaker is defined as a next step. ShapeMaker class uses the concrete classes to delegate user calls to these classes. FacadePatternDemo, our demo class, will use ShapeMaker class to show the results.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*

   Answer: This describes the `Facade` pattern — a `structural` pattern that provides one simple interface to a set of classes, so the client does not deal with them individually.

   Structure
   ```mermaid
   classDiagram
       class Shape {
           <<interface>>
           +draw()
       }
       class Rectangle {
           +draw()
       }
       class Square {
           +draw()
       }
       class Circle {
           +draw()
       }
       class ShapeMaker {
           -Shape circle
           -Shape rectangle
           -Shape square
           +drawCircle()
           +drawRectangle()
           +drawSquare()
       }
       class FacadePatternDemo
       Shape <|.. Rectangle
       Shape <|.. Square
       Shape <|.. Circle
       ShapeMaker --> Shape : uses
       FacadePatternDemo --> ShapeMaker : uses
   ```
   ```
      +---------------------+        +----------------------------+
      | FacadePatternDemo   |------->|        ShapeMaker          |
      |     (client)        |  uses  |        (FACADE)            |
      +---------------------+        +----------------------------+
                                     | -circle    : Shape         |
                                     | -rectangle : Shape         |
                                     | -square    : Shape         |
                                     +----------------------------+
                                     | +drawCircle()              |
                                     | +drawRectangle()           |
                                     | +drawSquare()              |
                                     +----------------------------+
                                                 | uses
                                                 v
                                     +----------------------------+
                                     |     <<interface>> Shape    |
                                     +----------------------------+
                                     | +draw()                    |
                                     +----------------------------+
                                               /_\  (dashed -
                                                :   realisation)
                                 +--------------+--------------+
                                 |              |              |
                       +-----------+   +-----------+   +-----------+
                       | Rectangle |   |  Square   |   |  Circle   |
                       +-----------+   +-----------+   +-----------+
                       | +draw()   |   | +draw()   |   | +draw()   |
                       +-----------+   +-----------+   +-----------+
   ```

   The code
   ```java
      // 1. the interface
      interface Shape {
          void draw();
      }

      // 2. the concrete classes
      class Rectangle implements Shape {
          public void draw() { System.out.println("Rectangle::draw()"); }
      }
      class Square implements Shape {
          public void draw() { System.out.println("Square::draw()"); }
      }
      class Circle implements Shape {
          public void draw() { System.out.println("Circle::draw()"); }
      }

      // 3. the FACADE
      class ShapeMaker {
          private Shape circle, rectangle, square;

          public ShapeMaker() {
              circle    = new Circle();
              rectangle = new Rectangle();
              square    = new Square();
          }
          public void drawCircle()    { circle.draw();    }
          public void drawRectangle() { rectangle.draw(); }
          public void drawSquare()    { square.draw();    }
      }

      // 4. the client
      public class FacadePatternDemo {
          public static void main(String[] args) {
              ShapeMaker shapeMaker = new ShapeMaker();
              shapeMaker.drawCircle();
              shapeMaker.drawRectangle();
              shapeMaker.drawSquare();
          }
      }
   ```

   Output
   ```
      Circle::draw()
      Rectangle::draw()
      Square::draw()
   ```

   How the four roles map onto the pattern
   ```
      Shape                     the SUBSYSTEM INTERFACE
      Rectangle, Square, Circle the SUBSYSTEM classes - the complex
                                part the client should not have to
                                know about
      ShapeMaker                the FACADE - it CREATES the concrete
                                objects and DELEGATES the calls
      FacadePatternDemo         the CLIENT - it talks only to the
                                facade
   ```
   - What the facade buys: the client writes `shapeMaker.drawCircle()` and never uses `new Circle()`. It does not know which classes exist, how they are constructed, or in what order. If `Triangle` is added, or `Circle` is renamed, `only ShapeMaker changes` — the client is untouched.
   - What the pattern is `not`. `Facade` simplifies an existing interface; `Adapter` converts an interface into a different one the client expects. Facade's purpose is `simplicity`, Adapter's is `compatibility`. Also note that a facade does not hide the subsystem — a client that needs the detail can still use `Circle` directly, which is exactly what distinguishes a facade from an encapsulating wrapper.

7. **Imagine a scenario where new child classes are introduced frequently from a basic class. The method calling sequences for every child class are the same but the implementation is different among the child classes. Here which design pattern would you like to apply? Explain the reasons with examples to support your answer.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

   Answer: Pattern to apply: the `Template Method` pattern.

   Why it fits the scenario exactly
   ```
      The scenario states two things :

      1. "The method calling SEQUENCE for every child class is the
          SAME"                 -> the ALGORITHM is fixed
      2. "the IMPLEMENTATION is DIFFERENT among the child classes"
                                -> the STEPS vary
      3. "new child classes are introduced FREQUENTLY"
                                -> extension must be cheap

      TEMPLATE METHOD is defined as : keep the SKELETON of an
      algorithm in a base class, and let subclasses override the
      individual STEPS without changing the sequence.

      That is a one-to-one match with the requirement.
   ```

   Structure
   ```mermaid
   classDiagram
       class AbstractClass {
           <<abstract>>
           +templateMethod()
           #step1()*
           #step2()*
           #step3()
       }
       class ChildA {
           #step1()
           #step2()
       }
       class ChildB {
           #step1()
           #step2()
       }
       AbstractClass <|-- ChildA
       AbstractClass <|-- ChildB
   ```
   ```
      +------------------------------------------+
      |            AbstractClass                 |
      |              {abstract}                  |
      +------------------------------------------+
      | +templateMethod()   <- FINAL : fixes the |
      |                        SEQUENCE          |
      | #step1()  {abstract} <- subclass MUST    |
      | #step2()  {abstract}    implement        |
      | #step3()             <- default , MAY be |
      |                         overridden       |
      +------------------------------------------+
                       /_\
                        |
             +----------+----------+
             |                     |
      +-------------+       +-------------+
      |   ChildA    |       |   ChildB    |
      +-------------+       +-------------+
      | #step1()    |       | #step1()    |
      | #step2()    |       | #step2()    |
      +-------------+       +-------------+
   ```

   Example — a report generator
   ```java
      abstract class ReportGenerator {

          // THE TEMPLATE METHOD - the sequence is fixed here,
          // and final so no subclass can change the order
          public final void generate() {
              openConnection();      // common - implemented here
              fetchData();           // varies  - subclass
              formatData();          // varies  - subclass
              addHeaderFooter();     // common , may be overridden
              export();              // varies  - subclass
              closeConnection();     // common - implemented here
          }

          private void openConnection()  { /* common code */ }
          private void closeConnection() { /* common code */ }
          protected void addHeaderFooter() { /* default */ }

          protected abstract void fetchData();
          protected abstract void formatData();
          protected abstract void export();
      }

      class SalesReport extends ReportGenerator {
          protected void fetchData()  { /* query the sales tables */ }
          protected void formatData() { /* group by region */ }
          protected void export()     { /* write a PDF */ }
      }

      class PayrollReport extends ReportGenerator {
          protected void fetchData()  { /* query the payroll tables */ }
          protected void formatData() { /* group by department */ }
          protected void export()     { /* write an Excel file */ }
      }
   ```
   ```
      Adding a TaxReport means writing ONE new class with three
      methods. Nothing existing is edited, and the sequence cannot
      accidentally be got wrong - because the base class owns it.
   ```

   Second example — the one everybody knows
   ```
      A COFFEE and TEA maker :

           prepare() {
                boilWater();      // same for both
                brew();           // DIFFERS - coffee vs tea leaves
                pourInCup();      // same for both
                addCondiments();  // DIFFERS - sugar+milk vs lemon
           }

      The sequence is identical ; only two steps differ.
   ```

   Why the alternatives are worse here
   ```
      STRATEGY
           Also swaps behaviour, but it replaces the WHOLE algorithm
           with a different object, and it uses COMPOSITION. It does
           not fix a shared SEQUENCE - and a shared sequence is
           exactly what the scenario specifies. Strategy is the right
           answer when the algorithms have nothing in common.

      FACTORY METHOD
           Decides WHICH object to create. It says nothing about a
           calling sequence. Useful ALONGSIDE Template Method, not
           instead of it.

      ABSTRACT FACTORY
           Creates FAMILIES of related objects - a different problem
           entirely.

      PLAIN INHERITANCE WITH NO TEMPLATE
           Each child writes its own full method. The common steps
           get DUPLICATED in every child, and a new developer can
           easily put them in the wrong order. This is precisely what
           Template Method prevents.
   ```

   - The mechanism that makes it work is the `Hollywood principle` — "don't call us, we'll call you". The base class calls down into the subclass, not the reverse. `Inversion of control` of this kind is why the sequence cannot be violated: the subclass never sees the order at all.
   - One caution worth adding: Template Method uses `inheritance`, so a subclass is tightly bound to its parent, and a change in the base class affects every child. Where the variation is large or must change at run time, `Strategy` — which uses composition — is the better choice. Here, with a fixed sequence and frequent new subclasses, Template Method is correct.

8. **(ক) 'ATM machine' এর Software Structure আঁকুন।** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Software structure of an ATM machine — a `layered architecture`.
   ```
      +==============================================================+
      |                  PRESENTATION LAYER                          |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Screen / UI    |  | Keypad Handler |  | Voice Prompt  |  |
      |   | Manager        |  |                |  |               |  |
      |   +----------------+  +----------------+  +---------------+  |
      +==============================================================+
                                    |
      +==============================================================+
      |               APPLICATION / CONTROL LAYER                    |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Session        |  | Transaction    |  | Menu / Flow   |  |
      |   | Manager        |  | Controller     |  | Controller    |  |
      |   +----------------+  +----------------+  +---------------+  |
      +==============================================================+
                                    |
      +==============================================================+
      |                 BUSINESS LOGIC LAYER                         |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Authentication |  | Withdrawal     |  | Deposit       |  |
      |   | Module (PIN)   |  | Module         |  | Module        |  |
      |   +----------------+  +----------------+  +---------------+  |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Balance /      |  | Fund Transfer  |  | Limit & Rule  |  |
      |   | Statement      |  | Module         |  | Validator     |  |
      |   +----------------+  +----------------+  +---------------+  |
      +==============================================================+
                                    |
      +==============================================================+
      |            DEVICE / HARDWARE ABSTRACTION LAYER               |
      |   +------------+ +------------+ +-----------+ +-----------+  |
      |   | Card       | | Cash       | | Receipt   | | Cash      |  |
      |   | Reader Drv | | Dispenser  | | Printer   | | Acceptor  |  |
      |   +------------+ +------------+ +-----------+ +-----------+  |
      +==============================================================+
                                    |
      +==============================================================+
      |          COMMUNICATION / NETWORK LAYER                       |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Encryption /   |  | Message        |  | Network       |  |
      |   | HSM Interface  |  | Formatter      |  | Client        |  |
      |   |                |  | (ISO 8583)     |  |               |  |
      |   +----------------+  +----------------+  +---------------+  |
      +==============================================================+
                                    |
      +==============================================================+
      |         DATA / LOGGING LAYER                                 |
      |   +----------------+  +----------------+  +---------------+  |
      |   | Local Journal  |  | Audit Trail    |  | Config Store  |  |
      |   +----------------+  +----------------+  +---------------+  |
      +==============================================================+
                                    |
                                    v
                       +---------------------------+
                       |   BANK SWITCH  ->  CORE   |
                       |   BANKING SYSTEM          |
                       |   (external)              |
                       +---------------------------+
   ```
   ```mermaid
   flowchart TD
       A[Presentation: screen, keypad] --> B[Control: session, transaction]
       B --> C[Business logic: auth, withdraw, deposit, limits]
       C --> D[Device layer: card reader, dispenser, printer]
       C --> E[Communication: encryption, ISO 8583, network]
       C --> F[Data: journal, audit log]
       E --> G[(Bank switch / Core banking)]
   ```

   What each layer does
   ```
      PRESENTATION
           Draws the screens, reads the keypad, plays prompts. It
           contains NO business rules - only display and input.

      APPLICATION / CONTROL
           SESSION MANAGER owns one customer's visit from card
           insertion to card return, and enforces the timeouts.
           TRANSACTION CONTROLLER sequences the steps of one
           transaction and is responsible for ROLLBACK if a step
           fails.

      BUSINESS LOGIC
           The rules : PIN verification, three-failure lockout,
           per-transaction and daily limits, valid note multiples,
           available balance. This layer is where the money rules
           live, and it is the layer that must be unit tested
           hardest.

      DEVICE / HARDWARE ABSTRACTION
           One driver per physical device, hiding the hardware behind
           a uniform interface. This is what lets the same software
           run on ATMs from different manufacturers.

      COMMUNICATION
           Formats the request as an ISO 8583 message, encrypts the
           PIN block through the HSM, sends it to the bank switch and
           handles timeouts and RETRIES.

      DATA / LOGGING
           The local JOURNAL - an append-only record of every
           transaction, used for end-of-day reconciliation and
           disputes. It must survive a power cut.
   ```

   The design points that matter
   ```
      TRANSACTION ATOMICITY
           Debit and dispense must both happen or neither. If the
           network drops after the debit, the Transaction Controller
           sends a REVERSAL. This single requirement shapes the whole
           control layer.

      SECURITY BOUNDARY
           The PIN is encrypted inside the HSM and never appears in
           plain form in any other layer or in any log.

      FAIL-SAFE DEFAULT
           On any doubt the ATM refuses service. It must never
           dispense on an unconfirmed authorisation.

      LAYER RULE
           Each layer talks ONLY to the layer directly below it. The
           presentation layer must never call the cash dispenser -
           that is what keeps the money rules in one place.
   ```
   - Why a `layered` architecture is the right choice here rather than, say, microservices: an ATM is a single physical device with hard real-time and safety constraints, and the layers map cleanly onto the separation the security requirements demand — presentation cannot reach the dispenser, and nothing can reach the network without passing through the encryption layer.

9. **(ii) Design the communication for the user login system for an MVC pattern framework.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

   Answer: Communication design for a login system in an MVC framework
   ```mermaid
   sequenceDiagram
       actor User
       participant V as View (login page)
       participant C as Controller (LoginController)
       participant M as Model (User)
       participant DB as Database
       User->>V: enter username, password
       V->>C: POST /login (form data)
       C->>C: validate input not empty
       C->>M: authenticate(username, password)
       M->>DB: SELECT * FROM users WHERE username=?
       DB-->>M: user row + password hash
       M->>M: hash(password) and compare
       alt valid credentials
           M-->>C: User object
           C->>C: create session, store user id
           C-->>V: redirect to dashboard view
           V-->>User: dashboard page
       else invalid credentials
           M->>DB: increment failed_attempts
           M-->>C: null / AuthException
           C-->>V: login view + error message
           V-->>User: "Invalid username or password"
       end
   ```
   ```
      User        VIEW        CONTROLLER      MODEL        DATABASE
       |            |             |             |             |
       | enter      |             |             |             |
       | u/p        |             |             |             |
       |----------->|             |             |             |
       |            | POST /login |             |             |
       |            |------------>|             |             |
       |            |             | [validate   |             |
       |            |             |  not empty] |             |
       |            |             | authenticate|             |
       |            |             |------------>|             |
       |            |             |             | SELECT user |
       |            |             |             |------------>|
       |            |             |             |<- - - - - - |
       |            |             |             | row + hash  |
       |            |             |             | [hash and   |
       |            |             |             |  compare]   |
       |            |             |<- - - - - - |             |
       |            |             | User object |             |
       |            |             | [create     |             |
       |            |             |  session]   |             |
       |            |<- - - - - - |             |             |
       |            | redirect to |             |             |
       |            | dashboard   |             |             |
       |<- - - - - -|             |             |             |
       | dashboard  |             |             |             |

      ------>  call        - - ->  return       [ ]  self-call
   ```

   Responsibility of each component
   ```
      VIEW  -  login.html / login.jsp
           Displays the username and password fields and any error
           message passed to it.
           It contains NO business logic and NO database access -
           presentation only.

      CONTROLLER  -  LoginController
           1. receives POST /login
           2. reads the form fields
           3. performs SHALLOW validation - are the fields present ?
           4. calls the MODEL to authenticate
           5. on success, CREATES THE SESSION and redirects
           6. on failure, returns the login view with an error
           It contains NO SQL and no password checking of its own.

      MODEL  -  User
           authenticate(username, password) :
                fetch the stored SALT and PASSWORD HASH
                hash the submitted password with that salt
                compare in CONSTANT TIME
                increment failed_attempts on failure ; lock after
                     three
                return the User object or null
           ALL business rules live here : the lockout rule, the
           account-active check, the password policy.

      DATABASE
           Stores username, password HASH, salt, failed_attempts,
           account status. The plain password is stored NOWHERE.
   ```

   Where each rule belongs — the design decision being tested
   ```
      Field is empty              -> CONTROLLER  (input validation)
      Password comparison         -> MODEL       (business rule)
      Lock after 3 failures       -> MODEL       (business rule)
      Which page to show next     -> CONTROLLER  (flow control)
      How the error looks         -> VIEW        (presentation)

      Putting the password check in the controller, or SQL in the
      view, is the classic MVC violation. It makes the logic
      untestable and unreusable.
   ```

   The route table
   ```
      GET  /login     LoginController.showForm()   -> login view
      POST /login     LoginController.doLogin()    -> redirect or
                                                      login view
      GET  /logout    LoginController.logout()     -> destroy session
      GET  /dashboard DashboardController.index()  -> requires an
                                                      active session
   ```
   - Two points that carry marks. First, the error message must be a `single generic message` — "Invalid username or password" — for both a wrong username and a wrong password; distinguishing them reveals which accounts exist, which is `user enumeration`. Second, on success the response must be a `redirect`, not a rendered page: the `POST-redirect-GET` pattern stops the browser from re-submitting the login on refresh.
   - Why this layering pays off: because `authenticate()` lives in the model with no dependency on HTTP, the same method serves the web login, a mobile API and an admin console, and it can be `unit tested` with no browser at all.

10. **(i) MVC framework কী? এর সুবিধাগুলো লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 960 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What an MVC framework is
    - An `MVC framework` is a ready-made application skeleton built on the `Model–View–Controller` pattern. It supplies the routing, the request handling, the template engine and the database layer, so the developer writes only the models, views and controllers.
    ```
       MODEL       data and business rules ; database access
       VIEW        presentation - what the user sees
       CONTROLLER  receives the request , calls the model , chooses
                   the view
    ```
    ```mermaid
    flowchart LR
        U[User] -->|1. request| C[Controller]
        C -->|2. query/update| M[Model]
        M -->|3. data| C
        C -->|4. selects| V[View]
        V -->|5. page| U
    ```
    - Examples: `Spring MVC` and `Struts` (Java), `ASP.NET MVC` (.NET), `Laravel` and `CodeIgniter` (PHP), `Django` (Python), `Ruby on Rails`.

    Advantages

    1. Separation of concerns
    - Each part has one job. Changing the screen design touches only `views`; changing a business rule touches only the `model`. Without the separation, one change ripples through the whole application.

    2. Maintainability
    - Code has a known place, so a defect is found and fixed faster. A new developer knows where to look because the framework's conventions decide it.

    3. Testability
    - The `model` can be unit tested with no browser and no HTTP request, because it does not depend on the view. Logic buried in a template can only be tested by driving the UI.

    4. Parallel development
    - Front-end developers work on views while back-end developers work on models and controllers, at the same time.

    5. Reusability
    - One `model` serves a web page, a mobile app and an API — three views over the same business logic.

    6. Multiple views of the same data
    - The same data appears as an HTML table, a PDF and a chart, with no change to the model.

    7. Built-in facilities
    - The framework already provides routing, `ORM`, form validation, session handling, authentication, `CSRF` protection, caching and a template engine — so the developer does not write them again.

    8. Security
    - Validation and authorisation live in known places, so they can be reviewed and audited. Frameworks also supply protection against `SQL injection`, `XSS` and `CSRF` by default.

    9. Faster development, and a common structure
    - Conventions mean less configuration, and every project in the framework looks the same — which matters when a team changes.

    Disadvantages, to note briefly
    ```
       more files and more structure - overhead for a very small site
       a learning curve for the framework's conventions
       a tendency toward FAT CONTROLLERS if logic is put in the wrong
            layer
       navigating the layers is harder for a newcomer
    ```
    - The rule of thumb: `views should contain no decisions and controllers should contain no business rules`. A controller ought to read as a short list of calls — validate, ask the model, pick a view. Anything longer means logic has leaked out of the model, and the benefits above are lost.

11. **MVC framework কী? MVC Framework এর সুবিধাসমূহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What the MVC framework is
    - An `MVC framework` is a ready-made application skeleton built on the `Model–View–Controller` architectural pattern. It provides the routing, request handling, template engine and database layer, so the developer writes only the models, views and controllers.
    ```
       MODEL       the DATA and the BUSINESS RULES - validation,
                   calculation, database access. It knows nothing
                   about how it will be displayed.

       VIEW        the PRESENTATION - HTML templates, forms, reports.
                   It only displays ; it holds no business rules.

       CONTROLLER  the INPUT HANDLER - receives the request, calls
                   the model, and selects which view to return.
    ```
    ```mermaid
    flowchart LR
        U[User] -->|1. request| C[Controller]
        C -->|2. query or update| M[Model]
        M -->|3. data| C
        C -->|4. selects with data| V[View]
        V -->|5. rendered page| U
    ```
    ```
                    +----------------+
            request |   CONTROLLER   | selects view
          --------->|  handles input |------------+
                    |  calls model   |            |
                    +----------------+            v
                        |        ^          +-----------+
            update /    |        | data     |   VIEW    |
            query       v        |          +-----------+
                    +----------------+            |
                    |     MODEL      |            v
                    | data , rules , |        to the USER
                    | database       |
                    +----------------+
    ```
    - Examples: `Spring MVC` and `Struts` (Java), `ASP.NET MVC` (.NET), `Laravel` and `CodeIgniter` (PHP), `Django` (Python), `Ruby on Rails`.

    The advantages
    ```
       1. SEPARATION OF CONCERNS
            Each layer has ONE job, so a change stays in one place.

       2. MAINTAINABILITY
            Redesigning the interface touches only views ; changing a
            business rule touches only the model.

       3. TESTABILITY
            The model can be unit tested with no browser and no HTTP
            request. Logic inside a template can only be tested by
            driving the UI.

       4. PARALLEL DEVELOPMENT
            Front-end and back-end developers work simultaneously,
            with the interface between them fixed.

       5. REUSABILITY
            One model serves a web page, a mobile app and an API.

       6. MULTIPLE VIEWS of the same data - an HTML table, a PDF and
            a chart, with no change to the model.

       7. BUILT-IN FACILITIES
            Routing, ORM, form validation, sessions, authentication,
            CSRF protection, caching and templating come with the
            framework.

       8. SECURITY
            Validation and authorisation sit in known places and can
            be audited. Frameworks give SQL-injection, XSS and CSRF
            protection by default.

       9. FASTER DEVELOPMENT and a COMMON STRUCTURE, so every project
            looks the same and a new developer knows where to look.
    ```

    Disadvantages
    ```
       more files and structure - overhead for a very small site
       a learning curve for the framework's conventions
       FAT CONTROLLERS if business logic is put in the wrong layer
       harder for a newcomer to trace a request through the layers
    ```
    - Two variants worth naming: `MVP (Model–View–Presenter)`, where the presenter holds all display logic and the view is passive, used in Android; and `MVVM (Model–View–ViewModel)`, which adds two-way `data binding`, used in Angular, Vue and WPF.

12. **What is MVC? Write down the MVC design pattern.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175-1176 (ET: N/A)]*

    Answer: What MVC is
    - `MVC` stands for `Model–View–Controller`. It is an architectural pattern that divides an application into three connected parts, so that the data, the display and the input handling are kept separate.

    The three components
    ```
       MODEL
            The DATA and the BUSINESS LOGIC - validation, calculation,
            database access. It knows nothing about how it will be
            displayed.
            Example : User , Account , Order classes ; the rule that a
            withdrawal may not exceed the balance.

       VIEW
            The PRESENTATION - HTML templates, forms, reports. It only
            DISPLAYS data ; it contains no business rules.
            Example : login.html , dashboard.jsp , invoice template.

       CONTROLLER
            The INPUT HANDLER - receives the user's request, validates
            it, calls the model, and chooses which view to return.
            Example : LoginController , OrderController.
    ```

    The MVC design pattern
    ```mermaid
    flowchart LR
        U[User] -->|1. request| C[Controller]
        C -->|2. update or query| M[Model]
        M -->|3. data| C
        C -->|4. selects with data| V[View]
        V -->|5. rendered page| U
    ```
    ```
                    +----------------+
            request |   CONTROLLER   | selects view
          --------->|  handles input |------------+
                    |  calls model   |            |
                    +----------------+            v
                        |        ^          +-----------+
            update /    |        | data     |   VIEW    |
            query       v        |          |  display  |
                    +----------------+      +-----------+
                    |     MODEL      |            |
                    | data           |            v
                    | business rules |        to the USER
                    | database       |
                    +----------------+
    ```

    Flow of one request — a login
    ```
       1. The user submits the login form.
       2. The CONTROLLER receives POST /login and reads the fields.
       3. It calls the MODEL : User.authenticate(username, password).
       4. The MODEL checks the database and returns success or
          failure.
       5. On success the controller creates a session and selects the
          DASHBOARD view ; on failure it selects the LOGIN view with
          an error message.
       6. The VIEW renders the page and it is returned to the user.
    ```

    Where each responsibility belongs
    ```
       Field is empty              -> CONTROLLER  (input validation)
       Password comparison         -> MODEL       (business rule)
       Lock after three failures   -> MODEL       (business rule)
       Which page to show next     -> CONTROLLER  (flow control)
       How the error looks         -> VIEW        (presentation)

       Putting the password check in the controller, or SQL in the
       view, is the classic MVC violation - it makes the logic
       untestable and unreusable.
    ```

    Advantages
    - `Separation of concerns` — each part has one job, so a change stays in one place.
    - `Maintainability` — redesigning the UI touches only views; changing a rule touches only the model.
    - `Testability` — the model can be unit tested with no browser.
    - `Parallel development` — front-end and back-end work simultaneously.
    - `Reusability` — one model serves a web page, a mobile app and an API.

    Disadvantages
    - More files and structure, which is overhead for a very small application; a learning curve; and a tendency toward `fat controllers` when logic is placed in the wrong layer.

    - Frameworks: `Spring MVC`, `Struts`, `ASP.NET MVC`, `Laravel`, `CodeIgniter`, `Django` (which calls it MTV), `Ruby on Rails`. Variants: `MVP`, where a presenter holds the display logic and the view is passive, and `MVVM`, which adds two-way `data binding`.

13. **Explain desin pattern MVC with appropriate figure.** *[NESCO Manager (Software) 2018 compact it 1209 (ET: N/A)]*

    Answer: The MVC design pattern
    - `MVC (Model–View–Controller)` divides an application into three connected parts, so that the data, the display and the input handling are kept separate. It is the standard architecture for web applications.

    The figure
    ```mermaid
    flowchart LR
        U([User]) -->|1. request| C[CONTROLLER<br/>handles input<br/>selects view]
        C -->|2. update / query| M[(MODEL<br/>data<br/>business rules<br/>database)]
        M -->|3. returns data| C
        C -->|4. selects, passes data| V[VIEW<br/>presentation<br/>HTML template]
        V -->|5. rendered page| U
    ```
    ```
                              +---------------------+
                              |     CONTROLLER      |
                  request     |  - receives input   |   selects view
       USER ----------------->|  - validates        |------------------+
         ^                    |  - calls the model  |                  |
         |                    |  - picks the view   |                  |
         |                    +---------------------+                  |
         |                         |            ^                      |
         |            update /     |            |  data                |
         |            query        v            |                      v
         |                    +---------------------+        +--------------------+
         |                    |       MODEL         |        |       VIEW         |
         |                    |  - data             |        |  - HTML template   |
         |                    |  - business rules   |        |  - formatting      |
         |                    |  - validation       |        |  - NO logic        |
         |                    |  - database access  |        +--------------------+
         |                    +---------------------+                  |
         |                             |                               |
         |                             v                               |
         |                        +---------+                          |
         |                        | DATABASE|                          |
         |                        +---------+                          |
         |                                                             |
         +-------------------------- rendered page --------------------+
    ```

    The three components
    ```
       MODEL       the DATA and the BUSINESS RULES. Validation,
                   calculation and database access live here. It
                   knows NOTHING about how it will be displayed -
                   which is what makes it reusable and testable.

       VIEW        the PRESENTATION. Templates, forms and reports.
                   It only DISPLAYS what it is given, and contains no
                   business rules and no database access.

       CONTROLLER  the INPUT HANDLER. Receives the request, performs
                   shallow input validation, calls the model, and
                   chooses which view to return. It contains no SQL
                   and no business rules of its own.
    ```

    Flow of one request
    ```
       1. The user submits a form or clicks a link.
       2. The CONTROLLER receives the request and reads the input.
       3. It calls the MODEL, which applies the business rules and
          reads or writes the database.
       4. The MODEL returns the result.
       5. The CONTROLLER selects a VIEW and hands it the data.
       6. The VIEW renders the page, which is returned to the user.
    ```

    Example — a login
    ```
       POST /login
            CONTROLLER  LoginController.doLogin()
                        - checks the fields are not empty
            MODEL       User.authenticate(username, password)
                        - fetches the stored hash, compares, applies
                          the three-failure lockout rule
            VIEW        dashboard.html on success ,
                        login.html with an error on failure
    ```

    Advantages
    - `Separation of concerns` — each part has one job, so a change stays in one place.
    - `Maintainability` — redesigning the interface touches only views; changing a rule touches only the model.
    - `Testability` — the model can be unit tested with no browser and no HTTP request.
    - `Parallel development` — front-end and back-end developers work at the same time.
    - `Reusability` — one model serves a web page, a mobile app and an API.

    - The rule that keeps the pattern intact: `views contain no decisions and controllers contain no business rules`. A controller should read as a short list of calls. Anything longer means logic has leaked out of the model — the `fat controller` problem, and the commonest way MVC is broken in practice.

## Software Requirements Engineering (10)

1. What is the difference between functional and non-functional requirements? What is requirement validation? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

   Answer: Difference between functional and non-functional requirements

   | Point | Functional requirement | Non-functional requirement |
   |---|---|---|
   | What it states | `What` the system must do | `How well` it must do it |
   | Describes | A feature or behaviour | A quality attribute or constraint |
   | Also called | Behavioural requirements | `Quality attributes`, constraints |
   | If not met | The system is `incomplete` | The system works but is `unusable or unacceptable` |
   | Testing | `Functional` testing — black box | `Non-functional` testing — load, security, usability |
   | Documented as | Use cases, user stories | Measurable targets in the SRS |
   | Example | "The system shall allow a customer to transfer funds" | "A transfer shall complete within 3 seconds" |

   Functional requirements — examples
   ```
      - The system SHALL allow a user to log in with a username and
        password.
      - The system SHALL calculate interest monthly on the closing
        balance.
      - The system SHALL send an email confirmation after every
        transaction.
      - The system SHALL allow an administrator to block an account.
      - The system SHALL generate a monthly statement in PDF.
   ```

   Non-functional requirements — examples
   ```
      PERFORMANCE   a page shall load within 2 seconds under a load
                    of 1000 concurrent users
      RELIABILITY   availability of 99.9 per cent ; MTBF over 1000
                    hours
      SECURITY      passwords stored as a salted hash ; all traffic
                    over TLS ; account locked after 3 failed logins
      USABILITY     a new clerk shall be able to complete a deposit
                    after 30 minutes of training
      SCALABILITY   shall support 10,000 users, growing to 50,000
      PORTABILITY   shall run on Windows, Linux and macOS
      MAINTAINABILITY  a defect shall be fixable within 4 hours
      COMPLIANCE    shall satisfy Bangladesh Bank regulations and
                    retain an audit trail for 7 years
   ```
   - The rule for writing a good non-functional requirement: it must be `measurable`. "The system shall be fast" is useless; "a transfer shall complete within 3 seconds for 95 per cent of requests at peak load" can be tested and accepted or rejected.

   What requirement validation is
   - `Requirement validation` is checking that the requirements in the `SRS` are the `right` requirements — that they genuinely describe what the customer wants — before design and coding begin.
   ```
      VERIFICATION of requirements : are they written correctly ?
      VALIDATION of requirements   : are they the RIGHT ones ?
   ```

   What it checks
   ```
      VALIDITY        does the system really need this ? Different
                      stakeholders often want different things.
      CONSISTENCY     do any two requirements CONTRADICT each other ?
      COMPLETENESS    is every function the customer needs included ?
      REALISM         can it be built with the available technology,
                      budget and time ?
      VERIFIABILITY   can each requirement be TESTED ? "user
                      friendly" cannot ; "30 minutes of training"
                      can.
      UNAMBIGUITY     can it be read in only ONE way ?
      TRACEABILITY    can each requirement be traced to its source
                      and forward to a design element and a test ?
   ```

   The techniques used
   ```
      REQUIREMENT REVIEW    a systematic walkthrough of the SRS with
           the customer and the development team - the commonest and
           most effective method.
      PROTOTYPING           build a model and let the user try it.
           Users cannot describe what they want, but they can react
           to what they see.
      TEST-CASE GENERATION  write the acceptance test for each
           requirement. If a test cannot be written, the requirement
           is not verifiable and must be rewritten.
      MODEL VALIDATION      check the DFDs, ER and UML models for
           consistency with the text.
      CHECKLISTS            a standard list of questions applied to
           every requirement.
   ```
   - Why it is the most valuable quality activity available: a requirement error found in the SRS costs about `1` unit to fix; the same error found after release costs `100 or more`. Validation acts at the far-left of that scale, which is why an SRS review returns more than any other single review.

2. **Which of the following are not needed in software Requirement Specifications (SRS)?** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*
   * (a) Functional Requirments
   * (b) Non- Functional Requirments
   * (c) Testing Requirments
   * (d) Interface Requirments

   Answer: The question asks which items are `not` needed in an SRS. Since the option list was not captured with the question, the answer is given as what an SRS `does` and `does not` contain — the list against which any option can be checked.

   What an SRS must contain
   ```
      IEEE 830 structure :

      1. INTRODUCTION
           purpose , scope , definitions and abbreviations ,
           references , overview

      2. OVERALL DESCRIPTION
           product perspective , product functions , user
           characteristics , operating environment , CONSTRAINTS ,
           ASSUMPTIONS and DEPENDENCIES

      3. SPECIFIC REQUIREMENTS
           FUNCTIONAL requirements - what the system must do
           NON-FUNCTIONAL requirements - performance , reliability ,
                security , usability , portability
           EXTERNAL INTERFACE requirements - user , hardware ,
                software , communication interfaces
           DESIGN CONSTRAINTS - standards, regulations, hardware
                limits the system must respect

      4. APPENDICES and INDEX
   ```

   What is NOT needed in an SRS
   ```
      NOT INCLUDED                       WHERE IT BELONGS INSTEAD
      ---------------------------------  ------------------------
      SOURCE CODE                        implementation phase
      ALGORITHM DETAIL and data
           structures                    design document (SDD)
      DATABASE SCHEMA , table design     design document
      CLASS DIAGRAMS , internal design   design document
      SCREEN LAYOUT DETAIL - exact
           colours, fonts, pixel
           positions                     UI design document
      PROJECT PLAN , SCHEDULE , GANTT
           CHART                         project plan
      COST ESTIMATE and BUDGET           project plan / feasibility
                                         report
      TEAM STRUCTURE , who does what     project plan
      TEST CASES                         test plan
      HOW the requirement will be
           implemented                   design document
      TECHNOLOGY CHOICE , unless it is
           a genuine constraint          design document
   ```

   The principle that decides every case
   ```
      An SRS states WHAT the system must do , NEVER HOW it will do it.

      Anything describing HOW - algorithms, code, schema, class
      design - belongs to the DESIGN phase.
      Anything about MANAGING the work - cost, schedule, staffing -
      belongs to the PROJECT PLAN.
   ```

   The characteristics of a good SRS
   ```
      CORRECT       every requirement stated is genuinely required
      UNAMBIGUOUS   it can be read in only ONE way
      COMPLETE      nothing needed is missing ; no "to be decided"
      CONSISTENT    no two requirements contradict each other
      VERIFIABLE    each one can be TESTED. "user friendly" is not
                    verifiable ; "30 minutes of training" is
      MODIFIABLE    well structured and indexed, so a change is easy
      TRACEABLE     each requirement has an ID, traceable back to its
                    source and forward to design, code and tests
      RANKED        by importance and stability
   ```
   - The two items most often offered as distractors in this kind of question are `algorithm design` and `project schedule`. Both are genuinely `not` part of an SRS: the first belongs in the `design document` and the second in the `project plan`.

3. **(b) Which contents shoud be consider when you setup a new system?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

   Answer: When setting up a new system, the following must be considered.

   1. Requirements
   ```
      FUNCTIONAL     what the system must DO - the features
      NON-FUNCTIONAL how well - performance, security, availability,
                     usability, scalability
      Both must be gathered from ALL stakeholders and recorded in an
      SRS that the customer signs off.
   ```

   2. Feasibility
   ```
      TECHNICAL    do we have the technology and the skills ?
      ECONOMIC     do the benefits exceed the costs ? (ROI, payback)
      OPERATIONAL  will the users actually accept and use it ?
      SCHEDULE     can it be delivered in the time available ?
      LEGAL        does it comply with law, licences and data
                   protection rules ?
   ```

   3. Hardware and infrastructure
   ```
      servers - specification, count, on-premises or cloud
      storage - capacity now, and growth over 3 to 5 years
      network - bandwidth, switches, routers, firewall
      POWER - UPS and generator ; in Bangladesh this is not optional
      air conditioning and physical security of the server room
   ```

   4. Software and platform
   ```
      operating system , database , web server , application
      framework , reporting tools , antivirus
      LICENSING - per user, per core, or open source ; and the cost
      at renewal, not only at purchase
   ```

   5. Security
   ```
      authentication and ROLE-BASED authorisation
      ENCRYPTION - at rest and in transit
      firewall , intrusion detection , patch policy
      AUDIT TRAIL - who did what, and when
      compliance with Bangladesh Bank or other regulations
   ```

   6. Data
   ```
      DATA MIGRATION from the old system - and its CLEANING, which
           is almost always underestimated
      database design , normalisation , indexing
      BACKUP schedule , retention period , and - the part usually
           forgotten - RESTORE TESTING
      archival and retention rules
   ```

   7. Integration
   ```
      which existing systems must it talk to ?
      what interfaces - API , file exchange , message queue ?
      data format and frequency of exchange
   ```

   8. Users and training
   ```
      how many users , in what roles , at which locations
      TRAINING plan and user manuals
      CHANGE MANAGEMENT - people resist a new system, and this is a
           commoner cause of failure than any technical fault
      help desk and support arrangements
   ```

   9. Cost — total cost of ownership
   ```
      Not the purchase price alone :
           hardware , software licences , implementation ,
           customisation , data migration , training , annual
           maintenance , upgrades - over FIVE years
   ```

   10. Deployment and continuity
   ```
      RELEASE STRATEGY : direct , PARALLEL (old and new run
           together) , PILOT (one branch first) , or PHASED
      ROLLBACK PLAN if the new system fails
      DISASTER RECOVERY - RTO and RPO , and a secondary site
      Service Level Agreement with the vendor , and SOURCE CODE
           ESCROW if the vendor closes
   ```

   11. Maintenance and future growth
   ```
      who fixes defects , in what time , under what SLA
      how often are new versions issued , and at what cost
      SCALABILITY - will it still work when the load triples ?
      documentation for whoever maintains it later
   ```

   - The two considerations most often neglected, and most often fatal: `data migration` from the old system, whose cost is routinely underestimated because the old data turns out to be dirty; and `change management` — a technically perfect system that the staff refuse to use has failed. Both belong in the plan from the start, not as afterthoughts at go-live.

4. **You have been given a responsibility to elicit requirements from a customer, who tells you that he is too busy to meet with you. What should you do?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

   Answer: The situation is common, and the answer is not to give up but to `reduce the demand on the customer's time` while still getting the requirements.

   What to do

   1. Explain the cost of not meeting
   - Politely make the consequence explicit: requirements gathered from guesswork produce a system that has to be rebuilt. A requirement error costs about `1` unit to fix now and `100 or more` after release. A short meeting now is far cheaper than the rework later. Framed this way, "too busy" often becomes "half an hour on Thursday".

   2. Ask for a small, specific commitment
   - "Too busy" usually means "not for an open-ended meeting". Ask instead for `30 minutes`, with a written agenda sent in advance and specific questions. A short, prepared meeting is easy to grant.

   3. Identify other stakeholders
   ```
      The CEO is rarely the only source, and often not the best one.
      The people who will USE the system daily know the detail far
      better :
           the clerks who do the work
           the supervisors who check it
           the accounts and audit staff
           the IT staff who will run it

      Requirements should be gathered from EVERY stakeholder group,
      not from one person.
   ```

   4. Use techniques that do not need his time
   ```
      STUDY THE EXISTING SYSTEM - forms, reports, registers,
           procedures. Existing documents carry most of the business
           rules already.
      OBSERVATION - watch the current process being performed.
      QUESTIONNAIRE - written questions the customer can answer when
           convenient, in his own time.
      DOCUMENT ANALYSIS - the organisation's manuals, circulars and
           regulations.
      STUDY SIMILAR SYSTEMS in the same industry.
   ```

   5. Build a prototype and let it do the asking
   ```
      Prepare a PROTOTYPE from what has been gathered and show it
      for 15 minutes.

      People cannot describe what they want, but they can always
      REACT to something in front of them. A prototype extracts more
      in fifteen minutes than an hour of open questions would.
   ```

   6. Send written requirements for confirmation
   - Draft the requirements from the other sources, and send them with a clear request: "please mark anything wrong". Correcting a draft takes a fraction of the time of composing an answer from nothing.

   7. Ask for a delegated representative
   - Request that he nominate someone with authority to answer on his behalf — a `Product Owner`, in Agile terms. Get it agreed in writing that this person's decisions are binding, so the CEO need only see the summary.

   8. Use short, asynchronous channels
   - Email, a shared document with comments, a five-minute phone call, or a video call. Many people who will not attend a meeting will answer three questions in an email.

   9. Record and escalate if it still fails
   ```
      Document in writing that access to the customer was requested
      and not obtained, and record the ASSUMPTIONS made in the SRS
      as a result.

      This is not blame-shifting. It makes the RISK visible to
      management, and it protects the project when a requirement
      later turns out to be wrong. Escalate to the sponsor if the
      project is genuinely blocked.
   ```

   - The judgement to state at the end: a customer who is too busy is a `project risk`, and it should be entered in the risk register with a mitigation. The right response is to `lower the cost of participating` — short meetings, prepared questions, a draft to correct, a prototype to react to — not to proceed on assumptions in silence.

5. **(ক) Software development এর ক্ষেত্রে কত প্রকার requirements পাওয়া যায়। উদাহরণসহ requirements সমূহ লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Requirements are classified in two ways: by `nature` (functional or non-functional) and by `level` (business, user, system).

   Classification by nature

   1. Functional requirements
   - State `what` the system must do — its features and behaviour.
   ```
      - The system SHALL allow a user to log in with a username and
        password.
      - The system SHALL calculate interest monthly on the closing
        balance.
      - The system SHALL send an email confirmation after every
        transaction.
      - The system SHALL allow an administrator to block an account.
      - The system SHALL generate a monthly statement in PDF.
   ```
   - If a functional requirement is not met, the system is `incomplete`.

   2. Non-functional requirements
   - State `how well` the system must do it — the quality attributes and constraints. Also called `quality attributes`.
   ```
      PERFORMANCE      a page shall load within 2 seconds under
                       1000 concurrent users
      RELIABILITY      99.9 per cent availability ; MTBF over 1000
                       hours
      SECURITY         passwords stored as a salted hash ; TLS for
                       all traffic ; lockout after 3 failed logins
      USABILITY        a new clerk shall complete a deposit after 30
                       minutes of training
      SCALABILITY      10,000 users now, growing to 50,000
      PORTABILITY      shall run on Windows, Linux and macOS
      MAINTAINABILITY  a defect shall be fixable within 4 hours
      COMPLIANCE       shall meet Bangladesh Bank rules and retain
                       an audit trail for 7 years
   ```
   - If a non-functional requirement is not met, the system `works but is unacceptable` — correct answers delivered too slowly, or insecurely, are still a failure.
   - The rule for writing one: it must be `measurable`. "The system shall be fast" cannot be tested; "3 seconds for 95 per cent of requests at peak load" can.

   3. Domain requirements
   - Requirements that come from the `application domain` rather than from any user — a banking system must follow accounting rules; a medical system must follow clinical protocols. They are often implicit, and missing one is a common cause of failure because nobody thinks to state what "everybody knows".

   Classification by level
   ```
      BUSINESS REQUIREMENTS
           Why the organisation wants the system, in business terms.
           "Reduce account-opening time from 3 days to 1 day."

      USER REQUIREMENTS
           What a user needs, in the user's own language.
           "A clerk should be able to open an account by filling one
            form."

      SYSTEM REQUIREMENTS
           The detailed technical statement, in the SRS.
           "The system shall validate the NID against the NID
            database within 5 seconds and store the result with a
            timestamp."
   ```

   Two further categories worth naming
   ```
      IMPLEMENTATION / DEPLOYMENT REQUIREMENTS
           server specification , operating system , database
           version , network , installation and rollout plan,
           training and data migration.

      INVERSE (or NEGATIVE) REQUIREMENTS
           what the system must NOT do.
           "The system shall NOT store the CVV of a card."
           Easy to forget, and important in security.
   ```

   - The classification that matters most in practice is `functional against non-functional`, because they are `tested differently`: functional requirements by black-box functional testing, non-functional ones by load, stress, security and usability testing. Projects fail far more often on missed `non-functional` requirements than on missed features — the system does everything asked of it, and does it too slowly to use.

6. **(খ) Software Requirement Specification (SRS) বলতে কি বুঝায়? Software Development এর কোন ধাপে SRS তৈরি করা হয়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What an SRS is
   - A `Software Requirements Specification (SRS)` is the formal document that records `everything the software must do`, agreed and signed off by both the customer and the developer. It is the contract between them and the basis of everything built afterwards.
   ```
      The SRS states WHAT the system must do , NEVER HOW it will do
      it. Anything describing HOW - algorithms, database schema,
      class design - belongs to the DESIGN document.
   ```

   Contents — the IEEE 830 structure
   ```
      1. INTRODUCTION
           purpose , scope , definitions and abbreviations ,
           references , overview

      2. OVERALL DESCRIPTION
           product perspective , product functions , user
           characteristics , operating environment , CONSTRAINTS ,
           ASSUMPTIONS and DEPENDENCIES

      3. SPECIFIC REQUIREMENTS
           FUNCTIONAL requirements     - what the system must do
           NON-FUNCTIONAL requirements - performance, reliability,
                security, usability, portability
           EXTERNAL INTERFACES - user, hardware, software,
                communication
           DESIGN CONSTRAINTS - standards and regulations it must
                respect

      4. APPENDICES and INDEX
   ```

   Characteristics of a good SRS
   ```
      CORRECT       every requirement stated is genuinely required
      UNAMBIGUOUS   it can be read in only ONE way
      COMPLETE      nothing needed is missing ; no "to be decided"
      CONSISTENT    no two requirements contradict each other
      VERIFIABLE    each one can be TESTED. "user friendly" is not
                    verifiable ; "30 minutes of training" is
      MODIFIABLE    well structured and indexed
      TRACEABLE     each requirement has an ID, traceable back to
                    its source and forward to design, code and tests
      RANKED        by importance and stability
   ```

   At which phase the SRS is prepared
   ```
      The SRS is produced in the SECOND phase of the SDLC -
      REQUIREMENT ANALYSIS , also called the requirement gathering
      and analysis phase.

        1. Planning and feasibility study
        2. REQUIREMENT ANALYSIS      <- the SRS is prepared HERE
        3. Design
        4. Coding
        5. Testing
        6. Deployment
        7. Maintenance
   ```
   ```mermaid
   flowchart LR
       A[1. Planning and feasibility] --> B[2. Requirement analysis<br/>SRS produced]
       B --> C[3. Design<br/>SDD produced]
       C --> D[4. Coding]
       D --> E[5. Testing<br/>tests derived from the SRS]
   ```
   - Why that phase and no other: the SRS is the `input` to design, so design cannot begin without it; and it is the `source of the acceptance criteria`, so the testing phase depends on it too. It is signed off at the end of requirement analysis and then placed under `change control` — after that, any change goes through a formal change request rather than a conversation.

   - The reason the document repays the effort spent on it: an error found in the SRS costs about `1` unit to fix, the same error found after release costs `100 or more`. Reviewing the SRS is therefore the single most cost-effective quality activity in the whole life cycle.

7. **Assume that you are going to implement an ecommerce site of “XYZ” company. The CEO of the company is Mr. X. You have to identify the following: (i) Stakeholder (ii) Functional requirements (iii) Non-functional requirements (iv) Deployment requirements** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

   Answer: (i) Stakeholders
   ```
      INTERNAL
        Mr. X , CEO of XYZ          the SPONSOR - funds the project
                                    and sets the business goals
        Marketing / Sales manager   pricing, promotions, campaigns
        Warehouse / Inventory staff stock levels, packing, dispatch
        Accounts / Finance staff    payments, refunds, reconciliation
        Customer support staff      handle complaints and returns
        IT / System administrator   will run and maintain the system
        Site administrator          manages products and users

      EXTERNAL
        CUSTOMERS (buyers)          the PRIMARY users - the most
                                    important stakeholder group
        Suppliers / Vendors         supply the products
        Payment gateway provider    bKash , Nagad , VISA , SSLCOMMERZ
        Courier / Delivery partner  Pathao , Sundarban , RedX
        SMS and email gateway
        Regulators                  VAT authority , consumer rights ,
                                    Bangladesh Bank for payments

      PROJECT SIDE
        Project manager , business analyst , developers , testers ,
        UI/UX designer
   ```
   - The point to make: `Mr. X is the sponsor, not the only stakeholder`. Requirements gathered only from the CEO will miss what the warehouse staff and the customers actually need — and those groups do the daily work.

   (ii) Functional requirements
   ```
      CUSTOMER SIDE
        register and log in ; reset a forgotten password
        browse products by category ; SEARCH and filter by price,
             brand, rating
        view product detail - images, description, price, stock
        add to CART ; update quantity ; remove an item
        maintain a WISHLIST
        CHECKOUT - enter the delivery address, choose a delivery slot
        PAY by card, bKash, Nagad, or cash on delivery
        apply a discount coupon
        receive an order confirmation by email and SMS
        TRACK the order status
        cancel an order , request a RETURN or REFUND
        write a product review and rating
        view order history

      ADMIN SIDE
        add , edit and delete products and categories
        manage stock levels ; receive a low-stock alert
        view and update order status
        process refunds
        manage customers and staff accounts
        set prices, discounts and coupons
        GENERATE REPORTS - sales, stock, revenue, best sellers

      SYSTEM SIDE
        integrate with the PAYMENT GATEWAY
        integrate with the COURIER API for tracking
        send email and SMS notifications
        calculate VAT and delivery charge
   ```

   (iii) Non-functional requirements
   ```
      PERFORMANCE     a product page shall load within 2 seconds ;
           SEARCH shall return results within 1 second ; the site
           shall support 5,000 concurrent users
      SCALABILITY     shall handle a 10-fold traffic increase during
           an Eid campaign without redesign
      AVAILABILITY    99.9 per cent uptime ; planned maintenance
           only between 2 and 4 a.m.
      SECURITY        HTTPS everywhere ; passwords stored as a
           SALTED HASH ; PCI-DSS compliance for card data ; the CVV
           SHALL NOT be stored ; protection against SQL injection,
           XSS and CSRF ; OTP for payment
      USABILITY       checkout in 3 clicks or fewer ; MOBILE
           RESPONSIVE ; Bangla and English interface
      COMPATIBILITY   Chrome, Firefox, Safari, Edge ; Android and
           iOS browsers
      RELIABILITY     no order shall be lost if payment succeeds but
           the network drops - the transaction must be ATOMIC
      BACKUP          daily automated backup ; RESTORE TESTED
           monthly ; RPO 1 hour , RTO 4 hours
      MAINTAINABILITY modular code , documented API , coding
           standards
      LEGAL           VAT calculation per NBR rules ; a privacy
           policy ; 7-year retention of transaction records
      SEO             clean URLs , meta tags , sitemap - a business
           requirement for an e-commerce site, not a luxury
   ```
   - The rule for writing these: every one must be `measurable`. "The site shall be fast" is untestable; "2 seconds for 95 per cent of requests at 5,000 concurrent users" can be accepted or rejected.

   (iv) Deployment requirements
   ```
      INFRASTRUCTURE
        cloud hosting - AWS , Azure or a local provider - with
             auto-scaling
        a CDN for images and static content
        a LOAD BALANCER in front of at least two application servers
        a database server with a REPLICA for failover
        a separate STAGING environment identical to production

      SOFTWARE STACK
        web server , application runtime , database version , cache
        (Redis) , search engine , SSL certificate
        a fixed, documented version of each - "works on my machine"
        is not a deployment plan

      RELEASE PROCESS
        CI/CD pipeline - automated build, test and deploy
        BLUE-GREEN or CANARY release, so a bad version affects few
             users
        a ROLLBACK PLAN and a tested rollback procedure
        DATABASE MIGRATION scripts, versioned and reversible

      DATA
        migration of the existing product catalogue and customer
             list , with CLEANING - almost always underestimated
        daily backup , offsite copy , tested restore

      MONITORING AND SUPPORT
        uptime and performance monitoring , error alerting , log
             aggregation
        a support rota and an SLA for defect response
        DISASTER RECOVERY site with stated RTO and RPO

      GO-LIVE
        a PILOT with limited traffic before full launch
        staff TRAINING and user documentation
        a defined cutover window and a communication plan
   ```
   - The two deployment items most often neglected: a `tested rollback`, and `restore testing` of backups. A backup that has never been restored is not a backup — and both failures only become visible on the day they matter.

8. **Software Requirement Specification (SRS) বলতে কী বোঝেন? Software development -এর কোন স্তরে SRS প্রস্তুত করা হয়?** *[41th BCS 2021 compact it 881 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What an SRS is
   - A `Software Requirements Specification (SRS)` is the formal document that records `everything the software must do`, agreed and signed off by both the customer and the developer. It serves as the contract between them and as the basis for design, coding and testing.
   ```
      The SRS states WHAT the system must do , NEVER HOW it will do
      it. Algorithms, database schema and class design belong to the
      DESIGN document, not here.
   ```

   Contents — IEEE 830
   ```
      1. INTRODUCTION
           purpose , scope , definitions , references , overview

      2. OVERALL DESCRIPTION
           product perspective and functions , user characteristics ,
           operating environment , CONSTRAINTS , ASSUMPTIONS and
           DEPENDENCIES

      3. SPECIFIC REQUIREMENTS
           FUNCTIONAL     - what the system must do
           NON-FUNCTIONAL - performance , reliability , security ,
                usability , portability
           EXTERNAL INTERFACES - user , hardware , software ,
                communication
           DESIGN CONSTRAINTS - standards and regulations

      4. APPENDICES and INDEX
   ```

   Characteristics of a good SRS
   ```
      CORRECT       every requirement stated is genuinely required
      UNAMBIGUOUS   readable in only ONE way
      COMPLETE      nothing needed is missing ; no "to be decided"
      CONSISTENT    no two requirements contradict each other
      VERIFIABLE    each one can be TESTED - "user friendly" cannot
                    be ; "30 minutes of training" can
      MODIFIABLE    well structured and indexed
      TRACEABLE     each has an ID, traceable back to its source and
                    forward to design, code and tests
      RANKED        by importance and stability
   ```

   At which stage the SRS is prepared
   ```
      In the SECOND phase of the SDLC - REQUIREMENT ANALYSIS.

        1. Planning and feasibility study
        2. REQUIREMENT ANALYSIS      <- the SRS is prepared HERE
        3. Design
        4. Coding
        5. Testing
        6. Deployment
        7. Maintenance
   ```
   ```mermaid
   flowchart LR
       A[1. Planning] --> B[2. Requirement analysis<br/>SRS produced and signed off]
       B --> C[3. Design<br/>uses the SRS as input]
       C --> D[4. Coding]
       D --> E[5. Testing<br/>acceptance criteria come from the SRS]
   ```
   - Why that stage: the SRS is the `input to design`, so design cannot start without it, and it is the `source of the acceptance criteria`, so testing depends on it as well. Once signed off it is placed under `change control` — after that, a change goes through a formal change request rather than a conversation.
   - Who prepares it: the `business analyst` or system analyst, working with the customer, and it is `reviewed` by the customer, the development team and the QA team before sign-off.

   - The reason the effort is worth spending: an error found in the SRS costs about `1` unit to fix, and the same error found after release costs `100 or more`. Reviewing the SRS is the single most cost-effective quality activity in the entire life cycle.

9. **(ক) Feasibility Test কী? সফটওয়্যার উন্নয়নে উহার প্রয়োজনীয়তা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a feasibility test is
   - A `feasibility test`, or feasibility study, is the assessment made `before a project starts` to decide whether it is `worth doing and possible to do`. It ends in a recommendation: proceed, revise the scope, or abandon.
   ```
      It is carried out in the FIRST phase of the SDLC - planning -
      and it is the CHEAPEST point at which a bad project can be
      stopped. Cancelling here costs a few weeks of analysis ;
      discovering the same problem after deployment costs the entire
      budget.
   ```

   The five kinds of feasibility
   ```
      TECHNICAL FEASIBILITY
           Do we have the technology, the tools and the SKILLS ?
           Will the existing hardware support it ? Can the
           performance target actually be met ?

      ECONOMIC FEASIBILITY
           Do the benefits exceed the costs ? Measured by COST-
           BENEFIT ANALYSIS , return on investment and PAYBACK
           PERIOD. This is usually the deciding factor.

      OPERATIONAL FEASIBILITY
           Will the users ACCEPT and USE it ? Does it fit the way
           the organisation actually works ? A technically perfect
           system that the staff refuse to use has failed.

      SCHEDULE FEASIBILITY
           Can it be delivered in the time available ? A system
           needed for the next financial year is worthless if it
           arrives after it.

      LEGAL FEASIBILITY
           Does it comply with the law, with licensing, with data-
           protection rules and with the regulator - Bangladesh Bank,
           NBR, and so on ?
   ```

   Why it is necessary in software development

   1. It prevents money being wasted on an impossible project
   - Most large project failures were `predictable at the start`. A feasibility study is the only stage at which cancellation is cheap.

   2. It gives management the information to decide
   - The output is a `feasibility report` with costs, benefits, risks and a recommendation — the basis on which a sponsor approves or refuses funding.

   3. It exposes risk early
   - Technical and business risks are identified while there is still time to plan for them, rather than discovered during testing.

   4. It fixes a realistic scope, budget and schedule
   - The estimates in the project plan come from the feasibility study. Without it, the plan is a guess.

   5. It compares alternatives
   - Build in-house, buy a package, outsource, or upgrade the existing system. Each is costed and scored, so the choice is made on evidence.

   6. It secures stakeholder agreement
   - Because the study consults the users and the sponsor, it builds the agreement the project will need later.

   7. It supplies the acceptance criteria
   - The benefits stated in the study — "reduce account-opening time from 3 days to 1" — become the measures by which the finished system is judged.

   The output
   ```
      THE FEASIBILITY REPORT contains :
           the problem and the objectives
           the alternatives considered
           the recommended alternative, with its costs and benefits
           the risks and their mitigation
           a clear RECOMMENDATION - GO , REVISE , or NO GO
   ```
   - The point worth stating plainly: a feasibility study `can and should conclude that the project should not be done`. A study that always says yes is not a study. Its value lies precisely in its power to stop a project before the money is spent.

10. **(খ) Feasibility Analysis এর বিভিন্ন ধাপসমূহের সংক্ষিপ্ত বিবরণ দিন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1087 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The stages of feasibility analysis
    ```mermaid
    flowchart TD
        A[1. Information assessment] --> B[2. Information collection]
        B --> C[3. Preliminary report]
        C --> D[4. Formulate alternatives]
        D --> E[5. Feasibility analysis]
        E --> F[6. Evaluate and compare]
        F --> G[7. Final report and decision]
    ```

    1. Information assessment
    - Understand the problem and the proposed system. What is wrong with the present arrangement, what should the new system do, who will use it, and what are the constraints of budget, time and law.

    2. Information collection
    - Gather the facts: interviews with users and managers, questionnaires, observation of the current process, study of existing documents, forms and reports, and a look at similar systems elsewhere.

    3. Preliminary report
    - Record the findings so far — the problem statement, the objectives, the scope, and the alternatives being considered.

    4. Formulation of alternatives
    - Draw up two or three `alternative solutions`: build in-house, buy a package, outsource, or upgrade the existing system. Each is described with its technology, cost and timeline.

    5. Feasibility analysis — the core stage
    ```
       Each alternative is tested against five kinds of feasibility :

       TECHNICAL     Do we have the technology, tools and SKILLS ?
            Will the existing hardware support it ? Can the
            performance target be met ?

       ECONOMIC      Do the benefits exceed the costs ?
            COST-BENEFIT ANALYSIS , return on investment ,
            PAYBACK PERIOD , net present value.
            This is usually the deciding factor.

       OPERATIONAL   Will the users ACCEPT and USE it ?
            Does it fit how the organisation actually works ? A
            technically perfect system the staff refuse to use has
            failed.

       SCHEDULE      Can it be delivered in the time available ?
            A system needed for the next financial year is worthless
            if it arrives after it.

       LEGAL         Does it comply with law, licensing, data
            protection and the regulator - Bangladesh Bank, NBR ?
    ```

    6. Evaluation and comparison
    - Score the alternatives against these criteria, weight the criteria by importance, weigh the risks, and select the best option. `Cost-benefit analysis` is the main instrument at this stage.
    ```
       Example of a weighted comparison :

       +-------------+--------+-----------+-----------+-----------+
       | Criterion   | Weight | Build     | Buy       | Outsource |
       +-------------+--------+-----------+-----------+-----------+
       | Cost        |  30 %  |    6      |    8      |     7     |
       | Fit to need |  25 %  |    9      |    6      |     8     |
       | Time        |  20 %  |    4      |    9      |     7     |
       | Risk        |  15 %  |    5      |    8      |     5     |
       | Support     |  10 %  |    7      |    8      |     6     |
       +-------------+--------+-----------+-----------+-----------+
       | WEIGHTED TOTAL       |   6.4     |   7.6     |    7.0    |
       +----------------------+-----------+-----------+-----------+
    ```

    7. Final report and decision
    ```
       THE FEASIBILITY REPORT states :
            the problem and the objectives
            the alternatives considered
            the recommended alternative, with costs and benefits
            the risks and their mitigation
            a clear RECOMMENDATION

       Management then decides :
            GO      - proceed to full development
            REVISE  - adjust the scope, budget or timeline first
            NO GO   - abandon, and consider other options
    ```

    - Two points worth adding. The `number of stages` differs between textbooks — some list five, some eight — because the reporting steps are sometimes merged; but the `five kinds of feasibility` in stage 5 are standard and are what examiners look for. And a feasibility analysis `must be able to conclude "no go"` — a study that always recommends proceeding is not a study, and its whole value lies in the power to stop a project while stopping is still cheap.

## Software Project Management & Organization (9)

1. **সংগঠনিক নির্দেশকগুলো কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Organisational indicators` are the measures an organisation uses to judge how well it is performing and how mature its process is. In software engineering they are the metrics collected across `projects`, not within one project, and they are what drive process improvement.

   Categories of organisational indicator

   1. Process indicators
   ```
      DEFECT DENSITY        defects per KLOC or per function point
      DEFECT REMOVAL
           EFFICIENCY       defects found before release / total
                            defects found
      REVIEW EFFECTIVENESS  defects found per review hour
      PHASE CONTAINMENT     what fraction of defects are caught in
                            the phase that introduced them
      REWORK PERCENTAGE     effort spent redoing work
      CMMI MATURITY LEVEL   1 to 5
   ```

   2. Project performance indicators
   ```
      SCHEDULE VARIANCE     actual duration vs planned
      COST VARIANCE         actual cost vs budget
      EFFORT VARIANCE       actual person-months vs estimated
      ESTIMATION ACCURACY   how close estimates are to actuals
      PRODUCTIVITY          function points or KLOC per person-month
      VELOCITY              story points completed per sprint
      ON-TIME DELIVERY RATE percentage of projects delivered on time
   ```

   3. Product quality indicators
   ```
      RELIABILITY           MTBF , failure rate
      AVAILABILITY          uptime percentage
      CUSTOMER-REPORTED
           DEFECTS          defects found by users after release
      MAINTAINABILITY INDEX
      TEST COVERAGE         statement and branch coverage achieved
   ```

   4. Customer indicators
   ```
      CUSTOMER SATISFACTION score
      NET PROMOTER SCORE
      CUSTOMER RETENTION and repeat business
      SLA COMPLIANCE        percentage of tickets answered in time
      AVERAGE RESOLUTION TIME for a reported defect
   ```

   5. People and resource indicators
   ```
      EMPLOYEE TURNOVER / ATTRITION RATE
      TRAINING HOURS per person per year
      RESOURCE UTILISATION  billable against total hours
      EMPLOYEE SATISFACTION
      SKILL INVENTORY       what competences the organisation holds
   ```

   6. Business indicators
   ```
      REVENUE and PROFIT per project
      RETURN ON INVESTMENT
      MARKET SHARE
      COST OF QUALITY       prevention + appraisal + failure cost
   ```

   How they are used
   ```mermaid
   flowchart LR
       A[Collect data from projects] --> B[Store in an organisational metrics repository]
       B --> C[Analyse trends across projects]
       C --> D[Set baselines and targets]
       D --> E[Improve the process]
       E --> A
   ```
   ```
      The cycle matters more than any single number. One project's
      defect density means little ; the ORGANISATIONAL BASELINE built
      from many projects is what lets a manager say whether a new
      project is going well or badly.

      This is exactly what CMMI level 4 (QUANTITATIVELY MANAGED)
      requires, and what level 5 (OPTIMISING) uses to improve the
      process continuously.
   ```

   - The rule for choosing indicators: they must be `SMART` — specific, measurable, achievable, relevant and time-bound — and there must be `few` of them. An organisation that tracks fifty indicators tracks none of them.
   - The caution worth stating: an indicator used to `judge individuals` stops being a measurement and becomes a target to be gamed. Measure lines of code per programmer and you will get more lines, not better software. Indicators should measure the `process`, not the people.

2. **Which you build about real life software project? What problems you faced during that time and how to solve this?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*

   Answer: A real project — an online loan application system for a bank

   The project
   ```
      A web system allowing customers to apply for a personal loan
      online, and bank officers to review, approve or reject the
      application.

      Team    : 6 people - 1 project manager , 3 developers ,
                1 tester , 1 business analyst
      Duration: 5 months
      Stack   : Java Spring Boot , MySQL , React , deployed on-
                premises
      Model   : Agile , two-week sprints
   ```

   Problem 1 — requirements kept changing
   ```
      PROBLEM
           The loan eligibility rules changed three times during
           development, because the bank's credit policy was itself
           being revised.

      SOLUTION
           We moved the rules OUT of the code and into a RULES TABLE
           in the database, with the officer able to edit the
           thresholds. A rule change then became a data change, not
           a code release.
           We also fixed a formal CHANGE CONTROL process : every
           change request was logged, estimated for impact, and
           approved or deferred to a later sprint.
   ```

   Problem 2 — the customer representative was rarely available
   ```
      PROBLEM
           The branch manager who owned the requirements was too busy
           to attend sprint reviews. Requirements were guessed, and
           two features had to be rebuilt.

      SOLUTION
           We asked for a NOMINATED PRODUCT OWNER with authority to
           decide, and reduced what we asked of them : a 30-minute
           prepared meeting instead of an open one, and a PROTOTYPE
           to react to rather than questions to answer.
           People cannot describe what they want, but they can always
           react to what they see.
   ```

   Problem 3 — integration with the legacy core banking system
   ```
      PROBLEM
           The core banking system was 12 years old, had no API and
           almost no documentation. Its data format was undocumented,
           and the original developers had left.

      SOLUTION
           We built an ADAPTER layer that translated between our
           format and the legacy file format, so no legacy code was
           touched.
           We used a SIMULATOR of the legacy system during
           development, because access to the real one was limited
           to a two-hour window each night.
   ```

   Problem 4 — performance collapsed under load
   ```
      PROBLEM
           The application list page took 40 seconds when the table
           reached 200,000 rows. It had been fast on 500 test rows.

      SOLUTION
           Profiling showed an N+1 QUERY - one query per row to fetch
           the applicant's name.
           We fixed it with a JOIN, added an INDEX on the status and
           date columns, and introduced PAGINATION.
           40 seconds became under 2 seconds.

      LESSON : test with PRODUCTION-SIZED data, not sample data.
           Performance defects are invisible on a small dataset.
   ```

   Problem 5 — a security finding in the audit
   ```
      PROBLEM
           The bank's IT audit found that the document upload
           accepted any file type, and that the application ID was
           sequential and could be guessed - so one customer could
           view another's application.

      SOLUTION
           Restricted uploads by MIME type and size, stored files
           outside the web root, and replaced sequential IDs with
           UUIDs.
           Added an OBJECT-LEVEL AUTHORISATION check on every
           request - the real fix, since hiding the ID alone is not
           security.
   ```

   Problem 6 — the deadline was fixed and the scope was not
   ```
      PROBLEM
           Go-live was tied to a marketing campaign date that could
           not move, and the scope had grown.

      SOLUTION
           We PRIORITISED with MoSCoW - Must, Should, Could, Won't -
           and agreed with the sponsor to release the MUST items on
           the date and the rest in a second release a month later.
           Working software delivered on time with 70 per cent of the
           features was far better than nothing on the date.
   ```

   - The general lessons, stated briefly: `test with realistic data volumes`; `keep volatile business rules out of the code`; `write an adapter rather than modify a legacy system`; and when the date is fixed, `negotiate scope, never quality`. The problems that actually threatened this project were not technical difficulty but `changing requirements`, `customer availability` and `legacy integration` — which is the usual finding.

3. **Project management related question (what are the approaches)** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 520 (ET: MIST)]*

   Answer: Project management approaches

   1. Predictive — Waterfall
   ```
      The whole scope, schedule and budget are fixed at the start,
      and the project runs through the phases once, in order.

      SUITS  : requirements fixed and fully understood ; fixed-price
           contracts ; safety-critical or regulated work.
      FAILS  : when requirements change, because change is very
           expensive and feedback arrives too late.
   ```

   2. Iterative and incremental
   ```
      The product is built and delivered in parts. Each increment is
      a complete mini life cycle producing WORKING SOFTWARE, and
      feedback shapes the next one.

      SUITS  : when early delivery matters and requirements are only
           partly known.
   ```

   3. Agile
   ```
      Short sprints of 1 to 4 weeks, each delivering working
      software, with the customer present throughout.

      FOUR VALUES
        Individuals and interactions over processes and tools
        Working software            over comprehensive documentation
        Customer collaboration      over contract negotiation
        Responding to change        over following a plan

      FRAMEWORKS
        SCRUM   sprints ; Product Owner , Scrum Master , team ;
                daily stand-up , review , retrospective
        KANBAN  visualise the work , LIMIT WORK IN PROGRESS ,
                continuous flow with no fixed sprints
        XP      pair programming , TDD , continuous integration
        SAFe , LeSS   Agile scaled to large organisations
   ```

   4. Spiral — risk-driven
   ```
      Each loop has four quadrants : set objectives , IDENTIFY AND
      RESOLVE RISKS with a prototype , develop and verify , plan the
      next loop.

      SUITS  : large, expensive, uncertain systems, where the risk of
           failure is itself the main problem.
      COSTS  : the repeated risk analysis is expensive, so it is
           wrong for small projects.
   ```

   5. Critical Path Method and PERT
   ```
      The project is broken into activities with dependencies, and
      the CRITICAL PATH - the longest chain, which has no slack -
      determines the shortest possible duration.

           A(3) --> B(5) --> D(4)
                       \       /
                        C(2)--+

           Path A-B-D = 12 days   <- CRITICAL PATH
           Path A-C-D =  9 days   -> 3 days of slack

      Any delay on the CRITICAL PATH delays the whole project ;
      delay elsewhere may not.

      PERT adds three-point estimation :
           expected time = (optimistic + 4*most likely + pessimistic)
                           / 6
   ```

   6. PRINCE2 and PMBOK
   ```
      PRINCE2  a process-based method - business case, defined roles,
           stages, and management by exception. Widely used in
           government.
      PMBOK    the PMI body of knowledge : 5 process groups
           (initiating, planning, executing, monitoring and
           controlling, closing) and 10 knowledge areas (scope, time,
           cost, quality, resource, communication, risk,
           procurement, stakeholder, integration).
   ```

   7. Lean and Six Sigma
   ```
      LEAN       eliminate WASTE - anything not adding customer
           value. Deliver as late as responsibly possible, decide as
           late as possible.
      SIX SIGMA  reduce VARIATION using DMAIC - Define , Measure ,
           Analyse , Improve , Control.
   ```

   8. Hybrid — what large organisations actually do
   ```
      Waterfall-style planning, architecture and contract UP FRONT,
      to satisfy the tender and the auditors ; AGILE SPRINTS for the
      build.

      Banks and government projects in Bangladesh usually work this
      way rather than adopting either model in pure form.
   ```

   Choosing between them
   ```
      +------------------+------------------+---------------------+
      | Condition        | Approach         | Reason              |
      +------------------+------------------+---------------------+
      | Requirements     | WATERFALL        | scope can be fixed  |
      | fixed and known  |                  | and priced          |
      | Requirements     | AGILE            | change is expected  |
      | unclear/changing |                  |                     |
      | Large, risky,    | SPIRAL           | risk is analysed    |
      | expensive        |                  | each loop           |
      | Fixed date,      | AGILE + MoSCoW   | negotiate SCOPE,    |
      | flexible scope   |                  | never quality       |
      | Government       | HYBRID / PRINCE2 | contract needs a    |
      | tender           |                  | fixed specification |
      +------------------+------------------+---------------------+
   ```
   - The judgement to state: there is no universally best approach. The deciding question is `how well the requirements are known` and `how much the customer can be involved`. A well-run Waterfall project beats a badly-run Agile one, and the commonest cause of failure is adopting a method whose preconditions the organisation cannot meet.

4. **(খ) User story ও Product backlog কী?** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) User story
   - A `user story` is a short, plain-language description of a feature, written from the `user's point of view`. It states who wants it, what they want, and why.
   ```
      THE STANDARD FORMAT

           As a  <type of user> ,
           I want <some goal> ,
           so that <some benefit / reason>.

      EXAMPLES

           As a CUSTOMER , I want to reset my password , so that I
           can log in again if I forget it.

           As a BANK OFFICER , I want to see a list of pending loan
           applications , so that I can process them in order.

           As an ADMIN , I want to block a user account , so that a
           compromised account cannot be used.
   ```
   ```
      ACCEPTANCE CRITERIA are attached to each story - the
      conditions that decide when it is DONE :

           Given the user clicks "Forgot password"
           When a registered email address is entered
           Then a reset link is emailed and expires in 30 minutes
   ```
   - The three parts a good story satisfies, called the `3 Cs`: the `Card` (the short written statement), the `Conversation` (the discussion it triggers, where the real detail emerges) and the `Confirmation` (the acceptance criteria).
   - The quality test is `INVEST`: `Independent`, `Negotiable`, `Valuable`, `Estimable`, `Small`, `Testable`.
   ```
      THE POINT OF A USER STORY is that it is deliberately BRIEF.
      It is a PLACEHOLDER FOR A CONVERSATION, not a specification.
      A story that tries to state every detail has defeated its own
      purpose - that is what an SRS is for.
   ```
   - Stories are estimated in `story points` — relative size, not hours — usually by `planning poker` with the whole team.

   Product backlog
   - The `product backlog` is the single, `prioritised list of everything wanted` in the product — features, changes, defect fixes and technical work. It is owned by the `Product Owner`.
   ```
      PRODUCT BACKLOG  (highest priority at the top)
      +----+--------------------------------------+--------+------+
      | ID | User story                           | Points | Pri  |
      +----+--------------------------------------+--------+------+
      | 12 | As a customer, I want to reset my    |   3    | High |
      |    | password ...                         |        |      |
      | 07 | As a customer, I want to view my     |   5    | High |
      |    | transaction history ...              |        |      |
      | 21 | As an admin, I want to export a      |   8    | Med  |
      |    | monthly report ...                   |        |      |
      | 34 | As a customer, I want dark mode ...  |   2    | Low  |
      +----+--------------------------------------+--------+------+
   ```
   ```
      PROPERTIES

      ORDERED     the most valuable item is at the TOP. Everything
                  has a position ; nothing is "equally important".
      DYNAMIC     it is never finished. Items are added, removed and
                  re-ordered every sprint - this is what makes Agile
                  able to absorb change.
      DETAILED
      APPROPRIATELY  items near the TOP are small and fully
                  detailed, ready to be worked on. Items lower down
                  are large and vague, and are refined only when they
                  come closer. This is DEEP - Detailed appropriately,
                  Emergent, Estimated, Prioritised.
      ESTIMATED   each item carries a size in story points.
      SINGLE      there is ONE backlog per product, however many
                  teams work on it.
   ```

   How the two work together
   ```mermaid
   flowchart LR
       A[Product Backlog<br/>all user stories, prioritised] --> B[Sprint Planning]
       B --> C[Sprint Backlog<br/>stories chosen for this sprint]
       C --> D[Sprint: 1-4 weeks]
       D --> E[Working increment]
       E --> F[Review + Retrospective]
       F --> A
   ```
   ```
      PRODUCT BACKLOG   everything wanted , ever         owned by the
                                                         PRODUCT OWNER
      SPRINT BACKLOG    what THIS sprint will deliver    owned by the
                                                         TEAM
   ```
   - `Backlog refinement` (or grooming) is the regular session in which the team and the Product Owner break large items down, add detail and estimate — so that the top of the backlog is always ready for the next sprint planning.

5. **Assume you are a project manager and your job is to develop an application which is similar to what you have developed is past only larger and complex. The customer has documented the requirements clearly. What team structure would you choose in this case and why?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*

   Answer: Team structure chosen: the `Chief Programmer team` — a `centralised control` structure.

   Why the scenario points to it
   ```
      The question gives three facts, and each one favours
      centralised control :

      1. "similar to what you have developed in the past"
           -> the problem is UNDERSTOOD. There is no need for group
              exploration or debate ; the solution approach is
              already known.

      2. "the requirements are DOCUMENTED CLEARLY"
           -> there is little uncertainty to resolve by discussion.
              A democratic structure earns its cost by exploring
              unknowns, and here there are few.

      3. "LARGER and more COMPLEX"
           -> a bigger team. Democratic structures do not scale :
              communication paths grow as n(n-1)/2 , so a team of 12
              has 66 channels and consensus becomes impossible.
   ```

   The chief programmer structure
   ```
                       +----------------------+
                       |  CHIEF PROGRAMMER    |
                       |  - designs the system|
                       |  - writes the        |
                       |    critical modules  |
                       |  - assigns work      |
                       |  - makes ALL         |
                       |    technical         |
                       |    decisions         |
                       +----------------------+
                          /      |        \
                         /       |         \
             +-----------+  +-----------+  +-------------+
             | Backup    |  | Librarian |  | Programmers |
             | Programmer|  | (docs,    |  | (2 to 6)    |
             | (deputy)  |  |  builds,  |  |             |
             +-----------+  |  records) |  +-------------+
                            +-----------+
                                   |
                            +-------------+
                            | Specialists |
                            | (DBA, tester|
                            |  UI, admin) |
                            +-------------+
   ```
   ```
      ROLES
        CHIEF PROGRAMMER   a senior, experienced engineer with full
             technical AND administrative authority. Designs the
             system and writes the hardest parts personally.
        BACKUP PROGRAMMER  the deputy - understands the whole design
             and can take over. This role exists precisely to remove
             the single-point-of-failure risk.
        LIBRARIAN          maintains documentation, source control,
             builds and records, so the programmers are not
             distracted by administration.
        PROGRAMMERS        implement the modules assigned to them.
        SPECIALISTS        DBA , tester , UI designer as needed.
   ```

   Why it fits this project
   ```
      FAST DECISIONS       one person decides, so no time is lost to
           consensus. With clear requirements there is little to
           debate.
      REUSE OF EXPERIENCE  the chief programmer has built this kind
           of system before, and that knowledge is applied directly
           to the design rather than rediscovered by the group.
      SCALES to a large team  work is decomposed and assigned ;
           communication is through the chief, so it grows linearly
           rather than quadratically.
      DESIGN CONSISTENCY   one architect means one coherent
           architecture - important as complexity grows.
      PREDICTABLE SCHEDULE clear ownership and clear assignment make
           progress easy to track, which matters on a fixed-scope
           project.
   ```

   The risks, and how they are managed
   ```
      SINGLE POINT OF FAILURE   if the chief programmer leaves or
           falls ill, the project stalls.
           -> the BACKUP PROGRAMMER role exists for exactly this ;
              the design must also be documented, not held in one
              head.

      LOWER MORALE and less creativity   juniors have little say and
           report lower job satisfaction in this structure.
           -> delegate module-level design decisions, hold design
              reviews where anyone may object, and rotate people
              through harder work.

      BOTTLENECK            every decision waits on one person.
           -> delegate within modules ; the chief decides ACROSS
              module boundaries only.
   ```

   The alternatives, and why they are rejected here
   ```
      DEMOCRATIC (egoless) TEAM
           No fixed leader ; decisions by consensus ; high morale and
           creativity.
           BEST FOR : small teams (under 5-8) , RESEARCH-type or
                POORLY UNDERSTOOD problems , long projects.
           REJECTED : this problem is well understood and the team is
                large. Consensus would only slow it down.

      MIXED CONTROL TEAM
           A hierarchy of small democratic groups, each reporting
           upward - democratic within a group, centralised between
           groups.
           THE SERIOUS ALTERNATIVE. If the team is very large - say
           over 15 - I would choose this instead : the chief
           programmer structure alone starts to bottleneck at that
           size, while mixed control keeps decisions local and
           scales further.
   ```

   - The general rule the answer rests on: `democratic structures suit uncertainty and small teams; centralised structures suit understood problems and large teams`. This project is an understood problem with a large team and documented requirements, so `chief programmer` is correct — moving to `mixed control` if the team grows beyond about fifteen people.

6. **a) What is conflict in git? How to resolve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

   Answer: What a Git conflict is
   - A `merge conflict` happens when two branches change the `same lines of the same file` in different ways, and Git cannot decide which version is correct. It stops and asks a human.
   ```
      Git merges automatically when the changes are in DIFFERENT
      places. It CANNOT merge when :

        - the same LINES were edited on both branches
        - one branch DELETED a file the other MODIFIED
        - both branches ADDED a file with the same name but
          different content
        - a file was RENAMED on one branch and edited on the other
   ```
   ```
      $ git merge feature-login
      Auto-merging src/login.js
      CONFLICT (content): Merge conflict in src/login.js
      Automatic merge failed; fix conflicts and then commit the result.
   ```

   What the conflict looks like in the file
   ```
      <<<<<<< HEAD
      const timeout = 30;          <- YOUR version (current branch)
      =======
      const timeout = 60;          <- THEIR version (incoming branch)
      >>>>>>> feature-login
   ```
   ```
      <<<<<<< HEAD        marks the start of YOUR changes
      =======             separates the two versions
      >>>>>>> branch      marks the end of THEIR changes
   ```

   How to resolve it
   ```
      1. SEE which files are in conflict

           git status
           git diff --name-only --diff-filter=U

      2. OPEN each conflicted file and decide what the code SHOULD
         be. There are three possibilities :

           keep YOURS      delete their block and the markers
           keep THEIRS     delete your block and the markers
           COMBINE BOTH    write the correct merged code by hand -
                           this is the commonest and correct answer

         REMOVE ALL THREE MARKERS - <<<<<<< , ======= , >>>>>>>
         Leaving one in the file is the classic mistake ; the code
         will not even compile.

      3. TEST the result. A resolved conflict that was never run is
         not resolved.

      4. STAGE and COMMIT

           git add src/login.js
           git commit               # Git supplies a merge message
   ```

   Shortcuts for whole-file resolution
   ```
      git checkout --ours   <file>    keep the current branch's
                                      version entirely
      git checkout --theirs <file>    keep the incoming version
                                      entirely
      git mergetool                   open a 3-way visual merge tool
      git merge --abort               cancel the merge and go back to
                                      where you were - the safe way
                                      out if the conflict is a mess
      git rebase --abort              the same, during a rebase
   ```
   ```
      CAUTION with --ours / --theirs : they take the WHOLE FILE, not
      the conflicting lines. Any good change from the other side is
      silently lost. Use them only when one version is genuinely
      correct in its entirety.
   ```
   ```
      NOTE that "ours" and "theirs" SWAP MEANING during a REBASE :
           in a MERGE  : ours = your branch , theirs = incoming
           in a REBASE : ours = the branch being rebased ONTO ,
                         theirs = your commits
      This reversal causes real mistakes, so check with git status
      before using either flag.
   ```

   How to reduce conflicts in the first place
   ```
      PULL and MERGE FREQUENTLY - a branch that diverges for two
           weeks conflicts far more than one merged daily.
      SMALL, FOCUSED COMMITS in one area of the code.
      AGREE OWNERSHIP - if two people must edit the same file, talk
           first.
      AGREE ON FORMATTING - an auto-formatter that reindents a whole
           file creates conflicts on every line for no reason.
      NEVER COMMIT generated files, build output or IDE settings ;
           put them in .gitignore.
      COMMUNICATE - most conflicts are an organisational problem
           showing up as a technical one.
   ```
   - The point worth stating: a conflict is `not an error`. It is Git correctly refusing to guess. The resolution is a `human decision about what the code should do`, and the only way to confirm it is right is to `run the tests afterwards`.

7. **b) Write down the difference between Patch and Upgrade.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

   Answer: Difference between a patch and an upgrade

   | Point | Patch | Upgrade |
   |---|---|---|
   | Purpose | `Fix` a specific defect or security hole | Move to a `newer version` with new features |
   | Size | `Small` — a few files | `Large` — often the whole product |
   | Scope | One problem | The entire application |
   | Version number | Changes the `last` digit — 2.1.3 → 2.1.4 | Changes the `major or minor` — 2.1 → 3.0 |
   | New features | `None` | `Yes` |
   | Frequency | Often — sometimes weekly | Rarely — every year or two |
   | Cost | Usually `free` under the support contract | Often `paid` |
   | Downtime | Little or none | Significant — planning required |
   | Risk | Low | `High` — behaviour may change |
   | Reversible | Easily uninstalled | Hard to reverse; needs a full backup |
   | Testing needed | Regression test the affected area | `Full` regression test |
   | User retraining | None | Often needed |

   Patch
   ```
      A small piece of code released to CORRECT a specific problem
      in software already installed.

      TYPES
        BUG FIX PATCH      corrects a defect
        SECURITY PATCH     closes a vulnerability. The most urgent -
             "Patch Tuesday" exists for these.
        HOTFIX             an emergency patch, released outside the
             normal schedule for a critical fault in production.
        SERVICE PACK       a bundle of many patches, released
             together.

      Example : Windows 10 build 19045.3570 -> 19045.3693
                MySQL 8.0.34 -> 8.0.35
   ```

   Upgrade
   ```
      Replacing the software with a NEWER VERSION that has new
      features, a changed interface, or a new architecture.

      Example : Windows 10  -> Windows 11
                MySQL 5.7   -> MySQL 8.0
                Office 2019 -> Office 365
   ```

   Semantic versioning — how the numbers say which is which
   ```
           MAJOR . MINOR . PATCH

             3   .   2   .   5

      PATCH  (5)  a backward-compatible BUG FIX     -> a PATCH
      MINOR  (2)  new features, still backward
                  compatible                        -> an UPGRADE
      MAJOR  (3)  BREAKING CHANGES                  -> an UPGRADE ,
                  and the risky kind
   ```

   The related term
   ```
      UPDATE is often used loosely for either. Strictly it sits
      between the two : it may add small features as well as fix
      defects, but it does not change the major version.

           PATCH   -> fix only
           UPDATE  -> fix + small improvements
           UPGRADE -> new version , new features , possible breaking
                      changes
   ```

   What each requires in practice
   ```
      BEFORE A PATCH
           read the release note ; test in staging ; regression test
           the affected area ; apply in a maintenance window.

      BEFORE AN UPGRADE
           FULL BACKUP and a TESTED ROLLBACK plan
           check hardware and licence requirements
           check COMPATIBILITY of every integration and plugin
           full regression test in a staging environment
           DATA MIGRATION scripts, versioned and reversible
           user TRAINING and documentation
           a defined cutover window and a communication plan
   ```
   - The judgement to state: `security patches should be applied promptly` — an unpatched known vulnerability is the commonest route into a system. `Upgrades should be planned`, because they change behaviour, may break integrations, and are hard to reverse. Treating an upgrade with the casualness appropriate to a patch is how production outages happen.

8. **Qualification of a good team leader.** *[NESCO Manager (Software) 2018 compact it 1208-1209 (ET: N/A)]*

   Answer: Qualifications of a good team leader

   Technical qualifications
   ```
      TECHNICAL COMPETENCE
           Enough depth to judge a design, review code and estimate
           realistically. A leader who cannot read the code cannot
           tell whether the team is in trouble.

      PROBLEM SOLVING
           Breaks a large problem into parts and decides between
           alternatives on evidence rather than preference.

      DOMAIN KNOWLEDGE
           Understands the business the software serves - banking
           rules, accounting practice - so requirements are
           challenged when they are wrong.

      PLANNING AND ESTIMATION
           Breaks work down, estimates, tracks progress, and adjusts
           when the estimate proves wrong.
   ```

   Management qualifications
   ```
      DECISION MAKING
           Decides with incomplete information, and decides in time.
           An undecided leader is worse than a wrong one, because the
           team stops.

      DELEGATION
           Assigns work by skill and then LEAVES IT ALONE. A leader
           who does everything personally becomes the bottleneck.

      ORGANISATION and TIME MANAGEMENT
           Prioritises, and protects the team's time from
           interruption.

      RISK MANAGEMENT
           Identifies what could go wrong early, and plans for it
           rather than reacting to it.
   ```

   Communication qualifications
   ```
      CLEAR COMMUNICATION
           Explains the same thing in the right register to a
           developer, a customer and a manager.

      LISTENING
           The single most underrated quality. A leader who does not
           listen never learns that the project is late until it is.

      UPWARD HONESTY
           Reports bad news to management EARLY and accurately. A
           leader who hides slippage guarantees a crisis.

      NEGOTIATION
           Negotiates scope, deadlines and resources with the
           sponsor - and negotiates SCOPE, never quality.
   ```

   Personal qualities
   ```
      INTEGRITY and FAIRNESS
           Gives credit where it is due, takes responsibility for
           failure, treats everyone by the same standard. Without
           this nothing else works, because the team will not
           follow.

      ACCOUNTABILITY
           Owns the outcome. "The team failed" is not a report a
           good leader makes.

      MOTIVATION and EMPATHY
           Knows what each person wants from the work, and notices
           when someone is struggling before it shows in the
           schedule.

      CALM UNDER PRESSURE
           Production is down at 2 a.m. The leader's job is to stay
           methodical, because panic spreads faster than any
           instruction.

      ADAPTABILITY
           Requirements change, people leave, technology moves. A
           leader attached to the original plan fails with it.

      WILLINGNESS TO LEARN, AND TO BE CORRECTED
           A leader who cannot be told they are wrong will be told
           nothing.
   ```

   Leadership behaviour
   ```
      LEADS BY EXAMPLE      follows the standards demanded of others
      SHIELDS THE TEAM      absorbs interruptions and political
                            pressure so the team can work
      DEVELOPS PEOPLE       mentors, and creates a successor. A
                            leader whose team cannot function
                            without them has failed at this
      GIVES FEEDBACK        specific, timely, and in private when
                            critical
      BUILDS TRUST          a team that fears blame hides problems,
                            and hidden problems are the ones that
                            kill projects
   ```

   - The distinction worth stating: a `manager` administers the plan; a `leader` makes the team want to deliver it. In software the leader also has to be `technically credible`, because engineers do not follow someone who cannot judge their work. The two qualities that matter most in practice are `honest upward reporting` and `psychological safety` — a leader who reports slippage early and whose team is not afraid to admit a mistake will recover from almost anything, and a leader lacking either will be surprised by failure.

9. **Write down pros and cons over qualification candidate.** *[NESCO Manager (Software) 2018 compact it 1210-1211 (ET: N/A)]*

   Answer: The question is `incomplete` — the specific candidate, post or comparison being asked about was not captured, so the exact answer cannot be given. What such a question tests is `how to weigh the strengths and weaknesses of a candidate against a job's requirements`, and that framework is given below.

   The framework: judge the candidate against the requirement, not in the abstract
   ```
      Every strength and weakness matters only in relation to what
      the POST actually needs. A brilliant researcher is a poor
      choice for a maintenance role, and the reverse is equally
      true.
   ```

   Pros of a highly qualified candidate
   ```
      TECHNICAL DEPTH        productive from an early stage ; needs
           less supervision and less training.
      JUDGEMENT              has seen the failure modes before, so
           designs and estimates are more realistic.
      MENTORING              raises the whole team's level, not only
           their own output.
      CREDIBILITY            with customers, auditors and regulators.
      FASTER PROBLEM SOLVING on the difficult problems, which is
           where most schedule risk lies.
   ```

   Cons of a highly qualified candidate
   ```
      COST                   a higher salary, and possibly a
           distortion of the existing pay structure.
      RETENTION RISK         likely to leave for a better offer,
           especially if the work is below their level.
      OVER-QUALIFICATION     a person given routine work becomes
           bored and disengaged - a real and common failure.
      RIGIDITY               long experience with one approach can
           become resistance to a different one.
      TEAM FIT               may not accept direction from a less
           experienced lead.
   ```

   Pros of a less qualified but promising candidate
   ```
      COST                   affordable, and easier to justify.
      TRAINABILITY           learns the organisation's way of working
           rather than importing another's.
      LOYALTY                a person developed in-house tends to
           stay longer.
      ENTHUSIASM             and willingness to take on unglamorous
           work.
      SUCCESSION             builds the organisation's future
           capability.
   ```

   Cons of a less qualified candidate
   ```
      TRAINING COST and TIME before they are productive.
      SUPERVISION            consumes a senior person's time - a
           hidden cost that is routinely underestimated.
      RISK on critical work  a mistake in a payment or security
           module is expensive.
      NO INDEPENDENT
           JUDGEMENT yet     needs their design decisions reviewed.
   ```

   How to decide
   ```
      1. SEPARATE the ESSENTIAL from the DESIRABLE in the job
         specification. Most requirement lists confuse the two.

      2. Ask WHAT THE ROLE ACTUALLY NEEDS :
           a NEW, DIFFICULT system      -> favour experience
           MAINTENANCE and support      -> favour trainability and
                                           retention
           a REGULATED or SAFETY-
                critical module         -> favour experience,
                                           without exception
           a LARGE TEAM to be built     -> hire one senior to mentor
                                           several juniors

      3. Consider the TEAM as a whole, not the individual. A team of
         all seniors is expensive and argumentative ; a team of all
         juniors has nobody to learn from. A MIX is almost always
         right.

      4. Test rather than assume. A structured technical exercise on
         REAL work tells more than a certificate or a years-of-
         experience count.

      5. Score against WEIGHTED criteria, so the decision is
         recorded and defensible :

         +------------------+--------+-------------+-------------+
         | Criterion        | Weight | Candidate A | Candidate B |
         +------------------+--------+-------------+-------------+
         | Technical skill  |  30 %  |      9      |      6      |
         | Domain knowledge |  20 %  |      7      |      8      |
         | Communication    |  20 %  |      6      |      9      |
         | Team fit         |  15 %  |      5      |      9      |
         | Cost / salary fit|  15 %  |      4      |      9      |
         +------------------+--------+-------------+-------------+
         | WEIGHTED TOTAL           |     6.7     |     7.8     |
         +--------------------------+-------------+-------------+
   ```
   - The judgement worth stating: `over-qualification is a genuine risk, not a bonus`. A candidate whose ability far exceeds the role will disengage or leave, and the cost of replacing them exceeds whatever was saved. The right answer is almost never "the most qualified candidate" but `the best fit between what the role needs and what the candidate offers` — and the criteria for that must be agreed and weighted before the interviews, not after.

## Software Design Principles (Coupling & Cohesion) (5)

1. **Write concepts of Coupling and Cohesion with Example?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*

   Answer: Coupling
   - `Coupling` measures `how much one module depends on another`. Low coupling is good — a change in one module should not force a change in another.
   ```
      TYPES OF COUPLING , from BEST to WORST

      DATA COUPLING          modules pass only simple DATA items
           calculateTax(income, rate)          <- BEST

      STAMP COUPLING         a whole RECORD is passed but only part
                             of it is used
           printName(employee)   when only employee.name is needed

      CONTROL COUPLING       a FLAG is passed that tells the callee
                             WHAT TO DO
           process(data, flag)   if flag==1 print else save

      EXTERNAL COUPLING      modules share an external device,
                             protocol or file format

      COMMON COUPLING        modules share GLOBAL DATA
           int total;   used and modified by many modules

      CONTENT COUPLING       one module directly changes ANOTHER'S
                             internal data or jumps inside its code
                                                        <- WORST
   ```
   ```
      EXAMPLE

      HIGH COUPLING (bad)
           class Order {
               void save() {
                   MySQLConnection c = new MySQLConnection(...);
                   c.execute("INSERT INTO orders ...");
               }
           }
           Order knows the DATABASE TYPE and the SQL. Changing to
           PostgreSQL means changing Order.

      LOW COUPLING (good)
           class Order {
               private Repository repo;              // an INTERFACE
               void save() { repo.save(this); }
           }
           Order knows only the INTERFACE. The database can be
           swapped with no change to Order.
   ```

   Cohesion
   - `Cohesion` measures `how closely the elements inside one module belong together`. High cohesion is good — a module should do `one` well-defined job.
   ```
      TYPES OF COHESION , from BEST to WORST

      FUNCTIONAL       every element contributes to ONE task
           calculateInterest()                  <- BEST

      SEQUENTIAL       the output of one element is the input to the
                       next
           readFile() -> parse() -> validate()

      COMMUNICATIONAL  elements work on the SAME DATA
           readRecord() and updateRecord() on the same record

      PROCEDURAL       elements follow a certain ORDER of execution
                       but are otherwise unrelated

      TEMPORAL         elements are grouped only because they happen
                       at the SAME TIME
           init() : open file , clear screen , set timer , read
                    config

      LOGICAL          elements do SIMILAR KINDS of thing, selected
                       by a flag
           handleInput(type)   keyboard , mouse , file

      COINCIDENTAL     no relationship at all - a "Utility" class
           Utils : calculateTax() , sendEmail() , printReport()
                                                        <- WORST
   ```
   ```
      EXAMPLE

      LOW COHESION (bad)
           class Employee {
               void calculateSalary() { ... }
               void sendEmail()       { ... }
               void printReport()     { ... }
               void connectToDatabase() { ... }
           }
           Four unrelated jobs in one class.

      HIGH COHESION (good)
           class SalaryCalculator { void calculate() {...} }
           class EmailService     { void send() {...} }
           class ReportPrinter    { void print() {...} }
           Each class does ONE thing.
   ```

   The rule
   ```
      AIM FOR :   HIGH COHESION  ,  LOW COUPLING

      Cohesion is about what is INSIDE one module.
      Coupling is about what is BETWEEN modules.
   ```
   - Why the pair matters more than either alone: `high cohesion causes low coupling`. When each module does one job, it needs little from the others, so the dependencies naturally shrink. The two properties are the single best predictor of how expensive a system will be to maintain — and maintenance is `60 to 80 per cent` of a product's lifetime cost.

2. **Software design table matching.......** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*

   Answer: The question is `incomplete` — the matching table was not captured, so the exact pairing cannot be given. The material such a question is set on is below, in the form a matching question uses.

   Design principles and their meanings
   ```
      MODULARITY          divide the system into independent
                          modules, each with one job
      ABSTRACTION         hide the detail behind an interface -
                          show WHAT, not HOW
      INFORMATION HIDING  a module's internal data is private
      COHESION            how closely elements INSIDE one module
                          belong together - HIGH is good
      COUPLING            how much one module DEPENDS on another -
                          LOW is good
      REFINEMENT          top-down decomposition, adding detail at
                          each level
      REFACTORING         improve the internal structure WITHOUT
                          changing behaviour
   ```

   Coupling types, best to worst
   ```
      DATA COUPLING     only simple data items are passed    BEST
      STAMP COUPLING    a whole record is passed, part used
      CONTROL COUPLING  a flag is passed that decides behaviour
      EXTERNAL COUPLING a shared device, protocol or format
      COMMON COUPLING   shared GLOBAL data
      CONTENT COUPLING  one module changes another's internals WORST
   ```

   Cohesion types, best to worst
   ```
      FUNCTIONAL       one single task                       BEST
      SEQUENTIAL       output of one element feeds the next
      COMMUNICATIONAL  elements work on the same data
      PROCEDURAL       elements follow an order of execution
      TEMPORAL         elements happen at the same time
      LOGICAL          similar kinds of thing, chosen by a flag
      COINCIDENTAL     no relationship at all                WORST
   ```

   Architectural and design patterns
   ```
      MVC          separates data , presentation and input handling
      LAYERED      presentation -> business -> data access
      SINGLETON    exactly one instance of a class
      FACTORY      creates objects without naming the concrete class
      OBSERVER     one-to-many notification when state changes
      STRATEGY     interchangeable algorithms, chosen at run time
      FACADE       one simple interface to a complex subsystem
      ADAPTER      converts one interface into another
      DECORATOR    adds behaviour to an object at run time
      TEMPLATE
           METHOD  fixes the SEQUENCE, lets subclasses vary the STEPS
      COMPOSITE    treats a single object and a group identically
   ```

   Design documents and diagrams
   ```
      SRS               what the system must do
      SDD               how it will be built
      DFD               how DATA FLOWS between processes and stores
      ER DIAGRAM        entities and their relationships
      STRUCTURE CHART   the module hierarchy
      CLASS DIAGRAM     classes, attributes and relationships
      SEQUENCE DIAGRAM  the ORDER of interactions over time
      USE CASE DIAGRAM  what the system does and who uses it
      DATA DICTIONARY   the definition of every data item
   ```

   The SOLID principles
   ```
      S  SINGLE RESPONSIBILITY  a class should have one reason to
                                change
      O  OPEN-CLOSED            open for EXTENSION, closed for
                                MODIFICATION
      L  LISKOV SUBSTITUTION    a subclass must be usable wherever
                                its parent is
      I  INTERFACE SEGREGATION  many small interfaces beat one large
                                one
      D  DEPENDENCY INVERSION   depend on ABSTRACTIONS, not on
                                concrete classes
   ```
   - The method for any matching question of this kind: read each item on the left, identify its `defining property`, and find the description naming that property. The traps are always the `similar-looking pairs` — coupling against cohesion, aggregation against composition, SRS against SDD, verification against validation — so those are worth learning as pairs rather than separately.

3. **(ক) Modularization কী? উহার সুবিধা সম্পর্কে লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What modularisation is
   - `Modularisation` is dividing a software system into `separate, independent modules`, each with a single well-defined job and a clear interface. Each module can be developed, tested and changed on its own.
   ```
                     +---------------------+
                     |   Banking System    |
                     +---------------------+
                        /       |        \
               +--------+  +---------+  +----------+
               |Account |  |Transact-|  | Report   |
               |Module  |  |ion Mod. |  | Module   |
               +--------+  +---------+  +----------+

      Each module HIDES its internal working and exposes only an
      INTERFACE. Another module needs to know WHAT it does, not HOW.
   ```
   ```
      THE TWO MEASURES OF GOOD MODULARISATION

      COHESION - HIGH is good
           How closely the elements INSIDE one module belong
           together. A module that only validates a PIN has high
           cohesion ; a "Utility" module that validates PINs, prints
           reports and sends email has LOW cohesion.

      COUPLING - LOW is good
           How much one module DEPENDS on another. Modules that talk
           only through a small, well-defined interface are loosely
           coupled ; modules sharing global variables are tightly
           coupled.

      THE RULE :  HIGH COHESION , LOW COUPLING.
   ```

   Advantages

   1. Maintainability
   - A change stays inside one module instead of rippling through the system. Since `maintenance is 60 to 80 per cent` of a product's lifetime cost, this is the largest single benefit.

   2. Testability
   - Each module can be `unit tested alone`, with `stubs` and `drivers` standing in for its neighbours. A defect is located in one module rather than hunted through the whole program.

   3. Parallel development
   - Different people build different modules `at the same time`, once the interfaces are agreed. This is what makes a large project possible at all.

   4. Reusability
   - A well-defined module — a date library, an authentication service — can be used in another system without modification.

   5. Comprehensibility
   - A person can understand `one module` without holding the whole system in mind. Human working memory is the real constraint on program size.

   6. Easier debugging
   - A failure is traced to the module whose interface produced the wrong value, rather than to any line in the program.

   7. Reduced complexity
   - A large problem becomes several small ones. This is `divide and conquer` applied to design.

   8. Flexibility and easier enhancement
   - A module can be `replaced` by a better implementation as long as the interface is unchanged — a MySQL data module swapped for a PostgreSQL one, with nothing else altered.

   9. Team specialisation
   - A database expert takes the data module, a UI specialist takes the presentation module.

   Disadvantages, briefly
   ```
      more files and more interfaces to design and document
      a small performance cost in the calls between modules
      OVER-MODULARISATION - too many tiny modules make the system
           harder to follow, not easier
      getting the DECOMPOSITION wrong is expensive to correct later
   ```
   - The judgement worth stating: modularisation is not free, and the benefit comes from decomposing `along the right boundaries`. A system split into ten modules that constantly call each other is worse than one split into four that rarely do — which is why `low coupling`, not the module count, is the measure of success.

4. **(খ) Software interface কত প্রকার ও কী কী? Interfacing এর ক্ষেত্রে কী কী error পাওয়া যেতে পারে?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Types of software interface

   1. User interface (UI)
   ```
      Between the SYSTEM and the HUMAN user.
        GUI              windows, buttons, forms
        CLI              command line
        WEB interface    browser-based
        TOUCH , VOICE , form-based , menu-driven
   ```

   2. Hardware interface
   ```
      Between the SOFTWARE and the PHYSICAL DEVICES - printer,
      scanner, card reader, sensor, disk. It defines the ports,
      signals and device driver protocol.
   ```

   3. Software interface
   ```
      Between one PROGRAM and another - operating system calls,
      database drivers, libraries, other applications.
        API     Application Programming Interface
        ODBC / JDBC for databases
        Web services : REST , SOAP
   ```

   4. Communication interface
   ```
      Between systems across a NETWORK - the protocols, message
      formats and rates used. HTTP , TCP/IP , FTP , SMTP , ISO 8583
      for banking messages.
   ```

   5. Module (internal) interface
   ```
      Between the MODULES of the same program - the function
      signatures, parameters and return values through which one
      module calls another.

      THREE FORMS
        PARAMETER interface   data passed in a function call - the
             usual and best form
        SHARED MEMORY interface  a block of memory both modules read
             and write
        PROCEDURAL interface  one module offers a set of procedures
             for others to call
        MESSAGE PASSING interface  used between subsystems and in
             distributed systems
   ```

   Interfacing errors

   1. Interface misuse
   ```
      The caller uses the interface WRONGLY - wrong parameter
      ORDER, wrong TYPE, or wrong NUMBER of parameters.

           declared :  transfer(fromAccount, toAccount, amount)
           called   :  transfer(toAccount, fromAccount, amount)

      The code COMPILES and the money goes the wrong way.
   ```

   2. Interface misunderstanding
   ```
      The caller misunderstands what the called module DOES or
      ASSUMES.

           binarySearch(array, key)  requires a SORTED array.
           A caller who passes an unsorted array gets a wrong
           answer with NO error message.
   ```

   3. Timing errors
   ```
      In real-time and concurrent systems, the two sides operate at
      different SPEEDS, so one reads data before it is written or
      after it has been overwritten - a RACE CONDITION on the
      interface.
   ```

   4. Unit and format mismatch
   ```
      One module sends METRES, the other expects FEET. One sends
      dd/mm/yyyy, the other reads mm/dd/yyyy. One sends taka, the
      other expects paisa.

      This class of error is the classic cause of expensive failure,
      and no amount of UNIT testing finds it - only INTEGRATION
      testing does.
   ```

   5. Other common interface errors
   ```
      WRONG RETURN VALUE HANDLING   the caller ignores an error code
      NULL / uninitialised parameter passed
      BUFFER SIZE mismatch - the caller's buffer is smaller than the
           data returned
      PRECISION LOSS - a double truncated to an int
      VERSION MISMATCH - the interface changed but one side was not
           rebuilt
      PROTOCOL VIOLATION - calls made in the wrong ORDER, such as
           read() before open()
   ```

   How these errors are prevented and detected
   ```
      PREVENT
        define the interface PRECISELY - types, units, valid ranges,
             pre-conditions and post-conditions, IN WRITING
        use STRONG TYPING and named types rather than plain int
        validate parameters at the boundary of every module
        keep the interface SMALL - fewer parameters, fewer mistakes
        use VERSIONED APIs so a change does not silently break a
             caller

      DETECT
        INTEGRATION TESTING - the level that exists precisely to find
             interface errors
        CODE REVIEW of the interface specification
        STATIC ANALYSIS for type and parameter mismatches
        CONTRACT TESTING between services
   ```
   - The point that matters: unit testing `cannot` find interface errors by definition — every module can pass its own tests while the assumptions they make about each other are wrong. Interface faults are the commonest defect in large systems, which is why `integration testing` is a separate level and not an optional extra.

5. **What is the common mistake of UI design?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

   Answer: Common mistakes in UI design

   1. Cluttered screen — too much on one page
   ```
      Every feature crammed onto one screen, so the user cannot find
      the one thing they came for.
      FIX : group related items, use white space, hide advanced
           options behind "More", and follow PROGRESSIVE DISCLOSURE -
           show what is needed now.
   ```

   2. Inconsistency
   ```
      The Save button is bottom-right on one screen and top-left on
      the next ; "Delete" on one page and "Remove" on another ; a
      different font on every form.
      FIX : a STYLE GUIDE and a component library, so the same
           action always looks and sits the same way.
   ```

   3. Poor or missing error messages
   ```
      BAD  : "Error 0x8007007E"
             "Invalid input"
      GOOD : "Password must be at least 8 characters and contain a
             number."

      An error message must say WHAT went wrong, WHERE, and HOW to
      fix it - in the user's language, not the system's.
   ```

   4. Ignoring the user's context and vocabulary
   ```
      Technical jargon on a screen used by clerks ; English-only
      labels for users who work in Bangla ; assuming a fast
      connection and a large monitor.
      FIX : design for the ACTUAL user, and test with them.
   ```

   5. No feedback for an action
   ```
      The user clicks Submit and nothing happens, so they click
      again - and the payment is made twice.
      FIX : disable the button, show a spinner, and confirm the
           result. Every action needs visible feedback within
           about a second.
   ```

   6. No undo, and no confirmation for destructive actions
   ```
      A record is deleted with one click and cannot be recovered.
      FIX : confirm destructive actions, and prefer UNDO to a
           confirmation dialogue - people click "Yes" without
           reading.
   ```

   7. Poor navigation
   ```
      The user cannot tell where they are or how to get back. Deep
      menus with no breadcrumb ; a Back button that loses the form
      data.
      FIX : clear labels, breadcrumbs, a visible current location,
           and a maximum of three levels.
   ```

   8. Not designing for mobile
   ```
      Fixed-width layouts, buttons too small for a thumb, tables
      that need horizontal scrolling. Most users in Bangladesh are
      on a phone.
      FIX : RESPONSIVE design, touch targets of at least 44 pixels.
   ```

   9. Ignoring accessibility
   ```
      Low colour contrast, colour used as the ONLY signal (invisible
      to a colour-blind user), images with no alternative text, no
      keyboard navigation.
      FIX : follow WCAG - contrast ratio at least 4.5 : 1 , label
           every field, and never rely on colour alone.
   ```

   10. Too many required fields, and bad form design
   ```
      A registration form asking for twenty fields when five would
      do. Validation shown only AFTER submission, with the entered
      data lost.
      FIX : ask for the minimum, validate INLINE as the user types,
           and never clear the form on an error.
   ```

   11. Designing for the designer rather than the user
   ```
      Beautiful animations that slow the work down ; a novel layout
      that ignores what users already know. USERS SPEND MOST OF
      THEIR TIME ON OTHER SITES, so they expect the conventions of
      those sites.
      FIX : follow established conventions, and USABILITY TEST with
           real users. The designer is never a representative user.
   ```

   12. No visual hierarchy
   ```
      Everything the same size and weight, so nothing stands out and
      the primary action is invisible.
      FIX : one clear PRIMARY action per screen, made visually
           dominant.
   ```

   The principles these mistakes violate
   ```
      Nielsen's heuristics, in short :
        visibility of system status        - give feedback
        match the real world               - the user's language
        user control and freedom           - undo, and an exit
        consistency and standards
        error PREVENTION                   - better than a message
        recognition rather than recall     - show the options
        flexibility - shortcuts for experts
        aesthetic and MINIMALIST design
        help users recover from errors
        help and documentation
   ```
   - The single most valuable corrective is `usability testing` with five real users. It finds most of the serious problems, costs very little, and is skipped on almost every project — which is why these same mistakes recur.

## Software Cost Estimation & Build vs Buy Decisions (4)

1. **If you are CEO of a software company. You need to develop an ERP software from following three options (i) Buy (ii) Build (iii) Open Source Modification**
   * **a) Buy: Buy a software with cost 50 lac.**
   * **b) Building: Developed by developer cost 40 lac for easy process. 50 lac for hard process. Possibility is 30% to develop in easy process.**
   * **c) Open Source and Modification: Buy and small modifications cost 30 lac, for large modifications cost 50 lac. Possibility is 80% for large.**
   **What way you choose and why? Explain with calculation.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 292 (ET: BUET)]*

   Answer: This is a `decision tree` problem. The option with the `lowest expected cost` is chosen, and the expected cost of a branch is the sum of each outcome multiplied by its probability.

   The decision tree
   ```
                                       +---- 50 lac (certain)
                           (i) BUY ----+     EV = 50 lac
                             |
                             |                   0.30
                             |               +--------- easy    40 lac
          CHOOSE ------ (ii) BUILD ---------+
                             |               +--------- hard    50 lac
                             |                   0.70
                             |                   EV = 47 lac
                             |
                             |                   0.20
                             |               +--------- small mod 30 lac
                   (iii) OPEN SOURCE --------+
                                             +--------- large mod 50 lac
                                                 0.80
                                                 EV = 46 lac
   ```

   Option (i) — Buy
   ```
      Cost = 50 lac , with certainty (probability 1.0)

      Expected cost = 50 lac
   ```

   Option (ii) — Build
   ```
      Easy process : 40 lac , probability = 30 % = 0.30
      Hard process : 50 lac , probability = 100 - 30 = 70 % = 0.70

      Expected cost = (0.30 * 40) + (0.70 * 50)

                    = 12 + 35

                    = 47 lac
   ```

   Option (iii) — Open source and modification
   ```
      Large modification : 50 lac , probability = 80 % = 0.80
      Small modification : 30 lac , probability = 100 - 80 = 20 % = 0.20

      Expected cost = (0.80 * 50) + (0.20 * 30)

                    = 40 + 6

                    = 46 lac
   ```

   Comparison
   ```
      +--------------------------------+------------------+
      | Option                         | Expected cost    |
      +--------------------------------+------------------+
      | (i)   Buy                      |     50 lac       |
      | (ii)  Build                    |     47 lac       |
      | (iii) Open source + modify     |     46 lac  <--  |
      +--------------------------------+------------------+
   ```

   Decision
   ```
      CHOOSE OPTION (iii) - OPEN SOURCE AND MODIFICATION

      It has the LOWEST EXPECTED COST : 46 lac , which is 1 lac less
      than building and 4 lac less than buying.
   ```

   Points to state alongside the calculation
   ```
      1. The margin is NARROW. 46 against 47 lac is a 2 per cent
         difference - well inside the error of any software
         estimate. So the numbers alone should not decide it.

      2. RISK differs between the options.
           BUY is CERTAIN at 50 lac - no variance at all.
           BUILD ranges 40 to 50 lac.
           OPEN SOURCE ranges 30 to 50 lac - the widest spread.
         A risk-averse CEO facing a fixed budget might prefer the
         certainty of BUY despite its higher expected cost.

      3. NON-COST FACTORS not in the tree :
           LICENCE terms of the open source ERP - GPL obligations
                may be unacceptable for a commercial product
           SUPPORT and maintenance cost after year one
           TIME TO MARKET - buying is fastest
           FIT to requirements - a bought ERP may not match the
                business, and BUILDING gives the exact fit
           IN-HOUSE SKILL to modify a large open source codebase
           VENDOR LOCK-IN if bought
   ```
   - The answer to give: `option (iii), open source with modification, on expected cost` — while noting that the 1 lac margin over building is not decisive, and that licence terms, support and in-house capability should be checked before committing.

2. **Given the following values, compute function point when all complexity adjustment factor (CAF) and weighting factors are average.**
   * **User Input = 50**
   * **User Output = 40**
   * **User Inquiries = 35**
   * **User Files = 6**
   * **External Interface = 4** *[Combined Bank Assistant Programmer 09.06.2023 compact it 492 (ET: N/A)]*

   Answer: Given
   ```
      User Input          = 50
      User Output         = 40
      User Inquiries      = 35
      User Files          = 6
      External Interface  = 4

      All weighting factors are AVERAGE.
      All complexity adjustment factors are AVERAGE.
   ```

   Step 1 — the average weighting factors
   ```
      +----------------------------+--------+---------+--------+
      | Function type              | Simple | AVERAGE | Complex|
      +----------------------------+--------+---------+--------+
      | External Input   (EI)      |   3    |    4    |   6    |
      | External Output  (EO)      |   4    |    5    |   7    |
      | External Inquiry (EQ)      |   3    |    4    |   6    |
      | Internal Logical File(ILF) |   7    |   10    |  15    |
      | External Interface   (EIF) |   5    |    7    |  10    |
      +----------------------------+--------+---------+--------+
   ```

   Step 2 — Unadjusted Function Points (UFP)
   ```
      UFP = SUM ( count * weight )

      +-------------------+-------+---------+------------------+
      | Function type     | Count | Weight  | Count * Weight   |
      +-------------------+-------+---------+------------------+
      | User Input        |  50   |    4    |  50 * 4  = 200   |
      | User Output       |  40   |    5    |  40 * 5  = 200   |
      | User Inquiries    |  35   |    4    |  35 * 4  = 140   |
      | User Files        |   6   |   10    |   6 * 10 =  60   |
      | External Interface|   4   |    7    |   4 * 7  =  28   |
      +-------------------+-------+---------+------------------+
      |                       UFP (total)   =         628      |
      +-------------------------------------+------------------+
   ```

   Step 3 — Complexity Adjustment Factor (CAF)
   ```
      There are 14 general system characteristics (Fi), each rated
      from 0 to 5 :

           0 = no influence     3 = AVERAGE
           1 = incidental       4 = significant
           2 = moderate         5 = essential

      All are AVERAGE, so every Fi = 3.

      Sum of Fi = 14 * 3 = 42

      CAF = 0.65 + ( 0.01 * sum of Fi )

          = 0.65 + ( 0.01 * 42 )

          = 0.65 + 0.42

          = 1.07
   ```

   Step 4 — Function Points
   ```
      FP = UFP * CAF

         = 628 * 1.07

         = 671.96

         = 672     (rounded)
   ```

   Answer
   ```
      Unadjusted Function Points , UFP = 628
      Complexity Adjustment Factor, CAF = 1.07
      FUNCTION POINTS , FP = 671.96 , approximately 672
   ```

   Notes worth adding
   ```
      THE RANGE OF CAF
           All Fi = 0  ->  CAF = 0.65   (minimum)
           All Fi = 5  ->  CAF = 0.65 + 0.70 = 1.35   (maximum)
           So the adjustment can only move the estimate by about
           +/- 35 per cent.

      WHY FUNCTION POINTS AT ALL
           They measure the SIZE of the FUNCTIONALITY delivered, not
           the lines of code. So they can be estimated from the SRS,
           BEFORE any code exists - which LOC cannot - and they do
           not depend on the programming language.

      CONVERTING TO EFFORT
           LOC = FP * (lines per FP for the language)
                 e.g. about 53 for Java , 128 for C
           Effort is then estimated from LOC using COCOMO, or
           directly from FP using the organisation's own
           productivity figure in FP per person-month.
   ```

3. **Your company earn a contract to develop a system for a government agency. The project team is considering whether to build the system from scratch, or reuse existing partial-experience components, or buy an available software product and modify it to meet the requirement. As analyst you have made a decision tree as a figure.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

   Answer: The figure referred to was not captured with the question, so the standard textbook decision tree for the build-or-reuse-or-buy problem is worked below. The `method` is what the question tests, and it applies unchanged to whatever figures the actual tree carries.

   The decision tree
   ```
                                                0.30
                                           +---------- simple   380,000
                          BUILD -----------+
                            |              +---------- difficult 450,000
                            |                  0.70
                            |                  EV = 429,000
                            |
                            |                  0.40
                            |              +---------- reusable  275,000
                          REUSE -----------+
                            |              |     0.60      0.30
      SYSTEM ---------------+              +--- major ---+------ minor  310,000
                            |                  changes   |
                            |                            +------ extensive 490,000
                            |                                0.70
                            |                            EV(major) = 436,000
                            |                            EV(reuse) = 371,600
                            |
                            |                  0.70
                            |              +---------- minor changes  210,000
                          BUY -------------+
                            |              +---------- major changes  400,000
                            |                  0.30
                            |                  EV = 267,000
                            |
                            |                  0.60
                            |              +---------- without changes 350,000
                          CONTRACT --------+
                                           +---------- with changes    500,000
                                               0.40
                                               EV = 410,000
   ```

   The rule
   ```
      EXPECTED VALUE of a path
           = SUM over outcomes of  ( probability * cost )

      Work from the RIGHT of the tree to the LEFT. Fold each chance
      node into a single expected value, then compare the decision
      branches. Choose the LOWEST expected cost.
   ```

   Path 1 — Build
   ```
      EV = (0.30 * 380,000) + (0.70 * 450,000)

         = 114,000 + 315,000

         = 429,000
   ```

   Path 2 — Reuse
   ```
      First fold the INNER chance node - "major changes" :

      EV(major changes) = (0.30 * 310,000) + (0.70 * 490,000)
                        = 93,000 + 343,000
                        = 436,000

      Now the outer node :

      EV(reuse) = (0.40 * 275,000) + (0.60 * 436,000)
                = 110,000 + 261,600
                = 371,600
   ```

   Path 3 — Buy
   ```
      EV = (0.70 * 210,000) + (0.30 * 400,000)

         = 147,000 + 120,000

         = 267,000
   ```

   Path 4 — Contract out
   ```
      EV = (0.60 * 350,000) + (0.40 * 500,000)

         = 210,000 + 200,000

         = 410,000
   ```

   Comparison and decision
   ```
      +----------------+--------------------+
      | Option         | Expected cost      |
      +----------------+--------------------+
      | Build          |      429,000       |
      | Reuse          |      371,600       |
      | BUY            |      267,000  <--  |
      | Contract       |      410,000       |
      +----------------+--------------------+

      DECISION : BUY the available product and modify it - the
      lowest expected cost at 267,000.
   ```

   What the expected value does NOT capture, and must be stated
   ```
      1. RISK / VARIANCE
           Expected value treats a certain 267,000 and a gamble
           averaging 267,000 as identical. They are not. Compare the
           SPREAD as well :
                Buy   ranges 210,000 to 400,000
                Build ranges 380,000 to 450,000 - higher, but
                      NARROWER
           An organisation with a fixed budget may prefer the
           narrower spread.

      2. NON-FINANCIAL FACTORS
           FIT to the requirement - building gives an exact fit
           TIME TO MARKET - buying is fastest
           VENDOR LOCK-IN and long-term support cost
           LICENCE terms
           IN-HOUSE CAPABILITY built by developing it yourself
           For a GOVERNMENT AGENCY : data sovereignty, procurement
                rules, and long-term maintainability may outweigh
                the cost difference entirely.

      3. THE PROBABILITIES ARE ESTIMATES
           They come from expert judgement, not measurement. A
           SENSITIVITY ANALYSIS - recomputing with the probabilities
           moved by 10 per cent - shows whether the decision is
           robust or balanced on a knife edge.
   ```
   - The answer to give in an exam: state the expected-value calculation for each branch, name the lowest as the recommendation, and then add the qualification that `expected value ignores risk and non-financial factors`, which for a government contract may be decisive.

4. **Which factors are to be consider as software pricing?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*

   Answer: Software pricing is not the same as software costing. `Cost` is what it takes to build; `price` is what the customer is charged, and it is set by market and strategic factors as well as by cost.
   ```
      PRICE = COST + PROFIT + adjustments for market, risk and
              strategy
   ```

   Development cost factors
   ```
      EFFORT           person-months of development, testing,
           analysis and documentation - usually the largest single
           component
      SALARY and OVERHEAD   staff cost plus office, electricity,
           equipment, administration
      HARDWARE and SOFTWARE tools, licences, servers, test
           environments
      TRAINING         of the development team
      TRAVEL and communication
      SUBCONTRACTING   any work bought in
   ```

   Project factors
   ```
      SIZE and COMPLEXITY   estimated in function points or KLOC
      REQUIRED RELIABILITY  a banking system costs far more per
           function than a website, because the testing and review
           burden is higher
      SCHEDULE PRESSURE     compressing a schedule RAISES cost more
           than proportionally - adding people to a late project
           makes it later
      TECHNOLOGY            an unfamiliar platform costs more
      REUSE                 existing components lower the cost
   ```

   Risk and contingency
   ```
      REQUIREMENT VOLATILITY  unclear or changing requirements
           justify a contingency margin
      TECHNICAL RISK          unproven technology
      CONTRACT TYPE
           FIXED PRICE - the developer carries the risk, so the
                price must include a margin for it
           TIME AND MATERIALS - the customer carries the risk, so
                the rate can be lower
      PENALTY CLAUSES for late delivery must be priced in
   ```

   Market and business factors — where pricing differs from costing
   ```
      COMPETITION        what competitors charge for the same thing
      MARKET OPPORTUNITY a company may price BELOW cost to enter a
           new market, or to win a first reference customer,
           expecting to profit on later contracts
      CUSTOMER'S ABILITY and WILLINGNESS TO PAY
      CONTRACTUAL TERMS  a customer may accept a lower price in
           return for the right to reuse the software
      COST-PLUS PRICING  cost plus an agreed percentage - common in
           government contracts
      VALUE-BASED PRICING  priced by the VALUE to the customer, not
           the cost to build. A system saving a bank 10 crore a year
           can be priced far above its build cost.
   ```

   Lifetime and post-delivery factors
   ```
      MAINTENANCE and SUPPORT - 60 to 80 per cent of lifetime cost,
           and often the real source of profit
      ANNUAL MAINTENANCE CONTRACT , typically 15 to 20 per cent of
           the licence value per year
      UPGRADES and future versions
      SLA level - 24x7 support costs far more than office hours
      HOSTING and infrastructure, for a cloud product
   ```

   Licensing model
   ```
      PERPETUAL LICENCE     one payment, plus annual maintenance
      SUBSCRIPTION / SaaS   monthly or yearly per user
      PER USER , PER CORE , PER SITE , or ENTERPRISE-WIDE
      FREEMIUM              free basic version, paid features
      OPEN SOURCE + SUPPORT the software is free, the support is
           charged
   ```

   Legal, tax and local factors
   ```
      VAT and income tax , customs duty on imported software
      currency fluctuation on an export contract
      regulatory compliance cost - Bangladesh Bank, NBR
      INTELLECTUAL PROPERTY : does the customer own the code, or
           licence it ? Transferring ownership commands a higher
           price
      SOURCE-CODE ESCROW and warranty obligations
   ```

   - The point that distinguishes a good answer: `price is not a function of cost alone`. Two projects with the same development cost can be priced very differently — one priced low to win a strategic customer, the other priced high because it saves the customer far more than it costs. Cost sets the `floor`; the market and the value to the customer set the `ceiling`.
   - The practical warning: pricing below cost to win a contract, then relying on `change requests` to recover the loss, is a common and damaging practice. It is why fixed-price contracts must include a `clear scope` and a `formal change-control process` — without them the developer absorbs every change and the project fails commercially even when it succeeds technically.

## IT Governance, Audit & Risk Management (4)

1. **Difference between: Policy, Guideline, Procedure; why auditor must focus on control as a system? Explain four types of risks auditor faces, Explain each of theme.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 310 (ET: BIBM)]*

   Answer: Difference between policy, guideline and procedure

   | Point | Policy | Guideline | Procedure |
   |---|---|---|---|
   | What it is | A `high-level statement` of intent and rule | `Recommended` best practice | `Step-by-step` instructions |
   | Answers | `Why` and `what` | `How, suggested` | `How, exactly` |
   | Mandatory? | `Yes` — compulsory | `No` — advisory | `Yes` — compulsory |
   | Detail | Low | Medium | `High` |
   | Approved by | `Board` / senior management | Department or subject expert | Process owner |
   | Changes | Rarely | Often | When the process changes |
   | Length | Short — a page | Varies | Long — a checklist |
   | Audience | Everyone | Anyone needing advice | The person doing the task |

   Example — the same subject at three levels
   ```
      POLICY
           "All user passwords must be strong and must be changed
            every 90 days."
           -> the RULE. Short, mandatory, rarely changed.

      GUIDELINE
           "A strong password is best made from a passphrase of four
            unrelated words. Avoid names, dates and dictionary
            words."
           -> ADVICE. Helpful, not enforceable.

      PROCEDURE
           "To change your password :
              1. Log in to the portal
              2. Click Settings, then Security
              3. Enter the old password
              4. Enter the new password twice
              5. Click Save and log in again"
           -> the EXACT STEPS. Mandatory, and it changes whenever
              the portal changes.
   ```
   ```
      The related term is a STANDARD :
           "Passwords must be at least 12 characters and contain an
            upper case letter, a digit and a symbol."
           -> a MANDATORY, MEASURABLE specification that supports
              the policy. Between a policy and a procedure in level.

      HIERARCHY :  POLICY -> STANDARD -> PROCEDURE
                          -> GUIDELINE (advisory, alongside)
   ```

   Why the auditor must focus on control as a system
   - An auditor cannot test every transaction. A bank posts millions of them, so testing each one is impossible. Instead the auditor tests the `system of controls` that governs them, and infers the reliability of the transactions from the reliability of the system.
   ```
      THE REASONS

      1. VOLUME MAKES 100 PER CENT TESTING IMPOSSIBLE.
           Testing a SAMPLE tells you about the sample. Testing the
           CONTROL SYSTEM tells you about the whole population -
           provided the system operated consistently.

      2. CONTROLS ARE INTERDEPENDENT.
           No single control is sufficient. A strong password policy
           is worthless if the leavers' process does not disable
           accounts. Controls only work as a SET, so they must be
           evaluated as a set.
           A COMPENSATING control elsewhere may cover a weak one -
           which the auditor cannot see by examining controls in
           isolation.

      3. A WEAKNESS IN THE SYSTEM IS SYSTEMATIC.
           One wrong transaction is an error. A broken control
           produces wrong transactions CONTINUOUSLY, in every period,
           past and future. Finding the broken control is worth far
           more than finding one error.

      4. PREVENTION IS THE OBJECTIVE, NOT DETECTION.
           Detecting errors after the fact corrects the past. Fixing
           the control prevents recurrence. An audit that lists
           errors without identifying the control failure has not
           done its job.

      5. IT DETERMINES HOW MUCH SUBSTANTIVE TESTING IS NEEDED.
           Strong, tested controls -> the auditor may rely on them
                and reduce detailed testing.
           Weak controls -> far more substantive testing is required.
           This assessment IS the audit plan.

      6. AUTOMATED CONTROLS ARE ALL-OR-NOTHING.
           A manual clerk makes occasional mistakes. A program with
           a logic error makes the SAME mistake every single time.
           So in an IT environment the control system matters more,
           not less.

      7. THE THREE LAYERS MUST HOLD TOGETHER.
           PREVENTIVE  - stop it happening (access control,
                validation, SEGREGATION OF DUTIES)
           DETECTIVE   - find it if it happens (reconciliation,
                exception report, audit log)
           CORRECTIVE  - put it right (backup, recovery, incident
                response)
           A system with prevention but no detection cannot tell
           whether prevention is working.
   ```

   Four types of risk the auditor faces

   1. Inherent risk
   ```
      The risk of material misstatement BEFORE considering any
      internal control - the risk arising from the NATURE of the
      business and the transaction itself.

      The auditor CANNOT REDUCE inherent risk ; it can only be
      ASSESSED.

      HIGH inherent risk :
           cash and card transactions - liquid and easily stolen
           complex financial instruments requiring judgement
           estimates and provisions
           a new payment channel with no operating history
           a heavily regulated activity

      LOW inherent risk :
           fixed assets , simple recurring rent payments
   ```

   2. Control risk
   ```
      The risk that the entity's INTERNAL CONTROLS FAIL to prevent
      or detect a material misstatement.

      The auditor does not create the controls, so cannot reduce
      this risk either - only ASSESS it, by testing the controls.

      CAUSES :
           no SEGREGATION OF DUTIES - one person initiates and
                approves
           management OVERRIDE of controls
           a control that exists on paper but is not performed
           shared or excessive user privileges
           no reconciliation, no exception review
           COLLUSION between two people, which defeats even good
                segregation
   ```

   3. Detection risk
   ```
      The risk that THE AUDITOR fails to detect a material
      misstatement that exists.

      This is the ONLY component the auditor CONTROLS, and it is
      controlled by the amount, timing and nature of the audit
      work.

      CAUSES :
           too small a sample
           the wrong audit procedure for the risk
           insufficient time or an inexperienced audit team
           misinterpreting the evidence obtained

      REDUCED BY : a larger sample , better procedures , more
           experienced staff , and review of the audit work itself.
   ```
   ```
      THE AUDIT RISK MODEL

           AUDIT RISK = INHERENT RISK * CONTROL RISK * DETECTION RISK

      The auditor sets ACCEPTABLE AUDIT RISK (say 5 per cent),
      ASSESSES inherent and control risk, and then works out how low
      DETECTION RISK must be - which decides how much testing to do.

           High inherent + high control risk
                -> detection risk must be LOW
                -> MORE testing, larger samples

           Low inherent + low control risk
                -> detection risk may be higher
                -> LESS testing
   ```

   4. Business risk
   ```
      The risk that the AUDITOR SUFFERS LOSS from the engagement,
      even if the audit itself was properly performed :
           litigation and damages
           loss of reputation
           regulatory sanction
           loss of the client, or non-payment of fees

      It is managed by client screening, engagement letters,
      professional indemnity insurance, and documenting the work
      thoroughly.
   ```
   - The relationship worth stating: the first three multiply to give `audit risk`, and only `detection risk` is within the auditor's control. Inherent and control risk are properties of the `client`, which the auditor `assesses` and then responds to by adjusting the depth of testing. `Business risk` is separate — it is the auditor's own exposure, not the client's.

2. **A bank has association with two different service providers as their payment gateways. The bank hires Mr. X to audit the payment gateway based on risk and threat detection. Which possible scenarios Mr. X will face?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 443 (ET: BIBM)]*

   Answer: The scenario: a bank uses `two different payment gateway service providers`, and Mr. X audits them for risk and threat detection. The scenarios he will face fall into the following groups.

   1. Inconsistency between the two providers
   ```
      Two providers means TWO of everything, and the differences are
      themselves a risk :

        different SECURITY STANDARDS - one PCI-DSS certified, the
             other not
        different ENCRYPTION - one on TLS 1.3, the other still on
             TLS 1.0 or 1.1
        different AUTHENTICATION - one enforcing 3D Secure and OTP,
             the other not
        different LOG FORMATS and retention periods, so a
             transaction cannot be traced end to end across both
        different SLA and incident-response commitments
        ONE PROVIDER BECOMES THE WEAK LINK - an attacker will use
             the weaker gateway, so the bank's security is that of
             its WEAKEST provider, not its average
   ```

   2. Transaction integrity and reconciliation risk
   ```
      DOUBLE DEBIT       the customer is charged twice because a
           retry was not IDEMPOTENT
      DEBIT WITHOUT
           CREDIT        money leaves the account but the merchant
           is never credited - the network failed after the debit
           and NO REVERSAL was sent
      ORPHAN TRANSACTION recorded at the gateway but not in the core
           banking system, or the reverse
      AMOUNT or CURRENCY MISMATCH between the two systems
      SETTLEMENT MISMATCH  the gateway's settlement file does not
           agree with the bank's ledger
      RECONCILIATION      does the bank reconcile with BOTH
           providers DAILY, and who investigates a break ?
   ```
   - This group is where real money is lost, and it is the first thing to test: `pick a failure point deliberately and check what state the account, the gateway and the ledger are left in`.

   3. Security and threat scenarios
   ```
      DATA AT REST and IN TRANSIT
           Is card data ENCRYPTED ? Is the CVV STORED anywhere - it
           must NOT be. Is TOKENISATION used instead of raw card
           numbers ?
      MAN IN THE MIDDLE on the bank-to-gateway link
      API KEY and CREDENTIAL MANAGEMENT
           Are the gateway API keys hard-coded in the application ?
           Are they rotated ? Who can see them ?
      REPLAY ATTACK - can a captured transaction message be resent
           and processed again ?
      INJECTION and application-layer attacks on the payment page
      PHISHING and fake payment pages impersonating the bank
      CARD TESTING / ENUMERATION - many small transactions probing
           stolen card numbers
      DDoS on one gateway, and whether traffic fails over safely
      INSIDER THREAT - can a bank or provider employee alter or view
           transaction data ?
   ```

   4. Access control and segregation of duties
   ```
      Who at the bank can change the GATEWAY ROUTING RULES ?
      Can one person both INITIATE and APPROVE a refund ?
      Are there SHARED or GENERIC accounts on the gateway console ?
      Are LEAVERS' accounts disabled promptly ?
      Is PRIVILEGED ACCESS logged and reviewed ?
      Is MULTI-FACTOR AUTHENTICATION enforced on administrative
           access ?
   ```

   5. Third-party and vendor risk
   ```
      Is each provider PCI-DSS certified, and is the certificate
           CURRENT ?
      Has an independent security assessment or penetration test
           been done, and were the findings closed ?
      What does the CONTRACT say about liability for a breach ?
      Does the provider SUBCONTRACT any part of the processing - the
           FOURTH-PARTY risk the bank cannot see ?
      WHERE IS THE DATA HOSTED ? Offshore hosting raises data-
           sovereignty and regulatory questions.
      What is the EXIT PLAN if a provider fails or the contract
           ends ?
      CONCENTRATION RISK - what share of volume goes through each ?
   ```

   6. Availability and continuity
   ```
      If gateway A fails, does traffic FAIL OVER to gateway B
           automatically, and is the failover TESTED ?
      Is there a documented RTO and RPO ?
      Are transactions in flight at the moment of failure LOST,
           DUPLICATED, or correctly recovered ?
      Is there enough capacity at PEAK - salary day, Eid ?
   ```

   7. Compliance and regulatory
   ```
      BANGLADESH BANK guidelines on ICT security and payment
           systems
      PCI-DSS for card data
      AML and CFT - is transaction monitoring in place for
           suspicious patterns, on BOTH gateways ?
      AUDIT TRAIL retention - is it complete, immutable, and kept
           for the required period ?
      CUSTOMER DATA PRIVACY and consent
   ```

   8. Monitoring and threat detection — the specific brief
   ```
      Is there REAL-TIME FRAUD MONITORING, and does it cover both
           providers or only one ?
      Are ALERTS defined for : velocity (many transactions in
           seconds), unusual geography, high-value transactions,
           repeated declines from one card ?
      Is there a SIEM collecting logs from both gateways, and does
           anyone actually read the alerts ?
      Is there a documented INCIDENT RESPONSE plan, and has it been
           rehearsed ?
      Are logs TAMPER-PROOF - can an insider delete evidence ?
   ```

   9. Practical obstacles Mr. X will face during the audit itself
   ```
      The providers may REFUSE ACCESS to their systems, offering
           only a SOC 2 report or a certificate - so the auditor
           must rely on third-party assurance rather than direct
           testing.
      No TEST ENVIRONMENT, so failure scenarios cannot be driven
           deliberately.
      INCOMPLETE DOCUMENTATION of the integration.
      LOGS in different formats that cannot be correlated across the
           two gateways.
      Testing on the LIVE system risks real customer transactions.
      COMMERCIAL PRESSURE not to report findings against a provider
           the bank depends on.
   ```

   - The finding most likely to matter: with two providers the bank's exposure is set by the `weaker` of the two, and the `boundary between them` — routing, failover and reconciliation — is where nobody's controls apply. That gap between two well-controlled systems is exactly where an auditor should look first, and it is the scenario a single-provider audit would never reveal.

3. **(ক) Software risk কত প্রকার ও কী কী? Risk management process চিত্রের মাধ্যমে বুঝিয়ে লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Types of software risk

   Risk is classified by `what it threatens`.
   ```
      1. PROJECT RISK
           Threatens the SCHEDULE and the BUDGET.
             staff turnover , unrealistic estimates , requirement
             creep , loss of a key person , customer unavailable ,
             budget cut , late delivery by a supplier
           EFFECT : the project is late or over cost.

      2. PRODUCT RISK  (technical risk)
           Threatens the QUALITY of the software being built.
             unproven technology , performance target that cannot be
             met , integration with a legacy system , defective
             third-party component , changing specification
           EFFECT : the product is delivered but does not work well
             enough.

      3. BUSINESS RISK
           Threatens the VIABILITY of the product or the
           organisation.
             the market changes and the product is no longer wanted
             a competitor releases first
             the sponsor loses interest or leaves
             management support is withdrawn
             regulation changes and makes the product illegal
           EFFECT : the software is built correctly and is
             worthless. THE MOST DANGEROUS CATEGORY, because
             technical excellence cannot cure it.
   ```
   ```
      The same risk can fall in more than one category :

           "The lead developer resigns"
                -> PROJECT risk (delay) AND PRODUCT risk (their
                   knowledge of the design is lost)
   ```

   Other classifications used
   ```
      BY SOURCE
        KNOWN risks       identifiable from the plan and experience
        PREDICTABLE risks likely from past projects - staff
                          turnover, poor communication
        UNPREDICTABLE     cannot be foreseen - a natural disaster

      BY AREA
        requirement risk , estimation risk , technology risk ,
        people risk , organisational risk , tools risk , security
        risk , legal risk
   ```

   The risk management process
   ```mermaid
   flowchart LR
       A[1. Risk identification] --> B[2. Risk analysis]
       B --> C[3. Risk planning]
       C --> D[4. Risk monitoring]
       D --> A
   ```
   ```
      +---------------------+     +---------------------+
      | 1. RISK             |---->| 2. RISK             |
      |    IDENTIFICATION   |     |    ANALYSIS         |
      | - checklists        |     | - PROBABILITY       |
      | - brainstorming     |     | - IMPACT            |
      | - past projects     |     | - risk EXPOSURE     |
      | - expert judgement  |     |   = P * I           |
      +---------------------+     +---------------------+
                ^                            |
                |                            v
      +---------------------+     +---------------------+
      | 4. RISK MONITORING  |<----| 3. RISK PLANNING    |
      | - track each risk   |     | - AVOID             |
      | - has probability   |     | - TRANSFER          |
      |   changed ?         |     | - MITIGATE          |
      | - new risks ?       |     | - ACCEPT            |
      | - trigger the plan  |     | - CONTINGENCY plan  |
      +---------------------+     +---------------------+

      THE LOOP IS CONTINUOUS - it runs through the whole project,
      not once at the start.
   ```

   Step 1 — Risk identification
   - List everything that could go wrong, using checklists, brainstorming with the team, the record of past projects, and expert judgement. The output is the `risk register`.

   Step 2 — Risk analysis
   ```
      Each risk is given a PROBABILITY and an IMPACT :

           RISK EXPOSURE = PROBABILITY * IMPACT

      Example :
           Risk : the lead developer resigns
           Probability = 0.3     Impact = 20 lakh delay cost
           Exposure = 0.3 * 20 = 6 lakh

      Risks are then RANKED by exposure, and attention goes to the
      top few. A register of fifty risks all treated equally is a
      register nobody uses.
   ```
   ```
      THE RISK MATRIX

                 IMPACT ->
                 LOW      MEDIUM     HIGH
      HIGH   |  monitor | mitigate | AVOID or
      P      |          |          | MITIGATE NOW
      R  MED |  accept  | monitor  | mitigate
      O      |          |          |
      B  LOW |  accept  | accept   | TRANSFER
             |          |          | (insure)
   ```

   Step 3 — Risk planning
   ```
      FOUR RESPONSES

      AVOID      change the plan so the risk cannot occur.
           "Use a proven database instead of the new one."
      TRANSFER   move the risk to someone else - insurance, a fixed-
           price subcontract, a penalty clause.
      MITIGATE   reduce the probability or the impact.
           "Cross-train a second developer on the payment module."
      ACCEPT     do nothing, but prepare a CONTINGENCY PLAN and
           reserve budget for it.

      Each risk also needs a TRIGGER - the observable sign that it
      is materialising - and an OWNER responsible for watching it.
   ```

   Step 4 — Risk monitoring
   - Review the register regularly. Has any probability or impact changed? Have new risks appeared? Has a trigger fired? Retire risks that have passed. In Agile this review happens at every `sprint retrospective`.

   - The judgement worth stating: risk management is not about eliminating risk, which is impossible, but about `knowing which risks matter and having a prepared response`. A project that identifies its top five risks and plans for them will outperform one that identifies fifty and plans for none.

4. **Draw risk analysis digram.** *[NESCO Manager (Software) 2018 compact it 1210 (ET: N/A)]*

   Answer: Risk analysis diagram

   The risk management cycle
   ```mermaid
   flowchart LR
       A[1. Risk identification] --> B[2. Risk analysis:<br/>probability x impact]
       B --> C[3. Risk prioritisation]
       C --> D[4. Risk planning:<br/>avoid, transfer, mitigate, accept]
       D --> E[5. Risk monitoring]
       E --> A
   ```
   ```
      +---------------------+       +---------------------+
      | 1. RISK             |------>| 2. RISK ANALYSIS    |
      |    IDENTIFICATION   |       |  - PROBABILITY (P)  |
      |  - checklists       |       |  - IMPACT (I)       |
      |  - brainstorming    |       |  - EXPOSURE = P * I |
      |  - past projects    |       +---------------------+
      +---------------------+                  |
                ^                              v
                |                    +---------------------+
                |                    | 3. PRIORITISATION   |
                |                    |  rank by exposure   |
                |                    +---------------------+
                |                              |
      +---------------------+                  v
      | 5. RISK MONITORING  |       +---------------------+
      |  - track exposure   |<------| 4. RISK PLANNING    |
      |  - watch TRIGGERS   |       |  AVOID / TRANSFER / |
      |  - find new risks   |       |  MITIGATE / ACCEPT  |
      +---------------------+       |  + contingency plan |
                                    +---------------------+
   ```

   The risk matrix
   ```
                             I M P A C T
                    LOW         MEDIUM        HIGH
               +------------+------------+---------------+
         HIGH  |  MONITOR   |  MITIGATE  |   AVOID or    |
               |            |            |   MITIGATE    |
      P        |            |            |   IMMEDIATELY |
      R        +------------+------------+---------------+
      O   MED  |  ACCEPT    |  MONITOR   |   MITIGATE    |
      B        |            |            |               |
      A        +------------+------------+---------------+
      B   LOW  |  ACCEPT    |  ACCEPT    |   TRANSFER    |
      I        |            |            |   (insure)    |
      L        +------------+------------+---------------+
      I
      T
      Y
   ```

   The risk register — how analysis is recorded
   ```
      +----+------------------+------+--------+----------+-----------+
      | ID | Risk             | Prob | Impact | Exposure | Response  |
      +----+------------------+------+--------+----------+-----------+
      | R1 | Lead developer   | 0.30 | 20 L   |   6.0 L  | MITIGATE  |
      |    | resigns          |      |        |          | cross-    |
      |    |                  |      |        |          | train     |
      | R2 | Requirements     | 0.60 |  8 L   |   4.8 L  | MITIGATE  |
      |    | change late      |      |        |          | change    |
      |    |                  |      |        |          | control   |
      | R3 | Legacy system    | 0.40 | 10 L   |   4.0 L  | MITIGATE  |
      |    | integration      |      |        |          | build an  |
      |    | fails            |      |        |          | adapter   |
      | R4 | Vendor delivers  | 0.20 | 15 L   |   3.0 L  | TRANSFER  |
      |    | late             |      |        |          | penalty   |
      |    |                  |      |        |          | clause    |
      | R5 | Server hardware  | 0.10 | 12 L   |   1.2 L  | ACCEPT    |
      |    | failure          |      |        |          | + backup  |
      +----+------------------+------+--------+----------+-----------+

      RISK EXPOSURE = PROBABILITY * IMPACT
      The register is sorted by EXPOSURE, and effort goes to the top.
   ```

   The risk-exposure calculation
   ```
      Example : R1 , the lead developer resigns

           Probability = 0.30
           Impact      = 20 lakh  (delay and re-work cost)

           Exposure = 0.30 * 20 = 6.0 lakh

      This is the amount it is worth spending to remove the risk.
      Spending 2 lakh to cross-train a second developer is clearly
      worthwhile ; spending 10 lakh would not be.
   ```

   The four responses
   ```
      AVOID      change the plan so the risk cannot arise
      TRANSFER   pass it to someone else - insurance, a fixed-price
                 subcontract, a penalty clause
      MITIGATE   reduce the probability or the impact
      ACCEPT     take it knowingly, with a CONTINGENCY PLAN and
                 reserved budget
   ```
   - Two things every entry needs besides the numbers: a `trigger` — the observable sign that the risk is materialising — and an `owner` responsible for watching it. A register with exposures but no triggers and no owners records risk without managing it.
   - The purpose of the whole diagram is the `loop`. Risk analysis is not done once at the start; probabilities change, risks retire and new ones appear, so the cycle runs for the life of the project — at every `sprint retrospective` in an Agile project, and at every phase review in a Waterfall one.

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
