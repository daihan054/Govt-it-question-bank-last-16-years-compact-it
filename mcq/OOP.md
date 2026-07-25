# OOP (Java / C++)

**Total Questions: 51** (from last 16 years government job exams)

## Table of Contents

- [Encapsulation (5)](#encapsulation-5)
- [Interface (5)](#interface-5)
- [Class & Object (11)](#class-object-11)
- [Java Specific (6)](#java-specific-6)
- [Inheritance (14)](#inheritance-14)
- [Polymorphism (7)](#polymorphism-7)
- [General (3)](#general-3)

---

## Encapsulation (5)

10. Which of the following does NOT achieve encapsulation? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) Using private access specifier
   (b) Using classes in object-oriented programming
   (c) Using getter and setter methods
   (d) Using global variables

97. The following method, which is intended to find the maximum element of the parameter array, is incorrect. **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

42. Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়? **(Bangladesh Bank Data Entry Operator (IT) Exam: 2020) [compact it 189]**

29. What is default level of inheritance has to be specified in C++? **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 193]**
   (a) Public
   (b) Private
   (c) Protected
   (d) Compile time error

7. Multiple inheritances in Java can be implemented using which of the following? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) Interfaces
   B) Multithreading
   C) Protected methods
   D) Private methods

---

## Interface (5)

9. Which of the following statements about abstract classes and interfaces in Java is correct? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) An abstract class can implement multiple interfaces.
   b) An interface can have concrete methods (methods with a body).
   c) An abstract class cannot have any method implementations.
   d) A class can extend multiple abstract classes.

5. Small computer system interface (SCSI) is pronounced as ________? **(Bangladesh Bank Data Entry Operator (IT) Exam: 2020) [compact it 189]**
   a. Asei
   b. Scuzzy
   c. SCSI
   d. None

30. Issuance of cash through terminal outside bank is an example of- **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 213]**
   A) terminals
   B) interfaces
   C) hardware devices
   D) telecommunication

5. Which layer of OSI determines the interface of the system with the user? **(BREB Assistant Junior Engineer (IT) Exam: 2019) [compact it 218]**
   A) Network
   B) Application
   C) Data-link
   D) Session

13. What type of interface has the fastest data transfer? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 2011) [compact it 270]**
   a. Parallel
   b. Serial
   c. SCSI
   d. IDE

---

## Class & Object (11)

10. Which of the following correctly describes the meaning of "Class", "&&", and "&" in Java? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) Class is a keyword to define a new class; && is a bitwise AND operator; & is a logical AND operator.
   b) Class is used to create objects; && is a bitwise OR operator; & is a logical OR operator.
   c) Class is used to create objects; && is a logical OR operator; & is a bitwise OR operator.
   d) Class is a keyword to define a new class; && is a logical AND operator; & is a bitwise AND operator.

62. In a class definition with 10 methods, to make the class maximally cohesive number ofconnections required among the methods are- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 14]**
   (a) 90
   (b) 100
   (c) 10
   (d) 45

63. What type of variable should be used to store data that is important throughout an object's lifespan? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 14]**
   (a) A reference variable
   (b) A method variable
   (c) An instance variable
   (d) A parameter variable

100. Read the following statement in a Java program that compiles and executes- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
   **submarine.dive (depth); What can you say for sure?**
   (a) depth must be an int
   (b) dive must be the name of an instance field
   (c) dive must be a method
   (d) submarine must be the name of a class

21. A constructor is a special type of- **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 192]**
   (a) Class
   (b) Field
   (c) Method
   (d) Property

39. Which of the following is not an operator in Java? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) instanceof
   B) sizeof
   C) new
   D) All of this

2. Which of the following provides a programmer with the facility of using object of a class inside other classes? **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 209]**
   A) Inheritance
   B) Abstraction
   C) Encapsulation
   D) Composition

39. In java, which one will be used for comprising whether the two String object str1 and str2 are same? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) str1=str2
   B) str1.equalsIgnoreCase(str2)
   C) str1==str2
   D) All of above

6. Which part of a class is invoked when an object is initialized in java? **(Sonali & Janata Bank Assistant Programmer Preliminary Exam: 2018) [compact it 239]**
   A) constructor
   B) fields
   C) methods
   D) class

15. In object Oriented Programming, a property can be accessed from ________ **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 260]**
   A) Anywhere the project
   B) Only from its own class
   C) Parent class
   D) Child class

9. Which one of these lists contains only Java programming language keywords? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
   a. class, if, void, long, int, continue
   b. goto, instanceof, native, finally, default, throws
   c. try, virtual, throw, final, volatile, transient
   d. strictfp, constant, super, implements, do

---

## Java Specific (6)

12. What is Java's machine code? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 7]**
   a) Java source code is directly executed by the CPU.
   b) Java source code is compiled into platform-specific machine code by the Java compiler.
   c) Java source code is compiled into assembly code, which is then executed by the CPU.
   d) Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM).

34. Find the output of following Java code line: System.out.println (math.floor (-7.4) **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) -7
   B) -7.4
   C) -8
   D) -7.2

8. Which component is used to compile, debug and execute in Java program? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) JVM
   B) JDK
   C) JIT
   D) JRE

34. int C=10; System.out.println(C--); gives a output of- **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 224]**
   A) 10
   B) 11
   C) 9
   D) 8

31. What is the value of variable x after the following statement is executed in JavaScript var x2= "3" + "4" ? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 228]**
   A) 34
   B) 7
   C) 0
   D) undefine

4. Which is the correct variable declaration in JavaScript? **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 244]**
   A) var a= {'a', 'b', 'c'};
   B) var a= {'a' 'b' 'c'}
   C) var a= {“a” “b” “c”}
   D) None

---

## Inheritance (14)

2. Which is not the feature of JAVA OOP? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
   a) Multiple Inheritance
   b) Multi-level inheritance
   c) Compile time Polymorphism
   d) Runtime Polymorphism

9. The concept of which Superposition theorem is based on- **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 190]**
   (a) Reciprocity
   (b) duality
   (c) non-linearity
   (d) linearity

12. At absolute zero temperature, a semiconductor behaves as a/an- **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 191]**
   (a) Good conductor
   (b) Superconductor
   (c) Insulator
   (d) Variable resistor

7. In C++, the idea to hiding the details of how something is implemented is known as **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 215]**
   A) inheritance
   B) encapsulation
   C) recursion
   D) polymorphism

6. A derived class inherits attributes from a- **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) Super Class
   B) Sub Class
   C) Inner Class
   D) Upper Class

20. How to access the overridden method of base class from the derived class? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 222]**
   A) Using arrow operator
   B) Using dot operator
   C) Using scope resolution operator
   D) Can't be accessed once overridden

4. Which is not feature of object-oriented programming? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 225]**
   A) inheritance
   B) recursion
   C) encapsulation
   D) abstraction

12. Which of the keywords can be used in a subclass to call the constructor of superclass? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) Extent
   B) Extends
   C) Super
   D) This

22. Which keyword must be used to inherit class in java? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
   A) extends
   B) super
   C) this
   D) extend

24. A class that is inherited in java is called a ________. **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
   A) sub class
   B) super class
   C) state class
   D) implement class

12. Server machine is connected to— **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 245]**
   A) Network
   B) Client
   C) supercomputer
   D) Host

50. Which is not a feature of object-oriented programming? **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 251]**
   A) Inheritance
   B) Encapsulation
   C) Recursion
   B) Abstraction

51. In C++, the idea to hiding the details of how something is implemented is known as- **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 251]**
   A) inheritance
   B) polymorphism
   C) recursion
   D) encapsulation

8. A class that is inherited in java is called a ________. **(Sonali Bank Limited Assistant Programmer Preliminary Exam: 2016) [compact it 252]**
   A) Subclass
   B) Super class
   C) Static class
   D) Implement class

---

## Polymorphism (7)

44. Object Oriented programming এর বৈশিষ্ট্য কোনটি? **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 186]**
   A) Polymorphism
   B) Friend function
   C) Structure
   D) Loop

40. Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়? **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 189]**
   A) Inheritance
   B) Abstraction
   C) Polymorphism
   D) Overloading

38. Object Oriented programming এর বৈশিষ্ট্য কোনটি? **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
   A) Polymorphism
   B) Friend function
   C) Structure
   D) Loop

16. If same message is passed to objects of several different classes and all of those can respond in a different way, what is this feature called? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 221]**
   A) Inheritance
   B) Overloading
   C) Polymorphism
   D) Overriding

17. Does constructor overloading include different return types for constructors to be overloaded? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 221]**
   A) Yes, if return types are different, signature becomes different
   B) Yes, because return types can differentiate two functions
   C) No, return type can't differentiate two functions
   D) No, constructors don't have any return type

27. What is the process of defining two or more methods within the same class that have same name but different parameters declaration? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) Method overriding
   B) Method overloading
   C) Method hiding
   D) Method duplicating

14. Which one of the following is the core property of Object-Oriented Programming? **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 259]**
A) Encapsulation, inheritance
B) Encapsulation, Object
C) polymorphism, overloading
D) Encapsulation, polymorphism and inheritance

---

## General (3)

8. Which of the following statements about the "do while" loop is correct? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 6]**

a) The condition is checked before the loop body is executed for the first time.
b) The loop body is guaranteed to execute at least once.
c) The loop condition must always be false for the loop to execute.
d) The "do while" loop and "while" loop have identical behavior in all cases.

39. Martin Cooper is known for his invention of— **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 12]**
   (a) Digital Camera
   (b) X-ray
   (c) Solar Energy
   (d) Mobile Phone

14. Which one is the loopback address? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 181]**
   a) 255.255.2550
   b) 127.0.0.1
   c) 255.0.0.0
   d) 127.127.127.0

---
