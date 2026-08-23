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

3. **Explain OOP Feature.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

4. **Write a program using any object-oriented language (e.g., C++ / Java / Python) to represent a Bank Account. Your program should include:**
 * **A class BankAccount with data members for account holder's name, account number, and balance.**
 * **Member functions to deposit() money, withdraw() money (ensuring sufficient balance), and display() account details.**
**Demonstrate the concept of encapsulation by keeping data member's private and providing appropriate public methods for accessing and modifying them.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1423]**

5. **(a) Write a C++ program named 'class student' that has three attributes: name, roll, and marks. Use the get method to create two objects. Then, find the student with the highest marks and print that student's name.** **(Cadet College (Combined) - Lecturer ICT Exam: 11.05.2025) [compact it 1444]**

6. **b) What is polymorphism in the context of an object-oriented paradigm? Explain the method of overloading and method of overriding with suitable examples.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1344]**

## C++ OOP Concepts & Friend Functions

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1355]**
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```

## Java Programming & Methods

1. **Write a Java Code which return a value.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**

2. **Write a Java Code....** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**
