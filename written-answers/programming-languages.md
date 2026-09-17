<!-- TOC START -->
**Table of Contents** — 2 subtopics · 13 questions

- [Core Programming Languages (7)](#core-programming-languages-7)
  - [Programming Exercise (Leap Year) (1)](#programming-exercise-leap-year-1)
  - [AI Search Algorithms (1)](#ai-search-algorithms-1)
  - [Sustainable Development Goals (SDG) (2)](#sustainable-development-goals-sdg-2)
  - [RSA Algorithm & Cryptography (1)](#rsa-algorithm--cryptography-1)
  - [English Grammar Correction (1)](#english-grammar-correction-1)
  - [OS Page Replacement (LRU) (1)](#os-page-replacement-lru-1)
- [Visual Basic & .NET (6)](#visual-basic--net-6)

<!-- TOC END -->

---

## Core Programming Languages (7)

### Programming Exercise (Leap Year) (1)

1. **Write a C/JAVA program to determine if a given year is a leap year or not.** *[Dhaka Power Distribution Company (DPDC) Post: Junior Assistant Manager Exam Taker: BUET Date: 27.06.2025 [bitbox it book 81]]*

Answer:
    A year is a leap year if:
    - It is divisible by 400, OR
    - It is divisible by 4 AND NOT divisible by 100.

    C Program:
    ```c
    #include <stdio.h>

    int main(void) {
        int year;
        printf("Enter a year: ");
        scanf("%d", &year);

        if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)) {
            printf("%d is a Leap Year.\n", year);
        } else {
            printf("%d is NOT a Leap Year.\n", year);
        }
        return 0;
    }
    ```

### AI Search Algorithms (1)

1. **Write down the difference between informed and uninformed search algorithm.** *[Dhaka Power Distribution Company (DPDC) Post: Junior Assistant Manager Exam Taker: BUET Date: 27.06.2025 [bitbox it book 82]]*

Answer:

    | Feature | Uninformed (Blind) Search | Informed (Heuristic) Search |
    |---|---|---|
    | Knowledge Used | Uses only problem definition and state domain; no domain heuristics | Uses domain-specific knowledge and heuristic evaluation function $h(n)$ |
    | Search Efficiency | Lower efficiency; traverses search tree systematically | High efficiency; guides traversal toward the most promising nodes |
    | Time & Space Complexity | Generally higher time and memory consumption ($O(b^d)$) | Significantly reduced search space and lower average execution time |
    | Direction of Search | Searches blindly without knowing distance to goal | Evaluates cost and estimates remaining distance to goal state |
    | Algorithms | BFS (Breadth-First), DFS (Depth-First), Uniform Cost Search (UCS) | A* Search, Greedy Best-First Search, Hill Climbing, IDA* |

### Sustainable Development Goals (SDG) (2)

1. **Number of SDGs (Sustainable Development Goals)?** *[Bangladesh Computer Council (BCC) Post: AP/Technical Writer (TW), ANE Marks: 80; Date: 18 Oct 2025 [bitbox it book 238]]*

Answer:
    - Total number of SDGs = 17 Goals (comprising 169 specific targets).
    - Adopted by the United Nations General Assembly in September 2015 under the 2030 Agenda for Sustainable Development (2016–2030).

2. **SDG বা “Sustainable Development Goal” কী?** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 331]]*

Answer:
    এসডিজি (SDG - Sustainable Development Goals / টেকসই উন্নয়ন অভীষ্ট):
    - ২০১৫ সালের ২৫ সেপ্টেম্বর জাতিসংঘের সাধারণ অধিবেশনে গৃহীত বৈশ্বিক রূপরেখা, যা ২০১৬ থেকে ২০৩০ সাল পর্যন্ত বিশ্বব্যাপী দারিদ্র্য দূরীকরণ, জলবায়ু পরিবর্তন মোকাবেলা এবং অর্থনৈতিক সমৃদ্ধি ও বৈষম্যহীন সমাজ বিনির্মাণের লক্ষ্যে প্রণীত হয়েছে।
    - মূল বৈশিষ্ট্য: ১৭টি সুনির্দিষ্ট লক্ষ্য (Goals), ১৬৯টি সহযোগী লক্ষ্যমাত্রা (Targets) এবং ২৩২টি বৈশ্বিক সূচক অন্তর্ভুক্ত।
    - প্রধান অভীষ্টসমূহ: দারিদ্র্যমুক্তি, ক্ষুধা নিরসন, সুস্বাস্থ্য ও কল্যাণ, মানসম্মত শিক্ষা, লিঙ্গ সমতা, নিরাপদ পানি ও স্যানিটেশন, সাশ্রয়ী ও দূষণমুক্ত জ্বালানি এবং জলবায়ু কার্যক্রম।

### RSA Algorithm & Cryptography (1)

1. **Write the RSA Algorithm used for public key cryptography.** *[ICB Asset Management Company Ltd Assistant Programmer; Date: 01 January 2024 Exam taker: FBS, DU; Marks: Non:50 Tech:50 [bitbox it book 318-319]]*

Answer:
    The RSA algorithm is an asymmetric cryptographic algorithm based on the computational difficulty of factoring the product of two large prime numbers.

    Step-by-Step Procedure:
    - Step 1 (Select Primes): Choose two large distinct prime numbers $p$ and $q$.
    - Step 2 (Compute Modulus): Calculate $n = p \times q$. The value $n$ forms the modulus for both public and private keys.
    - Step 3 (Euler's Totient): Calculate $\phi(n) = (p - 1)(q - 1)$.
    - Step 4 (Public Exponent $e$): Choose an integer $e$ such that $1 < e < \phi(n)$ and $\gcd(e, \phi(n)) = 1$ (typically $e = 65537$).
    - Step 5 (Private Exponent $d$): Calculate $d$ as the modular multiplicative inverse:
      $$d \equiv e^{-1} \pmod{\phi(n)} \implies d \times e \equiv 1 \pmod{\phi(n)}$$
    - Key Pairs:
      - Public Key: $(e, n)$ (distributed openly for encryption)
      - Private Key: $(d, n)$ (kept secret for decryption)
    - Encryption: Given plaintext message $M$ ($M < n$):
      $$C = M^e \bmod n$$
    - Decryption: Given ciphertext $C$:
      $$M = C^d \bmod n$$

### English Grammar Correction (1)

1. **Change the following sentences as directed:** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 330]]*
(a) He is capable to do the work. (Correct the sentence) (b) It is high time he leave the place. (Use the right form of verb) (c) Honesty is the best policy. (Transform the sentence into comparative degree) (d) Man is never content with long life. (e) The player (wear) Jersey No-10 is Messy. (Use the right form of verb) (f) I had been there. (Complete the sentence) (g) John, Tom and his friends were going to the playground. (Correct the sentence) (h) Four years - long time to complete the course. (Fill in the gap) (i) He is not loyal to me. (Correct the sentence) (j) He has said to me, “When will you come?” (Change the narration)

Answer:
    - (a) Corrected: He is capable of doing the work.
    - (b) Right form of verb: It is high time he left the place.
    - (c) Comparative degree: Honesty is better than any other policy.
    - (d) Affirmative transformation: Man is always discontented with short life.
    - (e) Right form of verb: The player wearing Jersey No-10 is Messi.
    - (f) Completed sentence: I had been there before the storm began.
    - (g) Corrected: John, Tom and their friends were going to the playground.
    - (h) Fill in the gap: Four years is a long time to complete the course.
    - (i) Corrected: He is not loyal to me. (The sentence is already grammatically correct).
    - (j) Indirect narration: He has asked me when I would come (or would go).

### OS Page Replacement (LRU) (1)

1. **Consider the page reference of LRU Page Replacement Algorithm string in 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 3. Assume number for frame 4. Find number of page faults.** *[Jamuna Oil Company Ltd Post: Junior Officer (MIS & IT); Date: 23 May, 2024 Exam Taker: JOCL [compact it 397]]*

Answer:
    Given Reference String: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 3
    Number of Memory Frames = 4

    Step-by-Step Execution:
    - 1. Ref `7`: Frames `[7, -, -, -]` $\to$ Page Fault 1
    - 2. Ref `0`: Frames `[7, 0, -, -]` $\to$ Page Fault 2
    - 3. Ref `1`: Frames `[7, 0, 1, -]` $\to$ Page Fault 3
    - 4. Ref `2`: Frames `[7, 0, 1, 2]` $\to$ Page Fault 4
    - 5. Ref `0`: Frames `[7, 0, 1, 2]` $\to$ Hit (Recency: 7, 1, 2, 0)
    - 6. Ref `3`: Frames full. LRU page is `7`. Replace `7` with `3` $\to$ `[3, 0, 1, 2]` $\to$ Page Fault 5 (Recency: 1, 2, 0, 3)
    - 7. Ref `0`: Frames `[3, 0, 1, 2]` $\to$ Hit (Recency: 1, 2, 3, 0)
    - 8. Ref `4`: Frames full. LRU page is `1`. Replace `1` with `4` $\to$ `[3, 0, 4, 2]` $\to$ Page Fault 6 (Recency: 2, 3, 0, 4)
    - 9. Ref `2`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 3, 0, 4, 2)
    - 10. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 0, 4, 2, 3)
    - 11. Ref `0`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 4, 2, 3, 0)
    - 12. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 4, 2, 0, 3)
    - 13. Ref `2`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 4, 0, 3, 2)
    - 14. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ Hit (Recency: 4, 0, 2, 3)

    Summary:
    - Total Page Faults = 6
    - Total Hits = 8

## Visual Basic & .NET (6)

1. **What is .NET framework? Write down the different component of .NET Framework.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1056 (ET: AUST)]*, *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

Answer: What the .NET Framework is
   - The `.NET Framework` is Microsoft's platform for building and running applications on Windows: a `runtime` that executes code plus a large `class library` of ready-made functionality. Its defining feature is `language independence` — C#, VB.NET, F#, C++/CLI all compile to the same intermediate language (CIL), so a VB.NET class can be inherited by a C# class.

   The components
   ```
      1. CLR  - Common Language Runtime: execution engine - JIT
                compilation, garbage collection, exception handling,
                type safety, thread management, security.
      2. CTS  - Common Type System: makes C# int / VB.NET Integer the
                same type underneath, enabling cross-language use.
      3. CLS  - Common Language Specification: subset of CTS - the
                minimum rules every .NET language must follow.
      4. BCL  - Base Class Library: System, collections, file I/O,
                threading, networking.
      5. FCL  - Framework Class Library: BCL + ASP.NET, ADO.NET,
                WinForms/WPF, LINQ, XML, WCF.
      6. CIL/MSIL - CPU-independent intermediate code every compiler
                produces.
      7. ASSEMBLIES - unit of deployment (.dll/.exe): CIL + metadata
                + manifest.
      8. JIT COMPILER - converts CIL to native code, method by method,
                on first call.
      9. CAS  - Code Access Security: restricts code by its origin.
   ```

   Architecture
   ```
      +------------------------------------------------+
      | Applications : ASP.NET , WinForms , WPF , WCF   |
      +------------------------------------------------+
      |  FCL - Framework Class Library (includes BCL)   |
      +------------------------------------------------+
      |  CLR : JIT , Garbage Collector , CTS , CLS ,    |
      |        security , exception handling            |
      +------------------------------------------------+
      |               Windows Operating System          |
      +------------------------------------------------+
   ```
   - `Managed code` runs under the CLR (memory, type safety, security handled for you); `unmanaged code` manages its own memory.
   - Successor: `.NET Core`/`.NET` (5, 6, 7+) is cross-platform and open source; the classic Framework is Windows-only and gets no new features.

2. **What is CLR in .NET framework? List the components of .NET Framework.** *[Bangladesh Television Assistant Programmer 2019 compact it 1066 (ET: N/A)]*, *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

Answer: What CLR is
   - `CLR` (Common Language Runtime) is the .NET Framework's execution engine — the virtual machine that runs .NET programs. Code running under it is `managed code`: the CLR manages its memory, type safety and security.

   What the CLR does
   ```
      JIT COMPILATION    - compiles CIL to native code per method, on
                           first call; the result is cached.
      GARBAGE COLLECTION - frees unreferenced objects automatically.
      MEMORY MANAGEMENT  - allocates/compacts the managed heap.
      TYPE SAFETY        - no raw pointer arithmetic in managed code.
      EXCEPTION HANDLING - one model shared by every .NET language.
      THREAD MANAGEMENT  - thread pool, sync, async support.
      SECURITY (CAS)     - what code may do depends on its origin.
      INTEROPERABILITY   - all languages share CIL, so a VB.NET class
                           can be inherited by a C# class.
   ```

   The components of the .NET Framework
   ```
      1. CLR   Common Language Runtime - the execution engine.
      2. CTS   Common Type System - C# int and VB.NET Integer are the
               same type underneath.
      3. CLS   Common Language Specification - subset of CTS; minimum
               interoperability rules.
      4. BCL   Base Class Library - System, collections, file I/O,
               threading, networking.
      5. FCL   Framework Class Library - BCL + ASP.NET, ADO.NET,
               WinForms, WPF, LINQ, XML, WCF.
      6. CIL   Common Intermediate Language - CPU-independent code
               every compiler emits.
      7. ASSEMBLIES - unit of deployment: .dll/.exe with CIL, metadata,
               manifest.
      8. JIT COMPILER - CIL to native code, on demand.
      9. CAS   Code Access Security.
   ```

   Layered view
   ```
      +------------------------------------------------+
      | ASP.NET , WinForms , WPF , WCF , ADO.NET        |
      +------------------------------------------------+
      |   FCL - Framework Class Library (includes BCL)  |
      +------------------------------------------------+
      |   CLR : JIT , GC , CTS , CLS , security         |
      +------------------------------------------------+
      |              Windows Operating System           |
      +------------------------------------------------+
   ```
   - The CLR is to .NET what the `JVM` is to Java, but the JVM targets one language on many platforms, while the CLR was designed for `many languages` on one platform (though `.NET Core` made it cross-platform too).

3. **List the components of .NET Framework.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

Answer: The components of the .NET Framework
   ```
      1. CLR   Common Language Runtime - execution engine: JIT
               compilation, garbage collection, memory management,
               type safety, exception handling, threading, security.
      2. CTS   Common Type System - C# int and VB.NET Integer are the
               same type underneath, enabling cross-language inheritance.
      3. CLS   Common Language Specification - subset of CTS; minimum
               rules every .NET language must follow to interoperate.
      4. BCL   Base Class Library - System, collections, strings,
               file I/O, threading, networking.
      5. FCL   Framework Class Library - includes BCL, plus ASP.NET
               (web), ADO.NET (database), WinForms/WPF (desktop),
               LINQ, XML, WCF.
      6. CIL/MSIL - Common Intermediate Language: CPU-independent code
               every compiler produces.
      7. ASSEMBLIES - unit of deployment: .dll/.exe with CIL, metadata,
               manifest, resources.
      8. JIT COMPILER - CIL to native code, method by method, cached
               after first call.
      9. CAS   Code Access Security - limits code by its origin.
     10. CLI   Common Language Infrastructure - the published standard
               (ECMA-335) the whole design follows.
   ```

   Architecture
   ```
      +------------------------------------------------+
      | ASP.NET , WinForms , WPF , WCF , ADO.NET        |
      +------------------------------------------------+
      |   FCL - Framework Class Library (includes BCL)  |
      +------------------------------------------------+
      |   CLR : JIT , Garbage Collector , CTS , CLS ,   |
      |         exception handling , security           |
      +------------------------------------------------+
      |              Windows Operating System           |
      +------------------------------------------------+
   ```
   - The pair examiners often ask to distinguish: `CTS` is the complete type system; `CLS` is the smaller subset of rules that guarantees cross-language interoperability — every CLS rule is a CTS rule, not the reverse.

4. **Write down the component of .NET Framework.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*

Answer: The components of the .NET Framework
   ```
      1. CLR - COMMON LANGUAGE RUNTIME
           The execution engine. Provides JIT compilation, garbage
           collection, memory management, type safety, exception
           handling, threading and security.

      2. CTS - COMMON TYPE SYSTEM
           The rules for declaring and using types, so that C# int and
           VB.NET Integer are the same type underneath. This makes
           cross-language inheritance possible.

      3. CLS - COMMON LANGUAGE SPECIFICATION
           A SUBSET of CTS : the minimum rules a language must obey to
           interoperate with the other .NET languages.

      4. BCL - BASE CLASS LIBRARY
           Core classes : System, collections, strings, file I/O,
           threading, networking.

      5. FCL - FRAMEWORK CLASS LIBRARY
           Includes the BCL, plus ASP.NET (web), ADO.NET (database),
           Windows Forms and WPF (desktop), LINQ, XML and WCF.

      6. CIL / MSIL
           The CPU-independent intermediate code every .NET compiler
           emits.

      7. ASSEMBLIES
           The unit of deployment - a .dll or .exe holding CIL,
           metadata, a manifest and resources.

      8. JIT COMPILER
           Turns CIL into native code, method by method, on first call.

      9. CAS - CODE ACCESS SECURITY
           Restricts what code may do, based on its origin.
   ```

   Layered view
   ```
      +------------------------------------------------+
      | ASP.NET , WinForms , WPF , WCF , ADO.NET        |
      +------------------------------------------------+
      |   FCL - Framework Class Library (includes BCL)  |
      +------------------------------------------------+
      |   CLR : JIT , GC , CTS , CLS , security         |
      +------------------------------------------------+
      |              Windows Operating System           |
      +------------------------------------------------+
   ```

   How the pieces fit together
   ```
      C# / VB.NET source
           |  compiler
           v
      CIL + metadata , packaged as an ASSEMBLY
           |  CLR loads , JIT compiles
           v
      native machine code , with the GARBAGE COLLECTOR managing memory
   ```
   - The `CLR` is the one component to name first if only one is asked for — everything else either feeds it (CIL, assemblies) or is used by code running on it (BCL, FCL).

5. **What is garbage collection? Write down the difference between garbage collection in .NET 4 and earlier version of .NET** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

Answer: What garbage collection is
   - `Garbage collection (GC)` is automatic memory management. The runtime finds objects that the program can no longer reach and frees the memory they occupy, so the programmer never calls `delete` or `free`.
   ```
      The rule : an object is GARBAGE when NO REFERENCE reaches it
      from a ROOT.

      Roots = static fields , local variables on the stack , CPU
              registers , GC handles.

           root ---> A ---> B          A and B are REACHABLE - keep
                     C ---> D          C and D are UNREACHABLE - free
   ```
   - What it prevents: `memory leaks`, `dangling pointers` and `double free` — three of the commonest bugs in C and C++.

   The generational heap in .NET
   ```
      The GC exploits the observation that MOST OBJECTS DIE YOUNG.

      GEN 0   newly created , small objects.
              Collected very often , and very fast.
      GEN 1   survivors of one Gen 0 collection.
              A buffer between short-lived and long-lived objects.
      GEN 2   long-lived objects - static data, caches.
              Collected rarely , because it is expensive.
      LOH     Large Object Heap - objects over 85,000 bytes.
              Collected with Gen 2 , and NOT compacted by default.
   ```
   ```
      Phases of a collection :
           MARK    - walk from the roots and mark everything reachable
           SWEEP   - treat everything unmarked as free
           COMPACT - slide surviving objects together, so free memory
                     is one contiguous block and allocation stays a
                     simple pointer bump
   ```

   Garbage collection in .NET 4 compared with earlier versions

   | Point | Before .NET 4 | .NET 4 and later |
   |---|---|---|
   | Mode for Gen 2 | `Concurrent GC` | `Background GC` |
   | Gen 0/1 during a Gen 2 collection | `Blocked` — must wait | `Allowed` to run |
   | User threads during Gen 2 | Suspended when a Gen 0/1 collection was needed | Keep running far longer |
   | Pause times | Longer and less predictable | `Shorter`, more predictable |
   | Where supported in .NET 4 | Concurrent, workstation only | Background, `workstation` only |
   | Server GC | Suspends threads for the whole collection | Background server GC arrived in `.NET 4.5` |

   The key change
   ```
      BEFORE .NET 4 (Concurrent GC): a background thread collected
      Gen 2, but a needed Gen 0/1 collection during that pass BLOCKED
      the program's threads until it finished.

      .NET 4 (Background GC): an ephemeral Gen 0/1 collection can now
      run IN THE MIDDLE of a background Gen 2 pass, so the app no
      longer waits - pauses are much shorter, a real win for
      interactive / latency-sensitive apps.
   ```

   Other .NET 4 additions
   ```
      GC.Collect(gen, GCCollectionMode.Optimized) - collect only if
           worthwhile.
      GCSettings.LatencyMode (SustainedLowLatency in 4.5) - suppress
           blocking Gen 2 collections during a critical phase.
      LOH compaction added later, in .NET 4.5.1.
   ```

   - Two practical points: the GC manages `managed memory` only — unmanaged resources (files, sockets, DB connections) still need `Dispose()`/`using`. And calling `GC.Collect()` manually is usually a mistake, since it forces a full collection that the GC's own heuristics would normally avoid.

6. **What is .NET framework? Write the main components of .NET framework?** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

Answer: What the .NET Framework is
   - The `.NET Framework` is Microsoft's platform for building and running applications on Windows: a `runtime` that executes the code plus a large `class library` of ready-made functionality. Its defining feature is `language independence` — C#, VB.NET and F# all compile to the same intermediate language (CIL), so a VB.NET class can be inherited by a C# class. It also gives the developer automatic memory management (GC), type safety and a uniform exception model across languages.

   The main components
   ```
      1. CLR - Common Language Runtime: execution engine - JIT
               compilation, garbage collection, type safety, exception
               handling, thread management, security.
      2. CTS - Common Type System: C# int and VB.NET Integer are one
               and the same type underneath.
      3. CLS - Common Language Specification: subset of CTS - minimum
               rules so code is consumable from any .NET language.
      4. BCL - Base Class Library: System, collections, strings,
               file I/O, threading, networking.
      5. FCL - Framework Class Library: BCL + ASP.NET (web), ADO.NET
               (database), WinForms/WPF (desktop UI), LINQ, XML, WCF.
      6. CIL/MSIL - the CPU-independent intermediate code.
      7. ASSEMBLIES - the .dll/.exe unit of deployment, holding CIL,
               metadata, a manifest and resources.
      8. JIT COMPILER - CIL to native code, method by method.
      9. CAS - Code Access Security.
   ```

   Architecture
   ```
      +------------------------------------------------+
      | ASP.NET , WinForms , WPF , WCF , ADO.NET        |
      +------------------------------------------------+
      |   FCL - Framework Class Library (includes BCL)  |
      +------------------------------------------------+
      |   CLR : JIT , Garbage Collector , CTS , CLS ,   |
      |         exception handling , security           |
      +------------------------------------------------+
      |              Windows Operating System           |
      +------------------------------------------------+
   ```
   - `Managed code` runs under the CLR, which handles its memory, types and security; `unmanaged code` manages its own. The classic `.NET Framework` is Windows-only with no new features; its successor `.NET Core`/`.NET` (5, 6, 7+) is open source and cross-platform.
