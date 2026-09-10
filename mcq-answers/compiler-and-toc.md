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

   answer: b — regular  
   explanation: Regular languages are closed under complement — swap accepting and non-accepting states of the DFA and it still recognises a regular set.

2. **Number of steps required to get 'aab' from A→ aA|a|b—** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*  
   (a) 4  
   (b) 3  
   (c) 2  
   (d) 1

   answer: b — 3  
   explanation: The derivation is A ⇒ aA ⇒ aaA ⇒ aab, which is three steps.

3. **Which of the operation is eligible in Push Down Automate?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*  
   (a) Delete  
   (b) Pushod  
   (c) Insert  
   (d) None of these

   answer: b — Pushod  
   explanation: A pushdown automaton works on a stack, so the legal operations are push and pop; the garbled option "Pushod" stands for push.

4. **Which of the following regular expressions represents the set of all the binary strings with an odd number of 1's?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 77 (ET: N/A)]*  
   a. 0*+(10*1) *10*  
   b. (0*+(10*1) *)10*n  
   c. 0*+10*1*10*  
   d. (0*+10) *1*10*

   answer: a — 0*+(10*1) *10*  
   explanation: Read as 0*(10*1)*10*: the (10*1)* part contributes 1s in pairs (even), and the final 1 makes the total odd, while the 0* parts allow zeros anywhere.

5. **Which of the following is the regular expression to represent all the binary strings with odd number of 1's?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*  
   a. 0*(10*1)*11  
   b. 0*(10*1)*10*  
   c. (0*10*1)*0*10*  
   d. (0*10*)*1(0*10*)*

   answer: b — 0*(10*1)*10*  
   explanation: Pairs of 1s from (10*1)* keep the count even, and the trailing 1 makes it odd; leading and trailing zeros are covered by the 0* terms.

6. **Which one of the following regular expressions represents the set of all binary strings with an odd number of 1's?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 185 (ET: N/A)]*  
   a) ((0+1)*1(0+1)*1)*10*  
   b) (0*10*10*)*0*1  
   c) 1*+(1*01*0)*1*  
   d) None

   answer: d — None  
   explanation: Option (a) cannot produce 0100, (b) forces the string to end in 1 so it misses 10, and (c) includes 1* which allows an even number of 1s.
