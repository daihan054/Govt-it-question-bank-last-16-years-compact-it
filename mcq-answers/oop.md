<!-- TOC START -->
**Table of Contents** — 7 subtopics · 100 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Java Programming](#java-programming-48) | 48 |
| 2 | [Polymorphism & Overloading](#polymorphism--overloading-16) | 16 |
| 3 | [OOP Concepts & Principles](#oop-concepts--principles-11) | 11 |
| 4 | [Encapsulation & Access Modifiers](#encapsulation--access-modifiers-7) | 7 |
| 5 | [Inheritance](#inheritance-6) | 6 |
| 6 | [Constructors & Destructors](#constructors--destructors-6) | 6 |
| 7 | [Exception Handling](#exception-handling-6) | 6 |

<!-- TOC END -->

---

## Java Programming (48)

1. **Which of the following statements about abstract classes and interfaces in Java is correct?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*  
   a) An abstract class can implement multiple interfaces.  
   b) An interface can have concrete methods (methods with a body).  
   c) An abstract class cannot have any method implementations.  
   d) A class can extend multiple abstract classes.

   answer: a — An abstract class can implement multiple interfaces  
   explanation: Java allows only single class inheritance, but a class — abstract or not — may implement any number of interfaces; interfaces can also hold default methods.

2. **Which of the following correctly describes the meaning of "Class", "&&", and "&" in Java?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*  
   a) Class is a keyword to define a new class; && is a bitwise AND operator; & is a logical AND operator.  
   b) Class is used to create objects; && is a bitwise OR operator; & is a logical OR operator.  
   c) Class is used to create objects; && is a logical OR operator; & is a bitwise OR operator.  
   d) Class is a keyword to define a new class; && is a logical AND operator; & is a bitwise AND operator.

   answer: d — Class is a keyword to define a new class; && is a logical AND operator; & is a bitwise AND operator  
   explanation: && works on booleans and short-circuits, while & works bit by bit on integers (and as a non-short-circuit boolean AND).

3. **What is Java's machine code?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*  
   a) Java source code is directly executed by the CPU.  
   b) Java source code is compiled into platform-specific machine code by the Java compiler.  
   c) Java source code is compiled into assembly code, which is then executed by the CPU.  
   d) Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM).

   answer: d — Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM)  
   explanation: javac produces platform-independent .class bytecode, and the JVM runs it, JIT-compiling hot paths to native code.

4. **What type of variable should be used to store data that is important throughout an object's lifespan?** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*  
   (a) A reference variable  
   (b) A method variable  
   (c) An instance variable  
   (d) A parameter variable

   answer: c — An instance variable  
   explanation: An instance variable is created with the object and lives as long as the object does.

5. **A collection of objects that use common structure and a common behavior is knownas-** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*  
   (a) Object  
   (b) Entity  
   (c) Instance  
   (d) Class

   answer: d — Class  
   explanation: A class is the blueprint defining the attributes and behaviour shared by all its objects.

6. **The following method, which is intended to find the maximum element of the parameter array, is incorrect.** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*
   ```java
   public int max (int[] a) {
   int max = 0;
   for (int i=0; i<a.length;i++) {
   if(a[i]>max) {
   max = a[i];
   } }
   return max;
   }
   ```
   (a) It fails whenever the array a contains a 0.  
   (b) It fails whenever the array a contains a negative number.  
   (c) It fails whenever the array a contains only negative numbers.  
   (d) It fails whenever the first element of the array a is the largest.

   answer: c — It fails whenever the array a contains only negative numbers  
   explanation: max starts at 0, so if every element is below zero none beats it and the method wrongly returns 0.

7. **Read the following statement in a Java program that compiles and executes-** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*  
   **submarine.dive (depth); What can you say for sure?**  
   (a) depth must be an int  
   (b) dive must be the name of an instance field  
   (c) dive must be a method  
   (d) submarine must be the name of a class

   answer: c — dive must be a method  
   explanation: The parentheses after dive make it a method call; submarine could be a variable or a class, and depth could be any type the method accepts.

8. **What is the output of this Java program?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)], [Combined 4 Bank Assistant Programmer (AP) 2020 compact it 154 (ET: DU)]*
   ```java
   class Test{
   int i=1;
   }
   public class main{
   public static void main(String args[]) {
   Test t;
   System.out.println(t.i);
   }
   }
   ```
   a) The program will cause an runtime exception because the variable 'i' was not initialized  
   b) The program will cause an compile error because the object 't' was not initialized  
   c) 0  
   d) A garbage value

   answer: b — The program will cause an compile error because the object 't' was not initialized  
   explanation: Java refuses to compile a read of a local variable that has not been definitely assigned.

9. **Interfaces in Java are meant to be-** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)], [Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*  
   a) Extended  
   b) Implemented  
   c) Overridden  
   d) Used by creating object

   answer: b — Implemented  
   explanation: A class implements an interface and supplies bodies for its abstract methods; interfaces extend other interfaces.

10. **What is the result of compiling and running the following code?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 27 (ET: BIBM)]*
   ```java
   public class Test{
   public static void main(String[] args) {
   int[] a = new int[0];
   System.out.print(a.length);
   }
   }
   ```
   (a) 0  
   (b) Compilation error, arrays cannot be initialized to zero size  
   (c) None of the above  
   (d) Compilation error, it is length () not length

   answer: a — 0  
   explanation: A zero-length array is legal in Java, and length is a field, so it prints 0.

11. **What are the inbuit classes?** *[BCC Assistant Programmer 11.11.2023 compact it 35 (ET: N/A)]*  
   **Ans:** Predefined Method

   answer: Predefined (built-in) classes  
   explanation: Java ships with library classes such as String, Math, Scanner and ArrayList that can be used without writing them.

12. **What is syntax for call static method in class?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** class name, Method name

   answer: ClassName.methodName()  
   explanation: A static method belongs to the class, so it is called through the class name without creating an object.

13. **What does runFinalize() do?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** The runFinalization() method is a part of the Runtime class, and its purpose is to trigger the execution of the finalization methods of any objects that are awaiting finalization. Its sentence structure is as follows: public void runFinalization()

   answer: runFinalization() requests that the JVM run the pending finalize() methods of objects awaiting finalization  
   explanation: It is a method of the Runtime class (public void runFinalization()); finalization is deprecated in modern Java in favour of try-with-resources and Cleaner.

14. **Find the correct output: System.out.print('D' + 'E'+ 'F');** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*  
   a) 137  
   b) DEF  
   c) 207  
   d) DEF

   answer: c — 207  
   explanation: The chars promote to int, so 'D'+'E'+'F' = 68+69+70 = 207 and print shows the number.

15. **Find the output of the following code:** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*
   ```java
   int a=15, b=15;
   if((a-100) == (b-a)) System.out.print(b+a) ;
   else System.out.print(b-a) ;
   ```
   a) 100  
   b) 200  
   c) 0  
   d) 3

   answer: c — 0  
   explanation: a-100 is -85 and b-a is 0, so the condition is false and the else branch prints b-a = 0.

16. **Java Virtual Machine is-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*  
   (a) Acts as a full-fledged hypervisor  
   (b) Converts bytecodes to Operating System dependent code  
   (c) Is known as the Compiler of Java programming language  
   (d) Manages system memory and provides a portable execution environment for Java-bases applications

   answer: d — Manages system memory and provides a portable execution environment for Java-bases applications  
   explanation: The JVM loads and verifies bytecode, manages the heap and garbage collection, and gives the same runtime on every platform.

17. **Which of the following is not a method of the Thread class?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*  
   a. sleep (long msec)  
   b. stop()  
   c. go()  
   d. yield()

   answer: c — go()  
   explanation: Thread provides sleep(), stop(), yield(), start(), run() and join() — there is no go().

18. **Which of the following statements is correct regarding abstract classes?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*  
   a. An abstract class cannot be extended  
   b. A subclass of a non-abstract superclass cannot be abstract  
   c. A subclass can override a concreate method in a superclass to declare it abstract  
   d. An abstract class cannot be used as a data type

   answer: c — A subclass can override a concreate method in a superclass to declare it abstract  
   explanation: A subclass may redeclare an inherited concrete method as abstract, which then forces its own subclasses to implement it.

19. **What is the output of this Java program?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)]*
   ```java
   class Test {
   int i;
   }
   class Main {
   public static void main(String args[]) {
   Test t;
   System.out.println(t.i);
   }
   }
   ```
   a. 0  
   b. A garbage value  
   c. compiler error  
   d. runtime error

   answer: c — compiler error  
   explanation: The local variable t is never assigned, and Java will not compile a use of an unassigned local variable.

20. **Converting a primitive type data into its corresponding wrapper class object instance is called-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 86 (ET: N/A)]*  
   a. Boxing  
   b. Wrapping  
   c. Instantiation  
   d. Auto boxing

   answer: a — Boxing  
   explanation: Boxing wraps a primitive in its wrapper object; when the compiler inserts it for you it is called autoboxing.

21. **Which information is not correct for any constructor of a java class?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*  
   a) Constructor is not inherited  
   b) Constructor has no return type  
   c) Constructor can be final  
   d) Constructor can be overloaded

   answer: c — Constructor can be final  
   explanation: A constructor is never inherited, so final is meaningless and not allowed on it; constructors do have no return type and can be overloaded.

22. **What is the output of this Java program?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*
   ```java
   class Test {
   int i;
   }
   public class Main {
   public static void main(String args[]) {
   Test t = new Test();
   System.out.println(t.i);
   }
   }
   ```
   a) The program will cause an compile error because the object “t” was not initialized  
   b) The program will cause an runtime exception because the variable “i” was not initialized  
   c) A garbage value  
   d) 0

   answer: d — 0  
   explanation: The object is created, and instance fields get default values, so the int i is 0.

23. **Which of the following statements is/are true about Inheritance in Java?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*  
   i) Private methods are final  
   ii) Protected methods are final  
   iii) Private methods cannot be overridden  
   iv) Protected members of a class are accessible by inherited classes of another package  
   a) i, iii and iv  
   b) i and iii only  
   c) ii, iii and iv  
   d) ii and iv only

   answer: a — i, iii and iv  
   explanation: Private methods are implicitly final and invisible to subclasses so cannot be overridden, and protected members are reachable from a subclass even in another package; protected methods are not final.

24. **Which of the followings can be used in a Java Server Page (JSP) page?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*  
   a) HTML  
   b) AJAX  
   c) JSTL  
   d) All of the above

   answer: d — All of the above  
   explanation: A JSP page mixes HTML markup with JSTL tags, and the delivered page can carry AJAX scripts.

25. **Which of the following statements is not true for Java Language?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*  
   a) The number 1 can be used instead of the keyword ‘true’  
   b) Trying to store a fraction value in an ‘int’ datatype causes compile error  
   c) Static members of a class can be accessed without creating objects of that class  
   d) If not specified otherwise, the initial value of an integer variable is 0

   answer: a — The number 1 can be used instead of the keyword 'true'  
   explanation: Java has a strict boolean type, so an int cannot stand in for true as it can in C.

26. **Find the output of following Java code line: System.out.println (math.floor (-7.4)** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*  
   A) -7  
   B) -7.4  
   C) -8  
   D) -7.2

   answer: C — -8  
   explanation: Math.floor rounds down towards negative infinity, so -7.4 becomes -8.0.

27. **Which of the following is not an operator in Java?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*  
   A) instanceof  
   B) sizeof  
   C) new  
   D) All of this

   answer: B — sizeof  
   explanation: Java has no sizeof operator; instanceof and new are both genuine Java operators.

28. **In Java, which operator is used to create an object?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*  
   A) class  
   B) scanf  
   C) print  
   D) None of these

   answer: D — None of these  
   explanation: Objects are created with the new operator, which is not among the listed options.

29. **Which of the following produce an answer that is closest in value to a double, d, while not being greater than d?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)], [Combined Bank Maintenance Engineer 2018 compact it 229 (ET: N/A)]*  
   A) (int.Math.min(d))  
   B) (int.Math.max(d))  
   C) int.Math.abs(d))  
   D) (int).Math.floor(d))

   answer: D — (int).Math.floor(d))  
   explanation: Math.floor gives the largest whole value not greater than d, and casting to int keeps it as an integer.

30. **Which keyword must be used to inherit class in java?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*  
   A) extends  
   B) super  
   C) this  
   D) extend

   answer: A — extends  
   explanation: A class inherits from another with extends; implements is used for interfaces.

31. **A class that is inherited in java is called a ________.** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*  
   A) sub class  
   B) super class  
   C) state class  
   D) implement class

   answer: B — super class  
   explanation: The class being inherited from is the superclass (parent); the one inheriting is the subclass.

32. **Which one of these interfaces is implemented by thread class?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) Set  
   B) Connections  
   C) Runnable  
   D) None of above

   answer: C — Runnable  
   explanation: Thread implements Runnable, which declares the single run() method.

33. **In java, which operator is used to create an object?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) class  
   B) scanf  
   C) print  
   D) None of above

   answer: D — None of above  
   explanation: The new operator creates objects, and it is not listed.

34. **In java, which one will be used for comprising whether the two String object str1 and str2 are same?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*  
   A) str1=str2  
   B) str1.equalsIgnoreCase(str2)  
   C) str1==str2  
   D) All of above

   answer: B — str1.equalsIgnoreCase(str2)  
   explanation: Content must be compared with a method, not ==, which only tests whether both refer to the same object; equals() is the case-sensitive form.

35. **Which of these data types is used by operating system to manage the Recursion in Java?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) Array  
   B) Stack  
   C) Queue  
   D) Tree

   answer: B — Stack  
   explanation: Each recursive call pushes an activation record with its parameters and return address onto the call stack.

36. **Which of the following is an incorrect statement about packages?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) Package defines a namespace in which classes are stored  
   B) A package can contain other packages within  
   C) A package can be renamed without renaming the directory, in which the classes are stored  
   D) Java uses file system directories to store packages

   answer: C — A package can be renamed without renaming the directory, in which the classes are stored  
   explanation: Java maps package names onto directory names, so renaming the package means renaming the folder too.

37. **Multiple inheritances in Java can be implemented using which of the following?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) Interfaces  
   B) Multithreading  
   C) Protected methods  
   D) Private methods

   answer: A — Interfaces  
   explanation: A class can implement several interfaces, which gives the effect of multiple inheritance without the diamond problem.

38. **Which component is used to compile, debug and execute in Java program?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) JVM  
   B) JDK  
   C) JIT  
   D) JRE

   answer: B — JDK  
   explanation: The JDK contains the compiler, debugger and other tools plus the JRE needed to run the program.

39. **int C=10; System.out.println(C--); gives a output of-** *[Combined Bank Senior Officer (IT) 2018 compact it 224 (ET: DU)]*  
   A) 10  
   B) 11  
   C) 9  
   D) 8

   answer: A — 10  
   explanation: C-- is post-decrement, so the current value 10 is printed and C only then becomes 9.

40. **In java, which operator is used to create an object?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*  
   A) class  
   B) scanf  
   C) print  
   D) None

   answer: D — None  
   explanation: Objects are created with new, which is not among the options.

41. **Which of the keywords can be used in a subclass to call the constructor of superclass?** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*  
   A) Extent  
   B) Extends  
   C) Super  
   D) This

   answer: C — Super  
   explanation: super(...) as the first statement of a constructor invokes the superclass constructor.

42. **Which of the following is a valid declaration of an object of class Box?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*  
   A) Box obj = new Box();  
   B) Box obj = new Box;  
   C) obj = new Box();  
   D) new Box obj;

   answer: A — Box obj = new Box();  
   explanation: Declaring a reference and calling the constructor with new and parentheses is the correct form.

43. **In Java, which operator is used to create an object-** *[Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*  
   A) Class  
   B) scanf  
   C) Print  
   D) none of them

   answer: D — none of them  
   explanation: The new operator creates objects in Java, and it is not listed.

44. **A class that is inherited in java is called a ________.** *[Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*  
   A) Subclass  
   B) Super class  
   C) Static class  
   D) Implement class

   answer: B — Super class  
   explanation: The inherited (parent) class is called the superclass.

45. **In Java, which operator is used to create an object?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*  
   A) class  
   B) scanf  
   C) print  
   D) New

   answer: D — New  
   explanation: The new operator allocates the object and calls its constructor.

46. **Java source code is compiled into ________** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*  
   A) Source Code  
   B) Byte Code  
   C) Object  
   D) .exe

   answer: B — Byte Code  
   explanation: javac produces platform-independent bytecode that the JVM executes.

47. **Which one of these lists contains only Java programming language keywords?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. class, if, void, long, int, continue  
   b. goto, instanceof, native, finally, default, throws  
   c. try, virtual, throw, final, volatile, transient  
   d. strictfp, constant, super, implements, do

   answer: a — class, if, void, long, int, continue  
   explanation: All six are Java keywords; option (c) has "virtual" and (d) has "constant", neither of which exists in Java.

48. **Which method must be defined by a class implementing java.lang.Runnable interface?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. void run()  
   b. public void run()  
   c. public void start()  
   d. void run(int priority)

   answer: b — public void run()  
   explanation: Runnable declares run() as public, and an implementing class may not reduce that visibility.

## Polymorphism & Overloading (16)

1. **Which of the following operators should be preferred to overload as a global function rather than a member method?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxii (ET: DU)]*  
   (a) Postfix ++  
   (b) Comparison Operator  
   (c) Insertion Operator <<  
   (d) Prefix++

   answer: c — Insertion Operator <<  
   explanation: For cout << obj the left operand is the stream, not your class, so << must be a global (usually friend) function.

2. **Which of the following operators cannot be overloaded in C/C++ ?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*  
   (a) Bitwise right shift assignment  
   (b) Address of  
   (c) Indirection  
   (d) Structure reference

   answer: d — Structure reference  
   explanation: The dot member-access operator cannot be overloaded in C++; >>=, & and * all can.

3. **A feature of Object oriented programming languages that allows a specific routine to use variables of different types at different times, is called OOP?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** Polymorphism

   answer: Polymorphism  
   explanation: Polymorphism lets the same operation behave differently depending on the type of object it acts on.

4. **A function having more than one distinct meaning is called ______ function** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*  
   (ক) Parameter  
   (খ) Prototype  
   (গ) Overloaded  
   (ঘ) Polymorphism

   answer: গ — Overloaded  
   explanation: Function overloading gives one name several versions distinguished by their parameter lists.

5. **The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)]*  
   a. Inheritance  
   b. Polymorphism  
   c. Over functioning  
   d. Overriding

   answer: b — Polymorphism  
   explanation: The same call resolves to a different implementation depending on the actual object type.

6. **The most common use of ________ in OOP occurs when a parent class reference is used to refer to a child class object.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 174 (ET: N/A)]*  
   a) Polymorphism  
   b) Inheritance  
   d) Encapsulation  
   d) Method overriding

   answer: a — Polymorphism  
   explanation: Holding a child object in a parent-type reference and having the overridden method run is runtime polymorphism.

7. **Which of the following is the destructor of class Vehicle?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*  
   A) *Vehicle()  
   B) ~Vehicle ()  
   C) ~Vehicle (int value)  
   D) *Vehicle (int value)

   answer: B — ~Vehicle ()  
   explanation: A destructor has the class name preceded by ~, takes no parameters and returns nothing.

8. **The operator that cannot be overloaded is ________.** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*  
   A) ++  
   B) ()  
   C) ~  
   D) ::

   answer: D — ::  
   explanation: The scope resolution operator ::, along with ., .* and ?:, cannot be overloaded.

9. **Which functions overloads the ">>" operator?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*  
   A) gt()  
   B) more()  
   C) ge()  
   D) None of this

   answer: D — None of this  
   explanation: The extraction operator is overloaded by defining operator>>, not by any function called gt, more or ge.

10. **Which of the following operator functions cannot be global i.e. must be a member function?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*  
   A) Conversion operator  
   B) new  
   C) delete  
   D) all of these

   answer: A — Conversion operator  
   explanation: A conversion operator converts the object it belongs to, so it must be a member; new and delete may be defined globally.

11. **Which of the following is the destructor for class “vehicle”?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*  
   A) *vehicle()  
   B) *vehicle (int value)  
   C) ~vehicle()  
   D) ~vehicle (int value)

   answer: C — ~vehicle()  
   explanation: The destructor is named ~ClassName, takes no arguments and cannot be overloaded.

12. **Which operator that can be overloaded is?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) ++  
   B) ::  
   C) . (dot)  
   D) 0

   answer: A — ++  
   explanation: The increment operator can be overloaded; ::, . and .* cannot.

13. **How many instances of an abstract can be created?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) 0  
   B) 1  
   C) 2  
   D) 13

   answer: A — 0  
   explanation: An abstract class has at least one method with no implementation, so it can never be instantiated directly.

14. **If same message is passed to objects of several different classes and all of those can respond in a different way, what is this feature called?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*  
   A) Inheritance  
   B) Overloading  
   C) Polymorphism  
   D) Overriding

   answer: C — Polymorphism  
   explanation: One message producing different behaviour in different classes is exactly polymorphism.

15. **What is the process of defining two or more methods within the same class that have same name but different parameters declaration?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*  
   A) Method overriding  
   B) Method overloading  
   C) Method hiding  
   D) Method duplicating

   answer: B — Method overloading  
   explanation: Same name with different parameter lists inside one class is overloading, resolved at compile time.

16. **Overloaded functions are ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*  
   a. Very long functions that can hardly run  
   b. One function containing another one or more functions inside it  
   c. Two or more functions with same name but different number of parameter or type  
   d. None of above

   answer: c — Two or more functions with same name but different number of parameter or type  
   explanation: The compiler picks the right version by matching the argument list.

## OOP Concepts & Principles (11)

1. **Which of the following is not property of the Object Oriented Programming Concept?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*  
   a) Encapsulation  
   b) Inheritance  
   c) Exception  
   d) Abstraction

2. **Which of the following modifiers cannot be applied to a method in C++?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*  
   (ক) Protected  
   (খ) Private  
   (গ) Public  
   (ঘ) Abstract

3. **Which is not the feature of JAVA OOP?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 180 (ET: N/A)]*  
   a) Multiple Inheritance  
   b) Multi-level inheritance  
   c) Compile time Polymorphism  
   d) Runtime Polymorphism

4. **Object Oriented programming এর বৈশিষ্ট্য কোনটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*  
   A) Polymorphism  
   B) Friend function  
   C) Structure  
   D) Loop

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 189 (ET: N/A)]*  
   A) Inheritance  
   B) Abstraction  
   C) Polymorphism  
   D) Overloading

6. **Which of the following provides a programmer with the facility of using object of a class inside other classes?** *[Probashi Kallyan Bank Programmer: 2019 compact it 209 (ET: AUST)]*  
   A) Inheritance  
   B) Abstraction  
   C) Encapsulation  
   D) Composition

7. **Which one is pure object-oriented language?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 219 (ET: N/A)]*  
   A) C++  
   B) C+  
   C) Java  
   D) None

8. **Which is not feature of object-oriented programming?** *[Combined Bank Maintenance Engineer 2018 compact it 225 (ET: N/A)]*  
   A) inheritance  
   B) recursion  
   C) encapsulation  
   D) abstraction

9. **Which is not a feature of object-oriented programming?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*  
   A) Inheritance  
   B) Encapsulation  
   C) Recursion  
   B) Abstraction

10. **Which one of the following is the core property of Object-Oriented Programming?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 259 (ET: N/A)]*  
   A) Encapsulation, inheritance  
   B) Encapsulation, Object  
   C) polymorphism, overloading  
   D) Encapsulation, polymorphism and inheritance

11. **In object Oriented Programming, a property can be accessed from ________** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*  
   A) Anywhere the project  
   B) Only from its own class  
   C) Parent class  
   D) Child class

## Encapsulation & Access Modifiers (7)

1. **Which of the following does NOT achieve encapsulation?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*  
   (a) Using private access specifier  
   (b) Using classes in object-oriented programming  
   (c) Using getter and setter methods  
   (d) Using global variables

2. **Which variable violates the principle of ecvapsulation?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** Gobal variable

3. **Which of the following is a technique for hiding the internal implementation details of an object?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 115 (ET: N/A)]*  
   a) Encapsulation  
   b) Polymorphism  
   c) Inheritance  
   d) All of the above

4. **What is the characteristic of OOP programming that allows binding data and methods to work as a unit?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)]*  
   a. Inheritance  
   b. Encapsulation  
   c. Polymorphism  
   d. Projection

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** *[Bangladesh Bank Data Entry Operator (IT) 2020 compact it 189 (ET: N/A)]*

6. **In C++, the idea to hiding the details of how something is implemented is known as** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*  
   A) inheritance  
   B) encapsulation  
   C) recursion  
   D) polymorphism

7. **In C++, the idea to hiding the details of how something is implemented is known as-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*  
   A) inheritance  
   B) polymorphism  
   C) recursion  
   D) encapsulation

## Inheritance (6)

1. **When a class serves as base class for many derived classes, the situation is called-** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*  
   a) Polymorphism  
   b) hierarchical inheritance  
   c) Hybrid inheritance  
   d) Multipath inheritance

2. **Which language is not support OOP four Inheritance feature?** *[BREB Assistant Programmer 2023 compact it 33 (ET: N/A)]*  
   (a) Smaltalk  
   (b) Java  
   (c) C  
   (d) C++

3. **Which type of members can't accessed in derived classes of a base class?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** Private members

4. **What is default level of inheritance has to be specified in C++?** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*  
   (a) Public  
   (b) Private  
   (c) Protected  
   (d) Compile time error

5. **A derived class inherits attributes from a-** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) Super Class  
   B) Sub Class  
   C) Inner Class  
   D) Upper Class

6. **How to access the overridden method of base class from the derived class?** *[Combined Bank Senior Officer (IT) 2018 compact it 222 (ET: DU)]*  
   A) Using arrow operator  
   B) Using dot operator  
   C) Using scope resolution operator  
   D) Can't be accessed once overridden

## Constructors & Destructors (6)

1. **Which of the following is true regarding a constructor in Object Oriented Programming?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) May consist of a return type  
   b) Does not consist of any return type  
   c) has some return type  
   d) None of the above

2. **A constructor is a special type of-** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*  
   (a) Class  
   (b) Field  
   (c) Method  
   (d) Property

3. **Which part of a class is invoked when an object is initialized in java?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 239 (ET: N/A)]*  
   A) constructor  
   B) fields  
   C) methods  
   D) class

4. **Which operator is used to declare the destructor in C++?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) #  
   B) ~  
   C) @  
   D) $

5. **Object being passed to a copy constructor-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*  
   A) Must be passed by reference  
   B) Must not be mentioned in parameter list  
   C) Must be passed with integer type  
   D) Must be passed by value

6. **Does constructor overloading include different return types for constructors to be overloaded?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*  
   A) Yes, if return types are different, signature becomes different  
   B) Yes, because return types can differentiate two functions  
   C) No, return type can't differentiate two functions  
   D) No, constructors don't have any return type

## Exception Handling (6)

1. **The statements that allows you to define a block of code to be tested for exceptions while it is being executed.** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** Try-cache

2. **The ________ block used to execute a given set of the statement whether the exception is thrown or not.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 171 (ET: N/A)]*  
   a) try  
   b) tryif  
   c) finally  
   d) thrown

3. **Java uses a keyword ________ to preface a block of code that is likely to cause an error condition and ‘throw’ an exception.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 171 (ET: N/A)]*  
   a) throw  
   b) catch  
   c) finally  
   d) try

4. **Which of the following method(s) not included in InputStream class?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 171 (ET: N/A)]*  
   a) available()  
   b) reset()  
   c) flush()  
   d) close()

5. **Which alternative can replace the throw statement in C++?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) for  
   B) break  
   C) return  
   D) exit

6. **Why do you need to handle exceptions?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*  
   A) To prevent abnormal termination of program  
   B) To encourage exception prone program  
   C) To avoid syntax errors  
   D) To save memory
