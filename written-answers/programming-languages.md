<!-- TOC START -->
**Table of Contents** — 2 subtopics · 13 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Core Programming Languages](#core-programming-languages-7) | 7 |
| 2 | [Visual Basic & .NET](#visual-basic--net-6) | 6 |

<!-- TOC END -->

---

## Core Programming Languages (7)

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

2. **Write down the difference between informed and uninformed search algorithm.** *[Dhaka Power Distribution Company (DPDC) Post: Junior Assistant Manager Exam Taker: BUET Date: 27.06.2025 [bitbox it book 82]]*

Answer:

    | Feature | Uninformed (Blind) Search | Informed (Heuristic) Search |
    |---|---|---|
    | Knowledge Used | Uses only problem definition and state domain; no domain heuristics | Uses domain-specific knowledge and heuristic evaluation function $h(n)$ |
    | Search Efficiency | Lower efficiency; traverses search tree systematically | High efficiency; guides traversal toward the most promising nodes |
    | Time & Space Complexity | Generally higher time and memory consumption ($O(b^d)$) | Significantly reduced search space and lower average execution time |
    | Direction of Search | Searches blindly without knowing distance to goal | Evaluates cost and estimates remaining distance to goal state |
    | Algorithms | BFS (Breadth-First), DFS (Depth-First), Uniform Cost Search (UCS) | A* Search, Greedy Best-First Search, Hill Climbing, IDA* |

3. **Number of SDGs (Sustainable Development Goals)?** *[Bangladesh Computer Council (BCC) Post: AP/Technical Writer (TW), ANE Marks: 80; Date: 18 Oct 2025 [bitbox it book 238]]*

Answer:
    - Total number of SDGs = **17 Goals** (comprising **169 specific targets**).
    - Adopted by the United Nations General Assembly in September 2015 under the 2030 Agenda for Sustainable Development (2016–2030).

4. **Write the RSA Algorithm used for public key cryptography.** *[ICB Asset Management Company Ltd Assistant Programmer; Date: 01 January 2024 Exam taker: FBS, DU; Marks: Non:50 Tech:50 [bitbox it book 318-319]]*

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
      - **Public Key**: $(e, n)$ (distributed openly for encryption)
      - **Private Key**: $(d, n)$ (kept secret for decryption)
    - Encryption: Given plaintext message $M$ ($M < n$):
      $$C = M^e \bmod n$$
    - Decryption: Given ciphertext $C$:
      $$M = C^d \bmod n$$

5. **Change the following sentences as directed:** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 330]]*
(a) He is capable to do the work. (Correct the sentence) (b) It is high time he leave the place. (Use the right form of verb) (c) Honesty is the best policy. (Transform the sentence into comparative degree) (d) Man is never content with long life. (e) The player (wear) Jersey No-10 is Messy. (Use the right form of verb) (f) I had been there. (Complete the sentence) (g) John, Tom and his friends were going to the playground. (Correct the sentence) (h) Four years - long time to complete the course. (Fill in the gap) (i) He is not loyal to me. (Correct the sentence) (j) He has said to me, “When will you come?” (Change the narration)

Answer:
    - (a) Corrected: He is capable **of doing** the work.
    - (b) Right form of verb: It is high time he **left** the place.
    - (c) Comparative degree: Honesty is **better than any other policy**.
    - (d) Affirmative transformation: Man is always discontented with short life.
    - (e) Right form of verb: The player **wearing** Jersey No-10 is Messi.
    - (f) Completed sentence: I had been there **before the storm began**.
    - (g) Corrected: John, Tom and **their** friends were going to the playground.
    - (h) Fill in the gap: Four years **is a** long time to complete the course.
    - (i) Corrected: He is not loyal to me. (The sentence is already grammatically correct).
    - (j) Indirect narration: He has asked me when I **would come** (or **would go**).

6. **SDG বা “Sustainable Development Goal” কী?** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 331]]*

Answer:
    এসডিজি (SDG - Sustainable Development Goals / টেকসই উন্নয়ন অভীষ্ট):
    - ২০১৫ সালের ২৫ সেপ্টেম্বর জাতিসংঘের সাধারণ অধিবেশনে গৃহীত বৈশ্বিক রূপরেখা, যা ২০১৬ থেকে ২০৩০ সাল পর্যন্ত বিশ্বব্যাপী দারিদ্র্য দূরীকরণ, জলবায়ু পরিবর্তন মোকাবেলা এবং অর্থনৈতিক সমৃদ্ধি ও বৈষম্যহীন সমাজ বিনির্মাণের লক্ষ্যে প্রণীত হয়েছে।
    - মূল বৈশিষ্ট্য: ১৭টি সুনির্দিষ্ট লক্ষ্য (Goals), ১৬৯টি সহযোগী লক্ষ্যমাত্রা (Targets) এবং ২৩২টি বৈশ্বিক সূচক অন্তর্ভুক্ত।
    - প্রধান অভীষ্টসমূহ: দারিদ্র্যমুক্তি, ক্ষুধা নিরসন, সুস্বাস্থ্য ও কল্যাণ, মানসম্মত শিক্ষা, লিঙ্গ সমতা, নিরাপদ পানি ও স্যানিটেশন, সাশ্রয়ী ও দূষণমুক্ত জ্বালানি এবং জলবায়ু কার্যক্রম।

7. **Consider the page reference of LRU Page Replacement Algorithm string in 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 3. Assume number for frame 4. Find number of page faults.** *[Jamuna Oil Company Ltd Post: Junior Officer (MIS & IT); Date: 23 May, 2024 Exam Taker: JOCL [compact it 397]]*

Answer:
    Given Reference String: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 3
    Number of Memory Frames = 4

    Step-by-Step Execution:
    - 1. Ref `7`: Frames `[7, -, -, -]` $\to$ **Page Fault 1**
    - 2. Ref `0`: Frames `[7, 0, -, -]` $\to$ **Page Fault 2**
    - 3. Ref `1`: Frames `[7, 0, 1, -]` $\to$ **Page Fault 3**
    - 4. Ref `2`: Frames `[7, 0, 1, 2]` $\to$ **Page Fault 4**
    - 5. Ref `0`: Frames `[7, 0, 1, 2]` $\to$ **Hit** (Recency: 7, 1, 2, 0)
    - 6. Ref `3`: Frames full. LRU page is `7`. Replace `7` with `3` $\to$ `[3, 0, 1, 2]` $\to$ **Page Fault 5** (Recency: 1, 2, 0, 3)
    - 7. Ref `0`: Frames `[3, 0, 1, 2]` $\to$ **Hit** (Recency: 1, 2, 3, 0)
    - 8. Ref `4`: Frames full. LRU page is `1`. Replace `1` with `4` $\to$ `[3, 0, 4, 2]` $\to$ **Page Fault 6** (Recency: 2, 3, 0, 4)
    - 9. Ref `2`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 3, 0, 4, 2)
    - 10. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 0, 4, 2, 3)
    - 11. Ref `0`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 4, 2, 3, 0)
    - 12. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 4, 2, 0, 3)
    - 13. Ref `2`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 4, 0, 3, 2)
    - 14. Ref `3`: Frames `[3, 0, 4, 2]` $\to$ **Hit** (Recency: 4, 0, 2, 3)

    Summary:
    - Total Page Faults = **6**
    - Total Hits = **8**

## Visual Basic & .NET (6)

1. **What is .NET framework? Write down the different component of .NET Framework.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1056 (ET: AUST)]*, *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

Answer: What the .NET Framework is
   - The `.NET Framework` is a software platform from Microsoft for building and running applications on Windows. It provides a `runtime` that executes the code and a large `class library` of ready-made functions, so the programmer does not rewrite common work.
   ```
      Key idea : LANGUAGE INDEPENDENCE.

      C# , VB.NET , F# , C++/CLI all compile to the SAME intermediate
      language (CIL), so a class written in VB.NET can be inherited by
      a C# class.

      C# source ---+
      VB.NET src --+---> compiler ---> CIL + metadata ---> CLR ---> native
      F# source ---+                   (an ASSEMBLY)       JIT      code
   ```

   The components
   ```
      1. CLR - COMMON LANGUAGE RUNTIME
           The execution engine, the heart of .NET. It provides :
             JIT compilation - CIL to native machine code
             GARBAGE COLLECTION - automatic memory management
             exception handling , thread management
             type safety and code access security

      2. CTS - COMMON TYPE SYSTEM
           Defines how types are declared and used, so that an int in
           C# and an Integer in VB.NET are the SAME type underneath.
           This is what makes cross-language inheritance possible.

      3. CLS - COMMON LANGUAGE SPECIFICATION
           A SUBSET of CTS - the minimum rules every .NET language must
           follow so its code can be used from any other .NET language.
           C# is case-sensitive and VB.NET is not, so a CLS-compliant
           public API must not rely on case alone to distinguish names.

      4. BCL - BASE CLASS LIBRARY
           The core classes : System, collections, file I/O, strings,
           threading, networking.

      5. FCL - FRAMEWORK CLASS LIBRARY
           The wider library, which INCLUDES the BCL and adds
           ASP.NET (web), ADO.NET (database), Windows Forms and WPF
           (desktop UI), LINQ, XML and WCF.

      6. CIL / MSIL - COMMON INTERMEDIATE LANGUAGE
           The CPU-independent code every .NET compiler produces.

      7. ASSEMBLIES
           The unit of deployment - a .dll or .exe holding CIL,
           metadata, a manifest and resources.

      8. JIT COMPILER
           Converts CIL to native code method by method, only when the
           method is first called.

      9. CAS - CODE ACCESS SECURITY
           Restricts what code may do, based on where it came from.
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
   - `Managed code` is code the CLR runs and looks after: memory, type safety and security are all handled for you. `Unmanaged code` runs outside the CLR and manages its own memory.
   - Note the successor: `.NET Core`, and now simply `.NET` (5, 6, 7 and later), is `cross-platform` and open source, running on Windows, Linux and macOS. The classic `.NET Framework` is Windows-only and is no longer given new features.

2. **What is CLR in .NET framework? List the components of .NET Framework.** *[Bangladesh Television Assistant Programmer 2019 compact it 1066 (ET: N/A)]*, *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

Answer: What CLR is
   - `CLR` stands for `Common Language Runtime`. It is the execution engine of the .NET Framework — the virtual machine that actually runs .NET programs. Code that runs under it is called `managed code`, because the CLR manages its memory, type safety and security.
   ```
      C# source ---+
      VB.NET src --+--> compiler --> CIL + metadata --> CLR --> native
      F# source ---+                 (an ASSEMBLY)      JIT     code
                                                               |
                                                               v
                                                             RUNS
   ```

   What the CLR does
   ```
      JIT COMPILATION
           Converts CIL (intermediate language) into native machine
           code, method by method, the first time each method is
           called. The compiled result is cached, so it is compiled
           once, not every time.

      GARBAGE COLLECTION
           Frees objects no longer referenced. The programmer never
           calls delete, so memory leaks and dangling pointers largely
           disappear.

      MEMORY MANAGEMENT
           Allocates on the managed heap and compacts it.

      TYPE SAFETY
           Verifies that code does not read memory it does not own -
           no pointer arithmetic in ordinary managed code.

      EXCEPTION HANDLING
           One exception model shared by every .NET language, so a C#
           try-catch can catch an exception thrown by VB.NET code.

      THREAD MANAGEMENT
           Thread pool, synchronisation, async support.

      SECURITY
           Code Access Security - what code may do depends on where it
           came from.

      LANGUAGE INTEROPERABILITY
           Because all languages compile to the same CIL, a VB.NET
           class can be inherited by a C# class.
   ```

   The components of the .NET Framework
   ```
      1. CLR   Common Language Runtime - the execution engine.
      2. CTS   Common Type System - how types are declared and used, so
               C# int and VB.NET Integer are the same type underneath.
      3. CLS   Common Language Specification - a SUBSET of CTS ; the
               minimum rules a language must follow to interoperate.
      4. BCL   Base Class Library - System, collections, file I/O,
               strings, threading, networking.
      5. FCL   Framework Class Library - includes the BCL and adds
               ASP.NET, ADO.NET, Windows Forms, WPF, LINQ, XML, WCF.
      6. CIL   Common Intermediate Language - the CPU-independent code
               every .NET compiler emits.
      7. ASSEMBLIES - the unit of deployment : a .dll or .exe holding
               CIL, metadata, a manifest and resources.
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
   - The comparison usually expected: the CLR is to .NET what the `JVM` is to Java. The important difference is that the JVM was designed for one language and many platforms, while the CLR was designed for `many languages` on one platform — though `.NET Core` has since made it cross-platform too.

3. **List the components of .NET Framework.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

Answer: The components of the .NET Framework
   ```
      1. CLR - COMMON LANGUAGE RUNTIME
           The execution engine, the core of .NET. It provides JIT
           compilation, garbage collection, memory management, type
           safety, exception handling, thread management and security.

      2. CTS - COMMON TYPE SYSTEM
           Defines how types are declared, used and managed, so C#
           int and VB.NET Integer are the SAME type underneath. This
           is what makes cross-language inheritance work.

      3. CLS - COMMON LANGUAGE SPECIFICATION
           A SUBSET of CTS - the minimum rules every .NET language
           must follow to interoperate. A CLS-compliant public API,
           for example, must not distinguish two names by CASE alone,
           because VB.NET is not case-sensitive.

      4. BCL - BASE CLASS LIBRARY
           The core classes : System, collections, strings, file I/O,
           threading, networking.

      5. FCL - FRAMEWORK CLASS LIBRARY
           The full library. It INCLUDES the BCL and adds ASP.NET for
           web, ADO.NET for databases, Windows Forms and WPF for
           desktop UI, plus LINQ, XML and WCF.

      6. CIL / MSIL - COMMON INTERMEDIATE LANGUAGE
           The CPU-independent code that every .NET compiler produces.

      7. ASSEMBLIES
           The unit of deployment - a .dll or .exe containing CIL,
           metadata, a manifest and resources.

      8. JIT COMPILER
           Turns CIL into native machine code, method by method, the
           first time each method is called. The result is cached.

      9. CAS - CODE ACCESS SECURITY
           Limits what code may do according to where it came from.

     10. COMMON LANGUAGE INFRASTRUCTURE (CLI)
           The published standard (ECMA-335) that the whole design
           follows.
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

   How a program runs
   ```
      C# / VB.NET source
           |  language compiler
           v
      CIL + metadata , packaged as an ASSEMBLY (.dll / .exe)
           |  CLR loads it , JIT compiles it
           v
      NATIVE MACHINE CODE  ->  executes , with the GC managing memory
   ```
   - The two components examiners ask to be distinguished are `CTS` and `CLS`. `CTS` is the complete type system; `CLS` is the smaller set of rules that guarantees interoperability. Every CLS rule is a CTS rule, but not the reverse.

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
      BEFORE .NET 4 - CONCURRENT GC
           A dedicated background thread collected Gen 2 while the
           program ran. BUT if the program needed a Gen 0 or Gen 1
           collection while that was in progress, the program's
           threads were BLOCKED until the Gen 2 pass finished.

      .NET 4 - BACKGROUND GC
           An EPHEMERAL collection (Gen 0 or Gen 1) can now run IN THE
           MIDDLE of a background Gen 2 collection. The application no
           longer has to wait for the long Gen 2 pass, so pauses are
           much shorter.

           This is why .NET 4 was a real improvement for interactive
           and latency-sensitive applications.
   ```

   Other .NET 4 additions
   ```
      GC.Collect(gen, GCCollectionMode.Optimized)  - ask the runtime
           to collect only if it would actually be worthwhile.
      GCSettings.LatencyMode , including SustainedLowLatency in 4.5,
           to suppress blocking Gen 2 collections during a critical
           phase.
      Better handling of the Large Object Heap , with LOH compaction
           made available later, in .NET 4.5.1.
   ```

   - Two practical points. First, the GC handles `managed memory` only — file handles, database connections and sockets are `unmanaged` and must be released by `Dispose()`, usually through a `using` block. Second, calling `GC.Collect()` by hand is almost always a mistake: it forces a full collection and usually makes performance worse, because the GC's own heuristics are better than a guess.

6. **What is .NET framework? Write the main components of .NET framework?** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

Answer: What the .NET Framework is
   - The `.NET Framework` is Microsoft's platform for building and running applications on Windows. It supplies a `runtime` that executes the code and a large `class library` of ready-made functionality, so common work is not written again from scratch.
   ```
      Its defining feature is LANGUAGE INDEPENDENCE :

      C# source ---+
      VB.NET src --+--> compiler --> CIL + metadata --> CLR --> native
      F# source ---+                 (an ASSEMBLY)      JIT     code

      All languages compile to the SAME intermediate language, so a
      class written in VB.NET can be inherited by a C# class.
   ```
   - What it gives the developer: `automatic memory management` through garbage collection, `type safety`, a uniform `exception model` across languages, and a very large standard library.

   The main components
   ```
      1. CLR - COMMON LANGUAGE RUNTIME
           The execution engine and the heart of .NET. Provides JIT
           compilation, garbage collection, type safety, exception
           handling, thread management and security.

      2. CTS - COMMON TYPE SYSTEM
           How types are declared and used, so C# int and VB.NET
           Integer are one and the same type underneath.

      3. CLS - COMMON LANGUAGE SPECIFICATION
           A SUBSET of CTS - the minimum rules a language must follow
           so its code can be consumed from any other .NET language.

      4. BCL - BASE CLASS LIBRARY
           System, collections, strings, file I/O, threading,
           networking.

      5. FCL - FRAMEWORK CLASS LIBRARY
           Includes the BCL and adds ASP.NET (web), ADO.NET
           (database), Windows Forms and WPF (desktop UI), LINQ, XML
           and WCF.

      6. CIL / MSIL - the CPU-independent intermediate code.
      7. ASSEMBLIES - the .dll or .exe unit of deployment, holding
           CIL, metadata, a manifest and resources.
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
   - The distinction to state clearly: `managed code` runs under the CLR, which looks after its memory, types and security; `unmanaged code` runs outside it and manages its own memory.
   - Worth one line at the end: the classic `.NET Framework` is Windows-only and receives no new features. Its successor, `.NET Core` — now simply `.NET` 5, 6, 7 and later — is open source and `cross-platform`, running on Windows, Linux and macOS.
