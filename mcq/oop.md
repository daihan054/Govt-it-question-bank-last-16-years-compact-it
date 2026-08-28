## Java Programming

1. **Which of the following statements about abstract classes and interfaces in Java is correct?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) An abstract class can implement multiple interfaces.
   b) An interface can have concrete methods (methods with a body).
   c) An abstract class cannot have any method implementations.
   d) A class can extend multiple abstract classes.

2. **Which of the following correctly describes the meaning of "Class", "&&", and "&" in Java?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) Class is a keyword to define a new class; && is a bitwise AND operator; & is a logical AND operator.
   b) Class is used to create objects; && is a bitwise OR operator; & is a logical OR operator.
   c) Class is used to create objects; && is a logical OR operator; & is a bitwise OR operator.
   d) Class is a keyword to define a new class; && is a logical AND operator; & is a bitwise AND operator.

3. **What is Java's machine code?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) Java source code is directly executed by the CPU.
   b) Java source code is compiled into platform-specific machine code by the Java compiler.
   c) Java source code is compiled into assembly code, which is then executed by the CPU.
   d) Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM).

4. **What type of variable should be used to store data that is important throughout an object's lifespan?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 14]**
   (a) A reference variable
   (b) A method variable
   (c) An instance variable
   (d) A parameter variable

5. **A collection of objects that use common structure and a common behavior is knownas-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Object
   (b) Entity
   (c) Instance
   (d) Class

6. **The following method, which is intended to find the maximum element of the parameter array, is incorrect.** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

7. **Read the following statement in a Java program that compiles and executes-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
   **submarine.dive (depth); What can you say for sure?**
   (a) depth must be an int
   (b) dive must be the name of an instance field
   (c) dive must be a method
   (d) submarine must be the name of a class

8. **What is the output of this Java program?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 154]**
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

9. **Interfaces in Java are meant to be-** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) Extended
   b) Implemented
   c) Overridden
   d) Used by creating object

10. **What is the result of compiling and running the following code?** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
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

11. **What are the inbuit classes?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 35]**
   **Ans:** Predefined Method

12. **What is syntax for call static method in class?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** class name, Method name

13. **What does runFinalize() do?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** The runFinalization() method is a part of the Runtime class, and its purpose is to trigger the execution of the finalization methods of any objects that are awaiting finalization. Its sentence structure is as follows: public void runFinalization()

14. **Find the correct output: System.out.print('D' + 'E'+ 'F');** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) 137
   b) DEF
   c) 207
   d) DEF

15. **Find the output of the following code:** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   ```java
   int a=15, b=15;
   if((a-100) == (b-a)) System.out.print(b+a) ;
   else System.out.print(b-a) ;
   ```
   a) 100
   b) 200
   c) 0
   d) 3

16. **Java Virtual Machine is-** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) Acts as a full-fledged hypervisor
   (b) Converts bytecodes to Operating System dependent code
   (c) Is known as the Compiler of Java programming language
   (d) Manages system memory and provides a portable execution environment for Java-bases applications

17. **Which of the following is not a method of the Thread class?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. sleep (long msec)
   b. stop()
   c. go()
   d. yield()

18. **Which of the following statements is correct regarding abstract classes?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. An abstract class cannot be extended
   b. A subclass of a non-abstract superclass cannot be abstract
   c. A subclass can override a concreate method in a superclass to declare it abstract
   d. An abstract class cannot be used as a data type

19. **What is the output of this Java program?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
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

20. **Converting a primitive type data into its corresponding wrapper class object instance is called-** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 86]**
   a. Boxing
   b. Wrapping
   c. Instantiation
   d. Auto boxing

21. **Which information is not correct for any constructor of a java class?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) Constructor is not inherited
   b) Constructor has no return type
   c) Constructor can be final
   d) Constructor can be overloaded

22. **What is the output of this Java program?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
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

23. **Which of the following statements is/are true about Inheritance in Java?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   i) Private methods are final
   ii) Protected methods are final
   iii) Private methods cannot be overridden
   iv) Protected members of a class are accessible by inherited classes of another package
   a) i, iii and iv
   b) i and iii only
   c) ii, iii and iv
   d) ii and iv only

24. **Which of the followings can be used in a Java Server Page (JSP) page?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) HTML
   b) AJAX
   c) JSTL
   d) All of the above

25. **Which of the following statements is not true for Java Language?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) The number 1 can be used instead of the keyword ‘true’
   b) Trying to store a fraction value in an ‘int’ datatype causes compile error
   c) Static members of a class can be accessed without creating objects of that class
   d) If not specified otherwise, the initial value of an integer variable is 0

26. **Find the output of following Java code line: System.out.println (math.floor (-7.4)** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) -7
   B) -7.4
   C) -8
   D) -7.2

27. **Which of the following is not an operator in Java?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) instanceof
   B) sizeof
   C) new
   D) All of this

## Encapsulation & Access Modifiers

1. **Which of the following does NOT achieve encapsulation?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) Using private access specifier
   (b) Using classes in object-oriented programming
   (c) Using getter and setter methods
   (d) Using global variables

2. **Which variable violates the principle of ecvapsulation?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Gobal variable

3. **Which of the following is a technique for hiding the internal implementation details of an object?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Encapsulation
   b) Polymorphism
   c) Inheritance
   d) All of the above

4. **What is the characteristic of OOP programming that allows binding data and methods to work as a unit?** **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. Inheritance
   b. Encapsulation
   c. Polymorphism
   d. Projection

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** **(Bangladesh Bank Data Entry Operator (IT) Exam: 2020) [compact it 189]**

## Polymorphism & Overloading

1. **Which of the following operators should be preferred to overload as a global function rather than a member method?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xxii]**
   (a) Postfix ++
   (b) Comparison Operator
   (c) Insertion Operator <<
   (d) Prefix++

2. **Which of the following operators cannot be overloaded in C/C++ ?** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
   (a) Bitwise right shift assignment
   (b) Address of
   (c) Indirection
   (d) Structure reference

3. **A feature of Object oriented programming languages that allows a specific routine to use variables of different types at different times, is called OOP?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Polymorphism

4. **A function having more than one distinct meaning is called ______ function** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Parameter
   (খ) Prototype
   (গ) Overloaded
   (ঘ) Polymorphism

5. **The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is-** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
   a. Inheritance
   b. Polymorphism
   c. Over functioning
   d. Overriding

6. **The most common use of ________ in OOP occurs when a parent class reference is used to refer to a child class object.** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 174]**
   a) Polymorphism
   b) Inheritance
   d) Encapsulation
   d) Method overriding

7. **Which of the following is the destructor of class Vehicle?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 207]**
   A) *Vehicle()
   B) ~Vehicle ()
   C) ~Vehicle (int value)
   D) *Vehicle (int value)

8. **The operator that cannot be overloaded is ________.** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 207]**
   A) ++
   B) ()
   C) ~
   D) ::

9. **Which functions overloads the ">>" operator?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) gt()
   B) more()
   C) ge()
   D) None of this

10. **Which of the following operator functions cannot be global i.e. must be a member function?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) Conversion operator
   B) new
   C) delete
   D) all of these

## OOP Concepts & Principles

1. **Which of the following is not property of the Object Oriented Programming Concept?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Encapsulation
   b) Inheritance
   c) Exception
   d) Abstraction

2. **Which of the following modifiers cannot be applied to a method in C++?** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Protected
   (খ) Private
   (গ) Public
   (ঘ) Abstract

3. **Which is not the feature of JAVA OOP?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
   a) Multiple Inheritance
   b) Multi-level inheritance
   c) Compile time Polymorphism
   d) Runtime Polymorphism

4. **Object Oriented programming এর বৈশিষ্ট্য কোনটি?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 186]**
   A) Polymorphism
   B) Friend function
   C) Structure
   D) Loop

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 189]**
   A) Inheritance
   B) Abstraction
   C) Polymorphism
   D) Overloading

## Inheritance

1. **When a class serves as base class for many derived classes, the situation is called-** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Polymorphism
   b) hierarchical inheritance
   c) Hybrid inheritance
   d) Multipath inheritance

2. **Which language is not support OOP four Inheritance feature?** **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) Smaltalk
   (b) Java
   (c) C
   (d) C++

3. **Which type of members can't accessed in derived classes of a base class?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Private members

## Constructors & Destructors

1. **Which of the following is true regarding a constructor in Object Oriented Programming?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) May consist of a return type
   b) Does not consist of any return type
   c) has some return type
   d) None of the above

## Exception Handling

1. **The statements that allows you to define a block of code to be tested for exceptions while it is being executed.** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Try-cache

2. **The ________ block used to execute a given set of the statement whether the exception is thrown or not.** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) try
   b) tryif
   c) finally
   d) thrown

3. **Java uses a keyword ________ to preface a block of code that is likely to cause an error condition and ‘throw’ an exception.** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) throw
   b) catch
   c) finally
   d) try

4. **Which of the following method(s) not included in InputStream class?** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) available()
   b) reset()
   c) flush()
   d) close()
