## Output Tracing & Recursion

22. Consider the following Java program and determine the integer value printed by the execution of the main() method:
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

Explain the concepts of Inheritance and Polymorphism in Java. Write a Java program to demonstrate method overriding. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]
