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
   explanation: (a) is the intended key. Note that the string as typeset, 0*(10*1)*10*, is NOT the odd-parity language: (10*1)* allows no zeros BETWEEN consecutive pairs, so it rejects 1101, 10101, 11001 and 11010. It is a typographic rendering of (0+10*1)*10*, which is correct. Correct forms: (0+10*1)*10* = 0*(10*10*)*10* = (0*10*1)*0*10* = 0*1(0*10*1)*0*.

5. **Which of the following is the regular expression to represent all the binary strings with odd number of 1's?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*  
   a. 0*(10*1)*11  
   b. 0*(10*1)*10*  
   c. (0*10*1)*0*10*  
   d. (0*10*)*1(0*10*)*

   answer: c — (0*10*1)*0*10*  
   explanation: (c) is the only printed option that is exactly the odd-parity language: each (0*10*1) block supplies TWO 1s with zeros free to sit anywhere around them, and the final 0*10* supplies the ONE extra 1, giving 2k+1 ones. Some keys print (b) 0*(10*1)*10*, but that expression allows no zeros between consecutive 1-pairs and therefore REJECTS 1101, 10101, 11001 and 11010 — verified by exhaustive check over every binary string up to length 14. <!-- corrected: key was b -->

6. **Which one of the following regular expressions represents the set of all binary strings with an odd number of 1's?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 185 (ET: N/A)]*  
   a) ((0+1)*1(0+1)*1)*10*  
   b) (0*10*10*)*0*1  
   c) 1*+(1*01*0)*1*  
   d) None

   answer: d — None  
   explanation: Option (a) cannot produce 0100, (b) forces the string to end in 1 so it misses 10, and (c) includes 1* which allows an even number of 1s.
