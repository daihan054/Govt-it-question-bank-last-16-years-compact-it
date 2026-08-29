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

2. **ফরম্যাটিভ মূল্যায়ন (Formative Evaluation) বলতে কী বুঝায়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

3. **Explain Verification and Validation in Software Engineering. Discuss black-box testing and white-box testing with examples.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1426 (ET: E-Zone)]*

4. **Difference between Alpha tests, Beta test, gamma test in software development.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

5. **What do you understand about software quality assurance (SQA)? While purchasing a software system for your company, as a SQA team leader what aspects will you look into for a quality software.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 330 (ET: BIBM)]*

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

7. **Given scenario of software engineering (Unit test, Regression Test, Smoke Test, Integration testing, Load Testing). Write the name of the testing and whether it is functional? Non-functional or both.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

8. **(ক) Software Quality Assurance বলতে কী বোঝায়? উহার Attribute গুলো আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

9. **6.5 Explain the difference between Unit Testing and Integration Testing.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

10. **What is Software testing? Difference between Black box testing and White box testing.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

11. **Define test plan and Test case.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 567 (ET: N/A)]*

12. **(d) What is the main difference between black box and white box testing?** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)], [Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)], [Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

13. **Verification and validation are two process areas at CMMI level 3. For both of these areas (a) provide a definition (b) a description of how you can fulfill these areas in your software testing activities.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 444 (ET: BIBM)]*

14. **অথবা, (ক) Software testing কী? উহার গুরুত্ব আলোচনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 603 (ET: N/A)]*

15. **অথবা, (ক) Black-box এবং White-box testing এর মধ্যে পার্থক্যগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

16. **What is software testing? Discuss effective and exhaustive testing.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

17. **How alpha testing is performed in software development?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

18. **(b) Explain block box testing and white box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 692 (ET: N/A)]*

19. **(a) Explain software validation, Verification and Modularity.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*

20. **(b) Explain the diference between black-box and White-box testing.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 696 (ET: N/A)]*

21. **Software testing কত প্রকার ও কী কী? Testing এর ক্ষেত্রে Boundary Value Analysis (BVA) এবং Equivalence Partitioning কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

22. **(খ) Quality Control কাকে বলে? Quality review process কীভাবে কাজ করে?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

23. **What is black box testing? Consider a program which computes the square root of an input integer between 0 and 5000. Determine the equivalence class test cases. Determine the test cases using boundary value analysis also.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

24. **Definition of Gray-box testing and Unit testing.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*

25. **Integration testing of pharmaceutical automation software?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

26. **(ক) Software এর \alpha-version ও \beta-version কি?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

27. **(গ) Unit testing, Integration testing এবং Beta testing বলতে কি বুঝায়?** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

28. **(i) Black Box testing and White Box testing এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*

29. **(a) Distinguish between black box and white box testing. Give examples of both type of testing** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

30. **Software development এ Black Box Testing বলতে কি বুঝায়?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

31. **Briefly describe Unit testing, Smoke testing and Stress testing in software engineering.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*

32. **Write different between Alpha and Beta testing.** *[BREB Assistant General Manager (IT) 2021 compact it 933-934 (ET: N/A)]*

33. **Testing is an activity that is performed to verify correct behavior of a program. Testing should be conducted in all the stages of program development. Describe different types of tests conducted in the implementation stage.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 980 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

## Software Architecture & Design Patterns (MVC) (11)

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

## UML Diagrams (Class, Use Case, Sequence) (9)

1. An e-commerce platform has Customers, Orders, and Payment methods (Credit Card, Mobile Banking). Draw a **Class Diagram** showing attributes, methods, and relationships (inheritance, association). [SO IT 25-07-2026]

2. Draw a Use Case Diagram for an Online Banking System with two actors: Customer and Bank Admin. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. **Draw a class diagram for an E-commerce website where customer can view different products, can pay either by card or cash.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 401 (ET: BUET)]*

4. **Consider the following buy a product description. Customer browses catalog, selects items to buy and then goes to check out. Customer fills in shipping information (address, receive time). System presents full pricing information and customer fills in credit card information. System authorizes purchase, confirms sale and sends confirming email to customer. Draw a use case diagram for the above system.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*

5. **Library management class diagram:** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*

6. **Draw A class diagram. A token-ring based local area network (LAN) is a network consisting of nodes in which network packets are sent around. Every node has a unique name within the network, and refers to its next node. Different kinds of nodes exist: Workstations are originators of messages; servers and printers are network nodes that can receive messages. Packets contain an originator a destination and content, and are sent around on a network. A LAN is a circular configuration of nodes.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*

7. **(খ) একটি লাইব্রেরি ব্যবস্থাপনা সিস্টেম এর জন্যে Use Case Diagram অঙ্কন করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 621 (ET: N/A)]*

8. **How do you model the following situation with a UML class diagram the car fleet of a car rental contains multiple cars, one car belongs to exactly one car fleet.** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

9. **(ক) Typical web-based login system এর জন্য sequence diagram আঁকুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 778 (ET: N/A)]*

## Software Requirements Engineering (8)

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

## Software Project Management & Organization (7)

1. **সংগঠনিক নির্দেশকগুলো কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Which you build about real life software project? What problems you faced during that time and how to solve this?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*

3. **Project management related question (what are the approaches)** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 520 (ET: MIST)]*

4. **(খ) User story ও Product backlog কী?** *[Software Assistant Programmer 13.10.2022 compact it 707 (ET: N/A)]*

5. **Assume you are a project manager and your job is to develop an application which is similar to what you have developed is past only larger and complex. The customer has documented the requirements clearly. What team structure would you choose in this case and why?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*

6. **a) What is conflict in git? How to resolve it?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

7. **b) Write down the difference between Patch and Upgrade.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

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
