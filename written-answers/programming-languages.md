<!-- TOC START -->
**Table of Contents** — 1 subtopics · 6 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Visual Basic & .NET](#visual-basic--net-6) | 6 |

<!-- TOC END -->

---

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
