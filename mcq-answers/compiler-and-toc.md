<!-- TOC START -->
**Table of Contents** — 1 subtopics · 6 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Automata & Formal Languages](#automata--formal-languages-6) | 6 |

<!-- TOC END -->

---

## Automata & Formal Languages (6)

1. **Complement of a regular set is-** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) CFG
   (b) regular
   (c) CSG
   (d) None of these
answer: B
explanation: Regular languages are closed under complementation. If language L is accepted by a deterministic finite automaton (DFA), its complement L' is accepted by the DFA with accept and non-accept states swapped, making L' regular as well.

2. **Number of steps required to get 'aab' from A→ aA|a|b—** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) 4
   (b) 3
   (c) 2
   (d) 1
answer: B
explanation: The derivation requires 3 steps: (1) A -> aA, (2) aA -> aaA, (3) aaA -> aab.

3. **Which of the operation is eligible in Push Down Automate?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   (a) Delete
   (b) Push
   (c) Insert
   (d) None of these
answer: B
explanation: A Pushdown Automaton (PDA) utilizes an auxiliary stack storage mechanism that operates using standard stack operations: Push (adding a symbol to the stack) and Pop (removing the top symbol).

4. **Which of the following regular expressions represents the set of all the binary strings with an odd number of 1's?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 77 (ET: N/A)]*
   a. 0*+(10*1) *10*
   b. (0*+(10*1) *)10*n
   c. 0*+10*1*10*
   d. (0*+10) *1*10*
answer: A
explanation: To produce an odd number of 1's, strings consist of even pairs of 1's (10*1)* accompanied by exactly one additional 1 and arbitrary 0's.

5. **Which of the following is the regular expression to represent all the binary strings with odd number of 1's?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*
   a. 0*(10*1)*11
   b. 0*(10*1)*10*
   c. (0*10*1)*0*10*
   d. (0*10*)*1(0*10*)*
answer: B
explanation: The expression 0*(10*1)*10* enforces an even count of 1's from (10*1)* followed by a single mandatory 1, guaranteeing an odd total number of 1's with optional zeros interspersed.

6. **Which one of the following regular expressions represents the set of all binary strings with an odd number of 1's?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 185 (ET: N/A)]*
   a) ((0+1)*1(0+1)*1)*10*
   b) (0*10*10*)*0*1
   c) 1*+(1*01*0)*1*
   d) None
answer: D
explanation: None of the listed options accurately and uniquely defines the set of all binary strings with an odd number of 1's (option 'a' allows uncontrolled 1's within (0+1)*, while 'b' fails to accept strings ending in zeros after the final odd 1).
