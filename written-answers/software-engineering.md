<!-- TOC START -->
**Table of Contents** — 13 subtopics · 124 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [SDLC Phases & Models](#sdlc-phases--models-37) | 37 |
| 2 | [Software Testing & Evaluation](#software-testing--evaluation-33) | 33 |
| 3 | [Software Architecture & Design Patterns (MVC)](#software-architecture--design-patterns-mvc-11) | 11 |
| 4 | [UML Diagrams (Class, Use Case, Sequence)](#uml-diagrams-class-use-case-sequence-9) | 9 |
| 5 | [Software Requirements Engineering](#software-requirements-engineering-8) | 8 |
| 6 | [Software Project Management & Organization](#software-project-management--organization-7) | 7 |
| 7 | [Software Design Principles (Coupling & Cohesion)](#software-design-principles-coupling--cohesion-5) | 5 |
| 8 | [Software Cost Estimation & Build vs Buy Decisions](#software-cost-estimation--build-vs-buy-decisions-4) | 4 |
| 9 | [IT Governance, Audit & Risk Management](#it-governance-audit--risk-management-3) | 3 |
| 10 | [Data Flow Diagrams (DFD)](#data-flow-diagrams-dfd-2) | 2 |
| 11 | [Code Smells & Refactoring](#code-smells--refactoring-2) | 2 |
| 12 | [Open Source Software & Licensing](#open-source-software--licensing-2) | 2 |
| 13 | [CI/CD & DevOps Methodologies](#cicd--devops-methodologies-1) | 1 |

<!-- TOC END -->

---

## SDLC Phases & Models (37)

1. A software company has been hired to develop an Online Library Management System for a university. The librarian wants the system to be delivered in phases so that feedback from users can be incorporated after each release. As a software developer, identify the most suitable Software Development Life Cycle (SDLC) model for this project. Justify your choice by mentioning two advantages of the selected model. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*


   Answer: The most suitable SDLC model for this project is the Incremental model, and more specifically an Agile method such as Scrum, which is the incremental approach in its modern form.

   Why it fits this project exactly:
   - The librarian has explicitly asked for delivery in phases, which is the defining characteristic of the incremental model.
   - Feedback is to be incorporated after each release, which requires the customer to see working software repeatedly, and that is exactly what an increment provides.
   - A library management system has a naturally divisible feature set: cataloguing, member registration, issue and return, fine calculation, reservations, and reporting. Each can form one increment.

   How it would be organised:
   - Increment 1: book catalogue and search, plus member registration. Delivered and used.
   - Increment 2: issue and return of books, with due dates.
   - Increment 3: fine calculation and payment.
   - Increment 4: reservations, notifications and reports.
   Each increment goes through its own requirements, design, coding and testing, and each ends with a working system that the library can actually use.

   Two advantages of the incremental model for this case:

   - Early and continuous delivery of usable software: the library obtains a working catalogue and search facility after the first increment, perhaps within six weeks, instead of waiting a year for everything. The system begins to deliver value long before the project ends, and the university sees a return on its money early.

   - Feedback is incorporated cheaply, and requirement errors are caught early: after each release the librarian and the students use the system and say what is wrong or missing. Because the remaining increments have not yet been built, that feedback costs little to act upon. In a Waterfall project the same discovery would come at acceptance testing, when correcting it would be ten to a hundred times more expensive.

   Two further advantages worth mentioning:
   - Risk is reduced, because technical and usability problems appear in the first increment rather than at the end.
   - The team can absorb changing requirements, which is certain in a university, where rules on borrowing limits and fines change from year to year.

   Why the alternatives are less suitable:
   - Waterfall would deliver nothing until the end and cannot accommodate feedback between phases, which directly contradicts the librarian's stated requirement.
   - The Spiral model is designed for large, high-risk projects and its formal risk analysis in every cycle is heavier than a library system justifies.
   - The Big Bang model has no discipline at all and is unsuitable for anything with a paying customer.

   Practical recommendation: run the project as Scrum with three-week sprints, a product backlog of library features prioritised by the librarian acting as Product Owner, a sprint review at the end of each sprint at which the library staff try the software, and a retrospective to improve the process.
2. What are the main phases of the Software Development Life Cycle (SDLC)? Explain each phase briefly. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

   The phases:

   1. Planning and feasibility study:
   - Define the problem, the scope and the objectives.
   - Estimate cost, time and resources.
   - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
   - Output: the project plan and the feasibility report.

   2. Requirement analysis and specification:
   - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
   - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
   - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
   - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

   3. Design:
   - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
   - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
   - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
   - Output: the design document, sometimes divided into HLD and LLD.

   4. Implementation (coding):
   - The design is translated into source code in the chosen language, following coding standards.
   - Version control, code review and unit testing by the developer belong to this phase.
   - Output: the working source code and the developer documentation.

   5. Testing:
   - Verify that the software meets the specification and find defects before release.
   - Levels: unit testing, integration testing, system testing and acceptance testing.
   - Types: functional, performance, security, usability and regression testing.
   - Output: test plans, test cases, defect reports and the test summary.

   6. Deployment:
   - Install the system in the live environment, migrate the data, train the users and go live.
   - Strategies: direct changeover, parallel running, pilot and phased introduction.
   - Output: the running system and the user manual.

   7. Maintenance:
   - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
   - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
   - Output: updated versions and revised documentation.

   Diagram:

   ```mermaid
   flowchart LR
     A[Planning and Feasibility] --> B[Requirement Analysis]
     B --> C[Design]
     C --> D[Implementation]
     D --> E[Testing]
     E --> F[Deployment]
     F --> G[Maintenance]
     G -.feedback.-> B
   ```

   The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
3. Critically analyze the limitations of the Waterfall model and explain how Agile methodologies address those limitations. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer:

   Limitations of the Waterfall model:

   - No working software until late: the customer sees nothing until the very end. A project of a year produces its first demonstrable output after eleven months, by which time it may be too late to correct a fundamental misunderstanding.

   - Requirements are assumed to be complete and stable at the start, which is almost never true. Users often cannot articulate what they want until they see something working, and business needs change during a long project.

   - Change is expensive and is therefore resisted. Once the requirements phase is signed off, a change requires going back up the waterfall, revising the specification, the design, the code and the tests. Formal change control processes exist precisely because change is treated as an exception rather than as normal.

   - Defects are found late. A misunderstanding introduced in the requirement phase surfaces only during system testing, at which point it costs ten to a hundred times more to correct than it would have done at the point of origin. This is Boehm's cost-of-change curve.

   - Risk is concentrated at the end. If integration fails or the system proves unusable at acceptance, the entire investment is lost, and there is no partial result to fall back on.

   - Testing is compressed into a single phase, which is also the phase most often cut when the project runs late, so quality suffers exactly when the schedule is under pressure.

   - No customer involvement between the requirements phase and delivery, so there is no opportunity to detect a divergence between what was specified and what is actually needed.

   - Progress is measured by documents produced rather than by software that works, which can conceal how far the project really is from completion. A project reported as 90 per cent complete for months is a familiar symptom.

   - It is unsuitable for long, large or exploratory projects, and for anything where the technology is unfamiliar.

   How Agile addresses each limitation:

   | Waterfall limitation | Agile remedy |
   |---|---|
   | No software until the end | Working software is delivered every one to four weeks, so value arrives early and continuously |
   | Requirements assumed fixed | Changing requirements are welcomed, even late; the backlog is reprioritised every iteration |
   | Change is expensive | Change is cheap, because only the current short iteration is affected, not a signed-off specification |
   | Defects found late | Continuous testing, test-driven development and continuous integration find defects within days |
   | Risk concentrated at the end | Risk is spread across iterations; the hardest problems are tackled first and failure is discovered while it is still cheap |
   | Testing compressed and cut | Testing is part of every iteration and of the definition of done, not a separate phase that can be dropped |
   | No customer involvement | The customer or Product Owner is engaged continuously and reviews every increment |
   | Progress measured by documents | Working software is the primary measure of progress |
   | Unsuitable for long projects | A long project becomes a sequence of short ones, each of which delivers something usable |

   The mechanisms Agile uses to achieve this:
   - Short iterations or sprints, of one to four weeks, each producing a potentially shippable increment.
   - A prioritised product backlog, reordered before every sprint, so that the most valuable work is always done first.
   - Daily stand-up meetings, which surface obstacles within a day rather than a month.
   - Sprint reviews, at which the customer sees and tries the software.
   - Retrospectives, at which the team improves its own process.
   - Continuous integration and automated testing, so that the software is always in a working state.
   - Refactoring, so that the design can evolve rather than having to be right at the start.

   A balanced conclusion, which a good answer should include: Agile is not universally superior. Waterfall remains appropriate where requirements are genuinely fixed and where exhaustive documentation is a regulatory necessity, for example in avionics certified under DO-178C, in medical devices, or in a government procurement whose contract fixes scope and price in advance. Agile is appropriate where requirements are uncertain, where the customer is available, and where the ability to change direction is worth more than a fixed plan. Many organisations use a hybrid, planning at a high level in a Waterfall manner while executing each phase iteratively.
4. What is SDLC, Steps of SDLC, in which Step user acceptance assured? *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

   The phases:

   1. Planning and feasibility study:
   - Define the problem, the scope and the objectives.
   - Estimate cost, time and resources.
   - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
   - Output: the project plan and the feasibility report.

   2. Requirement analysis and specification:
   - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
   - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
   - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
   - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

   3. Design:
   - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
   - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
   - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
   - Output: the design document, sometimes divided into HLD and LLD.

   4. Implementation (coding):
   - The design is translated into source code in the chosen language, following coding standards.
   - Version control, code review and unit testing by the developer belong to this phase.
   - Output: the working source code and the developer documentation.

   5. Testing:
   - Verify that the software meets the specification and find defects before release.
   - Levels: unit testing, integration testing, system testing and acceptance testing.
   - Types: functional, performance, security, usability and regression testing.
   - Output: test plans, test cases, defect reports and the test summary.

   6. Deployment:
   - Install the system in the live environment, migrate the data, train the users and go live.
   - Strategies: direct changeover, parallel running, pilot and phased introduction.
   - Output: the running system and the user manual.

   7. Maintenance:
   - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
   - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
   - Output: updated versions and revised documentation.

   Diagram:

   ```mermaid
   flowchart LR
     A[Planning and Feasibility] --> B[Requirement Analysis]
     B --> C[Design]
     C --> D[Implementation]
     D --> E[Testing]
     E --> F[Deployment]
     F --> G[Maintenance]
     G -.feedback.-> B
   ```

   The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
5. **What is SDLC? Describe the steps of SDLC.** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)], [NPCBL Executive Trainee (Software) 26.05.2023 compact it 500 (ET: IBA)]*


   Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

   The phases:

   1. Planning and feasibility study:
   - Define the problem, the scope and the objectives.
   - Estimate cost, time and resources.
   - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
   - Output: the project plan and the feasibility report.

   2. Requirement analysis and specification:
   - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
   - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
   - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
   - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

   3. Design:
   - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
   - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
   - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
   - Output: the design document, sometimes divided into HLD and LLD.

   4. Implementation (coding):
   - The design is translated into source code in the chosen language, following coding standards.
   - Version control, code review and unit testing by the developer belong to this phase.
   - Output: the working source code and the developer documentation.

   5. Testing:
   - Verify that the software meets the specification and find defects before release.
   - Levels: unit testing, integration testing, system testing and acceptance testing.
   - Types: functional, performance, security, usability and regression testing.
   - Output: test plans, test cases, defect reports and the test summary.

   6. Deployment:
   - Install the system in the live environment, migrate the data, train the users and go live.
   - Strategies: direct changeover, parallel running, pilot and phased introduction.
   - Output: the running system and the user manual.

   7. Maintenance:
   - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
   - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
   - Output: updated versions and revised documentation.

   Diagram:

   ```mermaid
   flowchart LR
     A[Planning and Feasibility] --> B[Requirement Analysis]
     B --> C[Design]
     C --> D[Implementation]
     D --> E[Testing]
     E --> F[Deployment]
     F --> G[Maintenance]
     G -.feedback.-> B
   ```

   The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
6. **Why agile model is better than waterfall model?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: The Agile model is better than the Waterfall model in most modern software projects, for the following reasons. The claim should be qualified, however, because Waterfall remains preferable in specific circumstances, and a complete answer says so.

   Why Agile is better:

   - It delivers working software early and continuously. A customer receives something usable after two to four weeks rather than after a year, so value begins to accrue immediately and the investment is not entirely at risk until the end.

   - It welcomes changing requirements. In practice requirements always change, because business needs shift and because users cannot describe what they want until they see something. Waterfall treats change as an exception to be controlled; Agile treats it as normal and reprioritises the backlog each iteration.

   - It finds defects early. Testing happens in every iteration, so a defect is found within days of being created, when it is cheap to fix. In Waterfall a requirement error is discovered during system testing, by which time correcting it costs ten to a hundred times more.

   - It reduces risk. The hardest and most uncertain parts can be tackled in the first iterations, so a fatal technical or usability problem is discovered while the project can still be redirected or stopped. Waterfall concentrates all the risk at the end.

   - It keeps the customer involved throughout, so the divergence between what was specified and what is actually needed never grows large.

   - It measures progress by working software rather than by documents completed, which prevents the familiar illusion of a project reported as ninety per cent complete for months.

   - It improves team morale and communication, through daily stand-ups, self-organising teams and regular retrospectives in which the team improves its own process.

   - It suits the pace of modern business, where a competitor may release a product in the time a Waterfall project spends writing its specification.

   | Point | Waterfall Model | Agile Model |
   |---|---|---|
   | Approach | Linear and sequential | Iterative and incremental |
   | Phases | Completed once, strictly in order | Repeated in every short iteration |
   | Delivery | One delivery at the end | Working software every one to four weeks |
   | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
   | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
   | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
   | Testing | A single phase, late in the project | Continuous, in every iteration |
   | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
   | Flexibility | Low | High |
   | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
   | Progress measured by | Phase completion and documents signed off | Working software delivered |
   | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
   | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
   | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
   | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

   Where Waterfall is still better, which a balanced answer must state:
   - Where requirements are genuinely fixed and fully understood at the start, for example a system implementing a published tax rule.
   - Where exhaustive documentation is a legal or certification requirement, as in avionics, medical devices and defence.
   - Where the contract fixes scope, price and delivery date in advance, as in most government procurement, since Agile cannot promise a fixed scope for a fixed price.
   - Where the customer cannot make people available continuously.
   - For very small projects with a familiar technology, where the overhead of iteration ceremonies is not worth paying.

   Conclusion: Agile is better wherever requirements are uncertain and the ability to respond to change is worth more than a fixed plan, which describes the great majority of commercial software today. Waterfall is better where the specification is stable and the documentation is itself a deliverable. Many organisations use a hybrid, planning at a high level sequentially while executing each stage iteratively.
7. **a) What are the advantages and disadvantages of the Agile Model compared to the Waterfall Model in software development?** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*


   Answer: | Point | Waterfall Model | Agile Model |
   |---|---|---|
   | Approach | Linear and sequential | Iterative and incremental |
   | Phases | Completed once, strictly in order | Repeated in every short iteration |
   | Delivery | One delivery at the end | Working software every one to four weeks |
   | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
   | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
   | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
   | Testing | A single phase, late in the project | Continuous, in every iteration |
   | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
   | Flexibility | Low | High |
   | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
   | Progress measured by | Phase completion and documents signed off | Working software delivered |
   | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
   | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
   | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
   | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

   Advantages of the Agile model compared with Waterfall:
   - Working software is delivered every one to four weeks, so the customer sees value early instead of waiting for a single delivery at the end.
   - Changing requirements are welcomed rather than resisted, which matters because requirements always change in practice.
   - Defects are found within days through continuous testing, when they are far cheaper to correct than after a late test phase.
   - Risk is reduced, because the hardest problems can be tackled first and failure is discovered while the project can still be redirected.
   - The customer is involved throughout, so the system that is built is the system that is actually wanted.
   - Progress is measured by working software, which cannot be faked, rather than by documents signed off.
   - Team morale and communication improve through daily stand-ups, self-organisation and regular retrospectives.
   - Time to market is shorter, since a usable subset can be released long before the full product is complete.

   Disadvantages of the Agile model compared with Waterfall:
   - Documentation is lighter, which makes long-term maintenance, audit and hand-over to a different team harder. This is a real cost in a government system expected to run for twenty years.
   - The total cost and the delivery date cannot be fixed in advance, because scope is the variable. This makes Agile awkward for a fixed-price tender, which is the normal form of public procurement.
   - It requires continuous customer availability. If the Product Owner cannot attend reviews and answer questions promptly, the method stalls.
   - It depends on experienced, disciplined and self-motivated developers. An inexperienced team without discipline can turn Agile into unplanned coding.
   - Scope creep is a constant danger, since welcoming change can become never finishing.
   - It scales poorly to very large programmes without additional frameworks such as SAFe or LeSS, which reintroduce much of the overhead Agile sought to remove.
   - Architectural decisions can be deferred too long, producing a design that must later be reworked.
   - It is unsuitable where exhaustive certification evidence is required, as in avionics or medical devices.

   Summary judgement: Agile is preferable where requirements are uncertain, the customer is engaged and the ability to change direction is valuable. Waterfall is preferable where the specification is stable, the contract is fixed and the documentation is itself a deliverable. In practice many organisations adopt a hybrid, planning at a high level sequentially while executing each stage iteratively.
8. **Write down the differences between Agile model and Waterfall model in Software development. What is white box testing?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*


   Answer:

   Differences between the Agile model and the Waterfall model:

   | Point | Waterfall Model | Agile Model |
   |---|---|---|
   | Approach | Linear and sequential | Iterative and incremental |
   | Phases | Completed once, strictly in order | Repeated in every short iteration |
   | Delivery | One delivery at the end | Working software every one to four weeks |
   | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
   | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
   | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
   | Testing | A single phase, late in the project | Continuous, in every iteration |
   | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
   | Flexibility | Low | High |
   | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
   | Progress measured by | Phase completion and documents signed off | Working software delivered |
   | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
   | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
   | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
   | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

   White box testing:

   White box testing, also called structural testing, glass box testing, clear box testing or open box testing, is a testing technique in which the tester has full knowledge of the internal structure, design and source code of the system, and designs test cases to exercise that internal structure.

   What it examines:
   - Every statement, branch, path and loop in the code
   - Internal data structures and their manipulation
   - Conditions and their combinations
   - Error-handling paths that a user could not easily trigger from outside

   Coverage criteria, in increasing order of strength:
   - Statement coverage: every executable statement is run at least once.
   - Branch or decision coverage: every branch of every decision is taken both ways.
   - Condition coverage: every individual boolean sub-condition takes both values.
   - Path coverage: every independent path through the code is executed. Cyclomatic complexity, computed as E - N + 2 for a control flow graph with E edges and N nodes, gives the number of independent paths that must be covered.
   - Loop coverage: loops are executed zero times, once, and many times.

   Example:
   ```java
   int max(int a, int b) {
       if (a > b) {
           return a;
       } else {
           return b;
       }
   }
   ```
   Statement coverage needs only one test, say (5, 3). Branch coverage needs two, (5, 3) and (3, 5), so that both the if and the else are executed. A white box tester would also add the boundary case (5, 5), which a black box tester might miss.

   Who performs it: developers and testers with programming knowledge, usually during unit testing and integration testing.

   Advantages: it finds hidden logic errors and dead code; it can achieve measurable coverage; it tests error paths that are hard to reach from outside; and it can be largely automated, for example with JUnit together with a coverage tool such as JaCoCo.

   Disadvantages: it requires skilled testers who can read the code; it is expensive on a large system, since exhaustive path testing is combinatorially impossible; it does not detect missing requirements, because it tests only what was written, not what should have been written; and the tests must be revised whenever the code is refactored.

   Comparison with black box testing: black box testing is based on the specification alone, with no knowledge of the code, and it is performed by independent testers; it finds missing and incorrect functionality but cannot guarantee coverage of the code. Grey box testing combines the two, with partial knowledge of the internals. In practice both are needed: white box confirms that the code does what it says, and black box confirms that it does what the customer asked for.
9. **You are asked to lead a team of software engineers to develop an application software system for your company and deploy it as fast as possible. You need to gather user requirements, design, develop, test and then deploy the system. Between Waterfall Approach and Incremental Approach, which software development approach will you take for your software project? Explain your answer.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 338 (ET: BIBM)]*


   Answer: For this project I would take the Incremental approach rather than the Waterfall approach.

   Restating the situation: an application system is to be developed and deployed as fast as possible, and the full cycle of requirement gathering, design, development, testing and deployment must be carried out.

   Justification:

   - Speed of deployment is the stated priority. Waterfall delivers nothing until every phase is complete, so the first usable system appears only at the very end. The incremental approach delivers a working subset after the first increment, perhaps within a few weeks, and that subset can be deployed and used while the rest is being built. Since the requirement is to deploy as fast as possible, this alone is decisive.

   - Requirements will not be fully known at the start. In a business application the users cannot describe everything they need until they have seen something. Waterfall assumes a complete and correct specification before design begins, and that assumption fails here. The incremental approach gathers the requirements for the highest-priority features first, builds them, and refines the rest with the benefit of user feedback.

   - Feedback is incorporated cheaply. After each increment the users try the software and say what is wrong. Because the later increments have not yet been built, acting on that feedback costs little. In Waterfall the same discovery would come at acceptance testing, when correcting it costs ten to a hundred times more.

   - Risk is reduced. Technical and usability problems appear in the first increment rather than at the end. If something proves unworkable, only one increment has been lost, not the whole project.

   - Business value begins early. The company gets a return on part of the investment long before the project ends, which is exactly what "deploy as fast as possible" means in practice.

   - Testing is spread across the project rather than compressed into one late phase that gets cut when the schedule slips.

   How I would organise it:
   - Increment 1: the core function, the minimum viable product, deployed and used.
   - Increment 2 onwards: the next most valuable features, each fully analysed, designed, coded, tested and deployed.
   - Each increment of two to four weeks, with a review by the users at the end.
   - Run it as Scrum, with a prioritised product backlog, a Product Owner from the business, daily stand-ups, sprint reviews and retrospectives.
   - Use continuous integration and automated tests, so that each increment can be deployed without a long stabilisation period.

   When Waterfall would have been the right choice instead:
   - If the requirements were genuinely fixed and fully understood, for example a system implementing a published regulation.
   - If exhaustive documentation were required for certification or audit.
   - If the contract fixed scope, price and date in advance, as in most public procurement.
   - If the customer could not make people available for continuous involvement.
   None of these applies to a project whose declared objective is to deploy as fast as possible.

   Risks of the incremental approach, and how I would manage them:
   - Architectural rework, if early increments are built without thought for what follows. I would spend the first days on an architectural skeleton that anticipates the whole system, without building it all.
   - Scope creep, since welcoming change can become never finishing. I would fix the number of increments and the release date, and let scope be the variable.
   - Integration difficulty, addressed by continuous integration from the first day.
10. **(খ) Spiral Model চিত্রসহ ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


    Answer: Spiral Model হলো একটি ঝুঁকিনির্ভর (risk-driven) সফটওয়্যার উন্নয়ন মডেল, যা ব্যারি বোয়েম ১৯৮৮ সালে প্রস্তাব করেন। এটি Waterfall মডেলের ধারাবাহিকতা এবং Prototyping মডেলের পুনরাবৃত্তির সমন্বয়ে গঠিত, এবং এর প্রধান বৈশিষ্ট্য হলো প্রতিটি চক্রে আনুষ্ঠানিক ঝুঁকি বিশ্লেষণ।

    গঠন: প্রকল্পটি একটি সর্পিল পথে এগোয়। কেন্দ্র থেকে শুরু করে প্রতিটি পূর্ণ ঘূর্ণন বা চক্র (spiral) একটি সম্পূর্ণ পর্যায় নির্দেশ করে, এবং প্রতিটি চক্রে চারটি চতুর্ভাগ (quadrant) অতিক্রম করতে হয়।

    চিত্র:

    ```
             ঝুঁকি বিশ্লেষণ                 উদ্দেশ্য নির্ধারণ
          (Risk Analysis)              (Determine Objectives)
                  \                          /
                   \      ২য় চক্র           /
                    \   +-----------+     /
                     \  |  ১ম চক্র  |    /
                      \ |  +-----+  |   /
                       \|  |  o  |  |  /      o = শুরুর বিন্দু
                        +--+-----+--+-+
                       /|           |\
                      / |           | \
                     /  +-----------+  \
                    /                    \
           পরবর্তী পর্যায়ের              উন্নয়ন ও যাচাইকরণ
             পরিকল্পনা                  (Develop and Verify)
             (Plan)
    ```

    চারটি চতুর্ভাগ:

    ১. উদ্দেশ্য নির্ধারণ (Determine Objectives):
    - এই চক্রে কী অর্জন করতে হবে তা ঠিক করা।
    - বিকল্প সমাধানগুলো চিহ্নিত করা এবং সীমাবদ্ধতা (খরচ, সময়, প্রযুক্তি) নির্ধারণ করা।

    ২. ঝুঁকি নিরূপণ ও হ্রাস (Identify and Resolve Risks):
    - এটিই স্পাইরাল মডেলের প্রাণ এবং অন্য সব মডেল থেকে এর মূল পার্থক্য।
    - প্রযুক্তিগত, আর্থিক, সময়গত ও ব্যবস্থাপনাগত ঝুঁকি চিহ্নিত করা।
    - সবচেয়ে বড় ঝুঁকিগুলো কমাতে prototype তৈরি করা, সিমুলেশন চালানো বা সম্ভাব্যতা যাচাই করা।
    - ঝুঁকি অগ্রহণযোগ্য মনে হলে এখানেই প্রকল্প বন্ধ করে দেওয়া যায়, যা বড় অপচয় রোধ করে।

    ৩. উন্নয়ন ও যাচাইকরণ (Develop and Verify):
    - এই চক্রের জন্য নির্ধারিত অংশটি ডিজাইন, কোডিং ও টেস্ট করা।
    - প্রতিটি চক্রে এটি Waterfall এর মতো ধারাবাহিকভাবে সম্পন্ন হয়, তবে কেবল ওই অংশটুকুর জন্য।

    ৪. পরবর্তী পর্যায়ের পরিকল্পনা (Plan the Next Iteration):
    - গ্রাহকের মূল্যায়ন গ্রহণ করা।
    - পরবর্তী চক্রের পরিকল্পনা করা এবং প্রকল্প চালিয়ে যাওয়া হবে কিনা তা সিদ্ধান্ত নেওয়া।

    চক্রগুলো ক্রমশ বড় হতে থাকে, কারণ প্রতিটি চক্রে সঞ্চিত খরচ ও তৈরি হওয়া সফটওয়্যারের পরিমাণ বাড়ে।

    সুবিধা:
    - ঝুঁকি ব্যবস্থাপনাই এর কেন্দ্রবিন্দু, তাই বড় ও অনিশ্চিত প্রকল্পের জন্য সবচেয়ে উপযোগী।
    - গ্রাহক প্রতিটি চক্রেই ফলাফল দেখেন এবং মতামত দেন।
    - প্রয়োজনীয়তার পরিবর্তন পরবর্তী চক্রে গ্রহণ করা যায়।
    - Prototype তৈরির মাধ্যমে অস্পষ্ট প্রয়োজনীয়তা স্পষ্ট হয়।
    - খরচের অনুমান চক্রে চক্রে নির্ভুল হতে থাকে।
    - প্রকল্প ব্যর্থ হবে বুঝতে পারলে আগেভাগেই বন্ধ করা যায়।

    অসুবিধা:
    - অত্যন্ত ব্যয়বহুল; ছোট বা মাঝারি প্রকল্পের জন্য অতিরিক্ত।
    - ঝুঁকি বিশ্লেষণে বিশেষ দক্ষতা প্রয়োজন, যা সব দলে থাকে না। ঝুঁকি সঠিকভাবে চিহ্নিত না হলে পুরো মডেলটির সুবিধা নষ্ট হয়ে যায়।
    - কতগুলো চক্র লাগবে তা আগে থেকে বলা যায় না, তাই মোট সময় ও খরচ অনিশ্চিত।
    - ব্যবস্থাপনা জটিল এবং প্রচুর নথিপত্র তৈরি হয়।
    - স্থির মূল্যের চুক্তিতে ব্যবহার করা কঠিন।

    কখন ব্যবহার করা উপযুক্ত: বৃহৎ ও ব্যয়বহুল প্রকল্প, উচ্চ ঝুঁকিসম্পন্ন প্রকল্প, অস্পষ্ট বা পরিবর্তনশীল প্রয়োজনীয়তা, নতুন ও অপরীক্ষিত প্রযুক্তি, এবং দীর্ঘমেয়াদি প্রকল্প। প্রতিরক্ষা, মহাকাশ ও বড় সরকারি ব্যবস্থায় এটি ব্যবহৃত হয়।

    অন্য মডেলের সঙ্গে সম্পর্ক: Waterfall ধারাবাহিক কিন্তু পুনরাবৃত্তিহীন; Prototyping পুনরাবৃত্ত কিন্তু ঝুঁকি বিশ্লেষণহীন; Spiral দুটির সমন্বয় এবং তার ওপর ঝুঁকি বিশ্লেষণ যুক্ত। Agile ও পুনরাবৃত্ত, কিন্তু এর চক্র অনেক ছোট (২-৪ সপ্তাহ) এবং আনুষ্ঠানিক ঝুঁকি বিশ্লেষণের বদলে ধারাবাহিক সরবরাহের ওপর জোর দেয়।
11. **Write down the step of SDLC?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)], [BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
12. **Which SDLC do you prefer between Agile and waterfall model explain with example.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 522 (ET: MIST)]*


    Answer: I prefer the Agile model for most modern projects, but the correct answer states the condition under which each is right, and then justifies the preference with an example.

    | Point | Waterfall Model | Agile Model |
    |---|---|---|
    | Approach | Linear and sequential | Iterative and incremental |
    | Phases | Completed once, strictly in order | Repeated in every short iteration |
    | Delivery | One delivery at the end | Working software every one to four weeks |
    | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
    | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
    | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
    | Testing | A single phase, late in the project | Continuous, in every iteration |
    | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
    | Flexibility | Low | High |
    | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
    | Progress measured by | Phase completion and documents signed off | Working software delivered |
    | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
    | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
    | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
    | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

    Example 1 - where Agile is clearly the right choice:

    A bank wishes to build a mobile banking application. At the start nobody knows exactly which features customers will use, the competition is releasing new features every month, and the regulator's rules on digital transactions are still evolving.

    With Agile: the team releases a first version in six weeks with balance enquiry and fund transfer only. Real customers use it, and the analytics show that bill payment is requested far more often than the statement download that had been planned next, so the backlog is reordered. When the central bank issues a new rule on transaction limits, it is absorbed in the next sprint. After a year the application has been through twenty releases, each guided by real use.

    With Waterfall the same project would have spent four months writing a specification, six months building, and would have released after a year a product designed around assumptions made before a single customer had used anything.

    Example 2 - where Waterfall is the right choice:

    A government department must build a system to compute income tax under a published finance act. The rules are fixed by law, they are written down completely, and they will not change during the project. The contract is a fixed-price tender with a fixed delivery date, and the auditor requires full traceability from every requirement to the code that implements it.

    Here Waterfall is appropriate: the requirements genuinely are complete and stable, the documentation is itself a deliverable, and the fixed-price contract cannot accommodate a method in which scope is the variable.

    My preference and its reasoning:

    I prefer Agile, because:
    - Requirements change in almost every real project, and Agile treats that as normal rather than as an exception to be controlled.
    - Working software every few weeks reduces risk, since a fundamental error is discovered in the first month rather than the eleventh.
    - Defects found in the same iteration in which they are created cost a fraction of what they cost after a late test phase.
    - The customer sees and steers the product continuously, so the system delivered is the system actually wanted.
    - Progress is measured by working software, which cannot be exaggerated the way a document count can.

    But I would use Waterfall, or a hybrid, when:
    - The requirements are fixed by law or by an external standard.
    - Certification requires exhaustive documentation, as in avionics or medical devices.
    - The contract fixes scope, price and date, which is the norm in public procurement.
    - The customer cannot make people available continuously, which Agile absolutely requires.

    The hybrid that many organisations actually use: plan the programme at a high level in phases, as Waterfall does, so that the contract and the budget can be written, but execute each phase iteratively with sprints, reviews and continuous testing. This gives the contractual predictability of Waterfall together with the feedback and risk reduction of Agile.
13. **Define SDLC? Write the steps of SDLC?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
14. **What is SDLC? Write the name of 7 phase of SDLC?** *[DESCO Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its retirement, and its purpose is to produce software of predictable quality within budget and on schedule.

    The seven phases of SDLC:

    1. Planning and feasibility study: define the problem, the scope and the objectives; estimate cost, time and resources; and assess technical, economic, operational and legal feasibility. Output: the project plan and the feasibility report.

    2. Requirement analysis: gather and analyse what the system must do, through interviews, questionnaires, observation and study of existing documents; separate functional from non-functional requirements; and check that each is complete, consistent, unambiguous and verifiable. Output: the Software Requirements Specification (SRS).

    3. Design: decide how the system will be built. High-level design fixes the architecture, the modules, the database schema and the interfaces; low-level design fixes the internal logic, the algorithms and the data structures of each module. Output: the design document.

    4. Implementation (coding): translate the design into source code in the chosen language, following coding standards, under version control, with code review and unit testing by the developer. Output: the working source code.

    5. Testing: verify that the software meets the specification and find defects before release, at the levels of unit, integration, system and acceptance testing. Output: test plans, test cases, defect reports and the test summary.

    6. Deployment: install the system in the live environment, migrate the data, train the users and go live, using a direct, parallel, pilot or phased changeover. Output: the running system and the user manual.

    7. Maintenance: correct faults found in use, adapt to changes in the environment, add enhancements and improve internal quality. This is the longest and most expensive phase, typically 60 to 70 per cent of the total lifetime cost.

    Diagram:

    ```mermaid
    flowchart LR
      A[1 Planning] --> B[2 Requirement Analysis]
      B --> C[3 Design]
      C --> D[4 Implementation]
      D --> E[5 Testing]
      E --> F[6 Deployment]
      F --> G[7 Maintenance]
      G -.feedback.-> B
    ```

    Note on the number of phases: different textbooks divide the same work into five, six, seven or eight phases. The seven-phase form given above is the most common, and some books add "documentation" or split "planning" from "feasibility". What matters in an answer is that the sequence and the purpose of each phase are correct, not the exact count.

    The phase that assures user acceptance: acceptance testing, within phase 5, in which the customer's own users run the system against real business scenarios and formally accept or reject it.
15. **(a) What do you understand by Agile? Mention its four values.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 486 (ET: N/A)]*


    Answer: Agile is an iterative and incremental approach to software development in which requirements and solutions evolve through collaboration between self-organising cross-functional teams and the customer. Work is delivered in short cycles called iterations or sprints, typically of one to four weeks, and each cycle produces a potentially shippable increment of working software.

    The four values of the Agile Manifesto, published in 2001 by seventeen practitioners:

    - Individuals and interactions over processes and tools
    - Working software over comprehensive documentation
    - Customer collaboration over contract negotiation
    - Responding to change over following a plan

    The manifesto adds the crucial qualification: while there is value in the items on the right, the items on the left are valued more. Agile does not reject documentation or planning; it subordinates them to working software and to responsiveness.

    The twelve principles behind the manifesto, in summary:
    1. Satisfy the customer through early and continuous delivery of valuable software.
    2. Welcome changing requirements, even late in development.
    3. Deliver working software frequently, from a couple of weeks to a couple of months.
    4. Business people and developers must work together daily.
    5. Build projects around motivated individuals, give them the environment and support they need, and trust them.
    6. Face-to-face conversation is the most efficient method of conveying information.
    7. Working software is the primary measure of progress.
    8. Promote sustainable development, at a pace that can be maintained indefinitely.
    9. Continuous attention to technical excellence and good design enhances agility.
    10. Simplicity, the art of maximising the work not done, is essential.
    11. The best architectures, requirements and designs emerge from self-organising teams.
    12. At regular intervals the team reflects on how to become more effective and adjusts accordingly.

    Popular Agile frameworks:
    - Scrum: sprints of two to four weeks, roles of Product Owner, Scrum Master and Development Team, artefacts of product backlog, sprint backlog and increment, and ceremonies of sprint planning, daily stand-up, sprint review and retrospective.
    - Extreme Programming (XP): pair programming, test-driven development, continuous integration, refactoring, simple design and frequent small releases.
    - Kanban: a visual board, limits on work in progress, and continuous flow rather than fixed iterations.
    - Lean software development, Crystal, and the Feature Driven Development method.

    Advantages: rapid delivery of usable software; the customer sees progress every few weeks; changing requirements are welcomed rather than resisted; defects are found early through continuous testing; risk is reduced because problems surface in the first iterations; and team morale and communication improve.

    Disadvantages: less documentation, which can make long-term maintenance and hand-over harder; the total cost and schedule are difficult to fix in advance, which makes it awkward for fixed-price government contracts; it requires continuous customer availability, which is often not forthcoming; it depends on experienced and disciplined developers; it scales less easily to very large teams without additional frameworks such as SAFe; and without discipline it can degenerate into unplanned coding.
16. **(a) Write down the steps of Waterfall model.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*


    Answer: The steps of the Waterfall model:

    1. Requirement analysis and specification: gather all the requirements from the customer, analyse them for completeness and consistency, and record them in the Software Requirements Specification (SRS), which becomes the contract for the rest of the project.

    2. System design: convert the requirements into a design. High-level design fixes the architecture, the modules, the database schema and the interfaces; low-level design fixes the internal logic, algorithms and data structures of each module. Output: the System Design Document.

    3. Implementation (coding): translate the design into source code, module by module, following coding standards, with unit testing by the developer as each module is finished.

    4. Integration and testing: combine the modules into the complete system and test it against the SRS. Integration testing, system testing and acceptance testing all belong here.

    5. Deployment: install the system in the customer's environment, migrate the data, train the users and go live.

    6. Maintenance: correct faults found in use, adapt the system to changes in its environment, and add enhancements. This is the longest and costliest phase.

    Diagram:

    ```
    Requirement Analysis
             |
             v
        System Design
             |
             v
       Implementation
             |
             v
    Integration and Testing
             |
             v
         Deployment
             |
             v
        Maintenance
    ```

    The defining rules of the model:
    - Each phase must be completed and formally reviewed before the next begins.
    - The output of one phase is the input of the next.
    - There is no overlapping between phases, and going back is expensive.
    - Each phase produces a document, and progress is measured by those documents.

    Where it works: stable and well-understood requirements, a familiar technology, a short project, and a contract that fixes scope and price.

    Where it fails: no working software until the end, no ability to accommodate change, defects found late when they are most expensive, and all the risk concentrated at the final acceptance.

    Historical note worth adding: Winston Royce, who described this model in 1970, wrote in the same paper that the pure sequential form was risky and invited failure, and recommended iteration and prototyping. The model became a standard through a misreading of that paper.
17. **(খ) Software Engineering এর ক্ষেত্রে Waterfall Model বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*


    Answer: The Waterfall model is the classical linear sequential model of software development, proposed by Winston Royce in 1970. Each phase must be completed and approved before the next begins, and the output of one phase is the input of the next, so the progress flows steadily downwards like a waterfall.

      Phases:
      1. Requirement analysis and specification, producing the SRS
      2. System design, producing the architecture and the detailed design
      3. Implementation, producing the code
      4. Integration and testing
      5. Deployment
      6. Maintenance

      ```
      Requirements
           |
           v
        Design
           |
           v
    Implementation
           |
           v
        Testing
           |
           v
      Deployment
           |
           v
      Maintenance
      ```

      Advantages:
      - Simple to understand, to explain and to manage, which is why it is still taught first.
      - Each phase has well-defined deliverables and a formal review, so progress is easy to measure.
      - Heavy documentation makes the system maintainable long after the original team has gone, and it survives staff turnover.
      - It works well when the requirements are stable, clearly understood and unlikely to change, for example in a system that must satisfy a fixed legal or regulatory specification.
      - Suits small projects with a familiar technology, and it is easy to schedule and to cost.
      - The clear contractual milestones suit government and defence procurement, which is why it remains common in public-sector tenders.

      Disadvantages and limitations:
      - No working software is produced until late in the cycle, so the customer sees nothing for months and cannot judge whether it is what was wanted.
      - It cannot accommodate changing requirements. Going back to an earlier phase is expensive, and in practice requirements always change.
      - It assumes the customer can state all requirements correctly at the start, which is rarely true. Users often do not know what they want until they see something.
      - Defects introduced in the requirement or design phase are found only during testing, when they are ten to a hundred times more expensive to correct.
      - Risk is concentrated at the end: if the system proves unusable at acceptance, the whole investment is lost.
      - Testing is compressed into a single late phase, and when the project runs late it is the phase that gets cut.
      - There is no customer involvement between the requirements phase and delivery.
      - It is unsuitable for large, long or complex projects, and for anything exploratory.

      Royce's own view is worth stating: in the very paper that described the model, Royce wrote that this pure sequential form was "risky and invites failure", and he recommended iteration and prototyping. The model became a standard largely by misreading of that paper.
18. **(খ) Software maintenance এর সাথে কী কী বিষয় জড়িত, তা আলোচনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*


    Answer: Software maintenance বলতে বোঝায় সফটওয়্যার সরবরাহের পর তাতে করা সব পরিবর্তন — ত্রুটি সংশোধন, পরিবেশের পরিবর্তনের সঙ্গে খাপ খাওয়ানো, নতুন সুবিধা যোগ করা এবং ভবিষ্যতের রক্ষণাবেক্ষণ সহজ করা।

    এটি SDLC এর সবচেয়ে দীর্ঘ ও ব্যয়বহুল পর্যায়। একটি সফটওয়্যারের সম্পূর্ণ জীবনকালের মোট খরচের প্রায় ৬০ থেকে ৭০ শতাংশ ব্যয় হয় রক্ষণাবেক্ষণেই, উন্নয়নে নয়।

    Software maintenance এর সঙ্গে যে যে বিষয় জড়িত:

    ১. রক্ষণাবেক্ষণের প্রকারভেদ:

    - Corrective maintenance (সংশোধনমূলক): ব্যবহারের সময় পাওয়া ত্রুটি বা বাগ সারানো। মোট রক্ষণাবেক্ষণের প্রায় ২০ শতাংশ।
    - Adaptive maintenance (অভিযোজনমূলক): পরিবেশের পরিবর্তনের সঙ্গে খাপ খাওয়ানো, যেমন নতুন অপারেটিং সিস্টেম, নতুন ডেটাবেজ সংস্করণ, নতুন হার্ডওয়্যার বা নতুন সরকারি বিধি। প্রায় ২৫ শতাংশ।
    - Perfective maintenance (উৎকর্ষমূলক): ব্যবহারকারীর অনুরোধে নতুন সুবিধা যোগ করা বা কর্মদক্ষতা বাড়ানো। সবচেয়ে বড় অংশ, প্রায় ৫০ শতাংশ।
    - Preventive maintenance (প্রতিরোধমূলক): ভবিষ্যতের সমস্যা এড়াতে কোড পরিষ্কার করা, রিফ্যাক্টর করা ও নথিপত্র হালনাগাদ করা। প্রায় ৫ শতাংশ।

    ২. রক্ষণাবেক্ষণের কার্যক্রম:
    - পরিবর্তনের অনুরোধ গ্রহণ ও বিশ্লেষণ করা।
    - প্রভাব বিশ্লেষণ (impact analysis): এই পরিবর্তনে আর কোন কোন অংশ প্রভাবিত হবে তা নির্ণয় করা।
    - খরচ ও সময় নিরূপণ করা এবং অনুমোদন নেওয়া।
    - প্রোগ্রাম বোঝা (program comprehension): অন্যের লেখা পুরোনো কোড পড়ে বোঝা, যা রক্ষণাবেক্ষণের সবচেয়ে সময়সাপেক্ষ অংশ; কোনো কোনো গবেষণায় এতে ৫০ শতাংশের বেশি সময় যায়।
    - কোড পরিবর্তন করা ও নতুন ইউনিট টেস্ট লেখা।
    - Regression testing: নিশ্চিত করা যে পরিবর্তনটি আগের কাজ করা অংশ ভেঙে ফেলেনি।
    - নথিপত্র হালনাগাদ করা।
    - নতুন সংস্করণ প্রকাশ ও স্থাপন করা।

    ৩. সহায়ক ব্যবস্থাপনা:
    - Configuration management: কোন সংস্করণে কী আছে তার হিসাব রাখা, শাখা ব্যবস্থাপনা ও প্রকাশনার নিয়ন্ত্রণ। Git এর মতো সংস্করণ নিয়ন্ত্রণ ব্যবস্থা এর ভিত্তি।
    - Change control board: কোন অনুরোধ গ্রহণ করা হবে তা সিদ্ধান্ত নেওয়ার আনুষ্ঠানিক কমিটি।
    - Issue tracking system: ত্রুটি ও অনুরোধের হিসাব রাখা।
    - Service level agreement: কত সময়ের মধ্যে কোন শ্রেণির সমস্যার সমাধান দিতে হবে।

    ৪. যেসব বিষয় রক্ষণাবেক্ষণ কঠিন করে তোলে:
    - অপর্যাপ্ত বা পুরোনো নথিপত্র।
    - মূল ডেভেলপারদের চলে যাওয়া, ফলে জ্ঞান হারিয়ে যাওয়া।
    - দুর্বল বা জটিল নকশা, উচ্চ coupling ও নিম্ন cohesion।
    - Technical debt বা কারিগরি ঋণ: দ্রুত সরবরাহের জন্য নেওয়া শর্টকাট, যার সুদ পরে দিতে হয়।
    - পুরোনো প্রযুক্তি বা ভাষা, যাতে দক্ষ লোক পাওয়া যায় না।
    - স্বয়ংক্রিয় পরীক্ষার অভাব, ফলে প্রতিটি পরিবর্তনের পর ম্যানুয়াল পরীক্ষা করতে হয়।

    ৫. রক্ষণাবেক্ষণ সহজ করার উপায়:
    - পরিষ্কার ও মডিউলার নকশা, উচ্চ cohesion ও নিম্ন coupling।
    - কোডিং মান মেনে চলা এবং অর্থবহ নামকরণ।
    - পর্যাপ্ত ও হালনাগাদ নথিপত্র।
    - স্বয়ংক্রিয় ইউনিট ও রিগ্রেশন টেস্ট, যা প্রতিটি পরিবর্তনের পর চালানো যায়।
    - সংস্করণ নিয়ন্ত্রণ ও ধারাবাহিক সংযোজন (CI)।
    - নিয়মিত রিফ্যাক্টরিং, যাতে কারিগরি ঋণ জমে না যায়।
    - কোড রিভিউ, যাতে জ্ঞান একাধিক ব্যক্তির মধ্যে ছড়িয়ে থাকে।

    ৬. Lehman এর সফটওয়্যার বিবর্তনের সূত্র, যা এই পর্যায়ের তাত্ত্বিক ভিত্তি:
    - ক্রমাগত পরিবর্তনের সূত্র: ব্যবহৃত সফটওয়্যারকে অবশ্যই বদলাতে হবে, নইলে তা ক্রমশ কম উপযোগী হয়ে পড়ে।
    - ক্রমবর্ধমান জটিলতার সূত্র: সফটওয়্যার বদলাতে থাকলে তার জটিলতা বাড়ে, যদি না সচেতনভাবে তা কমানো হয়।
    - গুণমান হ্রাসের সূত্র: পরিবেশের সঙ্গে খাপ না খাওয়ালে সফটওয়্যারের মান কমতে থাকে বলে মনে হয়।

    সারকথা: রক্ষণাবেক্ষণ কোনো গৌণ কাজ নয়; এটিই সফটওয়্যারের জীবনের প্রধান অংশ। তাই উন্নয়নের সময় নেওয়া প্রতিটি সিদ্ধান্ত এই প্রশ্ন সামনে রেখে নেওয়া উচিত: পাঁচ বছর পর যে ব্যক্তি এই কোড রক্ষণাবেক্ষণ করবেন, তিনি কি এটি বুঝতে পারবেন?
19. **(ক) Waterfall model বিস্তারিত বর্ণনা করুন। এই model এর সুবিধা এবং সীমাবদ্ধতাগুলো উল্লেখ করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*


    Answer: The Waterfall model is the classical linear sequential model of software development, proposed by Winston Royce in 1970. Each phase must be completed and approved before the next begins, and the output of one phase is the input of the next, so the progress flows steadily downwards like a waterfall.

      Phases:
      1. Requirement analysis and specification, producing the SRS
      2. System design, producing the architecture and the detailed design
      3. Implementation, producing the code
      4. Integration and testing
      5. Deployment
      6. Maintenance

      ```
      Requirements
           |
           v
        Design
           |
           v
    Implementation
           |
           v
        Testing
           |
           v
      Deployment
           |
           v
      Maintenance
      ```

      Advantages:
      - Simple to understand, to explain and to manage, which is why it is still taught first.
      - Each phase has well-defined deliverables and a formal review, so progress is easy to measure.
      - Heavy documentation makes the system maintainable long after the original team has gone, and it survives staff turnover.
      - It works well when the requirements are stable, clearly understood and unlikely to change, for example in a system that must satisfy a fixed legal or regulatory specification.
      - Suits small projects with a familiar technology, and it is easy to schedule and to cost.
      - The clear contractual milestones suit government and defence procurement, which is why it remains common in public-sector tenders.

      Disadvantages and limitations:
      - No working software is produced until late in the cycle, so the customer sees nothing for months and cannot judge whether it is what was wanted.
      - It cannot accommodate changing requirements. Going back to an earlier phase is expensive, and in practice requirements always change.
      - It assumes the customer can state all requirements correctly at the start, which is rarely true. Users often do not know what they want until they see something.
      - Defects introduced in the requirement or design phase are found only during testing, when they are ten to a hundred times more expensive to correct.
      - Risk is concentrated at the end: if the system proves unusable at acceptance, the whole investment is lost.
      - Testing is compressed into a single late phase, and when the project runs late it is the phase that gets cut.
      - There is no customer involvement between the requirements phase and delivery.
      - It is unsuitable for large, long or complex projects, and for anything exploratory.

      Royce's own view is worth stating: in the very paper that described the model, Royce wrote that this pure sequential form was "risky and invites failure", and he recommended iteration and prototyping. The model became a standard largely by misreading of that paper.
20. **How does agile methodology used in software development differ from that of waterfall methodology? Explain in brief.** *[BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*


    Answer: | Point | Waterfall Model | Agile Model |
    |---|---|---|
    | Approach | Linear and sequential | Iterative and incremental |
    | Phases | Completed once, strictly in order | Repeated in every short iteration |
    | Delivery | One delivery at the end | Working software every one to four weeks |
    | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
    | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
    | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
    | Testing | A single phase, late in the project | Continuous, in every iteration |
    | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
    | Flexibility | Low | High |
    | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
    | Progress measured by | Phase completion and documents signed off | Working software delivered |
    | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
    | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
    | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
    | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

    In brief: Waterfall completes each phase once, in a fixed order, and delivers everything at the end; Agile repeats all the phases in every short iteration and delivers a working increment every few weeks. Waterfall fixes the scope and lets time and cost vary; Agile fixes time and cost and lets scope vary. Waterfall treats change as an exception to be controlled; Agile treats it as normal and expected.
21. **Software engineering এ ফিজিবিলিটি স্ট্যাড্যির ৭টি ধাপ বর্ণনা কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*


    Answer: ফিজিবিলিটি স্টাডি বা সম্ভাব্যতা যাচাই হলো SDLC এর প্রথম পর্যায়ের একটি গুরুত্বপূর্ণ কাজ, যেখানে প্রস্তাবিত ব্যবস্থাটি আদৌ তৈরি করা সম্ভব ও যুক্তিসঙ্গত কিনা তা যাচাই করা হয়। উদ্দেশ্য হলো বড় বিনিয়োগ করার আগেই অকার্যকর প্রকল্প বাতিল করা।

    ফিজিবিলিটি স্টাডির সাতটি ধাপ:

    ১. প্রাথমিক তথ্য সংগ্রহ ও পরিধি নির্ধারণ (Information Gathering and Scope Definition):
    - বর্তমান ব্যবস্থা কীভাবে চলছে তা পর্যবেক্ষণ ও নথিভুক্ত করা।
    - ব্যবহারকারী, ব্যবস্থাপক ও অংশীজনদের সাক্ষাৎকার নেওয়া।
    - প্রকল্পের সীমানা নির্ধারণ করা: কী কী অন্তর্ভুক্ত হবে এবং কী কী হবে না।

    ২. সমস্যা ও উদ্দেশ্য নির্ধারণ (Problem Definition and Objectives):
    - বর্তমান ব্যবস্থার প্রকৃত সমস্যাগুলো স্পষ্টভাবে চিহ্নিত করা।
    - নতুন ব্যবস্থার কাছ থেকে কী প্রত্যাশা করা হচ্ছে তা পরিমাপযোগ্য ভাষায় লেখা, যেমন "আবেদন প্রক্রিয়াকরণের সময় ৭ দিন থেকে ১ দিনে নামিয়ে আনা"।

    ৩. বিকল্প সমাধান চিহ্নিতকরণ (Identify Alternative Solutions):
    - নিজে তৈরি করা, তৈরি সফটওয়্যার কেনা, ভাড়া নেওয়া (SaaS), অথবা বর্তমান ব্যবস্থা উন্নত করা — এই বিকল্পগুলো তালিকাভুক্ত করা।
    - প্রতিটি বিকল্পের প্রাথমিক রূপরেখা তৈরি করা।

    ৪. কারিগরি সম্ভাব্যতা যাচাই (Technical Feasibility):
    - প্রয়োজনীয় হার্ডওয়্যার, সফটওয়্যার ও প্রযুক্তি বিদ্যমান আছে কিনা।
    - প্রতিষ্ঠানে বা বাজারে প্রয়োজনীয় দক্ষ জনবল পাওয়া যাবে কিনা।
    - ব্যবস্থাটি প্রয়োজনীয় গতি, ধারণক্ষমতা ও নিরাপত্তা দিতে পারবে কিনা।

    ৫. অর্থনৈতিক সম্ভাব্যতা যাচাই (Economic Feasibility):
    - এটিই সাধারণত সবচেয়ে নির্ণায়ক ধাপ; একে বলা হয় Cost-Benefit Analysis।
    - খরচ: উন্নয়ন ব্যয়, হার্ডওয়্যার, লাইসেন্স, প্রশিক্ষণ ও বার্ষিক রক্ষণাবেক্ষণ।
    - সুফল: বাস্তব সুফল (শ্রম সাশ্রয়, কাগজ সাশ্রয়, দ্রুত সেবা) এবং অবাস্তব সুফল (ভাবমূর্তি, সিদ্ধান্তের মান)।
    - সূচক: Return on Investment, Net Present Value, Payback Period ও Break-even point।

    ৬. পরিচালনগত, আইনগত ও সময়গত সম্ভাব্যতা যাচাই (Operational, Legal and Schedule Feasibility):
    - Operational: ব্যবহারকারীরা কি ব্যবস্থাটি গ্রহণ করবেন ও ব্যবহার করবেন? প্রতিরোধ আসবে কিনা? প্রশিক্ষণ দিয়ে সামলানো যাবে কিনা?
    - Legal: তথ্য সুরক্ষা আইন, কপিরাইট, লাইসেন্স ও সরকারি বিধি লঙ্ঘিত হচ্ছে কিনা।
    - Schedule: নির্ধারিত সময়ের মধ্যে শেষ করা বাস্তবসম্মত কিনা।

    ৭. প্রতিবেদন প্রণয়ন ও সুপারিশ (Feasibility Report and Recommendation):
    - সব বিশ্লেষণ একত্র করে একটি আনুষ্ঠানিক প্রতিবেদন তৈরি করা।
    - প্রতিটি বিকল্পের তুলনামূলক বিচার দেখানো।
    - স্পষ্ট সুপারিশ দেওয়া: প্রকল্পটি এগিয়ে নেওয়া হবে (go), বাতিল করা হবে (no-go), নাকি পরিবর্তিত আকারে নেওয়া হবে।
    - ঊর্ধ্বতন কর্তৃপক্ষের অনুমোদন গ্রহণ করা।

    সম্ভাব্যতার প্রধান চারটি দিক, সংক্ষেপে TELOS নামে পরিচিত:
    - Technical (কারিগরি)
    - Economic (অর্থনৈতিক)
    - Legal (আইনগত)
    - Operational (পরিচালনগত)
    - Schedule (সময়গত)

    কেন এই ধাপটি অপরিহার্য: প্রকল্পের শুরুতে অল্প খরচে করা একটি সম্ভাব্যতা যাচাই কোটি টাকার ব্যর্থ প্রকল্প ঠেকিয়ে দিতে পারে। বহু সরকারি আইটি প্রকল্প ব্যর্থ হয় এই কারণে যে শুরুতেই পরিচালনগত সম্ভাব্যতা যাচাই করা হয়নি — অর্থাৎ ব্যবস্থাটি কারিগরিভাবে ঠিক ছিল, কিন্তু ব্যবহারকারীরা তা ব্যবহার করেননি।
22. **Explain software development life cycle (SDLC).** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 678 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
23. **(b) What is SDLC? Define the activities of the design phase in SDLC.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes from conception to retirement: planning and feasibility, requirement analysis, design, implementation, testing, deployment and maintenance. Its purpose is to produce software of predictable quality within budget and on schedule.

    Activities of the design phase:

    The design phase converts what the system must do, recorded in the Software Requirements Specification, into how it will be built. It is divided into high-level and low-level design.

    High-level design, also called architectural or system design:

    - Architectural design: choose the overall structure, for example layered, client-server, microservices or event-driven, and justify the choice against the non-functional requirements.
    - Module decomposition: divide the system into modules or subsystems, and define the responsibility of each, aiming for high cohesion within a module and low coupling between modules.
    - Interface design between modules: define exactly what each module offers to the others and what it requires, so that different teams can work in parallel.
    - Database design: design the conceptual, logical and physical schema; draw the entity-relationship diagram; normalise the relations; choose keys, indexes and constraints.
    - Technology selection: programming language, framework, database, application server, and the deployment platform.
    - Data flow design: draw data flow diagrams showing how data moves through the processes and stores.
    - Security architecture: authentication, authorisation, encryption of data at rest and in transit, and audit logging.
    - Deployment architecture: servers, network topology, load balancing, redundancy and backup.

    Low-level design, also called detailed design:

    - Module internal design: the algorithm and the logic of each module, expressed in pseudocode, flowcharts or activity diagrams.
    - Data structure design: the structures used inside each module and their complexity.
    - Function and method specification: the signature, the parameters, the return value, the preconditions and the postconditions of every function.
    - Error handling design: which errors can occur, how each is detected, reported and recovered from.
    - User interface design: screen layouts, navigation, input validation, messages, and adherence to usability and accessibility guidelines.
    - Report design: the layout and content of every printed or exported report.
    - File and data format design.
    - Test design: the test cases can and should be derived from the design, before the code is written.

    Cross-cutting activities in the design phase:

    - Applying design principles: high cohesion, low coupling, information hiding, separation of concerns, and the SOLID principles.
    - Applying design patterns where they fit: Singleton, Factory, Observer, Strategy, MVC and others, so that well-known problems are solved in well-understood ways.
    - Design review or walkthrough, in which the design is inspected by peers before coding begins. Finding a design fault here costs a fraction of finding it during testing.
    - Traceability: every requirement in the SRS must be traceable to at least one design element, and every design element must trace back to a requirement, so that nothing is missed and nothing superfluous is built.
    - Prototyping of the user interface, to obtain user feedback before the code is written.
    - Estimating effort for the implementation phase, now that the modules are known.

    Deliverables of the design phase:
    - The High-Level Design Document (HLD)
    - The Low-Level Design Document (LLD)
    - The database schema and the entity-relationship diagram
    - UML diagrams: class, sequence, component and deployment
    - Interface specifications
    - The user interface prototype or wireframes
    - An updated traceability matrix

    Why the design phase matters most: a defect introduced in design and found in testing costs ten to a hundred times more to correct than one found during the design review itself. Time spent on design is therefore the cheapest time in the whole project.
24. **(ক) Software development এর Agile পদ্ধতির মূলনীতিগুলো লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 706 (ET: N/A)]*


    Answer: Agile পদ্ধতির মূলনীতিসমূহ নিচে দেওয়া হলো। Agile হলো সফটওয়্যার উন্নয়নের একটি পুনরাবৃত্ত ও ক্রমবর্ধমান পদ্ধতি, যেখানে ছোট ছোট চক্রে (sprint, সাধারণত ১ থেকে ৪ সপ্তাহ) কার্যকর সফটওয়্যার সরবরাহ করা হয় এবং প্রতিটি চক্রে গ্রাহকের মতামত গ্রহণ করা হয়।

    Agile Manifesto (২০০১) এর চারটি মূল্যবোধ:
    - প্রক্রিয়া ও যন্ত্রের চেয়ে ব্যক্তি ও পারস্পরিক যোগাযোগ বেশি গুরুত্বপূর্ণ।
    - বিস্তারিত নথিপত্রের চেয়ে কার্যকর সফটওয়্যার বেশি গুরুত্বপূর্ণ।
    - চুক্তি নিয়ে দর কষাকষির চেয়ে গ্রাহকের সঙ্গে সহযোগিতা বেশি গুরুত্বপূর্ণ।
    - পরিকল্পনা অনুসরণের চেয়ে পরিবর্তনে সাড়া দেওয়া বেশি গুরুত্বপূর্ণ।

    উল্লেখযোগ্য: ইশতেহারে স্পষ্ট বলা আছে যে ডান পাশের বিষয়গুলোরও মূল্য আছে, কেবল বাম পাশেরগুলোকে বেশি মূল্য দেওয়া হয়। অর্থাৎ Agile নথিপত্র বা পরিকল্পনা বাতিল করে না, বরং সেগুলোকে কার্যকর সফটওয়্যারের অধীনে রাখে।

    বারোটি মূলনীতি:

    ১. আগেভাগে ও ধারাবাহিকভাবে মূল্যবান সফটওয়্যার সরবরাহ করে গ্রাহককে সন্তুষ্ট করা।
    ২. প্রয়োজনীয়তার পরিবর্তনকে স্বাগত জানানো, এমনকি উন্নয়নের শেষ পর্যায়েও।
    ৩. কয়েক সপ্তাহ থেকে কয়েক মাস অন্তর কার্যকর সফটওয়্যার সরবরাহ করা, যত ঘন ঘন সম্ভব।
    ৪. ব্যবসায়িক পক্ষ ও ডেভেলপারদের প্রতিদিন একসঙ্গে কাজ করা।
    ৫. অনুপ্রাণিত ব্যক্তিদের ঘিরে প্রকল্প গড়া, তাদের প্রয়োজনীয় পরিবেশ ও সহায়তা দেওয়া এবং তাদের ওপর আস্থা রাখা।
    ৬. তথ্য আদান-প্রদানের সবচেয়ে কার্যকর উপায় মুখোমুখি আলোচনা।
    ৭. অগ্রগতির প্রধান পরিমাপক হলো কার্যকর সফটওয়্যার।
    ৮. টেকসই গতিতে উন্নয়ন; দল যেন অনির্দিষ্টকাল একই গতি বজায় রাখতে পারে।
    ৯. কারিগরি উৎকর্ষ ও উত্তম নকশার প্রতি ধারাবাহিক মনোযোগ ক্ষিপ্রতা বাড়ায়।
    ১০. সরলতা, অর্থাৎ যে কাজ না করলেও চলে তা বাদ দেওয়ার শিল্প, অপরিহার্য।
    ১১. সর্বোত্তম স্থাপত্য, প্রয়োজনীয়তা ও নকশা স্ব-সংগঠিত দল থেকেই উদ্ভূত হয়।
    ১২. নিয়মিত বিরতিতে দল নিজের কার্যপদ্ধতি পর্যালোচনা করে এবং তা উন্নত করে।

    প্রধান কাঠামোসমূহ:
    - Scrum: ২ থেকে ৪ সপ্তাহের sprint, তিনটি ভূমিকা (Product Owner, Scrum Master, Development Team), তিনটি উপকরণ (Product Backlog, Sprint Backlog, Increment) এবং চারটি অনুষ্ঠান (Sprint Planning, Daily Stand-up, Sprint Review, Retrospective)।
    - Extreme Programming (XP): জোড়ায় প্রোগ্রামিং, টেস্ট-চালিত উন্নয়ন, ধারাবাহিক সংযোজন, রিফ্যাক্টরিং ও সরল নকশা।
    - Kanban: দৃশ্যমান বোর্ড, চলমান কাজের সীমা এবং নির্দিষ্ট চক্রের বদলে ধারাবাহিক প্রবাহ।

    সুবিধা: দ্রুত সরবরাহ, পরিবর্তন গ্রহণের ক্ষমতা, আগেভাগে ত্রুটি শনাক্তকরণ, কম ঝুঁকি এবং গ্রাহকের ধারাবাহিক সম্পৃক্ততা।

    সীমাবদ্ধতা: নথিপত্র কম হওয়ায় দীর্ঘমেয়াদি রক্ষণাবেক্ষণ কঠিন, মোট খরচ ও সময় আগে থেকে নির্ধারণ করা যায় না, গ্রাহকের ধারাবাহিক উপস্থিতি প্রয়োজন, এবং অভিজ্ঞ ও সুশৃঙ্খল দল না হলে এটি অপরিকল্পিত কোডিংয়ে পরিণত হয়।
25. **(খ) Software development এর Waterfall model এর অসুবিধাগুলো কী কী?** *[Software Assistant Programmer 13.10.2022 compact it 706 (ET: N/A)]*


    Answer: Waterfall model এর অসুবিধাসমূহ:

    - শেষ পর্যন্ত কোনো কার্যকর সফটওয়্যার পাওয়া যায় না: গ্রাহক পুরো প্রকল্প শেষ না হওয়া পর্যন্ত কিছুই দেখতে পান না। এক বছরের প্রকল্পে প্রথম ব্যবহারযোগ্য ফল আসে এগারো মাস পরে, তখন মৌলিক ভুল সংশোধনের সুযোগ আর থাকে না।

    - প্রয়োজনীয়তার পরিবর্তন গ্রহণ করা যায় না: একবার SRS চূড়ান্ত হয়ে গেলে পরিবর্তন করতে হলে আগের ধাপে ফিরে গিয়ে নথি, নকশা, কোড ও পরীক্ষা সবই বদলাতে হয়, যা অত্যন্ত ব্যয়বহুল। অথচ বাস্তবে প্রয়োজনীয়তা সবসময়ই বদলায়।

    - শুরুতেই সব প্রয়োজনীয়তা সঠিকভাবে জানা যায় বলে ধরে নেওয়া হয়, যা প্রায় কখনোই সত্য নয়। ব্যবহারকারী কিছু দেখার আগে নিজের চাহিদা স্পষ্ট করে বলতে পারেন না।

    - ত্রুটি অনেক দেরিতে ধরা পড়ে: প্রয়োজনীয়তা বা নকশা পর্যায়ে ঢোকা একটি ভুল কেবল টেস্টিং পর্যায়ে ধরা পড়ে, যখন তা সারাতে ১০ থেকে ১০০ গুণ বেশি খরচ হয়।

    - ঝুঁকি শেষে কেন্দ্রীভূত: সংযোজন ব্যর্থ হলে বা গ্রহণযোগ্যতা পরীক্ষায় ব্যবস্থাটি অকেজো প্রমাণিত হলে পুরো বিনিয়োগ নষ্ট হয়; আংশিক ফলও হাতে থাকে না।

    - টেস্টিং একটি মাত্র পর্যায়ে সীমাবদ্ধ, এবং প্রকল্প দেরি হলে সেই পর্যায়টিই সবচেয়ে আগে কাটছাঁট করা হয়, ফলে চাপের সময়েই গুণমান নষ্ট হয়।

    - প্রয়োজনীয়তা সংগ্রহ ও সরবরাহের মাঝখানে গ্রাহকের কোনো সম্পৃক্ততা নেই, তাই নির্দিষ্ট করা ব্যবস্থা ও প্রকৃত প্রয়োজনের মধ্যে ব্যবধান বাড়তেই থাকে।

    - অগ্রগতি মাপা হয় তৈরি হওয়া নথির সংখ্যা দিয়ে, কার্যকর সফটওয়্যার দিয়ে নয়। ফলে প্রকল্প মাসের পর মাস "৯০ শতাংশ সম্পন্ন" দেখানো সম্ভব হয়।

    - বৃহৎ, দীর্ঘমেয়াদি বা অনিশ্চিত প্রকল্পের জন্য অনুপযুক্ত, এবং নতুন বা অপরীক্ষিত প্রযুক্তির ক্ষেত্রেও ব্যবহারযোগ্য নয়।

    - সমান্তরাল কাজের সুযোগ নেই; এক পর্যায়ের কাজ শেষ না হলে পরের দল বসে থাকে, ফলে জনবল অপচয় হয়।

    তবু কেন এটি এখনো ব্যবহৃত হয়: প্রয়োজনীয়তা স্থির ও সম্পূর্ণ জানা থাকলে, নথিপত্র নিজেই একটি সরবরাহযোগ্য পণ্য হলে (যেমন সনদপ্রাপ্তির প্রয়োজনে), এবং চুক্তিতে পরিধি, মূল্য ও তারিখ আগেই নির্দিষ্ট থাকলে (যেমন সরকারি দরপত্রে) এই মডেলই সবচেয়ে উপযোগী।

    সমাধান হিসেবে যা ব্যবহৃত হয়: Iterative ও Incremental মডেল, Spiral মডেল (ঝুঁকি বিশ্লেষণসহ), এবং Agile পদ্ধতি, যেখানে ২ থেকে ৪ সপ্তাহের চক্রে কার্যকর সফটওয়্যার সরবরাহ করা হয় এবং প্রতিটি চক্রে গ্রাহকের মতামত নেওয়া হয়।
26. **(খ) System/Model Prototype বলতে কী বুঝায়? Product ও Process এর মধ্যে সম্পর্ক কী?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*


    Answer:

    System/Model Prototype বলতে কী বোঝায়:

    Prototype হলো প্রস্তাবিত ব্যবস্থার একটি প্রাথমিক, অসম্পূর্ণ কিন্তু কার্যকর মডেল, যা তৈরি করা হয় ব্যবহারকারীকে দেখিয়ে প্রয়োজনীয়তা স্পষ্ট করার জন্য এবং মতামত সংগ্রহের জন্য। এটি চূড়ান্ত পণ্য নয়, বরং চূড়ান্ত পণ্য কেমন হবে তার একটি নমুনা।

    কেন প্রয়োজন: ব্যবহারকারীরা প্রায়ই নিজের চাহিদা কথায় প্রকাশ করতে পারেন না, কিন্তু কিছু দেখলে সঙ্গে সঙ্গে বলতে পারেন এটি ঠিক আছে কি নেই। প্রোটোটাইপ সেই দেখার সুযোগটি তৈরি করে দেয়, তাও উন্নয়নের অনেক আগে, যখন পরিবর্তন সস্তা।

    প্রোটোটাইপের প্রকারভেদ:
    - Throwaway বা Rapid prototype: দ্রুত তৈরি করে প্রয়োজনীয়তা স্পষ্ট হলে ফেলে দেওয়া হয়; চূড়ান্ত ব্যবস্থা আলাদাভাবে তৈরি হয়।
    - Evolutionary prototype: প্রাথমিক প্রোটোটাইপকেই ধাপে ধাপে উন্নত করে চূড়ান্ত ব্যবস্থায় পরিণত করা হয়।
    - Incremental prototype: ব্যবস্থাটিকে অংশে ভাগ করে প্রতিটি অংশের আলাদা প্রোটোটাইপ তৈরি করে শেষে একত্র করা হয়।
    - Extreme prototype: ওয়েব অ্যাপ্লিকেশনের জন্য; প্রথমে স্থির HTML পাতা, তারপর কৃত্রিম সেবাস্তর, শেষে প্রকৃত সেবা।
    - Horizontal prototype: পুরো ব্যবস্থার ইন্টারফেস দেখায় কিন্তু গভীরতা নেই।
    - Vertical prototype: একটি নির্দিষ্ট কাজ সম্পূর্ণভাবে বাস্তবায়ন করে।

    প্রোটোটাইপিং মডেলের ধাপ:
    ১. প্রাথমিক প্রয়োজনীয়তা সংগ্রহ
    ২. দ্রুত নকশা প্রণয়ন
    ৩. প্রোটোটাইপ তৈরি
    ৪. ব্যবহারকারীর মূল্যায়ন
    ৫. প্রোটোটাইপ পরিমার্জন
    ৬. সন্তোষজনক হলে চূড়ান্ত ব্যবস্থা নির্মাণ ও রক্ষণাবেক্ষণ
    ধাপ ৩ থেকে ৫ ততক্ষণ পুনরাবৃত্ত হয়, যতক্ষণ না ব্যবহারকারী সন্তুষ্ট হন।

    সুবিধা: প্রয়োজনীয়তার ভুল আগেভাগে ধরা পড়ে, ব্যবহারকারীর সম্পৃক্ততা বাড়ে, ব্যবহারযোগ্যতা যাচাই করা যায় এবং ঝুঁকি কমে।

    অসুবিধা: ব্যবহারকারী প্রোটোটাইপকেই প্রায় প্রস্তুত পণ্য ভেবে ভুল করেন; দ্রুত তৈরি করতে গিয়ে নেওয়া শর্টকাট চূড়ান্ত পণ্যে থেকে যেতে পারে; এবং বারবার পরিবর্তনের চাহিদায় প্রকল্পের পরিধি বেড়ে যেতে পারে।

    Product ও Process এর মধ্যে সম্পর্ক:

    - Product (পণ্য): যা তৈরি করা হয় — অর্থাৎ সফটওয়্যার নিজে, তার সোর্স কোড, নথিপত্র, ডেটাবেজ, ব্যবহারকারী নির্দেশিকা ও প্রশিক্ষণ উপকরণ। এটি প্রকল্পের ফলাফল ও সরবরাহযোগ্য বস্তু।

    - Process (প্রক্রিয়া): কীভাবে তৈরি করা হয় — অর্থাৎ যে ধাপ, কার্যক্রম, পদ্ধতি ও নিয়ম মেনে পণ্যটি তৈরি হয়। SDLC, Waterfall, Agile, Scrum — এগুলো সবই প্রক্রিয়া।

    সম্পর্ক:
    - প্রক্রিয়া হলো কাঠামো, পণ্য হলো ফল। ভালো প্রক্রিয়া ভালো পণ্য তৈরির সম্ভাবনা বাড়ায়, তবে নিশ্চয়তা দেয় না।
    - পণ্যের গুণমান প্রক্রিয়ার গুণমানের ওপর নির্ভরশীল। এই ধারণা থেকেই CMMI (Capability Maturity Model Integration) ও ISO 9001 এর মতো প্রক্রিয়া উন্নয়ন কাঠামো তৈরি হয়েছে, যেগুলোর মূল যুক্তি: প্রক্রিয়া উন্নত করলে পণ্য আপনিই উন্নত হবে।
    - পণ্য থেকে প্রাপ্ত তথ্য প্রক্রিয়াকে উন্নত করে। কোন পর্যায়ে কত ত্রুটি পাওয়া গেল, তা মেপে প্রক্রিয়ার দুর্বল ধাপ চিহ্নিত করা যায় এবং পরের প্রকল্পে তা সংশোধন করা যায়। এটি একটি প্রতিক্রিয়া চক্র (feedback loop)।
    - প্রক্রিয়া পণ্যের ধরন অনুযায়ী বদলাতে হয়। একটি পেসমেকারের সফটওয়্যারে কঠোর নথিভিত্তিক প্রক্রিয়া দরকার, আর একটি মোবাইল গেমে Agile উপযুক্ত। একই প্রক্রিয়া সব পণ্যের জন্য নয়।
    - প্রক্রিয়া দৃশ্যমান নয়, পণ্য দৃশ্যমান। গ্রাহক পণ্য দেখেন, প্রক্রিয়া দেখেন না; কিন্তু পণ্যের নির্ভরযোগ্যতা ও রক্ষণাবেক্ষণযোগ্যতা প্রক্রিয়াই নির্ধারণ করে।

    সংক্ষেপে: প্রক্রিয়া হলো রন্ধনপ্রণালী, পণ্য হলো রান্না করা খাবার। ভালো প্রণালী ভালো খাবারের সম্ভাবনা বাড়ায়, কিন্তু উপকরণ ও রাঁধুনির দক্ষতাও লাগে। আর খাবারের স্বাদ থেকেই বোঝা যায় প্রণালীটি কোথায় শোধরাতে হবে।
27. **What is full meaning of SDLC?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


    Answer: The full meaning of SDLC is Software Development Life Cycle.

    It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases, in order:
    1. Planning and feasibility study
    2. Requirement analysis and specification
    3. Design
    4. Implementation (coding)
    5. Testing
    6. Deployment
    7. Maintenance

    Models that arrange these phases differently: Waterfall (strictly sequential), Iterative, Incremental, Prototyping, Spiral (risk-driven), V-model (testing paired with each development phase), RAD, and Agile methods such as Scrum, XP and Kanban.

    Related abbreviations often asked alongside it:
    - SRS: Software Requirements Specification
    - HLD and LLD: High-Level Design and Low-Level Design
    - UAT: User Acceptance Testing
    - CI/CD: Continuous Integration and Continuous Deployment or Delivery
    - STLC: Software Testing Life Cycle
    - PDLC: Product Development Life Cycle
28. **Difference between Waterfall Model and Spiral Model.** *[BDCCL Assistant Engineer (Network) 2022 compact it 741 (ET: N/A)]*


    Answer:

    | Point | Waterfall Model | Spiral Model |
    |---|---|---|
    | Approach | Linear and sequential; each phase once, in order | Iterative and evolutionary; the same phases repeat in successive spirals |
    | Risk analysis | None; risk is not addressed explicitly | Formal risk analysis in every cycle, which is its defining feature |
    | Phases per cycle | Six phases in total, executed once | Four quadrants per cycle: determine objectives, identify and resolve risks, develop and verify, plan the next cycle |
    | Customer involvement | At the beginning and at final acceptance | At the end of every cycle |
    | Prototyping | Not used | Central; prototypes are built to reduce risk |
    | Handling of change | Very difficult and expensive | Accommodated in the next cycle |
    | Cost | Lower, and estimable in advance | Higher; the risk analysis in every cycle is itself expensive |
    | Duration | Fixed and predictable | Not known in advance, since the number of cycles is not fixed |
    | Complexity of management | Simple | Complex; needs experienced risk analysts |
    | Documentation | Extensive, produced phase by phase | Extensive, produced cycle by cycle |
    | Early cancellation | Not possible without total loss | Possible at the end of any cycle, before further money is spent |
    | Suitable for | Small to medium projects with stable, well-understood requirements | Large, expensive, high-risk projects with unclear or changing requirements |
    | Unsuitable for | Long, complex or uncertain projects | Small or low-risk projects, where the overhead is not justified |
    | Examples of use | A system implementing a fixed published regulation | Defence, aerospace and large government systems |
    | Proposed by | Winston Royce, 1970 | Barry Boehm, 1988 |

    The four quadrants of one spiral cycle:
    1. Determine objectives, alternatives and constraints for this cycle.
    2. Identify and resolve risks, building prototypes or running simulations to reduce the biggest ones. This is the quadrant that distinguishes the model.
    3. Develop and verify the deliverable of this cycle, following a Waterfall-like sequence for that part only.
    4. Plan the next cycle, obtain customer evaluation, and decide whether to continue at all.

    The essential difference in one sentence: Waterfall assumes that the risks are known and the requirements are fixed, so it goes straight through; the Spiral model assumes that neither is true, so it repeatedly asks what could go wrong, builds something to find out, and only then commits further money.

    Relationship with the other models: the Spiral model can be seen as Waterfall repeated in cycles, with prototyping and risk analysis added. Agile is also iterative, but its cycles are far shorter, two to four weeks against months, and it substitutes continuous customer collaboration and delivery for the Spiral model's formal risk analysis.
29. **What is the principles of agile method?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 757 (ET: N/A)]*


    Answer: Agile is an iterative and incremental approach to software development in which requirements and solutions evolve through collaboration between self-organising cross-functional teams and the customer. Work is delivered in short cycles called iterations or sprints, typically of one to four weeks, and each cycle produces a potentially shippable increment of working software.

    The four values of the Agile Manifesto, published in 2001 by seventeen practitioners:

    - Individuals and interactions over processes and tools
    - Working software over comprehensive documentation
    - Customer collaboration over contract negotiation
    - Responding to change over following a plan

    The manifesto adds the crucial qualification: while there is value in the items on the right, the items on the left are valued more. Agile does not reject documentation or planning; it subordinates them to working software and to responsiveness.

    The twelve principles behind the manifesto, in summary:
    1. Satisfy the customer through early and continuous delivery of valuable software.
    2. Welcome changing requirements, even late in development.
    3. Deliver working software frequently, from a couple of weeks to a couple of months.
    4. Business people and developers must work together daily.
    5. Build projects around motivated individuals, give them the environment and support they need, and trust them.
    6. Face-to-face conversation is the most efficient method of conveying information.
    7. Working software is the primary measure of progress.
    8. Promote sustainable development, at a pace that can be maintained indefinitely.
    9. Continuous attention to technical excellence and good design enhances agility.
    10. Simplicity, the art of maximising the work not done, is essential.
    11. The best architectures, requirements and designs emerge from self-organising teams.
    12. At regular intervals the team reflects on how to become more effective and adjusts accordingly.

    Popular Agile frameworks:
    - Scrum: sprints of two to four weeks, roles of Product Owner, Scrum Master and Development Team, artefacts of product backlog, sprint backlog and increment, and ceremonies of sprint planning, daily stand-up, sprint review and retrospective.
    - Extreme Programming (XP): pair programming, test-driven development, continuous integration, refactoring, simple design and frequent small releases.
    - Kanban: a visual board, limits on work in progress, and continuous flow rather than fixed iterations.
    - Lean software development, Crystal, and the Feature Driven Development method.

    Advantages: rapid delivery of usable software; the customer sees progress every few weeks; changing requirements are welcomed rather than resisted; defects are found early through continuous testing; risk is reduced because problems surface in the first iterations; and team morale and communication improve.

    Disadvantages: less documentation, which can make long-term maintenance and hand-over harder; the total cost and schedule are difficult to fix in advance, which makes it awkward for fixed-price government contracts; it requires continuous customer availability, which is often not forthcoming; it depends on experienced and disciplined developers; it scales less easily to very large teams without additional frameworks such as SAFe; and without discipline it can degenerate into unplanned coding.
30. **From the diagram write down the process of prototype development.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 758 (ET: N/A)]*


    Answer: The process of prototype development, as shown in the standard prototyping model diagram:

    Steps:

    1. Requirements gathering and analysis (preliminary):
    - The developer and the customer meet and identify the broad objectives of the system and the areas where the requirements are unclear.
    - Only an outline is sought at this stage, not a complete specification, because the whole purpose of the prototype is to clarify what is not yet known.

    2. Quick design:
    - A rapid design is prepared, concentrating on the parts the user will actually see: the input screens, the output formats and the navigation.
    - Internal details, performance, security and error handling are deliberately deferred.

    3. Build the prototype:
    - The quick design is turned into a working, though incomplete, prototype, usually with rapid development tools.
    - It may simulate functionality rather than implement it, for example by returning fixed data instead of querying a database.

    4. Customer evaluation:
    - The prototype is given to the users, who try it against their real tasks.
    - Their comments identify what is missing, what is wrong, and what they had not thought to ask for.
    - This step is the whole point of the exercise: it converts vague requirements into concrete ones.

    5. Refine the prototype:
    - The feedback is incorporated, and the prototype is modified.
    - Steps 3, 4 and 5 form a loop, repeated until the users are satisfied that the prototype represents what they want.

    6. Engineer the final product:
    - Once the requirements are stable, the actual system is built to proper engineering standards, with full attention to architecture, performance, security and maintainability.
    - Depending on the type of prototyping, the prototype is either discarded (throwaway) or evolved into the final product (evolutionary).

    7. Deploy and maintain:
    - The finished system is installed, the users are trained, and it enters maintenance.

    Diagram:

    ```mermaid
    flowchart LR
      A[1 Requirements gathering] --> B[2 Quick design]
      B --> C[3 Build prototype]
      C --> D[4 Customer evaluation]
      D --> E{Satisfied?}
      E -- No --> F[5 Refine prototype]
      F --> C
      E -- Yes --> G[6 Engineer the final product]
      G --> H[7 Deploy and maintain]
    ```

    Types of prototyping:
    - Throwaway or rapid prototyping: the prototype is discarded once the requirements are clear, and the real system is built afresh.
    - Evolutionary prototyping: the prototype itself is refined step by step until it becomes the delivered system.
    - Incremental prototyping: separate prototypes are built for separate parts and finally merged.
    - Extreme prototyping, used for web applications: first static pages, then a simulated services layer, then the real services.

    Advantages: requirement errors are found very early, when they are cheapest to correct; users are actively involved and therefore accept the result; usability can be tested before the code is written; and the risk of building the wrong system is greatly reduced.

    Disadvantages: users may mistake the prototype for a nearly finished product and expect delivery immediately; the shortcuts taken to build it quickly may survive into the final system if it is evolved rather than discarded; repeated changes can cause scope creep and make the schedule unpredictable; and the effort spent on a throwaway prototype is, by definition, thrown away.

    When to use it: when the requirements are unclear or unstable, when the user interface is critical to acceptance, when the users cannot describe what they want in words, and when a new or unfamiliar technology must be evaluated.
31. **From the diagram write down the software evolution.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 760 (ET: N/A)]*


    Answer: Software evolution is the process by which a software system changes over time after it has first been delivered, in response to corrections, changes in its environment and new requirements. The standard diagram shows it as a continuous feedback loop rather than a straight line, because delivery is not the end of the life of the software but the beginning of its longest phase.

    The process of software evolution:

    1. Change requests arrive:
    - From users reporting defects
    - From users requesting new features
    - From changes in the operating environment: a new operating system, a new database version, new hardware
    - From changes in law or business rules
    - From the development team, wishing to improve internal quality

    2. Impact analysis:
    - Determine which modules, data structures, interfaces and documents the proposed change would affect.
    - Estimate the effort, the cost and the risk of the change.
    - Identify the regression tests that will be needed.

    3. Release planning:
    - Decide which of the requested changes will go into the next release, based on value, urgency and cost.
    - Group them into a release, and fix a date.

    4. System implementation:
    - Carry out the changes: modify the design, the code, the database and the documentation.
    - Write or update the unit tests.

    5. Verification and validation:
    - Test the changes themselves.
    - Run regression tests to confirm that nothing that previously worked has been broken. This is the most important and most often neglected step.

    6. System release:
    - Deploy the new version, update the user documentation, and inform and if necessary retrain the users.

    7. Back to step 1:
    - The new version generates new requests, and the cycle repeats for as long as the system is in use.

    Diagram:

    ```mermaid
    flowchart LR
      CR[Change requests] --> IA[Impact analysis]
      IA --> RP[Release planning]
      RP --> SI[System implementation]
      SI --> VV[Verification and regression testing]
      VV --> SR[System release]
      SR --> CR
    ```

    The stages of a system's life, which the evolution diagram also shows:
    - Development: the system is built for the first time.
    - Evolution: changes are made continuously and the system remains valuable. Most of the money is spent here.
    - Servicing: only essential corrections are made; no new features are added, because the system has become too costly to change.
    - Phase-out: the system is still in use but is no longer maintained, while a replacement is prepared.
    - Retirement: the system is withdrawn and its data is migrated.

    Types of change, following Lientz and Swanson:
    - Corrective, about 20 per cent: fixing defects.
    - Adaptive, about 25 per cent: keeping up with the environment.
    - Perfective, about 50 per cent: new features and better performance. This is the largest category, which surprises many people.
    - Preventive, about 5 per cent: refactoring and improving maintainability.

    Lehman's laws of software evolution, which explain why the loop cannot be escaped:
    - Continuing change: a program used in a real environment must continually change, or it becomes progressively less satisfactory.
    - Increasing complexity: as a program evolves its complexity increases, unless work is done explicitly to reduce it.
    - Conservation of familiarity: the rate of change must be limited to what the team can absorb and understand.
    - Declining quality: quality appears to decline unless the system is rigorously adapted to changes in its environment.

    Practical implications: because 60 to 70 per cent of the lifetime cost of software is spent after the first delivery, decisions made during development should be judged by how easy they make the evolution that follows. Clean modular design, low coupling, automated regression tests, version control and up-to-date documentation are not luxuries; they are what makes evolution affordable.
32. **(খ) SDLC diagram সহ বর্ণনা করুন। SDLC এর মেজর phases গুলি কী?** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 779 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
33. **(ii) Software development এর Agile Method সম্পর্কে আলোচনা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*


    Answer: Agile Method হলো সফটওয়্যার উন্নয়নের একটি পুনরাবৃত্ত ও ক্রমবর্ধমান (iterative and incremental) পদ্ধতি, যেখানে প্রয়োজনীয়তা ও সমাধান স্ব-সংগঠিত, বহুবিভাগীয় দল ও গ্রাহকের যৌথ প্রচেষ্টায় ধাপে ধাপে বিকশিত হয়। কাজ সম্পন্ন হয় ছোট ছোট চক্রে, যাকে বলা হয় iteration বা sprint, সাধারণত ১ থেকে ৪ সপ্তাহের, এবং প্রতিটি চক্রের শেষে একটি কার্যকর ও সরবরাহযোগ্য সফটওয়্যার তৈরি হয়।

    প্রেক্ষাপট: ঐতিহ্যবাহী Waterfall পদ্ধতিতে বিশাল নথিপত্র তৈরি হতো, গ্রাহক বছরের পর বছর কিছুই দেখতেন না এবং প্রয়োজনীয়তা বদলালে বিপুল খরচ হতো। এর প্রতিক্রিয়ায় ২০০১ সালে সতেরোজন অভিজ্ঞ প্রকৌশলী Agile Manifesto প্রকাশ করেন।

    চারটি মূল্যবোধ:
    - প্রক্রিয়া ও যন্ত্রের চেয়ে ব্যক্তি ও পারস্পরিক যোগাযোগ
    - বিস্তারিত নথিপত্রের চেয়ে কার্যকর সফটওয়্যার
    - চুক্তির দর কষাকষির চেয়ে গ্রাহকের সঙ্গে সহযোগিতা
    - পরিকল্পনা অনুসরণের চেয়ে পরিবর্তনে সাড়া দেওয়া

    Scrum কাঠামো, যা সবচেয়ে বেশি ব্যবহৃত:
    - ভূমিকা: Product Owner (কী তৈরি হবে ও কোন ক্রমে, তা নির্ধারণ করেন), Scrum Master (প্রক্রিয়া রক্ষা করেন ও বাধা দূর করেন), Development Team (৫ থেকে ৯ জনের স্ব-সংগঠিত দল)।
    - উপকরণ: Product Backlog (অগ্রাধিকার অনুযায়ী সাজানো সব কাজের তালিকা), Sprint Backlog (এই চক্রে যা করা হবে), Increment (চক্রের ফলাফল)।
    - অনুষ্ঠান: Sprint Planning (কী করা হবে ঠিক করা), Daily Stand-up (১৫ মিনিটের দৈনিক সভা: গতকাল কী করেছি, আজ কী করব, কী বাধা আছে), Sprint Review (গ্রাহককে ফলাফল দেখানো), Sprint Retrospective (দল নিজের কার্যপদ্ধতি উন্নত করা)।

    অন্যান্য কাঠামো:
    - Extreme Programming (XP): জোড়ায় প্রোগ্রামিং, টেস্ট-চালিত উন্নয়ন (TDD), ধারাবাহিক সংযোজন, রিফ্যাক্টরিং, সরল নকশা ও ঘন ঘন ছোট রিলিজ।
    - Kanban: দৃশ্যমান বোর্ডে কাজের প্রবাহ দেখানো, একসঙ্গে চলমান কাজের সংখ্যায় সীমা আরোপ, এবং নির্দিষ্ট দৈর্ঘ্যের চক্রের বদলে ধারাবাহিক প্রবাহ।
    - Lean, Crystal ও Feature Driven Development।

    কার্যপ্রবাহ:

    ```mermaid
    flowchart LR
      PB[Product Backlog] --> SP[Sprint Planning]
      SP --> SB[Sprint Backlog]
      SB --> DEV[Sprint: Design, Code, Test]
      DEV --> DS[Daily Stand-up]
      DS --> DEV
      DEV --> INC[Working Increment]
      INC --> SR[Sprint Review with customer]
      SR --> RT[Retrospective]
      RT --> PB
    ```

    সুবিধা:
    - প্রতি কয়েক সপ্তাহেই ব্যবহারযোগ্য সফটওয়্যার পাওয়া যায়, তাই বিনিয়োগের প্রতিদান দ্রুত শুরু হয়।
    - প্রয়োজনীয়তার পরিবর্তন স্বাগত জানানো হয়, প্রতিরোধ করা হয় না।
    - প্রতিটি চক্রেই পরীক্ষা হয় বলে ত্রুটি কয়েক দিনের মধ্যেই ধরা পড়ে, যখন তা সারানো সস্তা।
    - ঝুঁকি ছড়িয়ে যায়; কঠিন সমস্যাগুলো প্রথম চক্রগুলোতেই সামনে আসে।
    - গ্রাহক ধারাবাহিকভাবে যুক্ত থাকেন, তাই যা তৈরি হয় তা-ই প্রকৃতপক্ষে দরকার ছিল।
    - দলের মনোবল ও যোগাযোগ উন্নত হয়।

    সীমাবদ্ধতা:
    - নথিপত্র কম হওয়ায় দীর্ঘমেয়াদি রক্ষণাবেক্ষণ ও নিরীক্ষা কঠিন হয়।
    - মোট খরচ ও সরবরাহের তারিখ আগে থেকে নির্দিষ্ট করা যায় না, তাই স্থির মূল্যের সরকারি দরপত্রে প্রয়োগ কঠিন।
    - গ্রাহকের ধারাবাহিক উপস্থিতি অপরিহার্য, যা বাস্তবে প্রায়ই পাওয়া যায় না।
    - অভিজ্ঞ ও সুশৃঙ্খল দল প্রয়োজন; নইলে এটি অপরিকল্পিত কোডিংয়ে পরিণত হয়।
    - অতি বৃহৎ দলে সরাসরি প্রয়োগ কঠিন; সে ক্ষেত্রে SAFe বা LeSS এর মতো কাঠামো লাগে।

    কখন ব্যবহার উপযুক্ত: প্রয়োজনীয়তা অনিশ্চিত বা পরিবর্তনশীল হলে, গ্রাহক নিয়মিত সময় দিতে পারলে, দ্রুত বাজারে আনা জরুরি হলে এবং নতুন পণ্য তৈরি করলে।
34. **(a) What is Agile? Mentionits four values.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*


    Answer: Agile is an iterative and incremental approach to software development in which requirements and solutions evolve through collaboration between self-organising cross-functional teams and the customer. Work is delivered in short cycles called iterations or sprints, typically of one to four weeks, and each cycle produces a potentially shippable increment of working software.

    The four values of the Agile Manifesto, published in 2001 by seventeen practitioners:

    - Individuals and interactions over processes and tools
    - Working software over comprehensive documentation
    - Customer collaboration over contract negotiation
    - Responding to change over following a plan

    The manifesto adds the crucial qualification: while there is value in the items on the right, the items on the left are valued more. Agile does not reject documentation or planning; it subordinates them to working software and to responsiveness.

    The twelve principles behind the manifesto, in summary:
    1. Satisfy the customer through early and continuous delivery of valuable software.
    2. Welcome changing requirements, even late in development.
    3. Deliver working software frequently, from a couple of weeks to a couple of months.
    4. Business people and developers must work together daily.
    5. Build projects around motivated individuals, give them the environment and support they need, and trust them.
    6. Face-to-face conversation is the most efficient method of conveying information.
    7. Working software is the primary measure of progress.
    8. Promote sustainable development, at a pace that can be maintained indefinitely.
    9. Continuous attention to technical excellence and good design enhances agility.
    10. Simplicity, the art of maximising the work not done, is essential.
    11. The best architectures, requirements and designs emerge from self-organising teams.
    12. At regular intervals the team reflects on how to become more effective and adjusts accordingly.

    Popular Agile frameworks:
    - Scrum: sprints of two to four weeks, roles of Product Owner, Scrum Master and Development Team, artefacts of product backlog, sprint backlog and increment, and ceremonies of sprint planning, daily stand-up, sprint review and retrospective.
    - Extreme Programming (XP): pair programming, test-driven development, continuous integration, refactoring, simple design and frequent small releases.
    - Kanban: a visual board, limits on work in progress, and continuous flow rather than fixed iterations.
    - Lean software development, Crystal, and the Feature Driven Development method.

    Advantages: rapid delivery of usable software; the customer sees progress every few weeks; changing requirements are welcomed rather than resisted; defects are found early through continuous testing; risk is reduced because problems surface in the first iterations; and team morale and communication improve.

    Disadvantages: less documentation, which can make long-term maintenance and hand-over harder; the total cost and schedule are difficult to fix in advance, which makes it awkward for fixed-price government contracts; it requires continuous customer availability, which is often not forthcoming; it depends on experienced and disciplined developers; it scales less easily to very large teams without additional frameworks such as SAFe; and without discipline it can degenerate into unplanned coding.
35. **What is SDLC? List the stages involed in the SDLC process. Which stages ensures the user acceptance of the system?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
36. **(ii) Software development এর ধাপসমূহ সংক্ষেপে বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 960 (ET: N/A)]*


    Answer: SDLC stands for Software Development Life Cycle. It is the structured sequence of phases through which a software product passes, from the first idea to its final retirement. Its purpose is to produce software of predictable quality, within budget and on schedule, by making every stage explicit, reviewable and documented.

    The phases:

    1. Planning and feasibility study:
    - Define the problem, the scope and the objectives.
    - Estimate cost, time and resources.
    - Assess feasibility in four dimensions: technical (can it be built with available technology), economic (is the benefit worth the cost, using cost-benefit analysis and return on investment), operational (will the users actually use it) and legal or schedule feasibility.
    - Output: the project plan and the feasibility report.

    2. Requirement analysis and specification:
    - Gather what the system must do, by interviews, questionnaires, observation, study of existing documents and workshops with users.
    - Distinguish functional requirements (what the system does) from non-functional ones (performance, security, usability, reliability).
    - Resolve conflicts and ambiguities, and check that every requirement is complete, consistent, unambiguous, verifiable and traceable.
    - Output: the Software Requirements Specification (SRS), which is the contract between the customer and the developer.

    3. Design:
    - High-level (architectural) design: the overall structure, the modules and their relationships, the technology stack, the database schema and the interfaces between components.
    - Low-level (detailed) design: the internal logic of each module, the algorithms, the data structures, the input and output formats and the user interface.
    - Tools: data flow diagrams, entity relationship diagrams and UML class, sequence and component diagrams.
    - Output: the design document, sometimes divided into HLD and LLD.

    4. Implementation (coding):
    - The design is translated into source code in the chosen language, following coding standards.
    - Version control, code review and unit testing by the developer belong to this phase.
    - Output: the working source code and the developer documentation.

    5. Testing:
    - Verify that the software meets the specification and find defects before release.
    - Levels: unit testing, integration testing, system testing and acceptance testing.
    - Types: functional, performance, security, usability and regression testing.
    - Output: test plans, test cases, defect reports and the test summary.

    6. Deployment:
    - Install the system in the live environment, migrate the data, train the users and go live.
    - Strategies: direct changeover, parallel running, pilot and phased introduction.
    - Output: the running system and the user manual.

    7. Maintenance:
    - Correct faults found in use, adapt the system to changes in the environment, add enhancements requested by users, and improve internal quality.
    - This is the longest and most expensive phase, typically 60 to 70 per cent of the total cost over the life of the system.
    - Output: updated versions and revised documentation.

    Diagram:

    ```mermaid
    flowchart LR
      A[Planning and Feasibility] --> B[Requirement Analysis]
      B --> C[Design]
      C --> D[Implementation]
      D --> E[Testing]
      E --> F[Deployment]
      F --> G[Maintenance]
      G -.feedback.-> B
    ```

    The phase that assures user acceptance: the acceptance testing stage, also called User Acceptance Testing (UAT), which is part of the testing phase and immediately precedes deployment. Here the customer's own users run the system against real business scenarios and formally accept or reject it. It answers the question "are we building the right system", whereas earlier testing answers "are we building the system right".
37. **What is Agile Methodology? Difference between Agile Model and Waterfall Model.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1003-1004 (ET: DU)]*


    Answer: Agile Methodology is an iterative and incremental approach to software development in which requirements and solutions evolve through collaboration between self-organising cross-functional teams and the customer. Work proceeds in short cycles called iterations or sprints, typically of one to four weeks, and each cycle produces a potentially shippable increment of working software.

    Its four values, from the Agile Manifesto of 2001:
    - Individuals and interactions over processes and tools
    - Working software over comprehensive documentation
    - Customer collaboration over contract negotiation
    - Responding to change over following a plan

    Its main frameworks are Scrum, Extreme Programming and Kanban.

    Difference between the Agile model and the Waterfall model:

    | Point | Waterfall Model | Agile Model |
    |---|---|---|
    | Approach | Linear and sequential | Iterative and incremental |
    | Phases | Completed once, strictly in order | Repeated in every short iteration |
    | Delivery | One delivery at the end | Working software every one to four weeks |
    | Requirements | Fixed at the start; changes are costly | Expected to evolve; changes are welcomed |
    | Customer involvement | Mainly at the beginning and at acceptance | Continuous, throughout the project |
    | Documentation | Extensive and formal | Minimal but sufficient; working software is preferred |
    | Testing | A single phase, late in the project | Continuous, in every iteration |
    | Risk | Concentrated at the end; discovered late | Spread out; problems surface in the first iterations |
    | Flexibility | Low | High |
    | Team size and structure | Larger, with specialised roles and a hierarchy | Small, cross-functional and self-organising |
    | Progress measured by | Phase completion and documents signed off | Working software delivered |
    | Cost and schedule | Fixed and estimated in advance | Evolve; scope is the variable |
    | Suitable for | Stable, well-understood requirements; regulatory and safety-critical systems | Changing requirements; new products; systems where the users must see and react |
    | Not suitable for | Long, complex or exploratory projects | Fixed-price contracts; systems needing exhaustive certification documentation |
    | Failure mode | The wrong system is delivered, months late | Scope drifts and the end is never reached without discipline |

## Software Testing & Evaluation (33)

1. Explain the difference between Unit Testing and Integration Testing. [SO IT 25-07-2026]


   Answer: | Point | Unit Testing | Integration Testing |
   |---|---|---|
   | What is tested | A single smallest testable component: one function, method or class, in isolation | The interfaces and interaction between two or more units that have already been unit tested |
   | Purpose | To confirm that each unit does what it is supposed to do on its own | To confirm that units work correctly together and that data passes correctly across their interfaces |
   | Performed by | The developer who wrote the code | Developers or a dedicated integration testing team |
   | When | As each unit is written, before integration | After unit testing, before system testing |
   | Knowledge required | White box; the internal code is known | Usually grey box; the interfaces are known, the internals partly |
   | Isolation | Dependencies are replaced with stubs, mocks or drivers | Real components are used, progressively |
   | Scope | Very narrow | Wider, covering the connections |
   | Defects found | Logic errors, wrong calculations, unhandled edge cases inside a unit | Interface mismatches, wrong parameter order or type, incorrect data format, timing problems, missing error handling between modules |
   | Speed | Very fast; thousands of unit tests run in seconds | Slower, since real components and sometimes databases and networks are involved |
   | Tools | JUnit, NUnit, PyTest, Mockito | Postman, REST Assured, JUnit with Spring Boot Test, Selenium for end-to-end |
   | Ease of locating a fault | Easy; the fault is inside the unit under test | Harder; the fault lies somewhere in the interaction |

   Approaches to integration:
   - Big bang: all modules are combined at once and tested together. Simple but faults are very hard to locate.
   - Top-down: high-level modules are tested first, with stubs standing in for the lower ones that are not yet written. The main control logic is validated early.
   - Bottom-up: low-level modules are tested first, with drivers calling them. The utility layers are validated early, but the user-visible behaviour appears late.
   - Sandwich or hybrid: top-down and bottom-up are combined, meeting in the middle.
   - Incremental: modules are added one at a time and tested after each addition, which makes fault location easy.

   Stubs and drivers, which are often asked with this question:
   - A stub is a dummy module that stands in for a called module that is not yet ready. It is used in top-down integration.
   - A driver is a dummy module that calls the module under test. It is used in bottom-up integration.

   Illustration: suppose a function calculateTax() returns the tax and a function generateInvoice() uses it. Unit testing checks that calculateTax(50000) returns the correct figure, with generateInvoice replaced by nothing at all. Integration testing checks that generateInvoice actually calls calculateTax with the right argument, receives the value correctly, and formats it into the invoice. A unit can be perfectly correct and the integration still fail, for example if one side works in taka and the other in paisa.
2. **ফরম্যাটিভ মূল্যায়ন (Formative Evaluation) বলতে কী বুঝায়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer: ফরম্যাটিভ মূল্যায়ন (Formative Evaluation) বলতে বোঝায় এমন মূল্যায়ন, যা কোনো ব্যবস্থা, প্রকল্প বা শিক্ষণপ্রক্রিয়া চলাকালীন সময়ে করা হয়, যার উদ্দেশ্য চূড়ান্ত রায় দেওয়া নয়, বরং চলার পথেই দুর্বলতা চিহ্নিত করে তা সংশোধন করা এবং মান উন্নত করা।

   মূল বৈশিষ্ট্য:
   - এটি চলমান ও পুনরাবৃত্ত; একবার নয়, বারবার করা হয়।
   - উদ্দেশ্য উন্নয়ন (improvement), বিচার (judgement) নয়।
   - ফলাফল তাৎক্ষণিকভাবে কাজে লাগানো হয়, প্রতিবেদন আকারে জমা রাখার জন্য নয়।
   - এটি প্রক্রিয়াকেন্দ্রিক (process-oriented)।
   - সাধারণত অনানুষ্ঠানিক ও কম ঝুঁকিপূর্ণ।

   সফটওয়্যার ইঞ্জিনিয়ারিংয়ে প্রয়োগ:
   - উন্নয়ন চলাকালে প্রতিটি পর্যায়ে পর্যালোচনা (review), ওয়াকথ্রু ও ইনস্পেকশন।
   - প্রোটোটাইপ দেখিয়ে ব্যবহারকারীর মতামত নেওয়া।
   - প্রতিটি স্প্রিন্টের শেষে Sprint Review ও Retrospective।
   - ধারাবাহিক সংযোজনের (CI) প্রতিটি বিল্ডে স্বয়ংক্রিয় পরীক্ষা চালিয়ে তাৎক্ষণিক প্রতিক্রিয়া পাওয়া।
   - ব্যবহারযোগ্যতা পরীক্ষা (usability testing) নকশা চূড়ান্ত হওয়ার আগেই করা।

   শিক্ষাক্ষেত্রে প্রয়োগ: শ্রেণিকক্ষে ছোট কুইজ, বাড়ির কাজ, প্রশ্নোত্তর ও উপস্থাপনা — যেগুলোর নম্বর চূড়ান্ত ফলে যোগ হয় না, কিন্তু শিক্ষক বুঝতে পারেন কোন বিষয়টি শিক্ষার্থীরা ধরতে পারেননি এবং সেটি আবার পড়ানো যায়।

   সামেটিভ মূল্যায়নের (Summative Evaluation) সঙ্গে পার্থক্য:

   | বিষয় | Formative Evaluation | Summative Evaluation |
   |---|---|---|
   | কখন করা হয় | প্রক্রিয়া চলাকালে, বারবার | প্রক্রিয়া শেষে, একবার |
   | উদ্দেশ্য | উন্নয়ন ও সংশোধন | চূড়ান্ত বিচার ও সিদ্ধান্ত |
   | দৃষ্টিভঙ্গি | প্রক্রিয়াকেন্দ্রিক | ফলাফলকেন্দ্রিক |
   | ফলাফলের ব্যবহার | তাৎক্ষণিক সংশোধনে | গ্রহণ, প্রত্যাখ্যান বা সনদ প্রদানে |
   | আনুষ্ঠানিকতা | কম | বেশি |
   | সফটওয়্যারে উদাহরণ | কোড রিভিউ, স্প্রিন্ট রিভিউ, প্রোটোটাইপ মূল্যায়ন | User Acceptance Testing, চূড়ান্ত অডিট |
   | শিক্ষায় উদাহরণ | শ্রেণি পরীক্ষা, বাড়ির কাজ | বার্ষিক পরীক্ষা, বোর্ড পরীক্ষা |

   একটি প্রচলিত উপমা: রাঁধুনি রান্না করতে করতে বারবার চেখে দেখেন — এটি formative evaluation। অতিথি খেয়ে মতামত দেন — এটি summative evaluation। প্রথমটিতে লবণ ঠিক করা যায়, দ্বিতীয়টিতে আর কিছু করার থাকে না।

   গুরুত্ব: ফরম্যাটিভ মূল্যায়ন সমস্যাটিকে তখনই ধরে ফেলে, যখন তা সারানো সস্তা। সফটওয়্যারে প্রয়োজনীয়তা পর্যায়ে ধরা পড়া একটি ত্রুটি সারাতে যত খরচ হয়, একই ত্রুটি সরবরাহের পর ধরা পড়লে তার দশ থেকে একশ গুণ খরচ হয়। এ কারণেই আধুনিক পদ্ধতিগুলো, বিশেষত Agile, ধারাবাহিক ফরম্যাটিভ মূল্যায়নের ওপর নির্মিত।
3. **Explain Verification and Validation in Software Engineering. Discuss black-box testing and white-box testing with examples.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*


   Answer: Verification and validation are the two halves of software quality control, and the difference between them is one of the most frequently asked questions in software engineering.

   Verification:
   - Definition: the process of evaluating the products of a development phase to determine whether they satisfy the conditions imposed at the start of that phase.
   - The question it answers: "Are we building the product right?"
   - It checks conformity to the specification and to the design.
   - It is static in nature and does not require the code to run.
   - Activities: reviews, walkthroughs, inspections, desk checking, static analysis of code, and checking that the design conforms to the requirements.
   - Performed by: the quality assurance team, and by peers in reviews.
   - It finds defects early, at the point where they are introduced, which is where they are cheapest to correct.

   Validation:
   - Definition: the process of evaluating the finished product to determine whether it satisfies the needs of the customer and the intended use.
   - The question it answers: "Are we building the right product?"
   - It checks fitness for purpose, not merely conformity to a document.
   - It is dynamic in nature and requires the software to be executed.
   - Activities: unit testing, integration testing, system testing, acceptance testing, and all forms of black box and white box testing.
   - Performed by: the testing team, and by the customer during acceptance testing.
   - It finds defects at the end, when they are more expensive to correct.

   | Point | Verification | Validation |
   |---|---|---|
   | Question | Are we building the product right? | Are we building the right product? |
   | Checks against | The specification and the design | The customer's actual needs |
   | Nature | Static; the code need not run | Dynamic; the code must run |
   | Methods | Reviews, inspections, walkthroughs, static analysis | Testing at all levels |
   | Performed by | Quality assurance team and peers | Testing team and the customer |
   | When | Throughout development, at every phase | After the product or a component is built |
   | Cost of defects found | Low, since they are found early | Higher, since they are found late |
   | Finds | Deviation from the specification | Deviation from the real requirement |

   The classic illustration: suppose the specification wrongly says that the retirement age is 62 when the law says 59. Verification will pass, because the code correctly implements the specification. Validation will fail, because the system does not meet the real need. This is exactly why both are required.

   Black box testing and white box testing:

   | Point | Black Box Testing | White Box Testing |
   |---|---|---|
   | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
   | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
   | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
   | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
   | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
   | Programming knowledge | Not required | Essential |
   | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
   | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
   | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
   | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
   | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
   | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
   | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

   Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

   Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.

   Example of black box testing:

   A function accepts an age between 18 and 60 and returns whether the person is eligible for a loan. The tester knows only this specification and designs the cases from it:
   - Equivalence partitioning: one invalid class below (age 10), one valid class (age 35), one invalid class above (age 70). Three cases test three whole ranges.
   - Boundary value analysis: 17, 18, 19 and 59, 60, 61. Boundaries are where errors cluster, because of mistakes such as writing < instead of <=.
   - Error guessing: age 0, a negative age, a non-numeric input, an empty input.

   Example of white box testing:

   ```java
   int grade(int marks) {
       if (marks >= 80) return 1;        // A+
       else if (marks >= 60) return 2;   // A
       else if (marks >= 40) return 3;   // pass
       else return 4;                    // fail
   }
   ```
   The tester reads the code and designs cases to cover every branch: marks = 85 for the first branch, 70 for the second, 50 for the third and 30 for the fourth. Four cases give complete branch coverage. The tester would also notice that the code does not reject a mark above 100 or below 0, which is a defect a black box tester might never think to try.

   Why both are needed: white box testing confirms that the code does what it says; black box testing confirms that it does what the customer asked for. A program with a missing requirement can have 100 per cent code coverage and still be wrong.
4. **Difference between Alpha tests, Beta test, gamma test in software development.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*


   Answer: | Point | Alpha Testing | Beta Testing |
   |---|---|---|
   | Who tests | The organisation's own staff, typically an internal testing team and sometimes other employees who are not developers | Real external users, that is actual customers or a selected public |
   | Where | At the developer's site, in a controlled laboratory environment | At the user's own site, in the real environment |
   | When | After system testing, before beta | After alpha testing, before the general release |
   | Environment | Controlled, with the developers present | Uncontrolled and real, with all the variety of real hardware, networks and usage |
   | Developer presence | Present, and can observe and fix problems immediately | Absent; feedback is collected through reports and telemetry |
   | Type of testing | Both white box and black box may be used | Black box only |
   | Purpose | To find defects before the software is exposed to any outsider | To discover problems that only real use reveals, and to gather usability and acceptance feedback |
   | Reliability required | The product may still be unstable | The product must be reasonably stable |
   | Duration | Weeks, in cycles | Weeks to months |
   | Issues found | Functional and logical defects | Usability problems, unexpected usage patterns, compatibility with real hardware and configurations, scalability under real load |
   | Fixing | Defects can be fixed during the test cycle | Defects are usually deferred to a later release |
   | Also called | In-house acceptance testing | Field testing, external user acceptance testing, pre-release testing |

   Both are forms of acceptance testing, which is the final level of testing before release.

   Gamma testing: a less standard term, used for the final check made when the software is considered complete and only a limited set of critical checks is repeated before shipping, with no further feature changes. Some organisations use it to mean a release candidate check. It is not part of the standard ISTQB terminology, and an answer should say so rather than invent a definition.

   Practical illustration: a mobile banking application is first tested in the bank's own laboratory by its testing team (alpha), then released to two thousand selected customers who use it for real transactions on their own phones for a month (beta), and only then published to all customers.
5. **What do you understand about software quality assurance (SQA)? While purchasing a software system for your company, as a SQA team leader what aspects will you look into for a quality software.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 330 (ET: BIBM)]*


   Answer: Software Quality Assurance (SQA) is the set of planned and systematic activities carried out throughout the software development life cycle to ensure that the process used and the product produced conform to defined standards and satisfy the requirements. It is preventive: its aim is to build quality in, not to inspect it in at the end.

   Distinction from related terms, which is frequently asked:
   - Quality Assurance (QA) is process-oriented and preventive. It asks whether the right process is being followed, and it is the responsibility of the whole team.
   - Quality Control (QC) is product-oriented and corrective. It examines the finished product to find defects, and testing is its principal activity.
   - Testing is one activity within quality control.
   In short: QA prevents defects, QC detects them, and testing is how QC detects them.

   Activities of SQA:
   - Defining standards, procedures and coding conventions, and checking that they are followed.
   - Reviews, walkthroughs and inspections of requirements, design and code.
   - Audits of the process.
   - Configuration management and version control.
   - Defect tracking, measurement and root cause analysis.
   - Metrics collection: defect density, defect removal efficiency, test coverage, mean time between failures.
   - Training and process improvement, guided by frameworks such as CMMI, ISO 9001 and Six Sigma.
   - Test planning and management.

   Quality attributes of software, following the ISO 25010 model:

   - Functional suitability: does the software do what it is supposed to do, completely and correctly?
   - Reliability: does it work correctly for a stated period under stated conditions? Sub-attributes are maturity, availability, fault tolerance and recoverability. Measured by mean time between failures.
   - Performance efficiency: response time, throughput and resource utilisation under a stated load.
   - Usability: how easily users can learn and operate the system. Sub-attributes are learnability, operability, user error protection and accessibility.
   - Security: confidentiality, integrity, authenticity, accountability and non-repudiation.
   - Compatibility: co-existence with other systems, and interoperability with them.
   - Maintainability: how easily the software can be modified. Sub-attributes are modularity, reusability, analysability, modifiability and testability. This is the attribute that determines 60 to 70 per cent of the lifetime cost.
   - Portability: how easily it can be moved to another environment. Sub-attributes are adaptability, installability and replaceability.

   Two further attributes usually listed in examinations: correctness, that is conformity to the specification, and efficiency, that is economical use of resources.

   Metrics used to measure these:
   - Defect density = number of defects / size in KLOC or function points
   - Defect removal efficiency = defects found before release / total defects, expressed as a percentage
   - Test coverage = statements or branches executed / total, as a percentage
   - Mean time between failures and mean time to repair
   - Customer-reported defects per release

   What a Software Quality Assurance team leader should examine when purchasing a software system:

   1. Functional fit:
   - Does the product meet the documented business requirements? Prepare a requirements traceability matrix and score the product against every requirement as fully met, partly met or not met.
   - Is a live demonstration available, using our own data and our own scenarios rather than the vendor's prepared script?
   - Can the gaps be closed by configuration, or would they need customisation, which is far more expensive and complicates every future upgrade?

   2. Quality attributes:
   - Reliability: what is the vendor's record of downtime? Ask for the mean time between failures and the release history.
   - Performance: does it meet our response time and throughput targets under our expected peak load, not under an ideal laboratory load? Insist on a load test with our transaction volumes.
   - Security: authentication and authorisation model, encryption at rest and in transit, audit logging, vulnerability history, and compliance with the relevant standards. Ask for a recent independent penetration test report.
   - Usability: have real users from our own staff try it, not only the IT department.
   - Scalability: what happens when our data or our user count grows tenfold?

   3. Technical fit:
   - Compatibility with our existing operating systems, databases, browsers and hardware.
   - Integration: does it provide documented APIs, and can it exchange data with the systems we already run?
   - Data migration: can our existing data be imported, and at what cost?
   - Standards compliance and use of open formats, so that our data is not trapped.

   4. Vendor evaluation:
   - Financial stability and years in business. A cheap product from a vendor that disappears is the most expensive purchase possible.
   - Reference customers of comparable size, and permission to speak to them without the vendor present.
   - Support: hours of coverage, response and resolution times, and whether the service level agreement carries penalties.
   - Roadmap: how often are new versions released, and how long is each version supported?
   - Escrow: is the source code placed in escrow so that we can maintain it if the vendor fails?

   5. Total cost of ownership, not merely the purchase price:
   - Licence cost, and its model: perpetual, subscription, per user, per core.
   - Implementation, data migration and customisation cost.
   - Annual maintenance and support, typically 15 to 22 per cent of the licence cost.
   - Training, hardware and infrastructure.
   - The cost of eventually migrating away from it.

   6. Documentation and testability:
   - User manuals, administrator guides and API documentation.
   - A test environment we can use before purchase.
   - Test results and quality certifications from the vendor.

   7. Legal and compliance:
   - Licence terms, including any limits on use, and the ownership of data.
   - Compliance with the data protection rules that apply to us.
   - Exit clauses and the terms on which our data is returned.
   - Warranty and liability.

   8. Process evidence:
   - Does the vendor follow a defined development process? Ask for their CMMI level or ISO 9001 certification.
   - What is their defect density and defect removal efficiency?
   - How are security patches issued, and how quickly?

   Method of decision: score every candidate product against these criteria in a weighted matrix, with the weights agreed in advance by the business and by IT together. Run a proof of concept with the two highest-scoring products using our own data. Only then negotiate price. A decision made on price alone is the commonest cause of a failed software purchase.
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


   Answer: The correct matching:

   | Testing method | Correct option | Definition |
   |---|---|---|
   | (i) Unit Testing | (a) | The process where you test the smallest functional unit of code |
   | (ii) Integration Testing | (b) | A type of software testing in which the different units, modules or components of a software application are tested as a combined entity |
   | (iii) System Testing | (c) | Examines every component of an application to make sure that they work as a complete and unified whole |
   | (iv) Acceptance Testing | (d) | Software testing that evaluates whether a system meets its business and user requirements |
   | (v) Performance Testing | (e) | A testing measure that evaluates the speed, responsiveness and stability of a computer, network, software program or device under a workload |
   | (vi) Security Testing | (f) | Identifying and addressing security vulnerabilities in a software application |
   | (vii) Usability Testing | (g) | A method of testing the functionality of a website, app or other digital product by observing real users as they attempt to complete tasks on it |

   Answer in short form: i-a, ii-b, iii-c, iv-d, v-e, vi-f, vii-g.

   Explanation of each, since the matching is only the first half of a good answer:

   - Unit testing: the smallest testable component, one function, method or class, tested in isolation with its dependencies replaced by stubs or mocks. Performed by the developer, using JUnit or a similar framework. It is white box testing.

   - Integration testing: two or more already unit-tested components combined, to check that the interfaces between them work and that data passes correctly across them. Approaches: big bang, top-down with stubs, bottom-up with drivers, and incremental.

   - System testing: the complete integrated system tested against the specification as a whole, in an environment resembling production. It is black box testing and covers both functional and non-functional behaviour.

   - Acceptance testing: the customer's own users confirm that the system meets their business needs and formally accept it. Its forms are alpha, beta and user acceptance testing. It answers the question "are we building the right system".

   - Performance testing: measures speed, responsiveness and stability under load. Its sub-types are load testing (expected load), stress testing (beyond the limit, to find the breaking point), spike testing (sudden surge), endurance or soak testing (sustained load over hours, to find memory leaks) and scalability testing.

   - Security testing: finds vulnerabilities. Its forms are vulnerability scanning, penetration testing, security auditing and ethical hacking, checking against issues such as SQL injection, cross-site scripting, broken authentication and insecure configuration.

   - Usability testing: real users attempt real tasks while observers watch, measuring learnability, efficiency, error rate and satisfaction. It finds problems that no automated test can, because the software may be entirely correct and still be unusable.

   The order of the first four is also the order of the levels of testing: unit, then integration, then system, then acceptance, moving from the smallest scope to the largest and from the developer to the customer. The last three are types rather than levels, and they can be applied at more than one level.
7. **Given scenario of software engineering (Unit test, Regression Test, Smoke Test, Integration testing, Load Testing). Write the name of the testing and whether it is functional? Non-functional or both.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*


   Answer: Each of the named tests is identified below, with its category.

   | Test | What it does | When performed | Category |
   |---|---|---|---|
   | Unit Test | Tests the smallest testable component, a single function, method or class, in isolation, with dependencies replaced by stubs or mocks | As each unit is written, by the developer | Functional |
   | Integration Test | Tests the interfaces and interaction between two or more units that have already been unit tested, to confirm that data passes correctly across them | After unit testing, before system testing | Functional |
   | Smoke Test | A quick, shallow set of checks on the most critical functions, to decide whether a new build is stable enough to be tested further. Also called a build verification test | Immediately after every new build | Functional |
   | Regression Test | Re-runs existing tests after a change, to confirm that previously working functionality has not been broken | After every change, fix or enhancement | Both. It is usually functional, but a non-functional regression suite exists too, to confirm that performance has not degraded |
   | Load Test | Measures how the system behaves under the expected volume of concurrent users or transactions, checking response time, throughput and resource use | After the system is functionally stable | Non-functional |

   Explanation of the classification:

   - Functional testing asks what the system does. It checks behaviour against the specification: given this input, is this the correct output? Unit, integration and smoke testing are all of this kind.

   - Non-functional testing asks how well the system does it. It checks qualities rather than functions: how fast, how many users, how secure, how usable, how reliable. Load testing is of this kind, along with stress, security, usability, compatibility and reliability testing.

   - Regression testing is classified as both, and the reason is worth stating. Its purpose is not to test a new function but to confirm that nothing already working has been broken. The suite it re-runs is normally a set of functional tests, so it is usually described as functional; but a mature project also re-runs performance benchmarks after a change, which makes that part non-functional. Regression is therefore better understood as a purpose than as a type.

   Two further distinctions often asked with this question:

   - Smoke testing versus sanity testing: smoke testing is a broad and shallow check of the whole build to decide whether it is worth testing at all; sanity testing is a narrow and deep check of one specific area after a fix, to decide whether that fix worked. Smoke is scripted and often automated; sanity is usually unscripted.

   - Load testing versus stress testing: load testing applies the expected peak load and confirms that the system meets its targets; stress testing deliberately exceeds the limit to find the breaking point and to check that the system fails gracefully rather than catastrophically.
8. **(ক) Software Quality Assurance বলতে কী বোঝায়? উহার Attribute গুলো আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


   Answer: Software Quality Assurance (SQA) বলতে বোঝায় সফটওয়্যার উন্নয়নের পুরো জীবনচক্রজুড়ে পরিচালিত পরিকল্পিত ও সুসংগঠিত কার্যক্রমসমূহ, যার উদ্দেশ্য নিশ্চিত করা যে ব্যবহৃত প্রক্রিয়া এবং উৎপাদিত পণ্য উভয়ই নির্ধারিত মান ও প্রয়োজনীয়তা পূরণ করছে। এটি প্রতিরোধমূলক: লক্ষ্য শেষে পরীক্ষা করে ত্রুটি খুঁজে বের করা নয়, বরং প্রক্রিয়ার ভেতরেই গুণমান গেঁথে দেওয়া।

   সম্পর্কিত পরিভাষার পার্থক্য:
   - Quality Assurance (QA): প্রক্রিয়াকেন্দ্রিক ও প্রতিরোধমূলক। প্রশ্ন করে — সঠিক প্রক্রিয়া অনুসরণ করা হচ্ছে কি? এটি পুরো দলের দায়িত্ব।
   - Quality Control (QC): পণ্যকেন্দ্রিক ও সংশোধনমূলক। তৈরি হওয়া পণ্য পরীক্ষা করে ত্রুটি খুঁজে বের করে।
   - Testing: QC এর একটি কার্যক্রম মাত্র।
   সংক্ষেপে: QA ত্রুটি প্রতিরোধ করে, QC ত্রুটি শনাক্ত করে, আর Testing হলো শনাক্ত করার উপায়।

   SQA এর কার্যক্রম:
   - মান, পদ্ধতি ও কোডিং রীতি নির্ধারণ এবং তা অনুসরণ হচ্ছে কিনা তা যাচাই করা।
   - প্রয়োজনীয়তা, নকশা ও কোডের পর্যালোচনা, ওয়াকথ্রু ও ইনস্পেকশন।
   - প্রক্রিয়ার নিরীক্ষা (audit)।
   - কনফিগারেশন ব্যবস্থাপনা ও সংস্করণ নিয়ন্ত্রণ।
   - ত্রুটির হিসাব রাখা, পরিমাপ করা ও মূল কারণ বিশ্লেষণ করা।
   - মেট্রিক সংগ্রহ: defect density, defect removal efficiency, test coverage।
   - প্রশিক্ষণ ও প্রক্রিয়া উন্নয়ন, CMMI, ISO 9001 বা Six Sigma কাঠামো অনুসরণ করে।

   Software Quality Attributes (ISO 25010 মডেল অনুযায়ী):

   - Functional Suitability (কার্যগত উপযুক্ততা): সফটওয়্যারটি যা করার কথা, তা সম্পূর্ণ ও সঠিকভাবে করছে কিনা। উপ-বৈশিষ্ট্য: completeness, correctness, appropriateness।

   - Reliability (নির্ভরযোগ্যতা): নির্দিষ্ট শর্তে নির্দিষ্ট সময় ধরে সঠিকভাবে কাজ করার ক্ষমতা। উপ-বৈশিষ্ট্য: maturity, availability, fault tolerance, recoverability। পরিমাপ: Mean Time Between Failures।

   - Performance Efficiency (কর্মদক্ষতা): নির্দিষ্ট চাপের অধীনে সাড়া দেওয়ার সময়, থ্রুপুট ও সম্পদের ব্যবহার।

   - Usability (ব্যবহারযোগ্যতা): ব্যবহারকারী কত সহজে শিখতে ও চালাতে পারেন। উপ-বৈশিষ্ট্য: learnability, operability, user error protection, accessibility।

   - Security (নিরাপত্তা): গোপনীয়তা, অখণ্ডতা, প্রমাণীকরণ, জবাবদিহি ও অস্বীকার-অসম্ভবতা (non-repudiation)।

   - Compatibility (সামঞ্জস্য): অন্য ব্যবস্থার সঙ্গে সহাবস্থান ও আন্তঃক্রিয়া করার ক্ষমতা।

   - Maintainability (রক্ষণাবেক্ষণযোগ্যতা): কত সহজে পরিবর্তন করা যায়। উপ-বৈশিষ্ট্য: modularity, reusability, analysability, modifiability, testability। জীবনকালের মোট খরচের ৬০ থেকে ৭০ শতাংশ এই একটি বৈশিষ্ট্যই নির্ধারণ করে।

   - Portability (স্থানান্তরযোগ্যতা): অন্য পরিবেশে কত সহজে সরানো যায়। উপ-বৈশিষ্ট্য: adaptability, installability, replaceability।

   পরীক্ষায় সচরাচর উল্লিখিত আরও দুটি: Correctness (স্পেসিফিকেশনের সঙ্গে সঙ্গতি) এবং Efficiency (সম্পদের মিতব্যয়ী ব্যবহার)।

   পরিমাপের সূচক:
   - Defect density = ত্রুটির সংখ্যা / আকার (KLOC বা function point)
   - Defect removal efficiency = সরবরাহের আগে পাওয়া ত্রুটি / মোট ত্রুটি, শতকরায়
   - Test coverage = পরীক্ষিত বিবৃতি বা শাখা / মোট, শতকরায়
   - Mean Time Between Failures ও Mean Time To Repair

   গুরুত্ব: প্রয়োজনীয়তা পর্যায়ে ধরা পড়া একটি ত্রুটি সারাতে যত খরচ হয়, একই ত্রুটি সরবরাহের পর ধরা পড়লে তার ১০ থেকে ১০০ গুণ খরচ হয়। SQA এর মূল অর্থনৈতিক যুক্তি এটিই।
9. **6.5 Explain the difference between Unit Testing and Integration Testing.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: | Point | Unit Testing | Integration Testing |
   |---|---|---|
   | What is tested | A single smallest testable component: one function, method or class, in isolation | The interfaces and interaction between two or more units that have already been unit tested |
   | Purpose | To confirm that each unit does what it is supposed to do on its own | To confirm that units work correctly together and that data passes correctly across their interfaces |
   | Performed by | The developer who wrote the code | Developers or a dedicated integration testing team |
   | When | As each unit is written, before integration | After unit testing, before system testing |
   | Knowledge required | White box; the internal code is known | Usually grey box; the interfaces are known, the internals partly |
   | Isolation | Dependencies are replaced with stubs, mocks or drivers | Real components are used, progressively |
   | Scope | Very narrow | Wider, covering the connections |
   | Defects found | Logic errors, wrong calculations, unhandled edge cases inside a unit | Interface mismatches, wrong parameter order or type, incorrect data format, timing problems, missing error handling between modules |
   | Speed | Very fast; thousands of unit tests run in seconds | Slower, since real components and sometimes databases and networks are involved |
   | Tools | JUnit, NUnit, PyTest, Mockito | Postman, REST Assured, JUnit with Spring Boot Test, Selenium for end-to-end |
   | Ease of locating a fault | Easy; the fault is inside the unit under test | Harder; the fault lies somewhere in the interaction |

   Approaches to integration:
   - Big bang: all modules are combined at once and tested together. Simple but faults are very hard to locate.
   - Top-down: high-level modules are tested first, with stubs standing in for the lower ones that are not yet written. The main control logic is validated early.
   - Bottom-up: low-level modules are tested first, with drivers calling them. The utility layers are validated early, but the user-visible behaviour appears late.
   - Sandwich or hybrid: top-down and bottom-up are combined, meeting in the middle.
   - Incremental: modules are added one at a time and tested after each addition, which makes fault location easy.

   Stubs and drivers, which are often asked with this question:
   - A stub is a dummy module that stands in for a called module that is not yet ready. It is used in top-down integration.
   - A driver is a dummy module that calls the module under test. It is used in bottom-up integration.

   Illustration: suppose a function calculateTax() returns the tax and a function generateInvoice() uses it. Unit testing checks that calculateTax(50000) returns the correct figure, with generateInvoice replaced by nothing at all. Integration testing checks that generateInvoice actually calls calculateTax with the right argument, receives the value correctly, and formats it into the invoice. A unit can be perfectly correct and the integration still fail, for example if one side works in taka and the other in paisa.
10. **What is Software testing? Difference between Black box testing and White box testing.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


    Answer: Software testing is the process of evaluating a software product to find defects and to verify that it meets the specified requirements. Its purpose is to establish confidence that the software will behave correctly in use, and, equally important, to find the ways in which it does not.

    Objectives:
    - To find defects before the customer does.
    - To verify that the software meets its specification.
    - To validate that it meets the customer's actual need.
    - To measure quality and to provide information for a release decision.
    - To prevent defects, by involving testers early in requirements and design reviews.

    An important principle, stated by Dijkstra: testing can show the presence of defects, but never their absence. Exhaustive testing is impossible for any non-trivial program, so testing is always a matter of choosing the most valuable subset of possible tests.

    Levels of testing: unit, integration, system and acceptance.
    Types: functional and non-functional (performance, security, usability, compatibility), and regression testing after every change.

    Difference between black box and white box testing:

    | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.
11. **Define test plan and Test case.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 567 (ET: N/A)]*


    Answer:

    Test Plan:

    A test plan is a formal document that describes the scope, approach, resources and schedule of the testing activities for a project. It is prepared by the test manager or test lead, usually during the requirement or design phase, and it is the master document that governs all testing.

    Contents of a test plan, following the IEEE 829 standard:
    - Test plan identifier and version
    - Introduction and objectives
    - Scope: what will be tested, and equally important, what will not be tested
    - Test items: the software components and versions to be tested
    - Features to be tested, and features not to be tested with the reason
    - Test approach or strategy: the levels and types of testing, and the techniques to be used
    - Item pass and fail criteria
    - Suspension criteria and resumption requirements: when testing will be stopped, for example if the build fails the smoke test
    - Test deliverables: test cases, test data, defect reports, the test summary report
    - Test environment: hardware, software, network, tools and test data
    - Roles and responsibilities: who does what
    - Staffing and training needs
    - Schedule and milestones
    - Risks and contingencies
    - Approvals

    Test Case:

    A test case is a set of conditions, inputs, execution steps and expected results, written to verify one particular behaviour of the software. It is the smallest unit of testing work.

    Contents of a test case:
    - Test case ID, a unique identifier
    - Test case title or description
    - Related requirement, for traceability
    - Preconditions: the state the system must be in before the test
    - Test data: the exact inputs to be used
    - Test steps, numbered and precise enough for anyone to follow
    - Expected result
    - Actual result, filled in during execution
    - Status: pass, fail, blocked or not executed
    - Priority and severity
    - Author, date and any remarks

    Example of a test case:

    | Field | Value |
    |---|---|
    | Test Case ID | TC_LOGIN_003 |
    | Title | Verify login fails with an incorrect password |
    | Requirement | REQ-AUTH-02 |
    | Precondition | A user account rahim@example.com exists and is active |
    | Test data | Username: rahim@example.com, Password: WrongPass123 |
    | Steps | 1. Open the login page. 2. Enter the username. 3. Enter the wrong password. 4. Click Login. |
    | Expected result | Login is refused; the message "Invalid username or password" is displayed; the user remains on the login page; the failed attempt is recorded in the audit log |
    | Actual result | (filled in on execution) |
    | Status | (Pass / Fail) |
    | Priority | High |

    Difference between the two:

    | Point | Test Plan | Test Case |
    |---|---|---|
    | Level | Strategic; covers the whole project | Tactical; covers one specific condition |
    | Number | One per project or per release | Hundreds or thousands per project |
    | Prepared by | Test manager or test lead | Test engineer |
    | Answers | What, why, when, who and with what resources | Exactly how to test one thing, and what to expect |
    | Changes | Rarely, and through formal approval | Often, as requirements evolve |
    | Standard | IEEE 829 test plan | IEEE 829 test case specification |

    Related terms: a test scenario is a high-level description of what is to be tested, from which several test cases are derived; a test suite is a collection of related test cases; and a test script is the automated implementation of a test case.
12. **(d) What is the main difference between black box and white box testing?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)], [Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)], [Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*


    Answer: The main difference is the knowledge the tester has of the internal structure of the software.

    - In black box testing the tester knows nothing about the internal code. Test cases are derived only from the specification, that is from what the system is supposed to do. The tester supplies inputs and checks outputs, treating the program as an opaque box.

    - In white box testing the tester has full knowledge of the source code and designs test cases to exercise its internal structure: its statements, branches, conditions and paths.

    | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.

    Stated in one sentence: black box testing asks whether the software does what the customer wants; white box testing asks whether the code does what the programmer wrote it to do. Both questions must be answered, because a program can pass either test and fail the other.
13. **Verification and validation are two process areas at CMMI level 3. For both of these areas (a) provide a definition (b) a description of how you can fulfill these areas in your software testing activities.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 444 (ET: BIBM)]*


    Answer: Verification and validation are two process areas at CMMI maturity level 3, the Defined level.

    (a) Definitions:

    Verification:
    - The CMMI definition: the purpose of verification is to ensure that selected work products meet their specified requirements.
    - In plain terms: verification confirms that the product is being built correctly, that is, in conformity with its specification and design.
    - The question it answers: "Are we building the product right?"
    - It is static; the software need not be executed.
    - Its principal method is peer review.

    Validation:
    - The CMMI definition: the purpose of validation is to demonstrate that a product or product component fulfils its intended use when placed in its intended environment.
    - In plain terms: validation confirms that the right product is being built, that is, one that actually meets the customer's need.
    - The question it answers: "Are we building the right product?"
    - It is dynamic; the software must be executed in a realistic environment.
    - Its principal method is testing with real users and real data.

    (b) How each is fulfilled in software testing activities:

    Fulfilling verification:

    - Establish a verification environment: define the review checklists, the entry and exit criteria for each phase, the standards documents and the tools for static analysis.
    - Select the work products to be verified: the requirements specification, the architecture and design documents, the test plans, the test cases and the source code. Every significant work product should be verified, not only the code.
    - Conduct peer reviews. CMMI names this as a specific practice, and it is the heart of verification.
      - Inspection: the most formal, with defined roles (moderator, author, reader, recorder), preparation before the meeting, and recorded defect counts. Fagan inspections typically find 60 to 90 per cent of defects present.
      - Walkthrough: the author leads colleagues through the work product to gather comments.
      - Desk check: a single reviewer reads and comments.
    - Perform static analysis of the code with tools such as SonarQube, Checkstyle or PMD, to find violations of standards, unreachable code, unsafe constructs and complexity hot spots.
    - Maintain a traceability matrix linking every requirement to its design element, its code and its test cases, so that nothing is missed and nothing superfluous is built.
    - Analyse the verification results: record the defects found, classify them by type and phase of origin, and feed that back into process improvement. A high proportion of requirement defects found late is itself a process defect.
    - In testing terms, verification corresponds to reviewing the test cases themselves before they are run, and to unit and integration testing against the design.

    Fulfilling validation:

    - Establish a validation environment that resembles the production environment as closely as possible: the same operating system, database version, network conditions and data volumes. Validating in an unrealistic environment proves nothing.
    - Select the products to be validated and the validation methods: system testing, end-to-end testing, user acceptance testing, alpha and beta testing, pilot operation, and demonstrations to the customer.
    - Prepare realistic test data, including production-like volumes and the awkward cases that real data always contains, with any personal data masked.
    - Involve the actual end users, not only the testing team. This is what distinguishes validation from verification: the criterion is fitness for the user's purpose, not conformity to a document.
    - Perform system testing against the requirements as a whole, including non-functional requirements: performance under real load, security, usability and compatibility.
    - Perform user acceptance testing with business scenarios written by the users themselves, and obtain formal sign-off.
    - Run a pilot or a beta with a limited group of real users in the real environment, and collect their feedback and their usage data.
    - Analyse the validation results: any failure means either that the requirement was wrong or that the product does not meet it, and the two must be distinguished, because the corrective action differs.

    Why both are required, illustrated:

    Suppose the requirement specification states that the retirement age is 62, but the law says 59.
    - Verification passes: the code correctly implements the specification, the design matches the requirement, and every review finds nothing wrong.
    - Validation fails: the users try the system with real cases and find that it computes the wrong retirement date.
    Verification cannot catch this, because the fault is in the specification itself. Only validation, which tests against the real need rather than against the document, can find it. Conversely, validation alone would find such faults very late and expensively, which is why verification must run throughout.

    Supporting practices at CMMI level 3 that both depend on: Requirements Management, Configuration Management, Measurement and Analysis, and Process and Product Quality Assurance.
14. **অথবা, (ক) Software testing কী? উহার গুরুত্ব আলোচনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*


    Answer: Software testing হলো একটি সফটওয়্যার পণ্য মূল্যায়নের প্রক্রিয়া, যার উদ্দেশ্য ত্রুটি খুঁজে বের করা এবং যাচাই করা যে সফটওয়্যারটি নির্ধারিত প্রয়োজনীয়তা পূরণ করছে। এটি কেবল ভুল ধরার কাজ নয়, বরং সফটওয়্যারের গুণমান সম্পর্কে তথ্য সরবরাহ করার প্রক্রিয়া, যার ভিত্তিতে সরবরাহের সিদ্ধান্ত নেওয়া হয়।

    উদ্দেশ্যসমূহ:
    - গ্রাহকের আগেই ত্রুটি খুঁজে বের করা।
    - সফটওয়্যারটি স্পেসিফিকেশন পূরণ করছে কিনা তা যাচাই করা (verification)।
    - সফটওয়্যারটি প্রকৃত প্রয়োজন মেটাচ্ছে কিনা তা নিশ্চিত করা (validation)।
    - গুণমান পরিমাপ করে সরবরাহের সিদ্ধান্তের জন্য তথ্য দেওয়া।
    - ত্রুটি প্রতিরোধ করা, কারণ পরীক্ষকদের প্রয়োজনীয়তা ও নকশা পর্যালোচনায় যুক্ত করলে ত্রুটি জন্মানোর আগেই ঠেকানো যায়।

    Software Testing এর গুরুত্ব:

    - অর্থনৈতিক গুরুত্ব: ত্রুটি সারানোর খরচ পর্যায়ের সঙ্গে সঙ্গে দ্রুত বাড়ে। প্রয়োজনীয়তা পর্যায়ে ধরা পড়া একটি ত্রুটি সারাতে যত খরচ, নকশা পর্যায়ে তার প্রায় ৫ গুণ, কোডিংয়ে ১০ গুণ, টেস্টিংয়ে ২০ গুণ এবং সরবরাহের পর ১০০ গুণ বা তার বেশি। আগেভাগে পরীক্ষা করাই সবচেয়ে সস্তা।

    - নিরাপত্তা ও জীবনরক্ষা: চিকিৎসা যন্ত্র, বিমান নিয়ন্ত্রণ, পারমাণবিক চুল্লি ও যানবাহনের সফটওয়্যারে একটি ত্রুটি প্রাণহানি ঘটাতে পারে। Therac-25 বিকিরণ যন্ত্রের সফটওয়্যার ত্রুটিতে রোগীর মৃত্যু এবং Ariane 5 রকেটের একটি রূপান্তর ত্রুটিতে ৩৭ কোটি ডলারের ক্ষতি এর পরিচিত উদাহরণ।

    - আর্থিক ক্ষতি প্রতিরোধ: ব্যাংকিং ও লেনদেন ব্যবস্থায় একটি হিসাবের ত্রুটি বিপুল আর্থিক ক্ষতি ডেকে আনতে পারে।

    - প্রতিষ্ঠানের সুনাম রক্ষা: ত্রুটিপূর্ণ সফটওয়্যার প্রকাশ পেলে গ্রাহকের আস্থা নষ্ট হয়, যা পুনরুদ্ধার করা কঠিন।

    - গুণমান নিশ্চিতকরণ: কেবল কার্যকারিতা নয়, কর্মদক্ষতা, নিরাপত্তা, ব্যবহারযোগ্যতা ও নির্ভরযোগ্যতাও যাচাই করা হয়।

    - গ্রাহক সন্তুষ্টি: পরীক্ষিত সফটওয়্যার নির্ভরযোগ্যভাবে চলে, ফলে ব্যবহারকারীর আস্থা বাড়ে।

    - আইনি ও নিয়ন্ত্রক বাধ্যবাধকতা: বহু ক্ষেত্রে পরীক্ষার প্রমাণপত্র ছাড়া সনদ বা অনুমোদন মেলে না।

    - রক্ষণাবেক্ষণ সহজ করা: স্বয়ংক্রিয় রিগ্রেশন টেস্ট থাকলে ভবিষ্যতে নির্ভয়ে কোড পরিবর্তন করা যায়, কারণ কিছু ভেঙে গেলে সঙ্গে সঙ্গে জানা যাবে।

    টেস্টিংয়ের মূল নীতিসমূহ:
    - টেস্টিং ত্রুটির উপস্থিতি প্রমাণ করতে পারে, অনুপস্থিতি নয় (Dijkstra)।
    - সম্পূর্ণ বা নিঃশেষ পরীক্ষা (exhaustive testing) অসম্ভব; তাই ঝুঁকি ও অগ্রাধিকার দেখে পরীক্ষা করতে হয়।
    - আগেভাগে পরীক্ষা শুরু করা লাভজনক (early testing)।
    - ত্রুটি গুচ্ছাকারে থাকে (defect clustering): সাধারণত ২০ শতাংশ মডিউলে ৮০ শতাংশ ত্রুটি পাওয়া যায়।
    - কীটনাশক প্যারাডক্স (pesticide paradox): একই টেস্ট বারবার চালালে নতুন ত্রুটি আর পাওয়া যায় না; টেস্ট কেস নিয়মিত হালনাগাদ করতে হয়।
    - টেস্টিং প্রেক্ষাপটনির্ভর: ব্যাংকিং ব্যবস্থা ও মোবাইল গেম একইভাবে পরীক্ষা করা হয় না।
    - ত্রুটিহীনতার ভ্রান্তি (absence of errors fallacy): ত্রুটিহীন সফটওয়্যারও অকেজো হতে পারে, যদি সেটি ব্যবহারকারীর প্রকৃত প্রয়োজন না মেটায়।
15. **অথবা, (ক) Black-box এবং White-box testing এর মধ্যে পার্থক্যগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*


    Answer: Black-box এবং White-box testing এর মধ্যে পার্থক্য:

    | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.

    সংক্ষেপে মূল পার্থক্য: Black box টেস্টিংয়ে পরীক্ষক কোডের ভেতরে কী আছে তা জানেন না; তিনি কেবল স্পেসিফিকেশন দেখে ইনপুট দেন এবং আউটপুট মিলিয়ে দেখেন। White box টেস্টিংয়ে পরীক্ষক সোর্স কোড দেখে প্রতিটি শাখা ও পথ পরীক্ষা করার জন্য কেস তৈরি করেন।

    দুটিই প্রয়োজন: White box নিশ্চিত করে কোডটি যা লেখা হয়েছে তা ঠিকভাবে করছে; Black box নিশ্চিত করে কোডটি যা করার কথা ছিল তা-ই করছে। একটি প্রোগ্রামে কোড কভারেজ শতভাগ হতে পারে, অথচ একটি প্রয়োজনীয়তা বাদ পড়ে থাকতে পারে।
16. **What is software testing? Discuss effective and exhaustive testing.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*


    Answer: Software testing is the process of evaluating a software product to find defects and to verify that it meets its specified requirements. It provides information about the quality of the product on which a release decision can be based.

    Effective testing:

    Effective testing means testing that finds the greatest number of important defects for the least effort. It accepts that not everything can be tested and concentrates the available effort where it will do most good.

    Characteristics of effective testing:
    - It is risk-based: the areas where failure would be most damaging, and where defects are most likely, are tested most thoroughly.
    - It is planned: it has clear objectives, entry and exit criteria and defined coverage targets.
    - It uses systematic techniques rather than random inputs: equivalence partitioning, boundary value analysis, decision tables and state transition testing, each of which covers many possible inputs with a few cases.
    - It begins early. Reviewing the requirements finds defects before any code exists, and a requirement defect found then costs a hundredth of what it costs after release.
    - It exploits defect clustering: about 20 per cent of the modules typically contain 80 per cent of the defects, so effort is concentrated where defects have already been found.
    - It is automated where the tests will be repeated, in particular regression tests, and manual where human judgement is needed, as in usability and exploratory testing.
    - It is measured: defect density, defect removal efficiency and coverage are tracked, so that the process itself can be improved.
    - It avoids the pesticide paradox by revising the test cases regularly, since a suite that has been run many times stops finding new defects.

    Exhaustive testing:

    Exhaustive testing means testing every possible combination of inputs, preconditions and execution paths. It would prove the software correct, and it is impossible for any non-trivial program.

    Why it is impossible:

    - The input space is astronomically large. Consider a function that takes two 32-bit integers. The number of input combinations is 2^32 x 2^32 = 2^64, which is about 1.8 x 10^19. At a million tests per second this would take more than half a million years.

    - The number of paths is astronomically large. A loop that may execute up to 20 times, containing a single if, has 2^20 possible path combinations, which is over a million, for a fragment of a dozen lines.

    - The number of states is astronomically large. A form with ten fields, each with ten possible values, has 10^10 combinations.

    - Timing, concurrency and environment multiply all of this further. A concurrent program's behaviour depends on the interleaving of threads, which is not under the tester's control.

    - Even if it were possible, it would still not guarantee correctness, because the specification against which the outputs are compared may itself be wrong.

    Conclusion, which is one of the seven principles of testing: exhaustive testing is impossible except in the most trivial cases, so testing must always be a selection. Effective testing is precisely the art of choosing that selection well. Dijkstra's statement expresses the same point: testing can show the presence of defects, but never their absence.

    | Point | Effective testing | Exhaustive testing |
    |---|---|---|
    | Coverage | A selected, risk-based subset | Every possible combination |
    | Feasibility | Practical and standard | Impossible for any real program |
    | Basis of selection | Risk, likelihood of defects, criticality | None; everything is tested |
    | Cost | Controlled and justified | Infinite in practice |
    | Guarantee | Confidence, not proof | Proof, in theory only |
    | Used in practice | Always | Never, except in trivial cases |
17. **How alpha testing is performed in software development?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*


    Answer: Alpha testing is the first stage of acceptance testing, performed at the developer's own site by the organisation's own people before the software is shown to any external user.

    How it is performed:

    Step 1 - Entry criteria are met:
    - System testing is complete and its exit criteria have been satisfied.
    - All critical and high-severity defects from system testing have been fixed.
    - The build is stable enough to be used for realistic work.
    - The test environment, resembling production, is ready, and realistic test data has been prepared.

    Step 2 - The alpha test team is assembled:
    - The internal testing team, and employees from other departments who are not developers, because a person who wrote the code cannot see it as a user does.
    - In a product company, the sales, support and training staff are often included, since they will later have to explain the product.

    Step 3 - Realistic scenarios are prepared:
    - The scenarios describe complete business tasks end to end, not isolated functions. For a banking application: open an account, deposit money, transfer to another account, print a statement, close the account.
    - Both the normal path and the awkward cases are covered.

    Step 4 - The software is used as a real user would use it:
    - Testers run the scenarios in a controlled laboratory environment, with the developers present.
    - Both black box testing, from the user's point of view, and white box testing, examining the internals, may be used, which distinguishes alpha testing from beta testing.
    - Usage is observed and, where possible, recorded, since how a user struggles is as informative as whether the software works.

    Step 5 - Defects are logged and fixed within the cycle:
    - Because the developers are present, defects are reported, triaged and fixed immediately, and the corrected build is retested.
    - This is the main practical difference from beta testing, in which defects are usually deferred to a later release.

    Step 6 - Cycles are repeated:
    - Alpha testing is normally run in two or more cycles, each with a fresh build, until the defect discovery rate falls to an acceptable level.

    Step 7 - Exit criteria and sign-off:
    - No open critical or high-severity defects.
    - All planned scenarios executed with an agreed pass rate.
    - Performance and security checks satisfied.
    - The product is then declared ready for beta testing.

    Characteristics of alpha testing:
    - Location: the developer's site, in a controlled environment.
    - Testers: internal staff, not customers.
    - Developers: present, and able to observe and intervene.
    - Techniques: both black box and white box.
    - Stability required: the product may still be unstable.
    - Duration: typically a few weeks, in cycles.
    - Defects found: functional and logical errors, missing features, usability problems.

    What it achieves:
    - It finds defects before any outsider sees the product, which protects the organisation's reputation.
    - It validates that the system as a whole meets the business need, not merely the specification.
    - It gives the support and training staff early experience of the product.
    - It reduces the number of embarrassing failures during beta testing.

    Its limitation, and why beta testing follows: alpha testing is conducted in a controlled environment by people who know the product and who share the developers' assumptions. It cannot reproduce the variety of real hardware, real network conditions and unexpected real usage. Only beta testing, with real users at their own sites, can do that.
18. **(b) Explain block box testing and white box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 692 (ET: N/A)]*


    Answer: | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.
19. **(a) Explain software validation, Verification and Modularity.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*


    Answer:

    Verification and validation are the two halves of software quality control, and the difference between them is one of the most frequently asked questions in software engineering.

    Verification:
    - Definition: the process of evaluating the products of a development phase to determine whether they satisfy the conditions imposed at the start of that phase.
    - The question it answers: "Are we building the product right?"
    - It checks conformity to the specification and to the design.
    - It is static in nature and does not require the code to run.
    - Activities: reviews, walkthroughs, inspections, desk checking, static analysis of code, and checking that the design conforms to the requirements.
    - Performed by: the quality assurance team, and by peers in reviews.
    - It finds defects early, at the point where they are introduced, which is where they are cheapest to correct.

    Validation:
    - Definition: the process of evaluating the finished product to determine whether it satisfies the needs of the customer and the intended use.
    - The question it answers: "Are we building the right product?"
    - It checks fitness for purpose, not merely conformity to a document.
    - It is dynamic in nature and requires the software to be executed.
    - Activities: unit testing, integration testing, system testing, acceptance testing, and all forms of black box and white box testing.
    - Performed by: the testing team, and by the customer during acceptance testing.
    - It finds defects at the end, when they are more expensive to correct.

    | Point | Verification | Validation |
    |---|---|---|
    | Question | Are we building the product right? | Are we building the right product? |
    | Checks against | The specification and the design | The customer's actual needs |
    | Nature | Static; the code need not run | Dynamic; the code must run |
    | Methods | Reviews, inspections, walkthroughs, static analysis | Testing at all levels |
    | Performed by | Quality assurance team and peers | Testing team and the customer |
    | When | Throughout development, at every phase | After the product or a component is built |
    | Cost of defects found | Low, since they are found early | Higher, since they are found late |
    | Finds | Deviation from the specification | Deviation from the real requirement |

    The classic illustration: suppose the specification wrongly says that the retirement age is 62 when the law says 59. Verification will pass, because the code correctly implements the specification. Validation will fail, because the system does not meet the real need. This is exactly why both are required.

    Modularity:

    Modularity is the design principle by which a software system is divided into separate, named, addressable components called modules, each of which performs a well-defined part of the whole and can be developed, tested and modified largely independently of the others.

    Characteristics of a well-modularised system:
    - High cohesion within each module: everything inside a module belongs together and serves a single purpose.
    - Low coupling between modules: modules depend on one another as little as possible, and only through well-defined interfaces.
    - Information hiding: each module conceals its internal data and implementation, exposing only what other modules genuinely need. This is Parnas's criterion, and it is what makes a module replaceable.
    - Well-defined interfaces: what a module offers and what it requires are stated explicitly.
    - Functional independence: a module can be understood on its own.

    Advantages of modularity:
    - Complexity is reduced, because a large problem becomes several small ones. This is divide and conquer applied to design.
    - Parallel development becomes possible, since different teams can work on different modules once the interfaces are agreed.
    - Testing is easier, because each module can be unit tested in isolation.
    - Maintenance is easier and safer, since a change is confined to one module and does not ripple outwards.
    - Reuse becomes possible, since a well-defined module can be used in another system.
    - Faults are easier to locate, because the failing module can usually be identified quickly.

    The cost of over-modularisation: dividing a system into too many very small modules increases the number of interfaces and the cost of communication between them, so the total effort begins to rise again. There is an optimum number of modules, which is the point at which the falling cost per module and the rising cost of integration cross.

    ```
    Cost
     |\                       /
     | \  cost per module   /  cost of integration
     |  \                 /
     |   \               /
     |    \_____________/     <- total cost, with a minimum
     |         optimum
     +---------------------------> number of modules
    ```

    How the three relate: modularity is a property of the design; verification checks that the design and the code conform to the specification; and validation checks that the resulting system meets the user's real need. Good modularity makes both verification and validation cheaper, because each module can be reviewed and tested on its own.
20. **(b) Explain the diference between black-box and White-box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*


    Answer: | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.
21. **Software testing কত প্রকার ও কী কী? Testing এর ক্ষেত্রে Boundary Value Analysis (BVA) এবং Equivalence Partitioning কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*


    Answer: Software testing এর প্রকারভেদ:

    ক. পরীক্ষণের স্তর অনুযায়ী (Levels of Testing) — চারটি:
    - Unit Testing: ক্ষুদ্রতম একক, অর্থাৎ একটি ফাংশন বা ক্লাস আলাদাভাবে পরীক্ষা করা। করেন ডেভেলপার।
    - Integration Testing: একাধিক ইউনিট একত্র করে তাদের মধ্যকার ইন্টারফেস পরীক্ষা করা।
    - System Testing: সম্পূর্ণ সমন্বিত ব্যবস্থাটি স্পেসিফিকেশনের বিপরীতে পরীক্ষা করা।
    - Acceptance Testing: গ্রাহক নিজে যাচাই করেন ব্যবস্থাটি তাঁর ব্যবসায়িক প্রয়োজন মেটায় কিনা। এর রূপ: Alpha, Beta ও User Acceptance Testing।

    খ. পদ্ধতি অনুযায়ী:
    - Black Box Testing: কোড না দেখে কেবল স্পেসিফিকেশন থেকে পরীক্ষা।
    - White Box Testing: সোর্স কোড দেখে প্রতিটি শাখা ও পথ পরীক্ষা।
    - Grey Box Testing: আংশিক অভ্যন্তরীণ জ্ঞান নিয়ে পরীক্ষা।

    গ. কার্যকারিতা অনুযায়ী:
    - Functional Testing: ব্যবস্থাটি কী করে তা পরীক্ষা — smoke, sanity, regression, integration, user acceptance।
    - Non-functional Testing: কতটা ভালোভাবে করে তা পরীক্ষা — performance (load, stress, spike, endurance), security, usability, compatibility, reliability, scalability।

    ঘ. সম্পাদনের ধরন অনুযায়ী:
    - Manual Testing: মানুষ হাতে করে।
    - Automated Testing: টুল দিয়ে, যেমন Selenium, JUnit, JMeter।

    ঙ. বিশেষ ধরনসমূহ:
    - Regression Testing: পরিবর্তনের পর আগের কাজ ভেঙেছে কিনা তা যাচাই।
    - Smoke Testing: নতুন বিল্ড আদৌ পরীক্ষার যোগ্য কিনা তার দ্রুত যাচাই।
    - Sanity Testing: নির্দিষ্ট একটি সংশোধন কাজ করেছে কিনা তার সংকীর্ণ যাচাই।
    - Exploratory Testing: পূর্বলিখিত কেস ছাড়া, অভিজ্ঞতার ভিত্তিতে অনুসন্ধান।
    - Ad-hoc Testing: অপরিকল্পিত, এলোমেলো পরীক্ষা।
    - Recovery Testing: বিপর্যয়ের পর ব্যবস্থাটি ঠিকমতো পুনরুদ্ধার হয় কিনা।

    Boundary Value Analysis (BVA) কীভাবে কাজ করে:

    মূলনীতি: প্রোগ্রামারের ভুল সবচেয়ে বেশি ঘটে সীমানায় — যেমন < এর জায়গায় <= লেখা, বা লুপে একবার কম বা বেশি চালানো। তাই পরিসরের মাঝখানের মান নয়, সীমানার মানগুলোই সবচেয়ে বেশি ত্রুটি ধরিয়ে দেয়।

    পদ্ধতি: প্রতিটি ইনপুট পরিসরের জন্য পাঁচটি মান পরীক্ষা করা হয় —
    - সর্বনিম্ন সীমার ঠিক নিচে (min - 1)
    - সর্বনিম্ন সীমা (min)
    - মাঝামাঝি একটি স্বাভাবিক মান
    - সর্বোচ্চ সীমা (max)
    - সর্বোচ্চ সীমার ঠিক উপরে (max + 1)

    উদাহরণ: একটি ব্যবস্থা ১৮ থেকে ৬০ বছর বয়সের আবেদন গ্রহণ করে।
    BVA অনুযায়ী টেস্ট কেস: ১৭, ১৮, ৩৯, ৬০, ৬১।
    - ১৭ প্রত্যাখ্যাত হওয়া উচিত
    - ১৮ গ্রহণ করা উচিত
    - ৬০ গ্রহণ করা উচিত
    - ৬১ প্রত্যাখ্যাত হওয়া উচিত
    কোডে যদি ভুল করে `if (age > 18)` লেখা হতো, তবে ১৮ প্রত্যাখ্যাত হতো এবং এই টেস্টেই তা ধরা পড়ত। মাঝখানের ৩৯ দিয়ে পরীক্ষা করলে ভুলটি কখনোই ধরা পড়ত না।

    Equivalence Partitioning কীভাবে কাজ করে:

    মূলনীতি: ইনপুটের সম্পূর্ণ পরিসরকে এমন কয়েকটি শ্রেণিতে ভাগ করা যায়, যেখানে একটি শ্রেণির যেকোনো মান দিলে প্রোগ্রাম একইভাবে আচরণ করবে। তাই প্রতিটি শ্রেণি থেকে একটি মান পরীক্ষা করলেই ওই পুরো শ্রেণিটি পরীক্ষিত হয়ে যায়।

    পদ্ধতি:
    - ইনপুটকে বৈধ শ্রেণি (valid equivalence class) ও অবৈধ শ্রেণিতে (invalid equivalence class) ভাগ করা।
    - প্রতিটি শ্রেণি থেকে একটি প্রতিনিধিত্বমূলক মান নির্বাচন করা।
    - প্রতিটি অবৈধ শ্রেণি আলাদাভাবে পরীক্ষা করা, কারণ একটি টেস্টে একাধিক অবৈধ মান দিলে প্রোগ্রাম প্রথমটিতেই থেমে যেতে পারে এবং বাকিগুলো পরীক্ষিত হবে না।

    উদাহরণ: একই ১৮ থেকে ৬০ বয়সের ক্ষেত্রে তিনটি শ্রেণি —
    - অবৈধ শ্রেণি ১: ১৮ এর নিচে → প্রতিনিধি মান ১০
    - বৈধ শ্রেণি: ১৮ থেকে ৬০ → প্রতিনিধি মান ৩৫
    - অবৈধ শ্রেণি ২: ৬০ এর উপরে → প্রতিনিধি মান ৭০
    মাত্র তিনটি টেস্ট কেসেই সমগ্র পূর্ণসংখ্যা পরিসর ঢেকে যায়।

    দুটির সমন্বয়: বাস্তবে দুটি কৌশল একসঙ্গে ব্যবহার করা হয়। Equivalence Partitioning ঠিক করে কতগুলো শ্রেণি পরীক্ষা করতে হবে, আর BVA ঠিক করে প্রতিটি শ্রেণির কোন মানগুলো বেছে নিতে হবে। উপরের উদাহরণে সম্মিলিত টেস্ট কেস হবে: ১০, ১৭, ১৮, ৩৫, ৬০, ৬১, ৭০।

    সুবিধা: অসীম সংখ্যক সম্ভাব্য ইনপুটকে অল্প কয়েকটি টেস্ট কেসে নামিয়ে আনা যায়, অথচ ত্রুটি ধরার সম্ভাবনা সর্বোচ্চ থাকে। এ কারণেই এই দুটি কৌশল black box testing এর সবচেয়ে মৌলিক ও বহুল ব্যবহৃত পদ্ধতি।
22. **(খ) Quality Control কাকে বলে? Quality review process কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*


    Answer:

    Quality Control কাকে বলে:

    Quality Control (QC) বলতে বোঝায় তৈরি হওয়া পণ্য পরীক্ষা করে ত্রুটি শনাক্ত করা এবং তা নির্ধারিত মান পূরণ করছে কিনা তা যাচাই করার কার্যক্রম। এটি পণ্যকেন্দ্রিক ও সংশোধনমূলক: ত্রুটি ঘটে যাওয়ার পর তা খুঁজে বের করে সারানো এর কাজ।

    Quality Assurance এর সঙ্গে পার্থক্য:

    | বিষয় | Quality Assurance (QA) | Quality Control (QC) |
    |---|---|---|
    | কেন্দ্রবিন্দু | প্রক্রিয়া | পণ্য |
    | প্রকৃতি | প্রতিরোধমূলক | সংশোধনমূলক |
    | প্রশ্ন | সঠিক প্রক্রিয়া অনুসরণ হচ্ছে কি? | পণ্যটি কি ত্রুটিমুক্ত? |
    | কখন | পুরো জীবনচক্রজুড়ে | পণ্য বা অংশ তৈরির পর |
    | দায়িত্ব | পুরো দলের | পরীক্ষক দলের |
    | কার্যক্রম | মান নির্ধারণ, প্রক্রিয়া নিরীক্ষা, প্রশিক্ষণ | পরীক্ষা, পরিদর্শন, পর্যালোচনা |
    | উদাহরণ | কোডিং স্ট্যান্ডার্ড তৈরি ও প্রয়োগ | টেস্ট চালিয়ে ত্রুটি খোঁজা |

    সংক্ষেপে: QA ত্রুটি প্রতিরোধ করে, QC ত্রুটি শনাক্ত করে, আর Testing হলো QC এর প্রধান কৌশল।

    Quality Review Process কীভাবে কাজ করে:

    Quality review হলো একটি আনুষ্ঠানিক প্রক্রিয়া, যেখানে একদল ব্যক্তি কোনো কাজের ফল (নথি, নকশা বা কোড) পরীক্ষা করে ত্রুটি ও মান লঙ্ঘন খুঁজে বের করেন। এর সবচেয়ে গুরুত্বপূর্ণ বৈশিষ্ট্য হলো এটি স্থির (static): সফটওয়্যার চালানোর প্রয়োজন হয় না, তাই কোড লেখার আগেই প্রয়োজনীয়তা ও নকশার ত্রুটি ধরা যায়।

    ধাপসমূহ:

    ১. পরিকল্পনা (Planning):
    - কোন কাজের ফল পর্যালোচনা করা হবে তা নির্বাচন করা।
    - Moderator নিয়োগ, পর্যালোচক দল গঠন এবং প্রবেশের শর্ত (entry criteria) যাচাই করা।
    - চেকলিস্ট ও মানদণ্ড ঠিক করা।

    ২. প্রস্তুতি ও কিক-অফ (Kick-off):
    - পর্যালোচকদের নথি ও চেকলিস্ট আগেই বিতরণ করা।
    - পর্যালোচনার উদ্দেশ্য ও ভূমিকা বুঝিয়ে দেওয়া।

    ৩. ব্যক্তিগত প্রস্তুতি (Individual Preparation):
    - প্রত্যেক পর্যালোচক আলাদাভাবে নথিটি পড়েন এবং সম্ভাব্য ত্রুটি লিখে রাখেন।
    - এটিই সবচেয়ে গুরুত্বপূর্ণ ধাপ; গবেষণা বলছে বেশিরভাগ ত্রুটি সভায় নয়, এই একক প্রস্তুতিতেই আবিষ্কৃত হয়।

    ৪. পর্যালোচনা সভা (Review Meeting):
    - Moderator সভা পরিচালনা করেন, Reader নথিটি অংশে অংশে উপস্থাপন করেন এবং Recorder ত্রুটিগুলো লিপিবদ্ধ করেন।
    - মূল নিয়ম: ত্রুটি শনাক্ত করা হয়, সমাধান আলোচনা করা হয় না। সমাধান আলোচনা শুরু হলে সভা দীর্ঘ হয় এবং বাকি অংশ পর্যালোচিত হয় না।
    - আরেকটি মূল নিয়ম: আলোচনা নথির ওপর, লেখকের ওপর নয়। ব্যক্তিগত সমালোচনা হলে ভবিষ্যতে কেউ আর নিজের কাজ পর্যালোচনায় দিতে চাইবেন না।

    ৫. সংশোধন (Rework):
    - লেখক লিপিবদ্ধ ত্রুটিগুলো সংশোধন করেন।

    ৬. অনুসরণ (Follow-up):
    - Moderator যাচাই করেন সব ত্রুটি সংশোধিত হয়েছে কিনা এবং প্রস্থানের শর্ত (exit criteria) পূরণ হয়েছে কিনা।
    - প্রয়োজনে আবার পর্যালোচনা করা হয়।

    ভূমিকাসমূহ: Moderator (পরিচালনা ও নিরপেক্ষতা রক্ষা), Author (লেখক), Reader (উপস্থাপক), Recorder (লিপিকার), Reviewers (পর্যালোচক)।

    পর্যালোচনার প্রকারভেদ, আনুষ্ঠানিকতার ক্রমানুসারে:
    - Informal review: সহকর্মীকে দিয়ে পড়িয়ে নেওয়া, কোনো নথি নেই।
    - Walkthrough: লেখক নিজেই দলকে নথির মধ্য দিয়ে নিয়ে যান, মূলত বোঝানো ও মতামত সংগ্রহের জন্য।
    - Technical review: বিশেষজ্ঞ দল কারিগরি সিদ্ধান্তগুলো যাচাই করে।
    - Inspection: সবচেয়ে আনুষ্ঠানিক; নির্দিষ্ট ভূমিকা, চেকলিস্ট, পরিমাপ ও লিখিত প্রতিবেদনসহ। Fagan inspection পদ্ধতিতে উপস্থিত ত্রুটির ৬০ থেকে ৯০ শতাংশ পর্যন্ত ধরা পড়ে।

    কেন এটি কার্যকর:
    - কোড চালানোর আগেই ত্রুটি ধরা পড়ে, তাই সারানোর খরচ সবচেয়ে কম।
    - প্রয়োজনীয়তা ও নকশার ত্রুটি টেস্টিং দিয়ে ধরা যায় না, কেবল পর্যালোচনাতেই ধরা যায়।
    - জ্ঞান দলের মধ্যে ছড়িয়ে পড়ে, ফলে একজন চলে গেলেও কাজ থেমে থাকে না।
    - নতুন সদস্যরা দ্রুত শেখেন এবং মান একরকম থাকে।
23. **What is black box testing? Consider a program which computes the square root of an input integer between 0 and 5000. Determine the equivalence class test cases. Determine the test cases using boundary value analysis also.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*


    Answer: Black box testing is a technique in which the tester has no knowledge of the internal code and derives the test cases entirely from the specification, treating the program as an opaque box: inputs are supplied and outputs are compared with what the specification says they should be.

    The problem: a program computes the square root of an input integer between 0 and 5000.

    Equivalence class test cases:

    Equivalence partitioning divides the input domain into classes within which the program is expected to behave identically, so that testing one value from each class is enough.

    Identifying the classes:

    | Class | Description | Valid or invalid | Representative value | Expected result |
    |---|---|---|---|---|
    | EC1 | Integers below 0 | Invalid | -25 | Error message: input out of range |
    | EC2 | Integers from 0 to 5000 | Valid | 2500 | 50 |
    | EC3 | Integers above 5000 | Invalid | 7500 | Error message: input out of range |
    | EC4 | Non-integer numeric input | Invalid | 25.7 | Error message: integer required |
    | EC5 | Non-numeric input | Invalid | abc | Error message: numeric input required |
    | EC6 | Empty input | Invalid | (blank) | Error message: input required |

    The first three classes are the ones the question is chiefly asking for; the last three should be mentioned because a real specification implies them and a good tester does not assume the input will always be an integer.

    Rule to note: each invalid class is tested in a separate test case. If two invalid values were supplied together, the program might reject the first and never reach the check for the second, so the second would not actually have been tested.

    Test cases from equivalence partitioning:

    | Case | Input | Expected output |
    |---|---|---|
    | TC1 | -25 | Error: out of range |
    | TC2 | 2500 | 50 |
    | TC3 | 7500 | Error: out of range |
    | TC4 | 25.7 | Error: integer required |
    | TC5 | abc | Error: numeric input required |
    | TC6 | (blank) | Error: input required |

    Boundary value analysis test cases:

    Boundary value analysis tests the values at and immediately around the edges of each valid range, because that is where programmers most often make mistakes, typically by writing < where <= was meant.

    For the valid range 0 to 5000, the boundary values are:

    | Case | Input | Position | Expected output |
    |---|---|---|---|
    | BVA1 | -1 | Just below the minimum | Error: out of range |
    | BVA2 | 0 | Minimum | 0 |
    | BVA3 | 1 | Just above the minimum | 1 |
    | BVA4 | 2500 | A middle value | 50 |
    | BVA5 | 4999 | Just below the maximum | 70.70 (approximately) |
    | BVA6 | 5000 | Maximum | 70.71 (approximately) |
    | BVA7 | 5001 | Just above the maximum | Error: out of range |

    The standard forms of the technique:
    - Two-value BVA tests min, min-1, max and max+1: four cases.
    - Three-value BVA tests min-1, min, min+1, max-1, max and max+1: six cases, and this is the form used above.

    Additional values worth testing, which show understanding beyond the mechanical technique:
    - Perfect squares: 1, 4, 9, 16, 25, 100, 4900. These should return exact integers, and rounding errors are visible here.
    - Non-perfect squares: 2, 3, 5, 50. These test the precision and the rounding of the result. What does the specification say the result of sqrt(2) should be, and to how many decimal places?
    - 0, which is a boundary and also a mathematically special case.
    - A very large valid value, 5000, to confirm that no overflow occurs in the algorithm.

    Why both techniques are used together: equivalence partitioning decides how many classes must be covered and reduces an effectively infinite input domain to a handful of classes; boundary value analysis decides which particular value to pick from each class, choosing the values most likely to expose a defect. Combining them gives the greatest chance of finding defects for the smallest number of test cases, which is the definition of effective testing.

    Combined minimal test set: -1, 0, 1, 2500, 4999, 5000, 5001, together with 25.7, abc and a blank input.
24. **Definition of Gray-box testing and Unit testing.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*


    Answer:

    Grey-box testing:

    Grey-box testing (also spelled gray-box) is a testing technique in which the tester has partial knowledge of the internal structure of the application, but not the complete source code. It combines the strengths of black box and white box testing.

    What the tester typically knows:
    - The architecture and the main components
    - The database schema
    - The API contracts and the data formats exchanged
    - The algorithms used at a high level
    but not the line-by-line implementation.

    How it is used:
    - Test cases are designed from the specification, as in black box testing, but the partial internal knowledge is used to choose the cases more intelligently and to verify results more deeply. A tester who knows the database schema can, after submitting a form, query the database directly to confirm that the record was written correctly, which a pure black box tester could not do.
    - It is the normal technique in integration testing, web application testing, security testing and penetration testing.

    Advantages:
    - It gives the user's perspective of black box testing together with the targeted coverage of white box testing.
    - It is unbiased: the tester is not the developer, so the developer's assumptions are not repeated.
    - It is more efficient than black box testing, because knowledge of the internals guides the choice of cases.
    - It is well suited to distributed systems, where the internals of one service are known and those of another are not.

    Disadvantages:
    - Complete code coverage cannot be measured or guaranteed, since the code is not fully visible.
    - It is less effective than white box testing for finding deep logic errors.
    - It requires more skill than pure black box testing.

    | Point | Black box | Grey box | White box |
    |---|---|---|---|
    | Knowledge of internals | None | Partial | Full |
    | Performed by | Testers and users | Testers with technical knowledge | Developers |
    | Level | System and acceptance | Integration | Unit |
    | Coverage measurable | No | Partly | Yes |

    Unit testing:

    Unit testing is the testing of the smallest testable component of a software system, that is a single function, method, procedure or class, in isolation from the rest of the system, to confirm that it behaves correctly on its own.

    Characteristics:
    - Performed by the developer who wrote the code, usually as the code is written.
    - It is white box testing: the internal logic is known and is used to design the cases.
    - Dependencies are replaced by stubs, mocks or fakes, so that the unit is genuinely tested alone and a failure can be attributed to it with certainty.
    - It is the first and lowest level of testing, preceding integration testing.
    - Unit tests are fast: thousands can run in seconds, which is what makes them practical to run on every change.

    Example in Java with JUnit:
    ```java
    public class Calculator {
        public int divide(int a, int b) {
            if (b == 0) throw new ArithmeticException("Division by zero");
            return a / b;
        }
    }

    public class CalculatorTest {
        @Test
        public void testDivideNormal() {
            assertEquals(5, new Calculator().divide(10, 2));
        }

        @Test
        public void testDivideNegative() {
            assertEquals(-5, new Calculator().divide(-10, 2));
        }

        @Test
        public void testDivideByZero() {
            assertThrows(ArithmeticException.class,
                         () -> new Calculator().divide(10, 0));
        }
    }
    ```

    Advantages:
    - Defects are found at the moment they are created, when they are cheapest to fix and when the developer still has the code in mind.
    - The fault is localised precisely: a failing unit test names the unit.
    - It enables safe refactoring, because a comprehensive unit test suite tells the developer immediately if a change has broken something.
    - It serves as executable documentation of what the unit is supposed to do.
    - It is the foundation of continuous integration and of test-driven development, in which the test is written before the code.

    Limitations:
    - It cannot find integration or interface defects, since each unit is tested alone.
    - It cannot find missing requirements.
    - Writing and maintaining the tests takes effort, roughly 30 to 50 per cent additional development time, which is repaid many times over in maintenance.
    - A high number of unit tests passing does not mean the system works; it means the parts work.

    Tools: JUnit and TestNG for Java, NUnit for C#, PyTest and unittest for Python, Jest and Mocha for JavaScript, and Google Test for C++.
25. **Integration testing of pharmaceutical automation software?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*


    Answer: Integration testing of pharmaceutical automation software is the stage at which the separately developed and unit-tested components of the system are combined and the interfaces between them are verified. It is unusually important in this domain, because the components are not merely software modules but include physical machinery, laboratory instruments and regulated record-keeping, and a failure at an interface can produce a contaminated batch or a falsified record.

    The components typically integrated:
    - The Manufacturing Execution System (MES), which manages the batch record and the production workflow
    - The SCADA or process control layer and the PLCs that drive the physical equipment
    - The equipment itself: mixers, granulators, tablet presses, coating machines, filling and packaging lines
    - Laboratory instruments and the Laboratory Information Management System (LIMS)
    - The Enterprise Resource Planning system, for materials, inventory and dispatch
    - The warehouse management system and barcode or RFID scanners
    - The environmental monitoring system for temperature, humidity and differential pressure
    - The electronic batch record and the audit trail database

    What integration testing verifies in this setting:

    - Data flow across interfaces: that a batch order created in the ERP appears correctly in the MES, that the recipe parameters passed from the MES to the PLC are exactly those approved, and that the results returned by the instrument are recorded against the correct batch.
    - Units and formats: that a value expressed in kilograms on one side is not read as grams on the other. This class of interface defect is the classic cause of catastrophic failure, and it is precisely what unit testing cannot find.
    - Sequencing and interlocks: that the system will not permit the next step to begin until the previous one has been completed and verified, and that safety interlocks cannot be bypassed by any sequence of operations.
    - Alarm and exception propagation: that an out-of-specification temperature raises an alarm at every layer that needs it, that the batch is placed on hold, and that the event is written to the audit trail.
    - Recovery: that a power failure, a network interruption or an instrument fault leaves the system in a defined state, that no partial record is committed, and that the operator is told exactly what happened.
    - Timing: that the software responds within the time the physical process requires. A control decision that arrives late is a wrong decision.
    - Security and access control across systems: that an operator's privileges are consistent in every subsystem and that electronic signatures are propagated correctly.

    Approach:
    - Incremental integration is used, adding one interface at a time, because in this domain locating a fault matters more than testing quickly. Big bang integration would make a failure almost impossible to diagnose.
    - Simulators and stubs stand in for the physical equipment during early testing, since running a real tablet press for every test is impossible. The transition from simulator to real equipment is itself a test stage.
    - Both normal and abnormal paths are tested; in a regulated environment the abnormal paths matter more, because that is where records are most likely to be lost.

    The regulatory dimension, which distinguishes this from ordinary integration testing:
    - Computer System Validation (CSV) is mandatory, following GAMP 5 guidance and the ISPE V-model, in which each specification document has a corresponding qualification stage.
    - The qualification stages are Design Qualification, Installation Qualification (IQ), Operational Qualification (OQ) and Performance Qualification (PQ). Integration testing corresponds broadly to OQ.
    - 21 CFR Part 11 in the United States and Annex 11 in the European Union govern electronic records and electronic signatures. Integration testing must demonstrate that the audit trail is complete, attributable, legible, contemporaneous, original and accurate, the ALCOA principles, and that it cannot be altered.
    - Every test must be pre-approved, executed against a written protocol, and its evidence retained. An undocumented test does not exist as far as an inspector is concerned.
    - Traceability from the User Requirement Specification through the functional specification to the test case must be complete.
    - A formal risk assessment determines how much testing each interface receives, concentrating effort where patient safety or product quality is at stake.

    Practical difficulties:
    - Test data must be realistic without being real production data.
    - Physical equipment is expensive to occupy for testing, so simulator fidelity is critical.
    - Any change after validation requires formal change control and partial revalidation, which makes the cost of a late-discovered integration defect very high indeed. This is the strongest argument for thorough integration testing in this domain.
26. **(ক) Software এর \alpha-version ও \beta-version কি?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*


    Answer: Software এর Alpha-version ও Beta-version:

    Alpha version (আলফা সংস্করণ):

    - এটি সফটওয়্যারের প্রথম মোটামুটি সম্পূর্ণ সংস্করণ, যা অভ্যন্তরীণ পরীক্ষার জন্য তৈরি হয়।
    - পরীক্ষা করা হয় ডেভেলপার প্রতিষ্ঠানের নিজস্ব কর্মীদের দিয়ে, প্রতিষ্ঠানের নিজস্ব নিয়ন্ত্রিত পরিবেশে।
    - ডেভেলপাররা উপস্থিত থাকেন এবং ত্রুটি পাওয়া মাত্রই তা সংশোধন করে নতুন বিল্ড দেন।
    - এই পর্যায়ে সফটওয়্যারটি অস্থিতিশীল হতে পারে, অনেক সুবিধা অসম্পূর্ণ থাকতে পারে এবং ঘন ঘন ভেঙে পড়তে পারে।
    - Black box ও White box দুই ধরনের পরীক্ষাই করা হয়।
    - কোনো বাইরের গ্রাহককে এটি দেওয়া হয় না।
    - উদ্দেশ্য: বাইরের কেউ দেখার আগেই বড় ত্রুটিগুলো ধরে ফেলা।

    Beta version (বিটা সংস্করণ):

    - আলফা পরীক্ষা শেষে যখন সফটওয়্যারটি যথেষ্ট স্থিতিশীল হয়, তখন এটি সীমিতসংখ্যক প্রকৃত ব্যবহারকারীর হাতে দেওয়া হয়।
    - পরীক্ষা হয় ব্যবহারকারীর নিজের পরিবেশে, নিজের যন্ত্রে, প্রকৃত কাজে।
    - ডেভেলপাররা উপস্থিত থাকেন না; মতামত আসে প্রতিবেদন, জরিপ ও স্বয়ংক্রিয় তথ্য সংগ্রহের মাধ্যমে।
    - কেবল Black box পরীক্ষা হয়, কারণ ব্যবহারকারী কোড দেখেন না।
    - দুই ধরনের: Closed beta (নির্বাচিত সীমিত ব্যবহারকারী) এবং Open beta (যে কেউ অংশ নিতে পারেন)।
    - উদ্দেশ্য: এমন সমস্যা খুঁজে বের করা যা কেবল প্রকৃত ব্যবহারেই ধরা পড়ে — অপ্রত্যাশিত ব্যবহারের ধরন, বিভিন্ন যন্ত্রের সঙ্গে অসামঞ্জস্য, প্রকৃত চাপের অধীনে কর্মদক্ষতা এবং ব্যবহারযোগ্যতা সংক্রান্ত অসুবিধা।

    | Point | Alpha Testing | Beta Testing |
    |---|---|---|
    | Who tests | The organisation's own staff, typically an internal testing team and sometimes other employees who are not developers | Real external users, that is actual customers or a selected public |
    | Where | At the developer's site, in a controlled laboratory environment | At the user's own site, in the real environment |
    | When | After system testing, before beta | After alpha testing, before the general release |
    | Environment | Controlled, with the developers present | Uncontrolled and real, with all the variety of real hardware, networks and usage |
    | Developer presence | Present, and can observe and fix problems immediately | Absent; feedback is collected through reports and telemetry |
    | Type of testing | Both white box and black box may be used | Black box only |
    | Purpose | To find defects before the software is exposed to any outsider | To discover problems that only real use reveals, and to gather usability and acceptance feedback |
    | Reliability required | The product may still be unstable | The product must be reasonably stable |
    | Duration | Weeks, in cycles | Weeks to months |
    | Issues found | Functional and logical defects | Usability problems, unexpected usage patterns, compatibility with real hardware and configurations, scalability under real load |
    | Fixing | Defects can be fixed during the test cycle | Defects are usually deferred to a later release |
    | Also called | In-house acceptance testing | Field testing, external user acceptance testing, pre-release testing |

    Both are forms of acceptance testing, which is the final level of testing before release.

    Gamma testing: a less standard term, used for the final check made when the software is considered complete and only a limited set of critical checks is repeated before shipping, with no further feature changes. Some organisations use it to mean a release candidate check. It is not part of the standard ISTQB terminology, and an answer should say so rather than invent a definition.

    Practical illustration: a mobile banking application is first tested in the bank's own laboratory by its testing team (alpha), then released to two thousand selected customers who use it for real transactions on their own phones for a month (beta), and only then published to all customers.

    সংস্করণের ধারাবাহিকতা: Pre-alpha (উন্নয়নাধীন) → Alpha (অভ্যন্তরীণ পরীক্ষা) → Beta (বাহ্যিক পরীক্ষা) → Release Candidate (প্রায় চূড়ান্ত, কেবল গুরুতর ত্রুটি থাকলে সংশোধন) → Release to Manufacturing / General Availability (চূড়ান্ত প্রকাশ)।

    বাস্তব উদাহরণ: একটি মোবাইল ব্যাংকিং অ্যাপ প্রথমে ব্যাংকের নিজস্ব পরীক্ষাগারে তাদের কর্মীরা পরীক্ষা করেন (আলফা), তারপর দুই হাজার নির্বাচিত গ্রাহককে দেওয়া হয় যাঁরা এক মাস ধরে নিজেদের ফোনে প্রকৃত লেনদেন করেন (বিটা), এবং তার পরেই সবার জন্য প্রকাশ করা হয়।
27. **(গ) Unit testing, Integration testing এবং Beta testing বলতে কি বুঝায়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*


    Answer:

    Unit Testing:

    Unit testing হলো সফটওয়্যারের ক্ষুদ্রতম পরীক্ষণযোগ্য অংশ — একটি ফাংশন, মেথড বা ক্লাস — আলাদাভাবে পরীক্ষা করা, যাতে নিশ্চিত হওয়া যায় যে অংশটি নিজে থেকে সঠিকভাবে কাজ করছে।

    - কে করেন: যে ডেভেলপার কোডটি লিখেছেন, সাধারণত লেখার সঙ্গে সঙ্গেই।
    - পদ্ধতি: White box, অর্থাৎ অভ্যন্তরীণ কোড জেনে পরীক্ষা করা হয়।
    - বিচ্ছিন্নতা: অন্য অংশের ওপর নির্ভরতা stub, mock বা fake দিয়ে প্রতিস্থাপন করা হয়, যাতে ব্যর্থতার দায় নিশ্চিতভাবে ওই ইউনিটের ওপরই বর্তায়।
    - গতি: অত্যন্ত দ্রুত; হাজার হাজার ইউনিট টেস্ট কয়েক সেকেন্ডে চলে, তাই প্রতিটি পরিবর্তনের পর চালানো ব্যবহারিক।
    - সরঞ্জাম: JUnit (Java), NUnit (C#), PyTest (Python), Jest (JavaScript)।
    - সুবিধা: ত্রুটি জন্মানোর মুহূর্তেই ধরা পড়ে, ত্রুটির অবস্থান সুনির্দিষ্টভাবে জানা যায়, এবং নির্ভয়ে refactoring করা যায়।

    Integration Testing:

    Integration testing হলো ইতোমধ্যে ইউনিট-পরীক্ষিত দুই বা ততোধিক অংশ একত্র করে তাদের মধ্যকার ইন্টারফেস ও পারস্পরিক ক্রিয়া পরীক্ষা করা।

    - উদ্দেশ্য: অংশগুলো একসঙ্গে ঠিকভাবে কাজ করছে কিনা এবং তাদের মধ্যে তথ্য সঠিকভাবে আদান-প্রদান হচ্ছে কিনা তা যাচাই করা।
    - কখন: ইউনিট টেস্টিংয়ের পর, সিস্টেম টেস্টিংয়ের আগে।
    - কী ধরনের ত্রুটি ধরা পড়ে: ইন্টারফেসের অমিল, ভুল ক্রমে প্যারামিটার পাঠানো, ভুল ডেটা ফরম্যাট, একক (unit) এর অসঙ্গতি (যেমন এক পাশে টাকা, অন্য পাশে পয়সা), এবং মডিউলের মধ্যে ত্রুটি সামলানোর অভাব।
    - পদ্ধতিসমূহ:
      - Big bang: সব মডিউল একসঙ্গে জুড়ে দেওয়া। সহজ, কিন্তু ত্রুটির অবস্থান খুঁজে বের করা কঠিন।
      - Top-down: উপরের মডিউল আগে, নিচেরগুলোর জায়গায় stub ব্যবহার করে।
      - Bottom-up: নিচের মডিউল আগে, উপরেরগুলোর জায়গায় driver ব্যবহার করে।
      - Sandwich বা hybrid: দুটির সমন্বয়।
      - Incremental: একটি একটি করে মডিউল যোগ করে প্রতিবার পরীক্ষা করা; ত্রুটির অবস্থান খুঁজে পাওয়া সবচেয়ে সহজ।
    - Stub হলো এমন একটি কৃত্রিম মডিউল, যা এখনো তৈরি না হওয়া অধীনস্থ মডিউলের জায়গা নেয়; Driver হলো এমন একটি কৃত্রিম মডিউল, যা পরীক্ষাধীন মডিউলটিকে ডাকে।

    Beta Testing:

    Beta testing হলো গ্রহণযোগ্যতা পরীক্ষার দ্বিতীয় পর্যায়, যেখানে প্রায়-চূড়ান্ত সফটওয়্যারটি সীমিতসংখ্যক প্রকৃত ব্যবহারকারীর হাতে দেওয়া হয়, এবং তাঁরা নিজেদের পরিবেশে নিজেদের প্রকৃত কাজে সেটি ব্যবহার করেন।

    - কে করেন: প্রকৃত বাইরের ব্যবহারকারী বা গ্রাহক, প্রতিষ্ঠানের কর্মী নন।
    - কোথায়: ব্যবহারকারীর নিজের স্থানে, প্রকৃত ও অনিয়ন্ত্রিত পরিবেশে।
    - ডেভেলপার উপস্থিত থাকেন না; মতামত আসে প্রতিবেদন ও স্বয়ংক্রিয় তথ্যের মাধ্যমে।
    - পদ্ধতি: কেবল black box।
    - দুই ধরনের: Closed beta (আমন্ত্রিত সীমিত ব্যবহারকারী) ও Open beta (সবার জন্য উন্মুক্ত)।
    - কী ধরনের সমস্যা ধরা পড়ে: ব্যবহারযোগ্যতার অসুবিধা, অপ্রত্যাশিত ব্যবহারের ধরন, বিভিন্ন যন্ত্র ও সংস্করণের সঙ্গে অসামঞ্জস্য, এবং প্রকৃত চাপের অধীনে কর্মদক্ষতার সমস্যা — যেগুলোর কোনোটিই নিয়ন্ত্রিত পরীক্ষাগারে ধরা পড়ে না।
    - পাওয়া ত্রুটি সাধারণত পরবর্তী সংস্করণে সংশোধনের জন্য রেখে দেওয়া হয়।

    তিনটির সম্পর্ক: এগুলো পরীক্ষণের ক্রমবর্ধমান স্তর। Unit testing একটি অংশ পরীক্ষা করে, Integration testing অংশগুলোর সংযোগ পরীক্ষা করে, System testing সম্পূর্ণ ব্যবস্থা পরীক্ষা করে, আর Acceptance testing (যার অংশ Alpha ও Beta) যাচাই করে ব্যবস্থাটি গ্রাহকের প্রকৃত প্রয়োজন মেটায় কিনা। পরিধি ক্রমশ বাড়ে এবং দায়িত্ব ডেভেলপার থেকে গ্রাহকের দিকে সরে যায়।
28. **(i) Black Box testing and White Box testing এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*


    Answer: | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.
29. **(a) Distinguish between black box and white box testing. Give examples of both type of testing** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*


    Answer: | Point | Black Box Testing | White Box Testing |
    |---|---|---|
    | Also called | Functional, behavioural, closed box, specification-based testing | Structural, glass box, clear box, open box, code-based testing |
    | Knowledge of the code | None; only the specification is used | Full knowledge of the internal structure and source code |
    | Basis of test cases | The requirements and the expected input-output behaviour | The control flow, the data flow and the code paths |
    | Performed by | Independent testers, and by end users during acceptance testing | Developers and testers who can read code |
    | Level applied | Mainly system and acceptance testing | Mainly unit and integration testing |
    | Programming knowledge | Not required | Essential |
    | What it finds | Missing or incorrect functionality, interface errors, wrong behaviour at boundaries | Logic errors, dead code, uncovered paths, incorrect conditions, poor error handling |
    | What it misses | Hidden logic errors and untested paths inside the code | Missing requirements, because it can only test what was written, not what should have been written |
    | Coverage measurement | Not possible in terms of code | Measurable: statement, branch, condition and path coverage |
    | Techniques | Equivalence partitioning, boundary value analysis, decision tables, state transition testing, error guessing, use case testing | Statement coverage, branch coverage, path coverage, condition coverage, loop testing, cyclomatic complexity |
    | Time and cost | Less time to design, since the code need not be studied | More time, since the code must be analysed |
    | Automation | Through tools such as Selenium and JMeter | Through unit test frameworks such as JUnit with coverage tools such as JaCoCo |
    | Analogy | Testing a car by driving it | Testing a car by opening the bonnet and inspecting the engine |

    Grey box testing lies between the two: the tester has partial knowledge of the internals, for example the database schema or the architecture, but not the full source. It is common in integration and security testing.

    Both are necessary. White box confirms that the code does what it says; black box confirms that it does what the customer asked for. A program can pass one and fail the other.

    Example of black box testing:

    A function accepts a percentage mark from 0 to 100 and returns a grade. The tester knows only this specification.
    - Equivalence partitioning: valid class 0 to 100, invalid classes below 0 and above 100. Test with -5, 55 and 105.
    - Boundary value analysis: test with -1, 0, 1 and 99, 100, 101, since errors cluster at boundaries.
    - Decision table: for each grade band, one representative value: 85 for A+, 70 for A, 50 for B, 30 for F.
    - Error guessing: a blank input, a letter instead of a number, a decimal such as 59.5.

    Example of white box testing:

    ```java
    String grade(int marks) {
        if (marks >= 80)      return "A+";
        else if (marks >= 60) return "A";
        else if (marks >= 40) return "Pass";
        else                  return "Fail";
    }
    ```
    Reading the code, the tester designs the minimum set of cases that covers every branch: 85, 70, 50 and 30, giving 100 per cent branch coverage with four tests. The tester also notices that the code accepts 150 and returns A+, and that it accepts -20 and returns Fail, neither of which the specification permits. This defect is visible from the code but might never be guessed from the specification alone, which illustrates exactly why both techniques are used.
30. **Software development এ Black Box Testing বলতে কি বুঝায়?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*


    Answer: Black Box Testing বলতে বোঝায় এমন পরীক্ষণ পদ্ধতি, যেখানে পরীক্ষক সফটওয়্যারের অভ্যন্তরীণ গঠন, নকশা বা সোর্স কোড সম্পর্কে কিছুই জানেন না। তিনি সফটওয়্যারটিকে একটি বন্ধ বাক্স হিসেবে দেখেন, নির্দিষ্ট ইনপুট দেন এবং প্রাপ্ত আউটপুট প্রত্যাশিত আউটপুটের সঙ্গে মিলিয়ে দেখেন। টেস্ট কেসগুলো তৈরি হয় কেবল স্পেসিফিকেশন বা প্রয়োজনীয়তার নথি থেকে।

    অন্য নাম: Functional testing, Behavioural testing, Specification-based testing, Closed box testing।

    কে করেন: স্বাধীন পরীক্ষক দল, এবং গ্রহণযোগ্যতা পরীক্ষার সময় প্রকৃত ব্যবহারকারীরা। প্রোগ্রামিং জ্ঞান আবশ্যক নয়।

    কোন স্তরে প্রয়োগ হয়: প্রধানত System testing ও Acceptance testing স্তরে।

    প্রধান কৌশলসমূহ:

    - Equivalence Partitioning: ইনপুটের পরিসরকে এমন শ্রেণিতে ভাগ করা, যেখানে একটি শ্রেণির সব মান একইভাবে আচরণ করবে বলে ধরে নেওয়া যায়। প্রতিটি শ্রেণি থেকে একটি করে মান পরীক্ষা করলেই যথেষ্ট। যেমন বয়স ১৮ থেকে ৬০ গ্রহণযোগ্য হলে তিনটি শ্রেণি: ১৮ এর নিচে (অবৈধ), ১৮ থেকে ৬০ (বৈধ), ৬০ এর উপরে (অবৈধ)। মাত্র তিনটি টেস্ট কেসেই পুরো পরিসর ঢেকে যায়।

    - Boundary Value Analysis: সীমানার ঠিক আগে, সীমানায় এবং সীমানার ঠিক পরে পরীক্ষা করা, কারণ প্রোগ্রামারের ভুল প্রায়ই সীমানাতেই ঘটে (যেমন < এর জায়গায় <= লেখা)। উপরের উদাহরণে: ১৭, ১৮, ১৯ এবং ৫৯, ৬০, ৬১।

    - Decision Table Testing: একাধিক শর্তের সব সম্ভাব্য সমন্বয় এবং প্রতিটির প্রত্যাশিত ফল সারণিতে সাজিয়ে পরীক্ষা করা। জটিল ব্যবসায়িক নিয়মের জন্য উপযুক্ত।

    - State Transition Testing: ব্যবস্থার বিভিন্ন অবস্থা ও তাদের মধ্যে পরিবর্তন পরীক্ষা করা। যেমন এটিএমে পিন ভুল দিলে কী হয়, তিনবার ভুল দিলে কী হয়।

    - Use Case Testing: ব্যবহারকারীর বাস্তব কর্মপ্রবাহ অনুসরণ করে পরীক্ষা করা।

    - Error Guessing: অভিজ্ঞতার ভিত্তিতে অনুমান করা কোথায় ত্রুটি থাকতে পারে — যেমন খালি ইনপুট, শূন্য, ঋণাত্মক সংখ্যা, অতিরিক্ত দীর্ঘ লেখা, বিশেষ অক্ষর।

    সুবিধা:
    - পরীক্ষক ব্যবহারকারীর দৃষ্টিকোণ থেকে দেখেন, তাই প্রকৃত ব্যবহারে যেসব সমস্যা হবে সেগুলো ধরা পড়ে।
    - প্রোগ্রামিং জ্ঞান ছাড়াই করা যায়, তাই ব্যবসায়িক বিশেষজ্ঞরাও অংশ নিতে পারেন।
    - স্পেসিফিকেশন চূড়ান্ত হলেই টেস্ট কেস লেখা শুরু করা যায়, কোড লেখার অপেক্ষা করতে হয় না।
    - পরীক্ষক ও ডেভেলপার আলাদা হওয়ায় নিরপেক্ষতা বজায় থাকে।
    - বড় সিস্টেমেও কার্যকর।

    অসুবিধা:
    - কোডের ভেতরের লুকানো যুক্তিগত ত্রুটি ও অব্যবহৃত কোড ধরা পড়ে না।
    - কোড কভারেজ মাপা যায় না, তাই কতটুকু পরীক্ষা হলো তা নিশ্চিত করে বলা যায় না।
    - একই ইনপুট অজান্তে বারবার পরীক্ষা হতে পারে, আবার কিছু পথ কখনোই পরীক্ষা না হতে পারে।
    - স্পেসিফিকেশন অস্পষ্ট বা অসম্পূর্ণ হলে টেস্ট কেসও অসম্পূর্ণ হবে।

    White box testing এর সঙ্গে সম্পর্ক: White box testing এ কোড দেখে প্রতিটি শাখা ও পথ পরীক্ষা করা হয়। দুটিই প্রয়োজন — Black box নিশ্চিত করে সফটওয়্যারটি যা করার কথা তা করছে, আর White box নিশ্চিত করে কোডটি যা লেখা হয়েছে তা ঠিকভাবে চলছে। দুইয়ের মাঝামাঝি অবস্থান Grey box testing এর, যেখানে পরীক্ষক আংশিক অভ্যন্তরীণ জ্ঞান রাখেন।
31. **Briefly describe Unit testing, Smoke testing and Stress testing in software engineering.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*


    Answer:

    Unit testing:

    Unit testing is the testing of the smallest testable component of a system, a single function, method or class, in isolation from everything else, to confirm that it behaves correctly on its own.

    - Performed by the developer who wrote the code, as the code is written.
    - It is white box testing: the internal logic is known and used to design the cases.
    - Dependencies are replaced by stubs or mocks, so that a failure can be attributed with certainty to the unit under test.
    - It is extremely fast; thousands of unit tests run in seconds, which is what makes it practical to run them on every change.
    - Tools: JUnit, NUnit, PyTest, Jest.
    - Value: defects are found at the moment they are created, when they are cheapest to fix; the fault is precisely localised; and a good unit test suite makes refactoring safe, because a broken change is reported immediately.
    - Limitation: it cannot find interface or integration defects, nor missing requirements.

    Smoke testing:

    Smoke testing is a quick, shallow set of checks on the most critical functions of a new build, carried out to decide whether the build is stable enough to justify further testing.

    - Also called build verification testing or a confidence test.
    - Performed immediately after every new build is deployed to the test environment, before the detailed testing begins.
    - It is broad but shallow: it touches many functions but tests none of them deeply. For a banking application it would check that the application starts, that a user can log in, that the account list loads and that a transfer screen opens, without testing the details of any of these.
    - If the smoke test fails, the build is rejected and returned to the developers at once, and no further testing time is wasted on it. This is its whole purpose.
    - It is usually automated and forms part of the continuous integration pipeline, so that every commit is smoke tested within minutes.
    - The name comes from hardware testing: switch the device on and see whether smoke comes out.

    Distinction from sanity testing, which is frequently asked alongside: smoke testing is broad and shallow across the whole build; sanity testing is narrow and deep on one specific area after a fix, to check that the fix worked and that its immediate surroundings still function. Smoke is normally scripted and automated; sanity is usually unscripted.

    Stress testing:

    Stress testing is a non-functional testing technique in which the system is deliberately subjected to a load beyond its specified limits, in order to find its breaking point and to observe how it behaves when it fails.

    - Purpose: not to confirm that the system works under normal load, which is load testing, but to discover where and how it stops working, and whether it fails gracefully.
    - Method: increase the number of concurrent users, the transaction rate or the data volume beyond the design limit; or restrict a resource, by reducing available memory, disk space or network bandwidth, or by removing a server from the cluster.
    - What is observed: the point at which response times become unacceptable; whether the system degrades gradually or collapses suddenly; whether it corrupts data when it fails; whether it produces a clear error message rather than crashing; and, above all, whether it recovers correctly when the load is removed. This last point is called recovery testing and is the most valuable outcome.
    - Example: a mobile banking application designed for ten thousand concurrent users is driven to twenty, thirty and fifty thousand, to find where it breaks and to ensure that it rejects excess requests cleanly rather than losing transactions.
    - Tools: JMeter, LoadRunner, Gatling, Locust.

    Distinction from load testing: load testing applies the expected peak load and confirms that the performance targets are met; stress testing deliberately exceeds that load to find the limit. Related forms are spike testing, a sudden surge; endurance or soak testing, a sustained load over many hours to reveal memory leaks; and scalability testing, which measures how performance changes as resources are added.

    Where each fits in the process: unit testing during development, smoke testing immediately after each build, and stress testing after the system is functionally stable, as part of non-functional system testing.
32. **Write different between Alpha and Beta testing.** *[BREB Assistant General Manager (IT) 2021 compact it 933-934 (ET: N/A)]*


    Answer: | Point | Alpha Testing | Beta Testing |
    |---|---|---|
    | Who tests | The organisation's own staff, typically an internal testing team and sometimes other employees who are not developers | Real external users, that is actual customers or a selected public |
    | Where | At the developer's site, in a controlled laboratory environment | At the user's own site, in the real environment |
    | When | After system testing, before beta | After alpha testing, before the general release |
    | Environment | Controlled, with the developers present | Uncontrolled and real, with all the variety of real hardware, networks and usage |
    | Developer presence | Present, and can observe and fix problems immediately | Absent; feedback is collected through reports and telemetry |
    | Type of testing | Both white box and black box may be used | Black box only |
    | Purpose | To find defects before the software is exposed to any outsider | To discover problems that only real use reveals, and to gather usability and acceptance feedback |
    | Reliability required | The product may still be unstable | The product must be reasonably stable |
    | Duration | Weeks, in cycles | Weeks to months |
    | Issues found | Functional and logical defects | Usability problems, unexpected usage patterns, compatibility with real hardware and configurations, scalability under real load |
    | Fixing | Defects can be fixed during the test cycle | Defects are usually deferred to a later release |
    | Also called | In-house acceptance testing | Field testing, external user acceptance testing, pre-release testing |

    Both are forms of acceptance testing, which is the final level of testing before release.

    Gamma testing: a less standard term, used for the final check made when the software is considered complete and only a limited set of critical checks is repeated before shipping, with no further feature changes. Some organisations use it to mean a release candidate check. It is not part of the standard ISTQB terminology, and an answer should say so rather than invent a definition.

    Practical illustration: a mobile banking application is first tested in the bank's own laboratory by its testing team (alpha), then released to two thousand selected customers who use it for real transactions on their own phones for a month (beta), and only then published to all customers.
33. **Testing is an activity that is performed to verify correct behavior of a program. Testing should be conducted in all the stages of program development. Describe different types of tests conducted in the implementation stage.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 980 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer: The implementation stage is the phase in which the design is translated into source code. Testing carried out during this stage is aimed at finding defects as close as possible to the point where they are introduced, because a defect found here costs a small fraction of what it costs after release.

    The types of test conducted during the implementation stage:

    1. Unit testing:
    - The smallest testable component, a single function, method or class, is tested in isolation.
    - Performed by the developer who wrote the code, usually immediately after writing it, and often before writing it in test-driven development.
    - It is white box testing, using knowledge of the internal logic to design the cases.
    - Dependencies are replaced by stubs, mocks or fakes, so that a failure can be attributed with certainty to the unit under test.
    - Coverage is measured: statement, branch and condition coverage.
    - Tools: JUnit, NUnit, PyTest, Jest.

    2. Static testing, that is testing without executing the code:
    - Code review or peer review: another developer reads the code against a checklist. Reviews typically find 60 per cent or more of the defects present, and they find kinds of defect that no dynamic test can, such as unclear naming and missing error handling.
    - Walkthrough: the author leads colleagues through the code.
    - Inspection: the most formal form, with defined roles and recorded defect counts.
    - Static analysis with tools such as SonarQube, Checkstyle, PMD or FindBugs, which detect unreachable code, unsafe constructs, resource leaks, violations of coding standards and excessive complexity.
    - Desk checking, in which the developer traces the logic by hand.

    3. Integration testing:
    - As modules are completed, they are combined and the interfaces between them are tested.
    - Approaches: top-down with stubs, bottom-up with drivers, incremental one module at a time, or big bang.
    - It finds interface mismatches, wrong parameter order or type, incorrect data formats and unit inconsistencies, none of which unit testing can find.

    4. Smoke testing:
    - After every build, a quick and shallow check of the critical paths determines whether the build is stable enough to be tested further. A failed smoke test returns the build to the developers immediately, saving the testing team's time.
    - Usually automated as part of continuous integration.

    5. Regression testing:
    - After every change or fix, the existing test suite is re-run to confirm that previously working functionality has not been broken.
    - This is the type most dependent on automation, since it must be repeated constantly.

    6. Interface and API testing:
    - The published interfaces of each module and each service are tested against their contracts, checking request and response formats, status codes and error handling.
    - Tools: Postman, REST Assured.

    7. Debugging, which accompanies all of the above:
    - Strictly, debugging is not testing. Testing finds that a failure exists; debugging finds the fault that caused it and corrects it. The two are distinct activities with distinct skills, and confusing them is a common error.

    8. Continuous integration testing:
    - Every commit triggers an automated build, followed by static analysis, the unit test suite and a smoke test. A developer therefore learns within minutes if a change has broken anything, rather than weeks later.

    Why testing at this stage matters most:

    The cost of correcting a defect rises sharply with the phase in which it is found. Taking the cost at the requirement stage as one unit, it is roughly five at design, ten during coding, twenty during system testing and one hundred or more after release. Every defect caught during implementation is therefore worth many times its cost to find.

    The V-model expresses this by pairing each development phase with a corresponding test level:

    ```
    Requirements ------------------------> Acceptance Testing
        Design --------------------------> System Testing
        Detailed Design -----------------> Integration Testing
            Coding ----------------------> Unit Testing
    ```

    Reading it: unit testing verifies the code against the detailed design, integration testing verifies the modules against the architectural design, system testing verifies the system against the requirements, and acceptance testing verifies it against the user's actual need. Tests at each level are written from the corresponding document, which is why the test cases can and should be prepared before the code, not after it.

## Software Architecture & Design Patterns (MVC) (11)

1. **Why is it essential to maintain proper MVC structure in web applications?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*


   Answer: Maintaining a proper MVC structure is essential in web applications for the following reasons.

   MVC stands for Model-View-Controller. It is an architectural pattern that separates an application into three interconnected components, so that the internal representation of information is kept separate from the way it is presented to the user and from the way the user interacts with it.

   The three components:

   - Model: the data and the business logic. It manages the state of the application, enforces the business rules, and communicates with the database. It knows nothing about the user interface. In a banking application the Model holds the Account class, the balance, and the rules governing a withdrawal.

   - View: the presentation layer, that is what the user sees. It displays the data supplied by the Model and sends user actions to the Controller. It contains no business logic and performs no calculation. In a web application the View is the HTML template.

   - Controller: the intermediary. It receives input from the user through the View, interprets it, calls the appropriate operations on the Model, and selects the View to display in response. It contains no business rules of its own; it coordinates.

   Flow of control:

   ```mermaid
   flowchart LR
     U[User] -->|action| C[Controller]
     C -->|updates / queries| M[Model]
     M -->|data| C
     C -->|selects and supplies data| V[View]
     V -->|displays| U
   ```

   Sequence for a typical request:
   1. The user performs an action in the View, for example submitting a login form.
   2. The Controller receives the request and validates the input format.
   3. The Controller calls the Model to authenticate the user.
   4. The Model queries the database, applies the business rules and returns the result.
   5. The Controller chooses the appropriate View, the dashboard on success or the login page with an error on failure.
   6. The View renders and is returned to the user.

   Advantages:
   - Separation of concerns: the three responsibilities are independent, so each can be understood and changed on its own.
   - Parallel development: a front-end developer can build the View while a back-end developer builds the Model, once the Controller's interface is agreed.
   - Testability: the Model contains the business logic and has no dependence on the user interface, so it can be unit tested directly. Testing business logic embedded in a page is far harder.
   - Multiple views of the same data: one Model can serve an HTML page, a mobile application and a JSON API, without duplication.
   - Maintainability: a change to the appearance touches only the View; a change to a business rule touches only the Model.
   - Reusability: Models and Controllers can be reused across interfaces.
   - Clear structure for a team: a new developer knows where to look for any particular kind of code.

   Disadvantages:
   - It adds complexity, and for a very small application the overhead is not justified.
   - There are more files and more layers to navigate.
   - Strict separation is not always natural, and developers often let logic leak into the Controller, producing what is called a fat controller.
   - The learning curve is real for beginners.

   Frameworks that implement it: Laravel and CodeIgniter in PHP, Spring MVC and Struts in Java, ASP.NET MVC in C#, Django (which calls it MVT, Model-View-Template) and Flask in Python, and Ruby on Rails.

   Related patterns: MVP (Model-View-Presenter), used in Android; MVVM (Model-View-ViewModel), used in WPF and in Angular and Vue; and the three-tier architecture, which is similar but describes deployment layers rather than responsibilities within a layer.

   Why it is essential specifically in web applications:
   - A web application has at least three distinct audiences for its output: browsers, mobile applications and other systems calling an API. With MVC, one Model and one Controller serve all three simply by choosing a different View.
   - Web front ends change far more often than business rules. A redesign should not require the business logic to be touched, and MVC guarantees that it need not be.
   - Web teams are usually divided into front-end and back-end specialists, and MVC gives each a clearly bounded area to work in.
   - Security is easier to reason about when input validation and authorisation live in the Controller and the business rules live in the Model, rather than being scattered through the pages.
   - Without MVC, business logic embedded in the presentation pages cannot be unit tested, and in practice it is simply never tested at all.
2. **What is MVC? Write down the MVC design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*


   Answer: MVC stands for Model-View-Controller. It is an architectural pattern that separates an application into three interconnected components, so that the internal representation of information is kept separate from the way it is presented to the user and from the way the user interacts with it.

   The three components:

   - Model: the data and the business logic. It manages the state of the application, enforces the business rules, and communicates with the database. It knows nothing about the user interface. In a banking application the Model holds the Account class, the balance, and the rules governing a withdrawal.

   - View: the presentation layer, that is what the user sees. It displays the data supplied by the Model and sends user actions to the Controller. It contains no business logic and performs no calculation. In a web application the View is the HTML template.

   - Controller: the intermediary. It receives input from the user through the View, interprets it, calls the appropriate operations on the Model, and selects the View to display in response. It contains no business rules of its own; it coordinates.

   Flow of control:

   ```mermaid
   flowchart LR
     U[User] -->|action| C[Controller]
     C -->|updates / queries| M[Model]
     M -->|data| C
     C -->|selects and supplies data| V[View]
     V -->|displays| U
   ```

   Sequence for a typical request:
   1. The user performs an action in the View, for example submitting a login form.
   2. The Controller receives the request and validates the input format.
   3. The Controller calls the Model to authenticate the user.
   4. The Model queries the database, applies the business rules and returns the result.
   5. The Controller chooses the appropriate View, the dashboard on success or the login page with an error on failure.
   6. The View renders and is returned to the user.

   Advantages:
   - Separation of concerns: the three responsibilities are independent, so each can be understood and changed on its own.
   - Parallel development: a front-end developer can build the View while a back-end developer builds the Model, once the Controller's interface is agreed.
   - Testability: the Model contains the business logic and has no dependence on the user interface, so it can be unit tested directly. Testing business logic embedded in a page is far harder.
   - Multiple views of the same data: one Model can serve an HTML page, a mobile application and a JSON API, without duplication.
   - Maintainability: a change to the appearance touches only the View; a change to a business rule touches only the Model.
   - Reusability: Models and Controllers can be reused across interfaces.
   - Clear structure for a team: a new developer knows where to look for any particular kind of code.

   Disadvantages:
   - It adds complexity, and for a very small application the overhead is not justified.
   - There are more files and more layers to navigate.
   - Strict separation is not always natural, and developers often let logic leak into the Controller, producing what is called a fat controller.
   - The learning curve is real for beginners.

   Frameworks that implement it: Laravel and CodeIgniter in PHP, Spring MVC and Struts in Java, ASP.NET MVC in C#, Django (which calls it MVT, Model-View-Template) and Flask in Python, and Ruby on Rails.

   Related patterns: MVP (Model-View-Presenter), used in Android; MVVM (Model-View-ViewModel), used in WPF and in Angular and Vue; and the three-tier architecture, which is similar but describes deployment layers rather than responsibilities within a layer.
3. **Name of few architecture in design pattern.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 503 (ET: N/A)]*


   Answer: The word "architecture" is used in two senses in this context, so both are given.

   Architectural patterns, that is patterns that structure a whole system:

   - Model-View-Controller (MVC): separates data, presentation and control. Used in almost every web framework.
   - Model-View-Presenter (MVP): a variant in which the Presenter, rather than the View, holds the presentation logic. Used in Android.
   - Model-View-ViewModel (MVVM): the View binds declaratively to a ViewModel. Used in WPF, Angular and Vue.
   - Layered (n-tier) architecture: presentation, business logic, data access and database layers, each depending only on the one below.
   - Client-Server: a server provides a service and many clients consume it.
   - Three-tier architecture: client, application server and database server.
   - Microservices: the application is decomposed into small independently deployable services, each owning its data and communicating over a network.
   - Monolithic architecture: the whole application is built and deployed as one unit.
   - Service-Oriented Architecture (SOA): services communicate through an enterprise service bus.
   - Event-Driven architecture: components communicate by producing and consuming events, often through a message broker.
   - Publish-Subscribe: publishers emit messages on topics and subscribers receive them, without knowing one another.
   - Peer-to-Peer: every node acts as both client and server.
   - Pipe and Filter: data flows through a series of processing stages, as in a Unix pipeline or a compiler.
   - Broker: a broker coordinates communication between distributed components.
   - Blackboard: several specialist components contribute to a shared knowledge store; used in artificial intelligence and speech recognition.
   - Repository: components share data through a common central store.
   - Master-Slave: a master distributes work to identical slaves and combines their results.
   - Serverless: functions are executed on demand by a cloud platform, with no server managed by the developer.

   Design patterns proper, that is the Gang of Four patterns, in their three categories:

   - Creational: Singleton, Factory Method, Abstract Factory, Builder, Prototype.
   - Structural: Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy.
   - Behavioural: Chain of Responsibility, Command, Interpreter, Iterator, Mediator, Memento, Observer, State, Strategy, Template Method, Visitor.

   The distinction worth stating: an architectural pattern determines the overall shape of the system and is chosen once, at the beginning, and is expensive to change later. A design pattern solves a local problem within a component and can be introduced or removed during refactoring.
4. **What is software design pattern? What are the advantages?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 471 (ET: N/A)]*


   Answer: A design pattern is a general, reusable solution to a commonly occurring problem in software design. It is not finished code that can be pasted into a program; it is a description of a problem, of a proven solution to it, and of the consequences of applying that solution. Patterns were catalogued in 1994 by Gamma, Helm, Johnson and Vlissides, known as the Gang of Four, in the book Design Patterns.

   Categories and the principal patterns:

   Creational patterns, concerned with how objects are created:
   - Singleton: ensures a class has only one instance and provides a global point of access to it. Used for a configuration object, a logger or a database connection pool.
   - Factory Method: defines an interface for creating an object but lets subclasses decide which class to instantiate.
   - Abstract Factory: creates families of related objects without specifying their concrete classes.
   - Builder: constructs a complex object step by step, separating construction from representation.
   - Prototype: creates new objects by cloning an existing one.

   Structural patterns, concerned with how classes and objects are composed:
   - Adapter: converts the interface of a class into another interface that a client expects, so that classes with incompatible interfaces can work together.
   - Facade: provides a simplified interface to a complex subsystem.
   - Decorator: attaches additional responsibilities to an object dynamically, without changing its class.
   - Proxy: provides a placeholder that controls access to another object, used for lazy loading, access control and remote objects.
   - Composite: composes objects into tree structures so that individual objects and groups are treated uniformly.
   - Bridge and Flyweight.

   Behavioural patterns, concerned with communication between objects:
   - Observer: defines a one-to-many dependency so that when one object changes state, all its dependants are notified automatically. This is the basis of event handling.
   - Strategy: defines a family of interchangeable algorithms and lets the algorithm vary independently of the clients that use it.
   - Template Method: defines the skeleton of an algorithm in a base class, deferring some steps to subclasses.
   - Command: encapsulates a request as an object, which allows queuing, logging and undo.
   - Iterator, State, Chain of Responsibility, Mediator, Memento and Visitor.

   Architectural patterns, which operate at a higher level: MVC, MVP, MVVM, layered architecture, microservices, client-server, publish-subscribe and repository.

   Advantages of design patterns:
   - Proven solutions: the pattern has been used successfully many times, so its pitfalls are known.
   - Reusability of design, not merely of code.
   - A shared vocabulary: saying "use an Observer here" conveys in two words what would otherwise take a paragraph. This is arguably the single greatest practical benefit.
   - Better maintainability and extensibility, because patterns generally reduce coupling and localise change.
   - Faster development, since a designer need not invent a solution to a problem that has been solved a thousand times.
   - Easier communication with other developers and in design documents.
   - They embody good principles such as programming to an interface rather than an implementation.

   Disadvantages and cautions:
   - Over-use produces unnecessary complexity. Applying a pattern where a simple function would do is a well-known beginner's error.
   - Patterns are not a substitute for understanding the problem.
   - Some patterns, in particular Singleton, introduce global state and make testing harder, and many practitioners now regard it as an anti-pattern.
   - A pattern must be adapted to the situation, not copied mechanically.
5. **Define design pattern. Write about singleton pattern.** *[BREB Assistant Programmer 18.02.2023 compact it 469 (ET: N/A)]*


   Answer: A design pattern is a general, reusable solution to a commonly occurring problem in software design. It is not code to be copied, but a description of a problem, of a proven solution and of the consequences of applying it. The standard catalogue is that of the Gang of Four, published in 1994, which divides patterns into creational, structural and behavioural categories.

   The Singleton pattern:

   Intent: to ensure that a class has exactly one instance, and to provide a single global point of access to it.

   When it is used:
   - A configuration object that must be shared by the whole application.
   - A logging service.
   - A database connection pool.
   - A cache.
   - A hardware device driver, where only one object may control the device.

   How it is implemented:
   - The constructor is made private, so that no other class can create an instance with new.
   - A private static field holds the single instance.
   - A public static method returns that instance, creating it on the first call.

   Simple implementation in Java:
   ```java
   public class ConfigManager {
       private static ConfigManager instance;   // the single instance
       private String databaseUrl;

       private ConfigManager() {                // private constructor
           databaseUrl = "jdbc:mysql://localhost:3306/mydb";
       }

       public static ConfigManager getInstance() {
           if (instance == null) {              // lazy initialisation
               instance = new ConfigManager();
           }
           return instance;
       }

       public String getDatabaseUrl() { return databaseUrl; }
   }
   ```
   Usage:
   ```java
   ConfigManager c1 = ConfigManager.getInstance();
   ConfigManager c2 = ConfigManager.getInstance();
   System.out.println(c1 == c2);    // true: both refer to the same object
   ```

   The thread safety problem: the version above is not thread safe. Two threads may both find instance to be null and both create an object, so two instances would exist. Three standard remedies:

   Eager initialisation, the simplest and safe:
   ```java
   public class ConfigManager {
       private static final ConfigManager INSTANCE = new ConfigManager();
       private ConfigManager() { }
       public static ConfigManager getInstance() { return INSTANCE; }
   }
   ```

   Double-checked locking, when creation is expensive and must be deferred:
   ```java
   public class ConfigManager {
       private static volatile ConfigManager instance;
       private ConfigManager() { }
       public static ConfigManager getInstance() {
           if (instance == null) {
               synchronized (ConfigManager.class) {
                   if (instance == null) {
                       instance = new ConfigManager();
                   }
               }
           }
           return instance;
       }
   }
   ```
   The keyword volatile is essential here, otherwise a partially constructed object could become visible to another thread.

   Enum singleton, which Joshua Bloch recommends as the best approach in Java, since it is thread safe, handles serialisation correctly and cannot be defeated by reflection:
   ```java
   public enum ConfigManager {
       INSTANCE;
       public String getDatabaseUrl() { return "jdbc:mysql://localhost:3306/mydb"; }
   }
   ```

   Advantages:
   - Controlled access to the single instance.
   - Memory is saved, since the object is created only once and only when needed.
   - A single point of access makes global state easy to reach.

   Disadvantages, which should always be stated, because many practitioners now regard Singleton as an anti-pattern:
   - It introduces global state, which makes the flow of data through a program hard to follow.
   - It makes unit testing difficult, because the singleton cannot easily be replaced by a mock, and state persists between tests.
   - It hides dependencies: a class that calls getInstance() does not declare that it depends on the configuration, so the dependency is invisible in its interface.
   - It violates the single responsibility principle, since the class both does its job and controls its own instantiation.
   - Thread safety requires care.
   - It is difficult to subclass.

   Modern alternative: dependency injection. Instead of a class fetching the single instance itself, the single instance is created once by the framework and passed to whoever needs it. The object is still unique, but the dependency is explicit and can be replaced in a test. Spring, Guice and most modern frameworks work this way.
6. **We are going to create a Shape interface and concrete classes implementing the Shape interface. A facade class ShapeMaker is defined as a next step. ShapeMaker class uses the concrete classes to delegate user calls to these classes. FacadePatternDemo, our demo class, will use ShapeMaker class to show the results.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*


   Answer: This describes the Facade design pattern, which is a structural pattern.

   Intent of the Facade pattern: to provide a single simplified interface to a complex subsystem, so that a client can use the subsystem without knowing about its individual classes.

   Implementation of the described scenario:

   Step 1 - the Shape interface:
   ```java
   public interface Shape {
       void draw();
   }
   ```

   Step 2 - the concrete classes implementing Shape:
   ```java
   public class Rectangle implements Shape {
       @Override
       public void draw() {
           System.out.println("Rectangle::draw()");
       }
   }

   public class Square implements Shape {
       @Override
       public void draw() {
           System.out.println("Square::draw()");
       }
   }

   public class Circle implements Shape {
       @Override
       public void draw() {
           System.out.println("Circle::draw()");
       }
   }
   ```

   Step 3 - the facade class ShapeMaker, which holds the concrete objects and exposes simple methods:
   ```java
   public class ShapeMaker {
       private Shape circle;
       private Shape rectangle;
       private Shape square;

       public ShapeMaker() {
           circle    = new Circle();
           rectangle = new Rectangle();
           square    = new Square();
       }

       public void drawCircle()    { circle.draw();    }
       public void drawRectangle() { rectangle.draw(); }
       public void drawSquare()    { square.draw();    }
   }
   ```

   Step 4 - the demonstration class, which uses only the facade:
   ```java
   public class FacadePatternDemo {
       public static void main(String[] args) {
           ShapeMaker shapeMaker = new ShapeMaker();

           shapeMaker.drawCircle();
           shapeMaker.drawRectangle();
           shapeMaker.drawSquare();
       }
   }
   ```

   Output:
   ```
   Circle::draw()
   Rectangle::draw()
   Square::draw()
   ```

   Class relationships:

   ```mermaid
   classDiagram
     class Shape {
       <<interface>>
       +draw()
     }
     class Circle {
       +draw()
     }
     class Rectangle {
       +draw()
     }
     class Square {
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
     Shape <|.. Circle
     Shape <|.. Rectangle
     Shape <|.. Square
     ShapeMaker --> Shape
   ```

   What the pattern achieves here:
   - The client, FacadePatternDemo, never mentions Circle, Rectangle or Square. It knows only ShapeMaker.
   - The subsystem can be changed freely. A new Triangle class can be added, or Circle can be reimplemented, without touching the client at all.
   - Coupling between the client and the subsystem is reduced from three dependencies to one.
   - The client code is simpler and reads at the level of intent, drawCircle(), rather than at the level of mechanism, new Circle().draw().

   When to use the Facade pattern:
   - When a subsystem is complex and most clients need only a small part of it.
   - When a layer boundary is being defined, to give the layer a single entry point.
   - When legacy code with an awkward interface must be wrapped for new clients.
   - Real examples: a JDBC helper class that hides connection, statement and result set handling; a service layer in a web application that hides the repositories beneath it.

   Distinction from related patterns:
   - Adapter converts an existing interface into a different one that a client expects; Facade defines a new simpler interface to a whole subsystem.
   - Facade does not prevent direct access to the subsystem classes; it merely makes it unnecessary.
   - Mediator centralises communication between peers; Facade centralises access from outside to inside.
7. **Imagine a scenario where new child classes are introduced frequently from a basic class. The method calling sequences for every child class are the same but the implementation is different among the child classes. Here which design pattern would you like to apply? Explain the reasons with examples to support your answer.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*


   Answer: The Template Method design pattern should be applied, and the Factory Method pattern may be used alongside it for the creation of the child objects.

   Restating the scenario: new child classes are introduced frequently from a base class; the sequence of method calls is the same for every child; only the implementation of the individual steps differs among the children.

   That description is precisely the intent of the Template Method pattern: define the skeleton of an algorithm in a base class, deferring some steps to subclasses, so that subclasses can redefine those steps without changing the structure of the algorithm.

   Why Template Method is the right choice:
   - The sequence is fixed and identical for every child, so it should be written once in the base class rather than repeated in every child, where it could drift out of step.
   - Only the individual steps vary, and those are exactly what the pattern leaves abstract.
   - A new child class is added by implementing the abstract steps, and the base class need not be touched at all. This satisfies the open-closed principle: open for extension, closed for modification.
   - Duplication is eliminated. Without the pattern, every child would repeat the calling sequence, and a change to that sequence would have to be made in every child.
   - The base class controls the algorithm, so a child cannot accidentally reorder or omit a step. This is called inversion of control, or the Hollywood principle: do not call us, we will call you.

   Implementation:

   ```java
   // The base class defines the skeleton of the algorithm
   abstract class DataProcessor {

       // The template method: final, so that no subclass can change the sequence
       public final void process() {
           openConnection();
           readData();
           processData();
           writeResult();
           closeConnection();
           logCompletion();          // a concrete step, shared by all
       }

       // Steps that every subclass must implement
       protected abstract void readData();
       protected abstract void processData();
       protected abstract void writeResult();

       // Steps with a default implementation that a subclass may override
       protected void openConnection() {
           System.out.println("Opening a default connection");
       }

       protected void closeConnection() {
           System.out.println("Closing the connection");
       }

       // A step that is the same for every subclass
       private void logCompletion() {
           System.out.println("Processing completed at " + java.time.LocalTime.now());
       }
   }

   // Child class 1
   class CsvProcessor extends DataProcessor {
       protected void readData()    { System.out.println("Reading rows from a CSV file"); }
       protected void processData() { System.out.println("Parsing comma-separated fields"); }
       protected void writeResult() { System.out.println("Writing the result to a CSV file"); }
   }

   // Child class 2
   class DatabaseProcessor extends DataProcessor {
       protected void openConnection() { System.out.println("Opening a JDBC connection"); }
       protected void readData()       { System.out.println("Executing a SELECT query"); }
       protected void processData()    { System.out.println("Aggregating the result set"); }
       protected void writeResult()    { System.out.println("Executing an INSERT statement"); }
       protected void closeConnection(){ System.out.println("Closing the JDBC connection"); }
   }

   // Child class 3, added later, with no change to the base class
   class XmlProcessor extends DataProcessor {
       protected void readData()    { System.out.println("Parsing an XML document"); }
       protected void processData() { System.out.println("Applying an XSLT transformation"); }
       protected void writeResult() { System.out.println("Writing the transformed XML"); }
   }

   public class TemplateDemo {
       public static void main(String[] args) {
           DataProcessor[] processors = {
               new CsvProcessor(),
               new DatabaseProcessor(),
               new XmlProcessor()
           };

           for (DataProcessor p : processors) {
               p.process();          // the same sequence, different implementations
               System.out.println("-----");
           }
       }
   }
   ```

   Output:
   ```
   Opening a default connection
   Reading rows from a CSV file
   Parsing comma-separated fields
   Writing the result to a CSV file
   Closing the connection
   Processing completed at 11:42:03
   -----
   Opening a JDBC connection
   Executing a SELECT query
   Aggregating the result set
   Executing an INSERT statement
   Closing the JDBC connection
   Processing completed at 11:42:03
   -----
   Opening a default connection
   Parsing an XML document
   Applying an XSLT transformation
   Writing the transformed XML
   Closing the connection
   Processing completed at 11:42:03
   -----
   ```

   Adding the Factory Method: since new child classes are introduced frequently, the client should not decide which one to create with a chain of if statements. A factory keeps that decision in one place:
   ```java
   class ProcessorFactory {
       public static DataProcessor create(String type) {
           switch (type.toLowerCase()) {
               case "csv":      return new CsvProcessor();
               case "database": return new DatabaseProcessor();
               case "xml":      return new XmlProcessor();
               default: throw new IllegalArgumentException("Unknown type: " + type);
           }
       }
   }
   ```
   Now adding a JsonProcessor requires changing only the factory, not every place in the program that creates a processor.

   Why the alternatives are less suitable:
   - Strategy would be the choice if the algorithms were entirely different and interchangeable at run time. Here the sequence is fixed and only the steps vary, which is Template Method, not Strategy. The distinction is that Template Method uses inheritance and fixes the structure, while Strategy uses composition and replaces the whole algorithm.
   - Simple inheritance without a template method would let each child define its own process() method, which is exactly the duplication the question is trying to avoid.
   - Observer, Decorator and Adapter address different problems entirely.

   Real examples of Template Method in practice: the servlet lifecycle in Java (init, service, destroy), JUnit's setUp, test and tearDown sequence, and Spring's JdbcTemplate.
8. **(ক) 'ATM machine' এর Software Structure আঁকুন।** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*


   Answer: ATM machine এর Software Structure (সফটওয়্যার কাঠামো):

   একটি ATM ব্যবস্থাকে স্তরে স্তরে সাজানো (layered) স্থাপত্যে বিন্যস্ত করা হয়, যেখানে উপরের স্তর নিচের স্তরের সেবা ব্যবহার করে কিন্তু বিপরীতটি ঘটে না।

   স্তরভিত্তিক কাঠামো:

   ```mermaid
   flowchart LR
     subgraph P[Presentation Layer]
       SC[Screen / Touch UI]
       KP[Keypad Handler]
     end
     subgraph A[Application Layer]
       TM[Transaction Manager]
       SM[Session Manager]
       AU[Authentication Module]
     end
     subgraph B[Business Logic Layer]
       WD[Withdrawal Service]
       DP[Deposit Service]
       BQ[Balance Enquiry]
       TR[Fund Transfer]
       ST[Mini Statement]
     end
     subgraph D[Device Control Layer]
       CR[Card Reader Driver]
       CD[Cash Dispenser Driver]
       PR[Receipt Printer Driver]
       DS[Deposit Slot Driver]
       CM[Camera / Sensor Driver]
     end
     subgraph N[Communication Layer]
       NW[Network Interface]
       EN[Encryption Module]
     end
     BK[(Bank Host / Core Banking Server)]
     LOG[(Local Transaction Log)]

     P --> A
     A --> B
     B --> D
     B --> N
     N --> BK
     A --> LOG
   ```

   প্রতিটি স্তরের দায়িত্ব:

   ১. Presentation Layer (উপস্থাপনা স্তর):
   - পর্দায় মেনু ও বার্তা দেখানো, ভাষা নির্বাচন (বাংলা বা ইংরেজি)।
   - কীপ্যাড ও টাচ ইনপুট গ্রহণ ও যাচাই।
   - পিন প্রবেশের সময় তা আড়াল করা।
   - এতে কোনো ব্যবসায়িক যুক্তি থাকে না।

   ২. Application Layer (অ্যাপ্লিকেশন স্তর):
   - Session Manager: কার্ড প্রবেশ থেকে কার্ড ফেরত পর্যন্ত সম্পূর্ণ সেশন নিয়ন্ত্রণ করে; নির্দিষ্ট সময় নিষ্ক্রিয় থাকলে সেশন বাতিল করে।
   - Authentication Module: কার্ড নম্বর ও পিন যাচাই করে; তিনবার ভুল পিনে কার্ড আটকে দেয়।
   - Transaction Manager: প্রতিটি লেনদেনকে একটি পরমাণুসদৃশ (atomic) একক হিসেবে পরিচালনা করে — হয় সম্পূর্ণ সম্পন্ন হবে, নয়তো পুরোপুরি বাতিল হবে।

   ৩. Business Logic Layer (ব্যবসায়িক যুক্তি স্তর):
   - টাকা তোলা: ব্যালেন্স পরীক্ষা, দৈনিক সীমা যাচাই, নোটের সংমিশ্রণ নির্ণয়।
   - টাকা জমা, ব্যালেন্স জিজ্ঞাসা, তহবিল স্থানান্তর, মিনি স্টেটমেন্ট, পিন পরিবর্তন।
   - সব ব্যবসায়িক নিয়ম এখানেই কেন্দ্রীভূত।

   ৪. Device Control Layer (যন্ত্র নিয়ন্ত্রণ স্তর):
   - Card Reader Driver: কার্ডের চৌম্বকীয় ফিতা বা চিপ পড়া ও কার্ড ফেরত দেওয়া।
   - Cash Dispenser Driver: নোট গণনা, বিতরণ ও নোট আটকে গেলে সংকেত দেওয়া।
   - Receipt Printer Driver, Deposit Slot Driver, Camera ও Sensor Driver।
   - প্রতিটি যন্ত্রের ত্রুটি ওপরের স্তরে জানানো এর দায়িত্ব।

   ৫. Communication Layer (যোগাযোগ স্তর):
   - Encryption Module: পিন ব্লক ও লেনদেনের তথ্য এনক্রিপ্ট করা। পিন কখনোই সাধারণ পাঠ্য আকারে পাঠানো হয় না।
   - Network Interface: ব্যাংকের কেন্দ্রীয় সার্ভারের সঙ্গে ISO 8583 প্রোটোকলে বার্তা আদান-প্রদান।
   - সংযোগ বিচ্ছিন্ন হলে লেনদেন বাতিল করা এবং তা স্থানীয় লগে লিখে রাখা।

   ৬. Data Layer:
   - স্থানীয় লেনদেন লগ (audit trail), যা কখনো মুছে ফেলা যায় না।
   - যন্ত্রের অবস্থা ও নোটের হিসাব।
   - কেন্দ্রীয় ডেটাবেজ ব্যাংকের সার্ভারে থাকে, ATM এ নয়।

   একটি টাকা তোলার লেনদেনের ক্রম:

   ```
   ১. কার্ড প্রবেশ            → Card Reader → Session Manager
   ২. পিন প্রবেশ              → Keypad → Encryption → Authentication
   ৩. যাচাইকরণ                → Network → Bank Host → সাড়া
   ৪. মেনু প্রদর্শন            → Presentation Layer
   ৫. পরিমাণ নির্বাচন          → Withdrawal Service
   ৬. ব্যালেন্স ও সীমা যাচাই   → Bank Host
   ৭. অনুমোদন                 → Transaction Manager
   ৮. টাকা বিতরণ              → Cash Dispenser
   ৯. নিশ্চিতকরণ বার্তা        → Bank Host (ডেবিট চূড়ান্ত)
   ১০. রসিদ ছাপা ও কার্ড ফেরত  → Printer, Card Reader
   ```

   গুরুত্বপূর্ণ নকশাগত বিবেচনা:
   - পরমাণুসদৃশতা (Atomicity): টাকা বেরোনোর পর সংযোগ বিচ্ছিন্ন হলে যেন হিসাব থেকে দুইবার কাটা না যায় বা কাটা বাদ না পড়ে। এ জন্য দুই ধাপের নিশ্চিতকরণ ব্যবহার করা হয়।
   - ব্যর্থতা সামলানো: নোট আটকে গেলে, কাগজ ফুরালে বা বিদ্যুৎ চলে গেলে ব্যবস্থাটি একটি সুনির্দিষ্ট অবস্থায় থাকবে এবং লগে তা লেখা থাকবে।
   - নিরাপত্তা: পিন কখনো সংরক্ষণ করা হয় না, কেবল এনক্রিপ্ট করে পাঠানো হয়; সব লেনদেন লগবদ্ধ; ক্যামেরা সচল; এবং যন্ত্রটি খোলা হলে তা শনাক্ত হয় (tamper detection)।
   - রিয়েল-টাইম প্রয়োজনীয়তা: নির্দিষ্ট সময়ের মধ্যে সাড়া না পেলে লেনদেন বাতিল হবে।

   ব্যবহৃত নকশা নীতি: স্তরভিত্তিক স্থাপত্য (layered architecture), যাতে প্রতিটি স্তর কেবল নিচের স্তরের ওপর নির্ভর করে; State pattern, কারণ ATM একটি সসীম অবস্থা যন্ত্র (idle, card inserted, authenticated, transaction, dispensing); এবং Facade pattern, যাতে অ্যাপ্লিকেশন স্তর যন্ত্রগুলোর জটিলতা না জেনেই কাজ করতে পারে।
9. **(ii) Design the communication for the user login system for an MVC pattern framework.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*


   Answer: Communication design for a user login system in an MVC framework.

   The components:
   - View: the login page containing the form, and the dashboard page shown after success.
   - Controller: the LoginController, which receives the request, validates its format, calls the Model and selects the response.
   - Model: the User model and the AuthenticationService, which hold the business rules and query the database.

   Sequence diagram:

   ```mermaid
   sequenceDiagram
     actor User
     participant V as View (login.html)
     participant C as LoginController
     participant M as User Model / AuthService
     participant DB as Database
     participant S as Session

     User->>V: Opens the login page
     V-->>User: Displays the form with a CSRF token
     User->>V: Enters username and password, submits
     V->>C: POST /login with the credentials
     C->>C: Validate the CSRF token
     C->>C: Validate the input format (not empty, valid email)
     alt Input invalid
       C-->>V: Re-render the form with an error message
       V-->>User: "Please enter a valid email address"
     else Input valid
       C->>M: authenticate(username, password)
       M->>DB: SELECT user WHERE email = ?
       DB-->>M: User record with the password hash, or none
       alt User not found or password does not match
         M->>DB: Record the failed attempt
         M-->>C: AuthResult.failure()
         C-->>V: Re-render the form with a generic error
         V-->>User: "Invalid username or password"
       else Credentials correct
         M->>M: Verify the hash with bcrypt or Argon2
         M->>DB: Update last_login, reset the failed count
         M-->>C: AuthResult.success(user)
         C->>S: Create a session, regenerate the session ID
         S-->>C: Session token
         C-->>V: Redirect to /dashboard
         V-->>User: Dashboard page
       end
     end
   ```

   Step-by-step description of the communication:

   1. The user requests the login page. The Controller returns the View, which includes a CSRF token.
   2. The user submits the form. The View sends a POST request to the Controller. It does not talk to the Model directly; that is the rule that MVC exists to enforce.
   3. The Controller performs only presentation-level validation: is the CSRF token valid, are the fields present, is the email syntactically valid. It performs no authentication itself.
   4. The Controller calls the Model, passing the credentials. All business logic lives here.
   5. The Model queries the database, compares the stored password hash with the supplied password using a slow hashing function such as bcrypt or Argon2, checks whether the account is locked or inactive, and applies the rate-limiting rules.
   6. The Model returns a result object to the Controller. It does not know or care what the Controller will do with it, and it never writes to the screen.
   7. The Controller decides the response: on success it creates a session and redirects; on failure it re-renders the form with an error.
   8. The View renders whatever the Controller gives it, and contains no logic beyond simple display.

   Why the responsibilities are divided in this way:
   - The Model can be unit tested without any web server, because it takes a username and a password and returns a result.
   - The same Model serves a browser login, a mobile application and an API, with only the Controller and the View differing.
   - A change to the appearance of the login page cannot break the authentication rules.
   - Security logic is in one place rather than scattered through the pages.

   Security points that must be built into this design:
   - Never store the password itself; store a salted hash produced by bcrypt, scrypt or Argon2.
   - Return the same generic message for an unknown user and for a wrong password, so that an attacker cannot enumerate valid accounts.
   - Regenerate the session identifier on successful login, to prevent session fixation.
   - Use a CSRF token on the form.
   - Rate-limit attempts and lock the account after a number of failures.
   - Send everything over HTTPS, and mark the session cookie HttpOnly, Secure and SameSite.
   - Log every attempt, successful and failed, with the time and the source address.
   - Use parameterised queries, never string concatenation, to prevent SQL injection.
10. **(i) MVC framework কী? এর সুবিধাগুলো লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 960 (ET: N/A)]*


    Answer: MVC framework কী এবং এর সুবিধাসমূহ:

    MVC এর পূর্ণরূপ Model-View-Controller। এটি একটি স্থাপত্যিক নকশা কাঠামো (architectural pattern), যা একটি অ্যাপ্লিকেশনকে তিনটি পরস্পর সংযুক্ত অংশে ভাগ করে, যাতে তথ্যের অভ্যন্তরীণ উপস্থাপনা, ব্যবহারকারীর কাছে তা প্রদর্শনের পদ্ধতি এবং ব্যবহারকারীর সঙ্গে মিথস্ক্রিয়া — এই তিনটি আলাদা থাকে।

    তিনটি অংশ:

    - Model (মডেল): তথ্য ও ব্যবসায়িক যুক্তি। অ্যাপ্লিকেশনের অবস্থা ব্যবস্থাপনা করে, ব্যবসায়িক নিয়ম প্রয়োগ করে এবং ডেটাবেজের সঙ্গে যোগাযোগ করে। এটি ব্যবহারকারী ইন্টারফেস সম্পর্কে কিছুই জানে না। ব্যাংকিং অ্যাপে Account শ্রেণি, ব্যালেন্স এবং টাকা তোলার নিয়ম মডেলে থাকে।

    - View (ভিউ): উপস্থাপনা স্তর, অর্থাৎ ব্যবহারকারী যা দেখেন। মডেল থেকে পাওয়া তথ্য প্রদর্শন করে এবং ব্যবহারকারীর কাজ কন্ট্রোলারের কাছে পাঠায়। এতে কোনো ব্যবসায়িক যুক্তি বা হিসাব থাকে না। ওয়েব অ্যাপে ভিউ হলো HTML টেমপ্লেট।

    - Controller (কন্ট্রোলার): মধ্যস্থতাকারী। ভিউয়ের মাধ্যমে ব্যবহারকারীর ইনপুট গ্রহণ করে, তা ব্যাখ্যা করে, মডেলের ওপর উপযুক্ত কাজ সম্পাদন করায় এবং প্রতিক্রিয়া হিসেবে কোন ভিউ দেখানো হবে তা নির্বাচন করে।

    কার্যপ্রবাহ:

    ```mermaid
    flowchart LR
      U[User] -->|কাজ| C[Controller]
      C -->|আহ্বান| M[Model]
      M -->|তথ্য| C
      C -->|তথ্যসহ নির্বাচন| V[View]
      V -->|প্রদর্শন| U
    ```

    সুবিধাসমূহ:

    - দায়িত্বের পৃথকীকরণ (Separation of Concerns): তিনটি ভিন্ন দায়িত্ব তিনটি আলাদা অংশে থাকায় প্রতিটি স্বাধীনভাবে বোঝা ও বদলানো যায়। ডিজাইন বদলাতে হলে কেবল View, ব্যবসায়িক নিয়ম বদলাতে হলে কেবল Model স্পর্শ করতে হয়।

    - সমান্তরাল উন্নয়ন: ফ্রন্ট-এন্ড ডেভেলপার View তৈরি করতে পারেন আর ব্যাক-এন্ড ডেভেলপার Model তৈরি করতে পারেন, একই সময়ে।

    - পরীক্ষণযোগ্যতা: সব ব্যবসায়িক যুক্তি Model এ থাকে এবং তার সঙ্গে ইন্টারফেসের কোনো নির্ভরতা নেই, তাই একে সরাসরি ইউনিট টেস্ট করা যায়। ওয়েব পাতার ভেতরে ছড়িয়ে থাকা যুক্তি বাস্তবে কখনোই পরীক্ষিত হয় না।

    - একই তথ্যের একাধিক উপস্থাপনা: একটিমাত্র Model দিয়ে HTML পাতা, মোবাইল অ্যাপ এবং JSON API — তিনটিই চালানো যায়, কোনো কোড পুনরাবৃত্তি ছাড়াই।

    - রক্ষণাবেক্ষণযোগ্যতা: পরিবর্তন একটি নির্দিষ্ট স্তরেই সীমাবদ্ধ থাকে, সারা প্রোগ্রামে ছড়ায় না।

    - পুনঃব্যবহারযোগ্যতা: Model ও Controller একাধিক ইন্টারফেসে পুনরায় ব্যবহার করা যায়।

    - সুস্পষ্ট কাঠামো: নতুন ডেভেলপার সহজেই বুঝতে পারেন কোন ধরনের কোড কোথায় থাকবে, ফলে বড় দলে কাজ করা সহজ হয়।

    - নিরাপত্তা: ইনপুট যাচাই ও অনুমোদন Controller এ এবং ব্যবসায়িক নিয়ম Model এ কেন্দ্রীভূত থাকায় নিরাপত্তা যাচাই করা সহজ হয়।

    অসুবিধা: ছোট অ্যাপ্লিকেশনের জন্য অতিরিক্ত জটিলতা তৈরি করে; ফাইল ও স্তরের সংখ্যা বাড়ে; নতুনদের জন্য শেখার বাধা আছে; এবং শৃঙ্খলা না থাকলে যুক্তি Controller এ জমা হয়ে "fat controller" সমস্যা তৈরি হয়।

    বাস্তব কাঠামোসমূহ: PHP তে Laravel ও CodeIgniter, Java তে Spring MVC ও Struts, C# এ ASP.NET MVC, Python এ Django (যা একে MVT বলে) ও Flask, এবং Ruby on Rails।

    সংশ্লিষ্ট নকশা: MVP (Model-View-Presenter), যা অ্যান্ড্রয়েডে ব্যবহৃত, এবং MVVM (Model-View-ViewModel), যা Angular ও Vue তে ব্যবহৃত।
11. **MVC framework কী? MVC Framework এর সুবিধাসমূহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*


    Answer: MVC stands for Model-View-Controller. It is an architectural pattern that separates an application into three interconnected components, so that the internal representation of information is kept separate from the way it is presented to the user and from the way the user interacts with it.

    The three components:

    - Model: the data and the business logic. It manages the state of the application, enforces the business rules, and communicates with the database. It knows nothing about the user interface. In a banking application the Model holds the Account class, the balance, and the rules governing a withdrawal.

    - View: the presentation layer, that is what the user sees. It displays the data supplied by the Model and sends user actions to the Controller. It contains no business logic and performs no calculation. In a web application the View is the HTML template.

    - Controller: the intermediary. It receives input from the user through the View, interprets it, calls the appropriate operations on the Model, and selects the View to display in response. It contains no business rules of its own; it coordinates.

    Flow of control:

    ```mermaid
    flowchart LR
      U[User] -->|action| C[Controller]
      C -->|updates / queries| M[Model]
      M -->|data| C
      C -->|selects and supplies data| V[View]
      V -->|displays| U
    ```

    Sequence for a typical request:
    1. The user performs an action in the View, for example submitting a login form.
    2. The Controller receives the request and validates the input format.
    3. The Controller calls the Model to authenticate the user.
    4. The Model queries the database, applies the business rules and returns the result.
    5. The Controller chooses the appropriate View, the dashboard on success or the login page with an error on failure.
    6. The View renders and is returned to the user.

    Advantages:
    - Separation of concerns: the three responsibilities are independent, so each can be understood and changed on its own.
    - Parallel development: a front-end developer can build the View while a back-end developer builds the Model, once the Controller's interface is agreed.
    - Testability: the Model contains the business logic and has no dependence on the user interface, so it can be unit tested directly. Testing business logic embedded in a page is far harder.
    - Multiple views of the same data: one Model can serve an HTML page, a mobile application and a JSON API, without duplication.
    - Maintainability: a change to the appearance touches only the View; a change to a business rule touches only the Model.
    - Reusability: Models and Controllers can be reused across interfaces.
    - Clear structure for a team: a new developer knows where to look for any particular kind of code.

    Disadvantages:
    - It adds complexity, and for a very small application the overhead is not justified.
    - There are more files and more layers to navigate.
    - Strict separation is not always natural, and developers often let logic leak into the Controller, producing what is called a fat controller.
    - The learning curve is real for beginners.

    Frameworks that implement it: Laravel and CodeIgniter in PHP, Spring MVC and Struts in Java, ASP.NET MVC in C#, Django (which calls it MVT, Model-View-Template) and Flask in Python, and Ruby on Rails.

    Related patterns: MVP (Model-View-Presenter), used in Android; MVVM (Model-View-ViewModel), used in WPF and in Angular and Vue; and the three-tier architecture, which is similar but describes deployment layers rather than responsibilities within a layer.

## UML Diagrams (Class, Use Case, Sequence) (9)

1. An e-commerce platform has Customers, Orders, and Payment methods (Credit Card, Mobile Banking). Draw a **Class Diagram** showing attributes, methods, and relationships (inheritance, association). [SO IT 25-07-2026]


   Answer: Class diagram for an e-commerce platform with Customers, Orders and Payment methods.

   ```mermaid
   classDiagram
     class Customer {
       -int customerId
       -String name
       -String email
       -String phone
       -String address
       +register()
       +login()
       +placeOrder(Order)
       +viewOrderHistory() List~Order~
     }

     class Order {
       -int orderId
       -Date orderDate
       -String status
       -double totalAmount
       +addItem(Product, int)
       +removeItem(Product)
       +calculateTotal() double
       +confirm()
       +cancel()
     }

     class OrderItem {
       -int quantity
       -double unitPrice
       +getSubtotal() double
     }

     class Product {
       -int productId
       -String name
       -double price
       -int stockQuantity
       +checkStock(int) boolean
       +reduceStock(int)
     }

     class Payment {
       <<abstract>>
       -int paymentId
       -double amount
       -Date paymentDate
       -String status
       +processPayment()* boolean
       +refund()* boolean
     }

     class CreditCard {
       -String cardNumber
       -String cardHolderName
       -Date expiryDate
       -String cvv
       +processPayment() boolean
       +refund() boolean
       +validateCard() boolean
     }

     class MobileBanking {
       -String mobileNumber
       -String provider
       -String transactionPin
       +processPayment() boolean
       +refund() boolean
       +sendOtp()
     }

     Customer "1" --> "0..*" Order : places
     Order "1" *-- "1..*" OrderItem : contains
     OrderItem "0..*" --> "1" Product : refers to
     Order "1" --> "1" Payment : is paid by
     Payment <|-- CreditCard : inheritance
     Payment <|-- MobileBanking : inheritance
   ```

   Explanation of the classes:

   - Customer: holds the identity and contact details of the buyer, with operations to register, log in and place orders.
   - Order: represents one purchase, with its date, status and total, and operations to add and remove items and to confirm or cancel.
   - OrderItem: an association class holding the quantity and the price at the time of purchase. It is necessary because the same product may appear in many orders with different quantities, and because the price must be frozen at the time of the order rather than following later price changes.
   - Product: the catalogue item, with its price and stock level.
   - Payment: an abstract base class holding what every payment has in common: an identifier, an amount, a date and a status, and two abstract operations that every payment method must implement.
   - CreditCard and MobileBanking: concrete subclasses, each with its own attributes and its own implementation of processPayment and refund.

   Explanation of the relationships:

   - Customer to Order is an association with multiplicity 1 to 0..*: one customer may place many orders, and each order belongs to exactly one customer. The multiplicity 0..* is used rather than 1..* because a newly registered customer has no orders.

   - Order to OrderItem is a composition, shown by the filled diamond, with multiplicity 1 to 1..*: an order consists of at least one item, and an item cannot exist without its order. If the order is deleted, its items are deleted with it. This is what distinguishes composition from aggregation.

   - OrderItem to Product is an association: an item refers to a product, but the product exists independently of any order.

   - Order to Payment is an association: each order has one payment.

   - Payment to CreditCard and MobileBanking is inheritance, shown by the hollow triangle: a credit card payment is a payment. This is the "is-a" relationship the question asks for.

   Why the inheritance is designed this way: the Order class holds a reference of type Payment, not of type CreditCard. At run time that reference may hold either subclass, and calling processPayment() dispatches to the correct implementation. This is run-time polymorphism, and its practical value is that a new payment method, for example a bank transfer or a digital wallet, can be added as a new subclass without changing the Order class at all.

   UML notation used in the diagram:
   - A minus sign before an attribute means private; a plus sign before an operation means public.
   - An abstract class and its abstract operations are shown in the stereotype and marked with an asterisk.
   - A solid line with an arrow is an association; a filled diamond is composition; a hollow triangle is inheritance.
   - Multiplicities are written at each end: 1, 0..*, 1..*.
2. Draw a Use Case Diagram for an Online Banking System with two actors: Customer and Bank Admin. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: Use case diagram for an Online Banking System with two actors, Customer and Bank Admin.

   ```mermaid
   flowchart LR
     Cust((Customer))
     Admin((Bank Admin))

     subgraph OBS[Online Banking System]
       UC1([Login])
       UC2([View Account Balance])
       UC3([View Transaction History])
       UC4([Transfer Funds])
       UC5([Pay Utility Bill])
       UC6([Request Cheque Book])
       UC7([Change Password])
       UC8([Download Statement])
       UC9([Manage Customer Accounts])
       UC10([Approve Account Opening])
       UC11([Block / Unblock Account])
       UC12([Generate Reports])
       UC13([Set Transaction Limits])
       UC14([Authenticate User])
       UC15([Send OTP])
     end

     Cust --> UC1
     Cust --> UC2
     Cust --> UC3
     Cust --> UC4
     Cust --> UC5
     Cust --> UC6
     Cust --> UC7
     Cust --> UC8

     Admin --> UC1
     Admin --> UC9
     Admin --> UC10
     Admin --> UC11
     Admin --> UC12
     Admin --> UC13

     UC1 -.includes.-> UC14
     UC4 -.includes.-> UC15
     UC5 -.includes.-> UC15
   ```

   In the conventional stick-figure notation:

   ```
                     +--------------------------------------+
                     |      Online Banking System           |
                     |                                      |
     Customer        |   ( Login ) --<<include>>--> (Authenticate User)
        O            |                                      |
       /|\ ----------|-> ( View Account Balance )           |
       / \           |                                      |
                     |-> ( View Transaction History )       |
                     |                                      |
                     |-> ( Transfer Funds ) --<<include>>--> (Send OTP)
                     |                                      |
                     |-> ( Pay Utility Bill )               |
                     |                                      |
                     |-> ( Request Cheque Book )            |
                     |                                      |
                     |-> ( Change Password )                |
                     |                                      |
                     |-> ( Download Statement )             |
                     |                                      |
     Bank Admin      |-> ( Manage Customer Accounts )       |
        O            |                                      |
       /|\ ----------|-> ( Approve Account Opening )        |
       / \           |                                      |
                     |-> ( Block / Unblock Account )        |
                     |                                      |
                     |-> ( Generate Reports )               |
                     |                                      |
                     |-> ( Set Transaction Limits )         |
                     +--------------------------------------+
   ```

   Explanation of the elements:

   - Actors, drawn as stick figures outside the system boundary: Customer and Bank Admin. An actor is a role, not a person, so one individual could act as both.
   - Use cases, drawn as ovals inside the boundary: each is a complete piece of functionality that delivers value to an actor. Each is named with a verb phrase.
   - The system boundary, drawn as a rectangle, separates what is inside the system from what is outside it.
   - Association, a plain line, means that the actor participates in the use case.
   - Include, a dashed arrow labelled <<include>>, means that the base use case always incorporates the included one. Login always includes Authenticate User, and a funds transfer always includes sending a one-time password.
   - Extend, a dashed arrow labelled <<extend>>, would mean an optional behaviour that occurs only under a condition, for example "Transfer Funds" extended by "Charge Excess Transaction Fee" when a limit is exceeded.
   - Generalisation between actors could be added if, for example, a Bank Admin were also a Customer.

   Use cases shared by both actors: Login, and by extension logout and password change. This is shown by lines from both actors to the same oval.

   Points that a good answer should state:
   - The diagram shows what the system does, not how it does it. It contains no logic, no sequence and no data structures.
   - Each use case should be named from the actor's point of view and should deliver something the actor recognises as valuable. "Validate account number" is not a use case; it is a step inside one.
   - The diagram is only the summary; each use case is described in detail in a separate specification giving the actor, the preconditions, the main flow, the alternative flows, the exceptions and the postconditions.
   - External systems can also be actors. Here a Payment Gateway and a Core Banking Server would be secondary actors, drawn on the right of the boundary.
3. **Draw a class diagram for an E-commerce website where customer can view different products, can pay either by card or cash.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 401 (ET: BUET)]*


   Answer: Class diagram for an e-commerce website in which a customer can view products and pay by card or by cash.

   ```mermaid
   classDiagram
     class Customer {
       -int customerId
       -String name
       -String email
       -String phone
       -String shippingAddress
       +register()
       +login()
       +viewProducts() List~Product~
       +addToCart(Product, int)
       +placeOrder() Order
     }

     class Product {
       -int productId
       -String name
       -String description
       -double price
       -int stockQuantity
       -String category
       +getDetails() String
       +checkAvailability(int) boolean
       +reduceStock(int)
     }

     class Cart {
       -int cartId
       -double subtotal
       +addItem(Product, int)
       +removeItem(Product)
       +updateQuantity(Product, int)
       +calculateSubtotal() double
       +clear()
     }

     class CartItem {
       -int quantity
       -double unitPrice
       +getLineTotal() double
     }

     class Order {
       -int orderId
       -Date orderDate
       -String status
       -double totalAmount
       -String deliveryAddress
       +confirm()
       +cancel()
       +track() String
     }

     class Payment {
       <<abstract>>
       -int paymentId
       -double amount
       -Date paymentDate
       -String status
       +processPayment()* boolean
       +generateReceipt() String
     }

     class CardPayment {
       -String cardNumber
       -String cardHolderName
       -Date expiryDate
       -String cvv
       -String cardType
       +processPayment() boolean
       +validateCard() boolean
       +authorize() boolean
     }

     class CashPayment {
       -String collectedBy
       -Date collectionDate
       -double amountReceived
       -double changeGiven
       +processPayment() boolean
       +calculateChange() double
     }

     Customer "1" --> "0..1" Cart : owns
     Cart "1" *-- "0..*" CartItem : contains
     CartItem "0..*" --> "1" Product : refers to
     Customer "1" --> "0..*" Order : places
     Order "1" --> "1" Payment : settled by
     Payment <|-- CardPayment
     Payment <|-- CashPayment
   ```

   Explanation of the design decisions:

   - Payment is abstract, with processPayment declared abstract. Neither a generic payment nor an object of class Payment can exist; only a card payment or a cash payment can. This forces every new payment type to implement the operation.

   - CardPayment and CashPayment inherit from Payment. This is the "is-a" relationship: a card payment is a payment. Their attributes differ completely, which is exactly why they are separate classes rather than one class with a type field and a great many null columns.

   - The Order class holds a reference of type Payment, not of type CardPayment. At run time the reference may hold either subclass, and calling processPayment() dispatches to the right implementation. This is run-time polymorphism, and its practical value is that mobile banking can be added later as a third subclass without changing the Order class at all.

   - CartItem is an association class between Cart and Product, holding the quantity and the unit price at the time the item was added. Storing the price here rather than reading it from Product matters, because the price of a product may change after the customer adds it to the cart.

   - Cart to CartItem is a composition, shown by the filled diamond: an item cannot exist without its cart, and clearing the cart destroys the items.

   - CartItem to Product is a plain association: the product exists independently and is shared by many carts.

   - Customer to Cart has multiplicity 0..1, because a customer may not yet have an active cart.

   Cash on delivery, which the question implies: the CashPayment class models payment at the moment of delivery, so it records who collected the money, when, how much was received and how much change was given. Its status remains pending until the delivery is completed, which is why status is an attribute of Payment rather than of Order alone.

   UML notation used:
   - Minus for private attributes, plus for public operations.
   - An abstract class is marked with the stereotype, and abstract operations with an asterisk.
   - A hollow triangle points to the superclass, indicating inheritance.
   - A filled diamond indicates composition; a plain line an association.
   - Multiplicities appear at both ends of each association.
4. **Consider the following buy a product description. Customer browses catalog, selects items to buy and then goes to check out. Customer fills in shipping information (address, receive time). System presents full pricing information and customer fills in credit card information. System authorizes purchase, confirms sale and sends confirming email to customer. Draw a use case diagram for the above system.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*


   Answer: Use case diagram for the described purchase process.

   The description in steps: the customer browses the catalogue, selects items to buy, goes to check out, fills in shipping information, is shown the full pricing, enters credit card information; the system authorises the purchase, confirms the sale and sends a confirming email.

   ```mermaid
   flowchart LR
     Cust((Customer))
     Bank((Payment Gateway))
     Mail((Email Service))

     subgraph SYS[Online Shopping System]
       UC1([Browse Catalog])
       UC2([Select Items])
       UC3([Checkout])
       UC4([Enter Shipping Information])
       UC5([Display Pricing Information])
       UC6([Enter Credit Card Information])
       UC7([Authorize Purchase])
       UC8([Confirm Sale])
       UC9([Send Confirmation Email])
     end

     Cust --> UC1
     Cust --> UC2
     Cust --> UC3
     Cust --> UC4
     Cust --> UC6

     UC3 -.include.-> UC4
     UC3 -.include.-> UC5
     UC3 -.include.-> UC6
     UC3 -.include.-> UC7
     UC7 -.include.-> UC8
     UC8 -.include.-> UC9

     UC7 --> Bank
     UC9 --> Mail
   ```

   In the conventional notation:

   ```
                      +----------------------------------------+
                      |       Online Shopping System           |
     Customer         |                                        |        Payment
        O             |   ( Browse Catalog )                   |        Gateway
       /|\ -----------|-> ( Select Items )                     |           O
       / \            |                                        |          /|\
                      |-> ( Checkout )                         |          / \
                      |        |                               |
                      |        |--<<include>>--> ( Enter Shipping Info )
                      |        |--<<include>>--> ( Display Pricing )
                      |        |--<<include>>--> ( Enter Card Info )
                      |        |--<<include>>--> ( Authorize Purchase )-----+
                      |                                  |                 |
                      |                             <<include>>            |
                      |                                  v                 |
                      |                          ( Confirm Sale )          |
                      |                                  |                 |
                      |                             <<include>>            |
                      |                                  v                 |
                      |                     ( Send Confirmation Email )----|--> Email
                      +----------------------------------------+          |    Service
   ```

   Actors identified:
   - Customer: the primary actor, who initiates the process and derives value from it.
   - Payment Gateway: a secondary actor, an external system that authorises the card transaction. It is drawn on the right of the boundary by convention.
   - Email Service: a secondary actor, the external system that delivers the confirming message.

   Use cases identified from the description, one for each activity that delivers recognisable value:
   - Browse Catalog
   - Select Items
   - Checkout, which is the central use case
   - Enter Shipping Information
   - Display Pricing Information
   - Enter Credit Card Information
   - Authorize Purchase
   - Confirm Sale
   - Send Confirmation Email

   Relationships:
   - Include, shown by a dashed arrow labelled <<include>>: the base use case always performs the included one. Checkout always includes entering shipping information, showing the pricing, taking the card details and authorising the purchase. Authorising always leads to confirming the sale, and confirming always sends the email.
   - Extend, shown by a dashed arrow labelled <<extend>>, would be used for optional behaviour. Examples that could be added here: "Apply Discount Coupon" extending Checkout, or "Handle Payment Failure" extending Authorize Purchase.
   - Association, a plain line, connects an actor to a use case in which it participates.

   The main flow of the Checkout use case, written out as it would appear in the use case specification that accompanies the diagram:

   1. Precondition: the customer has selected at least one item and is logged in.
   2. The customer initiates checkout.
   3. The system requests the shipping address and the preferred delivery time.
   4. The customer supplies them.
   5. The system displays the full pricing: item subtotal, shipping charge, tax and grand total.
   6. The customer supplies the credit card details.
   7. The system sends an authorisation request to the payment gateway.
   8. The gateway authorises the transaction.
   9. The system confirms the sale, reduces the stock and creates the order record.
   10. The system sends a confirming email.
   11. Postcondition: the order exists with status confirmed, and the customer has been notified.

   Alternative and exception flows, which a complete specification must include:
   - At step 8, if the gateway declines the card, the system informs the customer and returns to step 6.
   - At step 9, if an item has gone out of stock since selection, the system informs the customer and returns to the cart.
   - At step 10, if the email cannot be sent, the order still stands and the message is queued for retry. The sale must not be reversed because an email failed.

   Points worth stating about use case diagrams generally:
   - They show what the system does, not how. There is no sequence, no logic and no data in the diagram itself.
   - Each use case is named as a verb phrase from the actor's point of view.
   - The diagram is a summary; the value lies in the accompanying specifications with their main, alternative and exception flows.
5. **Library management class diagram:** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*


   Answer: Class diagram for a library management system.

   ```mermaid
   classDiagram
     class Library {
       -String name
       -String address
       +addBook(Book)
       +removeBook(Book)
       +searchBook(String) List~Book~
       +registerMember(Member)
     }

     class Person {
       <<abstract>>
       -int id
       -String name
       -String address
       -String phone
       -String email
       +getDetails() String
     }

     class Member {
       -int membershipId
       -Date joinDate
       -Date expiryDate
       -int booksIssued
       -double outstandingFine
       +borrowBook(Book) boolean
       +returnBook(Book)
       +reserveBook(Book)
       +payFine(double)
       +canBorrow() boolean
     }

     class Librarian {
       -int staffId
       -String designation
       -double salary
       +issueBook(Book, Member)
       +acceptReturn(Loan)
       +addBook(Book)
       +calculateFine(Loan) double
       +generateReport()
     }

     class Book {
       -String isbn
       -String title
       -String author
       -String publisher
       -int publicationYear
       -String category
       -int totalCopies
       -int availableCopies
       +isAvailable() boolean
       +getDetails() String
     }

     class BookCopy {
       -String accessionNumber
       -String status
       -String shelfLocation
       -Date acquisitionDate
       +markIssued()
       +markAvailable()
     }

     class Loan {
       -int loanId
       -Date issueDate
       -Date dueDate
       -Date returnDate
       -String status
       +calculateFine() double
       +isOverdue() boolean
       +renew() boolean
     }

     class Reservation {
       -int reservationId
       -Date reservationDate
       -String status
       +cancel()
       +notifyMember()
     }

     class Fine {
       -int fineId
       -double amount
       -Date fineDate
       -boolean isPaid
       +pay()
     }

     Person <|-- Member
     Person <|-- Librarian
     Library "1" *-- "0..*" Book : holds
     Book "1" *-- "1..*" BookCopy : has copies
     Member "1" --> "0..*" Loan : takes
     BookCopy "1" --> "0..*" Loan : is lent through
     Librarian "1" --> "0..*" Loan : issues
     Member "1" --> "0..*" Reservation : makes
     Book "1" --> "0..*" Reservation : is reserved in
     Loan "1" --> "0..1" Fine : may incur
   ```

   Explanation of the design decisions:

   - Person is an abstract superclass holding what a Member and a Librarian have in common: identity, name, address and contact details. Both inherit from it, which removes duplication and expresses the "is-a" relationship. No object of class Person can exist.

   - The distinction between Book and BookCopy is the most important decision in this model, and it is the one most often missed. Book represents the title, that is the bibliographic record with its ISBN, author and publisher. BookCopy represents one physical volume on the shelf, with its own accession number and its own status. A library with five copies of the same title has one Book and five BookCopy objects. Without this distinction it is impossible to record which particular copy a member has borrowed, or that copy number 3 is damaged while the others are fine.

   - Loan is an association class between Member and BookCopy. It carries the information that belongs to the relationship rather than to either class: the issue date, the due date, the return date and the status. The same member may borrow the same copy on different occasions, and each occasion is a separate Loan.

   - Fine is separated from Loan rather than being an attribute of it, because a fine has its own lifecycle: it is created, it may be waived, and it is paid, possibly long after the book is returned.

   - Reservation connects a Member to a Book, not to a BookCopy, because a member reserves the title and is satisfied by whichever copy becomes free first.

   - Library to Book is a composition, since the catalogue record has no meaning outside the library; Book to BookCopy is also a composition, since a physical copy is a copy of a particular title.

   Business rules that the model supports:
   - canBorrow() checks the member's outstanding fine, the number of books already issued against the limit, and whether the membership has expired.
   - isOverdue() compares the due date with the current date.
   - calculateFine() multiplies the days overdue by the daily rate.
   - availableCopies on Book is derived: it is the count of BookCopy objects whose status is available.

   UML notation used: a hollow triangle for inheritance, a filled diamond for composition, a plain arrow for association, multiplicities at both ends, minus for private attributes and plus for public operations.
6. **Draw A class diagram. A token-ring based local area network (LAN) is a network consisting of nodes in which network packets are sent around. Every node has a unique name within the network, and refers to its next node. Different kinds of nodes exist: Workstations are originators of messages; servers and printers are network nodes that can receive messages. Packets contain an originator a destination and content, and are sent around on a network. A LAN is a circular configuration of nodes.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*


   Answer: Class diagram for a token-ring local area network.

   Reading the requirements: a LAN is a circular configuration of nodes; every node has a unique name and refers to its next node; workstations originate messages; servers and printers can receive messages; a packet contains an originator, a destination and content, and is sent around the network.

   ```mermaid
   classDiagram
     class LAN {
       -String networkId
       -int nodeCount
       +addNode(Node)
       +removeNode(Node)
       +findNode(String) Node
       +isCircular() boolean
     }

     class Node {
       <<abstract>>
       -String name
       +accept(Packet)*
       +send(Packet)
       +getNextNode() Node
     }

     class Workstation {
       -String userName
       +originate(Packet)
       +accept(Packet)
     }

     class Server {
       -int storageCapacity
       -String operatingSystem
       +accept(Packet)
       +processRequest(Packet)
     }

     class Printer {
       -String model
       -int pagesPerMinute
       -boolean isBusy
       +accept(Packet)
       +printJob(Packet)
     }

     class Packet {
       -int packetId
       -String content
       -Date timestamp
       +getOriginator() Node
       +getDestination() Node
     }

     LAN "1" *-- "3..*" Node : consists of
     Node "1" --> "1" Node : next
     Node <|-- Workstation
     Node <|-- Server
     Node <|-- Printer
     Packet "0..*" --> "1" Workstation : originator
     Packet "0..*" --> "1" Node : destination
   ```

   Explanation of each modelling decision:

   - Node is an abstract superclass. Every kind of node has a unique name and a reference to the next node, so those belong in the superclass. accept(Packet) is abstract, because every concrete kind of node handles an incoming packet differently: a server processes a request, a printer prints, a workstation displays.

   - Workstation, Server and Printer inherit from Node. This is the "is-a" relationship: a printer is a node.

   - The self-association Node to Node with the role name "next" and multiplicity 1 to 1 is the crucial element. It captures the requirement that every node refers to its next node, and the fact that both ends have multiplicity 1 is what makes the configuration a ring rather than a chain: every node has exactly one successor and is the successor of exactly one node. In UML this is drawn as a line from the class back to itself, labelled with the role name at the arrow end.

   - LAN to Node is a composition, with multiplicity 3..* because a meaningful ring needs at least three nodes. A node does not exist outside its network, so the diamond is filled.

   - Packet has two associations to nodes. The originator is constrained to be a Workstation, because the requirement states that workstations are the originators of messages. The destination is any Node, since servers and printers can receive them. Modelling these as two separate associations with different target types is what captures that asymmetry; a single "involves" association would lose it.

   - Content, an identifier and a timestamp are attributes of Packet.

   Constraints that the diagram cannot express graphically and which are added as notes in UML:
   - {The name of every Node in a LAN is unique}
   - {Following the next reference from any node returns to that node, so the configuration is circular}
   - {The originator of a Packet must be a Workstation}

   A design point worth stating: an alternative model would introduce an interface Receiver, implemented by Server and Printer but not by Workstation, and a separate interface Originator implemented by Workstation. That would express the requirement more precisely, since it would make it impossible at compile time for a printer to originate a packet. The inheritance model above is simpler and is what the question's wording most directly suggests, but mentioning the interface alternative shows understanding of the trade-off between simplicity and precision in a model.

   How a packet travels, which the diagram implies: a workstation creates a packet with itself as originator and some node as destination, and passes it to its next node. Each node in turn examines the destination; if the packet is not for it, it passes the packet to its own next node. The packet therefore circulates until it reaches its destination, which is exactly the behaviour of a token ring.
7. **(খ) একটি লাইব্রেরি ব্যবস্থাপনা সিস্টেম এর জন্যে Use Case Diagram অঙ্কন করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*


   Answer: লাইব্রেরি ব্যবস্থাপনা সিস্টেমের জন্য Use Case Diagram:

   ```mermaid
   flowchart LR
     Mem((Member))
     Lib((Librarian))
     Adm((Administrator))

     subgraph LMS[Library Management System]
       UC1([Search Book])
       UC2([Borrow Book])
       UC3([Return Book])
       UC4([Reserve Book])
       UC5([Renew Book])
       UC6([Pay Fine])
       UC7([View Borrowing History])
       UC8([Issue Book])
       UC9([Accept Return])
       UC10([Calculate Fine])
       UC11([Add / Update Book])
       UC12([Register Member])
       UC13([Generate Report])
       UC14([Manage Staff Accounts])
       UC15([Verify Membership])
       UC16([Check Availability])
     end

     Mem --> UC1
     Mem --> UC2
     Mem --> UC3
     Mem --> UC4
     Mem --> UC5
     Mem --> UC6
     Mem --> UC7

     Lib --> UC8
     Lib --> UC9
     Lib --> UC11
     Lib --> UC12
     Lib --> UC13

     Adm --> UC13
     Adm --> UC14
     Adm --> UC11

     UC2 -.include.-> UC15
     UC2 -.include.-> UC16
     UC9 -.include.-> UC10
     UC5 -.include.-> UC16
   ```

   প্রচলিত চিত্র আকারে:

   ```
                        +--------------------------------------------+
                        |      Library Management System             |
      Member            |                                            |
         O              |   ( Search Book )                          |
        /|\ ------------|-> ( Borrow Book ) --<<include>>--> (Verify Membership)
        / \             |          |--<<include>>--> (Check Availability)
                        |                                            |
                        |-> ( Return Book )                          |
                        |-> ( Reserve Book )                         |
                        |-> ( Renew Book )                           |
                        |-> ( Pay Fine )                             |
                        |-> ( View Borrowing History )               |
                        |                                            |
      Librarian         |-> ( Issue Book )                           |
         O              |-> ( Accept Return ) --<<include>>--> (Calculate Fine)
        /|\ ------------|-> ( Add / Update Book )                    |
        / \             |-> ( Register Member )                      |
                        |-> ( Generate Report )                      |
                        |                                            |
      Administrator     |-> ( Manage Staff Accounts )                |
         O              |-> ( Generate Report )                      |
        /|\ ------------|-> ( Add / Update Book )                    |
        / \             +--------------------------------------------+
   ```

   উপাদানসমূহের ব্যাখ্যা:

   Actor (অভিনেতা): সিস্টেমের বাইরে অবস্থিত ব্যক্তি বা ব্যবস্থা, যারা সিস্টেমের সঙ্গে মিথস্ক্রিয়া করে। এখানে তিনজন:
   - Member (সদস্য): বই খোঁজেন, ধার নেন, ফেরত দেন, সংরক্ষণ করেন, নবায়ন করেন ও জরিমানা পরিশোধ করেন।
   - Librarian (গ্রন্থাগারিক): বই ইস্যু ও গ্রহণ করেন, নতুন বই যোগ করেন, সদস্য নিবন্ধন করেন ও প্রতিবেদন তৈরি করেন।
   - Administrator (প্রশাসক): কর্মীদের অ্যাকাউন্ট ব্যবস্থাপনা করেন এবং সামগ্রিক প্রতিবেদন দেখেন।

   Use Case (ব্যবহার-ঘটনা): ডিম্বাকৃতিতে আঁকা প্রতিটি সম্পূর্ণ কাজ, যা কোনো actor এর কাছে মূল্যবান একটি ফল এনে দেয়। প্রতিটির নাম ক্রিয়াপদ দিয়ে শুরু হয়।

   System Boundary (সিস্টেমের সীমানা): আয়তক্ষেত্র, যা ভেতরে সিস্টেমের কাজ এবং বাইরে actor দের আলাদা করে।

   সম্পর্কসমূহ:
   - Association (সংযোগ): সরল রেখা, যা বোঝায় ওই actor ওই use case এ অংশ নেন।
   - Include (<<include>>): ভাঙা তীর; মূল use case সবসময় অন্তর্ভুক্ত use case টি সম্পাদন করে। "Borrow Book" সবসময় সদস্যপদ যাচাই ও প্রাপ্যতা পরীক্ষা করে; "Accept Return" সবসময় জরিমানা হিসাব করে।
   - Extend (<<extend>>): ভাঙা তীর; ঐচ্ছিক আচরণ, যা কেবল নির্দিষ্ট শর্তে ঘটে। যেমন "Return Book" কে extend করতে পারে "Charge Damage Fee", যা কেবল বই ক্ষতিগ্রস্ত হলে ঘটে।
   - Generalization (সাধারণীকরণ): Administrator ও Librarian উভয়ই Staff হলে, একটি সাধারণ Staff actor তৈরি করে দুজনকে তার বিশেষ রূপ হিসেবে দেখানো যেত।

   "Borrow Book" use case এর বিস্তারিত বিবরণ, যা চিত্রের সঙ্গে অবশ্যই লিখতে হয়:
   - Actor: Member
   - Precondition: সদস্য লগইন করেছেন এবং তাঁর সদস্যপদ বৈধ।
   - প্রধান প্রবাহ: ১. সদস্য বই নির্বাচন করেন। ২. সিস্টেম সদস্যপদ যাচাই করে। ৩. সিস্টেম বইয়ের কপি প্রাপ্য কিনা দেখে। ৪. সিস্টেম সদস্যের ধার নেওয়ার সীমা ও বকেয়া জরিমানা পরীক্ষা করে। ৫. গ্রন্থাগারিক বই ইস্যু করেন। ৬. সিস্টেম ধারের রেকর্ড তৈরি করে ও ফেরতের তারিখ নির্ধারণ করে। ৭. প্রাপ্য কপির সংখ্যা কমে যায়।
   - বিকল্প প্রবাহ: বই প্রাপ্য না হলে সিস্টেম সংরক্ষণের প্রস্তাব দেয়; সীমা অতিক্রান্ত হলে বা জরিমানা বকেয়া থাকলে অনুরোধ প্রত্যাখ্যাত হয়।
   - Postcondition: ধারের রেকর্ড তৈরি হয়েছে এবং কপিটির অবস্থা "issued" হয়েছে।

   গুরুত্বপূর্ণ নীতি: Use case diagram দেখায় সিস্টেম কী করে, কীভাবে করে তা নয়। এতে কোনো ক্রম, যুক্তি বা ডেটা কাঠামো থাকে না; সেগুলো sequence diagram ও class diagram এ দেখানো হয়।
8. **How do you model the following situation with a UML class diagram the car fleet of a car rental contains multiple cars, one car belongs to exactly one car fleet.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*


   Answer: The situation is that a car fleet contains multiple cars, and one car belongs to exactly one car fleet.

   The correct model is a composition, or at minimum a strong aggregation, from CarFleet to Car, with multiplicity 1 to 1..* on one side and exactly 1 on the other.

   ```mermaid
   classDiagram
     class CarRental {
       -int rentalId
       -String companyName
       +getFleet() CarFleet
     }

     class CarFleet {
       -int fleetId
       -String location
       -int capacity
       +addCar(Car)
       +removeCar(Car)
       +getAvailableCars() List~Car~
       +getFleetSize() int
     }

     class Car {
       -String registrationNumber
       -String make
       -String model
       -int year
       -String status
       -double dailyRate
       +isAvailable() boolean
       +rent()
       +returnCar()
     }

     CarRental "1" *-- "1..*" CarFleet : has
     CarFleet "1" *-- "1..*" Car : contains
   ```

   In plain UML notation:

   ```
   +-------------+                    +---------+
   |  CarFleet   |◆-------------------|   Car   |
   +-------------+ 1            1..*  +---------+
   | -fleetId    |                    | -regNo  |
   | -location   |                    | -make   |
   +-------------+                    | -model  |
   | +addCar()   |                    +---------+
   | +removeCar()|                    | +rent() |
   +-------------+                    +---------+
   ```
   The filled diamond is placed at the CarFleet end, because the fleet is the whole and the car is the part.

   Reading the multiplicities:
   - At the Car end, 1..* means one fleet contains one or more cars. If an empty fleet is permitted, 0..* is used instead.
   - At the CarFleet end, 1 means each car belongs to exactly one fleet, which is precisely what the question states. It is this 1, rather than 0..1 or *, that expresses the constraint.

   Why composition rather than aggregation:
   - Composition, the filled diamond, means the part cannot belong to more than one whole and its lifetime is bound to the whole. Since a car belongs to exactly one fleet, composition is the correct choice.
   - Aggregation, the hollow diamond, would allow a car to belong to several fleets or to none, which contradicts the requirement.
   - A plain association would express only that the two classes are related, without capturing the whole-part nature of the relationship.

   The three relationships compared, since this distinction is the point of the question:

   | Relationship | Symbol | Meaning | Lifetime | Example |
   |---|---|---|---|---|
   | Association | plain line | The classes are related in some way | Independent | A Driver drives a Car |
   | Aggregation | hollow diamond | Whole-part, but the part can exist alone and can be shared | Independent | A Department has Teachers; a teacher survives the department |
   | Composition | filled diamond | Whole-part, the part belongs to exactly one whole and dies with it | Dependent | A CarFleet contains Cars; a House contains Rooms |

   A qualification worth stating: whether this particular case is composition or aggregation depends on how the business treats a car when a fleet is dissolved. If the car is simply transferred to another fleet, the relationship is really a strong aggregation, since the car survives. If the fleet is the only way a car exists in the system and dissolving it removes the cars, it is composition. The question says a car belongs to exactly one fleet, which fixes the multiplicity but not the lifetime; a complete answer should note this and state the assumption made.

   Extension of the model: if a car may be moved between fleets over time, that history is itself information, and it would be modelled as an association class FleetAssignment carrying the start date and the end date, with Car and CarFleet associated through it.
9. **(ক) Typical web-based login system এর জন্য sequence diagram আঁকুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 778 (ET: N/A)]*


   Answer: Typical web-based login system এর জন্য Sequence Diagram:

   ```mermaid
   sequenceDiagram
     actor U as User
     participant B as Browser
     participant S as Web Server / Controller
     participant A as Authentication Service
     participant DB as Database
     participant SS as Session Store

     U->>B: লগইন পাতা চান
     B->>S: GET /login
     S-->>B: লগইন ফর্ম + CSRF token
     B-->>U: ফর্ম প্রদর্শন

     U->>B: ইউজারনেম ও পাসওয়ার্ড দেন
     B->>S: POST /login (credentials, CSRF token) over HTTPS

     S->>S: CSRF token যাচাই
     S->>S: ইনপুট ফরম্যাট যাচাই

     alt ইনপুট অবৈধ
       S-->>B: ত্রুটিসহ ফর্ম পুনরায়
       B-->>U: "সঠিক তথ্য দিন"
     else ইনপুট বৈধ
       S->>A: authenticate(username, password)
       A->>DB: SELECT * FROM users WHERE email = ?
       DB-->>A: user record (password hash সহ) অথবা কিছুই নয়

       alt ব্যবহারকারী নেই বা পাসওয়ার্ড ভুল
         A->>DB: ব্যর্থ চেষ্টার সংখ্যা বাড়ানো
         A-->>S: AuthResult.failure()
         S-->>B: সাধারণ ত্রুটি বার্তা
         B-->>U: "ইউজারনেম বা পাসওয়ার্ড ভুল"
       else পাসওয়ার্ড সঠিক
         A->>A: bcrypt দিয়ে hash মিলিয়ে দেখা
         A->>DB: last_login হালনাগাদ, ব্যর্থ গণনা শূন্য
         A-->>S: AuthResult.success(user)
         S->>SS: নতুন session তৈরি, session ID পুনর্গঠন
         SS-->>S: session token
         S-->>B: 302 Redirect to /dashboard + Set-Cookie (HttpOnly, Secure)
         B->>S: GET /dashboard (cookie সহ)
         S->>SS: session যাচাই
         SS-->>S: বৈধ
         S-->>B: ড্যাশবোর্ড পাতা
         B-->>U: ড্যাশবোর্ড প্রদর্শন
       end
     end
   ```

   টেক্সট আকারে ক্রমটি:

   ```
   User    Browser   Server    AuthService   Database   SessionStore
    |         |         |           |            |            |
    |--চান--->|         |           |            |            |
    |         |--GET--->|           |            |            |
    |         |<--ফর্ম--|           |            |            |
    |<--দেখান-|         |           |            |            |
    |--তথ্য-->|         |           |            |            |
    |         |--POST-->|           |            |            |
    |         |         |--auth---->|            |            |
    |         |         |           |--SELECT--->|            |
    |         |         |           |<--record---|            |
    |         |         |<--result--|            |            |
    |         |         |--------create session------------->|
    |         |         |<-------------token-----------------|
    |         |<--302---|           |            |            |
    |<--ড্যাশ-|         |           |            |            |
   ```

   Sequence diagram এর উপাদানসমূহ:
   - Lifeline: প্রতিটি অংশগ্রহণকারীর নিচে নেমে যাওয়া উল্লম্ব ভাঙা রেখা, যা সময়ের প্রবাহ নির্দেশ করে। সময় উপর থেকে নিচে বয়ে যায়।
   - Activation bar: lifeline এর ওপর সরু আয়তক্ষেত্র, যা দেখায় ওই সময়ে অংশগ্রহণকারীটি সক্রিয়।
   - Synchronous message: ভরাট তীরযুক্ত অবিচ্ছিন্ন রেখা; প্রেরক উত্তরের জন্য অপেক্ষা করে।
   - Return message: ভাঙা রেখা ও খোলা তীর।
   - alt fragment: বিকল্প পথ (if-else) দেখায়।
   - opt fragment: ঐচ্ছিক অংশ দেখায়।
   - loop fragment: পুনরাবৃত্তি দেখায়।

   নিরাপত্তার দিকগুলো, যা এই নকশায় অবশ্যই থাকতে হবে:
   - পাসওয়ার্ড কখনোই সরাসরি সংরক্ষণ করা হয় না; bcrypt, scrypt বা Argon2 দিয়ে salt সহ hash করে রাখা হয়।
   - ব্যবহারকারী না থাকা এবং পাসওয়ার্ড ভুল — দুই ক্ষেত্রেই একই সাধারণ বার্তা দেওয়া হয়, যাতে আক্রমণকারী কোন অ্যাকাউন্ট আছে তা জানতে না পারে।
   - সফল লগইনের পর session ID পুনর্গঠন করা হয়, যাতে session fixation আক্রমণ ঠেকানো যায়।
   - CSRF token ব্যবহার করা হয়।
   - সব যোগাযোগ HTTPS এ হয়, এবং cookie তে HttpOnly, Secure ও SameSite পতাকা দেওয়া হয়।
   - নির্দিষ্টসংখ্যক ব্যর্থ চেষ্টার পর অ্যাকাউন্ট সাময়িকভাবে লক করা হয়।
   - সব চেষ্টা, সফল ও ব্যর্থ, সময় ও উৎস ঠিকানাসহ লগবদ্ধ করা হয়।
   - ডেটাবেজ কোয়েরিতে parameterized query ব্যবহার করা হয়, যাতে SQL injection সম্ভব না হয়।

   Sequence diagram এর উপযোগিতা: এটি দেখায় কোন বার্তা কোন ক্রমে কার কাছে যায়, তাই একটি জটিল মিথস্ক্রিয়ার সময়ভিত্তিক আচরণ বুঝতে ও নথিভুক্ত করতে এটি সবচেয়ে কার্যকর UML চিত্র। Class diagram দেখায় কাঠামো, আর sequence diagram দেখায় আচরণ।

## Software Requirements Engineering (8)

1. What is the difference between functional and non-functional requirements? What is requirement validation? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer: Functional and non-functional requirements, and requirement validation.

   Functional requirements state what the system must do. They describe the services, the inputs, the processing and the outputs, and each one can be tested by giving an input and checking the output.
   - A registered user shall be able to log in with an email address and a password.
   - The system shall generate a monthly salary statement for every employee.
   - The system shall send a confirmation email within one minute of an order being placed.
   - The system shall calculate income tax according to the current slab rates.

   Non-functional requirements state how well the system must do it. They are quality attributes and constraints; they do not add a service but constrain the way every service behaves.
   - Performance: the search page shall respond within 2 seconds for 1000 concurrent users.
   - Reliability: availability shall be at least 99.5 percent in a calendar month.
   - Security: all passwords shall be stored as salted hashes; all traffic shall use HTTPS.
   - Usability: a new clerk shall be able to complete a data entry task after 30 minutes of training.
   - Portability: the application shall run on Windows, Linux and Android.
   - Maintainability, scalability, and legal or regulatory compliance also fall here.

   The key differences:
   - Functional requirements define behaviour; non-functional requirements define quality of that behaviour.
   - A missing functional requirement leaves the system incomplete; an unmet non-functional requirement often makes the system unusable even though every function works.
   - Functional requirements are usually easy to state and verify; non-functional ones must be made measurable to be verifiable. "The system shall be fast" is useless; "shall respond in under 2 seconds at the 95th percentile" is testable.
   - Functional requirements are usually local to one module; non-functional ones cut across the whole architecture, which is why they drive architectural decisions.

   Requirement validation is the process of checking that the documented requirements actually define the system the customer wants, before design and coding begin. It answers the question "are we building the right product", whereas requirement verification asks "have we built the product right".

   What is checked during validation:
   - Validity: does the requirement reflect a real need of the stakeholders.
   - Consistency: no requirement contradicts another.
   - Completeness: all functions and constraints the user needs are present.
   - Realism: the requirement can be implemented with the available budget, technology and time.
   - Verifiability: each requirement is written so that a test can prove it was met.
   - Unambiguity: only one interpretation is possible.
   - Traceability: each requirement can be traced to its origin and forward to design and test cases.

   Techniques used:
   - Requirements review or inspection: a team walks through the SRS against a checklist.
   - Prototyping: an executable model is shown to users, who confirm or correct their understanding.
   - Test case generation: writing an acceptance test for each requirement. A requirement for which no test can be written is not verifiable and must be rewritten.
   - Model validation: checking the consistency of the analysis models.
   - Walkthrough with the customer and formal sign-off on the SRS.

   Why it matters: an error discovered at the requirements stage costs a fraction of what the same error costs after delivery. The commonly cited multiplier is that a defect costs about 1 unit to fix during requirements, 10 during design, 100 during coding and far more after release.
2. **Which of the following are not needed in software Requirement Specifications (SRS)?** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*
   * (a) Functional Requirments
   * (b) Non- Functional Requirments
   * (c) Testing Requirments
   * (d) Interface Requirments


   Answer: (c) Testing Requirements.

   An SRS records what the system must do and under what constraints. Functional requirements, non-functional requirements and interface requirements are all part of it. Testing requirements, that is the test plan, test cases and test strategy, belong in a separate document, the Software Test Plan, and are produced by the testing team from the SRS. The SRS makes each requirement verifiable, but it does not contain the tests themselves.
3. **(b) Which contents shoud be consider when you setup a new system?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*


   Answer: Contents to consider when setting up a new system.

   Before a new system is put in place, the following must be settled and documented:

   Requirement and scope
   - The business objective the system must serve and the problems in the present system.
   - Functional requirements: the services the system must provide.
   - Non-functional requirements: performance, availability, security, usability, scalability.
   - The boundary of the system: what is inside and what is left to other systems.

   Feasibility
   - Technical feasibility: is the technology available and does the team have the skill.
   - Economic feasibility: cost-benefit analysis, return on investment, payback period.
   - Operational feasibility: will the users accept and use it.
   - Legal feasibility: data protection rules, licensing, government regulations.
   - Schedule feasibility: can it be delivered in the time available.

   Hardware and infrastructure
   - Server capacity: processor, memory, storage, with growth allowance.
   - Network bandwidth, cabling and topology.
   - Uninterrupted power supply and generator backup.
   - Air conditioning and physical security of the server room.
   - Client machines and peripheral devices.

   Software
   - Operating system, database management system, application server, middleware.
   - Development platform and framework.
   - Licensing: proprietary versus open source, number of seats, renewal cost.

   Data
   - Data migration from the existing system, with cleansing and validation.
   - Database design, storage estimation and growth projection.
   - Backup policy, retention period and tested restore procedure.
   - Archiving of historical data.

   Security
   - Authentication and role-based authorisation.
   - Encryption of data in transit and at rest.
   - Firewall, intrusion detection, antivirus.
   - Audit trail of every significant transaction.
   - Disaster recovery site and recovery time and recovery point objectives.

   People and process
   - Project team structure and responsibilities.
   - Training for end users and for administrators.
   - User manuals, administrator manuals and technical documentation.
   - Change-over strategy: direct, parallel, pilot or phased.
   - Support arrangement after go-live, and the service level agreement.

   Cost and schedule
   - Total cost of ownership: acquisition, licences, training, maintenance, upgrades.
   - Project schedule with milestones and dependencies.
   - Risk register with mitigation plans.
4. **You have been given a responsibility to elicit requirements from a customer, who tells you that he is too busy to meet with you. What should you do?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*


   Answer: The customer is the source of the requirements, so the meeting cannot simply be abandoned; but pressing an unwilling customer is also useless. The correct response is to reduce the demand on the customer's time while still obtaining valid requirements, and to escalate only if that fails.

   What should be done, in order:

   - Explain the consequence politely and in business terms, not technical ones. Building the wrong system wastes the customer's money and time far more than a meeting would. Requirements errors are the most expensive kind of defect, because they propagate into design, code and tests.

   - Ask for a very short meeting, thirty minutes, at a time and place convenient to the customer, and come with a prepared agenda and specific questions. A busy person will often agree to a focused half hour when he will not agree to an open-ended one.

   - Offer alternative low-cost channels: a telephone or video call, a short questionnaire, or answering a numbered list of questions by email at his convenience.

   - Identify other stakeholders. The person who is too busy is often not the only source. Ask him to nominate a proxy, a domain expert or a senior user who works with the process daily and can speak for him. In practice these people give better operational detail than the executive does.

   - Use indirect elicitation techniques that do not need the customer's presence: study the existing system and its documents, forms, reports and manuals; observe the users at work, that is ethnography; study a competitor's or a similar organisation's system; examine the existing database.

   - Build a prototype or a set of mock-up screens from what you have gathered, and send it for review. Reviewing a concrete screen takes a customer five minutes and elicits far more correction than an abstract discussion would; people find it much easier to criticise something in front of them than to specify it from nothing.

   - Document every assumption explicitly and send the assumption list for confirmation, with a note that silence after a stated date will be taken as agreement. This creates a record and often prompts a reply.

   - If the customer still gives no access and no proxy, escalate through the project manager to the sponsor, in writing, recording it as a project risk in the risk register: "requirements may be incomplete or incorrect owing to lack of stakeholder availability".

   What should not be done:
   - Do not guess the requirements and start coding on assumptions alone.
   - Do not simply record "customer unavailable" and stop work.
   - Do not proceed silently, so that the risk is invisible to management until delivery.
5. **(ক) Software development এর ক্ষেত্রে কত প্রকার requirements পাওয়া যায়। উদাহরণসহ requirements সমূহ লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*


   Answer: Software development এ প্রধানত দুই শ্রেণির requirement পাওয়া যায় — functional ও non-functional। এদের সঙ্গে domain requirement ও user/system requirement এর বিভাজনও ব্যবহৃত হয়।

   Functional requirements state what the system must do. They describe the services, the inputs, the processing and the outputs, and each one can be tested by giving an input and checking the output.
   - A registered user shall be able to log in with an email address and a password.
   - The system shall generate a monthly salary statement for every employee.
   - The system shall send a confirmation email within one minute of an order being placed.
   - The system shall calculate income tax according to the current slab rates.

   Non-functional requirements state how well the system must do it. They are quality attributes and constraints; they do not add a service but constrain the way every service behaves.
   - Performance: the search page shall respond within 2 seconds for 1000 concurrent users.
   - Reliability: availability shall be at least 99.5 percent in a calendar month.
   - Security: all passwords shall be stored as salted hashes; all traffic shall use HTTPS.
   - Usability: a new clerk shall be able to complete a data entry task after 30 minutes of training.
   - Portability: the application shall run on Windows, Linux and Android.
   - Maintainability, scalability, and legal or regulatory compliance also fall here.

   The key differences:
   - Functional requirements define behaviour; non-functional requirements define quality of that behaviour.
   - A missing functional requirement leaves the system incomplete; an unmet non-functional requirement often makes the system unusable even though every function works.
   - Functional requirements are usually easy to state and verify; non-functional ones must be made measurable to be verifiable. "The system shall be fast" is useless; "shall respond in under 2 seconds at the 95th percentile" is testable.
   - Functional requirements are usually local to one module; non-functional ones cut across the whole architecture, which is why they drive architectural decisions.

   Domain requirements: এগুলো আসে যে ক্ষেত্রে সফটওয়্যারটি চলবে সেই ক্ষেত্রের নিয়ম থেকে, ব্যবহারকারীর চাওয়া থেকে নয়।
   - ব্যাংকিং সফটওয়্যারে সুদের হিসাব বাংলাদেশ ব্যাংকের নির্ধারিত পদ্ধতিতে হতে হবে।
   - গ্রন্থাগার ব্যবস্থায় কপিরাইট আইন অনুযায়ী নথি অনুলিপি সীমিত রাখতে হবে।
   - এই requirement গুলো প্রায়ই অলিখিত থেকে যায়, কারণ ওই ক্ষেত্রের লোকের কাছে সেগুলো এত সাধারণ যে বলার প্রয়োজন মনে হয় না। এটাই এদের সবচেয়ে বড় ঝুঁকি।

   অন্য একটি বিভাজন — কার জন্য লেখা তার ভিত্তিতে:
   - User requirement: গ্রাহকের ভাষায়, স্বাভাবিক বাক্যে ও চিত্রে লেখা, যা গ্রাহক পড়ে বুঝতে পারেন।
   - System requirement: বিস্তারিত ও কাঠামোবদ্ধ বিবরণ, যা ডেভেলপারদের জন্য লেখা এবং চুক্তির অংশ হয়।

   একটি উদাহরণে সব ধরন একসঙ্গে — একটি অনলাইন ট্রেন টিকিট ব্যবস্থা:
   - Functional: যাত্রী তারিখ ও গন্তব্য দিয়ে আসন খুঁজতে পারবেন; অনলাইনে মূল্য পরিশোধ করতে পারবেন; টিকিট বাতিল করতে পারবেন।
   - Non-functional: ঈদের সময় ৫০,০০০ যুগপৎ ব্যবহারকারী সামলাতে হবে; প্রতিটি অনুসন্ধানের উত্তর ৩ সেকেন্ডের মধ্যে দিতে হবে; কার্ডের তথ্য PCI-DSS মান অনুযায়ী সংরক্ষণ করতে হবে।
   - Domain: একজন যাত্রী একটি জাতীয় পরিচয়পত্রে সর্বোচ্চ চারটি টিকিট কিনতে পারবেন — এটি রেলওয়ের নিয়ম।
6. **(খ) Software Requirement Specification (SRS) বলতে কি বুঝায়? Software Development এর কোন ধাপে SRS তৈরি করা হয়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*


   Answer:    Software Requirement Specification (SRS) is the formal document that records everything the software must do and every constraint under which it must do it. It is the agreed contract between the customer and the development team, and it is the single reference from which design, coding, testing and acceptance all proceed.

   Contents of an SRS, following the IEEE 830 structure:
   - Introduction: purpose, scope, definitions and abbreviations, references, overview.
   - Overall description: product perspective, product functions, user characteristics, operating environment, design and implementation constraints, assumptions and dependencies.
   - Specific requirements: external interface requirements (user, hardware, software, communication interfaces), functional requirements, performance requirements, database requirements, design constraints, and software system attributes such as reliability, availability, security, maintainability and portability.
   - Appendices and index.

   Characteristics of a good SRS: correct, unambiguous, complete, consistent, ranked for importance and stability, verifiable, modifiable and traceable.

   Which stage produces the SRS: the SRS is produced at the end of the requirement analysis and specification phase, which is the second phase of the SDLC, after feasibility study or planning and before design.

   ```mermaid
   flowchart LR
     A[Feasibility Study / Planning] --> B[Requirement Analysis & Specification]
     B --> C[Design]
     C --> D[Coding]
     D --> E[Testing]
     E --> F[Deployment & Maintenance]
     B -.produces.-> S[(SRS Document)]
     S -.input to.-> C
     S -.basis of.-> E
   ```

   The activities of that phase are requirement elicitation or gathering, requirement analysis, requirement specification, which produces the document, and requirement validation, after which the customer signs off. The signed SRS is then frozen under configuration control; further changes go through a formal change control procedure.
7. **Assume that you are going to implement an ecommerce site of “XYZ” company. The CEO of the company is Mr. X. You have to identify the following: (i) Stakeholder (ii) Functional requirements (iii) Non-functional requirements (iv) Deployment requirements** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*


   Answer: Requirements for the e-commerce site of company XYZ.

   (i) Stakeholders — everyone who affects the system or is affected by it.

   Internal
   - Mr. X, the CEO: the project sponsor, who funds the project and owns the business objectives.
   - Sales and marketing team: manage catalogue, pricing, offers and campaigns.
   - Warehouse and inventory staff: maintain stock, pack and dispatch orders.
   - Customer support staff: handle enquiries, returns and complaints.
   - Accounts and finance department: reconcile payments, refunds and settlement.
   - System administrator and IT team: run and maintain the platform.
   - Development team: project manager, analysts, designers, developers, testers.

   External
   - Customers: the primary users, both registered and guest buyers.
   - Sellers or vendors, if the site is a marketplace.
   - Payment gateway provider: bKash, Nagad, SSLCOMMERZ, card networks.
   - Courier and logistics partners: Sundarban, RedX, Pathao and others.
   - SMS and email service providers.
   - Government and regulatory bodies: VAT and tax authority, consumer rights authority, Bangladesh Bank for payment rules.
   - Suppliers of the goods.

   (ii) Functional requirements — what the system must do.

   Customer facing
   - Register with an email or mobile number, and verify by OTP.
   - Log in and log out, with password reset.
   - Browse the catalogue by category and search by keyword, with filters for price, brand and rating.
   - View a product's detail page with images, description, price, stock and reviews.
   - Add items to the cart, change quantity, remove items, and save items to a wishlist.
   - Check out: enter or select a shipping address, choose a delivery option, apply a discount coupon.
   - Pay by card, mobile financial service or cash on delivery.
   - Receive an order confirmation by email and SMS.
   - Track the order status, and view the order history.
   - Request a return or refund within the return window.
   - Write a product review and a rating after delivery.

   Administrative
   - Add, update and remove products, categories and images.
   - Manage stock levels, with an alert when a product falls below its reorder level.
   - View, confirm, dispatch and cancel orders.
   - Manage discount coupons and promotional campaigns.
   - Manage customer accounts and support tickets.
   - Generate reports: daily and monthly sales, best sellers, stock status, revenue by category.

   (iii) Non-functional requirements — how well it must do it.
   - Performance: any page shall load within 3 seconds on a 3G connection; search shall return in under 2 seconds; the system shall support 5,000 concurrent users and 500 orders per hour.
   - Scalability: the architecture shall allow horizontal scaling to handle a tenfold traffic increase during festival sales without redesign.
   - Availability: 99.9 percent uptime, which allows about 43 minutes of downtime a month; planned maintenance only in a declared low-traffic window.
   - Security: HTTPS everywhere; passwords stored as bcrypt hashes; card data never stored on the site, PCI-DSS compliance by delegating to the gateway; protection against SQL injection, XSS and CSRF; role-based access control; a full audit trail of administrative actions.
   - Usability: checkout shall be completable in at most four steps; the site shall be fully responsive on mobile, tablet and desktop; the interface shall be available in Bangla and English.
   - Reliability: no order shall be lost; every payment shall be recorded exactly once, even if the customer's connection drops during payment.
   - Maintainability: modular code, documented APIs, automated test coverage above 70 percent.
   - Compatibility: the latest two versions of Chrome, Firefox, Safari and Edge; Android 8 and above, iOS 13 and above.
   - Legal: VAT shown separately on the invoice; a privacy policy and a return policy displayed; compliance with the consumer rights act.

   (iv) Deployment requirements — what is needed to put it into service and keep it there.
   - Hosting: cloud infrastructure, for example AWS or Azure, with the application servers behind a load balancer in at least two availability zones.
   - Environments: separate development, testing, staging and production environments, with staging matching production in configuration.
   - Database: a managed relational database with a primary and a read replica, automated daily backup and point-in-time recovery.
   - Content delivery network for images and static assets, to cut page load time.
   - Domain name, and an SSL/TLS certificate with automatic renewal.
   - CI/CD pipeline: build, automated test, and deployment with a blue-green or rolling strategy so releases cause no downtime, and with a one-command rollback.
   - Monitoring and alerting: server metrics, application performance monitoring, centralised logs, uptime checks, alerts to the on-call engineer.
   - Integration credentials and sandbox testing for the payment gateway, the SMS gateway and the courier APIs.
   - Data migration plan for existing product and customer data, with validation.
   - Disaster recovery: a documented plan, with the recovery time objective and recovery point objective agreed, and a restore drill performed before go-live.
   - Go-live plan: cut-over schedule, rollback criteria, support roster for the first weeks, and user training for the administrative staff.
8. **Software Requirement Specification (SRS) বলতে কী বোঝেন? Software development -এর কোন স্তরে SRS প্রস্তুত করা হয়?** *[41th BCS 2021 compact it 881 (ET: N/A)]*


   Answer:    Software Requirement Specification (SRS) is the formal document that records everything the software must do and every constraint under which it must do it. It is the agreed contract between the customer and the development team, and it is the single reference from which design, coding, testing and acceptance all proceed.

   Contents of an SRS, following the IEEE 830 structure:
   - Introduction: purpose, scope, definitions and abbreviations, references, overview.
   - Overall description: product perspective, product functions, user characteristics, operating environment, design and implementation constraints, assumptions and dependencies.
   - Specific requirements: external interface requirements (user, hardware, software, communication interfaces), functional requirements, performance requirements, database requirements, design constraints, and software system attributes such as reliability, availability, security, maintainability and portability.
   - Appendices and index.

   Characteristics of a good SRS: correct, unambiguous, complete, consistent, ranked for importance and stability, verifiable, modifiable and traceable.

   Which stage produces the SRS: the SRS is produced at the end of the requirement analysis and specification phase, which is the second phase of the SDLC, after feasibility study or planning and before design.

   ```mermaid
   flowchart LR
     A[Feasibility Study / Planning] --> B[Requirement Analysis & Specification]
     B --> C[Design]
     C --> D[Coding]
     D --> E[Testing]
     E --> F[Deployment & Maintenance]
     B -.produces.-> S[(SRS Document)]
     S -.input to.-> C
     S -.basis of.-> E
   ```

   The activities of that phase are requirement elicitation or gathering, requirement analysis, requirement specification, which produces the document, and requirement validation, after which the customer signs off. The signed SRS is then frozen under configuration control; further changes go through a formal change control procedure.

## Software Project Management & Organization (7)

1. **সংগঠনিক নির্দেশকগুলো কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer: সাংগঠনিক নির্দেশক বা organizational indicator বলতে বোঝায় সেই পরিমাপযোগ্য সূচকগুলো, যা দিয়ে একটি প্রতিষ্ঠান বা প্রকল্পের অবস্থা, অগ্রগতি ও কার্যকারিতা বোঝা যায়। সফটওয়্যার প্রকল্প ব্যবস্থাপনায় এগুলো ব্যবহৃত হয় প্রকল্পের স্বাস্থ্য মাপতে ও সিদ্ধান্ত নিতে।

   প্রকল্পভিত্তিক নির্দেশক
   - Schedule variance: পরিকল্পিত সময় ও প্রকৃত সময়ের পার্থক্য।
   - Cost variance ও budget utilization: বরাদ্দকৃত অর্থের কতটা ব্যয় হয়েছে এবং কাজের অনুপাতে তা যথাযথ কিনা।
   - Earned value ও তার অনুপাতসমূহ — CPI ও SPI।
   - Milestone completion rate: নির্ধারিত মাইলফলকের কতগুলো সময়মতো অর্জিত হয়েছে।
   - Scope creep: অনুমোদিত পরিধির বাইরে যোগ হওয়া কাজের পরিমাণ।

   গুণগত নির্দেশক
   - Defect density: প্রতি হাজার লাইন কোডে বা প্রতি function point এ পাওয়া ত্রুটির সংখ্যা।
   - Defect removal efficiency: মুক্তির আগে ধরা পড়া ত্রুটির অনুপাত।
   - Test coverage: স্বয়ংক্রিয় পরীক্ষায় কতটুকু কোড আচ্ছাদিত।
   - Mean time between failures ও mean time to repair।
   - Customer-reported defect: মুক্তির পর গ্রাহকের পাওয়া ত্রুটির সংখ্যা।

   উৎপাদনশীলতার নির্দেশক
   - Productivity: প্রতি ব্যক্তি-মাসে উৎপাদিত function point বা lines of code।
   - Velocity: Agile দলে প্রতি sprint এ সম্পন্ন story point।
   - Cycle time ও lead time: একটি কাজ শুরু থেকে শেষ হতে কত সময় লাগে।
   - Rework percentage: মোট প্রচেষ্টার কত অংশ পুনরায় করতে হয়েছে।

   মানবসম্পদ ও সাংগঠনিক নির্দেশক
   - Staff turnover rate: দল থেকে কর্মী ছেড়ে যাওয়ার হার। উচ্চ হার প্রকল্পের বড় ঝুঁকি, কারণ এতে অর্জিত জ্ঞান হারিয়ে যায়।
   - Training hours per employee ও দক্ষতার বিস্তার।
   - Resource utilization: কর্মীর সময়ের কত অংশ উৎপাদনশীল কাজে ব্যয় হয়।
   - Employee satisfaction ও দলের মনোবল।

   গ্রাহক ও ব্যবসায়িক নির্দেশক
   - Customer satisfaction index।
   - On-time delivery rate।
   - Return on investment ও payback period।
   - Service level agreement মেনে চলার হার।

   ব্যবহারের নীতি: নির্দেশক নির্বাচন করতে হয় প্রকল্পের লক্ষ্য অনুযায়ী, এবং সেগুলো SMART হতে হবে — Specific, Measurable, Achievable, Relevant ও Time-bound। শুধু একটি নির্দেশক দেখে সিদ্ধান্ত নেওয়া বিপজ্জনক; উদাহরণস্বরূপ কেবল lines of code মাপলে দল অপ্রয়োজনীয় লম্বা কোড লিখতে উৎসাহিত হয়। তাই একাধিক নির্দেশক একসঙ্গে বিবেচনা করতে হয়।
2. **Which you build about real life software project? What problems you faced during that time and how to solve this?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*


   Answer: A real-life software project, the problems faced, and how they were solved.

   The project: an online examination and result processing system for a public institution. It allowed the administration to create question banks, schedule examinations, let candidates sit the test in a browser, evaluate the multiple-choice part automatically, record the written marks, and publish the results. It was built with a three-tier architecture: a React front end, a Spring Boot REST API, and a PostgreSQL database, deployed on a Linux server behind Nginx. The team had six people and the schedule was five months.

   The problems, and how each was solved:

   1. Unclear and shifting requirements. The client could describe the paper-based process but not the system, and asked for changes after each demonstration.
   - Solution: switched from a documents-first approach to short iterations. A clickable prototype was shown at the end of every two-week sprint, and the client signed off each screen. A written change control procedure was introduced: any change after sign-off was logged with its cost and schedule impact, and the sponsor decided whether to accept it. Scope creep stopped being invisible.

   2. Performance collapse under load. The system worked for ten testers but timed out when 2,000 candidates logged in within the same five minutes.
   - Solution: profiling showed an N+1 query problem, where loading a question list issued one query per option. Fixed by eager fetching with a join. Added database indexes on the columns used in the WHERE clauses, introduced Redis caching for the question paper, which is read constantly and written rarely, and moved to a connection pool of the right size. Response time fell from about 11 seconds to under 1 second. The lesson was to load-test early, not at the end.

   3. Concurrency and lost answers. Two saves from the same candidate could overwrite each other, and a candidate whose network dropped lost the answers of the current page.
   - Solution: auto-save every 30 seconds to local storage on the client, and an idempotent save API keyed on candidate, question and attempt, so a repeated save is harmless. Optimistic locking with a version column prevented lost updates in the database.

   4. Integration failures with the payment gateway during application fee collection. Sometimes money was deducted but the application was not marked paid.
   - Solution: made the payment flow transactional and recoverable. Every payment attempt is written to the database before redirecting to the gateway; the callback and a scheduled reconciliation job both update it; a nightly job compares the gateway's settlement report with the local records and flags mismatches. Retries were made idempotent using the gateway's transaction ID as a unique key.

   5. Team communication and merge conflicts. Two developers repeatedly modified the same files and lost work in bad merges.
   - Solution: adopted a branching strategy of one feature branch per task with mandatory pull request review, a daily fifteen-minute stand-up, and a task board so that work was visible. Continuous integration ran the test suite on every push, so a broken merge was caught within minutes.

   6. Testing left too late. Bugs surfaced in the final two weeks in large numbers.
   - Solution: introduced unit tests for the service layer and made the build fail below a coverage threshold, wrote automated integration tests for the critical paths, and ran a pilot examination with 300 real candidates one month before the live examination. The pilot revealed the load problem and two usability problems that no internal test had found.

   7. Security. A review found that the answer key was retrievable from the browser and that the exam URL could be reached without an active session.
   - Solution: removed all evaluation logic from the client, so the browser never receives the correct answer; enforced server-side session and time-window checks on every request; added rate limiting, HTTPS, and an audit log of every answer submission with a timestamp and IP address.

   The general lessons drawn: involve the customer continuously rather than at the two ends; test performance and security from the beginning; automate the build, the tests and the deployment; keep the scope under written control; and treat a pilot run as an essential step, not an optional one.
3. **Project management related question (what are the approaches)** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 520 (ET: MIST)]*


   Answer: Approaches to software project management.

   Project management approaches fall into two broad families, the plan-driven and the adaptive, with hybrids between them.

   Plan-driven, also called predictive or traditional
   - Waterfall: phases are completed one after another, each fully documented and signed off before the next begins. Suited to projects with stable, well-understood requirements and heavy regulatory documentation needs.
   - V-Model: the same sequence, but each development phase is paired with a corresponding test level, so verification is planned from the start.
   - Incremental and iterative: the product is built and delivered in pieces, each adding function to a working system.
   - Spiral: each loop of the spiral performs objective setting, risk analysis, development and planning. Risk driven, and suited to large, expensive, high-risk projects.
   - PRINCE2 and PMBOK: formal management frameworks rather than lifecycles. PMBOK organises work into initiating, planning, executing, monitoring and controlling, and closing, across the knowledge areas of scope, schedule, cost, quality, resource, communication, risk, procurement, stakeholder and integration management.

   Adaptive, or agile
   - Scrum: fixed-length sprints of two to four weeks, a product backlog owned by the Product Owner, a sprint backlog owned by the team, and the ceremonies of sprint planning, daily stand-up, sprint review and retrospective. The Scrum Master removes impediments. Progress is measured by working software and velocity.
   - Kanban: continuous flow rather than fixed iterations, a visual board, and explicit work-in-progress limits to expose bottlenecks. Suited to maintenance and support work where items arrive unpredictably.
   - Extreme Programming (XP): engineering-focused, with pair programming, test-driven development, continuous integration, refactoring, collective code ownership, small releases and an on-site customer.
   - Lean: eliminate waste, amplify learning, decide as late as responsibly possible, deliver fast, and optimise the whole.
   - Scaled frameworks such as SAFe and LeSS coordinate many agile teams on one product.

   Hybrid: plan-driven governance and milestones at the programme level with agile delivery inside each workstream. This is what most large organisations, including government projects, actually use.

   The core management activities, whichever approach is chosen
   - Scope management: define the deliverables, build the work breakdown structure, and control changes.
   - Time management: estimate durations, sequence activities, and build the schedule with a Gantt chart and the critical path.
   - Cost management: estimate with COCOMO, function point analysis, expert judgement or analogy; then budget and control by earned value.
   - Quality management: standards, reviews, testing strategy and metrics.
   - Risk management: identify, analyse by probability and impact, plan responses of avoid, transfer, mitigate or accept, and monitor the risk register.
   - Human resource management: team structure, roles, staffing and training.
   - Communication management: who needs what information, how often and in what form.
   - Configuration management: version control, baselines and change control.

   How to choose
   - Requirements stable and well known, with heavy compliance needs: plan-driven.
   - Requirements uncertain or expected to evolve, and the customer is available: agile.
   - Large, novel and high-risk: spiral or a risk-driven incremental approach.
   - Continuous stream of small, unpredictable items: Kanban.
4. **(খ) User story ও Product backlog কী?** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*


   Answer: User story এবং Product backlog — Agile, বিশেষত Scrum পদ্ধতির দুটি মৌলিক উপাদান।

   User story: ব্যবহারকারীর দৃষ্টিকোণ থেকে লেখা একটি প্রয়োজনের সংক্ষিপ্ত, সরল বিবরণ। এটি সম্পূর্ণ requirement নয়, বরং আলোচনার একটি প্রতিশ্রুতি — কার্ড দেখে দল ও গ্রাহক কথা বলে বিস্তারিত ঠিক করে।

   প্রচলিত কাঠামো:
   - As a <ব্যবহারকারীর ভূমিকা>, I want <কী চাই>, so that <কেন চাই>।
   - উদাহরণ: As a customer, I want to reset my password by email, so that I can regain access without calling support.
   - উদাহরণ: As a librarian, I want to see the list of overdue books, so that I can send reminders.

   প্রতিটি user story এর সঙ্গে থাকে acceptance criteria — যেসব শর্ত পূরণ হলে story টি সম্পন্ন ধরা হয়। যেমন উপরের প্রথমটির জন্য: বৈধ ইমেইল দিলে পুনঃস্থাপনের লিঙ্ক পাঠানো হবে; লিঙ্কটি ৩০ মিনিট পর অকার্যকর হবে; অনিবন্ধিত ইমেইল দিলেও একই বার্তা দেখানো হবে।

   ভালো user story এর মাপকাঠি — INVEST:
   - Independent: অন্য story এর ওপর নির্ভরশীল নয়।
   - Negotiable: বিস্তারিত আলোচনার মাধ্যমে ঠিক হয়, আগে থেকে চূড়ান্ত নয়।
   - Valuable: ব্যবহারকারীর কাছে মূল্যবান।
   - Estimable: দল এর আকার অনুমান করতে পারে।
   - Small: একটি sprint এর মধ্যে শেষ করা যায়।
   - Testable: পরীক্ষা করে প্রমাণ করা যায়।

   Story এর আকার মাপা হয় story point এ, সাধারণত Fibonacci ধারায় ১, ২, ৩, ৫, ৮, ১৩। বড় story কে বলে epic, যা ভেঙে ছোট story তে রূপান্তর করতে হয়।

   Product backlog: পণ্যটির জন্য প্রয়োজনীয় সব কাজের একটি ক্রমবিন্যস্ত তালিকা — user story, feature, ত্রুটি সংশোধন, কারিগরি কাজ ও গবেষণার কাজ সব মিলিয়ে।

   বৈশিষ্ট্য:
   - এর একমাত্র মালিক Product Owner; তিনিই ক্রম নির্ধারণ করেন।
   - এটি সর্বদা পরিবর্তনশীল, কখনো চূড়ান্ত নয় — নতুন তথ্য এলে নতুন item যোগ হয়, পুরনোগুলোর ক্রম বদলায়।
   - উপরের item গুলো বিস্তারিত ও অনুমানকৃত, নিচের item গুলো অস্পষ্ট ও বড় থাকে। একে বলে DEEP — Detailed appropriately, Estimated, Emergent, Prioritized।
   - ক্রম নির্ধারণে ব্যবসায়িক মূল্য, ঝুঁকি, নির্ভরশীলতা ও খরচ বিবেচনা করা হয়। কৌশল হিসেবে MoSCoW — Must have, Should have, Could have, Won't have — ব্যবহৃত হয়।
   - Backlog refinement বা grooming নামে নিয়মিত সভায় item গুলো ভাঙা, স্পষ্ট করা ও অনুমান করা হয়।

   Product backlog ও Sprint backlog এর পার্থক্য:
   - Product backlog সমগ্র পণ্যের জন্য, মালিক Product Owner, এবং এটি কখনো শেষ হয় না।
   - Sprint backlog কেবল চলতি sprint এ নেওয়া item গুলোর তালিকা, মালিক Development Team, এবং sprint শেষে এটি নিঃশেষ হয়।

   দুইয়ের সম্পর্ক: Product backlog থেকে সর্বোচ্চ অগ্রাধিকারের user story গুলো sprint planning সভায় নির্বাচিত হয়ে sprint backlog এ যায়, সেখান থেকে কাজ হয়ে sprint শেষে সম্ভাব্য মুক্তিযোগ্য increment তৈরি হয়।
5. **Assume you are a project manager and your job is to develop an application which is similar to what you have developed is past only larger and complex. The customer has documented the requirements clearly. What team structure would you choose in this case and why?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*


   Answer: Given the situation — the work is similar to what the team has built before, only larger and more complex, and the customer has documented the requirements clearly — the right choice is a controlled decentralized team, that is a hierarchical or chief-programmer style structure with sub-teams.

   The two properties of the situation decide the answer:
   - The problem is familiar, and the requirements are clear and stable. There is therefore little need for continuous exploration, constant renegotiation or a highly democratic decision process. Certainty favours structure.
   - The project is larger and more complex than before. A single flat team cannot handle it, because communication paths grow as n(n-1)/2; a team of 20 has 190 possible channels, which is unmanageable.

   The structure proposed:

   ```mermaid
   flowchart TD
     PM[Project Manager / Chief Programmer]
     PM --> L1[Team Lead - Module A]
     PM --> L2[Team Lead - Module B]
     PM --> L3[Team Lead - Module C]
     PM --> QA[QA Lead]
     L1 --> D1[Developers]
     L2 --> D2[Developers]
     L3 --> D3[Developers]
     QA --> T1[Testers]
     PM --> LIB[Configuration / Librarian]
   ```

   - One project manager or chief programmer holds the overall design and makes the decisions that cross module boundaries.
   - The system is decomposed into modules, and each module is given to a small sub-team of three to five people with its own senior lead.
   - Within a sub-team the work is decentralized: members discuss and decide among themselves, which suits problem solving at the detailed level.
   - Between sub-teams the structure is centralized: the leads report to the project manager, so the number of communication channels stays linear rather than quadratic.
   - A separate quality assurance group tests independently of the developers.
   - A configuration manager owns version control, builds and releases.

   Why this rather than the alternatives:

   - Not democratic decentralized, that is an egoless team. It has no permanent leader and everyone participates in every decision. It is excellent for research work and for problems nobody has solved before, because it produces many ideas and high morale. But its communication cost is high and it slows down badly as the team grows. Here the problem is already understood, so the extra exploration buys nothing while the coordination cost is real.

   - Not fully controlled centralized, where the single chief programmer makes all decisions and the others only implement. It is efficient for small, simple, short projects, but it makes the chief a bottleneck and a single point of failure, it does not scale to a large complex system, and it wastes the experience of the senior members. Morale suffers and there is no succession if the chief leaves.

   - The controlled decentralized structure takes the strength of both: fast, consistent decisions at the top where the system must remain coherent, and full participation inside each sub-team where the detailed work happens.

   Supporting decisions that go with the structure:
   - Because the requirements are documented and stable, a plan-driven lifecycle such as the waterfall or the V-model, or an incremental one with fixed increments, fits well; a fully exploratory agile process is not necessary, though iterative delivery within each module is still useful.
   - Because the work resembles a previous project, estimation by analogy is reliable, and reuse of components, of the architecture and of the test suites from the earlier system should be planned explicitly.
   - Interfaces between modules must be defined and frozen early by the project manager, since the sub-teams will work in parallel against them.
   - Regular integration, ideally continuous, prevents the classic failure of parallel sub-teams: modules that each work alone but do not fit together.
6. **a) What is conflict in git? How to resolve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*


   Answer: Conflict in Git, and how to resolve it.

   A merge conflict occurs when Git cannot decide automatically which of two changes to keep. It happens when two branches modify the same lines of the same file, or when one branch modifies a file that the other deleted or renamed. Git merges changes to different parts of a file without help; it stops only when the changes overlap.

   When conflicts arise: during git merge, git rebase, git pull, which is a fetch followed by a merge, git cherry-pick and git stash pop.

   What Git does when it hits a conflict: it stops the operation, marks the affected files as unmerged, and writes conflict markers into them:

   ```
   <<<<<<< HEAD
   int timeout = 30;          // your version, the current branch
   =======
   int timeout = 60;          // their version, the incoming branch
   >>>>>>> feature-branch
   ```

   - Everything between `<<<<<<< HEAD` and `=======` is the current branch's content.
   - Everything between `=======` and `>>>>>>>` is the incoming branch's content.

   Resolution procedure:

   ```bash
   git status                    # lists the files under "Unmerged paths"
   git diff                      # shows the conflicting hunks
   # open each conflicted file, edit it to the correct final content,
   # and delete all three marker lines
   git add <file>                # marks the conflict as resolved
   git status                    # confirm nothing is left unmerged
   git commit                    # completes the merge; Git supplies a default message
   ```

   During a rebase the last step differs:

   ```bash
   git add <file>
   git rebase --continue
   ```

   Useful commands:
   - `git merge --abort` or `git rebase --abort` returns the working tree to the state before the operation began.
   - `git checkout --ours <file>` keeps the current branch's whole file; `git checkout --theirs <file>` keeps the incoming one. Note that during a rebase the meaning of ours and theirs is reversed, because the commits are being replayed onto the other branch.
   - `git mergetool` opens a three-way visual merge tool.
   - `git log --merge -p <file>` shows the commits on both sides that touched the file.

   The most important point: resolving means producing the correct code, not simply choosing one side. Often the correct result contains parts of both. After removing the markers the code must be compiled and the tests run before committing, because a syntactically valid merge can still be logically wrong.

   How to reduce conflicts:
   - Pull or rebase from the main branch frequently, so branches never diverge far.
   - Keep feature branches short-lived and small.
   - Divide work so that two people rarely edit the same file at the same time.
   - Agree on formatting and use an automatic formatter, so that whitespace and indentation changes do not create false conflicts.
   - Commit often with focused commits.
   - Communicate in the team about who is working on which module.
7. **b) Write down the difference between Patch and Upgrade.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*


   Answer: Difference between a patch and an upgrade.

   | Point | Patch | Upgrade |
   |---|---|---|
   | Purpose | Fixes a specific defect or security vulnerability in the existing version | Moves the software to a newer version with new features and improvements |
   | Size | Small; contains only the changed files or code | Large; often a full new installation package |
   | Scope of change | Narrow and targeted | Broad; may change the architecture, the interface and the data format |
   | Version number | Changes the last part, for example 2.4.1 to 2.4.2 | Changes the major or minor part, for example 2.4 to 3.0 |
   | New features | None; behaviour otherwise stays the same | Yes; that is its main purpose |
   | Frequency | Frequent, often monthly or on discovery of a vulnerability | Occasional, once in months or years |
   | Cost | Usually free within the support period | Often paid, or requires a new licence |
   | Downtime | Little or none; many patches apply while the system runs | Significant; planned outage, testing and possibly retraining |
   | Risk | Low, but a bad patch can still break a dependent feature | Higher; compatibility of data, plug-ins and integrations must be checked |
   | Reversibility | Usually easy to uninstall | Difficult; often needs a full restore from backup |
   | Example | A Windows security update, a MySQL 8.0.35 to 8.0.36 bug fix | Windows 10 to Windows 11, MySQL 5.7 to MySQL 8.0 |

   Related terms worth distinguishing:
   - Hotfix: an urgent patch issued outside the normal release schedule, usually for a critical production failure or an actively exploited vulnerability.
   - Service pack: a bundle of many patches and minor improvements released together.
   - Update: a general term, usually meaning a minor version change that may include both fixes and small features.

   Practical rule for administration: apply security patches promptly, because unpatched known vulnerabilities are the most common cause of compromise. Plan upgrades: test on a staging system first, verify that third-party integrations and custom code still work, take a full backup, schedule a maintenance window, and keep a documented rollback plan.

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

## IT Governance, Audit & Risk Management (3)

1. **Difference between: Policy, Guideline, Procedure; why auditor must focus on control as a system? Explain four types of risks auditor faces, Explain each of theme.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 310 (ET: BIBM)]*

2. **A bank has association with two different service providers as their payment gateways. The bank hires Mr. X to audit the payment gateway based on risk and threat detection. Which possible scenarios Mr. X will face?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 443 (ET: BIBM)]*

3. **(ক) Software risk কত প্রকার ও কী কী? Risk management process চিত্রের মাধ্যমে বুঝিয়ে লিখুন।** *[Software Assistant Programmer 13.10.2022 compact it 709 (ET: N/A)]*

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
