# C Programming

**Total Questions: 74**

## Table of Contents

* [Pointer and Memory Addressing (6)](#pointer-and-memory-addressing)
* [Array and String (6)](#array-and-string)
* [Loop and Control Statements (12)](#loop-and-control-statements)
* [Functions and Recursion (8)](#functions-and-recursion)
* [Operators and Data Types (11)](#operators-and-data-types)
* [OOP and Other Languages (31)](#oop-and-other-languages)

## Pointer and Memory Addressing (6)

1. Find Output: **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU))**

```cpp
int fun(int \*p) {
    \*p = \*p + 10;
    return \*p;
}
int main() {
    int x = 5;
    cout << fun(\&x);
    return 0;
}
```

(a) 15
(b) 10
(c) 25
(d) 5
Answer: (a)

2. Determine Output: **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**

```c
void main() {
    struct xx {
        int x=3;
        char name\[] = "hello";
    };
    struct xx \*s = malloc(sizeof(struct xx));
    printf("%d", s->x);
    printf("%s", s->name);
}
```

(a) 3 hello
(b) Compiler Error
(c) Linking error
(d) None of these
Answer: (b)

3. Address stored in the pointer variable is of type \_\_\_\_\_\_ **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) Integer
b) Float
c) Character
d) Double
Answer: a
4. Which of the following pairs of statements are not treated as identical by the compiler? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022)**
(ক) int foo(int \*i); int foo(int i\[])
(খ) a\[i]=5; i\[a]=5;
(গ) char c\[10]; char \*c;
(ঘ) void bar (int) ; void bar (int x);
Answer: (গ)
5. What is the correct output of the following C program statements? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
int array\[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, \*p=array+5;
printf("%d\\n",p\[1]);
```

a. 1
b. 2
c. 3
d. Compile Error
Answer: b

6. Find Output: **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
#include<stdio.h>
struct Testnode{char x, y, z;};
int main() {
    struct Testnode node1 = {'1', '2', 'c'+3};
    struct Testnode \*node2 = \&node1;
    printf("%c, %c", \*((char\*)node2+1),\*((char\*)node2+2));
    return 0;
}
```

a. 0, f
b. 0, c+3
c. '0', 'c+3'
d. '0', 'f'
Answer: a

## Array and String (6)

1. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
int data \[2]\[3]\[2]={0,1,2,3,4,5,6,7,8,9,10,11};
int i=0,j=2, k = 1;
printf("%d\\n", data \[i]\[j]\[k]);
return 0;
}
```

(a) 0
(b) 5
(c) 6
(d) 11
Answer: (b)

2. The following method, which is intended to find the maximum element of the parameter array, is incorrect. **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```java
public int max (int\[] a) {
int max = 0;
for (int i=0; i<a.length;i++) {
if(a\[i]>max) {
max = a\[i];
} }
return max;
}
```

(a) It fails whenever the array a contains a 0.
(b) It fails whenever the array a contains a negative number.
(c) It fails whenever the array a contains only negative numbers.
(d) It fails whenever the first element of the array a is the largest.
Answer: (c)

3. Which of the following correctly accesses the seventh element stored in arr, an array with 100 elements? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**
a) arr\[6]
b) arr\[7]
c) arr{6}
d) arr{7}
Answer: a
4. What is the result of compiling and running the following code? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**

```java
public class Test{
    public static void main(String\[] args) {
        int\[] a = new int\[0];
        System.out.print(a.length);
    }
}
```

(a) 0
(b) Compilation error, arrays cannot be initialized to zero size
(c) None of the above
(d) Compilation error, it is length () not length
Answer: (a)

5. Assuming an int is of 4 bytes, What is the size of “int array\[15]”? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) 15
(খ) 19
(গ) 11
(ঘ) 60
Answer: (ঘ)
6. Which of the following is correct to initialize arrays in C? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. int array = (1, 2, 3, 4, 5)
b. int array = {1, 2, 3, 4, 5}
c. int array() = (1, 2, 3, 4, 5)
d. int array\[5] = {1, 2, 3, 4, 5}
Answer: d

## Loop and Control Statements (12)

1. Find Output: **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU))**

```cpp
int main() {
    int x=3, y=2;
    if (x==3)
        y=2;
    else
        y=3;
    cout<<x<<" "<<y<<endl;
    return 0;
}
```

(a) 3 3
(b) 3 2
(c) 2 3
(d) 3 1
Answer: (b)

2. Which of the following statements about the "do while" loop is correct? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) The condition is checked before the loop body is executed for the first time.
b) The loop body is guaranteed to execute at least once.
c) The loop condition must always be false for the loop to execute.
d) The "do while" loop and "while" loop have identical behavior in all cases.
Answer: b
3. Which for loop has range of similar indexes of 'i' used in for (i = 0; i < n; i++)? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**
(a) for (i= n; i>0; i--)
(b) for (i=n-1; i>0; i--)
(c) for (i = 0; i = 0; i--)
(d) for (i=n-1; i>-1; i--)
Answer: (d)
4. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
double k=0;
for(k=0.0;k<3.0; k++)
printf("muli");
return 0;
}
```

(a) run time error
(b) muli is printed infinitely
(c) muli is printed twice
(d) muli is printed thrice
Answer: (d)

5. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
int i,j, count;
count=0;for (i=0; i<5; i++) {
for(j=0;j<i;j++) {
count++;
}
}
printf("%d", count);
return 0;
}
```

(a) 1
(b) 5
(c) 10
(d) 25
Answer: (c)

6. How many times will loop iterate? **(NPCBL Executive Trainee (Software) Exam: 2023)**
(a) 9
(b) 10
(c) 8
(d) infinite
Answer: b
7. Consider int i=0; Then which of the following is not an infinite loop? **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) for(;;){}
b) while ( ){}
c) while ( ++i<0) { --i;}
d) do {++i; while(--i<=0);
Answer: c
8. What will be the output of the following “C” code fragment? **(NPCBL Executive Trainee (Software) Exam: 2023)**

```c
x=0;
while (x<100)
x+=2;
print(x);
```

a) 99
b) 100
c) 101
d) 98
Answer: b

9. Which keyword is used to skip the rest of a loop and carry on from the top of the loop again? **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) Break
b) resume
c) continue
d) skip
Answer: c
10. What is the output for the following C code segment? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
int i;
if(printf("0")) i = 5;
else i = 3;
printf("%d",i);
```

a. 3
b. 5
c. 03
d. 05
Answer: d

11. Suppose, Y is an integer variable whose value is either 0 or 1. Which of the following is the equivalent of the statement. if(Y==0) Y=1; else Y=0;? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. Y = 1+Y
b. Y = 1-Y
c. Y = Y-1
d. Y = 1%Y
Answer: b
12. What can be used to terminate for(;;)? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: break statement

## Functions and Recursion (8)

1. Which of the following Output of this program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**

```c
#include <stdio.h>
int main() {
    static int i=5;
    if (--i) {
        printf("%d ",i);
        main() ;
    }
}
```

(A) 4 3 2 1
(B) 1 2 3 4
(C) 4 4 4 4
(D) 0 0 0 0
Answer: (A)

2. The number of values a function can return at a time? **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) 1
b) 2
c) 0
d) more than 2
Answer: a
3. Which of the following do not return any value? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) Constructor function
(খ) Friend function
(গ) In line Function
(ঘ) Member Functions
Answer: (ক)
4. In C++, The library function exit() causes an exit from- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) a block of statements
(খ) a loop in which it occurs
(গ) a function in which it occurs
(ঘ) a program in which it occurs
Answer: (ঘ)
5. Consider the function fun (x, y) below. That is the value of fun (4, 3)? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
int fun(int x, int y) {
    if (x == 0)
        return y;
    return fun(x - 1, x + y);
}
```

a. 13
b. 12
c. 9
d. 10
Answer: a

6. What does the following function do? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
int fun(int x, int y) {
    if (y == 0) return 0;
    return (x + fun(x, y-1));
}
```

a. x+y
b. x+x*y
c. x*y
d. xy
Answer: c

7. What does following function do for a given Linked List with first node as head? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```c
void fun1(struct node\* head) {
    if (head == NULL)
        return;
    fun1(head->next);
    printf("%d",head->data);
}
```

a. Prints all nodes of linked lists
b. Prints all nodes of linked list in reverse order
c. Prints alternate nodes of Linked List
d. Prints alternate nodes in reverse order
Answer: b

8. When a function is called more than one time that is called? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: This is known as function reusability or recursion or Idempotence

## Operators and Data Types (11)

1. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
int x=20, y=10, z=5;
printf("%d", x>y>z);
return 0;
}
```

(a) 20
(b) 10
(c) 0
(d) 1
Answer: (c)

2. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
int x = 107;
char y = 'Q';
printf("%c%d",x, y);
return 0;
}
```

(a) 107, Q
(b) k, 81
(c) k, Q
(d) Q, K
Answer: (b)

3. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**

```c
int main() {
int i= 11, j = 3;
printf("%d\\n", i|j);
return 0;
}
```

(a) 11
(b) 12
(c) 13
(d) 14
Answer: (a)

4. What will be the output of this C program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**

```c
#include<stdio.h>
int main() {
    float p=10.5;
    int a=5\*p+5.0;
    printf("%d\\n",a);
    return 0;
}
```

a) 57.500000
b) 57
c) 57.000000
d) The program has errors and will not run.
Answer: b

5. Which of the following is not a storage class specifier in C? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**
(A) auto
(B) register
(C) static
(D) extern
(E) volatile
Answer: (E)
6. In C, static storage class cannot be used with: **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**
(A) Global variabl
(B) Function parameter
(C) Function name
(D) Local variable
Answer: (B)
7. Which of the following storage classes have global visibility in C/C++? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**
(A) Auto
(B) Extern
(C) Static
(D) Register
Answer: (B)
8. Given Output: **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**

```c
#include <stdio.h>
int main() {
    int y = 0;
    int x = (y != 0);
    printf("%d", x);
    return 0;
}
```

(A) 0
(B) 1
(C) A bog negative Number
(D) Compiler Error
Answer: (A)

9. Determine Output: **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**

```c
void main() {
    int i=i++, j=j++, k=k++;
    printf("%d %d %d", i, j, k);
}
```

(a) 1 1 1
(b) 0 0 0
(c) garbage values
(d) Error
Answer: (c)

10. Assume that the size of an integer is 4 bytes, predict the output of following program. **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**

```c
#include <stdio.h>
int main() {
    int i = 12;
    int j = sizeof(i++);
    printf("%d %d", i, j);
    return 0;
}
```

(a) 12 4
(b) 13 4
(c) Compiler Error
(d) 0 4
Answer: (a)

11. Consider the following program fragment in assembly language: **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021)**

```assembly
mov ax, 0h
mov cx, 0A h
doloop:
dac ax
loop doloop
```

What is the value of ax and cx registers after the completion of the do loop?
(a) ax=FFF5 h and cx=0h
(b) ax=FFF6 h and cx=0h
(c) ax=FFF7 h and cx=A h
(d) ax=FFF5 h and cx=0A h
Answer: (b)

## OOP and Other Languages (31)

1. Which of the following does NOT achieve encapsulation? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU))**
(a) Using private access specifier
(b) Using classes in object-oriented programming
(c) Using getter and setter methods
(d) Using global variables
Answer: (d)
2. Which of the following operators should be preferred to overload as a global function rather than a member method? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU))**
(a) Postfix ++
(b) Comparison Operator
(c) Insertion Operator <<
(d) Prefix++
Answer: (c)
3. Which is not a valid variable name in PHP? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) age
b) \_age
c) PersonAge
d) 1age
Answer: d
4. Which of the following statements about abstract classes and interfaces in Java is correct? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) An abstract class can implement multiple interfaces.
b) An interface can have concrete methods (methods with a body).
c) An abstract class cannot have any method implementations.
d) A class can extend multiple abstract classes.
Answer: a
5. Which of the following correctly describes the meaning of "Class", "\&\&", and "\&" in Java? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) Class is a keyword to define a new class; \&\& is a bitwise AND operator; \& is a logical AND operator.
b) Class is used to create objects; \&\& is a bitwise OR operator; \& is a logical OR operator.
c) Class is used to create objects; \&\& is a logical OR operator; \& is a bitwise OR operator.
d) Class is a keyword to define a new class; \&\& is a logical AND operator; \& is a bitwise AND operator.
Answer: d
6. To start Python from the command prompt, use the command \_\_\_\_\_ **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) execute python
b) go python
c) python
d) run python
Answer: c
7. What is Java's machine code? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM))**
a) Java source code is directly executed by the CPU.
b) Java source code is compiled into platform-specific machine code by the Java compiler.
c) Java source code is compiled into assembly code, which is then executed by the CPU.
d) Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM).
Answer: d
8. Read the following statement in a Java program that compiles and executes- **submarine.dive (depth); What can you say for sure?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM))**
(a) depth must be an int
(b) dive must be the name of an instance field
(c) dive must be a method
(d) submarine must be the name of a class
Answer: (c)
9. What is the output of this Java program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**

```java
class Test{
    int i=1;
}
public class main{
    public static void main(String args\[]) {
        Test t;
        System.out.println(t.i);
    }
}
```

a) The program will cause an runtime exception because the variable 'i' was not initialized
b) The program will cause an compile error because the object 't' was not initialized
c) 0
d) A garbage value
Answer: b

10. Interfaces in Java are meant to be- **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**
a) Extended
b) Implemented
c) Overridden
d) Used by creating object
Answer: b
11. Which one is the first high level programming language? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM))**
A) C
B) COBOL
C) FORTRAN
D) C++
Answer: C
12. Which of the following operators cannot be overloaded in C/C++ ? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**
(a) Bitwise right shift assignment
(b) Address of
(c) Indirection
(d) Structure reference
Answer: (d)
13. What is the output of the following code? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM))**

```python
print 9//2
```

&#x20;   (a) 4.5
    (b) 4.0
    (c) 4
    (d) Error
    Answer: (c)


14. Which of the following is not property of the Object Oriented Programming Concept? **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) Encapsulation
b) Inheritance
c) Exception
d) Abstraction
Answer: c
15. When a class serves as base class for many derived classes, the situation is called- **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) Polymorphism
b) hierarchical inheritance
c) Hybrid inheritance
d) Multipath inheritance
Answer: b
16. Which of the following is true regarding a constructor in Object Oriented Programming? **(NPCBL Executive Trainee (Software) Exam: 2023)**
a) May consist of a return type
b) Does not consist of any return type
c) has some return type
d) None of the above
Answer: b
17. A function having more than one distinct meaning is called \_\_\_\_\_\_ function **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) Parameter
(খ) Prototype
(গ) Overloaded
(ঘ) Polymorphism
Answer: (গ)
18. Which of the following modifiers cannot be applied to a method in C++? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) Protected
(খ) Private
(গ) Public
(ঘ) Abstract
Answer: (ঘ)
19. A computer program that converts an entire program into machine language is called a/an: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022)**
(ক) Interpreter
(খ) Converter
(গ) Simulator
(ঘ) Compiler
Answer: (ঘ)
20. Which of the following is correct? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. “X extends Y” is correct if and only if X is a class and Y is an interface
b. “X extends Y” is correct if and only if X is an interface and Y is a class
c. “X extends Y” is correct if X and Y are either both classes or both interfaces
d. “X extends Y” is correct for all combinations of X and Y being classes and/or interfaces
Answer: c
21. Which of the following statements is correct regarding abstract classes? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. An abstract class cannot be extended
b. A subclass of a non-abstract superclass cannot be abstract
c. A subclass can override a concreate method in a superclass to declare it abstract
d. An abstract class cannot be used as a data type
Answer: d
22. The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is- **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. Inheritance
b. Polymorphism
c. Over functioning
d. Overriding
Answer: b
23. What is the output of this Java program? **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**

```java
class Test {
    int i;
}
class Main {
    public static void main(String args\[]) {
        Test t;
        System.out.println(t.i);
    }
}
```

&#x20;   a. 0
    b. A garbage value
    c. compiler error
    d. runtime error
    Answer: c


24. Converting a primitive type data into its corresponding wrapper class object instance is called- **(6 Banks \& Financial Institutions Assistant Programmer Exam: 18.03.2021)**
a. Boxing
b. Wrapping
c. Instantiation
d. Auto boxing
Answer: a
25. What are the inbuit classes? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: Predefined Method
26. The statements that allows you to define a block of code to be tested for exceptions while it is being executed. **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: Try-cache
27. A feature of Object oriented programming languages that allows a specific routine to use variables of different types at different times, is called OOP? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: Polymorphism
28. Which variable violates the principle of ecvapsulation? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: Gobal variable
29. Which type of members can't accessed in derived classes of a base class? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: Private members
30. What is syntax for call static method in class? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: class name, Method name
31. What does runFinalize() do? **(BCC Assistant Programmer Exam: 11.11.2023)**
Answer: The runFinalization() method is a part of the Runtime class, and its purpose is to trigger the execution of the finalization methods of any objects that are awaiting finalization. Its sentence structure is as follows: public void runFinalization()

