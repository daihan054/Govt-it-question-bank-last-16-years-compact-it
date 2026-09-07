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
answer: C
explanation: Integration testing focuses on verifying the communication, data transfer, and interfaces between integrated software modules or units.

2. **Which of the following testing strategy is related to the boundary value analysis?** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) White-box testing
   (b) Black box testing
   (c) White box and black box testing
   (d) None of these
answer: B
explanation: Boundary Value Analysis (BVA) is a classic black-box testing technique that tests input values at the boundaries of equivalence classes (minimum, just above minimum, nominal, just below maximum, and maximum).

3. **Objective of integration testing is to find _____** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) design error
   (b)-functional error
   (c) interface error
   (d) coding error
answer: C
explanation: The main objective of integration testing is to detect interface errors, data format mismatches, and communication flaws between collaborating modules.

4. **______ is a type of software testing where a group of individuals, usually from within the organization, use the software in a simulated or controlled environment to uncover defects.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*
   (a) Alpha Testing
   (b) User Acceptance Testing
   (c) Beta Testing
   (d) Regression Testing
answer: A
explanation: Alpha testing is performed in-house by internal team members in a controlled/simulated lab environment before making the build available to external users.

5. **Which of the following testing techniques includes how well the user will understand and interact with the system?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*
   (a) Alpha Testing
   (b) User Acceptance Testing
   (c) Beta Testing
   (d) Usability Testing
answer: D
explanation: Usability testing evaluates how user-friendly, intuitive, and learnable the software interface is for target end users.

6. **______ testing is a testing technique where the actual data verified in the real environment.** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*
   (a) Regression Testing
   (b) Alpha Testing
   (c) Beta Testing
   (d) None of the above
answer: C
explanation: Beta testing is performed by actual users in a real-world live environment using genuine operational data.

7. **Which of the below testing is related to Non-functional testing?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*
   (a) Unit testing
   (b) Black-box testing
   (c) Performance testing
   (d) None of the above
answer: C
explanation: Performance testing evaluates non-functional aspects such as response time, speed, scalability, and resource utilization under workload.

8. **Which of the following testing is also called Acceptance testing?** *[Pubali Bank Limited Software Quality Assurance 18.03.2023 compact it 42 (ET: N/A)]*
   (a) Beta testing
   (b) White-box testing
   (c) Grey box testing tab
   (d) Alpha testing
answer: A
explanation: Beta testing is often considered the final phase of user acceptance testing (UAT / Field Acceptance Testing), where end users validate acceptance criteria in operational conditions.

9. **Which is the correct definition of BUG?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) A difficult syntax error in a program
   b) A logical error in a program
   c) Documenting programs
   d) All of the above
answer: B
explanation: A software bug refers to a logical flaw or defect in code that causes an application to produce unexpected, incorrect, or unintended results.

10. **Which of the following is the appropriate set of test cases, (A, B) when the part of a program shown is tested by decision condition coverage (branch coverage)?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*
   ```c
   if(A OR B) X = X+1;
   else X = X-1;
   ```
   a. {(False, True)}
   b. {(False, True), (*True, False), (True, True)}
   c. {(False, True), (True, False)}
   d. {(False, False), (True, True)}
answer: D
explanation: Branch/decision coverage requires that the complete boolean condition evaluate to True at least once and False at least once. (False, False) makes (A OR B) False (executing the else branch), and (True, True) makes it True (executing the then branch).

11. **________ is the final stage of the testing process conducted before software release. This is referred as:** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 180 (ET: N/A)]*
   a) Alpha testing
   b) Beta testing
   c) Gamma testing
   d) Delta testing
answer: B
explanation: Beta testing is the final pre-release testing phase conducted in the user's live operational environment before broad commercial launch.

12. **Software goes through a phase in which errors are verified and studied on simulated user environments. This is referred as-** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*
   a) Alpha testing
   b) Beta testing
   C) Gamma testing
   d) Delta testing
answer: A
explanation: Testing performed within a simulated or lab environment at the developer's organization is referred to as Alpha testing.

13. **Modified software goes through a phase where it is tested in the user’s site or live environment. This is referred as-** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 149 (ET: DU)]*
   a) Alpha testing
   b) Beta testing
   c) Gamma testing
   d) Delta testing
answer: B
explanation: Testing done at the client/user site in a live operational environment is called Beta testing.

14. **________ is an integration testing that is commonly used when software products are being developed. It is designed as a pacing mechanism for time-critical project, allowing the software team to assess its project on a frequent basis.** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 151 (ET: DU)]*
   a) Unit testing
   b) Function testing
   c) Regression testing
   d) Smoke testing
answer: D
explanation: According to Roger Pressman, Smoke testing is an integration testing approach used as a pacing mechanism for time-critical software projects to assess daily/regular build stability.

15. **কোন Testing দিয়ে Input-Output ঠিক আছে কিনা বুঝা যায়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*
   A) Black-box Testing
   B) Integration Testing
   C) White-box testing
   D) Load Testing
answer: A
explanation: ব্ল্যাক-বক্স টেস্টিংয়ে (Black-box Testing) অভ্যন্তরীণ কোডের কাঠামো না দেখে শুধুমাত্র প্রদত্ত ইনপুটের বিপরীতে প্রত্যাশিত আউটপুট সঠিকভাবে আসছে কিনা তা যাচাই করা হয়।

16. **Testing of software with actual data and in actual environment is known as-** *[Probashi Kallyan Bank Programmer: 2019 compact it 210 (ET: AUST)]*
   A) Regression testing
   B) Beta testing
   C) Alpha testing
   D) None of these
answer: B
explanation: প্রকৃত পরিবেশে বাস্তব ডেটা ও ব্যবহারকারীদের দ্বারা সম্পাদিত টেস্টিং হলো বিটা টেস্টিং (Beta testing)।

17. **A Non-Functional Software testing is done to check if the user interface is easy to use and understand-** *[Probashi Kallyan Bank Programmer: 2019 compact it 212 (ET: AUST)]*
   A) Security Testing
   B) Unit testing
   C) Block Box Testing
   D) Usability Testing
answer: D
explanation: সফটওয়্যারের ইন্টারফেস ব্যবহারকারীর জন্য কতটা সহজ ও বোধগম্য তা যাচাই করার নন-ফাংশনাল টেস্টিং হলো ইউজেবিলিটি টেস্টিং (Usability Testing)।

18. **The name of the testing which is done to make sure the existing features are not affected by new changes** *[Probashi Kallyan Bank Programmer: 2019 compact it 213 (ET: AUST)]*
   A) Recursive testing
   B) Regression testing
   C) Whitebox testing
   D) Unit testing
answer: B
explanation: নতুন কোনো কোড সংযোজন বা সংশোধনের কারণে বিদ্যমান কোনো কার্যকারিতা ক্ষতিগ্রস্ত হয়েছে কিনা তা যাচাই করতে রিগ্রেশন টেস্টিং (Regression testing) করা হয়।

19. **Which kind of software testing strategy starts with testing the fundamental components first?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*
   A) Top-down testing
   B) Bottom-up testing
   C) Stress Testing
   D) Back to Back testing
answer: B
explanation: বটম-আপ টেস্টিংয়ে (Bottom-up testing) আর্কিটেকচারের সবচেয়ে নিচের স্তরের মৌলিক বা ফান্ডামেন্টাল মডিউলগুলো আগে টেস্ট করে পর্যায়ক্রমে ওপরের মডিউলে যাওয়া হয়।

20. **Test case is written by-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*
   A) Tester
   B) Developer
   C) Test Engineer
   D) Designer
answer: C
explanation: সফটওয়্যার টেস্টিং লাইফসাইকেলে ফর্মাল টেস্ট সিনারিও এবং বিশদ টেস্ট কেস রচনার দায়িত্ব থাকে টেস্ট ইঞ্জিনিয়ার (Test Engineer / QA Engineer)-এর ওপর।

## SDLC Models (14)

1. **What is the major drawback of waterfall Model?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxi (ET: DU)]*
   (a) It is difficult to manage
   (b) It requires too many resources
   (c) It is inflexible and not suitable for changing requirements
   (d) It lacks proper documentation
answer: C
explanation: The strictly linear and sequential structure of the Waterfall model makes it rigid and inflexible; accommodating requirement changes late in the lifecycle is difficult and expensive.

2. **How many steps in waterfall model?** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 22 (ET: BIBM)]*
   (a) 5
   (b) 6
   (c) 7
   (d) 8
answer: B
explanation: The standard classic Waterfall model comprises 6 sequential phases: 1. Requirements Analysis, 2. System Design, 3. Implementation (Coding), 4. Integration & Testing, 5. Deployment, and 6. Maintenance.

3. **Which of the following is an appropriate category of system maintenance performed for the purpose of modifying the system to cope with changes in the software environment?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 113 (ET: N/A)]*
   a) Preventive maintenance
   b) Corrective maintenance
   c) Adaptive maintenance
   d) Perfective maintenance
answer: C
explanation: Adaptive maintenance involves modifying an existing software application to make it compatible with changes in its operational environment (such as an updated OS, new hardware, database upgrade, or regulatory changes).

4. **Programmers being roughly out the logic they will use in the ________ stage of software SDLC.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) Design
   B) Development
   C) Implementation
   D) Testing
answer: A
explanation: During the software Design phase, developers and architects plan algorithms, data structures, and the structural logic (flowcharts, pseudocode) before actual coding begins.

5. **The process of making object code form one system work on another type of system is called ________.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 162 (ET: N/A)]*
   A) Porting
   B) Designing
   C) Developing
   D) Coding
answer: A
explanation: Porting is the engineering process of adapting software so that it can run on a different operating system, platform, or hardware architecture from the one it was originally built for.

6. **________ is natural language statements that look like programming code.** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 163 (ET: N/A)]*
   A) Source code
   B) Object code
   C) Pseudo code
   D) IPO chart
answer: C
explanation: Pseudocode is an informal, human-readable description of an algorithm written in natural language syntax that mimics structured programming code without strict language rules.

7. **A branch office, location or other data processing centers, where a newly developed system is used under normal operating conditions for several months, to test it, is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
   a) Beta test data
   b) String test data
   c) Alpha test data
   d) System test data
answer: A
explanation: Testing conducted at actual operational field locations or branch offices with end users under normal working conditions is known as Beta testing (or operating on beta test sites/data).

8. **Which of the following requires the most time in SDLC?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)], [Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*
   A) Requirement Analysis
   B) Testing
   C) Deployment
   D) Design
answer: B
explanation: Among the core development phases listed, Testing typically consumes the highest amount of time and resources (often 40% to 50% of the project effort) to ensure defects are identified and resolved.

9. **Program background, program functions and computing requirements are part of-** *[Probashi Kallyan Bank Programmer: 2019 compact it 212 (ET: AUST)]*
   A) decision box
   B) statement box
   C) operations detail
   D) none of these
answer: C
explanation: In formal system documentation, descriptive sections like program background, functional capabilities, and minimum computing/hardware requirements are documented in the Operations Detail (or Operational Specifications).

10. **Waterfall model phase in which system design is prepared and this system design helps is specifying system requirements and define overall system architecture is-** *[Probashi Kallyan Bank Programmer: 2019 compact it 214 (ET: AUST)]*
   A) planning
   B) modeling
   C) construction
   D) communication
answer: B
explanation: In Pressman's SDLC framework, the Modeling phase encompasses both requirements analysis and architectural/system design to define the overarching system structure.

11. **Which of the following is not a Software Development Life Cycle Phase?** *[Probashi Kallyan Bank Programmer: 2019 compact it 214 (ET: AUST)]*
   A) Test Closure
   B) Coding
   C) Testing
   D) None of these
answer: A
explanation: Test Closure is the final activity of the Software Testing Life Cycle (STLC), rather than an overarching Software Development Life Cycle (SDLC) phase.

12. **Method used in writing and design of a program is termed as-** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) Bottom-up method
   B) top-down method
   C) split method
   D) None of these
answer: B
explanation: Top-down design (stepwise refinement) is the standard structured programming methodology where a complex problem is progressively broken down into manageable sub-components.

13. **Which of the following is a project scheduling method that can be applied to software development?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*
   A) PERT
   B) CPM
   C) Both A & B
   D) CMM
answer: C
explanation: Both PERT (Program Evaluation and Review Technique) and CPM (Critical Path Method) are established network-based project management and scheduling techniques used in software project planning.

14. **In which model prototype can be developed?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
   A) Unified Process
   B) Waterfall Model
   C) Evolutionary-model
   D) All of the above
answer: C
explanation: The Evolutionary model (such as the Prototyping model or Spiral model) is built specifically around iteratively creating working prototypes to clarify requirements and adapt to feedback.

## Software Design & Metrics (8)

1. **In a class definition with 10 methods, to make the class maximally cohesive number ofconnections required among the methods are-** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) 90
   (b) 100
   (c) 10
   (d) 45
answer: D
explanation: In a maximally cohesive class, every method interacts with or shares attributes with every other method, forming a complete graph K_n. For n = 10 methods, the total number of connections is C(10, 2) = (10 * 9) / 2 = 45.

2. **Cyclomatic complexity is a software metric used in _____** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) White box testing
   (b) Black box testing
   (c) Grey box testing
   (d) None of these
answer: A
explanation: Cyclomatic complexity (developed by Thomas McCabe) measures the number of linearly independent paths in code and is a fundamental structural metric used in White-box (basis path) testing.

3. **The degree of interaction between two modules is known as-** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) Cohesion
   b) Strength
   c) Inheritance
   d) Coupling
answer: D
explanation: Coupling measures the degree of interdependence and interaction between two separate software modules (while cohesion measures the functional relatedness within a single module).

4. **In software development, value adjustment factors include the following among others:** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*
   (a) the criticality of the performance and reusability of the code
   (b) number of lines of code in the software.
   (c) number of technical manpower and hardware costs
   (d) time period available and the level of user friendliness
answer: A
explanation: In Function Point Analysis (FPA), the 14 General System Characteristics (GSCs) used to compute the Value Adjustment Factor (VAF) explicitly include system performance and code reusability.

5. **Assuming the existence of a start and end nodes for a program graph (PG), the total number of Paths is equivalent to _______ set of test data required to test software.** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   (a) Minimum
   (b) Maximum
   (c) Optimum
   (d) Supreme
answer: B
explanation: Covering all possible execution paths from start node to end node in a program graph represents exhaustive path testing, which requires the maximum set of test cases.

6. **________ is qualitative measure that refers to the number of connections between a ‘calling’ and a ‘called’ module and the complexity of these connections.** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 149 (ET: DU)]*
   a) Coupling
   b) Cohesion
   c) Both A and B
   d) None of them
answer: A
explanation: Coupling is a qualitative and structural measure of the number of interconnections and complexity of interaction between calling and called modules.

7. **ISO 9126 quality factors consist of –** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 152 (ET: DU)]*
   a) process-ability, consistency, usefulness, adaptability, rationality and transportability
   b) functionality, reliability, effectiveness, usability, maintainability and portability
   c) functionality, consistency, effectiveness, adaptability, maintainability and transportability
   d) None of them.
answer: B
explanation: Under the ISO/IEC 9126 standard, software quality is classified into 6 primary characteristics: Functionality, Reliability, Usability, Efficiency (printed here as effectiveness), Maintainability, and Portability.

8. **DFD stands for-** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*
   A) data file disk
   B) data flow diagram
   C) disk flat database
   D) disk file database
answer: B
explanation: DFD-এর পূর্ণরূপ হলো Data Flow Diagram, যা কোনো ইনফরমেশন সিস্টেমের ইনপুট, প্রসেসিং, ডেটা স্টোর এবং আউটপুটের প্রবাহ চিত্রে উপস্থাপন করে।

## Design Patterns (3)

1. **Design pattern for hierarchical structure is ______** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   (a) Structure chart
   (b) DFD
   (c) ERD
   (d) UML

2. **Which of the following is a design pattern?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) Factory
   B) List
   C) Queue
   D) All of these

3. **Which of the following is a design pattern?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*
   A) List
   B) Queue
   C) Factory
   D) All of above

## Software Requirements Engineering (1)

1. **If every requirement can be checked by a cost-effective process, then software requirement specification (SRS) is called-** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) Complete
   (b) Traceable
   (c) Verifiable
   (d) Modifiable
