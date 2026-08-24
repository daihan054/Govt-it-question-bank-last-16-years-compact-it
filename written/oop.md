## Output Tracing & Recursion

1. Consider the following Java program and determine the integer value printed by the execution of the main() method:
```java
class Test {
    static int x = 5;
    public static int fun(int n) {
        if (n <= 1) {
            return 1;
        }
        x = x + 2;
        return fun(n - 1) + x;
    }

    public static void main(String[] args) {
        System.out.println(fun(3));
    }
}
```
[SO IT 25-07-2026]

## OOP Concepts (Inheritance & Polymorphism)

1. Explain the concepts of Inheritance and Polymorphism in Java. Write a Java program to demonstrate method overriding. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

2. **What is runtime polymorphism and compile time polymorphism? Explain it's with example.** **(IFIC Bank - Officer IT Exam: 2025 (IFIC)) [compact it 1448]**

3. **What is polymorphism?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

4. **What is Polymorphism? Discuss about different types of Polymorphism with example?** **(Combined Bank - Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 296]**

5. **Explain OOP Feature.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

6. **Write a program using any object-oriented language (e.g., C++ / Java / Python) to represent a Bank Account. Your program should include:**
 * **A class BankAccount with data members for account holder's name, account number, and balance.**
 * **Member functions to deposit() money, withdraw() money (ensuring sufficient balance), and display() account details.**
**Demonstrate the concept of encapsulation by keeping data member's private and providing appropriate public methods for accessing and modifying them.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1423]**

7. **b) What is polymorphism in the context of an object-oriented paradigm? Explain the method of overloading and method of overriding with suitable examples.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1344]**

8. **Explain the concept of polymorphism in Object-oriented Programming with example?** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1336]**

9. **Write down the difference between Structure and Class.** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1324]**

10. **Explain how encapsulation and inheritance are advantageous in object oriented programming.** **(Combined 2 Bank (Sonali & Janata) - Officer IT Exam: 04.10.2024 (BIBM)) [compact it 420]**

11. **(খ) Function Overloading উদাহরণসহ ব্যাখ্যা করুন।** **(18th NTRCA - College Lecturer (ICT) Exam: 13.07.2024) [compact it 408]**

## Class Design & Object-Oriented Modeling

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** **(Combined 2 Bank (Sonali & Janata) - Officer IT Exam: 04.10.2024 (BIBM)) [compact it 425]**

## Encapsulation & Access Modifiers

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** **(Bangladesh Oil Gas Mineral Corporation (PetroBangla) - Assistant Manager (CSE/IT) Exam: 31.06.2024 (BUET)) [compact it 1456]**

## C++ OOP Concepts & Friend Functions

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1355]**
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```

2. **(ক) Friend Function কী? উহার সুবিধা অসুবিধাগুলো লিখুন।** **(18th NTRCA - College Lecturer (ICT) Exam: 13.07.2024) [compact it 408]**

## Interfaces & Abstract Classes

1. **Class/Interface implementation of code?** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1329]**

## Java Programming & Methods

1. **Write a Java Code which return a value.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**

2. **Write a Java Code....** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**
