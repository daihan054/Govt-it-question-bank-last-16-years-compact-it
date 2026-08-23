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

## Java Programming & Methods

1. **Write a Java Code which return a value.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**

2. **Write a Java Code....** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**
