<!-- TOC START -->
**Table of Contents** — 5 subtopics · 46 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Software Testing](#software-testing-20) | 20 |
| 2 | [SDLC Models](#sdlc-models-14) | 14 |
| 3 | [Software Design & Metrics](#software-design--metrics-8) | 8 |
| 4 | [Design Patterns](#design-patterns-3) | 3 |
| 5 | [Software Requirements Engineering](#software-requirements-engineering-1) | 1 |

<!-- TOC END -->

---

## Software Testing (20)

1. **Integration testing is the process of testing the _____ between two software units or modules.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxi (ET: DU)], [Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxii (ET: DU)]*  
   (a) Performance  
   (b) Functionality  
   (c) Interface  
   (d) Security

   answer: c — Interface  
   explanation: Integration testing checks that modules exchange data correctly across their interfaces once combined.

2. **Which of the following testing strategy is related to the boundary value analysis?** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) White-box testing  
   (b) Black box testing  
   (c) White box and black box testing  
   (d) None of these

   answer: b — Black box testing  
   explanation: Boundary value analysis picks inputs at the edges of valid ranges using only the specification, without looking at the code.

3. **Objective of integration testing is to find _____** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) design error  
   (b)-functional error  
   (c) interface error  
   (d) coding error

   answer: c — interface error  
   explanation: Faults in the way modules pass data or call each other show up when the units are combined.

4. **______ is a type of software testing where a group of individuals, usually from within the organization, use the software in a simulated or controlled environment to uncover defects.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*  
   (a) Alpha Testing  
   (b) User Acceptance Testing  
   (c) Beta Testing  
   (d) Regression Testing

   answer: a — Alpha Testing  
   explanation: Alpha testing is done in-house by the organisation's own people in a controlled environment before release to customers.

5. **Which of the following testing techniques includes how well the user will understand and interact with the system?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*  
   (a) Alpha Testing  
   (b) User Acceptance Testing  
   (c) Beta Testing  
   (d) Usability Testing

   answer: d — Usability Testing  
   explanation: Usability testing measures how easily real users understand, learn and operate the interface.

6. **______ testing is a testing technique where the actual data verified in the real environment.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*  
   (a) Regression Testing  
   (b) Alpha Testing  
   (c) Beta Testing  
   (d) None of the above

   answer: c — Beta Testing  
   explanation: Beta testing puts the software in the hands of real users with real data in their own environment.

7. **Which of the below testing is related to Non-functional testing?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*  
   (a) Unit testing  
   (b) Black-box testing  
   (c) Performance testing  
   (d) None of the above

   answer: c — Performance testing  
   explanation: Performance testing measures speed, stability and resource use — qualities of how the system works, not what it does.

8. **Which of the following testing is also called Acceptance testing?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*  
   (a) Beta testing  
   (b) White-box testing  
   (c) Grey box testing tab  
   (d) Alpha testing

   answer: a — Beta testing  
   explanation: Beta testing is carried out by actual users in their own environment to decide whether the product is acceptable.

9. **Which is the correct definition of BUG?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) A difficult syntax error in a program  
   b) A logical error in a program  
   c) Documenting programs  
   d) All of the above

   answer: b — A logical error in a program  
   explanation: A bug is a defect that makes the program behave incorrectly; a syntax error is caught by the compiler instead.

10. **Which of the following is the appropriate set of test cases, (A, B) when the part of a program shown is tested by decision condition coverage (branch coverage)?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*
   ```c
   if(A OR B) X = X+1;
   else X = X-1;
   ```
   a. {(False, True)}  
   b. {(False, True), (*True, False), (True, True)}  
   c. {(False, True), (True, False)}  
   d. {(False, False), (True, True)}

   answer: d — {(False, False), (True, True)}  
   explanation: Branch coverage needs the condition to evaluate both ways: (F,F) makes A OR B false and (T,T) makes it true.

11. **________ is the final stage of the testing process conducted before software release. This is referred as:** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 180 (ET: N/A)]*  
   a) Alpha testing  
   b) Beta testing  
   c) Gamma testing  
   d) Delta testing

   answer: b — Beta testing  
   explanation: Beta is the last stage before release, run by real users outside the development organisation.

12. **Software goes through a phase in which errors are verified and studied on simulated user environments. This is referred as-** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*  
   a) Alpha testing  
   b) Beta testing  
   C) Gamma testing  
   d) Delta testing

   answer: a — Alpha testing  
   explanation: Alpha testing takes place in a simulated environment at the developer's site before the software reaches real users.

13. **Modified software goes through a phase where it is tested in the user’s site or live environment. This is referred as-** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 149 (ET: DU)]*  
   a) Alpha testing  
   b) Beta testing  
   c) Gamma testing  
   d) Delta testing

   answer: b — Beta testing  
   explanation: Beta testing runs at the customer's site in the live environment.

14. **________ is an integration testing that is commonly used when software products are being developed. It is designed as a pacing mechanism for time-critical project, allowing the software team to assess its project on a frequent basis.** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 151 (ET: DU)]*  
   a) Unit testing  
   b) Function testing  
   c) Regression testing  
   d) Smoke testing

   answer: d — Smoke testing  
   explanation: Smoke testing integrates and exercises the build frequently to confirm the core functions still work, acting as a project pacing mechanism.

15. **কোন Testing দিয়ে Input-Output ঠিক আছে কিনা বুঝা যায়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*  
   A) Black-box Testing  
   B) Integration Testing  
   C) White-box testing  
   D) Load Testing

   answer: A — Black-box Testing  
   explanation: Black-box testing feeds inputs and checks outputs against the specification without looking inside the code.

16. **Testing of software with actual data and in actual environment is known as-** *[Probashi Kallyan Bank Programmer: 2019 compact it 210 (ET: AUST)]*  
   A) Regression testing  
   B) Beta testing  
   C) Alpha testing  
   D) None of these

   answer: B — Beta testing  
   explanation: Beta testing uses real data in the real operating environment at the user's site.

17. **A Non-Functional Software testing is done to check if the user interface is easy to use and understand-** *[Probashi Kallyan Bank Programmer: 2019 compact it 212 (ET: AUST)]*  
   A) Security Testing  
   B) Unit testing  
   C) Block Box Testing  
   D) Usability Testing

   answer: D — Usability Testing  
   explanation: Usability testing evaluates how easy the interface is to learn and use.

18. **The name of the testing which is done to make sure the existing features are not affected by new changes** *[Probashi Kallyan Bank Programmer: 2019 compact it 213 (ET: AUST)]*  
   A) Recursive testing  
   B) Regression testing  
   C) Whitebox testing  
   D) Unit testing

   answer: B — Regression testing  
   explanation: Regression testing re-runs existing tests after a change to confirm nothing that used to work has broken.

19. **Which kind of software testing strategy starts with testing the fundamental components first?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*  
   A) Top-down testing  
   B) Bottom-up testing  
   C) Stress Testing  
   D) Back to Back testing

   answer: B — Bottom-up testing  
   explanation: Bottom-up starts with the lowest-level modules and works upward, using drivers to call them.

20. **Test case is written by-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*  
   A) Tester  
   B) Developer  
   C) Test Engineer  
   D) Designer

   answer: A — Tester  
   explanation: The tester (test engineer) designs and writes the test cases from the requirements; option C names the same role.

## SDLC Models (14)

1. **What is the major drawback of waterfall Model?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxi (ET: DU)]*  
   (a) It is difficult to manage  
   (b) It requires too many resources  
   (c) It is inflexible and not suitable for changing requirements  
   (d) It lacks proper documentation

   answer: c — It is inflexible and not suitable for changing requirements  
   explanation: Waterfall freezes each phase before the next begins, so a late requirement change means going back through everything.

2. **How many steps in waterfall model?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 22 (ET: BIBM)]*  
   (a) 5  
   (b) 6  
   (c) 7  
   (d) 8

   answer: b — 6  
   explanation: The usual phases are requirement analysis, system design, implementation, integration and testing, deployment and maintenance.

3. **Which of the following is an appropriate category of system maintenance performed for the purpose of modifying the system to cope with changes in the software environment?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 113 (ET: N/A)]*  
   a) Preventive maintenance  
   b) Corrective maintenance  
   c) Adaptive maintenance  
   d) Perfective maintenance

   answer: c — Adaptive maintenance  
   explanation: Adaptive maintenance changes the software so it keeps working when the operating system, hardware or environment changes.

4. **Programmers being roughly out the logic they will use in the ________ stage of software SDLC.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*  
   A) Design  
   B) Development  
   C) Implementation  
   D) Testing

   answer: A — Design  
   explanation: The logic and structure of the program are worked out in the design phase, before any code is written.

5. **The process of making object code form one system work on another type of system is called ________.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 162 (ET: N/A)]*  
   A) Porting  
   B) Designing  
   C) Developing  
   D) Coding

   answer: A — Porting  
   explanation: Porting adapts software so it runs on a different platform or architecture.

6. **________ is natural language statements that look like programming code.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 163 (ET: N/A)]*  
   A) Source code  
   B) Object code  
   C) Pseudo code  
   D) IPO chart

   answer: C — Pseudo code  
   explanation: Pseudocode expresses the algorithm in plain language shaped like code, without any particular language's syntax.

7. **A branch office, location or other data processing centers, where a newly developed system is used under normal operating conditions for several months, to test it, is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Beta test data  
   b) String test data  
   c) Alpha test data  
   d) System test data

   answer: a — Beta test data  
   explanation: Running the new system at a real branch under normal conditions for months is beta testing with live data.

8. **Which of the following requires the most time in SDLC?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)], [Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*  
   A) Requirement Analysis  
   B) Testing  
   C) Deployment  
   D) Design

   answer: B — Testing  
   explanation: Testing runs across unit, integration, system and acceptance levels with repeated defect fixing, so it consumes the largest share of effort.

9. **Program background, program functions and computing requirements are part of-** *[Probashi Kallyan Bank Programmer: 2019 compact it 212 (ET: AUST)]*  
   A) decision box  
   B) statement box  
   C) operations detail  
   D) none of these

   answer: C — operations detail  
   explanation: Background, functions and computing requirements together describe how the program operates.

10. **Waterfall model phase in which system design is prepared and this system design helps is specifying system requirements and define overall system architecture is-** *[Probashi Kallyan Bank Programmer: 2019 compact it 214 (ET: AUST)]*  
   A) planning  
   B) modeling  
   C) construction  
   D) communication

   answer: B — modeling  
   explanation: The modeling phase produces the system design and architecture from the gathered requirements.

11. **Which of the following is not a Software Development Life Cycle Phase?** *[Probashi Kallyan Bank Programmer: 2019 compact it 214 (ET: AUST)]*  
   A) Test Closure  
   B) Coding  
   C) Testing  
   D) None of these

   answer: A — Test Closure  
   explanation: Test closure belongs to the testing life cycle (STLC), not to the SDLC phases of requirements, design, coding, testing and maintenance.

12. **Method used in writing and design of a program is termed as-** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*  
   A) Bottom-up method  
   B) top-down method  
   C) split method  
   D) None of these

   answer: B — top-down method  
   explanation: Top-down design starts from the overall problem and refines it stepwise into smaller modules.

13. **Which of the following is a project scheduling method that can be applied to software development?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*  
   A) PERT  
   B) CPM  
   C) Both A & B  
   D) CMM

   answer: C — Both A & B  
   explanation: PERT and CPM are both network scheduling techniques used to plan and track software projects.

14. **In which model prototype can be developed?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*  
   A) Unified Process  
   B) Waterfall Model  
   C) Evolutionary-model  
   D) All of the above

   answer: C — Evolutionary-model  
   explanation: The evolutionary (prototyping) model builds a working prototype early and refines it with user feedback; waterfall has no prototype stage.

## Software Design & Metrics (8)

1. **In a class definition with 10 methods, to make the class maximally cohesive number ofconnections required among the methods are-** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) 90  
   (b) 100  
   (c) 10  
   (d) 45

   answer: d — 45  
   explanation: Maximum cohesion means every method is connected to every other, giving n(n-1)/2 = 10×9/2 = 45 connections.

2. **Cyclomatic complexity is a software metric used in _____** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) White box testing  
   (b) Black box testing  
   (c) Grey box testing  
   (d) None of these

   answer: a — White box testing  
   explanation: Cyclomatic complexity counts the independent paths through the code, so it needs the internal structure — white box.

3. **The degree of interaction between two modules is known as-** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) Cohesion  
   b) Strength  
   c) Inheritance  
   d) Coupling

   answer: d — Coupling  
   explanation: Coupling measures how much two modules depend on each other; cohesion measures how focused one module is internally.

4. **In software development, value adjustment factors include the following among others:** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*  
   (a) the criticality of the performance and reusability of the code  
   (b) number of lines of code in the software.  
   (c) number of technical manpower and hardware costs  
   (d) time period available and the level of user friendliness

   answer: a — the criticality of the performance and reusability of the code  
   explanation: Function point analysis adjusts the raw count using 14 general system characteristics such as performance, reusability and complexity.

5. **Assuming the existence of a start and end nodes for a program graph (PG), the total number of Paths is equivalent to _______ set of test data required to test software.** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*  
   (a) Minimum  
   (b) Maximum  
   (c) Optimum  
   (d) Supreme

   answer: b — Maximum  
   explanation: Testing every path through the program graph is the most exhaustive possible test set, so it gives the maximum number of test cases.

6. **________ is qualitative measure that refers to the number of connections between a ‘calling’ and a ‘called’ module and the complexity of these connections.** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 149 (ET: DU)]*  
   a) Coupling  
   b) Cohesion  
   c) Both A and B  
   d) None of them

   answer: a — Coupling  
   explanation: Coupling describes how many connections exist between a calling and a called module and how complex those connections are.

7. **ISO 9126 quality factors consist of –** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 152 (ET: DU)]*  
   a) process-ability, consistency, usefulness, adaptability, rationality and transportability  
   b) functionality, reliability, effectiveness, usability, maintainability and portability  
   c) functionality, consistency, effectiveness, adaptability, maintainability and transportability  
   d) None of them.

   answer: b — functionality, reliability, effectiveness, usability, maintainability and portability  
   explanation: ISO 9126 lists six characteristics: functionality, reliability, usability, efficiency (effectiveness), maintainability and portability.

8. **DFD stands for-** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*  
   A) data file disk  
   B) data flow diagram  
   C) disk flat database  
   D) disk file database

   answer: B — data flow diagram  
   explanation: A DFD shows how data moves between processes, stores and external entities.

## Design Patterns (3)

1. **Design pattern for hierarchical structure is ______** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*  
   (a) Structure chart  
   (b) DFD  
   (c) ERD  
   (d) UML

   answer: a — Structure chart  
   explanation: A structure chart shows the program broken into modules arranged as a hierarchy of callers and called modules.

2. **Which of the following is a design pattern?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*  
   A) Factory  
   B) List  
   C) Queue  
   D) All of these

   answer: A — Factory  
   explanation: Factory is a creational design pattern; list and queue are data structures, not patterns.

3. **Which of the following is a design pattern?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*  
   A) List  
   B) Queue  
   C) Factory  
   D) All of above

   answer: C — Factory  
   explanation: The Factory pattern creates objects without naming the exact class, which is a design pattern rather than a data structure.

## Software Requirements Engineering (1)

1. **If every requirement can be checked by a cost-effective process, then software requirement specification (SRS) is called-** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) Complete  
   (b) Traceable  
   (c) Verifiable  
   (d) Modifiable
