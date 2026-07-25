# C Programming

**Total Questions: 39** (from last 16 years government job exams)

## Table of Contents

- [Output Tracing (9)](#output-tracing-9)
- [Structure & Union (4)](#structure-union-4)
- [Data Type & Variable (11)](#data-type-variable-11)
- [Loop & Iteration (1)](#loop-iteration-1)
- [Function & Recursion (3)](#function-recursion-3)
- [Pointer (3)](#pointer-3)
- [Operator & Expression (7)](#operator-expression-7)
- [String (1)](#string-1)

---

## Output Tracing (9)

1. Find Output: **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
```cpp
int fun(int *p) {
    *p = *p + 10;
    return *p;
}
int main() {
    int x = 5;
    cout << fun(&x);
    return 0;
}

```
(a) 15
(b) 10
(c) 25
(d) 5

2. Find Output: **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
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

90. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

91. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

92. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

95. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
```c
int main() {
int data [2][3][2]={0,1,2,3,4,5,6,7,8,9,10,11};
int i=0,j=2, k = 1;
printf("%d\n", data [i][j][k]);
return 0;
}

```
(a) 0
(b) 5
(c) 6
(d) 11

96. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
```c
int main() {
int i= 11, j = 3;
printf("%d\n", i|j);
return 0;
}

```
(a) 11
(b) 12
(c) 13
(d) 14

35. Find output in C- Program: **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
```c
#include<stdio.h>
int main() {
    printf("%c", 100);
    return 0;
}

```
A) 100
B) one hundred
C) d
D) 0

6. What will be output if you compile & and execute following C code? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
```c
void main() {
    const int i=5;
    i++;
    printf("%d", i);
}

```
a. 5
b. 6
c. 0
d. Compiler Error

---

## Structure & Union (4)

87. A collection of objects that use common structure and a common behavior is knownas- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Object
   (b) Entity
   (c) Instance
   (d) Class

33. C programming language এ নিচের কোনটিকে "if" দিয়ে Replace করা যায়? **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) switch
   B) structure
   C) return
   D) for

39. C programming language এ নিচের কোনটিকে “if” দিয়ে Replace করা যায়? **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
   A) switch
   B) structure
   C) return
   D) for

13. Which are the keywords of structured programming? **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 245]**
   A) Keywords
   B) Constant
   C) volatile
   D) Above all

---

## Data Type & Variable (11)

94. What will be the output of the following C code? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

36. What is the minimum value that can be stored accurately in a 32-bit signed integer of C programming language? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 179]**
   a) 0
   b) -2^{31}
   c) -2^{31}-1
   d) -2^{32}

40. Which is the correct output? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
```c
int i = 4;
printf ("%d%d", ++i, i++);
printf ("%d ", i++);

```
a) 5 4 6
b) 5 7 8
c) 6 4 6
d) 4 5 7

38. What is the correct output of the following C program statements? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 186]**
```c
int array[]={6,7,8,9,0,1,2,4,5,6},*p=array+5;
printf("%d\n",p[1]);

```
a) 1
b) 2
c) 3
d) Compile Error

8. C programming এ নিচের কোনটি Invalid variable name? **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 187]**
   A) Average
   B) No#of-students
   C) Xyz
   D) y23z

24. C programming এ নিচের কোনটি Invalid variable name? **(BPSC Assistant Network Engineer Exam: 2019) [compact it 197]**
   A) Average
   B) No#of-students
   C) Xyz
   D) y23z

2. Suppose a C program has floating constant 1.414, what's the best way to convert it as a float data type? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 203]**
   A) (float)1.414
   B) float (1.414)
   C) 1.414f or 1.414F
   D) None of these

25. Consider the following code
```c
#include<stdio.h>
int main (int argc, char *argv[]){
return 0;}

```
What is the maximum length of character array argv in the above code? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 227]**
A) 0
B) 1
C) Undefined
D) -1

33. Which of the following doesn’t require an ‘&’ for the input in scanf ( ) ? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) char name [10];
   B) int name [10];
   C) float name[10];
   D) double name [10];

17. Consider the following code
```c
#include<stdio.h>
int main (int argc, char *argv[]){
return 0;
}

```
What is the maximum length of character array argv in the above code? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
A) 0
B) 1
C) Undefined
D) -1

7. Which of the following is not derived data type in C? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
   a. Function
   b. Pointer
   c. Enumeration
   d. Array

---

## Loop & Iteration (1)

25. What will be the output of this C program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 19]**
```c
#include<stdio.h>

```c
int main() {
    float p=10.5;
    int a=5*p+5.0;
    printf("%d\n",a);
    return 0;
}

```
a) 57.500000
b) 57
c) 57.000000
d) The program has errors and will not run.
 26. What is the output of this Java program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
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
 27. Interfaces in Java are meant to be- **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   a) Extended
   b) Implemented
   c) Overridden
   d) Used by creating object
 28. Which one is the first high level programming language? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   A) C
   B) COBOL
   C) FORTRAN
   D) C++
 29. Which one is the first search engine? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   A) Google
   B) Archie
   C) Alta vista
   D) WAIS
 30. Which of the following sorting algorithms can be used to sort a random linked list with minimum time complexity? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) Insertion Sort
   (B) Quick Sort
   (C) Heap Sort
   (D) Merge Sort
 31. Let P be a singly linked list. Let Q be the pointer to an intermediate node x in the list. What is the worst-case time complexity of the best known algorithm to delete the node Q from the list? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) O(n)
   (B) O(log2 n)
   (C) O(logn)
   (D) O(1)
 32. In a doubly linked list, the number of pointers affected for an insertion operation will be- **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) 5
   (B) 0
   (C) 1
   (D) None of these
 33. The time required to search an element in a linked list of length n is- **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   (A) O (log n)
   (B) O (n)
   (C) O (1)
   (D) O (n^2)
 34. Which operation dose F1 key perform for all types of application? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 20]**
   A) Windows shut down
   B) File open
   C) Help
   D) Save

 35. The minimum number of fields with each node of doubly linked list is **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) 1
   (B) 2
   (C) 3
   (D) 4
 36. IPv6 does not support which of the following addressing modes? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) unicast addressing
   (B) multicast addressing
   (C) broadcast addressing
   (D) anycast addressing
 37. What is IP class and number of sub-networks if the subnet mask is 255.224.0.0? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) Class A, 3
   (B) Class A, 8
   (C) Class B, 3
   (D) Class B, 32
 38. Which of the following Output of this program? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
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
 39. Which of the following is not a storage class specifier in C? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) auto
   (B) register
   (C) static
   (D) extern
   (E) volatile
 40. In C, static storage class cannot be used with: **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) Global variabl
   (B) Function parameter
   (C) Function name
   (D) Local variable
 41. Which of the following storage classes have global visibility in C/C++? **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) Auto
   (B) Extern
   (C) Static
   (D) Register
 42. Given Output: **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
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

1. Which country is known as the 'Rainbow nation'? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) Chaina
   (b) South Korea
   (c) Japan
   (d) South Africa
 2. Which one of the following is related to the services provided by cloud? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) Sourcing
   (b) Ownership
   (c) Reliability
   (d) PaaS
 3. How many steps in waterfall model? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) 5
   (b) 6
   (c) 7
   (d) 8
 4. Which is the third largest economic country? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) United States
   (b) Japan
   (c) Chaina
   (d) Kolkata
 5. Where is data warehousing used? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) Transaction System
   (b) Logical system
   (c) Decision support system
   (d) None
 6. Which of the following protected by copyright ACT? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) Intellectual property
   (b) Original work of authorship
   (c) Software
   (d) All
 7. A basic memory storage element in a digital system is: **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Flip-flop
   (b) Counter
   (c) Multiplexer
   (d) Encoder
 8. What is the use of data cleaning? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) To remove the noisy data
   (b) Transformations to correct the wrong data
   (c) Correct the inconsistencies in data
   (d) All of the above
 9. The greatest negative number which can be stored in computer that has 8-bits work length and use 2's complement arithmetic is ______. **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) -256
   (b) -127
   (c) -255
   (d) -128
 10. 3^{20}+3^{20}+3^{20}=? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) 3^{20}
   (b) 9^{20}
   (c) 9^{60}
   (d) 3^{60}
 11. Who get Balon d'Or cup 2022? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Lionell Messi
   (b) Kylian Mbappe
   (c) Karim Benzema
   (d) Ronaldo
 12. Small logical units where data warehouse hold large amounts of data is known as ______. **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Access layers
   (b) Data marts
   (c) Data storage
   (d) Data miners
 13. Which of the following is an essential process in which the intelligent methods are applied to extract data patterns? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Warehousing
   (b) Data Mining
   (c) Text Mining
   (d) Data Selection
 14. Two resistors R1 and R2 are connected in parallel with R1 < R2. Choose all correct answers below. The total resistance of the combination below is: ______. **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) less than R1
   (b) less than R2
   (c) greater than R2
   (d) greater than 2*R2
 15. What type of computing technology refers to services and applications that typically run on a distributed network through virtualized resources? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Distributed Computing
   (b) Cloud Computing
   (c) Soft Computing
   (d) Parallel Computing
 16. Cloud Computing architecture is a combination of ______. **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Service-oriented architecture and grid computing
   (b) Utility computing and event-driven architecture.
   (c) Service-oriented architecture and event-driven architecture.
   (d) Virtualization and event-driven architecture.

 17. Service that generally focuses on the hardware following which one of the following services models? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) IaaS
   (b) PaaS
   (c) SaaS
   (d) Both A and B
 18. Which of the following pairs is an example of intra-domain routing protocols? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) ALOHA, RIP
   (b) OSPF, RIP
   (c) RIP, FTP
   (d) BGP, SMTP
 19. Which of the following cannot be used as a public IP address? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   a. 17.0.0.1
   b. 168.172.19.34
   c. 172.15.29.63
   d. 192.168.13.18
 20. Which one of the following cloud concepts is related to sharing and pooling the resources? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) Virtualization
   (b) Polymorphism
   (c) Abstraction
   (d) None of the avobe
 21. Which command loads a new version of the Cisco IOS into a router **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   a) copy flash ftp
   b) copy ftp flash
   c) copy flash tftp
   d) copy tftp flash
 22. Which of the following provides the ability to query information from the database and insert tuples into, delete tuples from, and modify tuples in the database? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) DML (Data Manipulation Language)
   (b) DDL (Data Definition Language)
   (c) Query
   (d) Relational Schema
 23. The lead character in the film 'The Bandit Queen' has been played by – **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) Rupa Ganguly
   (b) Seema Biswas
   (c) Pratiba Sinha
   (d) Shabana Azmi
 24. A CPU generates 32-bit virtual addresses. The page size is 4 KB. The processor has a translation look-aside buffer (TLB) which can hold a total of 128 page table entries and is 4-way set associative. The minimum size of the TLB tag is: **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) 11 bits
   (b) 13 bits
   (c) 15 bits
   (d) 20 bits
 25. When a host on network A sends a message to a host on network B, which address does the router look at? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
(a) Port
(b) IP
(c) Physical
(d) Subnet mask
Page fault occurs when (Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 25]
(a) When a requested page is in memory
(b) When a requested page is not in memory
(c) When a page is corrupted
(d) When an exception is thrown

 
 1. The ______ system may manage a high degree of interaction between processes and is very useful for high speed and real-time processing. **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) strongly coupled and loosely cohesive
   (b) loosely coupled and strongly cohesive
   (c) loosely coupled and loosely cohesive
   (d) strongly coupled and strongly cohesive
 2. The time taken by NP-class sorting algorithm is- **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) O (1)
   (b) O (\log n)
   (c) O(n^2)
   (d) O(n)
 3. What is the complexity of Merge sort? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) O(n^2 \log n)
   (b) O(n \log n)
   (c) O(n^2)
   (d) O(n)
 4. Which of the following is not the required condition for a binary search algorithm? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) The list must be sorted
   (b) There should be direct access to the middle element in any sub list
   (c) There must be a mechanism to delete and/or insert elements in the list.
   (d) Number values should only be present
 5. How many address is there 200.10.10.10/20 **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) 4096
   (b) 1024
   (c) 2048
   (d) 1022
 6. Which of the following belongs to the algorithm paradigm? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Minimum & Maximum problem
   (b) Knapsack problem
   (c) Selection problem
   (d) Merge sort
 7. Which is suitable subnet mask for 200 host? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) 255.255.0.200
   (b) 255.255.255.0
   (c) 255.0.0.0
   (d) 255.255.200.0
 8. Which of the following is a non linear data structure? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Array
   (b) Graph
   (c) Queue
   (d) Linked list
 9. Which data structure allows insertion and deletion of elements from both ends? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Deque
   (b) Queue
   (c) Stack
   (d) Linked list
 10. Determine Output: **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
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
 11. Design pattern for hierarchical structure is ______ **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) Structure chart
   (b) DFD
   (c) ERD
   (d) UML
 12. In a completer k-array, every internal node has exactly k children. The number of leaves in such a tree with n internal nodes is- **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
   (a) (n-1)k+1
   (b) nk
   (c) n(k-1)
   (d) n(k-1)+1
 13. World environment day is celebrated on ______ of every year. **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   (a) 5^{\text{th}} June
   (b) 6^{\text{th}} June
   (c) 2^{\text{nd}} June
   (d) 1^{\text{st}} June
 14. The IPv4 is encapsulated to IPv6 which is known as ______. **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   (a) Tunneling
   (b) hashing
   (c) NAT
   (d) Trasversing
 15. Determine Output: **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
```c
void main() {
    struct xx {
        int x=3;
        char name[] = "hello";
    };
    struct xx *s = malloc(sizeof(struct xx));
    printf("%d", s->x);
    printf("%s", s->name);
}

```
(a) 3 hello
(b) Compiler Error
(c) Linking error
(d) None of these
 16. Which of the following correctly accesses the seventh element stored in arr, an array with 100 elements? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   a) arr[6]
   b) arr[7]
   c) arr{6}
   d) arr{7}
 17. What is the result of compiling and running the following code? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
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
 18. Table employee has 10 records. It has a non-NULL SALARY column which is also UNIQUE. The SQL statement: **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
```sql
SELECT COUNT (*) FROM employee
WHERE SALARY > ALL(SELECT SALARY FROM EMPLOYEE);

```
Prints:
(a) 10
(b) 9
(c) 5
(d) 0
 19. If the radius is increased by 100% then by how much will the area of circle be increased? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   (a) 100
   (b) 200
   (c) 300
   (d) 400
 20. When was International Mother Language Day Declaration by UNESCO? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   (a) November, 1999
   (b) February, 2000
   (c) February, 1999
   (d) November, 2000
 21. Access time of the symbolic table will be logarithmic if it is implemented by- **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
   (a) Linear list
   (b) Search tree
   (c) Hash table
   (d) Self organization list
 22. Which one of the following algorithm design techniques is used in finding all pairs of shortest distances in a graph? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
   (a) Dynamic programming
   (b) Backtracking
   (c) Greedy
   (d) Divide and Conquer
 23. Assume that the size of an integer is 4 bytes, predict the output of following program. **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
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
 24. Which of the following operators cannot be overloaded in C/C++ ? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
   (a) Bitwise right shift assignment
   (b) Address of
   (c) Indirection
   (d) Structure reference
 25. What is the output of the following code? **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
```python
print 9//2

```
(a) 4.5
(b) 4.0
(c) 4
(d) Error


 1. Who is the name current China President? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Xi Jinping
   (b) Moon Jae-in
   (c) Yoshihide Suga
   (d) Jiang Zemin
 2. What is the name of capital city of Ukraine? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Kyiv
   (b) Moscow
   (c) Paris
   (d) Helsinki
 3. Which is the name of Sri Lanka currency? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Rufiyaa
   (b) Sri Lankan rupee
   (c) Rupee
   (d) Dollar

 4. Antonym of word ‘Stiff’ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) rigid
   (b) hard
   (c) flexible
   (d) inflexible
 5. DC current invented by ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Edison
   (b) William Stanley Jr
   (c) Michael Faraday
   (d) Westinghouse
 6. Biggest district in Bangladesh ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Dhaka
   (b) Chittagong
   (c) Rangamati
   (d) Mymensingh
 7. Who is the CEO of Tesla company? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Tim Cook
   (b) Elon Musk
   (c) Sundar Pichai
   (d) Mark Zuckerberg
 8. Which located in largest Coal Mine of Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Barapukuria in the Dinajpur
   (b) Sylhet
   (c) Gazipur
   (d) Rajshai
 9. Name of the first Prime Minister of Bangladesh ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Sheikh Mujibur Rahman
   (b) Abu Sayeed Chowdhury
   (c) Tajuddin Ahmad
   (d) Humayun Rashid Choudhury
 10. What is ChatGPT? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   Chatboot
 11. Which year declared Cybersecurity act in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) 2016
   (b) 2018
   (c) 2012
   (d) 2008
 12. I would ______ left the job than **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
 13. What is Smart Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Smart Citizens>Smart Government>Smart Economy>Smart Society
   (b) Smart Citizens>Smart Government>Smart Industry>Smart Society
   (c) Smart Citizens>Smart People>Smart Economy>Smart Society
   (d) Smart Citizens>Smart Government>Smart Economy>Smart Learn

 14. Who is the famous artist in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Zainul Abedin
   (b) Kamrul
   (c) Shabuddin
   (d) Monirul Islam
 15. ECNEC under which ministry? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Ministry of Education
   (b) Health
   (c) Planning
   (d) Foreign
 16. Full meaning of GDP ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Gross Domestic Product
   (b) Gross Development Product
   (c) Goal Domestic Product
   (d) Great Domestic Product
 17. Who is not space Agency? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) JAXA
   (b) SPACE
   (c) CSA
   (d) Roscosmos
 18. The Summer Olympic 2024 held on ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Paris
   (b) Los Angeles
   (c) Rio de Janeiro
   (d) Brisbane
 19. Three connecting point name of padma bridge of Bangladesh. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   Louhajang Upazila of Munshiganj and Zazira Upazila of Shariatpur and a small part of Shibchar Upazila of Madaripur
 20. How many sector liberation war in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) 10
   (b) 11
   (c) 7
   (d) 9
 21. Which is the correct spelling? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Extraterrestrial
   (b) extraterrestrial
   (c) Extraterastrial
   (d) extratarrestrial
 22. Prima facie ______ means. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Primal face
   (b) Primitive man
   (c) Main facilities
   (d) At first sight
 23. Indicate the correct sentence ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) An ant is the intelligent insect
   (b) The ant is an intelligent insect
   (c) A ant is the intelligent insect
   (d) An ant is a intelligent insect
 24. Put appropriate preposition for the sentence below:- Some writer sink ______ oblivion in course of time. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) on
   (b) from
   (c) under
   (d) into
 25. He said to me, “Do read the holy Quran daily.” **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) He asked to me to read the holy Quran daily.
   (b) He asked me to read the holy Quran daily.
   (c) He asked me to do read the holy Quran daily.
   (d) He requested me to read the holy Quran daily.
 26. কোনদিন কর্মহীন পূর্ণ অবকাশে বসন্ত বাতাসে অতীতে র তীর হতে যে রাত্রে বহিবে দীর্ঘশ্বাস, করা বকুলের কান্না ব্যথিবে আকাশ। উপরিউক্ত চরণের রচয়িতা কে? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) শামসুর রহমান
   (b) রবীন্দ্রনাথ ঠাকুর
   (c) কাজী নজরুল ইসলাম
   (d) কোনটিই নয়
 27. What's was the central place of recent Egyptian Protest? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   (a) Azadi Square
   (b) Tahrir Square
   (c) Taqdeer Square
   (d) Central square
 28. BPDB look ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** some young and energetic engineer
 29. The blow off some steam means ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** to make angry or excited
 30. সমাস ভাষাকে কি করে? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** সংক্ষেপন করে।
 31. নিচের কোন বানানটি সঠিক? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** জিগীষা
 32. শশাঙ্ক শব্দের প্রতিশব্দ- **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** সুধাংশু
 33. তিন বিঘা করিডোর কোথায় অবস্থিত? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** লালমনিরহাট
 34. যখন পড়বে না মোর পায়ের চিহ্ন। বাক্যে নিম্নরেখ শব্দটি কোন কারকে কোন বিভক্তি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** করণ কারকে ষষ্ঠী
 35. রেস্তোরা কোন ভাষার শব্দ? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** ফরাসি ভাষার শব্দ
 36. মুখরা রমণী বশীকরণ মুনির চৌধুরীর কি ধরনের লেখা? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** অনুবাদ নাটক
 37. রক্তাক্ত প্রান্তর এর বিষয়বস্তু কি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** পানিপথের তৃতীয় যুদ্ধ
 38. হ্ম কোন কোন বর্ণের সমন্বয়ে তৈরি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** হ্ + ম
 39. তুরস্ক ও সিরিয়ায় ভূমিকম্পের মাত্রা কত? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** ৭.৮
 40. নিচের কোনটি সরল বাক্য? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**

 1. Who is the name current China President? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Xi Jinping
   (b) Moon Jae-in
   (c) Yoshihide Suga
   (d) Jiang Zemin
 2. What is the name of capital city of Ukraine? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Kyiv
   (b) Moscow
   (c) Paris
   (d) Helsinki
 3. Which is the name of Sri Lanka currency? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 28]**
   (a) Rufiyaa
   (b) Sri Lankan rupee
   (c) Rupee
   (d) Dollar

 4. Antonym of word ‘Stiff’ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) rigid
   (b) hard
   (c) flexible
   (d) inflexible
 5. DC current invented by ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Edison
   (b) William Stanley Jr
   (c) Michael Faraday
   (d) Westinghouse
 6. Biggest district in Bangladesh ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Dhaka
   (b) Chittagong
   (c) Rangamati
   (d) Mymensingh
 7. Who is the CEO of Tesla company? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Tim Cook
   (b) Elon Musk
   (c) Sundar Pichai
   (d) Mark Zuckerberg
 8. Which located in largest Coal Mine of Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Barapukuria in the Dinajpur
   (b) Sylhet
   (c) Gazipur
   (d) Rajshai
 9. Name of the first Prime Minister of Bangladesh ______. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Sheikh Mujibur Rahman
   (b) Abu Sayeed Chowdhury
   (c) Tajuddin Ahmad
   (d) Humayun Rashid Choudhury
 10. What is ChatGPT? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   Chatboot
 11. Which year declared Cybersecurity act in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) 2016
   (b) 2018
   (c) 2012
   (d) 2008
 12. I would ______ left the job than **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
 13. What is Smart Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 29]**
   (a) Smart Citizens>Smart Government>Smart Economy>Smart Society
   (b) Smart Citizens>Smart Government>Smart Industry>Smart Society
   (c) Smart Citizens>Smart People>Smart Economy>Smart Society
   (d) Smart Citizens>Smart Government>Smart Economy>Smart Learn

 14. Who is the famous artist in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Zainul Abedin
   (b) Kamrul
   (c) Shabuddin
   (d) Monirul Islam
 15. ECNEC under which ministry? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Ministry of Education
   (b) Health
   (c) Planning
   (d) Foreign
 16. Full meaning of GDP ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Gross Domestic Product
   (b) Gross Development Product
   (c) Goal Domestic Product
   (d) Great Domestic Product
 17. Who is not space Agency? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) JAXA
   (b) SPACE
   (c) CSA
   (d) Roscosmos
 18. The Summer Olympic 2024 held on ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Paris
   (b) Los Angeles
   (c) Rio de Janeiro
   (d) Brisbane
 19. Three connecting point name of padma bridge of Bangladesh. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   Louhajang Upazila of Munshiganj and Zazira Upazila of Shariatpur and a small part of Shibchar Upazila of Madaripur
 20. How many sector liberation war in Bangladesh? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) 10
   (b) 11
   (c) 7
   (d) 9
 21. Which is the correct spelling? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Extraterrestrial
   (b) extraterrestrial
   (c) Extraterastrial
   (d) extratarrestrial
 22. Prima facie ______ means. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) Primal face
   (b) Primitive man
   (c) Main facilities
   (d) At first sight
 23. Indicate the correct sentence ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) An ant is the intelligent insect
   (b) The ant is an intelligent insect
   (c) A ant is the intelligent insect
   (d) An ant is a intelligent insect
 24. Put appropriate preposition for the sentence below:- Some writer sink ______ oblivion in course of time. **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) on
   (b) from
   (c) under
   (d) into
 25. He said to me, “Do read the holy Quran daily.” **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) He asked to me to read the holy Quran daily.
   (b) He asked me to read the holy Quran daily.
   (c) He asked me to do read the holy Quran daily.
   (d) He requested me to read the holy Quran daily.
 26. কোনদিন কর্মহীন পূর্ণ অবকাশে বসন্ত বাতাসে অতীতে র তীর হতে যে রাত্রে বহিবে দীর্ঘশ্বাস, করা বকুলের কান্না ব্যথিবে আকাশ। উপরিউক্ত চরণের রচয়িতা কে? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 30]**
   (a) শামসুর রহমান
   (b) রবীন্দ্রনাথ ঠাকুর
   (c) কাজী নজরুল ইসলাম
   (d) কোনটিই নয়
 27. What's was the central place of recent Egyptian Protest? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   (a) Azadi Square
   (b) Tahrir Square
   (c) Taqdeer Square
   (d) Central square
 28. BPDB look ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** some young and energetic engineer
 29. The blow off some steam means ______ **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** to make angry or excited
 30. সমাস ভাষাকে কি করে? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** সংক্ষেপন করে।
 31. নিচের কোন বানানটি সঠিক? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** জিগীষা
 32. শশাঙ্ক শব্দের প্রতিশব্দ- **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** সুধাংশু
 33. তিন বিঘা করিডোর কোথায় অবস্থিত? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** লালমনিরহাট
 34. যখন পড়বে না মোর পায়ের চিহ্ন। বাক্যে নিম্নরেখ শব্দটি কোন কারকে কোন বিভক্তি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** করণ কারকে ষষ্ঠী
 35. রেস্তোরা কোন ভাষার শব্দ? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** ফরাসি ভাষার শব্দ
 36. মুখরা রমণী বশীকরণ মুনির চৌধুরীর কি ধরনের লেখা? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** অনুবাদ নাটক
 37. রক্তাক্ত প্রান্তর এর বিষয়বস্তু কি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** পানিপথের তৃতীয় যুদ্ধ
 38. হ্ম কোন কোন বর্ণের সমন্বয়ে তৈরি? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** হ্ + ম
 39. তুরস্ক ও সিরিয়ায় ভূমিকম্পের মাত্রা কত? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
   **Ans:** ৭.৮
 40. নিচের কোনটি সরল বাক্য? **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 31]**
 1. How many bits of IPv6 address? **(BREB Assistant Programmer Exam: 2023) [compact it 31]**
   (a) 128
   (b) 32
   (c) 12
   (d) 48
 2. Which one is Private IP address? **(BREB Assistant Programmer Exam: 2023) [compact it 31]**
   (a) 192.168.10.10
   (b) 11.15.10.10
   (c) 1.1.1.1
   (d) 172.16.5.3
 3. Which device converts digital to analog signal? **(BREB Assistant Programmer Exam: 2023) [compact it 31]**
   (a) Router
   (b) Switch
   (c) Modem
   (d) Hub
 4. Which algorithm used in memorization? **(BREB Assistant Programmer Exam: 2023) [compact it 31]**
   (a) Dynamic Programming
   (b) Backtraking
   (c) Static Programming
   (d) Xtreme Programming
 5. Which protocol in data encryption of Network level? **(BREB Assistant Programmer Exam: 2023) [compact it 31]**
   (a) HTTPs
   (b) DNS
   (c) SMTP
   (d) FTP

 6. What does a block in a Blockchain? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) A blockchain is a centralized digital ledger consisting of records called blocks
   (b) A blockchain is a decentralized, distributed, digital ledger consisting of records called blocks
   (c) A blockchain is a centralized digital ledger consisting of records called blocks
   (d) None of the above
 7. Which is the correct Addition formula in MS Excel? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) sum(C9:C12)
   (b) = sum(C9:C12)
   (c) sum=(C9:C12)
   (d) sum(C9+C12)
 8. Which of the following sort algorithms has execution time that is least dependent on initial ordering of the input? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) Merge Sort
   (b) Insertion Sort
   (c) Selection Sort
   (d) Quick Sort
 9. Full meaning of CRC is- **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) Cyclic Redundancy Check
   (b) Cyclic Redundant Check
   (c) Cyclic Redundancy Cycle
   (d) Cyclic Redundancy Club
 10. Universal logic gate is: **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) NAND, XOR
   (b) NOR, XOR
   (c) NOR, OR
   (d) NAND, NOR
 11. Which language uses in AI? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) Prolog
   (b) Python
   (c) Java
   (d) C
 12. Hadoop written in which language? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) Java
   (b) C++
   (c) Pascal
   (d) Kotlin
 13. What is the port address of Oracle Database? **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) 1520
   (b) 1521
   (c) 1522
   (d) 1523
 14. (1111111101)_2 = (?)_{10} **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) 1511
   (b) 1510
   (c) 1500
   (d) 1537
 15. Find out 2's complement value of 11100101. **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
(a) 00011011
(b) 00011111
(c) 0011001
(d) 00011010
 16. What is the port address of FTP protocol? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) 21
   (b) 23
   (c) 80
   (d) 25
 17. (2023)_{10} = (?)_{16} **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) 7E0
   (b) 7D0
   (c) 8E0
   (d) 7E7
 18. Which language is not support OOP four Inheritance feature? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) Smaltalk
   (b) Java
   (c) C
   (d) C++
 19. Which is the noun form of ‘Waste’? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) Waste
   (b) Wasting
   (c) Wastage
   (d) Wasteful
 20. Which is the Verb form of ‘Short’? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   (a) Short
   (b) Shorten
   (c) enshort
   (d) Shortage
 21. বাগাড়ম্বর শব্দের সন্ধি বিচ্ছেদ করুন- **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** বাক্ + আড়ম্বর
 22. অনুরোধ এর বিপরীত শব্দ কোনটি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** অনুরোধ
 23. ৪ টাকায় ৫ টি করে কিনে ৫ টাকায় ৪ টি করে বিক্রি করলে শতকরা কত লাভ হবে? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ৫৬.২৫%
 24. ঠাকুরমার ঝুলি রবীন্দ্রনাথের কোন ধরনের রচনা? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** রূপকথা
 25. বাংলা একাডেমি প্রতিষ্ঠা হয় কবে? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ১৯৫৫
 26. স্বাধীন বাংলাদেশের পতাকা প্রথম উত্তোলিত হয়েছিল ১৯৭১ সালের- **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ২ মার্চ
 27. চন্দ্রদ্বীপ অঞ্চলের পূর্বনাম কি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** বরিশাল
 28. কোন রংগুলিকে মৌলিক রং বলা হয়? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** লাল, নীল, হলুদ
 29. আত্মঘাতী বাঙালি কার রচিত গ্রন্থ? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** নীরদ চন্দ্র চৌধুরী
 30. যে সর্বোচ্চ শ্রুতি সীমার উপরে মানুষ বধির হতে পারে তা হচ্ছে- **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ১০৫ ডিবি
 31. সমুদ্র স্রোত সৃষ্টির প্রধান কারণ কি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
 32. ৬০ থেকে ৮০ এর মধ্যে বৃহত্তর ও ক্ষুদ্রতম মৌলিক সংখ্যার অন্তর কত? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ১৮
 33. একটি ৪৮ মিটার লম্বা খুঁটি ভেঙ্গে সম্পূর্ণভাবে বিচ্ছিন্ন না হয়ে ভূমির সাথে 30^\circ কোন উৎপন্ন করে। খুঁটিটি কত উচুতে ভেঙ্গে ছিল? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ১৬
 34. কাজী নজরুল ইসলাম সম্পাদিত সাহিত্য পত্রিকা কোনটি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ধূমকেতু
 35. ইসলামি সংস্থা ওআইসি এর সদর দপ্তর কোথায়? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** জেদ্দায়
 36. জনৈক এর সন্ধি বিচ্ছেদ কোনটি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** জন+এক
 37. বাংলা সাহিত্যের প্রথম মুসলিম কবি কে? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** শাহ মুহম্মদ সগীর
 38. পারস্য উপসাগরের আঞ্চলিক জোটের নাম কি? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** জিসিসি
 39. কোন শব্দটি ইংরেজি ভাষা হতে আগত- **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** এজেন্ট
 40. চাচা কাহিনীর লেখক কে? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** সৈয়দ মুজতবা আলী
 41. ট্রাফালগার স্কয়ার কোথায় অবস্থিত? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** লন্ডন
 42. কি-বোর্ডের Del বাটন চাপলে কি হয়? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** কার্সরের পরের শব্দ মুছে যায়।
 43. যদি তেলের মূল্য ২৫% বৃদ্ধি পায় তবে তেলের ব্যবহার শতকরা কত কমালে তেল বাবদ খরচ বৃদ্ধি পাবে না? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** ২০%
 44. x+y = 7, xy = 10, (x-y)^2 এর মান কত? **(BREB Assistant Programmer Exam: 2023) [compact it 33]**
   **Ans:** 9

## BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)
 1. হরপ্পা মহেনজোদারো কোন সভ্যতার অন্তর্ভুক্ত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) রোমান
   (খ) সিন্ধু
   (গ) গ্রিক
   (ঘ) আফগানিস্তান
 2. গণপ্রজাতন্ত্রী বাংলাদেশের সংবিধান দিবস কত তারিখ? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) ৪ নভেম্বর
   (খ) ৮ অক্টোবর
   (গ) ৪ ডিসেম্বর
   (ঘ) ৪ জানুয়ারী
 3. The word ‘Imbibe’ means- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (a) to learn
   (b) to cry
   (c) to drink
   (d) to acquire
 4. বাংলাদেশ সুগারক্রপ গবেষণা ইনস্টিটিউট কোথায় অবস্থিত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) গাজীপুর
   (খ) পাবনা
   (গ) ময়মনসিংহ
   (ঘ) রাজশাহী
 5. কোন পরিবাহীর তারের ব্যাস দ্বিগুণ এবং দৈর্ঘ্য চারগুণ করা হলে উহার রোধ কত হবে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) অর্ধেক
   (খ) দ্বিগুণ
   (গ) চারগুণ
   (ঘ) একই থাকবে
 6. একটি সুষম সাইন তরঙ্গের পিক-টু-পিক ভোল্টেজ ২০ ভোল্ট হলে- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) তরঙ্গটির গড়মান ১০ ভোল্ট
   (খ) তরঙ্গটির গড়মান ৭.০৭ ভোল্ট
   (গ) তরঙ্গটির আর.এম.এস মান ৬.৩৭ ভোল্ট
   (ঘ) তরঙ্গটির আর.এম.এস মান ১৪.১৪ ভোল্ট
 7. নন-ইনভারটিং অপারেশনাল অ্যাম্প্লিফায়ারের ইনপুট রেজিস্টেন্স ১০ কিলো ওহম এবং ফিডব্যাক রেজিস্টেন্স ২০ কিলো ওহম হলে ক্লোজড-লুপ গেইন কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) ১
   (খ) ২
   (গ) ৩
   (ঘ) ৪
 8. ১ পিকো ফ্যারাডে = কত ফ্যারাডে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) 10^{-9}
   (খ) 10^{-10}
   (গ) 10^{-11}
   (ঘ) 10^{-12}
 9. পাইজোইলেকট্রিক ইফেক্টও কারণ কি? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) ক্রিস্টাল উপর ম্যাগনেটিক ফিল্ডের প্রভাব
   (খ) দুটি ক্রিস্টালের সংযোগস্থলে তাপ প্রভাব
   (গ) ক্রিস্টালের উপর চাপ প্রয়োগ
   (ঘ) ক্রিস্টালের সাথে ভেজাল মিশ্রণ
 10. অ্যাম্প্লিচিউড মডুলেশনে কি ঘটে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) সিগন্যালের অ্যাম্প্লিচিউড পরিবর্তিত হয়
   (খ) সিগন্যালের ফ্রিকুয়েন্সি পরিবর্তিত হয়
   (গ) ক্যারিয়ার অ্যাম্প্লিচিউড পরিবর্তিত হয়
   (ঘ) ক্যারিয়ার ফ্রিকুয়েন্সি পরিবর্তিত হয়
 11. নিম্নের কোন লজিক অপারেশনটি সঠিক? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) A+A = 1
   (খ) AA = 0
   (গ) A+1 = 1
   (ঘ) A+1 = 0
 12. বিসিডি কোডে বিট সংখ্যা কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) 1
   (খ) 2
   (গ) 8
   (ঘ) 4
 13. বাইনারি পদ্ধতির যোগে 1+1+1 = কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) 10
   (খ) 11
   (গ) 101
   (ঘ) 111
 14. একটি তরঙ্গের পিরিয়ড ১০ মিলি সেকেন্ড হলে এটির ফ্রিকুয়েন্সি কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) ১০ হার্টজ
   (খ) ২০ হার্টজ
   (গ) ৫০ হার্টজ
   (ঘ) ১০০ হার্টজ
 15. ইন্ডাক্টরের ইন্ডাক্টেন্স নিম্নের কোনটির উপর নির্ভর করে না? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) ব্যবহৃত কোরের প্রস্থচ্ছেদের ক্ষেত্রফল
   (খ) ব্যবহৃত তারের প্যাচ সংখ্যা
   (গ) ব্যবহৃত তারের পুরুত্ব
   (ঘ) ব্যবহৃত কোরের দৈর্ঘ্য
 16. নিচের কোন সেলটি শুষ্ক কিন্তু পুনরায় চার্জযোগ্য? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 34]**
   (ক) নিকেল-ক্যাডমিয়াম
   (খ) মার্কারি
   (গ) লোড এসিড
   (ঘ) সোলার
 17. একটি ডায়োডে ডিপলেশন লেয়ার কখন তৈরি হয়? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) ফরওয়ার্ড বায়াস করলে
   (খ) রিভার্স বায়াস করলে
   (গ) ডায়োড তৈরির সময়
   (ঘ) তাপমাত্রা বাড়লে
 18. ব্রেকডাউন ঘটলে জিনার ডায়োডের ক্ষেত্রে কোনটি প্রায় অপরিবর্তিত থাকে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) ভোল্টেজ
   (খ) কারেন্ট
   (গ) ইম্পিডেন্স
   (ঘ) ক্যাপাসিটেন্স
 19. ফুল-ওয়েভ রেক্টিফায়ারের কর্মদক্ষতা কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) ৪০.৬%
   (খ) ৮১.২%
   (গ) ৯১.৬%
   (ঘ) ১০০%
 20. বাইপোলার জংশন ট্রানজিস্টরের- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) মাঝের লেয়ারটি সর্বদা N টাইপ
   (খ) ইমিটার লেয়ার সবচেয়ে বেশি প্রশস্ত
   (গ) বেস লেয়ারের ডোপিং ঘনত্ব সবচেয়ে বেশি
   (ঘ) কালেক্টর লেয়ার সবচেয়ে বেশি প্রশস্ত
 21. স্বাধীন বাংলাদেশের জাতীয় সংসদের প্রথম স্পিকার কে ছিলেন? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) আবদুল খালেক উকিল
   (খ) আবদুল হাকিম
   (গ) সাহাবুদ্দিন আহমদ
   (ঘ) মোহাম্মদ উল্লাহ
 22. গ্রিনিচমান সময়ের সঙ্গে বাংলাদেশের সময়ের পার্থক্য কত ঘণ্টা? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) ৪ ঘণ্টা
   (খ) ৬ ঘণ্টা
   (গ) ১০ ঘণ্টা
   (ঘ) ৫ ঘণ্টা
 23. তেভাগা আন্দোলনের নেত্রী? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) ইলা মিত্র
   (খ) তারামন বিবি
   (গ) প্রীতিলতা
   (ঘ) জাহানারা
 24. তেজস্ক্রিয়তার একক কি? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) রনজেন
   (খ) কুরি
   (গ) হেনরি
   (ঘ) রেডিয়াম
 25. VSAT বলতে বুঝায়? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) Virtual Small Aperture Satellite
   (খ) Very Small Aperture Terminal
   (গ) Very Small Application Terminal
   (ঘ) Vertical Satellite
 26. bit এর সংখ্যার বিচারে নিচের কোন ক্রমটি সঠিক? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   (ক) \text{byte}>\text{GB}>\text{KB}>\text{TB}
   (খ) \text{byte}>\text{KB}>\text{GB}>\text{TB}
   (গ) \text{byte}>\text{KB}>\text{TB}>\text{GB}
   (ঘ) \text{byte}>\text{TB}>\text{GB}>\text{KB}
 27. ট্রান্সফরমারের কোন উইন্ডিং এ বেশি প্যাঁচ থাকে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** সেকেন্ডারি উইন্ডিং
 28. নিম্নের কোনটি কমানোর জন্য ট্রান্সফরমারের কোর লেমিনেটিং করা হয়? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** এডি কারেন্ট লস
 29. নিম্নের কোনটি চার লেয়ার বিশিষ্ট ডিভাইস? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** সিলিকন কন্ট্রোল রেক্টিফায়ার
 30. জংশন ফিল্ড ইফেক্ট ট্রানজিস্টর- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** কারেন্ট নিয়ন্ত্রিত
 31. ইমিটার ফলোয়ার ব্যবহারের প্রধান উদ্দেশ্য কি?- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** কারেন্ট গেইন
 32. ঘড়িতে এখন ৪ টা বাজে, ঘণ্টার কাঁটা ও মিনিটের কাঁটার মধ্যকার কোণ কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** ১২০ ডিগ্রি
 33. ইসলামের ইতিহাস ও ঐতিহ্য কোন কাব্যের উপজীব্য? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** সাত সাগরের মাঝি- ফররুখ আহমদ
 34. ট্রানজিস্টরের সার্কিট সঠিকভাবে বায়াসিং করা না হলে- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
   **Ans:** আউটপুট সিগন্যাল বিকৃত হতে পারে
 35. পূর্ণ অভ্যন্তরীণ প্রতিফলন ঘটে যখন আলো- **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
 36. দুইটি সমান্তরাল পরিবাহীকে কোন অপরিবাহী দ্বারা পৃথক করা হলে তাকে কি বলে? **(BDCCL Assistant Manager (Transmission) Exam: 2022 (BUET)) [compact it 35]**
 1. IPv6 is how many bits? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 35]**
   **Ans:** 128 bit
 2. What are the inbuit classes? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 35]**
   **Ans:** Predefined Method
 3. The statements that allows you to define a block of code to be tested for exceptions while it is being executed. **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Try-cache
 4. An optical fiber has a signal solid dielectric cylinder knowns as the core which is surrounded by a solid dielectric ______ is called? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** cladding
 5. What s the axon of neural network do? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** The function of the axon to transmit information to different neurons.
 6. In which layer IPsec works? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Network Layer
 7. What can be used to terminate for(;;)? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** break statement
 8. A feature of Object oriented programming languages that allows a specific routine to use variables of different types at different times, is called OOP? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Polymorphism
 9. Which variable violates the principle of ecvapsulation? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Gobal variable
 10. What is the degree of relation? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** a degree of relationship represents the number of entity types that are associated with a relationship.
 11. What is the popular way to linking many documents? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** hyperlink
 12. Software downloaded from internet and installed that is malicious is called- **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Malware
 13. Which type of members can't accessed in derived classes of a base class? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Private members
 14. What is the minimum node for binary tree? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** For a binary tree, max node = [2^{\text{h}} + 1] and min node = [2\text{h} + 1].
 15. What is syntax for call static method in class? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** class name, Method name
 16. Functional dependency use in which normalizations? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Second Normal Form (2NF)
 17. When a function is called more than one time that is called? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** This is known as function reusability or recursion or Idempotence
 18. Which level of abstraction specifies the data and relationships between data? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Conceptual Level (Logical Level)
 19. What is a distributed ledger on a peer-to-peer network called? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Block Chain
 20. What are hackers who find bugs and vulnerabilities called? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** White hat hacker.
 21. In data structure use recursion? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Stack
 22. What is the D in ACID property in database? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Durability
 23. What is the prefix conversion of the expression \text{A}+(\text{B}-\text{C})*\text{D}? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** +\text{A}*-\text{BCD}
 24. In which way blockchain data can be modifued? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Cannot Modify
 25. What does runFinalize() do? **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** The runFinalization() method is a part of the Runtime class, and its purpose is to trigger the execution of the finalization methods of any objects that are awaiting finalization. Its sentence structure is as follows: public void runFinalization()
 1. When established Bangladesh Rapid Action Battalion (RAB)? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 36]**
   **Ans:** 2004
 2. ‘End in smoke’ means- **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 36]**
   **Ans:** end in nothing
 3. My doctor knew that I would eventually recover and to kind of work ______ before. **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** had been doing
 4. Write is related to reader in the same way as producer is related to ______ **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** Consumer
 5. Nearest meaning of ‘AUGUST’ **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** Dignified
 6. Synonym of ‘EXTRANEOUS’ **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** Irrelevant
 7. Given, x is a real number. What is the minimim value of x^2-4x+5? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** 1
 8. With reference to a 2 dimensional coordinate system, the vertices of a uniform and thin triangular pate are given by (0,0), (1,4) and (-7, 8) points. The centroid of the plate is- **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** (-2, 4)
 9. কাজী নজরুল ইসলামের অগ্নিবীণা কাব্যের প্রথম কবিতা কোনটি? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** প্রলয়োল্লাস
 10. বৃক্ষ শব্দের সমার্থক শব্দ কোনটি? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** বিটপী
 11. হাতকামড়ানো বাগধারাটির অর্থ কি? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** আফসোস করা
 12. এককথায় প্রকাশ করুন: যে ভবিষ্যৎ না ভেবে কাজ করে: **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** অবিমৃষ্যকারী
 13. পুষ্পসৌরভ কোন সমাস? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** তৎপুরুষ সমাস
 14. ন্যাশনাল কংগ্রেস কত সালে গঠিত হয়? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** ১৮৮৫ সালে
 15. যুক্তরাষ্ট্রের নিউইয়র্কে কনসার্ট ফর বাংলাদেশ কে এরেঞ্জ করেন? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** পন্ডিত রবি শংকর
 16. World Trade Organization (WTO)- এর সদর দপ্তর কোথায় অবস্থিত? **(RPGCL Assistant Engineer Exam: 2022 (MIST)) [compact it 37]**
   **Ans:** জেনেভা
1. পেনাং কোন দেশের সমুদ্রবন্দর? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) ইন্দোনেশিয়া
   (b) মালয়েশিয়া
   (c) তাইওয়ান
   (d) ফিলিপাইন
 2. কুতুবদিয়া বাতিঘর নির্মাণ করা হয় কত সালে? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) ১৮৫৫ সালে
   (b) ১৮৪০ সালে
   (c) ১৮৪৬ সালে
   (d) ১৮৪৮ সালে
 3. কমার বিরতিকাল কতক্ষণ? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) ১ বলতে যে সময় লাগে
   (b) ১ বলার দ্বিগুণ সময়
   (c) ১ সেকেন্ড
   (d) থামার প্রয়োজন নেই
 4. সাধু ও চলিত রীতির মিশ্রণে বাক্য কোন দোষে দুষ্ট হয়? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) উৎপ্রেক্ষা দোষে
   (b) বাহুল্য দোষে
   (c) গুরুচণ্ডালী দোষে
   (d) আঞ্চলিক দোষে
 5. বাংলাদেশের একমাত্র পাহাড়ী দ্বীপ কোনটি? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) সেন্ট মার্টিন
   (b) মহেশখালি
   (c) ছেড়াদ্বীপ
   (d) নিঝুম দ্বীপ
 6. তামাবিল সীমান্তের সাথে ভারতের কোন শহরটি অবস্থিত? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) করিমগঞ্জ
   (b) খোয়াই
   (c) পেট্রাপোল
   (d) ডাউকি
 7. দক্ষিণ তালপট্টি কোন নদীর মোহনায় অবস্থিত? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) নাফ
   (b) তেতুলিয়া
   (c) আড়িয়াল খাঁ
   (d) হাঁড়িয়াভাঙ্গা
 8. Which of the following scheduling algorithm is non preemptive? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) Shortest Job First
   (b) FCFS
   (c) Rounf Robin
   (d) Priority Scheduling

 9. How many times will loop iterate? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   (a) 9
   (b) 10
   (c) 8
   (d) infinite
 10. What is the maximum number of possible nonzero values in an adjacency matrix of a simple graph with n vertices? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   (a) n(n-1)/2
   (b) n(n+1)/2
   (c) n(n-1)
   (d) n(n+1)
 11. OPEC থেকে কোন দেশ নিজেকে প্রত্যাহার করে নেয়? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) নাইজেরিয়া
   b) লিবিয়া
   c) ভেনিজুয়েলা
   d) কাতার
 12. A computer system needs to store 100 different symbols. In this case, how many bits of data is required for each symbol? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) 4
   b) 5
   c) 6
   d) 7
 13. Select the correct English translation of: The boy takes after his father. **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) ছেলেটি তার পিতার দেখাশুনা করে
   b) ছেলেটি তার পিতার অনুকরণ করে
   c) ছেলেটি তার পিতার পদাঙ্ক অনুসরণ করে
   d) ছেলেটি দেখতে তার পিতার মত
 14. Which Data structure is needed to convert infix notation to postfix notation? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Branch
   b) Tree
   c) Queue
   d) Stack
 15. What is the maximum number of IP addresses that can be assigned to be the host on a local subnet that uses the 255.255.255.224 subnet mask? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) 16
   b) 32
   b) 31
   d) 30
 16. Logical Memory is broken into blocks of the same size called- **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Frames
   b) Pages
   c) raids
   d) Blocks
 17. Which of the following is not property of the Object Oriented Programming Concept? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Encapsulation
   b) Inheritance
   c) Exception
   d) Abstraction
 18. CREATE TABLE employee (name VARCHAR, id INTEGER). What type of statement is this? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) DML
   b) DDL
   c) View
   d) Integrity constraint
 19. Which data structure is suitable to represent hierarchical relationship between elements? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Stack
   b) Queue
   c) List
   d) Tree
 20. How many children does a binary tree have? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) 2
   b) 0
   c) 0 or 1 or 2
   d) Any number of children
 21. When a class serves as base class for many derived classes, the situation is called- **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Polymorphism
   b) hierarchical inheritance
   c) Hybrid inheritance
   d) Multipath inheritance
 22. What is the number of edges in a complete graph with 5 nodes? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) 1
   b) 4
   c) 5
   d) 10
 23. Communication between a computer and a keyboard involves ______ transmission. **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Automatic
   b) Half-duplex
   c) Full-duplex
   d) Simplex
 24. A B* tree can contain a maximum of 7 pointers in a node. What is the minimum number keys in leaves? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) 6
   b) 3
   c) 4
   d) 7
 25. Which of the following is an example of dynamic programming approach? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) Fibonacci Series
   b) Tower of Hanoi
   c) Dijkstra Shortest Path
   d) None of the above
 26. Which of the following is true regarding a constructor in Object Oriented Programming? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) May consist of a return type
   b) Does not consist of any return type
   c) has some return type
   d) None of the above
 27. The degree of interaction between two modules is known as- **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Cohesion
   b) Strength
   c) Inheritance
   d) Coupling
 28. The number of values a function can return at a time? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) 1
   b) 2
   c) 0
   d) more than 2
 29. What type of join in needed when you wish to include rows that do not have matching values? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Equal join
   b) Natural join
   c) Outer join
   d) Inner join
 30. Find the output of the following prefix expression *+2-2 \text{ } 1/4 \text{ } 2+-531 **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) 2
   b) 12
   c) 10
   d) 4
 31. Which one of the following is the deadlock avoidance algorithm? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) banker’s algorithm
   b) round-robin algorithm
   c) Elevator algorithm
   d) karn’s algorithm
 32. Which one of the followings sorts rows in SQL? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) SORT BY
   b) ALIGN BY
   c) ORDER BY
   d) GROUP BY
 33. Choose the correct spelling **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Query
   b) Quelry
   c) Qeiry
   d) Queery
 34. Consider int i=0; Then which of the following is not an infinite loop? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) for(;;){}
   b) while ( ){}
   c) while ( ++i<0) { --i;}
   d) do {++i; while(--i<=0);
 35. Address stored in the pointer variable is of type ______ **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Integer
   b) Float
   c) Character
   d) Double
 36. What will be the output of the following “C” code fragment? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
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
 37. Which keyword is used to skip the rest of a loop and carry on from the top of the loop again? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Break
   b) resume
   c) continue
   d) skip

 38. Which of the following is not a deadlock handling strategy? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 41]**
   a) Deadlock prevention
   b) Timeout
   c) Deadlock detection and recovery
   d) Deadlock annihilation
 39. A transaction completes its execution is said to be- **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 41]**
   a) Committed
   b) Aborted
   c) Rolled back
   d) Successful
 40. Which of the following sorting algorithms is a divide and conquer algorithm? **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 41]**
   a) merge sort
   b) Bubble sort
   c) Insertion sort
   d) Counting sort
1. Which among the following is the fastest memory in a computer that holds information? **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 41]**
   (a) Register
   (b) Cache
   (c) Main memory
   (d) RAM
 2. Which of the following is temporary storage used to hold data that is used for arithmetic and logical operations and storing its results? **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 41]**
   (a) ALU
   (b) PC (Program counter)
   (c) Accumulator
   (d) IR (Instruction Register)
 3. A hard disk is divided into tracks which are further subdivided into ______ **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 41]**
   (a) Vectors
   (b) Clusters
   (c) Sectors
   (d) None of the above
 4. The Expansion cards are inserted into ______ in a computer. **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 41]**
   (a) Slots of CPU
   (b) Hard Disk of CPU
   (c) Peripheral Devices
   (d) None of above

 5. A system has two IDE hard drives that are each divided into primary and extended partitions, which drive letter is assigned to the primary partition of the second drive? **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 42]**
   (a) C
   (b) D
   (c) E
   (d) F
1. ______ is a type of software testing where a group of individuals, usually from within the organization, use the software in a simulated or controlled environment to uncover defects. **(Pubali Bank Limited, Software Quality Assurance Exam: 18.03.2023) [compact it 42]**
   (a) Alpha Testing
   (b) User Acceptance Testing
   (c) Beta Testing
   (d) Regression Testing
 2. Which of the following testing techniques includes how well the user will understand and interact with the system? **(Pubali Bank Limited, Software Quality Assurance Exam: 18.03.2023) [compact it 42]**
   (a) Alpha Testing
   (b) User Acceptance Testing
   (c) Beta Testing
   (d) Usability Testing
 3. ______ testing is a testing technique where the actual data verified in the real environment. **(Pubali Bank Limited, Software Quality Assurance Exam: 18.03.2023) [compact it 42]**
   (a) Regression Testing
   (b) Alpha Testing
   (c) Beta Testing
   (d) None of the above
 4. Which of the below testing is related to Non-functional testing? **(Pubali Bank Limited, Software Quality Assurance Exam: 18.03.2023) [compact it 42]**
   (a) Unit testing
   (b) Black-box testing
   (c) Performance testing
   (d) None of the above
 5. Which of the following testing is also called Acceptance testing? **(Pubali Bank Limited, Software Quality Assurance Exam: 18.03.2023) [compact it 42]**
   (a) Beta testing
   (b) White-box testing
   (c) Grey box testing tab
   (d) Alpha testing


 1. In an email address "abc@xxx.bd", the portion 'xxx' indicate **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) Domain name
   (খ) TCPAP layer name
   (গ) Domain type
   (ঘ) Protocol name
 2. The use of a high speed circuit breaker- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) reduces the short circuit current
   (খ) increases the short circuit current
   (গ) improves system stability
   (ঘ) decrease system stability
 3. "There must not be any partial dependency "Which of the following Normal Forms holds this condition? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) 1NF
   (খ) 2NF
   (গ) 3NF
   (ঘ) BCNF
 4. Which of the following pairs is an example of transport layer protocols of the OSI model? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) IP, ICMP
   (খ) ARP, IP
   (গ) TCP, IP
   (ঘ) UDP, TCP
 5. How long is an IPv6 address? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) 32 bits
   (খ) 128 bits
   (গ) 64 bits
   (ঘ) 132 bis
 6. Which of the following will not be treated as a cloud service? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 44]**
   (ক) VM rented from open stack based organization
   (খ) A Mobile connecting to weather and map services
   (গ) A LMS service taken from a free service provider
   (ঘ) An web portal hosted for Public Service Commission
 7. Which of the following search algorithm requires less memory? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 44]**
   (ক) Optimal Search
   (খ) Breadth-First Search
   (গ) Depth First Search
   (ঘ) Linear Search
 8. Which of the following pairs is an example of routing protocols? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 44]**
   (ক) ALOHA, SMTP
   (খ) BGP, RIP
   (গ) OSPF, FTP
   (ঘ) FTP, SMTP
 9. Which of the following numbers is the next sequence number of 77_8 in Octal number system? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 44]**
   (ক) 88
   (খ) 80
   (গ) 100
   (ঘ) 99
 10. If we have a very small amount of additional memory, but a large number of items to sort, which of the following sorting algorithm should we use? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 44]**
   (ক) Merge sort
   (খ) Heap sort
   (গ) Bubble sort
   (ঘ) Bogo sort
 11. Which of the following pairs is an example of intra-domain routing protocols? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) ALOHA, RIP
   (খ) OSPF, RIP
   (গ) RIP, FTP
   (ঘ) BGP, SMTP
 12. Which protocol assigns IP address to the client connected in the internet? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) DHCP
   (খ) IP
   (গ) RFC
   (ঘ) WWW
 13. What is the relationship between Paging and Virtual memory? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) Virtual memory came before Paging
   (খ) When pages are created in disks, it is called a virtual memory
   (গ) Virtual memory can never be implemented without paging
   (ঘ) Both have the same concepts
 14. Which of the following statement holds true for the divergence of electric and magnetic flux densities? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) Both are zero
   (খ) These are zero for static flux densities but non-zero for time-varying flux densities
   (গ) It is zero for electric flux densities
   (ঘ) It is zero for magnetic flux densities.
 15. An organization is granted a block; one address is 2.2.2.64/20. The organization needs 10 subnets. What is the subnet prefix length? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) /20
   (খ) /24
   (গ) /23
   (ঘ) /21
 16. Travelling Salesperson Problem is an example of- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) Polynomial time
   (খ) NP Complete
   (গ) NP
   (ঘ) NP-Hard
 17. Which of the following is a private IP address? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) 12.0.0.1
   (খ) 168.172.19.39
   (গ) 172.15.14.36
   (ঘ) 192.168.24.43
 18. What is Artificial Intelligence? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) Making a machine intelligent
   (খ) Putting your intelligence into computer
   (গ) Programming with you own intelligence
   (ঘ) Putting more memory into computer

 19. Which of the following algorithms can not be designed without recursion? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) Fibonacci series
   (খ) Tower of Hanoi
   (গ) None of (ক) and (খ)
   (ঘ) Both (ক) and (খ)
 20. An example of a hierarchical data structure is ______ **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) Array
   (খ) Link list
   (গ) Tree
   (ঘ) Ring
 21. Which of the following data structures follows the LIFO principle? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) stack
   (খ) Linked list
   (গ) Queue
   (ঘ) Graph
 22. In which of the following graphs can we apply topological sort? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) Undirected Cyclic graph
   (খ) Directed Cyclic graph
   (গ) Undirected Acyclic graph
   (ঘ) Directed Acyclic graph
 23. Condition of electricity transmission is- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) high voltage transmission
   (খ) using heavy wire
   (গ) using copper conductor
   (ঘ) using bundled conductor
 24. The speed of a DC shunt motor is required to be more than full load speed. This is possible by- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) reducing the field current
   (খ) decreasing the armature current
   (গ) increasing the armature current
   (ঘ) None of the above
 25. Which of the following is the most commonly used encoding standard of Unicode? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 46]**
   (ক) UTF-6
   (খ) UTF-7
   (গ) UTF-8
   (ঘ) UTF-9
 26. In a step down transformer, there is a change of 15A in the load current. This results in changing of supply current of - **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Less than 15 A
   (খ) Greater than 21 A
   (গ) More than 15 A
   (ঘ) None of the above
 27. The emf generated in a DC generator is directly proportional to- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Flux per pole
   (খ) No. of poles
   (গ) speed of armature
   (ঘ) all of the above
 28. A stack is also called- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Last in First Out
   (খ) First in Last Out
   (গ) Last In Last Out
   (ঘ) First in Frist Out
 29. If a processor has 8-bit register, what is the value of (11111111)_2 represented in 2's complement form- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) 255
   (খ) -1
   (গ) 256
   (ঘ) 0
 30. Which of the following pairs of statements are not treated as identical by the compiler? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) int foo(int *i); int foo(int i[])
   (খ) a[i]=5; i[a]=5;
   (গ) char c[10]; char *c;
   (ঘ) void bar (int) ; void bar (int x);
 31. When a step signal input is applying to an-amp integrator, the output will be- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) A ramp
   (খ) A sinusoidal wave
   (গ) A Rectangular Wave
   (ঘ) A triangular wave with bc bias
 32. Which of the following is not in connection with blockchain technology? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Peer-to-Peer digital currency
   (খ) Centralized social network
   (গ) Peer-to-Peer social network
   (ঘ) Distributed Ledger management
 33. Generally, the gain of a transistor amplifier falls at high frequency due to the **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Internal capacitance of the device
   (খ) coupling capacitor at the input
   (গ) Skin effect
   (ঘ) coupling capacitor at the output
 34. Which mode of memory access is the fastest? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) Reference
   (খ) Pointer
   (গ) Double pointer
   (ঘ) DMA
 35. Impedance and capacitance of a transmission line depend upon- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 47]**
   (ক) current in the line alone
   (খ) voltage in the line alone
   (গ) Both (ক) and (খ)
   (ঘ) Physical configuration of conductors in space
 36. For successful operation of two single phase transformers connected in parallel, the most essential condition is that them **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) Percentage independence are equal
   (খ) Polaritles me properly connected
   (গ) Turns ration are exactly equal
   (ঘ) KVA rating are equal
 37. Which of the following amplifier is used in a digital to analog coverter circuit? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) Non-inverting amplifier
   (খ) Summer circuit
   (গ) Voltage follower circuit
   (ঘ) Difference amplifier circuit
 38. The affected parameter by shunt capacitance are ______ **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) real power
   (খ) reactive power
   (গ) frequency
   (ঘ) all of these
 39. Which of following statements is connected with managed switch? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) It can configure each port differently and make VLAN
   (খ) It can manage traffic like a router
   (গ) It can ensure transport layer security
   (ঘ) None of the above
 40. Alice is one of the tallest girls (make it comparative) **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) Alice is taller than any other girl
   (খ) Alice is taller girl
   (গ) Alice is taller than most other girls
   (ঘ) Alice is taller than rest of the girls
 41. 'Quarterly' শব্দের অর্থ কী? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) সাপ্তাহিক
   (খ) পাক্ষিক
   (গ) মাসিক
   (ঘ) ত্রৈমাসিক
 42. 'দাতা' শব্দের বিপরীত শব্দ কোনটি? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) দাত্রী
   (খ) দানকারী
   (গ) গ্রহীতা
   (ঘ) গৃহীতা
 43. 'A cook and bull story' means — **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) An animal story
   (খ) A comedy
   (গ) A story about birds
   (ঘ) A false story
 44. গ্রিন হাউজ ইফেক্টের পরিপ্রেক্ষিতে বাংলাদেশের সবচেয়ে গুরুতর প্রত্যক্ষ ক্ষতি কী হবে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) বৃষ্টিপাত কমে যাবে
   (খ) সাইক্লোনের প্রবণতা বাড়বে
   (গ) উত্তাপ অনেক বেড়ে যাবে
   (ঘ) নিম্নভূমি নিমজ্জিত হবে
 45. 'ঢাকের কাঠি' বাগধারাটির অর্থ কী? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) ঢাক বাজানোর কাঠি
   (খ) কলুর বলদ
   (গ) মো-সাহেব
   (ঘ) বক-ধার্মিক
 46. Who wrote 'arms and the Man'? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) Ben Johnson
   (খ) T.S. Eliot
   (গ) G.B. Shaw
   (ঘ) Joseph Conrad
 47. 'পদ্মাবতী' কাব্যের রচয়িতা কে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) আলাওল
   (খ) সৈয়দ সুলতান
   (গ) দৌলত উজির বাহরাম খান
   (ঘ) শেখ ফয়জুল্লাহ
 48. বীরশ্রেষ্ঠ ক্যাপ্টেন মহিউদ্দিন জাহাঙ্গীর এর কবর কোন জেলায়? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) নওগাঁ
   (খ) নাটোর
   (গ) জয়পুরহাট
   (ঘ) চাঁপাইনবাবগঞ্জ
 49. 'তত্ত্ববোধিনী' পত্রিকার সম্পাদক কে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) অক্ষয় কুমার দত্ত
   (খ) রবীন্দ্রনাথ ঠাকুর
   (গ) মোজাম্মেল হক
   (ঘ) ঈশ্বরচন্দ্র গুপ্ত
 50. প্লেগ মহামারী/ব্ল্যাক ডেথ শুরু হয় কোথায়? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 48]**
   (ক) স্পেন
   (খ) ফ্রান্স
   (গ) ইতালী
   (ঘ) রাশিয়া
 51. বর্তমান বিশ্বের কোন দেশটির সংবিধানকে "শান্তি সংবিধান" বলা হয়? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) সুইজারল্যান্ড
   (খ) সুইডেন
   (গ) জার্মান
   (ঘ) জাপান
 52. The applied voltage of a certain transformer is increased by 50%, while the frequency is reduced by 50%. The Maximum core flux density will. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) become three times
   (খ) become 1.5 times
   (গ) become half
   (ঘ) remain the same
 53. স্বাধীনতার সুবর্ণজয়ন্তীর লোগোর নকশা করেন কে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) রামেন্দু মজুমদার
   (খ) প্রদীপ চক্রবর্তী
   (গ) সব্যসাচী হাজরা
   (ঘ) ক এবং খ উভয়টি
 54. সঠিক কোনটি? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) চলাকালীন সময়ে
   (খ) চলাকালে
   (গ) চলাকালের সময়ে
   (ঘ) চলাকালিন সময়ে
 55. বিশ্বে প্রথম দেশ হিসেবে করোনা গণটিকা প্রদান কার্যক্রম শুরু করে কোন দেশ? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) যুক্তরাজ্য
   (খ) যুক্তরাষ্ট্র
   (গ) জার্মানী
   (ঘ) ইতালী
 56. Which one is the correct passive form of "He has done a great job?" **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) A great job have been done by him.
   (খ) A great job have been doing by him.
   (গ) A great job has been done by him.
   (ঘ) A great job has been doing by him.
 57. Who wrote "The Solitary Reaper"? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) P.B. Shelley
   (খ) William Wordsworth
   (গ) Alfred Tennyson
   (ঘ) Mathew Arnold
 58. Put the right word in the following gap: Climate is ______ of environment. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) state
   (খ) situation
   (গ) rank
   (ঘ) sire
 59. বাংলাদেশের সর্বাধিক বৈদেশিক মুদ্রা অর্জনকারী শিল্প কোনটি? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) তৈরী পোশাক
   (খ) পাট
   (গ) মাছ
   (ঘ) চা
 60. কোনটি বানানটি শুদ্ধ? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) দ্বন্দ
   (খ) দন্দ
   (গ) দ্বন্দ্ব
   (ঘ) দন্দ্ব
 61. ২০২০-২০২১ অর্থবছরে বাংলাদেশের মাথাপিছু আয় মার্কিন ডলারে কত? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) ২১২৭
   (খ) ২২০৭
   (গ) ২২২৭
   (ঘ) ২০২৭
 62. 'যে উপকারীর অপকার করে' তাকে এক কথায় বলে- **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) অকৃতজ্ঞ
   (খ) কৃতঘ্ন
   (গ) অপকারী
   (ঘ) শত্রুঘ্ন
 63. জনসংখ্যা বৃদ্ধির হার সর্বনিম্ন কোন দেশ? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) বুলগেরিয়া
   (খ) সোমালিয়া
   (গ) লাটভিয়া
   (ঘ) লিথুনিয়া
 64. কাপাসিয়া মডেল কী? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) শিশু শ্রম নিরসন মডেল
   (খ) বাল্য বিবাহ রোধ মডেল
   (গ) মাতৃত্বমৃত্যু কমানোর সফল মডেল
   (ঘ) গৃহকর্মী সুরক্ষা মডেল
 65. 'Put up with' means ______. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) be excited
   (খ) complain
   (গ) hate
   (ঘ) tolerate
 66. এলিসি প্রাসাদ কোন দেশের প্রেসিডেন্টের বাসভবন? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
   (ক) রাশিয়া
   (খ) ফ্রান্স
   (গ) বলিভিয়া
   (ঘ) ব্রাজিল
 67. Swimming is conducive ______ health. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 49]**
(ক) for
(খ) in
(গ) at
(ঘ) to
 68. What is the correct antonym of 'Panic'? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) laugh
   (খ) relaxed
   (গ) sit
   (ঘ) meditate
 69. ওয়াটার লু কোথায় অবস্থিত? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) বেলজিয়াম
   (খ) ইংল্যান্ড
   (গ) ইতালী
   (ঘ) রাশিয়া
 70. The phrase 'an apple of discord' means ______. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) a sour apple
   (খ) and important matter
   (গ) an unexpected gift
   (ঘ) an object of quarrel
 71. He was guilty ______ contempt of court. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) off
   (খ) of
   (গ) for
   (ঘ) against
 72. ‘চর্যাপদ’ আবিষ্কৃত হয় কত সালে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) ১৯০৫ সালে
   (খ) ১৯০৬ সালে
   (গ) ১৯০৭ সালে
   (ঘ) ১৯০৮ সালে
 73. Which is not plural? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) Analysis
   (খ) Flora
   (গ) Seraphim
   (ঘ) Oxen
 74. Every man will fall a ______ to death. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) prey
   (খ) pray
   (গ) victim
   (ঘ) virtual
 75. ভাষার ক্ষুদ্রতম একক কোনটি? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) ধ্বনি
   (খ) শব্দ
   (গ) বর্ণ
   (ঘ) অক্ষর
 76. আল্ট্রাভায়োলেট রশ্মি নিম্নের কোন রোগ সৃষ্টি করে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) এইডস
   (খ) ব্রেন ক্যান্সার
   (গ) ব্লাড ক্যান্সার
   (ঘ) চর্ম ক্যান্সার
 77. রবীন্দ্রনাথ ঠাকুরের ‘শেষের কবিতা’ একটি— **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) উপন্যাস
   (খ) কাব্যগ্রন্থ
   (গ) নাটক
   (ঘ) গল্পগ্রন্থ
 78. ‘প্রাগৈতিহাসিক’ গল্পটি কার রচনা? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) শাহেদ আলী
   (খ) রাজশেখর বসু
   (গ) মানিক বন্দ্যোপাধ্যায়
   (ঘ) হাসান আজিজুল হক
 79. কোনটি ‘খবর’ শব্দের সমার্থক নয়? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) সন্দেশ
   (খ) গুজব
   (গ) বার্তা
   (ঘ) সংবাদ
 80. ‘আনারস’ শব্দটি কোন ভাষা থেকে আগত? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) ওলন্দাজ
   (খ) তুর্কি
   (গ) পর্তুগিজ
   (ঘ) ফারসি
 81. মুক্তিযুদ্ধভিত্তিক উপন্যাস কোনটি? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) আগুনের পরশমণি
   (খ) খোয়াবনামা
   (গ) আরেক ফাল্গুন
   (ঘ) আর্তনাদ
 82. The police were informed ______ the matter. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) of
   (খ) about
   (গ) by
   (ঘ) into
 83. First language means ______ language. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) important
   (খ) main
   (গ) official
   (ঘ) natural
 84. ‘আমার দেখা নয়াচীন’ গ্রন্থের রচয়িতা কে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) জামিল চৌধুরী
   (খ) ড. মুহম্মদ শহীদুল্লাহ
   (গ) আহমদ শরীফ
   (ঘ) শেখ মুজিবুর রহমান
 85. বাংলাদেশে বর্তমানে বিদ্যুৎ উৎপাদন ক্ষমতা কত? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 50]**
   (ক) ৩০ হাজার মেগাওয়াট
   (খ) ২২ হাজার মেগাওয়াট
   (গ) ১০ হাজার মেগাওয়াট
   (ঘ) ৮ হাজার মেগাওয়াট
 86. Choose the correct answer ______ **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) The gold is a precious metal
   (খ) A gold is a precious metal.
   (গ) Gold is a precious metal.
   (ঘ) Gold is precious metal.
 87. বেসরকারি বিল কাকে বলে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) সংসদ সদস্যদের উত্থাপিত বিল
   (খ) রাষ্ট্রপতি কর্তৃক ঘোষিত কোন বিল
   (গ) বিরোধী দলের সদস্যদের উত্থাপিত বিল
   (ঘ) স্পীকার যে বিলকে বেসরকারি বিল বলে ঘোষণা দেন
 88. কোন পাখিকে 'অন্যপুষ্ট' বলা হয়? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) কাক
   (খ) কোকিল
   (গ) কবুতর
   (ঘ) কাকাতুয়া
 89. Would you mind ______ a folk song? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) for
   (খ) singing
   (গ) to sing
   (ঘ) sing
 90. জাপান ও রাশিয়ার মধ্যকার বিরোধপূর্ণ দ্বীপটির নাম কী? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) কুরিল দ্বীপপুঞ্জ
   (খ) গ্রেট বেরিয়ার দ্বীপ
   (গ) মার্শাল দ্বীপ
   (ঘ) দিয়াগো গর্সিয়া দ্বীপ
 91. If I had another pen, I ______ you. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) would have helped you
   (খ) might have helped
   (গ) could help
   (ঘ) should help
 92. ২০২১ সাল থেকে বাংলাদেশ সরকার নতুন কোন পদক প্রদান করে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) বঙ্গবন্ধু আন্তর্জাতিক কৃষি পুরস্কার
   (খ) বঙ্গমাতা বেগম ফজিলাতুন্নেছা মুজিব পুরস্কার
   (গ) শেখ হাসিনা আন্তর্জাতিক শান্তি পুরস্কার
   (ঘ) শেখ রাসেল আইসিটি পুরস্কার
 93. "Impossible is a word to be found in a fools dictionary" উক্তিটি কার? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) Plato
   (খ) Nepoleon
   (গ) Che Guevara
   (ঘ) Einstein
 94. “মেঘদূত” কাব্যটি কার লেখা? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) দ্বিজমাধব
   (খ) বড়ুচণ্ডীদাস
   (গ) চণ্ডী দাস
   (ঘ) কালিদাস
 95. A song expressing grief is called ______ **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) Balled
   (খ) Elegy
   (গ) Hymn
   (ঘ) Dirge
 96. কোলাজেন কী? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) একটি কার্বোহাইড্রেট
   (খ) একটি প্রোটিন
   (গ) একটি লিপিড
   (ঘ) একটি নিউক্লিক এসিড
 97. Survival is a/an ______. **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) noun
   (খ) verb
   (গ) adjective
   (ঘ) adverb
 98. ‘ভোরের পাখি’ কার ছদ্ম নাম? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) রবীন্দ্রনাথ ঠাকুর
   (খ) বিহারীলাল চক্রবর্তী
   (গ) কায়কোবাদ
   (ঘ) সত্যেন্দ্রনাথ দত্ত
 99. ‘পায়ের আওয়াজ পাওয়া যায়’ নাটকটির লেখক কে? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) আব্দুল্লাহ আল মামুন
   (খ) সেলিম আল দিন
   (গ) সৈয়দ শামসুল হক
   (ঘ) মামুনুর রশীদ
 100. কোনটি কাজী নজরুল ইসলামের রচনা? **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 51]**
   (ক) গৃহদাহ
   (খ) মৃত্যুক্ষুধা
   (গ) কাশাবনের কন্যা
   (ঘ) কোয়ারি
1. ‘বঙ্গীয় মুসলমান সাহিত্য সমাজ’ প্রতিষ্ঠিত হয় কত সালে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 51]**
   (ক) ১৯০৭ সালে
   (খ) ১৯০৯ সালে
   (গ) ১৯১১ সালে
   (ঘ) ১৯২১ সালে
 2. In cryptography, RSA is- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) Symmetric key based
   (খ) Block-chain based
   (গ) Asymmetric key based
   (ঘ) None
 3. বাংলা ভাষার ছন্দের যাদুকর কাকে বলা হয়? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) মাইকেল মধুসূদন দত্ত
   (খ) সত্যেন্দ্রনাথ দত্ত
   (গ) কাজী নজরুল ইসলাম
   (ঘ) কবি জসীমউদ্দীন
 4. The total charge entering a terminal is given by q=5t\sin 4\mu t\text{ mC}. What is the current at t=0.5\text{ S}? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) 3.142\text{ mA}
   (খ) 31.42\text{ mA}
   (গ) 28.37\text{ mA}
   (ঘ) 8.34\text{ mA}
 5. রবীন্দ্রনাথের কোন ছোট গল্পটি উপন্যাসের পর্যায়ে পড়ে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) পোস্টমাস্টার
   (খ) খোকাবাবুর প্রত্যাবর্তন
   (গ) ছুটি
   (ঘ) নষ্টনীড়
 6. Choose the right option: ‘The engineer insists on ______ good materials.’ **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) use
   (খ) using
   (গ) to use
   (ঘ) the use
 7. Fill the blank: No Sooner had I reached the station ______ the train left **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) then
   (খ) than
   (গ) before
   (ঘ) after
 8. The transfer function of an LTI system is given as \frac{1}{s+2}. What is the value of its impulse response at t=0? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) 0.0
   (খ) 0.689
   (গ) 1.0
   (ঘ) 1.5
 9. Fill in the blank: ‘Smita was so sound asleep that it was most difficult to ______ her.’ **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) rise
   (খ) arise
   (গ) rouse
   (ঘ) raise
 10. Which one is an embedded operating system? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) UNIX
   (খ) MS windows XP
   (গ) Windows CE
   (ঘ) Windows NET
 11. The antonym of the word copious’ is ______ **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) plenty
   (খ) abundant
   (গ) brave
   (ঘ) scanty
 12. The rating of fuse is expressed as ______ **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) Ampere-hours
   (খ) Ampere-volts
   (গ) KWH
   (ঘ) Ampers
 13. Which of the following file format is not a Video file format? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) AVI
   (খ) MOV
   (গ) MPEG
   (ঘ) JPG
 14. A loss-less transmission line has L=8.5\text{ nH/m} and C=300\text{ pF/m}. What is the characteristic impedance of the line? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) 50\Omega
   (খ) 5.32\Omega
   (গ) 8.92\Omega
   (ঘ) 4.32\Omega
 15. The key selected from the sets of candidate keys by database design is called ______ key: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) Candidate
   (খ) Primary
   (গ) Super
   (ঘ) Foreign
 16. ‘কাঁদো নদী কাঁদো’- এর রচয়িতা কে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) মুনীর চৌধুরী
   (খ) মানিক বন্দ্যোপাধ্যায়
   (গ) শহীদুল্লাহ কায়সার
   (ঘ) সৈয়দ ওয়ালীউল্লাহ
 17. ______ are used to quickly accept, store and transfer data and instructions that are being used immediately by the CPU. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) Graphics
   (খ) RAMs
   (গ) Caches
   (ঘ) Registers
 18. বাংলা সাহিত্যে কখন গদ্যের সূচনা হয়? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) ষোড়শ শতকে
   (খ) নবম শতকে
   (গ) ত্রয়োদশ শতকে
   (ঘ) উনিশ শতকে
 19. Which of the following has no plural form? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) analysis
   (খ) crisis
   (গ) louse
   (ঘ) soap
 20. Which of the following do not return any value? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) Constructor function
   (খ) Friend function
   (গ) In line Function
   (ঘ) Member Functions
 21. The Synonym of the word 'docile' is- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) obedient
   (খ) disobedient
   (গ) hostile
   (ঘ) friendly
 22. For the protection of transformer, harmonic restraint is used to guard against ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) Magnetizing inrush current
   (খ) Unbalanced operation
   (গ) Lightning
   (ঘ) Switching over voltage
 23. A certain amount of water is boiled by inserting a current carrying resistor in water. The heat energy required to boil the water is 99kJ. The current taken by the resistor is 5A at 220V. What is the time required to boil water? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) 120\text{s}
   (খ) 180\text{s}
   (গ) 90\text{s}
   (ঘ) 70\text{s}
 24. 'সূর্য' শব্দের সমার্থক শব্দ কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) বিধু
   (খ) আদিত্য
   (গ) অর্ণব
   (ঘ) অলক
 25. কোন গ্রন্থটি মহাকাব্য? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) অবকাশ রঞ্জিকা
   (খ) বৃত্ত সংহার
   (গ) বিরহ বিলাপ
   (ঘ) বীরাঙ্গনা কাব্য
 26. বাংলাদেশের প্রথম জাতীয় সংসদ নির্বাচন হয় কোন তারিখে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) ৭ মার্চ ১৯৭৩
   (খ) ৮ মার্চ ১৯৭৩
   (গ) ৬ এপ্রিল ১৯৭৩
   (ঘ) ১১ এপ্রিল ১৯৭৩
 27. The logic gate that will have a Low output then any one of its inputs is High is ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) NAND gate
   (খ) AND gate
   (গ) NOR gate
   (ঘ) OR gate
 28. A voltage source supplies a signal of constant amplitude from 0 to 40kHz to a RC filter (low-pass). The load resistor experiences the maximum voltage at ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) 10\text{kHz}
   (খ) 40\text{kHz}
   (গ) 18\text{kHz}
   (ঘ) DC
 29. ভারতের কোন রাজ্য Seven Sisters এর অন্তর্ভুক্ত নয়? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) হিমাচল
   (খ) অরুণাচল
   (গ) নাগাল্যান্ড
   (ঘ) সিকিম
 30. DNS port number is: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) 63
   (খ) 21
   (গ) 53
   (ঘ) 24
 31. A 4-pole 50Hz induction motor running at 1300 rpm. The speed of stator magnetic field with respect to rotor is ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) 1500\text{rpm}
   (খ) 200\text{ rpm}
   (গ) 1300\text{ rpm}
   (ঘ) 300\text{ rpm}
 32. খাদ্য নিরাপত্তার ক্ষেত্রে যে সকল বিষয় বিবেচনা করতে হয়- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) খাদ্যের মূল্য
   (খ) খাদ্যের ক্রয়ক্ষমতা
   (গ) খাদ্যের সহজলভ্যতা
   (ঘ) উপরের তিনটি বিষয়
 33. A function having more than one distinct meaning is called ______ function **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Parameter
   (খ) Prototype
   (গ) Overloaded
   (ঘ) Polymorphism
 34. Which of the following communication medium requires ‘line-of-sight’? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Micro wate
   (খ) Fiber optic cable
   (গ) Twisted-pair cable
   (ঘ) Co-axial cable
 35. CIRDAP এর সদর দপ্তর কোথায় অবস্থিত? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) ব্যাংকক
   (খ) রাওয়ালপিন্ডি
   (গ) ঢাকা
   (ঘ) নয়াদিল্লী
 36. পৃথিবীর ক্ষুদ্রতম মহাদেশ কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) ওশেনিয়া
   (খ) আফ্রিকা
   (গ) উত্তর আমেরিকা
   (ঘ) ইউরোপ
 37. ‘Look before you leap.’ Here, before ‘ is used as a/an — **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) adverb
   (খ) preposition
   (গ) conjunction
   (ঘ) interjection
 38. What is the meaning of the phrase ‘sine die’? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) for a certain period
   (খ) for an uncertain period
   (গ) for a short time
   (ঘ) none
 39. Quick sort algorithm is an example of – **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Greedy approach
   (খ) Improved binary search
   (গ) Dynamic programming
   (ঘ) Divide and conquer
 40. Which one of the following is not a web browser? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Firefox
   (খ) Facebook
   (গ) Chrome
   (ঘ) Safari
 41. সূর্যের আলো পৃথিবীতে আসতে সময় লাগে প্রায়— **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) ১০ মিনিট
   (খ) ৮ মিনিট
   (গ) ১২ মিনিট
   (ঘ) ১৪ মিনিট
 42. Which of the following modifiers cannot be applied to a method in C++? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) Protected
   (খ) Private
   (গ) Public
   (ঘ) Abstract
 43. বাঙালি রচিত বাংলা অক্ষরে মুদ্রিত প্রথম গ্রন্থ কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) মহারাজা কৃষ্ণচন্দ্র চরিত্র
   (খ) বাজাবলি
   (গ) রাজা প্রতাপাদিত্য চরিত্র
   (ঘ) কথোপকথন
 44. ‘The door opened automatically.’ The verb in this sentence is – **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) transitive
   (খ) intransitive
   (গ) linking
   (ঘ) modal
 45. A large building in which aircraft are kept is called – **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 54]**
   (ক) terminal
   (খ) harbour
   (গ) hanger
   (ঘ) hangar
 46. Assuming an int is of 4 bytes, What is the size of “int array[15]”? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) 15
   (খ) 19
   (গ) 11
   (ঘ) 60
 47. To remove a relational table from SQL database, we use ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) Delete
   (খ) Purge
   (গ) Remove
   (ঘ) Drop
 48. 'দুধ থেকে দই হয়'- এখানে 'দুধ থেকে' কোন অর্থে অপাদান কারক? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) জাত
   (খ) আরম্ভ
   (গ) গৃহীত
   (ঘ) রক্ষিত
 49. 'আমার দেখা নয়াচীন' গ্রন্থের লেখক কে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) শেখ মুজিবুর রহমান
   (খ) আনোয়ার পাশা
   (গ) শেখ হাসিনা
   (ঘ) কবির চৌধুরী
 50. Which technology is used in Compact Disk (CD)? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) Mechanical
   (খ) Laser
   (গ) Electrical
   (ঘ) Electro magnetic
 51. ভারতের সাথে বাংলাদেশের সীমানা কত কিলোমিটার? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) ৩৭১৫ কি.মি
   (খ) ২০১৫ কি.মি
   (গ) ৪৫০০ কি.মি
   (ঘ) ৪১০০ কি.মি
 52. Which is the correct article? metre is ______ unit of length. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) an
   (খ) a
   (গ) the
   (ঘ) no article required
 53. প্রতিদিন বাংলাদেশে গড়ে কি পরিমাণ খাদ্যশস্য Consume হয়? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) ২ লক্ষ টন
   (খ) ৫০ লক্ষ টন
   (গ) ১ লক্ষ টন
   (ঘ) ৩ লক্ষ টন
 54. Fill in the blank with appropriate preposition: ‘Don't worry ______ me. i'll be alright. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) to
   (খ) with
   (গ) about
   (ঘ) at
 55. Choose the right determined: ‘You can park on ______ side of the street’. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) both
   (খ) many
   (গ) either
   (ঘ) these
 56. মধ্যযুগের বাংলা সাহিত্যের প্রথম মুসলমান কবি কে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) আলাওল
   (খ) শাহ মুহম্মদ সগীর
   (গ) কায়কোবাদ
   (ঘ) মীর মোশাররফ হোসেন
 57. কম্পট্রোলার এন্ড অডিটর জেনারেল পদটি- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) একটি সরকারি পদ
   (খ) স্বায়ত্তশাসিত পদ
   (গ) সাংবিধানিক পদ
   (ঘ) আধাসরকারি পদ
 58. A nuclear power plant is invariably used as a ______ plant. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) Peak load
   (খ) Base load
   (গ) Standby
   (ঘ) Spinning reserve
 59. Which configuration of Bipolar Junction Transistor is known as voltage follower? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) Common collector
   (খ) Common base
   (গ) Common emitter
   (ঘ) None of them
 60. বঙ্গবন্ধুর ঐতিহাসিক ৭ই মার্চ ভাষণে অ্যাসেম্বলিতে বসার জন্য তৎকালীন সরকারকে কয়টি শর্ত দিয়েছিলেন? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) ৬টি
   (খ) ৪টি
   (গ) ৩টি
   (ঘ) ৮টি
 61. What is the worst case time complexity of linear search algorithm? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) O(1)
   (খ) O(n)
   (গ) O(\log n)
   (ঘ) O(n^2)
 62. Identify the feminine gender. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) peer
   (খ) parent
   (গ) spinster
   (ঘ) boar
 63. A computer has main memory of 960 Kb. What is the exact number of bytes contained in this memory? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) 960x8
   (খ) 960x1000
   (গ) 960x1024
   (ঘ) 960x1024x1024
 64. Time during which a job is processed by the Computer is: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Delay time
   (খ) Real time
   (গ) Execution time
   (ঘ) Process time
 65. মানব উন্নয়ন সূচক (HDI) কোন সংস্থা প্রকাশ করে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) UNDP
   (খ) ILO
   (গ) UNEPA
   (ঘ) ICJ
 66. পৃথিবীর সর্বাপেক্ষা জ্বালানি তেল উৎপাদনকারী দেশ কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) সৌদি আরব
   (খ) যুক্তরাষ্ট্র
   (গ) সংযুক্ত আরব আমিরাত
   (ঘ) ইরান
 67. বাংলা সাহিত্যের প্রাচীনতম শাখা কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) ছোটগল্প
   (খ) কাব্য
   (গ) নাটক
   (ঘ) মহাকাব্য
 68. Two sets are called disjoint if their ______ is an empty set. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Union
   (খ) Difference
   (গ) Intersection
   (ঘ) Complement
 69. Who is controlling "Domain" in the world? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) CCNA
   (খ) WWW3
   (গ) ICANN
   (ঘ) ISDN
 70. গণপ্রজাতন্ত্রী বাংলাদেশের সংবিধান এ যাবৎ কতটি সংশোধনী হয়েছে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) ১৪টি
   (খ) ১৩টি
   (গ) ১৬টি
   (ঘ) ১৭টি
 71. ভাষার মূল উপকরণ কী? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) বর্ণ
   (খ) শব্দ
   (গ) ধ্বনি
   (ঘ) বাক্য
 72. Add correct question tag to it: 'He excelled in sports ______?' **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) won't he
   (খ) don't he
   (গ) doesn't he
   (ঘ) didn't he
 73. Which one of the following process is the main task for the computer in mapping the geographical data? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Data storage
   (খ) Data visualization
   (গ) Data retrieving and drawing
   (ঘ) Data collection
 74. ধাতু কয় প্রকার? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) তিন প্রকার
   (খ) চার প্রকার
   (গ) পাঁচ প্রকার
   (ঘ) দুই প্রকার
 75. ফররুখ আহমেদের 'নৌফেল ও হাতেম' কোন শ্রেণির নাটক? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) সামাজিক নাটক
   (খ) প্রেমমূলক নাটক
   (গ) কাব্যধর্মী নাটক
   (ঘ) রূপক নাটক
 76. In a 3-phase power measurement by two-wattmeters method, both wattmeters have identical reading. The power factor of the load is ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Unity
   (খ) 0.8 lagging
   (গ) 0.8 leading
   (ঘ) Zero
 77. Count-to-infinity problem occurs in ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Distance vector routing
   (খ) Shortest path first
   (গ) Link state routing
   (ঘ) Hierarchical routing
 78. 'Do you enjoy teaching?' Here 'teaching' is a/an- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) gerund
   (খ) adjective
   (গ) infinitive
   (ঘ) participle
 79. জাতিসংঘের কোন অঙ্গ সংস্থা কোনো দেশের LDC থেকে Developing Country এবং Developing Country থেকে Developed Country এর বিষয়টি নির্ধারণ করে? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) সাধারণ পরিষদ
   (খ) নিরাপত্তা পরিষদ
   (গ) জাতিসংঘ
   (ঘ) অর্থনৈতিক ও সামাজিক পরিষদ
 80. Which language is directly understood by the Computer without translating? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) Machine language
   (খ) Assemble
   (গ) High level language
   (ঘ) None
 81. বঙ্গবন্ধু কোথায় ঐতিহাসিক ছয় দফা পেশ করেন? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) ঢাকা
   (খ) লাহোর
   (গ) চট্টগ্রাম
   (ঘ) রাজশাহী
 82. কোনটি মুক্তিযুদ্ধভিত্তিক উপন্যাস? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) একাত্তর কথা কয়
   (খ) আগুনের পরশমণি
   (গ) একাত্তরের দিনগুলি
   (ঘ) পায়ের আওয়াজ পাওয়া যায়
 83. A doctor who treats kidney patients is known as a/an ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) oncologist
   (খ) pathologist
   (গ) urologist
   (ঘ) gynecologist
 84. প্রকৃতিতে সবচেয়ে শক্ত পদার্থ কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) পিতল
   (খ) ইস্পাত
   (গ) গ্রানাইট
   (ঘ) হীরা
 85. Which one is an encryption function? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) c=E(M,K)
   (খ) N=D(e,K)
   (গ) e=E(M)
   (ঘ) None
 86. In C++, The library function exit() causes an exit from- **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) a block of statements
   (খ) a loop in which it occurs
   (গ) a function in which it occurs
   (ঘ) a program in which it occurs
 87. ‘শিষ্টাচার’ শব্দের সমার্থক কোনটি? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) সদাচার
   (খ) সততা
   (গ) মমতা
   (ঘ) সংযম
 88. Find out the correct spelling. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) adolescence
   (খ) adolessence
   (গ) addoleseence
   (ঘ) adolescence
 89. Bulbs in street lighting are connected in ______. **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) Parallel
   (খ) Series
   (গ) Series-parallel
   (ঘ) End to end
 90. ফ্রান্সের সম্রাট নেপোলিয়ান মারা যান কোথায়? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) ওয়াটার লু-তে
   (খ) ভার্সাইন নগরীতে
   (গ) সেন্ট হেলেনা দ্বীপে
   (ঘ) দ্বীপ এলবাইতে
 91. বাংলা বর্ণমালায় কয়টি ফলা? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) সাতটি
   (খ) ছয়টি
   (গ) পাঁচটি
   (ঘ) নয়টি
 92. ‘সবার উপরে মানুষ সত্য, তাহার উপরে নাই’- কে বলেছেন? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) চণ্ডীদাস
   (খ) বিদ্যাপতি
   (গ) রামকৃষ্ণ পরমহংস
   (ঘ) বিবেকানন্দ
 93. গুড ফ্রাইডে চুক্তি কোন দেশের শান্তির জন্য হয়েছিল? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) ডেনমার্ক
   (খ) নরওয়ে
   (গ) আয়ারল্যান্ড
   (ঘ) উত্তর কোরিয়া
 94. Find out the correct indirect speech of the following sentence: He said to me, “Thank you.” **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) He thanked me
   (খ) He had thanked me
   (গ) He told me that thank you
   (ঘ) He wished thank to me.
 95. কোনটি তারিখবাচক শব্দ? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) ১
   (খ) এক
   (গ) প্রথম
   (ঘ) পহেলা
 96. A computer program that converts an entire program into machine language is called a/an: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) Interpreter
   (খ) Converter
   (গ) Simulator
   (ঘ) Compiler
 97. গ্রীনল্যান্ড কোন দেশ দ্বারা শাসিত অথবা নিয়ন্ত্রিত? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) যুক্তরাষ্ট্র
   (খ) যুক্তরাজ্য
   (গ) ডেনমার্ক
   (ঘ) ফিনল্যান্ড
 98. ‘ক্রোধানল’ শব্দটি কোন সমাস? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) উপমান কর্মধারয়
   (খ) উপমিত কর্মধারয়
   (গ) রূপক কর্মধারয়
   (ঘ) মধ্যপদলোপী কর্মধারয়
 99. Which of the following types of table constraints prevents the entry of duplicate rows? **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) Foreign keys
   (খ) Primary keys
   (গ) Unique keys
   (ঘ) Candidate keys
 100. Choose the correct sentence: **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) Tell me what is your name
   (খ) Tell me what the name you dear
   (গ) Tell me what your name
   (ঘ) Tell me what your name is.
1. Select the pair which has the same relationship. ORTHOPEDIC: BONE **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) Psychiatry: Mind
   b) Skin: Allergy
   c) Antibiotics: Fever
   d) Fracture: Plaster
 2. He told me that he ______ watching the movie. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) is finished
   b) was finished
   c) had finished
   d) not finished
 3. Choose the word which is most opposite in meaning to the word EMBRACE **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) Disobey
   b) Contradict
   c) Reject
   d) Obscure
 4. I haven't seen you ______ a week. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) Within
   b) Since
   c) for
   d) from
 5. It ______ I would not lose temper. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) I were you
   b) I was you
   c) I am not you
   d) I am you
 6. The price of gold as well as silver ______ risen. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) is
   b) has
   c) have
   d) are
 7. Shariful ______ overtime for the last two weeks. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 58]**
   a) is working
   b) has been working
   c) is being working
   d) does

 8. The meeting has been ______ due to the demise of the Minister. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) called for
   b) called off
   c) called out
   d) called on
 9. There are ______ opportunities to learn from this excellent project. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) Plentiful
   b) many
   c) likely
   d) unlikely
 10. The suitable synonym of the word honest is. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) kind
   b) ample
   c) Magnificent
   d) candid
 11. The suitable antonym of the word feasible is. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) weak
   b) bad
   c) Small
   d) unattainable
 12. Big Ship Ltd. set up a cold storage in Rajshahi for preserving agricultural products, but so far the company ______ the clearance from the Agriculture Ministry. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) will take
   b) never takes
   c) has not taken
   d) would not take
 13. We hope that, by the end of this month, the cost of the maintenance of the tower ______. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) would have been estimated
   b) would estimate
   c) has been estimated
   d) will be estimated
 14. As ______ of the students can afford this high tuition fee, will need scholarships. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) few/most
   b) none/nobody
   c) some/they
   d) few/none
 15. Her proposal ______ the new ICT policy seems more suitable than any of the others. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) Irrelevant to
   b) regarding
   c) regardless
   d) instead of
 16. ______ the forthcoming training, we able to find the skilled engineers. **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) Through/were
   b) By cannot be
   c) Through/will be
   d) From/could be
 17. বাংলাদেশে প্রধান নির্বাচন কমিশনার নিয়োগ দেন কে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) প্রধানমন্ত্রী
   b) সার্চ কমিটি
   c) রাষ্ট্রপতি
   d) প্রধান বিচারপতি
 18. বঙ্গবন্ধু শেখ মুজিবুর রহমানকে কবে জাতির জনক ঘোষণা করা হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) ০৩ ই জানুয়ারি ১৯৭২
   b) ১৬ই ডিসেম্বর ১৯৭১
   c) ২৬ শে মার্চ ১৯৭২
   d) ০৩ই মার্চ ১৯৭১
 19. কোনটি মায়ানমার-বাংলাদেশের অভিন্ন নদী নয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) সাঙ্গু
   b) মাতামুহুরী
   c) নাফ
   d) কর্ণফুলী
 20. কত তারিখে বাংলাদেশের সংবিধান কার্যকর হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) ১৬ ডিসেম্বর ১৯৭১
   b) ১৬ ডিসেম্বর ১৯৭২
   c) ২৬ মার্চ ১৯৭২
   d) ২৬ মার্চ ১৯৭৩
 21. সুয়েজ খাল কোন কোন মহাদেশকে বিভক্ত করেছে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) এশিয়া ও অস্ট্রেলিয়া
   b) আমেরিকা ও আফ্রিকা
   c) ইউরোপ ও আমেরিকা
   d) এশিয়া ও আফ্রিকা
 22. কিংবদন্তি মোহাম্মদ আলি কিসের জন্য বিখ্যাত? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) অভিনয়
   b) বক্সিং
   c) মার্শাল আর্টস
   d) সঙ্গীত
 23. পৃথিবীর সর্ববৃহৎ প্রবাল প্রাচীর কোনটি? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) গ্রেট ব্যারিয়ার রিফ
   b) আমাজান রিফ
   c) আমেরিকান রিফ
   d) মেক্সিকো রিফ
 24. আমাজন বনের মোট আয়তনের ৬০% কোন দেশে অবস্থিত? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) আর্জেন্টিনা
   b) বলিভিয়া
   c) পেরু
   d) ব্রাজিল
 25. পৃথিবীর বর্তমান জনসংখ্যা কত? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 59]**
   a) প্রায় ৭০০ কোটি
   b) প্রায় ৬০০ কোটি
   c) প্রায় ৯০০ কোটি
   d) প্রায় ৮০০ কোটি
 26. সূর্য গ্রহণের সময় কোনটি হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) পৃথিবী সূর্য ও চাঁদের মাঝে থাকে
   b) পূর্ণিমা তিথি
   c) চাঁদ পৃথিবী ও সূর্যের মাঝে থাকে
   d) চাঁদ পৃথিবী ও চাঁদের মাঝে ৯০° কোন তৈরি করে।
 27. ইদানিং সুপার ফুড বলে পরিচিত খাদ্য কি বৈশিষ্ট্য বহন করে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) অনিদ্রা দূর করে
   b) মানসিক চাপ দূর করে
   c) উচ্চ রক্তচাপ নিয়ন্ত্রণ করে
   d) এটি একটি প্রাকৃতিক প্রতিবিধান
 28. পৃথিবী পৃষ্ঠের গড় তাপমাত্রা কত ডিগ্রী সেলসিয়াস? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) ১৪
   b) ২৪
   c) ১৮
   d) ১৫
 29. সঠিক শব্দ কোনটি? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) চলাকালীন সময়ে
   b) চলাকালে
   c) চলাকালের সময়ে
   d) চলাকালীন সময়
 30. সাধুভাষা থেকে চলিত বাংলায় লিখতে কোন পদযুগলের পরিবর্তন ঘটে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) বিশেষ্য ও বিশেষণ
   b) সর্বনাম ও ক্রিয়া
   c) বিশেষণ ও ক্রিয়া
   d) বিশেষ্য ও নাম
 31. ‘তিতাস একটি নদীর নাম’ উপন্যাসটি রচয়িতা কে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) তারাশংকর বন্দ্যোপাধ্যায়
   b) বন্দে আলী মিঞা
   c) জহির রায়হান
   d) অদ্বৈতমল্ল বর্মন
 32. “ইঁদুর কপালে” - এর বিপরীত বাগধারা কোনটি? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) অদৃষ্টের পরিহাস
   b) অন্ধকার
   c) একাদশে বৃহস্পতি
   d) কেউকেটা
 33. একটি ঘরে ব্যবহৃত বৈদ্যুতিক যন্ত্রপাতি কিভাবে লাগানো থাকে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) শ্রেণী সংযোগে
   b) শ্রেণী এবং সমান্তরাল উভয় সংযোগেই
   c) সমান্তরাল সংযোগে
   d) T-সংযোগে
 34. পাওয়ার ফ্যাক্টর কি? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) ভোল্টেজ এবং কারেন্টের কৌণিক পার্থক্যের কোসাইন
   b) ভোল্টেজ এবং কারেন্টের অনুপাত
   c) ভোল্টেজ এবং কারেন্টের কৌণিক পার্থক্যের সাইন
   d) উপরে কোনটিই না।
 35. একটি ডায়োডের সাংকেতিক চিত্রে দেখানো তীর চিহ্নটি কী নির্দেশ করে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) গ্রাউন্ড
   b) ইলেকট্রন প্রবাহের দিক
   c) অ্যানোড কারেন্ট প্রবাহের দিক
   d) বিদ্যুৎ (current) প্রবাহের দিক
 36. কোন পদার্থ দিয়ে ইনসুলেটর তৈরি করা হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) স্টিল
   b) কপার
   c) পোরসেলিন
   d) এলুমিনিয়াম
 37. N rpm গতিতে ঘূর্ণায়মান, D ব্যাসবিশিষ্ট একটি পুলিতে তার দিয়ে সংযুক্ত বস্তুর প্রতি সেকেন্ডে রৈখিক বেল কত হবে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) IIND/60
   b) IIND/180
   c) 2IIND/60
   d) 2IIND/180
 38. কোন বস্তুকে টানা বল (tension force) দিয়ে ভাঙ্গা হলে, সেই বস্তুর শূন্য লোড থেকে ব্রেকিং লোড পর্যন্ত স্ট্রেইস, স্ট্রেইন কার্ডের অন্তর্গত এরিয়াকে কী বলা হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) মডুলার অব ইলাস্টিসিটি
   b) মডুলার অব ট্রাফনেস
   c) মডুলার অব রিজিডিটি
   d) উপরের কোনটিই নয়
 39. তাপ শক্তিকে যান্ত্রিক শক্তিতে রূপান্তর করা হয় কীভাবে? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) অন্তর্দাহ ইঞ্জিনের সাহায্যে
   b) স্টিম টারবাইনের সাহায্যে
   c) গ্যাস টারবাইনের সাহায্যে
   d) উপরের সবগুলোটি।
 40. BIOS দিয়ে কি বোঝানো হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) Basic Input / Output System
   b) Basic Interrupt / Output System
   c) Basic Interrupt / Outcome System
   d) ওপরের কোনটিই নয়।
 41. নিচের কোনটি Browser নয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 60]**
   a) Chrome
   b) Firefox
   c) Facebook
   d) Safari

 42. একটি পাতলা বেলনাকার (cylindrical) প্রেসার ভেসেলের লঙ্গিটিউডিনাল স্ট্রেস ও সারকামফারেনশিয়াল স্ট্রেস এর অনুপাত কত হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 61]**
   a) \frac{1}{2}
   b) 1
   c) 2
   d) 3
 43. নিচের networking technology গুলোর মধ্যে কোনটি সাধারণত সবচেয়ে কম দূরত্বে (বা সবচেয়ে কাছাকাছি) তথ্য প্রেরণের জন্য ব্যবহৃত হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 61]**
   a) Wimax
   b) GSM
   c) WiFi
   d) Bluetooth
 44. নিচের কোনটি image ফাইলের extension হিসাবে ব্যবহৃত হয়? **(BTCL Junior Assistant Manager (JAM) Exam: 2022 (BUET)) [compact it 61]**
   a) .docx
   b) .xls
   c) .jpg
   d) উপরের কোনটিই নয়।
1. কোনটি জসিম উদ্দিনের নাটক? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) রাখালী
   (খ) মাটির কান্না
   (গ) বেদের মেয়ে
   (ঘ) বোবা কাহিনী
 2. ‘পিতালয়’ এর সন্ধি বিচ্ছেদ কোনটি? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) পিতা + আলয়
   (খ) পিত্রি + আলয়
   (গ) পিতা + লয়
   (ঘ) পিতৃ + আলয়
 3. “পলাতক দাসে দাও স্বাধীনতা” এখানে “দাসে” কোন কারকে কোন বিভক্তি? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) করণে সপ্তমী
   (খ) কর্মে সপ্তমী
   (গ) অধিকরণে সপ্তমী
   (ঘ) সম্প্রদানে সপ্তমী
 4. নিচের কোনটি “সূর্য” এর সমার্থক শব্দ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) শশাঙ্ক
   (খ) সুধাকর
   (গ) সুধাংশু
   (ঘ) সবিতা
 5. নিচের কোনটি ‘বহুব্রীহি’ সমাস? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) বীণাপাণি
   (খ) সিংহাসন
   (গ) চৌরাস্তা
   (ঘ) বাচস্পতি
 6. বন্য শব্দের চলিত রূপ কোনটি? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) বন্যে
   (খ) বুনো
   (গ) বনো
   (ঘ) বণ্য
 7. ‘সাক্ষী গোপাল’ বাগধারাটির অর্থ কী? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) অপদার্থ
   (খ) মূর্খ
   (গ) নিরেট বোকা
   (ঘ) নিষ্ক্রিয় দর্শক
 8. আমি ______ প্রার্থনা করি। শূন্যস্থানে বসবে? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) কায়মন বাক্যে
   (খ) কায়মন বাক্যে
   (গ) কায়মনোবাক্যে
   (ঘ) কায়মনো বাক্যে
 9. কোনটি শুদ্ধ বানান? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) উপরেউক্ত
   (খ) উপরোক্ত
   (গ) উপর্যুক্ত
   (ঘ) উপরক্ত
 10. কোন দুটি মূল স্বরধ্বনি নয়? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) ঐ, অ
   (খ) আ, ঔ
   (গ) ই, ও
   (ঘ) ঐ, ঔ
 11. Oncology কিসের সাথে জড়িত? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) চোখের গবেষণায়
   (খ) ক্যান্সার গবেষণায়
   (গ) হাড়ের সাথে জড়িত
   (ঘ) হার্টের সাথে সম্পর্কিত
 12. নিচের কোনটি ইনপুট ডিভাইস নয়? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) মাউস
   (খ) কীবোর্ড
   (গ) মনিটর
   (ঘ) জয়স্টিক
 13. কোনটি ইমেজ ফাইল এক্সটেনশন নয়? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) Png
   (খ) Jpeg
   (গ) avi
   (ঘ) gif
 14. TCP দিয়ে কোনটি বোঝানো হয়? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 61]**
   (ক) প্রোগ্রাম
   (খ) প্রোটোকল
   (গ) প্রোগ্রামিং
   (ঘ) ফ্লোচার্ট

 15. ISO কিসের সাথে সম্পর্কিত? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) অ্যাপল
   (খ) এনড্রয়েড
   (গ) নোকিয়া
   (ঘ) গুগল
 16. জাতিসংঘের কোন সংস্থাটি রিফিউজি নিয়ে কাজ করে? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) WHO
   (খ) UNDP
   (গ) UNHCR
   (ঘ) UNFCC
 17. রাতারগুল কোন ধরণের বন? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) ম্যানগ্রোভ
   (খ) জলাবন
   (গ) হাওর
   (ঘ) হ্রদ
 18. নিচের কোনটি সর্বোচ্চ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) ১ গিগাবাইট
   (খ) ১০০ মেগাবাইট
   (গ) ১০০০ মেগাবাইট
   (ঘ) ১০০০০ মেগাবাইট
 19. ছয়দফা কতসালে প্রস্তাব করা হয়? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) ১৯৬৯
   (খ) ১৯৭২
   (গ) ১৯৫৪
   (ঘ) ১৯৬৬
 20. বাংলাদেশের দীর্ঘতম নদী কোনটি? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) যমুনা
   (খ) ব্রহ্মপুত্র
   (গ) মেঘনা
   (ঘ) পদ্মা
 21. Find the area of a circle whose circumference is 22\text{ cm}? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 35.2\text{ cm}^2
   (খ) 38.5\text{ cm}^2
   (গ) 41.7\text{ cm}^2
   (ঘ) 47.6\text{ cm}^2
 22. The mode and mean is given by 7 and 8 respectively. Then the median is: **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 1/13
   (খ) 13/3
   (গ) 23/3
   (ঘ) 33
 23. The function f(x)=x+\cos x is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) Always increasing
   (খ) always decreasing
   (গ) Increasing for a certain range of x
   (ঘ) none of these
 24. A pole 6\text{m} high casts a shadow 2\sqrt{3}\text{ m} long on the ground, they find the angle of elevation of sun. **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 30^\circ
   (খ) 60^\circ
   (গ) 45^\circ
   (ঘ) 90^\circ
 25. If 6\sin^{-1}(x^2-6x+8.5) = \pi, then the value of x is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 1
   (খ) 2
   (গ) 3
   (ঘ) 5
 26. If \log_4 x = 12, then \log_2 \frac{x}{4} = ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 11
   (খ) 22
   (গ) 44
   (ঘ) 2
 27. Value for k, for which A = \begin{bmatrix} k & 8 \\ 4 & 2k \end{bmatrix} is a singular matrix is---? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) -4
   (খ) 4
   (গ) +4
   (ঘ) 0
 28. A fraction becomes 1/3 when 1 is subtracted from the numerator and it becomes 1/4 when 8 is added to its denominator. Find the fraction. **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 5/12
   (খ) 3/32
   (গ) 12/5
   (ঘ) 8
 29. If P(A) = 0.6, P(B) = 0.4, P(B/A) = 0.2 then find P(A \cup B) = ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 0.76
   (খ) 0.88
   (গ) 0.56
   (ঘ) 0.69
 30. The scalar product of 5\hat{i}+\hat{j}-3\hat{k} and 3\hat{i}-4\hat{j}+7\hat{k} is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) 10
   (খ) -10
   (গ) 15
   (ঘ) -15
 31. The visit his mother off and on. Here "off and on" means? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) Regularly
   (খ) Hourly
   (গ) Occasionally
   (ঘ) Consistently
 32. Leaders should not only make speeches they should also be prepared to bell the cat. **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 62]**
   (ক) To take lead in danger
   (খ) To tie bell to a cat's neck
   (গ) To be alert of the enemy
   (ঘ) to make noise

 33. BCIC is looking ______ engineers for recruitment. **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) at
   (খ) for
   (গ) on
   (ঘ) after
 34. Which spell is correct word (s)? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Encyclopedia Britannica
   (খ) Encyclopedia Britannica
   (গ) Enciclopadia Britannica
   (ঘ) Enciclopedia Britannica
 35. After see that he told, ______ for tat." **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) tot
   (খ) tut
   (গ) tit
   (ঘ) tet
 36. Synonym of "Reverently" is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Adversely
   (খ) Negatively
   (গ) Disapprovingly
   (ঘ) Respectfully
 37. "Proportion" means ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Aggregate
   (খ) ensemble
   (গ) bulk
   (ঘ) ratio
 38. Who is the Chairman of BCIC? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Shah Md. Imdadul Haque
   (খ) Mrs. Jasmin Nahar
   (গ) Kazi Mohammad Saiful Islam
   (ঘ) Mr. Mohammada Shaheen Kamal
 39. Karim memorizing carry ______ the holy Quran? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) on
   (খ) out
   (গ) off
   (ঘ) for
 40. Which Idiom means 'try every possible course of action in order to achieve something'? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Leave no stone unturned
   (খ) Take one to task
   (গ) Ride the high horse
   (ঘ) Give a wide berth
 41. It works hard, we are ______ progress. **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Taking
   (খ) Having
   (গ) Making
   (ঘ) Doing
 42. Bangladesh Chemical Industries Corporation (BCIC), fully owned by the Gob, was established in ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) 1st January, 1973
   (খ) 1st January, 1976
   (গ) 1st july, 1976
   (ঘ) 1st July, 1973
 43. How many enterprise under BCIC? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) 11
   (খ) 17
   (গ) 23
   (ঘ) none of a, b and c
 44. How much number of enterprise of BCIC at founded period? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) 100
   ((খ) 92
   (গ) 88
   (ঘ) 8
 45. Number of fertilize enterprise of BCIC is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) 3
   (খ) 8
   (গ) 5
   (ঘ) 10
 46. The number of board of director of BCIC is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) 5
   (খ) 6
   (গ) 8
   (ঘ) 7
 47. The Most Loss making enterprise of BCIC in 2020–2021 is ______ ? **(BCIC Assistant Programmer Exam: 2022 (BUET)) [compact it 63]**
   (ক) Shahjalal Fertilizer Project
   (খ) Ashugonj Fertilizer & Chemical Co.
   (গ) Karnophuli Paper Mills Ltd.
   (ঘ) Chittagong Urea Fertilizer Project
1. ইজিসিবি'র মোট বিদ্যুৎ ক্ষমতা প্রায় কত মেগাওয়াট (প্রায়)? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 63]**
   (ক) ৮৫০ মে: ও:
   (খ) ৯০০ মে: ও:
   (গ) ৯৫০ মে: ও:
   (ঘ) ১০০০০ মে: ও:

 2. সর্বশেষ কোন বিদ্যুৎ বিতরণ প্রতিষ্ঠানের আত্মপ্রকাশ ঘটে? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) NESCO
   (খ) WZPGCL
   (গ) DESCO
   (ঘ) BREB
 3. দেশে সর্বশেষ বিদ্যুৎ বিপর্যয় ঘটে কোন অঞ্চলে? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) পূর্বাঞ্চল
   (খ) উত্তরাঞ্চল
   (গ) পশ্চিমাঞ্চল
   (ঘ) পূর্বাঞ্চল
 4. ইজিসিবি'র পাওয়ার প্লান্ট কোথায় আছে? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) হরিপুর
   (খ) মাতারবাড়ি
   (গ) মহেশখালি
   (ঘ) পায়রা
 5. ইজিসিবি'র কোন ধরণের কোম্পানী? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) সরকারী
   (খ) পাবলিক
   (গ) স্বায়ত্তশাসিত
   (ঘ) গ্রুপ
 6. কোনো সাইকেলকে কম্বাইন্ড সাইকেলে রূপান্তর করতে নিচের কোনটির প্রয়োজন হয়? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) গ্যাস টারবাইন
   (খ) স্টিম টারবাইন
   (গ) কোল টারবাইন
   (ঘ) হাইড্রো টারবাই
 7. বাংলাদেশে সর্বোচ্চ বিদ্যুৎ পিক আওয়ার কোন সময়কে ধরা হয়? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) সন্ধ্যা ৭ টায়
   (খ) রাহ ৯ টায়
   (গ) দুপুর ১২ টায়
   (ঘ) বিকাল ৫ টায়
 8. নিউক্লিয়ার পাওয়ার প্লান্টের পাওয়ার ট্রান্সমিশনের জন্য সর্বোচ্চ কত ট্রান্সমিশন ভোল্টেজ ব্যবহার করা হবে? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) ১৩৩ কেভি
   (খ) ৩৩ কেভি
   (গ) ২৩০ কেভি
   (ঘ) ৪০০ কেভি
 9. একটি পল্লি বিদ্যুৎ সমিতির অফিস প্রধানের পদবী কী? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) জেনারেল ম্যানেজার
   (খ) নির্বাহী প্রকৌশলী
   (গ) সিস্টেম ইঞ্জিনিয়ার
   (ঘ) চীপ ইঞ্জিনিয়ার
 10. নিউক্লিয়ার পাওয়ার প্লান্টের পাওয়ার ইউনিটের আয়ুষ্কাল কত? **(EGCB Sub-Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 64]**
   (ক) ৪০ বছর
   (খ) ৫০ বছর
   (গ) ৬০ বছর
   (ঘ) ৭০ বছর।
1. অহরহ শব্দের সন্ধি বিচ্ছেদ কর? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: অহঃ + অহ
 2. সাপ এর সমার্থক শব্দ কি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: অহি
 3. ঢেক ছাঁটা কোন সমাস? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: তৃতীয়া তৎপুরুষ
 4. বাংলাদেশের প্রথম ন্যানো স্যাটেলাইটের নাম কি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ব্র্যাক অন্বেষা
 5. তারামন বিবি কোন সেক্টরে যুদ্ধ করেছে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ১১ নং সেক্টর
 6. Poet of Nature এর লেখক কে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: William Wordsworth
 7. পাকিস্তান কবে শেখ মুজিবুর রহমানকে কারাগার থেকে মুক্তি দেয়? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ৮জানুয়ারি, ১৯৭২
 8. বঙ্গবন্ধু স্যাটেলাইট-১ কত তারিখে উৎক্ষেপন করা হয়? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ১২ই মে, ২০১৮
 9. বঙ্গবন্ধু স্যাটেলাইট এর ট্রান্সপন্ডার সংখ্যা কতটি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ৪০ টি
 10. LTE এর পূর্ণ নাম কি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: Long Term Evolution
 11. MoTiV কোন দেশের প্রতিষ্ঠান? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: উগান্ডা
 12. T-20 বিশ্বকাপ ২০২১ এ ম্যান অব দ্যা সিরিজ হন কে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ডেভিড ওয়ার্নার
 13. আমি কিংবদন্তীর কথা বলছি’ কবিতাটির লেখক কে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: আবু জাফর ওবায়দুল্লাহ
 14. MNP সার্ভিস BTRC কবে প্রণয়ন করে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ২০১৭
 15. বাংলাদেশ কবে SAE-ME-WE এর সদস্য হয়? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ২১ মে, ২০০৬
 16. SDG এর Goal কয়টি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: ১৭ টি
 17. He complied ______ my request. **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 64]**
   উত্তর: with

 18. To bring of - অর্থ কি? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 65]**
   উত্তর: Look after a child until it an adult
 19. \sqrt{-4} \times \sqrt{-4} = কত? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 65]**
   উত্তর: -4
 20. বাংলাদেশ কবে টেস্ট ক্রিকেটের মর্যাদা লাভ করে? **(BTRC Assistant Director (Technical) Exam: 2022 (MIST)) [compact it 65]**
   উত্তর: ২৬ জুন, ২০০০
1. ‘প্রাগৈতিহাসিক’ গল্পের রচয়িতা কে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) মানিক বন্দ্যোপাধ্যায়
   (খ) বিভূতিভূষণ বন্দ্যোপাধ্যায়
   (গ) আবু জাফর শামসুদ্দিন
   (ঘ) শওকত ওসমান
   **উত্তর: ক**
 2. He said to me “What a nice man you are, sir” The correct indirect speech of this sentence is: **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) He asked me what a nice man I was.
   (খ) Respectfully he exclaimed with joy that I was a very nice man.
   (গ) Addressing me as sir, he respectfully exclaimed with joy that I was very nice man.
   (ঘ) He asked me what a nice man I was.
   **উত্তর: খ**
 3. মহাবিশ্বে মৌলিক বল কয়টি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) ৩ টি
   (খ) ৪ টি
   (গ) ৫ টি
   (ঘ) ৬ টি
   **উত্তর: ক**
 4. ভাষা আন্দোলনের পটভূমিতে রচিত নাটক কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) রক্ত
   (খ) মাকড়সা
   (গ) ফেরি আসছে
   (ঘ) কবর
   **উত্তর: ঘ**
 5. The passive form of the sentence ‘He wrote a letter to me’-is- **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) A letter was written to me by him.
   (খ) A letter is written to my by him.
   (গ) A letter had written to me by him.
   (ঘ) A letter had written by me to him.
   **উত্তর: ক**
 6. কোন রশ্মির ভেদন ক্ষমতা বেশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) আলফা
   (খ) বিটা
   (গ) গামা
   (ঘ) সমগুলিরসমান
   **উত্তর: গ**
 7. পৃথিবীর কেন্দ্রে অভিকর্ষক ত্বরনের মান কত? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) শূন্য
   (খ) 9.8\text{ m/s}^2
   (গ) 4.9\text{ m/s}^2
   (ঘ) অসীম
   **উত্তর: ক**
 8. কোনটি গ্রীন হাউজ গ্যাস নয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) \text{O}_2
   (খ) \text{O}_3
   (গ) \text{CO}_3
   (ঘ) Water Vapor
   **উত্তর: গ**
 9. ত্রিভুজের তিন বাহুর দৈর্ঘ্য যথাক্রমে a,b এবং c **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) a+b > c
   (খ) a+b = c
   (গ) a+b < c
   (ঘ) a+b \approx c
   **উত্তর: ক**
 10. লেন্সের ক্ষমতার একক কী? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) ডায়াপটার
   (খ) ডেসিবেল
   (গ) ওয়াট
   (ঘ) মিটার
   **উত্তর: ক**
 11. কোন বস্তুকে ভূ-পৃষ্ঠ হতে 19.6\text{m} উপর থেকে ছেড়ে পৌঁছাতে বস্তুটি কত সময় লাগবে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) 2\text{ sec}
   (খ) 1\text{ sec}
   (গ) \frac{1}{2}\text{ sec}
   (ঘ) 9\text{ sec}
   **উত্তর: ক**
 12. প্রথম বাংলা সাময়িক পত্র কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) বেঙ্গল গেজেট
   (খ) দিগদর্শন
   (গ) বঙ্গদূত
   (ঘ) সমাচার দর্পণ
   **উত্তর: খ**
 13. কোনটি মুদ্রা ধাতু নয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) কপার
   (খ) সিলভার
   (গ) গোল্ড
   (ঘ) রন্টজেনিয়াম
   **উত্তর: ঘ**
 14. একটি কোণের পরিমাপ ১৮১° হলে তাকে কি কোণ বলে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 65]**
   (ক) স্থূল কোণ
   (খ) সমকোণ
   (গ) সূক্ষ্ম কোণ
   (ঘ) প্রবৃদ্ধ কোণ
   **উত্তর: ঘ**

 15. সর্ব কনিষ্ঠ খেতাবপ্রাপ্ত মুক্তিযোদ্ধা হলেন– **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) শহীদুল ইসলাম লালু
   (খ) হামিদুর রহমান
   (গ) নূর মোহাম্মদ শেখ
   (ঘ) মোস্তফা কামাল
   **উত্তর: গ**
 16. ‘অচলা’ কোন উপন্যাসের চরিত্র? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) দত্তা
   (খ) দেনা পাওনা
   (গ) গৃহদাহ
   (ঘ) চরিত্রহীন
   **উত্তর: গ**
 17. বাংলা সাহিত্যের প্রথম মুসলমান কবি হচ্ছেন– **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) দৌলত উজির বাহরাম খান
   (খ) আলাউল
   (গ) শাহ্ মুহাম্মদ সগীর
   (ঘ) দৌলত কাজী
   **উত্তর: গ**
 18. CNG এর মূল উপাদান কী? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) অক্সিজেন
   (খ) মিথেন
   (গ) ইথেন
   (ঘ) অকটেন
   **উত্তর: খ**
 19. তাপমাত্রা বাড়লে পরিবাহীর রোধ --- **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) বাড়ে
   (খ) কমে
   (গ) অপরিবর্তিত থাকে
   (ঘ) শূন্যহয়
   **উত্তর: খ**
 20. পার্বত্য চট্টগ্রাম শান্তি চুক্তি কবে সম্পাদিত হয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) ১২ নভেম্বর ১৯৯৭
   (খ) ২ ডিসেম্বর ১৯৯৭
   (গ) ১৬ ডিসেম্বর ১৯৯৮
   (ঘ) ২৫ ডিসেম্বর ১৯৯৭
   **উত্তর: খ**
 21. কোন ধাতু কক্ষ তাপমাত্রার তরল থাকে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) রেডিয়াম
   (খ) জিং
   (গ) প্রোটনিয়াম
   (ঘ) মারকারী
   **উত্তর: ঘ**
 22. The abbreviation of a.m is – **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) Anno meridiem
   (খ) After morning
   (গ) Ante meridiem
   (ঘ) Anti-meriden
   **উত্তর: গ**
 23. কোন আরব দেশ বাংলাদেশকে প্রথম স্বীকৃতি দেয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) সেনেগাল
   (খ) সৌদি আরব
   (গ) ইরাক
   (ঘ) মিসর
   **উত্তর: গ**
 24. পাকস্থলীতে কোন এসিড উৎপন্ন হয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) \text{HClO}
   (খ) \text{HClO}_4
   (গ) \text{HCl}
   (ঘ) \text{HNO}_3
   **উত্তর: গ**
 25. Choose the correct form of verb: I (watch) an English movie last night. **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) have watch
   (খ) had watched
   (গ) watched
   (ঘ) have been watching
   **উত্তর: গ**
 26. কোনটি ত্রিমাত্রিক বস্তু? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) তল
   (খ) ঘনক
   (গ) রেখা
   (ঘ) বিন্দু
   **উত্তর: খ**
 27. 1\text{ cm}^3 কত \text{m}^3 এর সমান? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) 10^{-6}\text{ m}^3
   (খ) 10^{-3}\text{ m}^3
   (গ) 10^{-2}\text{ m}^3
   (ঘ) 0.1\text{ m}^3
   **উত্তর: ক**
 28. কাজী নজরুল ইসলামের জন্ম তারিখ কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) ১১ জ্যৈষ্ঠ
   (খ) ২২ শ্রাবণ
   (গ) ১২ ভাদ্র
   (ঘ) ২৫ বৈশাখ
   **উত্তর: ক**
 29. ‘স্বাগত’ শব্দের সঠিক সন্ধি বিচ্ছেদ কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) সু+আগত
   (খ) স্ব + আগত
   (গ) সা + আগত
   (ঘ) স্ব্+আগত
   **উত্তর: ক**
 30. কোন পদার্থ আন্তকণা আকর্ষণ বেশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) চিনি
   (খ) পানি
   (গ) তেল
   (ঘ) অক্সিজেন
   **উত্তর: ক**
 31. NATO কোন বছর প্রতিষ্ঠিত হয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) ১৯৪৯
   (খ) ১৯৫৪
   (গ) ১৯৫৫
   (ঘ) ১৯৫৬
   **উত্তর: ক**
 32. কোনটির তরঙ্গ দৈর্ঘ্য বেশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) লাল আলো
   (খ) নীল আলো
   (গ) মাইক্রোওয়েভ
   (ঘ) রেডিও ওয়েভ
   **উত্তর: ক**
 33. শুষ্ক বাতাসের তুলনায় ঘনত্ব : **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) বেশি
   (খ) কম
   (গ) সমান
   (ঘ) কোন সম্পর্ক নেই
   **উত্তর: ক**
 34. এশিয়ার দীর্ঘতম নদী কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 66]**
   (ক) হোয়াংহো
   (খ) ইয়াংসিকিয়াং
   (গ) গঙ্গা
   (ঘ) সিন্ধু
   **উত্তর: খ**
 35. স্থিতি শক্তি আছে কোন পদার্থের? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) তরল
   (খ) বায়বীয়
   (গ) অষ্ট্রীয়
   (ঘ) কঠিন
   **উত্তর: ঘ**
 36. নীচের কোনটি মৃদু তড়িৎ বিশ্লেষ্য? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) \text{NaCl}
   (খ) \text{H}_2\text{O}
   (গ) \text{CaSO}_4
   (ঘ) \text{H}_2\text{SO}_4
   **উত্তর: ক**
 37. ২২ ক্যারেট স্বর্ণে কতভাগ স্বর্ণ থাকে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) 100%
   (খ) 95.37%
   (গ) 91.67%
   (ঘ) 75%
   **উত্তর: গ**
 38. বাংলা ভাষায় কয় প্রকারের উপসর্গ আছে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) দুই প্রকার
   (খ) চার প্রকার
   (গ) পাঁচ প্রকার
   (ঘ) তিন প্রকার
   **উত্তর: ঘ**
 39. বৃত্তস্থ সামান্তরিক কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) রম্বস
   (খ) আয়ত
   (গ) বর্গ
   (ঘ) ট্রাপিজিয়াম
   **উত্তর: খ**
 40. \text{H}_2\text{SO}_4-এ সালফারের জারণ সংখ্যা কত? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) +2
   (খ) +4
   (গ) +6
   (ঘ) 0
   **উত্তর: গ**
 41. ‘কলম’ শব্দটি কোন ভাষা থেকে এসেছে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) আরবি
   (খ) ফারসি
   (গ) ফরাসি
   (ঘ) তুর্কি
   **উত্তর: ক**
 42. কোন রেখার উপর সূর্য সারা বছর লম্বভাবে কিরণ দেয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) মেরু রেখা
   (খ) নিরক্ষ রেখা
   (গ) অক্ষ রেখা
   (ঘ) দ্রাঘিমা রেখা
   **উত্তর: খ**
 43. Green House কথাটি প্রথম ব্যবহৃত হয় কোন সালে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) ১৯৬৬
   (খ) ১৮৯৬
   (গ) ১৮৯০
   (ঘ) ১৯৫০
   **উত্তর: খ**
 44. কোনটি শব্দের তীব্রতা লেভেল পরিমাপের একক? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) হার্টজ
   (খ) ডেসিবেল
   (গ) প্যাসকেল
   (ঘ) টেসলা
   **উত্তর: খ**
 45. ‘পহেলা’ কোন ধরণের শব্দ? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) সংখ্যা বাচক
   (খ) গণনা বাচক
   (গ) পূরণ বাচক
   (ঘ) তারিখ বাচক
   **উত্তর: ঘ**
 46. ক্রোমোসমের গঠন কি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) DNA
   (খ) প্রোটিন
   (গ) RAN
   (ঘ) DNA এবং প্রোটিন
   **উত্তর: ঘ**
 47. Choose the appropriate preposition: Average price of food decreased ______ 13% **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) by
   (খ) at
   (গ) to
   (ঘ) upto
   **উত্তর: ঘ**
 48. Knot কিসের একক? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) গতিবেগ
   (খ) দূরত্ব
   (গ) গভীর
   (ঘ) ত্বরণ
   **উত্তর: ক**
 49. পরম শূন্য তাপমাত্রায় অর্ধপরিবাহী কিসের মত আচরণ করে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) পরিবাহী
   (খ) অপরিবাহী
   (গ) অর্ধপরিবাহী
   (ঘ) কোনটিই নয়
   **উত্তর: গ**
 50. রক্ত কোষের ক্যান্সারকে কি বলে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) লিওকেমিয়া
   (খ) এনিমিয়া
   (গ) Blood Clotting
   (ঘ) অ্যানজিনা
   **উত্তর: ক**
 51. I know you- the correct passive form is – **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) you are known by me
   (খ) you are known to me
   (গ) you are knowing to me
   (ঘ) you are known at me
   **উত্তর: খ**
 52. ভাষার মূল উপাদান কী? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) বর্ণ
   (খ) ধ্বনি
   (গ) শব্দ
   (ঘ) বাক্য
   **উত্তর: খ**
 53. কোন কারণে শব্দের প্রতিধ্বনি সৃষ্টি হয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) প্রতিফলন
   (খ) প্রতিসরণ
   (গ) উপরিপাতন
   (ঘ) সমপাতন
   **উত্তর: ক**
 54. I could not read the words because they were too blurry. Here ‘blurry’ means : **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
   (ক) small
   (খ) unclear
   (গ) unknown
   (ঘ) difficult
   **উত্তর: খ**
 55. এন্টি ভাইরাস কি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 67]**
(ক) সফটওয়্যার
(খ) ম্যালওয়্যার
(গ) হার্ডওয়্যার
(ঘ) সিস্টেম সফটওয়্যার
**উত্তর: ক**
 56. What is the meaning of the word "lately"? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) in the past
   (খ) at this moment
   (গ) in the recent time
   (ঘ) one more time
   **উত্তর: গ**
 57. The verb form of the word 'deep' is- **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) depth
   (খ) endeep
   (গ) deepen
   (ঘ) In depth
   **উত্তর: গ**
 58. সমতল দর্পণ ব্যবহৃত হয় কোন যন্ত্র তৈরিতে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) পেরিস্কোপ
   (খ) টেলিস্কোপ
   (গ) ক্যামেরা
   (ঘ) মাইক্রোস্কোপ
   **উত্তর: ক**
 59. Which is the correct synonym of the word INDISPENSABLE? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) Trivial
   (খ) Essential
   (গ) Negligible
   (ঘ) Worthy
   **উত্তর: খ**
 60. ব্রোঞ্জ কোন দুটি ধাতুর সংকর? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) অ্যালুমিনিয়াম ও টিন
   (খ) কপার ও টিন
   (গ) কপার ও গোল্ড
   (ঘ) কপার ও সিলভার
   **উত্তর: খ**
 61. পাখি আকাশে ওড়ে- Correct translation of this sentence is : **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) Bird fly in the sky.
   (খ) The bird flies in the sky.
   (গ) A bird fly in the sky.
   (ঘ) A bird fly in sky
   **উত্তর: খ**
 62. কোনটি পদার্থের জড়তা পরিমাপকের একক? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) ভর
   (খ) গতিবেগ
   (গ) তাপমাত্রা
   (ঘ) কৌনিকবেগ
   **উত্তর: ক**
 63. The author of the story "The Luncheon" is - **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) William Shakespeare
   (খ) William Wordsworth
   (গ) W. S. Maugham
   (ঘ) T. S. Eliot
   **উত্তর: গ**
 64. It makes me nostalgic. Here nostalgic is a/an- **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) Verb
   (খ) Noun
   (গ) Adjective
   (ঘ) Adverb
   **উত্তর: গ**
 65. Fill in the blank. His brother is – he looks. **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) Younger than
   (খ) as young
   (গ) Younger
   (ঘ) Very young
   **উত্তর: খ**
 66. তার বয়স বেড়েছে কিন্তু বুদ্ধি বাড়েনি- এটি কোন ধরনের বাক্য ? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) সরল বাক্য
   (খ) মিশ্র বাক্য
   (গ) যৌগিক বাক্য
   (ঘ) বৈপরিত্যমূলক বাক্য
   **উত্তর: গ**
 67. বাংলাদেশের সংবিধানে কয়টি অনুচ্ছেদ আছে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) ১৫০
   (খ) ১৪০
   (গ) ১৫৩
   (ঘ) ১৫১
   **উত্তর: গ**
 68. সবুজপত্র পত্রিকা বাংলা সাহিত্যে কোন ভাষারীতির প্রবর্তনে অগ্রণী ভূমিকা রেখেছে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) সাধুভাষা
   (খ) চলিত ভাষা
   (গ) উপভাষা
   (ঘ) আঞ্চলিক ভাষা
   **উত্তর: খ**
 69. কাদম্বিনী শব্দের অর্থ কি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) নদী
   (খ) মেঘমালা
   (গ) হীত কামনা
   (ঘ) বলহীনা
   **উত্তর: খ**
 70. ১ লিটার বিশুদ্ধ পানিতে H এর পরিমাণ কত? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) 10^{-7}\text{ মোল}
   (খ) 10^7\text{ মোল}
   (গ) 10^{-6}\text{ মোল}
   (ঘ) 10^{-5}\text{ মোল}
   **উত্তর: ক**
 71. কোন উপন্যাসটি মুক্তিযুদ্ধভিত্তিক? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) ক্রীতদাসের হাসি
   (খ) হাঙর নদী গ্রেনেড
   (গ) আব্দুল্লাহ
   (ঘ) লাল সালু
   **উত্তর: খ**
 72. What is the opposite word of facilitate? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) encourage
   (খ) impede
   (গ) increase
   (ঘ) promote
   **উত্তর: খ**
 73. অপটিক্যাল ফাইবার আলোর কোন নীতিতে কাজ করে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) প্রতিফলন
   (খ) প্রতিসরন
   (গ) অপবর্তন
   (ঘ) পূর্ণ অভ্যন্তরীণ প্রতিফলন
   **উত্তর: ঘ**
 74. কোন দেশটির ভেটো ক্ষমতা নেই? **(BPSC- Instructor Exam: 31.10.2022) [compact it 68]**
   (ক) যুক্তরাষ্ট্র
   (খ) যুক্তরাজ্য
   (গ) রাশিয়া
   (ঘ) জার্মানি
   **উত্তর: ঘ**
 75. মুক্তিযুদ্ধা তারামন বিবি যুদ্ধ করেছেন কোন সেক্টরে? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) ৯ নং
   (খ) ৪ নং
   (গ) ৮ নং
   (ঘ) ১১ নং
   **উত্তর: ঘ**
 76. ‘বই পড়া’ প্রবন্ধটি কার লেখা? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) রবীন্দ্রনাথ ঠাকুর
   (খ) প্রমথ চৌধুরী
   (গ) মোতাহের হোসেন চৌধুরী
   (ঘ) হায়াৎ মামুদ
   **উত্তর: খ**
 77. কোনটি ক্ষার? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) \text{NH}_3
   (খ) \text{NaSO}_4
   (গ) \text{NaCl}
   (ঘ) \text{HNO}_2
   **উত্তর: ক**
 78. IELTS stands for- **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) International English Language Teaching System
   (খ) International English Language Testing Skill
   (গ) International English Language Testing System
   (ঘ) International English Language Teaching Skill
   **উত্তর: গ**
 79. বাংলাদেশের জাতীয় সংসদের অধিবেশন কে আহ্বান করেন? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) স্পীকার
   (খ) প্রধানমন্ত্রী
   (গ) রাষ্ট্রপতি
   (ঘ) প্রধান বিচারপতি
   **উত্তর: গ**
 80. কোন গ্যাসের ব্যাপন হার বেশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) \text{N}_2
   (খ) \text{O}_2
   (গ) \text{CO}_2
   (ঘ) \text{H}_2
   **উত্তর: ঘ**
 81. চন্দ্র কোন শব্দের উদাহরণ? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) তৎসম
   (খ) তদ্ভব
   (গ) দেশি
   (ঘ) বিদেশি
   **উত্তর: ক**
 82. কোনটি আউটপুট ডিভাইস? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) মাউস
   (খ) প্রিন্টার
   (গ) কি বোর্ড
   (ঘ) স্ক্যানার
   **উত্তর: খ**
 83. কোনটি ভেক্টর রাশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) চাপ
   (খ) ভরবেগ
   (গ) কাজ
   (ঘ) বল
   **উত্তর: খ**
 84. কোন পদার্থের আপেক্ষিক তাপ সর্বাধিক? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) বায়ু
   (খ) পানি
   (গ) লোহা
   (ঘ) তামা
   **উত্তর: খ**
 85. প্রকৃতিতে প্রাপ্ত হাইড্রোজেনের আইসোটোপ কয়টি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) ২টি
   (খ) ৩টি
   (গ) ৪টি
   (ঘ) ৫টি
   **উত্তর: খ**
 86. দহগ্রাম ছিটমহল কোন জেলায় অবস্থিত? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) নীলফামারী
   (খ) কুড়িগ্রাম
   (গ) লালমনিরহাট
   (ঘ) দিনাজপুর
   **উত্তর: গ**
 87. কত তাপমাত্রায় পানির ঘনত্ব বেশি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) 10^\circ\text{C}
   (খ) 4^\circ\text{C}
   (গ) 85^\circ\text{C}
   (ঘ) 100^\circ\text{C}
   **উত্তর: খ**
 88. ব্লিচিং পাউডারের সংকেত কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) \text{Ca(OCI)Cl}
   (খ) \text{C}_6\text{H}_6\text{O}
   (গ) \text{CaCO}_3
   (ঘ) \text{HCl}
   **উত্তর: ক**
 89. ভারতচন্দ্র রায়গুণাকর কোন কাব্য রচনা করেছেন? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) অভয়া মঙ্গল
   (খ) শিব মঙ্গল
   (গ) অন্নদা মঙ্গল
   (ঘ) চণ্ডী মঙ্গল
   **উত্তর: গ**
 90. কোন দেশটি Group of Seven (G-7) এর সদস্য নয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) কানাডা
   (খ) ইতালি
   (গ) সুইডেন
   (ঘ) জাপান
   **উত্তর: গ**
 91. কোন আলোতে সালোক সংশ্লেষণ ভালো হয় না? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) লাল
   (খ) নীল
   (গ) কমলা
   (ঘ) হলুদ
   **উত্তর: ঘ**
 92. এশীয় উন্নয়ন ব্যাংক এর সদর দপ্তর কোথায়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) হংকং
   (খ) সিঙ্গাপুর
   (গ) ম্যানিলা
   (ঘ) ব্যাংকক
   **উত্তর: গ**
 93. উপমিত কর্মধারায় সমাসের উদাহরণ কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
   (ক) মুখচন্দ্র
   (খ) কাঁচামিঠা
   (গ) চন্দ্রমুখ
   (ঘ) মনমাঝি
   **উত্তর: গ**
 94. কোন গ্রন্থটি কাজী নজরুল ইসলামের লেখা নয়? **(BPSC- Instructor Exam: 31.10.2022) [compact it 69]**
(ক) আরেক ফাল্গুন
(খ) ব্যথার দান
(গ) রিক্তের বেদন
(ঘ) মৃত্যুক্ষুধা
**উত্তর: ক**
 95. জনসংখ্যার ভিত্তিতে সবচেয়ে বড় মুসলিম দেশ কোনটি? **(BPSC- Instructor Exam: 31.10.2022) [compact it 70]**
   (ক) বাংলাদেশ
   (খ) ইন্দোনেশিয়া
   (গ) মালয়েশিয়া
   (ঘ) সৌদি আরব
   **উত্তর: খ**
 96. Choose the right preposition: Rice sells ______ 50 TK a kg. **(BPSC- Instructor Exam: 31.10.2022) [compact it 70]**
   (ক) over
   (খ) in
   (গ) at
   (ঘ) to
   **উত্তর: গ**


১. মহেঞ্জোদারো কোন সভ্যতার অন্তর্ভুক্ত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) রোমান
(খ) সিন্ধু
(গ) গ্রিক
(ঘ) আফগানিস্তান
**Ans: খ**
২. গণপ্রজাতন্ত্রী বাংলাদেশের সংবিধান দিবস কত তারিখ? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) ৪ নভেম্বর
(খ) ৮ অক্টোবর
(গ) ৪ ডিসেম্বর
(ঘ) ৪ জানুয়ারী
**Ans: ক**
৩. The word ‘Imbibe’ means- **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(a) to learn
(b) to cry
(c) to drink
(d) to acquire
**Ans: c**
৪. বাংলাদেশ সুগারক্রপ গবেষণা ইনস্টিটিউট কোথায় অবস্থিত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) গাজীপুর
(খ) পাবনা
(গ) ময়মনসিংহ
(ঘ) রাজশাহী
**Ans: খ**
৫. কোন পরিবাহীর তারের ব্যাস দ্বিগুণ এবং দৈর্ঘ্য চারগুণ করা হলে উহার রোধ কত হবে? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) অর্ধেক
(খ) দ্বিগুণ
(গ) চারগুণ
(ঘ) একই থাকবে
**Ans: গ**
৬. একটি সূষম সাইন তরঙ্গের পিক-টু-পিক ভোল্টেজ ২০ ভোল্ট হলে- **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) তরঙ্গটির গড়মান ১০ ভোল্ট
(খ) তরঙ্গটির গড়মান ৭.০৭ ভোল্ট
(গ) তরঙ্গটির আর.এম.এস মান ৬.৩৭ ভোল্ট
(ঘ) তরঙ্গটির আর.এম.এস মান ১৪.১৪ ভোল্ট
**Ans: ঘ**
৭. নন-ইনভারটিং অপারেশনাল অ্যাম্প্লিফায়ারের ইনপুট রেজিস্টেন্স ১০ কিলো ওহম এবং ফিডব্যাক রেজিস্টেন্স ২০ কিলো ওহম হলে ক্লোজড-লুপ গেইন কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) ১
(খ) ২
(গ) ৩
(ঘ) ৪
**Ans: গ**
৮. ১ পিকো ফ্যারাডে = কত ফ্যারাডে? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) 10^{-9}
(খ) 10^{-10}
(গ) 10^{-11}
(ঘ) 10^{-12}
**Ans: ঘ**
৯. পাইজোইলেক্ট্রিক ইফেক্টও কারণ কি? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) ক্রিস্টাল উপর ম্যাগনেটিক ফিল্ডের প্রভাব
(খ) দুটি ক্রিস্টালের সংযোগস্থলে তাপ প্রভাব
(গ) ক্রিস্টালের উপর চাপ প্রয়োগ
(ঘ) ক্রিস্টালের সাথে ভেজাল মিশ্রণ
**Ans: গ**
১০. নিম্নের কোন লজিক অপারেশনটি সঠিক? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) A+A = 1
(খ) AA = 0
(গ) A+1 = 1
(ঘ) A+1 = 0
**Ans: গ**
১১. বিসিডি কোডে বিট সংখ্যা কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) 1
(খ) 2
(গ) 8
(ঘ) 4
**Ans: ঘ**
১২. বাইনারি পদ্ধতির যোগে 1+1+1 = কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) 10
(খ) 11
(গ) 101
(ঘ) 111
**Ans: খ**
১৩. একটি তরঙ্গের পিরিয়ড ১০ মিলি সেকেন্ড হলে এটির ফ্রিকুয়েন্সি কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) ১০ হার্টজ
(খ) ২০ হার্টজ
(গ) ৫০ হার্টজ
(ঘ) ১০০ হার্টজ
**Ans: ঘ**
১৪. অ্যাম্প্লিচিউড মডুলেশনে কি ঘটে? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**
(ক) সিগন্যালের অ্যাম্প্লিচিউড পরিবর্তিত হয়
(খ) সিগন্যালের ফ্রিকুয়েন্সি পরিবর্তিত হয়
(গ) ক্যারিয়ার অ্যাম্প্লিচিউড পরিবর্তিত হয়
(ঘ) ক্যারিয়ার ফ্রিকুয়েন্সি পরিবর্তিত হয়
**Ans: গ**
১৫. ইন্ডাক্টরের ইন্ডাক্টেন্স নিম্নের কোনটির উপর নির্ভর করেনা? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 70]**

(ক) ব্যবহৃত কোরের প্রস্থচ্ছেদের ক্ষেত্রফল
(খ) ব্যবহৃত তারের প্যাচ সংখ্যা
(গ) ব্যবহৃত তারের পুরুত্ব
(ঘ) ব্যবহৃত কোরের দৈর্ঘ্য
**Ans: গ**
১৬. নিচের কোন সেলটি শুষ্ক কিন্তু পুনরায় চার্জযোগ্য? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) নিকেল-ক্যাডমিয়াম
(খ) মারকারি
(গ) লেড এসিড
(ঘ) সোলার
**Ans: ক**
১৭. একটি ডায়োডে ডিপলেশন লেয়ার কখন তৈরি হয়? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) ফরওয়ার্ড বায়াস করলে
(খ) রিভার্স বায়াস করলে
(গ) ডায়োড তৈরির সময়
(ঘ) তাপমাত্রা বাড়লে
**Ans: গ**
১৮. ব্রেকডাউন ঘটলে জিনার ডায়োডের ক্ষেত্রে কোনটি প্রায় অপরিবর্তিত থাকে? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) ভোল্টেজ
(খ) কারেন্ট
(গ) ইম্পিডেন্স
(ঘ) ক্যাপাসিটেন্স
**Ans: ক**
১৯. ফুল-ওয়েভ রেক্টিফায়ারের কর্মদক্ষতা কত? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) ৪০.৬%
(খ) ৮১.২%
(গ) ৯১.৬%
(ঘ) ১০০%
**Ans: খ**
২০. স্বাধীন বাংলাদেশের জাতীয় সংসদের প্রথম স্পিকার কে ছিলেন? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) আব্দুল খালেক উকিল
(খ) আব্দুল হাকিম
(গ) সাহাবুদ্দিন আহমদ
(ঘ) মোহাম্মদ উল্লাহ
**Ans: ঘ**
২১. গ্রিনিচমান সময়ের সঙ্গে বাংলাদেশের সময়ের পার্থক্য কত ঘণ্টা? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) ৪ ঘণ্টা
(খ) ৬ ঘণ্টা
(গ) ১০ ঘণ্টা
(ঘ) ৫ ঘণ্টা
**Ans: খ**
২২. তেভাগা আন্দোলনের নেত্রী? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) ইলা মিত্র
(খ) তারামন বিবি
(গ) প্রীতিলতা
(ঘ) জাহানারা
**Ans: ক**
২৩. তেজস্ক্রিয়তার একক কি? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) রন্টজেন
(খ) কুরি
(গ) হেনরি
(ঘ) রেডিয়াম
**Ans: খ**
২৪. VSAT বলতে বুঝায়? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) Virtual Small Aperture Satellite
(খ) Very Small Aperture Terminal
(গ) Very Small Application Terminal
(ঘ) Vertical Satellite
**Ans: খ**
২৫. bit এর সংখ্যার বিচারে নিচের কোন ক্রমটি সঠিক? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
(ক) \text{byte} > \text{GB} > \text{KB} > \text{TB}
(খ) \text{byte} > \text{KB} > \text{GB} > \text{TB}
(গ) \text{byte} > \text{KB} > \text{TB} > \text{GB}
(ঘ) \text{byte} > \text{TB} > \text{GB} > \text{KB}
**Ans: খ**
২৬. ট্রান্সফরমারের কোন উইন্ডিং এ বেশি প্যাঁচ থাকে? সেকন্ডারি উইন্ডিং **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
২৭. নিউক্লিয়ার রিয়েক্টর ব্যবহৃত কন্ট্রোল রড কি দিয়ে তৈরি? ক্যাডমিয়াম **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
২৮. নিম্নের কোনটি কমানোর জন্য ট্রান্সফরমারের কোর লেমিনেটিং করা হয়? এডি কারেন্ট লস **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
২৯. নিম্নের কোনটি চার লেয়ার বিশিষ্ট ডিভাইস? সিলিকন কন্ট্রোল রেক্টিফায়ার **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩০. জাংশন ফিল্ড ইফেক্ট ট্রানজিস্টর- কারেন্ট নিয়ন্ত্রিত **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩১. ইমিটার ফলোয়ার ব্যবহারের প্রধান উদ্দেশ্য কি?- কারেন্ট গেইন **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩২. ঘড়িতে এখন ৪ টা বাজে, ঘণ্টার কাটা ও মিনিটের কাটার মধ্যকার কোণ কত? ১২০ ডিগ্রি **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩৩. ইসলামের ইতিহাস ও ঐতিহ্য কোন কাব্যের উপজীব্য? সাত সাগরের মাঝি- ফররুখ আহমদ **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩৪. ট্রানজিস্টরের সার্কিট সঠিকভাবে বায়াসিং করা না হলে- আউটপুট সিগন্যাল বিকৃত হতে পারে **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩৫. পূর্ণ অভ্যন্তরীণ প্রতিফলন ঘটে যখন আলো- **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**
৩৬. দুইটি সমান্তরাল পরিবাহী কে কোন অপরিবাহী দ্বারা পৃথক করা হলে তাকে কি বলে? **(BDCCL Assistant Manager (Transmission) Exam: 2022) [compact it 71]**


১. দক্ষিণ এশিয়ার দীর্ঘতম টাওয়ার কোথায় অবস্থিত? **Ans: কলম্বো** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 71]**
২. একুশে ফেব্রুয়ারিকে কখন আন্তর্জাতিক মাতৃভাষা দিবস হিসেবে ঘোষণা করা হয়? **Ans: ১৯৯৯ সারে** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 71]**
৩. রজার ফেদেরার মোট কয়টি উইম্বলডন জয়লাভ করেন? **Ans: ৮টি** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৪. বাংলাদেশের ও মায়ানমার পৃথককারী নদী কোনটি? **Ans: নাফ** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৫. টি-২০ বিশ্বকাপ ২০২২ কোথায় অনুষ্ঠিত হয়েছে? **Ans: অস্ট্রেলিয়া** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৬. বীরশ্রেষ্ঠ মতিউর রহমানের দেহাবশেষ কখন পাকিস্তান থেকে বাংলাদেশ ফিরিয়ে আনা হয়? **Ans: ২০০৬ সালে** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৭. Plagiarism means- **Ans: Theft of Idea** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৮. The tiger fell ______ prey. **Ans: Upon** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
৯. পিজিসিবি এর ক্ষমতা কত? **Ans: 950MW** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১০. Do not sit on a ______ chair. **Ans: broken** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১১. নিউক্লিয়ার পাওয়ার প্ল্যান্টের পাওয়ার ট্রান্সমিশনের জন্য সর্বোচ্চ ট্রান্সমিশন ভোল্টেজ কত? **Ans: 400KB** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১২. নিউক্লিয়ার পাওয়ার প্ল্যান্টের “পাওয়ার ইউনিট” এর আয়ুষ্কাল কত বছর? **Ans: 50 Year** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৩. বাংলাদেশকে কোন আরব দেশ প্রথম স্বীকৃতি দেয়? **Ans: ইরাক** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৪. All birds have beaks, and all sparrows are birds, so all sparrows must have beaks. **Ans: Syllogism** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৫. “রক্তাক্ত প্রান্তর” নাটকটির রচয়িতা কে? **Ans: মুনীর চৌধুরী** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৬. কোনটি যৌগিক শব্দ? **Ans: গায়ক = গৈ + অক (অক) – অর্থ : গান করে যে।** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৭. ইজিসিবি কোন ধরনের কোম্পানী? **Ans: পাবলিক** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৮. নিচের কোনটি সর্বশেষ প্রতিষ্ঠিত হয়েছে? **Ans: NESCO (2016)** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
১৯. ২০২১ সালে GDP প্রবৃদ্ধির হার কত? **Ans: ৬.৯৪%** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২০. কোনো সাইকেলকে কম্বাইন্ড সাইকেলে রূপান্তর করতে নিচের কোন টারবাইনের প্রয়োজন হয়? **Ans: গ্যাস টারবাইন** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২১. সর্বশেষ কোথায় গ্রীড বিপর্যয় হয়? **Ans: Eastern** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২২. পিক আওয়ার কখন ঘটে? **Ans: 5pm** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৩. বাংলাদেশের সর্বোচ্চ বেসামরিক পুরস্কার কোনটি? **Ans: স্বাধীনতা পুরস্কার** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৪. International Day for Total Elimination of Nuclear Weapons 2022? **Ans: ২৬ সেপ্টেম্বর** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৫. আন্তর্জাতিক ট্রান্সলেশন দিবসের থিম কি? **Ans: A world without Barriers** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৬. Could: Rain :: Vapour : **Ans: Moistrue** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৭. নিচের কোনটি নেটওয়ার্ক ডিভাইস নয়? **Ans: Wi-Fi** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৮. নোবেল পুরস্কার ২০২২, সাহিত্যে নোবেল কে পেয়েছেন **Ans: এনি আরনেল** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
২৯. “কাদম্বিনী” শব্দের অর্থ কী? **Ans: মেঘ** **(EGCB Assistant Engineer (ICT) Exam: 2022 (BUET)) [compact it 72]**
1. Choose the correct sentence: **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 72]**
   (a) Rahim is as tall as mine
   (b) Rahim is tall as mine
   (c) Rahim is as tall as I
   (c) Rahim is as tall as me
   **Ans: c**
 2. There is ______ on the roads today. **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 72]**
   (a) Few traffics
   (b) Very much traffic
   (c) Too much traffic
   (c) Too many traffic
   **Ans: c**
 3. A tank is 40% full. If 16 liters of water is added to the tank, it becomes 4/5 full. The capacity of the tank is: **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 72]**
   (a) 32 liters
   (b) 35liters
   (c) 40 liters
   (d) 42 liters
   **Ans: c**
 4. In a class of 24 students, one half of the student take higher math & one third take physics and one fourth take both. How many take neither? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 72]**

(a) 14
(b) 15
(c) 10
(d) 8
**Ans: c**
 5. 32^{x+y} = 16^{x+y}, what is the value x? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   (a) Y
   (b) -y
   (c) 2y
   (d) \text{X}(2y+2)
   **Ans: b**
 6. In a class there are 4 boys and 4 girls. Two students are selected at random, what is the probability that both will be girls? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   (a) \frac{1}{2}
   (b) \frac{3}{7}
   (c) \frac{3}{4}
   (d) \frac{3}{14}
   **Ans: d**
 7. কোন দুটি মূল স্বরধ্বনি নয়? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   (a) ঐ, ঔ
   (b) আ, ও
   (c) ই, ও
   (d) ঐ, ঔ
   **Ans: d**
 8. সারারাত বৃষ্টি হয়েছে। 'সারারাত' কোন কারকে কোন বিভক্তি? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   ক) কর্তৃকারকে ষষ্ঠী
   খ) কর্ম কারকে পঞ্চমী
   গ) অপাদান কারকে পঞ্চমী
   ঘ) অধিকরণ কারকে শূন্য
   **Ans: ঘ**
 9. বাংলা সাহিত্যের প্রথম মহিলা ঔপন্যাসিক কে? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   ক) বেগম রোকেয়া
   খ) সুফিয়া কামাল
   গ) স্বর্ণকুমারী দেবী
   ঘ) রিজিয়া রহমান
   **Ans: গ**
 10. What is the name of Russian foreign minister? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   (a) Sergey Lavrov
   (b) Ivar Igor
   (c) Sergei Shoigu
   (d) Dmytro Khuleba
   **Ans: a**
 11. সঠিক বানান চিহ্নিত করুনঃ **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   ক) বীণাপাণি
   খ) চরিত্র
   গ) মূঢ়
   ঘ) প্রত্যুষ
   **Ans: খ**
 12. 'বহ্ন্যুৎসব' শব্দের সঠিক সন্ধি বিচ্ছেদ কোনটি? **(Petrobangla; Assistant Engineer Exam: 16/12/2022) [compact it 73]**
   ক) বহ্ন্য + উৎসব
   খ) বহ্ন্যু + উৎসব
   গ) বহ্নি + উৎসব
   ঘ) বহ্নি + উৎসব
   **Ans: ঘ**

1. Select correct spelling? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   (a) Psychology
   (b) Sychology
   (c) Sycholagy
   (d) shychology
   **Ans: a**
 2. গীতাঞ্জলি কোন সালে প্রকাশিত হয় **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   ক) ১৯১১
   খ) ১৯১৩
   গ) ১৯১২
   ঘ) ১৯১০
   **Ans: ঘ**
 3. কোনটি সঠিক বানান- **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   ক) গীতাঞ্জলি
   খ) গীতাঞ্জলী
   গ) গিতাঞ্জলি
   ঘ) গিতাঞ্জলী
   **Ans: ক**
 4. Which one is correct? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   (a) Tit for tat
   (b) Tect for tat
   (c) Teat for tet
   (d) Tit for teet
   **Ans: a**
 5. The Showing ______ **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   (a) Off
   (b) Up
   (c) On
   (d) in
   **Ans: a**
 6. If \log_4(x)=12 then find \log_2(4/x) **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   (a) 22
   (b) 23
   (c) 26
   (d) 12
   **Ans: a**
 7. If age is P times then y after 6 years x age is 17 then find the age of y with respect to p. **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   (a) 11p
   (b) 11p+6
   (c) P+6
   (d) P+11
   **Ans: b**
 8. Submarine ক্যাবল কয়টি? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   ক) ২
   খ) ৩
   গ) 8
   ঘ) ৬
   **Ans: ক**
 9. কোনটিতে ক্রিয়াকাল উহ্য **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
   ক) আমি বই পড়ছি
   খ) সে পড়াশোনা করে
   গ) সে খাচ্ছে
   ঘ) সে ঘুমাতে যাবে
   **Ans: ক**
 10. অম্বুর এর সমার্থক শব্দ কোনটি? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 73]**
ক) আকাশ
খ) পৃথিবী
গ) জল
ঘ) সমুদ্র
**Ans: ক**
 11. কোন আসল ৫ বছরে সরল সুদে বৃদ্ধি পেয়ে ১০,০০০ টাকা এবং ১০ বছরে বৃদ্ধি পেয়ে ১২,০০০ টাকা হবে? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 74]**
   ক) ৫০০০ টাকা
   খ) ৬,৫০০ টাকা
   গ) ৮০০০ টাকা
   ঘ) ৯,৫০০ টাকা
   **Ans: গ**
 12. 2^{30}+2^{30}+2^{30}+2^{30}= কত? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 74]**
   ক) 2^{120}
   খ) 8^{30}
   গ) 2^{32}
   ঘ) 8^{120}
   **Ans: গ**
 13. একটি পরীক্ষায় ৫২% শিক্ষার্থী বাংলায় এবং ৪২% শিক্ষার্থী ইংরেজীতে অকৃতকার্য হয়। উভয় বিষয়ে অকৃতকার্য শিক্ষার্থী ১৭% হলে উভয় বিষয়ে কৃতকার্য শিক্ষার্থী? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 74]**
   ক) ২৩%
   খ) ২৭%
   গ) ২৮%
   ঘ) ৩৩%
   **Ans: ক**
 14. ১০০ টাকায় ১২টি কলা ক্রয় করে, ১২০ টাকায় ১০টি কলা বিক্রয় করলে শতকরা লাভ হবে? **(BDCCL; Assistant Manager (Cloud) Exam: 14/10/2022) [compact it 74]**
   ক) ২২%
   খ) ৩০%
   গ) ৩৩%
   ঘ) ৪৪%
   **Ans: ঘ**

1. Which of the following countries is the largest emitter of \text{CO}_2? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) France
   (b) USA
   (c) India
   (d) China
   **Ans: d**
 2. When china did recognized Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 1974
   (b) 1972
   (c) 1973
   (d) 1975
   **Ans: d**
 3. What is the length and width of the National Flag of Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 5:3
   (b) 5:2
   (c) 6:3
   (d) 10:3
   **Ans: a**
 4. Which country has Bengali as official language in Africa? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) South Africa
   (b) Sierra leone
   (c) Ghana
   (d) Somalia
   **Ans: b**
 5. The cabinet of Mujibnagar Government was sworn in- **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) Meherpur
   (b) Dhaka
   (c) Chattagram
   (d) Kolkata
   **Ans: a**
 6. What will be the generation capacity target by 2041 in Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 40,000 MW
   (b) 60,000 MW
   (c) 20,000 MW
   (d) 45,000 MW
   **Ans: b**
 7. During the liberation war of Bangladesh, Dhaka was under which sector? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 2
   (b) 4
   (c) 5
   (d) 7
   **Ans: a**
 8. The first gas field of Bangladesh was discovered in- **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 1956
   (b) 1957
   (c) 1986
   (d) 1955
   **Ans: d**
 9. Which of the following countries is the largest emitter of \text{CO}_2? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) France
   (b) USA
   (c) India
   (d) China
   **Ans: d**
 10. The only foreigner to be awarded the title “Bir Protic” is- **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) W.A.S Ouderland
   (b) Simon Dring
   (c) Sam manekshaw
   (d) Mark Tully
   **Ans: a**
 11. During the liberation war of Bangladesh, Dhaka was under which sector? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 2
   (b) 4
   (c) 5
   (d) 7
   **Ans: a**
 12. When china did recognized Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 1974
   (b) 1972
   (c) 1973
   (d) 1975
   **Ans: d**
 13. What is the length and width of the National Flag of Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 74]**
   (a) 5:3
   (b) 5:2
   (c) 6:3
   (d) 10:3
   **Ans:**

**(a) 5:3**
 14. Which country has Bengali as official language in Africa? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) South Africa
   (b) Sierra leone
   (c) Ghana
   (d) Somalia
   **Ans: b**
 15. The cabinet of Mujibnagar Government was sworn in- **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) Meherpur
   (b) Dhaka
   (c) Chattagram
   (d) Kolkata
   **Ans: a**
 16. What will be the generation capacity target by 2041 in Bangladesh? **(BCPCL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) 40,000 MW
   (b) 60,000 MW
   (c) 20,000 MW
   (d) 45,000 MW
   **Ans: b**
1. Who was the commander in chief of the mukti bahini? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) M.A. Rab
   (b) M.A.G Osmani
   (c) K.M Shafiullah
   (d) A.K Khander
   **Ans: b**
 2. Total amount of budget of Bangladesh for FY 2022-2023 was- **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) 6,78,064 Cr, TK
   (b) 5,23,190 Cr, TK
   (c) 6,80,473 Cr, TK
   (d) 7,80,064 Cr, TK
   **Ans: a**
 3. What is the current rank of Bangladesh of SDG? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) 109
   (b) 104
   (c) 136
   (d) 129
   **Ans: b**
 4. What is the meaning of 'to bell the cat'? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) Do the difficult
   (b) Do the unpleasant
   (c) To take lead in danger
   (d) Take the initiative
   **Ans: d**
 5. 'ব্যক্ত' শব্দের বিপরীতার্থক শব্দ কোনটি? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   ক) ত্যক্ত
   খ) গ্রাহ্য
   গ) দৃঢ়
   ঘ) গূঢ়
   **Ans: ঘ**
 6. Rahima carry ______ his language. **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) Out
   (b) Down
   (c) On
   (d) Away
   **Ans: d**
 7. The span of the Padma bridge are- **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) 40
   (b) 41
   (c) 42
   (d) 43
   **Ans: b**
 8. Who is the most wicket taker in T20? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) Rashid khan
   (b) TG southee
   (c) Shakib al hasan
   (d) SL Malinga
   **Ans: c**
 9. 'সুন্দর মাত্রেরই একটি আকর্ষণ শক্তি আছে'। এই বাক্যে 'সুন্দর' শব্দটি কোন পদ? **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   ক) বিশেষ্য
   খ) বিশেষণ
   গ) সর্বনাম
   ঘ) বিশেষণের বিশেষণ
   **Ans: ক**
 10. Install capacity of payra- **(NPCBL Assistant Engineer Exam: 07/01/2022) [compact it 75]**
   (a) 1320 MW
   (b) 1200 MW
   (c) 600 MW
   (d) 2400 MW
   **Ans: a**
 1. Which one of the following is not a search engine? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 76]**
   a. Windows
   b. Google
   c. Yahoo
   d. Bing
 2. Which of the following cannot be used as a public IP address? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 76]**
   a. 17.0.0.1
   b. 168.172.19.34
   c. 172.15.29.63
   d. 192.168.13.18
 3. In the diagram shown below. L1 is an Ethernet LAN and L2 is a Token-Ring LAN. An IP packet originates from sender S and traverses to R, as shown. The link within each ISP, and across two ISPs, are all point to point optical links. The initial value of TTL is 32. The maximum possible value of TTL field when R receives the datagram is- **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 76]**
   a. 25
   b. 24
   c. 26
   d. 28
 4. Which protocol is used to send a destination network unknown message back to the originating host? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 76]**
   a. TCP
   b. ARP
   c. ICMP
   d. BootP

 5. Which of the following statements is FALSE regarding a bridge? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. Bridge is a layer 3 device
   b. Bridge reduces collision domain
   c. Bridge is used to connect two or more LAN segments
   d. Bridge reduces broadcast domain
 6. Which of the following devices takes data sent from one network device and forward it to the destination node based on MAC address? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. Hub
   b. Modem
   c. Switch
   d. Gateway
 7. Suppose we want to download text documents at the rate of 100 pages per second. Assume that a page consists of an average of 24 lines with 80 characters in each line. What is the required bit rate of the channel? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. 182 kbps
   b. 512 kbps
   c. 1.248 Mbps
   d. 1.536 Mbps
 8. Which of the following is not a valid IP address? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. 3FFE::1:200:F8FF:FE75:50DF
   b. 10.25.26.24
   c. ABCD::100::F8FF:FE75:50DF
   d. 13.15.17.19
 9. Distance vector routing algorithm is a dynamic routing algorithm. The routing tables in distance vector routing algorithm are updated ____. **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. automatically
   b. by server
   c. with back up database
   d. by exchanging information with neighbor nodes
 10. Which of the following regular expressions represents the set of all the binary strings with an odd number of 1's? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 77]**
   a. 0*+(10*1) *10*
   b. (0*+(10*1) *)10*n
   c. 0*+10*1*10*
   d. (0*+10) *1*10*

17. Consider a 50 Mbps satellite channel with a 500 milliseconds round top propagation delay. If the sender wants to transmit 1000 bit frames, how much time will it take for the receiver to receive the frame? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 79]**
   a. 250 milliseconds
   b. 20 milliseconds
   c. 520 milliseconds
   d. 270 milliseconds
 18. The combination of an IP address and a port number is known as ____. **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 79]**
   a. Network number
   b. Socket address
   c. Subnet mask number
   d. MAC address
 19. The address resolution protocol (ARP) is used for- **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 79]**
   a. Finding the IP address from the DNS
   b. Finding the IP address of the default gateway
   c. Finding the IP address that corresponds to a MAC address
   d. Finding the MAC address the corresponds to an IP address
 20. A receiving host has failed to receive all of the segments that is should acknowledge what can the host do the improve the reliability of this communication session? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 79]**
   a. Send a different source port number
   b. Restart the virtual circuit
   c. Decrease the sequence number
   d. Decrease the window size
 21. Assume that Source S and Destination D are connected through an intermediate router R. How many times a packet has to visit the network layer and data link layer during a transmission from S to D? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 79]**
   a. Network layer -4 times, Data link layer -4 times
   b. Network layer -4 times, Data link layer -6 times
   c. Network layer -2 times, Data link layer -4 times
   d. Network layer -3 times, Data link layer -4 times

 28. Which one of the following has the truth value FALSE for the variables A=TRUE and B=TRUE and C=TRUE? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. A\bar{B}C + \bar{A}BC
   b. X = A.\bar{B} + \bar{A}.B
   c. (AC + \bar{B})(\bar{A} + (B \oplus C))
   d. (A + B) \oplus C \oplus (B + C)
 29. Which layer 1 devices can be used to enlarge the area covered by a single LAN segment? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. Switch only
   b. RF45 connector only
   c. Switch and Hub
   d. Hub and Repeater
 30. Which initial program is called at the starting of a computer? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. Computer Startup Loader
   b. Operating System Details
   c. Bootstrap Loader
   d. Hardware System Details
 31. What is the correct output of the following C program statements? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
```c
int array[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, *p=array+5;
printf("%d\n",p[1]);

```
a. 1
b. 2
c. 3
d. Compile Error
 32. Suppose you need to assign IPv4 address to two computers of your company so that the both computers belong to the subnet. 255.255.255.240. Which of the following is a valid assignment? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. 172.16.5.14 and 172.16.5.17
   b. 172.16.5.17 and 172.16.5.29
   c. 172.16.5.29 and 172.16.5.33
   d. 172.16.5.33 and 172.16.5.4
 33. Consider the following relational data table, Employee. Now, find the output for the following SQL Statement? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
```sql
SELECT COUNT (*) FROM Employee, Employee, Employee

```
a. 4
b. 27
c. 32
d. 64
 34. What is the characteristic of OOP programming that allows binding data and methods to work as a unit? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. Inheritance
   b. Encapsulation
   c. Polymorphism
   d. Projection

 35. Which of the following uses the flip-flop circuit in a memory cell? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 82]**
   a. DRAM
   b. EEPROM
   c. SDRAM
   d. SRAM
 36. Which of the logic expressions is equivalent to the digital circuit shown in the figure? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 82]**
   a. X = A.B + \overline{A}.\overline{B}
   b. X = A.B + \bar{A}.\bar{B}
   c. X = A.\bar{B} + \bar{A}.B
   d. X = (\bar{A} + B).(A + \bar{B})
 37. Laili digitally signs a message and sends it to Mojnu. Verification of the signature by Mojnu requires- **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 82]**
   a. Laili's public key
   b. Mojnu's public key
   c. Mojnu's private key
   d. Laili's private key
 38. Network 10.20.30.0 was assigned to the ITGod company to connect its ISP. The administrator of ITGod would like to configure one router with commands to access the internet. Which commands could be configured on the Gateway Router to allow internet access to the center network? **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 82]**
   A. Gateway(config)# ip route 0.0.0.0 0.0.0.0 10.20.30.2
   B. Gateway(config)# router rip
   C. Gateway(config)# network 10.20.30.0
   D. Gateway(config)# ip default-network 10.20.30.0
   a. A only
   b. C only
   c. A, B and D
   d. A and D
 39. Classless Inter Domain Routing (CIDR) receives a packet with address 131.23.151.76. The routers routing table has the following entries **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 82]**
| Prefix | Output Interface |
|---|---|
| 131.16.0.0/12 | 3 |
| 131.28.0.0/14 | 5 |
| 131.19.0.0/16 | 2 |
| 131.22.0.0/15 | 1 |
In which output interface the packet is forwarded to?
a. 1
b. 2
c. 3
d. 5

 40. An attacker sits between the sender and receiver and captures the information and retransmits to the receiver after some time without altering the information. This attack is called as ____ **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 83]**
   a. Denial of service attack
   b. Masquerade attack
   c. Simple attack
   d. Complex attack
 41. Which of the following is correct to initialize arrays in C? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 83]**
   a. int array = (1, 2, 3, 4, 5)
   b. int array = {1, 2, 3, 4, 5}
   c. int array() = (1, 2, 3, 4, 5)
   d. int array[5] = {1, 2, 3, 4, 5}
 42. What is the access methodology in array? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 83]**
   a. Sequential
   b. Random
   c. Rational
   d. Stochastic
 3. What is the output for the following C code segment? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
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
 4. In a shop, customers are provided the service as a first come first serve policy. But some special customers can be served at any time based on their importance. Which data structure most fits this scenario? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. Stack
   b. Queue
   c. Priority Queue
   d. Dequeue
 5. Which of the following is correct? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. “X extends Y” is correct if and only if X is a class and Y is an interface
   b. “X extends Y” is correct if and only if X is an interface and Y is a class
   c. “X extends Y” is correct if X and Y are either both classes or both interfaces
   d. “X extends Y” is correct for all combinations of X and Y being classes and/or interfaces
 6. Which of the following data structures is more suitable for graph representation in Floyd Warshall Algorithm? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. Adjacency Matrix
   b. Adjacency List
   c. Incidence Matrix
   d. Incidence List
 7. Which of the following is not a method of the Thread class? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. sleep (long msec)
   b. stop()
   c. go()
   d. yield()
 8. Which of the following statements is correct regarding abstract classes? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. An abstract class cannot be extended
   b. A subclass of a non-abstract superclass cannot be abstract
   c. A subclass can override a concreate method in a superclass to declare it abstract
   d. An abstract class cannot be used as a data type

 9. The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
   a. Inheritance
   b. Polymorphism
   c. Over functioning
   d. Overriding
 10. In the following graph, determine the cost of the shortest path between node 1 to node 4. **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
   a. 0
   b. 4
   c. -5
   d. \infty
 11. Suppose you searching student data using student number as the key. Which of following arrangement of the student data is suited for binary search? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
   a. Student data are arranged in the positions indicated by the student numbers hash values.
   b. Student data are arranged randomly irrespective of the student numbers.
   c. Student data are arranged in ascending order of student numbers.
   d. Student data are arranged in the order of the cell addresses of the student numbers' locations.
 12. What is the output of this Java program? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
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
 13. Suppose you are using an HTML browser at a client machine C to access a static HTML webpage hosted in a HTTP server S. The page contains exactly one static embedded image which also resides at S. Assuming no web caching which of the following is correct when you load the webpage along with the embedded image? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 85]**
   a. C need to send at least 2 HTTP requests to S using two different TCP connection.
   b. C need to send at least 2 HTTP requests to S but a single TCP connection is sufficient.
   c. A single HTTP request is sufficient without using any TCP connection from C to S.
   d. A single HTTP request is sufficient using a single TCP connection from C to S.

 14. Converting a primitive type data into its corresponding wrapper class object instance is called- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 86]**
   a. Boxing
   b. Wrapping
   c. Instantiation
   d. Auto boxing
 15. The combination of an IP address and a port number is known as ____. **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 86]**
   a. network number
   b. socket address
   c. subnet mask number
   d. MAC address
 16. An n x n array v is- defined as follows;
   v[i, j]=i-j for all i, j, 1<=i <=n, 1<=j <=n
   The sum of the elements of the array v is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 86]**
   a. 0
   b. n-1
   c. n^2-3n+2
   d. n^2(n+1)/2
 17. To implement Dijkstra's shortest path algorithm on unweighted graphs so that it runs in linear time, the data structure to be used is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 86]**
   a. Queue
   b. Stack
   c. Heap
   d. B-Tree
 18. Consider the function fun (x, y) below. That is the value of fun (4, 3)? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
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
 19. What does the following function do? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
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
 20. Which of the following is not an in-place algorithm? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   a. Insertion sort
   b. Selection sort
   c. Merge sort
   d. Heap sort
 21. Which of the following statements is/are TRUE for an undirected graph? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   P: Number of odd degree vertices is even
   Q: Sum of degrees of all vertices is even
   a. P Only
   b. Q Only
   c. Both P and Q
   d. Neither P nor Q
 22. What is the full form of SMTP? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   a. Single Mail Text Protocol
   b. Single Mail Transfer Problem
   c. Simple Mail Transfer Protocol
   d. Simple Mail Textual Protocol
 23. An inversion in a an array A[] is a pair (A[i], A[j] such that A[i]>A[j} and i<j. An array will have maximum number of inversions if it is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   a. Sorted in increasing order
   b. Sorted in decreasing order
   c. Sorted in alternate fashion
   d. Both A and B
 24. Which of the following data structures can be used both as Stack and Queue? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
   a. Vector
   b. Hash Table
   c. Deque
   d. Binary Search Tree

 25. Table Employee has 10 records. It has a non-NULL SALARY column which is also UNIQUE. The SQL statement **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
```sql
SELECT COUNT(*) FROM Employee WHERE SALARY > ANY (SELECT SALARY FROM EMPLOYEE);

```
prints
a. 0
b. 5
c. 9
d. 10
 26. Which of the following is the regular expression to represent all the binary strings with odd number of 1's? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   a. 0*(10*1)*11
   b. 0*(10*1)*10*
   c. (0*10*1)*0*10*
   d. (0*10*)*1(0*10*)*
 27. What is the correct output of the following C program statements? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
```c
int array[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, *p=array+5;
printf("%d\n",p[1]);

```
a. 1
b. 2
c. 3
d. Compile Error
 28. What does following function do for a given Linked List with first node as head? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
```c
void fun1(struct node* head) {
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
 29. Suppose you want to insert n elements into an empty linked list while maintaining the sorted order. What is the worst-case time complexity? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   a. \theta(n)
   b. \theta(n\log n)
   c. \theta(1)
   d. \theta(n^2)
 30. Which of the following operations is not O(1) for an array of sorted data. You may assume that array elements are distinct. **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   a. Find the ith largest element
   b. Delete an element
   c. Find the ith smallest element
   d. All of the above
 31. Which protocol dynamically assigns IP addresses in a TCP/IP network? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   a. ARP
   b. RIP
   c. SMTP
   d. DHCP

 32. The Post-order traversal of a binary tree is 8, 9, 6, 7, 4, 5, 2, 3, 1, The In-order traversal of the same tree is 8, 6, 9, 4, 7, 2, 5, 1, 3. What is the height of the above binary tree? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 89]**
   a. 2
   b. 3
   c. 4
   d. 1
 33. Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 89]**
   a. An exclusive logical sum of N with 0Fh
   b. A logical product of N with 0Fn
   c. A negative logical product of N with 0Fn
   d. A logical sum of N with 0Fh
 34. The minimum number of comparisons required to determine if an integer appears more than n/2 times in a sorted array of n integers is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 89]**
   a. \Theta(n)
   b. \Theta(\log n)
   c. \Theta(\log*n)
   d. \Theta(1)
 35. Which of the following is the appropriate set of test cases, (A, B) when the part of a program shown is tested by decision condition coverage (branch coverage)? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 89]**
```c
if(A OR B) X = X+1;
else X = X-1;

```
a. {(False, True)}
b. {(False, True), (*True, False), (True, True)}
c. {(False, True), (True, False)}
d. {(False, False), (True, True)}



 36. Consider a virtual memory system where three pages are allocated for real memory. If the page replacement algorithm used is FIFO, how many page replacements take place for the access sequence: 1, 3, 2, 1, 4, 5, 2, 3, 4, 5? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
   a. 2
   b. 3
   c. 4
   d. 6
 37. Find Output: **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
```c
#include<stdio.h>
struct Testnode(char x, y, z;);
int main() {
    struct Trstnode node1 = {'1', '2', 'c'+3};
    struct Testnode *node2 = &node1;
    printf("%c, %c", *((char*)node2+1),*((char*)node2+2));
    return 0;
}

```
Which one is the output of the above program?
a. 0, f
b. 0, c+3
c. '0', 'c+3'
d. '0', 'f'
 38. Consider an Entity-relationship from entity set E1 to entity set E2. If E1 and E2 participate totally in R and cardinality of E1 is greater that the cardinality of E2. Which of the following is true about R? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
   a. Every entity in E1 is associated with exactly one entity in E2
   b. Some entity in E1 is associated with more than one entity in E2
   c. Every entity in E2 is associated with exactly one entity in E1
   d. Every entity in E2 is associated with at most one entity in E1
 39. Suppose, Y is an integer variable whose value is either 0 or 1. Which of the following is the equivalent of the statement. if(Y==0) Y=1; else Y=0;? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
   a. Y = 1+Y
   b. Y = 1-Y
   c. Y = Y-1
   d. Y = 1%Y


 40. I said "If I were you, I wouldn't go". The indirect speech should be ____? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) I told him not to go
   (b) I said him do not go
   (c) I advised him not to go
   (d) I requested him not to go
 41. Following table shows the delivery record of an online shop. Which of the SQL statements results in the largest value? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
| Product ID | Delivery Data | Quantity |
|---|---|---|
| F101 | 2021-03-17 | 3 |
| H201 | 2021-03-17 | 2 |
| F101 | 2021-03-16 | 1 |
| H201 | 2021-03-16 | 2 |
a. SELECT AVE(Quantity) FROM Delivery Record WHERE Product No. = 'F101'
b. SELECT COUNT (*) FROM Delivery Record
c. SELECT SUM (Quantity) FROM Delivery Record WHERE data = '2021-03-16'
d. SELECT MAX (Quantity) FROM Delivery Record
 42. ____ sun came out right after ____ rain and there was ____ beautiful rainbow in ____ sky. **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) The/the/the/a
   (b) The/a/the/the
   (c) A/a/the/a
   (d) The/the/a/the
 43. Please come in. Here 'in' is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) Preposition
   (b) Adverb
   (c) Verb
   (d) None of above
 44. 'Every now and then' means- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) Rarely
   (b) Occasionally
   (c) Frequently
   (d) Regularly
 45. The correct spelling is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) Innagurate
   (b) Inaugurate
   (c) Inagorate
   (d) Inagurate
 46. Synonym of "Bargain" is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) Dissent
   (b) Quarrel
   (c) Stipulation
   (d) Confrontations
 47. What is the Active voice of – "What she thinks was known to us" **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) We knew what she thinks
   (b) We have known about her thinking
   (c) We knew what she is thinks
   (d) We know what she thinks
 48. The famous quote "It matters not what someone is born but what they grow to be" was written in novel by the author- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) J.K Rowling
   (b) J.R.R Tolkein
   (c) Dr. Seus
   (d) W. B. Yeats
 49. "Why do you always buy five loaves, no ____ and ____?" **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) more/less
   (b) less/fewer
   (c) more/much
   (d) many/little
 50. He never thought what might come out of it, ____? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) does he
   (b) hasn't he
   (c) didn't he
   (d) did he
 51. 'কেতাদুরস্ত' বাগধারাটির অর্থ- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) পরিপাটি
   (b) অতি চালাক
   (c) অত্যন্ত অলস
   (d) অসাবধান
 52. নিচের কোন বিপরীত শব্দগুচ্ছ সঠিক নয়? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) উৎকৃষ্ট-অপকৃষ্ট
   (b) উত্তল-অবোতল
   (c) অর্বাচীন-প্রাচীন
   (d) আগ্রহ-নিগ্রহ
 53. 'দুহাতে দুই আদিম পাথর'- কার রচিত কাব্য গ্রন্থ? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) শামসুর রাহমান
   (b) আহসান হাবীব
   (c) শহীদ কাদরী
   (d) আল মাহমুদ
 54. দ্বন্দ্ব সমাসে দ্বন্দ্ব শব্দের অর্থ হল- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   (a) যুদ্ধ
   (b) জোড়া
   (c) সমোচ্চারিত
   (d) যুক্ত


 74. Which article of the constitution of Bangladesh establishes the fundamental right of education for all? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) 13
   (b) 17
   (c) 21
   (d) 27
 75. In the which sea would you find the Great Barrier Reef? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) Coral Sea
   (b) Black Sea
   (c) Aral Sea
   (d) Dead Sea
 76. Which country is called "Thunderbolt of Asia"? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) Nepal
   (b) Sri Lanka
   (c) Bhutan
   (d) Maldives
 77. The total border district of Bangladesh is- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) 29
   (b) 32
   (c) 45
   (d) 53
 78. Who has designed the logo of Mujib Year? **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) Qamrul Hasan
   (b) Hashem Khan
   (c) Sabyasachi Hazra
   (d) Nithun Kundu
 79. Name of the bank established under Bangladesh Police Welfare Trust- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) Mitual Trust Bank
   (b) Community Bangladesh Bank Limited
   (c) IFIC Bank
   (d) Trust Bank Bangladesh Limited
 80. 'Playing It My Way' is written by- **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 93]**
   (a) Sohaib Akhter
   (b) Sachin Tendulkar
   (c) Sir Don Bradman
   (d) Tiger Woods

 1. A job which is schedule to run periodically at fixed times or intervals is known as- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 99]**
   (a) Batch Job
   (b) Cron job
   (c) Shell Script
   (d) None of the above

 2. Between a client and a web server, which of the following used for inspecting the data that is sent from the client to the web server and blocking attacks such as SQL injection? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) Cluster configuration
   (b) Load balancing function
   (c) SSL-VPN function
   (d) WAF
 3. On a class B network, how many hosts are available at each site with subnet mask of 248? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) 16,382
   (b) 8,190
   (c) 4,094
   (d) 2,046
 4. Which one of the following is false with respect to 4G and 5G cellular network? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) 5G supports faster bandwidth compared to 4G.
   (b) Latency in 4G networks is much higher than 5G network.
   (c) 4G uses a narrow slice of the available spectrum from 600 MHz to 2.5 GHz
   (d) There will be data session handoff feature in 5G network which is not available in 4G network
 5. What is the propagation time for a 2.5-kbyte message (an e-mail) if the bandwidth of the network is 1Gbps? Assume that the distance between the sender and the receiver is 12,000 km and that light travels at 2.4 \times 10^8\text{ m/s}. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) 50ms
   (b) 0.020ms
   (c) 100ms
   (d) 0.040ms
 6. User passwords in Linux are stored as- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) Direct text data
   (b) Encrypted using some sort of hashing function
   (c) Encrypted using mono-alphabetic cipher
   (d) Encrypted using homophonic substitution cipher
 7. In Oracle DBMS, LGWR process is a- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) Foreground Process
   (b) Background Process
   (c) High Priority Process
   (d) Batch Process

 8. The _______ is an HFC network device installed inside the distribution hub that receives data from the internet and passes them to the combiner. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) CM
   (b) CMTS
   (c) DOCSIS
   (d) MCNS
 9. Finding useful pattern from the data in a database is known as- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Data Visualization
   (b) Data Mining
   (c) Data Analytics
   (d) All of the above
 10. _______ helps prevent power surges. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Surge suppressor
   (b) Surge protector
   (c) UPS system
   (d) High-grade multi-meter
 11. What is the API level of Android version 11? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) 24
   (b) 25
   (c) 31
   (d) None of the above
 12. .NET can be used in the following- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Development of Desktop Applications
   (b) Development of Micro services and containers
   (c) Development of Cloud Applications
   (d) All of the above statements are true
 13. What is the Internal Codename of Android version 8.0? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Red Velvet Cake
   (b) Oatmeal Cookie
   (c) Snow Cone
   (d) Jelly Bean
 14. Which of the following statements is false with respect to SSL? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Secure Sockets Layer (SSL) is a security protocol that provides privacy, authentication, and integrity to Internet communications
   (b) SSL evolved into Transport Layer Security (TLS)
   (c) SSL's final version was SSL 4.0
   (d) None of the above statements is false

 15. A circuit has two different voltage sources that are connected in a series-opposing form. If the sources are rated at 6V and 9V, what is the total source voltage? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) 3 V
   (b) 16 V
   (c) 7.5 V
   (d) 8 V
 16. What is the typical speed of USB version 3.0? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) 4.8G bits per second
   (b) 610 Mbps
   (c) 6Gbps
   (d) Both a and b
 17. Java Virtual Machine is- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) Acts as a full-fledged hypervisor
   (b) Converts bytecodes to Operating System dependent code
   (c) Is known as the Compiler of Java programming language
   (d) Manages system memory and provides a portable execution environment for Java-bases applications
 18. In which type of circuit switching, delivery of data is delayed because data must be stored and retrieved from RAM. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) Space-division
   (b) Time-division
   (c) Virtual
   (d) Packet
 19. Which one of the following statements with respect to REST API is false? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) A REST API would use a GET request to retrieve a record
   (b) A REST API would use a DELETE request to delete a record
   (c) The operations in a REST API can be called from any HTTP client
   (d) None of the above statements is false
 20. What is the maximum data rate of a channel with a bandwidth of 200 KHz if we use four levels of digital signaling? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
   (a) 400 Kbps
   (b) 800 Kbps
   (c) 1000 Kbps
   (d) 1200 Kbps
 21. SSDs are more durable than HDDs in extreme and harsh environments because **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 102]**
(a) They don't have actuator arms
(b) They use fast electronics Memory
(c) They do not use 0/1 as data storage unit which is prone to crash
(d) All of the above statements are true
 22. Which one of the following statements is false? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) Data mining is considered as a process of extracting data from large data sets
   (b) Data warehouse is the process of pooling all the relevant data together.
   (c) Data warehouse is created with the data generated by data mining for future use.
   (d) None of the above statements is false
 23. Which one of the following is a No-SQL Database? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) MongoDB
   (b) CasperDB
   (c) ZBase
   (d) All of the above
 24. If the end office receives two bursts of analog signals with frequencies of 697 and 1477 Hz, then the number ____ has been punched. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) 1
   (b) 2
   (c) 3
   (d) 4
 25. What will be the output of the following SQL "Select Round (232.420, -2) AS Round Value"? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) 240
   (b) 200
   (c) 233
   (d) Syntax error
 26. Which one of the following statements is true with respect to Printer Daemon process? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) The printer daemon of Operating System runs in kernel mode.
   (b) Jobs in the printer daemon queue cannot be removed once inserted.
   (c) Printer daemon application runs only when it is printing.
   (d) Printer daemon runs as a service in Operating System
 27. When a beam of light travels through media of two different densities, if the angle of incidence is greater than the critical angle, ____ occurs. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) Refraction
   (b) Reflection
   (c) Incidence
   (d) Criticism
 28. In the ____ protocol, the symmetric key is K= G^{xy} \pmod N, where G and N are public numbers. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) Needham-Schroeder
   (b) Otway-Rees
   (c) Diffie-Hellman
   (d) Kerberos
 29. Which of the following statements is false? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) 64-bit processor is more capable than a 32-bit processor because it can handle more data at once
   (b) A Computer works with Hexa-Decimal number system
   (c) A 32-bit system can access 232 memory addresses
   (d) None of the above statements is false

 30. Which one of the following statements is true? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Cache memory is a small amount of memory which is a part of the Random-Access memory
   (b) Cache memory is used to temporarily hold instructions and data that the CPU is likely to reuse
   (c) Cache Memory is cheaper memory
   (d) All of the above statements are true
 31. Which error detection method involves the use of parity bits? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Simple parity check
   (b) Two-dimensional parity check
   (c) CRC
   (d) a and b
 32. A DNS response is classified as ____ if the information comes from a cache memory. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Authoritative
   (b) Recursive
   (c) Unauthoritative
   (d) Iterative
 33. An email contains a textual birthday greeting, a picture of a cake, and a song. The order is not important. What is the Content-type? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Multipart/digest
   (b) Multipart/alternative
   (c) Multipart/mixed
   (d) Multipart/parallel
 34. Which one of the following statements is true with respect to a Database Management System? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Super key and candidate keys are similar
   (b) Candidate keys and Unique Keys are similar
   (c) Unique Keys and Primary Keys are similar
   (d) Candidate keys and Primary keys are similar
 35. _______ is a client-server program that provides and IP address, subnet mask, IP address of a router, and IP address of a name server to a computer. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) NAT
   (b) DHCP
   (c) CIDR
   (d) ISP
 36. The Average-case Time Complexity of the binary search algorithm is- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) O(n/2 logn)
   (b) O(n log n)
   (c) O(log n)
   (d) O(1)


 37. _______ is a standard to allow telephones on the public telephone network to talk to computers connected to the Internet. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) SIP
   (b) H.323
   (c) IEEE 802.3
   (d) V.90bis
 38. An Ethernet LAN using the OSPF protocol with five attached routers can be called a _______ network. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) Point-to-point
   (b) Stub
   (c) Transient
   (d) Virtual
 39. The term LPDDR means- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) Low-Power Discrete Data Rate
   (b) Low-processing Double Data Rate
   (c) Low-Programmable Double Data Rate
   (d) None of the above
 40. What is the maximum data rate in IEEE 802.11n? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) 300 Mbps
   (b) 600 Mbps
   (c) 1 Gbps
   (d) 832 Mbps
 41. An IPv6 basic header is fixed as- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) 32 bytes long
   (b) 40 bytes long
   (c) 64 bits long
   (d) 128-bit long
 42. The binary search algorithm is used to search for a given item when items are sorted. If the number of items is 1 million, which of the following is the closest to the maximum number of comparisons required to find the item. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) 15
   (b) 20
   (c) 25
   (d) 30
 43. What is the min and max number of tables required to convert an ER diagram with 2 entities and 1 relationship between them with partial participation constraints of both entities? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) Min 1 and max 2
   (b) Min 1 and max 3
   (c) Min 2 and max 3
   (d) Min 2 and max 2
 44. Major function of a transport layer in the OSI model is to perform **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
(a) Peer to peer message encryption
(b) Node to node message delivery
(c) Transparent transfer of data between end users
(d) None of the above
 45. At any iteration of simplex method, if \Delta_j\ (Z_j - C_j) corresponding to any non-basic variable X_j is obtained as zero, the solution under the test is- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) Degenerate solution
   (b) Unbounded solution
   (c) Alternative solution
   (d) Optimal solution
 46. Which of the following neural networks uses supervised learning? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) Multilayer perceptron
   (b) Self organizing feature map
   (c) Hopfield network
   (d) a and c
 47. Which of the following services uses both TCP and UDP ports? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) DNS
   (b) TFTP
   (c) SSH
   (d) TELNET
 48. Which of the following Linux command has incorrect syntax? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) cat sample.txt | grep -v a | sort - r
   (b) chown:group3 File 1
   (c) chmoda+rx viewer.sh
   (d) None of the above
 49. In software development, value adjustment factors include the following among others: **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) the criticality of the performance and reusability of the code
   (b) number of lines of code in the software.
   (c) number of technical manpower and hardware costs
   (d) time period available and the level of user friendliness
 50. What is the maximum size of a file allowed in Linux with the following data Block Size = 4KB, inode data pointer size = 4 byte? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) 1 TB
   (b) Less than 4TB
   (c) 2TB+2GB+2MB+64KB
   (d) More than 4 TB
 51. In a two-level memory hierarchy, the access time of the memory is 12 nanoseconds, and the access time of the main memory is 1.5 microseconds. The hit ratio is 0.98. What is the average access time of the two-level memory system? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) 13.5 nsec
   (b) 42 nsec
   (c) 7.56 nsec
   (d) 76 nsec
 52. A single switch port is considered as- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) A separate unicast domain
   (b) A separate broadcast domain
(c) A separate multicast domain
(d) A separate collision domain
 53. Which UNIX/Linux command is used to make all files and sub-directories in the directory "progs" executable by all users? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) chmod -R a+x progs
   (b) chmod -R 222 progs
   (c) chmod -X a+x progs
   (d) chmod -X 222 progs
 54. An Access point operates in which layer of OSI model? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) Data link Layer
   (b) Presentation layer
   (c) Physical layer
   (d) Transport layer
 55. Which of the following Process scheduling algorithm is highly improbable to be implemented? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) FCFS Scheduling
   (b) Priority Scheduling
   (c) Shortest Job First Scheduling
   (d) None of the above
 56. Consider the following program fragment in assembly language: **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
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
 57. How many core/threads does the Intel Core i7-9700K processor have? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) 6/12
   (b) 4/8
   (c) 8/8
   (d) 8/16
 58. Assuming the existence of a start and end nodes for a program graph (PG), the total number of Paths is equivalent to _______ set of test data required to test software. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) Minimum
   (b) Maximum
   (c) Optimum
   (d) Supreme
 59. In which year were chips used inside the computer for the first time? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) 1964
   (b) 1974
   (c) 1975
   (d) 1981

 60. Which one of the following is false with respect to cryptography? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) A symmetric key system uses only the private key
   (b) An asymmetric key system makes use of the both the public key and the private key
   (c) An Asymmetric key system is used as a Public Key Infrastructure, or PKI for sho
   (d) None of the above statements is false
 61. সামন্তবাদ কোন ইউরোপীয় দেশে প্রথম সূত্রপাত হয়? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) ইতালি
   (b) ইংল্যান্ড
   (c) ফ্রান্স
   (d) রাশিয়া
 62. ধরিত্রী সম্মেলন কোথায় অনুষ্ঠিত হয়? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) আফ্রিকার জোহানেসবার্গ
   (b) ব্রাজিলের রিওডিজেনিরোতে
   (c) ইতালির রোমে
   (d) যুক্তরাষ্ট্রের ওয়াশিংটন ডিসিতে
 63. আইওএস (IOS) মোবাইল অপারেটিং সিস্টেমটি কোন প্রতিষ্ঠান বাজারজাত করে? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) অ্যাপেল
   (b) গুগল
   (c) মাইক্রোসফট
   (d) আইবিএম
 64. The product of two positive numbers is p. If each of the numbers is increased by 2, the new product is how much greater than twice the sum of the two original numbers? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) p times
   (b) 2p times
   (c) (p+4) times
   (d) (2p+3) times
 65. A jar contains white, red and green marbles in the ratios 2:3:5 Six more green marbles are added to the jars, and then the ratio becomes 2:3:7. How many white marbles are there in the jar? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) 2
   (b) 4
   (c) 6
   (d) 8
 66. If a, b and c are 3 consecutive integers and a>b>c, which of the following has the maximum value? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) c + \frac{b}{a}
   (b) a + \frac{b}{c}
   (c) b + \frac{c}{a}
   (d) c + \frac{a}{b}
 67. One dozen eggs and ten pounds of apples are currently of the same price. If the price of a dozen eggs rises by 10% and that of apples rises by 2% how much more will it cost to buy a dozen of eggs and ten pounds of apples? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) 2%
   (b) 10%
   (c) 6%
   (d) 12%
 68. 'ব্যক্ত' শব্দের বিপরীতার্থক শব্দ কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) ত্যক্ত
   (b) গ্রাহ্য
   (c) দৃঢ়
   (d) গুপ্ত
 69. মুক্তিযুদ্ধের পটভূমিতে রচিত কাব্যগ্রন্থ কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) নেকড়ে অরণ্য
   (b) বন্দী শিবির থেকে
   (c) নিষিদ্ধ লোবান
   (d) প্রিয়তমা প্রিয়তম
 70. কাজী নজরুল ইসলামের 'অগ্নি-বীণা' কাব্যের প্রথম কবিতা কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) আগমনী
   (b) কোরবানী
   (c) প্রলয়োল্লাস
   (d) বিদ্রোহী
 71. কোনটি রবীন্দ্রনাথ ঠাকুরের কাব্যগ্রন্থ? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
   (a) শেষ লেখা
   (b) শেষ প্রশ্ন
   (c) শেষ কথা
   (d) শেষ দিন
 72. মুনীর চৌধুরীর 'মুখরা রমণী বশীকরণ' একটি- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 108]**
(a) উপন্যাস
(b) ছোটগল্প
(c) প্রবন্ধ
(d) অনুবাদ নাটক
 73. 'বন্ধন' শব্দের সঠিক অক্ষর বিন্যাস কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) ব+নদ্ধ+ন্
   (b) বন্+ধন্
   (c) ব+দ্ধ+ন্
   (d) বান্+ধন্
 74. বহুব্রীহি সমাসবদ্ধ পদ কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) জনশ্রুতি
   (b) অনমনীয়
   (c) খাসমহল
   (d) তপোবন
 75. 'বিষাদ সিন্ধু' একটি- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) গবেষণা গ্রন্থ
   (b) ধর্মবিষয়ক প্রবন্ধ
   (c) ইতিহাস আশ্রয়ী উপন্যাস
   (d) আত্মজীবনীপ
 76. বাংলা কথ্য ভাষার আদি গ্রন্থ কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) প্রভু যিশুর বাণী
   (b) কৃপার শাস্ত্রের অর্থভেদ
   (c) ফুলমণি ও করুণার বিবরণ
   (d) মিশনারি জীবন
 77. উপসর্গ কোনটি? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) অতি
   (b) থেকে
   (c) চেয়ে
   (d) দ্বারা
 78. The warning of the authority falls on deaf ears. Here warning does the function of- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) adverb
   (b) adjective
   (c) verb
   (d) noun
 79. “A rolling stone gathers no moss” The complex form of the sentence is- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) Since a stone is rolling, it gathers no moss
   (b) Though a stone roll, it gathers no moss.
   (c) A stone what rolls gathers no moss.
   (d) A stone that rolls gathers no moss.
 80. Which word is the determiner in the sentence “Will it take much time?” **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) Will
   (b) take
   (c) much
   (d) time
 81. Choose the pair of words that expresses a relationship similar to that of “Harm:Damage”= **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) Sweet:Sour
   (b) Injure:Incapacitate
   (c) Stout:Weak
   (d) Hook:Crook
 82. Which is the correct sentence? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) He insisted on seeing her
   (b) He insisted for seeing her
   (c) He insisted in seeing her
   (d) He insisted to be seeing her
 83. If a part of a speech or writing breaks the theme, it is called- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) pomposity
   (b) digression
   (c) exaggeration
   (d) anti-climax
 84. There are n students in a school. If r % among the students are 12 years or younger, which of the following expressions represents the number of students who are older than 12? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) n(1-r)
   (b) 100(1-r)
   (c) n(1-r)/100
   (d) n(100-r)/100
 85. Length of a train is 170 meters and speed of train is 63 km/hour. This train can pass a bridge in 30 seconds, then find the length of the bridge. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) 355 m
   (b) 325 m
   (c) 365 m
   (d) 312 m
 86. A wholesaler sells goods to a retailer at a profit of 20%. The retailer sells to the customer, who pays 80% more than the cost of the wholesaler. What is the retailer's profit? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) 40%
   (b) 50%
   (c) 60%
   (d) 70%
 87. If x^3 < x^2 < x then the value of x could be **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 109]**
   (a) 0
   (b) 1
   (c) 1/3
   (d) \sqrt{3}

 88. The hypotenuse of a right triangle is 2 centimeters more than the longer side of the triangle. The shorter side of the triangle is 7 centimeters less than the longer side. Find the length of the hypotenuse. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) 13
   (b) 15
   (c) 17
   (d) 19
 89. Equal amounts of water were poured into two empty jars of different capacities, which made one jar 1/4 full and the other jar 1/3 full. If the water in the jar with the lesser capacity is then poured into the jar with the greater capacity, what fraction of the larger jar will be filled with water? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) 1/3
   (b) 1/4
   (c) 1/5
   (d) 1/2
 90. গণপ্রজাতন্ত্রী বাংলাদেশের সংবিধান প্রবর্তিত হয়- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) ১৭ এপ্রিল ১৯৭১
   (b) ১৬ ডিসেম্বর ১৯৭২
   (c) ৭ মার্চ ১৯৭২
   (d) ২৬ মার্চ ১৯৭৩
 91. বঙ্গবন্ধু আগরতলা ষড়যন্ত্র মামলায় মোট আসামি সংখ্যা ছিল কতজন? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) ৩৪ জন
   (b) ৩৫ জন
   (c) ৩৬ জন
   (d) ৩২ জন
 92. আইন প্রণয়নের ক্ষমতা- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) আইন মন্ত্রণালয়ের
   (b) রাষ্ট্রপতির
   (c) স্পিকারের
   (d) জাতীয় সংসদের
 93. পার্বত্য চট্টগ্রাম শান্তিচুক্তি কত সালে স্বাক্ষরিত হয়? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) ১৯৯৬
   (b) ১৯৯৭
   (c) ১৯৯৯
   (d) ২০০১
 94. বাংলাদেশের প্রথম স্বাধীন নবাব কে? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) নবাব সিরাজউদ্দৌলা
   (b) মুর্শিদ কুলী খান
   (c) ইলিয়াস শাহ
   (d) আলাউদ্দিন হোসেন শাহ
 95. বায়ুমণ্ডলের যে স্তরে বেতার তরঙ্গ প্রতিফলিত হয়- **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) স্ট্র্যাটোস্ফিয়ার
   (b) ট্রপোস্ফিয়ার
   (c) আয়নোস্ফিয়ার
   (d) ওজোনস্তর
 96. 'কালাপানি' কোন দুই রাষ্ট্রের মধ্যে অমীমাংসিত ভূখণ্ড? **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) ভারত ও নেপাল
   (b) পাকিস্তান ও চীন
   (c) ভূটান ও ভারত
   (d) বাংলাদেশ ও ভারত
 97. Education is enlightening. Here 'enlightening' is: **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) A gerund
   (b) A participle
   (c) An infinitive
   (d) A finite verb
 98. The comparison of unlike things using the words like on as is known to be – **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) metaphor
   (b) simile
   (c) alliteration
   (d) personification
 99. In English grammar, _______ deals with formation of sentences. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) Morphology
   (b) Etymology
   (c) Syntax
   (d) Semantics
 100. Give the antonym of the word 'transitory'. **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 110]**
   (a) temporary
   (b) permanent
   (c) transparent
   (d) short-lived
 101. A database can be hacked by- **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 110]**
   a) Exploiting weak passwords
   b) SQL Injection
   c) Delivering a Trojan
   d) All of the above
 2. Which of the following is not a DDL command? **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Create
   b) Drop
   c) Alter
   d) Update
 3. Business Intelligence (BI) reporting analyses can be performed using **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) standard SQL only
   b) extensions to SQL only
   c) OLAP only
   d) Both standard SQL and extensions to SQL
 4. The SQL statement **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
```sql
SELECT ROUND (45.926, -1) FROM DUAL;

```
a) is illegal
b) prints garbage
c) prints 045.926
d) prints 50
 5. Assume that you want to improve database performance and willing to see the amount of swap space. Which command you can use in LINUX OS environment? **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Lsps -a
   b) Swapinfo -m
   c) Swapon -s
   d) Swap -l and Swap -s
 6. In oracle to change the DB_Block_size parameter, you need to- **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Re-create the database
   b) Alter the database
   c) Move database to temporary
   d) Update the table types of the database
 7. Which of the following controls the execution of application program and UI in two tier client/server architecture? **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Modulation side
   b) Server side
   c) Host side
   d) None of the above
 8. Which one of the following is a failure to a system? **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Boot crash
   b) Read failure
   c) Transaction failure
   d) All of the mentioned
 9. Referential integrity in a DBMS is a form of- **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Foreign key
   b) Primary key
   c) Assertion
   d) Referential constraint
 10. How can your rollback a committed transaction in any DBMS? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) Using SQL rollback commands
   b) Restoring the data from backups
   c) Run the transaction again in Reverse order
   d) All of the Above
 11. In a schema with attributes A, B, C, D and F following set of functional dependencies are given A => B, A=>C, CD=> E, B=>D, E=>A. Which of the following functional dependencies is not implied by the above set? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) CD=>AC
   b) BD=>CD
   c) BC=>CD
   d) AC=>BC
 12. Let E1 and E2 be two entities in an E/R diagram with simple single-valued attributes. R1 and R2 are two relationships between E1 and E2, where R1 is one-to-many and R2 is many-to-many. R1 and R2 do not have any attributes of their own. What is the minimum number of tables required to represent this situation in the relational model? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) 2
   b) 3
   c) 4
   d) 5
 13. LGWR process writes information into- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) Database files
   b) Control Files
   c) Redo log Files
   d) All of the above

 14. Which of the following is an appropriate category of system maintenance performed for the purpose of modifying the system to cope with changes in the software environment? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Preventive maintenance
   b) Corrective maintenance
   c) Adaptive maintenance
   d) Perfective maintenance
 15. What are the different events in Triggers? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Define, Create
   b) Drop, Comment
   c) Insert, Update, Delete
   d) Select, Commit
 16. XSLT processors evaluate each statement in the context of the match that has been made. That is, XSLT processors are: **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Context oriented
   b) Procedural oriented
   c) Object oriented
   d) Relational oriented
 17. The packaged procedure that makes data in form permanent in the Database is- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Post
   b) Post form
   c) Commit form
   d) None of the above
 18. When three or more AND & OR conditions are combined, it is easier to use the SQL keyword(s): **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) LIKE only
   b) IN only
   c) NOT IN only
   d) Both IN and NOT IN
 19. How to select all data from student table starting the name from letter 'r'? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) SELECT * FROM student WHERE name LIKE 'r%';
   b) SELECT * FROM student WHERE name LIKE '%r%';
   c) SELECT * FROM student WHERE name LIKE '%r';
   d) SELECT * FROM student WHERE name LIKE '_r%';
 20. Needing to assess the validity of assumed referential integrity constraints on foreign keys is a(n) _________ of normalization. **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) advantage
   b) disadvantage
   c) either an advantage or disadvantage
   d) neither an advantage nor disadvantage

 21. Data integrity problems in a DBMS is caused due to- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Missing Data
   b) Data inconsistency
   c) Data Redundancy
   d) Security constraints
 22. A collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints, is known as- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Data organization
   b) Data Binding
   c) Data schemas
   d) Data models
 23. The fastest read/write time and most efficient data storage of any disk array type is: **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) RAID-0
   b) RAID-1
   c) RAID-2
   d) RAID-3
 24. Which of the following is an appropriate description of the mapping between the relational model and relational database as its implementations? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) A domain is mapped to a character type or a character string type.
   b) A relation is mapped to a table
   c) Attributes and columns are ordered from left to right
   d) Neither tuples nor rows have duplicates
 25. How can you generate debugging output from PL/SQL? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) DBMS_SQL
   b) DBMS_OUTPUT
   c) DBMS_PIPE
   d) DBMS_LOB
 26. What is GET_BLOCK property? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Restricted procedure
   b) Unrestricted procedure
   c) Library function
   d) None of the above
 27. Which of these is not a common reason businesses choose to go with a data center colocation service for disaster recovery instead of building a new data center? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Full control of hardware
   b) Security and location
   c) Granular climate control
   d) Cost of building data centers
 28. Which of the following are the five built-in functions provided by SQL? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) COUNT, SUM, AVG, MAX, MIN
   b) SUM, AVG, MIN, MAX, MULT
   c) SUM, AVG, MULT, DIV, MIN
   d) SUM, AVG, MIN, MAX, NAME
 29. Which of the following is a technique for hiding the internal implementation details of an object? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Encapsulation
   b) Polymorphism
   c) Inheritance
   d) All of the above
 30. ROLLBACK command is used to undo the changes made by- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) DDL commands
   b) TCL commands
   c) DML Commands
   d) Commit command
 31. Embedded SQL is which of the following? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Hard-coded SQL statements in a program language such as Java.
   b) The process of making an application capable of generating specific SQL code on the fly
   c) Hard-coded SQL statements in a procedure.
   d) Hard-coded SQL statements in a trigger.
 32. In a comparatively small organization if you want data forwarding among departments based on IP address which one of the following will be a better bet for networking? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Using Layer-3 routers
   b) Using Layer-3 switches
   c) Using Unmanaged switches
   d) Combining a and b
 33. A star schema has what type of relationship between a dimension and fact table? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Many-to-many
   b) One-to-one
   c) One-to-many
   d) All of the above
 34. What does this query do? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
```sql
SELECT employee_number, name FROM
employees AS Parent WHERE salary> (SELECT AVG (salary)
FROM employee WHWRE department= Parent department) ,

```
a) Finds the name and ID of employees who get more than average
b) Finds the employee's name and ID of those who gets more than average salaries of all the departments' salaries.
c) Finds the name and ID of employees who get more than average salaries of his own department.
d) None
 35. What is invoked via HTTP on the Web server computer when it responds to requests from a user's Web browser? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) A Java application
   b) A Java applet
   c) A Java servlet
   d) None of the above is correct
 36. How does RAID provide data protection? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Using either data mirroring or parity
   b) Using either data mirroring or striping
   c) Using high quality disk drives
   d) Using dedicated data protection hardware
 37. A DNS client is called a ____________ **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) DNS updater
   b) DNS resolver
   c) DNS handler
   d) DNS host
 38. Which of the following is correct for the Create index command? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Insert index index_name on table_name
   b) Insert index index_name on database_name;
   c) Create index index_name on database_name;
   d) Create index index_name on table_name;
 39. Third normal form is based on the concept of ______. **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Normal Dependency
   b) Closure Dependency
   c) Functional Dependency
   d) Transitive Dependency
 40. Which one of the following is true for a tuple in a database? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) A tuple in a database represents a column
   b) A tuple in a database represents database schema.
   c) A tuple in a database represents a Record
   d) A tuple in a database represents a Database topology
 41. Which of the following is not a nonvolatile storage device? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Memory Stick
   b) Hard Disk
   c) Random Access Memory
   d) NVRAM
 42. In an asymmetric key encryption process, the key used to encrypt the data is known as a- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Private key
   b) Encryption key
   c) Public key
   d) Modulation key
 43. Why is set transaction used in an oracle DBMS? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) For placing a name on a transaction
   b) For committing a transaction
   c) For locking a transaction
   d) To setup transaction user parameters.
 44. Which is the oracle component that contains the memory structures and background process? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Instance
   b) Server
   c) SGA
   d) Database files
 45. The three different application logic components are which of the following? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Presentation, Client, and Storage
   b) Presentation, Client, and Processing
   c) Presentation, Processing, and Storage
   d) Presentation, Processing, and Network
 46. Which of the following is not a factor in determining the concurrency control behavior of SQL Server? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Lock level
   b) Transaction isolation level
   c) Cursor concurrency setting
   d) Locking hints
 47. In a DBMS, when multiple transaction programs update the same database simultaneously, which of the following is a technology that is used to prevent logical contradictions? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Exclusive Control
   b) Integrity constraint
   c) Normalization
   d) Reorganization
 48. The Application program interface in a two-tier architecture DBMS is provided by- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Close module connectivity
   b) Open module connectivity
   c) Open database connectivity
   d) Close database connectivity
 49. Which of the below is responsible for controlling the interaction among simultaneous transaction? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Serializable controller
   b) Concurrency Control Manager
   c) Transportation management system
   d) Multiple Access Protocol
 50. Of the functions provided by a DBMS. Which of the following is a means for achieving protection for data confidentiality? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Checking referential constraints when the data is updated
   b) Managing a transaction that combines a series of processes as a logical Unit.
   c) Managing the data access rights of users.
d) Placing an exclusive lock on the data before it is updated
 51. Which is not the UTL_FILE function- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) FOPEN()
   b) File_Close()
   c) FCOPY
   d) FFLUSH()
 52. In strict two phase locking protocol- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) All exclusive mode locks taken by transaction be held until transaction commit
   b) All exclusive mode locks taken by transaction can be released before transaction commits
   c) All locks can be released before transaction commits
   d) None of these
 53. The maximum number of super keys for the relation schema R (E, F, G, H) with E as the key is- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) 5
   b) 6
   c) 7
   d) 8
 54. Oracle materialized views or SNAPSHOTS is used- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Hiding data from users
   b) Dynamic data replication
   c) Table Space Reduction
   d) Data Abstraction
 55. A distributed database has which of the following advantages over a centralized database? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Software cost
   b) Software complexity
   c) Slow Response
   d) Modular growth
 56. Database index speeds up- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Select queries
   b) Where clauses
   c) Update query
   d) Both a and b
 57. Which of the following index is automatically created by the database server when an object is created? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Implicit
   b) Single column
   c) Unique
   d) composite
 58. We are waiting for the bus The underlined part is ______. **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) A noun phrase
   b) An infinitive phrase
   c) A prepositional phrase
   d) A verb phrase
 59. Fill in the blank with correct preposition. He is devoid ______ Commonsense. **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Of
   b) From
   c) Introduction
   d) At
 60. Complete the following sentence ‘Had I known you were waiting outside, I ______ **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Had invited you to come in
   b) Would invite you to come in
   c) Would be inviting you to come in
   d) Would have invited you to come in
 61. What is the meaning of “White Elephant”? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) An elephant of white color
   b) A hoarder
   c) A black Marketer.
   d) A very costly or troublesome possession
 62. A floor with dimension of 20 feet to 35 feet is needed to be tiled. Two workers can tile that floor in 2 hours and 30 minutes. If they are joined by three other workers of similar ability. How many hours will it take to tile the floor? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) 1 hr
   b) 1.25 hr
   c) 1.5 hr
   d) 1.75 hr
 63. Choose the appropriate meaning of the idiom ‘swan song’ **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) First Work
   b) Last Work
   c) Middle Work
   d) Early Work
 64. A train went 300 km from city X to city Y at an average speed of 100 km/h. At what speed did it travel on the way back if its average speed for the whole trip was 120 km/h. **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 120 km/h
   b) 125 km/h
   c) 130 km/h
   d) 150 km/h
 65. A lamp is manufactured to sell for $35.00, which yields a profit of 25% of cost. If the profit is to be reduced to 15% of cost, what will be the new retail price of the lamp? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) $21.00
   b) $28.00
   c) $31.50
   d) $32.20
 66. A leading library charges c cents for the first week that a book is loaned and f cents for each day over one week. What is the cost for taking out a book for days, where d is greater than 7? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) C+f(d-7)
   b) C+fd
   c) cd
   d) Cd+f
 67. A boat sailing against a stream of river takes 6 hours to travel 24 kms, while sailing with the stream it takes 4 hours to travel the same distance. What is the speed of the stream? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 2.5 km/hr
   b) 1.5 km/hr
   c) 1 km/hr
   d) 0.5 km / hr
 68. Which one of the following words is masculine? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) Mare
   b) Lad
   c) pillow
   d) Pony
 69. Love for the whole world is called ______ . **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) Philanthropy
   b) Misogyny
   c) Benevolence
   d) Misanthropy
 70. Who did write first English dictionary? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) Boswell
   b) Ben Jonson
   c) Samuel Johnson
   d) Milton
 71. Choose the correct spelling- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) Ascertain
   b) Ascertain
   c) Ascertain
   d) Asartain
 72. Misanthropist means- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) One who flirts with ladies
   b) A person of narrow views
   c) A hater of mankind
   d) One who believe that God is in everything
 73. A manufacturer sells three products i.e. A, B and C Product A costs 200 and sells for 250. Product B costs 150 and sells for 180, product C costs 1000 and sells for 110. On which product, he has maximum percentage of profit? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) B only
   b) A and B both
   c) A only
   d) C only
 74. Three boys have marbles in the ration of 19:5:3. If the boy with the least number has 9 marbles, how many marbles does the boy with the highest number have? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 23
   b) 37
   c) 45
   d) 57
 75. In a Group of 15, 7 can speak Spanish, 8 can speak French and 3 can speak neither. What fraction of the group can speak both French and Spanish? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 1/5
   b) 4/15
   c) 1/3
   d) 7/15
 76. In distributing milk at a summer camp, it is found that a quart of milk will fill wither 3 large glass tumblers or 5 small glass tumblers. How many small glass tumblers can be filled with one large glass tumbler? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 11/5
   b) 7/5
   c) 5/3
   d) 7/3
 77. The triangular base of a prism is a right triangle of sides a and b =2a. The height h of the prism is equal to 10mm and its volume is equal to 40 mm³. What will be the lengths of the sides a and b of the triangle? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 119]**
   a) 2mm and 3mm
   b) 1 mm and 4 mm
   c) 2 mm and 2 mm
   d) 2 mm and 4 mm
 78. তুমি আসবে বলে হে স্বাধীনতা সখিনা বিবির কপাল ভাঙল। এটি কোন বাক্য? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) সরল
   b) মিশ্র বা জটিল
   c) যৌগিক
   d) সংযুক্ত
 79. সমাসবদ্ধ শব্দ আনত কোন সমাসের উদাহরণ? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) বহুব্রীহি
   b) কর্মধারয়
   c) অব্যয়ীভাব
   d) সবগুলো
 80. বৈষ্ণব পদাবলির সঙ্গে কোন তথ্য সম্পর্কিত? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) সন্ধ্যাভাষা
   b) অভিভাষা
   c) ব্রজবুলি
   d) সংস্কৃত ভাষা
 81. সহচর শব্দের শুদ্ধ গঠন কোনটি? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) সম+চর+র্য
   b) সহচর+ৎ ফলা
   c) সহচর+য
   d) কোনটি নয়
 82. চৌ-হদ্দি শব্দটি কোন কোন ভাষার শব্দ মিলে হয়েছে? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) বাংলা + ফারসি
   b) সংস্কৃত + ফারসি
   c) ফারসি + আরবি
   d) সংস্কৃত + আরবি
 83. বাংলাদেশে প্রথম জাতীয় সংসদের নির্বাচন কখন হয়? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ৭ ফেব্রুয়ারী ১৯৭৩
   b) ৭ জানুয়ারি ১৯৭৩
   c) ৭ মার্চ ১৯৭৩
   d) ৭ এপ্রিল ১৯৭৩
 84. টেস্ট ক্রিকেটে বাংলাদেশের পক্ষে কে প্রথম ডাবল সেঞ্চুরি করেন? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) মুশফিক
   b) তামিম
   c) সাব্বির
   d) লিটন দাস
 85. স্টিফেন হকিং একজন- **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) দার্শনিক
   b) পদার্থবিদ
   c) কবি
   d) রসায়নবিদ
 86. চীনের জিনজিয়াং প্রদেশে বসবাসকারী প্রধান মুসলিম সম্প্রদায়ের নাম কি? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) তুর্কমেন
   b) উইঘুর
   c) কাজখ
   d) তাজিক
 87. EDSAC কম্পিউটার এ ডাটা সংরক্ষণের জন্য কি ধরণের মেমরি ব্যবহার হত? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) RAM
   b) ROM
   c) Mercury Delay
   d) Registers Lines
 88. শিব রাত্রির সলতে- বাগধারাটির অর্থ কী? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) শিবরাত্রির আলো
   b) একমাত্র সম্বল
   c) একমাত্র সন্তান
   d) শিবরাত্রির গুরুত্ব
 89. ‘কোন পান্থ ক্ষান্ত হও হেরি দীর্ঘ পথ’- কার লেখা? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) কৃষ্ণচন্দ্র মজুমদার
   b) ঈশ্বরচন্দ্র গুপ্ত
   c) কামিনী রায়
   d) যতীন্দ্রমোহন বাগচী
 90. বাংলা গদ্যের জনক কে? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ঈশ্বরচন্দ্র বিদ্যাসাগর
   b) বঙ্কিমচন্দ্র চট্টোপাধ্যায়
   c) উইলিয়াম কেরি
   d) রবীন্দ্রনাথ ঠাকুর
 91. বাংলা ভাষার আদি নিদর্শন চর্যাপদ আবিষ্কৃত হয় কত সালে? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ২০০৭
   খ) ১৯০৭
   c) ১৯০৯
   d) ১৯১৬
 92. বাংলা কথ্য ভাষার আদি গ্রন্থ কোনটি? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) প্রভু যিশুর বাণী
   b) কৃপার শাস্ত্রের অর্থভেদ
   c) ফুলমণি ও করুণার
   d) শিনারি জীবন বিবরণ
 93. কত সালে আওয়ামী লীগের ৬দফা পেশ করা হয়েছিল? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ১৯৬৬ সালে
   b) ১৯৬৭ সালে
   c) ১৯৬৮ সালে
   d) ১৯৬৯ সালে
 94. নির্বাহী বিভাগ থেকে বিচার বিভাগ পৃথক করার বিষয়টি সংবিধানের কোন অনুচ্ছেদে উল্লেখ রয়েছে? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) অনুচ্ছেদ ২৩b) অনুচ্ছেদ ২৪
   c) অনুচ্ছেদ ২১
   d) অনুচ্ছেদ ২২
 95. ১৯৫৪ সালে পূর্ব পাকিস্তান প্রাদেশিক পরিষদ নির্বাচনে যুক্তফ্রন্টের কি প্রতীক ছিল? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ধানের শীষ
   b) নৌকা
   c) লাঙ্গল
   d) বাইসাইকেল
 96. সলোমন দ্বীপপুঞ্জ কোন মহাসাগরে অবস্থিত? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) ভারত মহাসাগর
   b) প্রশান্ত মহাসাগর
   c) অ্যাটলান্টিক মহাসাগর
   d) আকটিক মহাসাগর
 97. বিশ্বব্যাংক সংশ্লিষ্ট কোন সংস্থাটি স্বল্প আয়ের উন্নয়নশীল দেশে বেসরকারি খাতে আর্থিক সহায়তা ও উপদেশ দিয়ে থাকে? **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 120]**
   a) IBRD
   b) MIGA
   c) IFC
   d) ICSID
 1. ‘ক্ষুধপিপাসা’ শব্দের সন্ধি বিচ্ছেদ কী? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. ক্ষুদ + পিপাসা
   b. ক্ষুধ + পিপাসা
   c. ক্ষুত্ + পিপাসা
   d. খুদ্ + পিপাসা
 2. সঠিক সন্ধি বিচ্ছেদ কোনটি? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. মনঃ + কষ্ট = মনোকষ্ট
   b. চক্ষু + রো
   c. পরি + কার = পরিষ্কার
   d. ইতঃ + মধ্যে
 3. ‘কানে-কলম’ কোন সমাসের উদাহরণ? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. উপপদ তৎপুরুষ
   b. অলুক দ্বন্দ্ব
   c. প্রত্যয়ান্ত বহুব্রীহি
   d. অলুক বহুব্রীহি
 4. ‘চৌরাস্তা’ কোন সমাসের উদাহরণ? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. দ্বিগু কর্মধারায়
   b. সংখ্যাবাচক বহুব্রীহি
   c. অলুক বহুব্রীহি
   d. সমানাধিকরণ বহুব্রীহি
 5. কারক ও বিভক্তি নির্ণয় করুন: কাননে কুসুমকলি সকলি ফুটিল। **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. কর্তায় শূন্য
   b. কর্মে শূন্য
   c. করণে দ্বিতীয়
   d. অপাদানে দ্বিতীয়
 6. ‘প্রিয়জনে যাহা দিতে চাই তাই দিই দেবতারে’। কারক ও বিভক্তি নির্ণয় করুন। **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. কর্তায় সপ্তমী
   b. কর্মে সপ্তমী
   c. সম্প্রদানে ষষ্ঠী
   d. সম্প্রদানে ষষ্ঠী
 7. এক কথায় প্রকাশ করুন: অক্ষির অভিমুখে— **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. প্রত্যক্ষ
   b. পরোক্ষ
   c. সমক্ষ
   d. চাক্ষুস
 8. কোন শব্দগুচ্ছের বানান শুদ্ধ? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. রুগ্ন, শিহরণ, বাল্মীকি
   b. অদ্যাবধি, তিরস্কার, ধরণ
   c. দারুন, দৈন্যতা, বৈচিত্র
   d. জাত্যাভিমান, ব্রহ্মপুত্র, প্রবেশক
 9. বিদেশাগত বাংলা শব্দের ভিন্ন জাতীয় শব্দগুচ্ছ কোনটি? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. পোশাক-পছন্দ-হিসাব
   b. আড়ু-রং-মোরগ
   c. আলাদা-লোকসান-জেলা
   d. দোকান-শনাক্ত-নিশান
 10. নিচের কোন বাগধারাটি ব্যতিক্রম? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. বিড়াল তপস্বী
   b. বক ধার্মিক
   c. ভিজে বিড়াল
   d. ধর্মপুত্র যুধিষ্ঠির
 11. ‘তীক্ষ্ণ’ শব্দের যুক্তব্যঞ্জনের সঠিক বিশ্লেষণ কোনটি? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. ক+ষঞ্চ
   b. ক্+ষ্ণ+ন
   c. ক্+ষ+ম
   d. ক্+হ+ণ
 12. ‘Graphic’ এর বাংলা পরিভাষা কী? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. নকশা
   b. রৈখিক
   c. কসড়া
   d. অঙ্কন
 13. কোনটি মৌলিক শব্দ? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. বাঁশি
   b. মা
   c. তেল
   d. জলধি
 14. বিপরীতার্থক শব্দের ক্ষেত্রে নিচের কোনটি ভুল? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. অমৃত-গরল
   b. তস্কর-সাধু
   c. কৃশ-মূল
   d. আর্বাচীন-আধুনিক
 15. “Every man is for himself” এর সঠিক বাংলা অনুবাদ কী? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 121]**
   a. ইচ্ছা থাকলে উপায় হয়
   b. চাচা আপন প্রাণ বাঁচা
   c. প্রত্যেকে আমরা পরের তরে
   d. সবার উপরে মানুষ সত্য
 16. “যে পরিশ্রম করে, সে-ই সুখলাভ করে”। কোন ধরনের বাক্য? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. মিশ্র বাক্য
   b. সরল বাক্য
   c. যৌগিক বাক্য
   d. ব্যাস বাক্য
 17. ‘শোকার্ত তরবারী’ কাব্যগ্রন্থের রচয়িতা কে? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. শামসুর রহমান
   b. আল মাহমুদ
   c. হাসান হাফিজুর রহমান
   d. নির্মলেন্দু গুণ
 18. মহাকাব্যিক উপন্যাস নয় কোনটি? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. সংশপ্তক
   b. গায়ত্রী সন্ধ্যা
   c. আগুন পাখি
   d. জাহান্নাম হইতে বিদায়
 19. ‘বিমলা-কুমুদিনী’ কোন দুটি উপন্যাসের কেন্দ্রীয় চরিত্র? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. ঘরে-বাইরে, যোগাযোগ
   b. চতুরঙ্গ, যোগাযোগ
   c. ঘরে-বাইরে, শেষের কবিতা
   d. চোখের বালি, শেষের কবিতা
 20. মোহাম্মদ নাসিরউদ্দিন কোন পত্রিকা সম্পাদনা করেছিলেন? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. মোসলেম ভারত
   b. প্রগতি
   c. সওগাত
   d. সমকাল
 21. ________ opportunity comes responsibility. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. From
   b. Before
   c. without
   d. With
 22. ________ the year 2014 and 2019, I was a student of University of Dhaka. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. From
   b. Except
   c. Between
   d. Both
 23. Are you sure that you ________ the killer before? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. will have seen
   b. had seen
   c. would have seen
   d. must have seen
 24. I have enrolled of ________ European University. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. a
   b. an
   c. the
   d. no article
 25. What is the antonym of “Segregate”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. isolate
   b. combine
   c. divide
   d. severs
 26. The Children were too flabbergasted ________. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. so they could not speak
   b. that they started speaking
   c. to speak
   d. to stop speaking
 27. Good morning, ________ see the manager, please. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. am interested to
   b. wish I can
   c. like to
   d. would like to
 28. There was somebody waling behind us. I thought we ________. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. were following
   b. were being followed
   c. were followed
   d. have been followed by somebody
 29. You have been working since morning ________. (You have) your lunch yet? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. do you have
   b. have you
   c. have you had
   d. did you have
 30. Which of the following has the similar sound of the word “won”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. own
   b. one
   c. on
   d. un
 31. What is the noun form the word “defer”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. defer
   b. deferment
   c. deference
   d. different
 32. Choose the correct sentence. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. She disguised herself lest she be recognized
   b. She was disguised lest she should be recognized
   c. She disguised lest she be recognized
   d. She disguised herself lest the can be recognized
 33. What is the verb form of the word “Acquisition”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 122]**
   a. acquiesce
   b. acquisition
   c. acquire
   d. aquifer
 34. Choose the correct sentence. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. No sooner he graduated he got a job
   b. No sooner had he graduated than he got a job
   c. No sooner had he graduated then he had got a job
   d. No sooner he had graduated he got a job
 35. What is the synonym of the word “Erudite”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. knowledgeable
   b. angry
   c. illiterate
   d. smart
 36. Choose the correct translation of the sentence- “You should fight shy of an evil company”. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. তোমার খারাপ সংস্থা থেকে দূরে থাকা উচিত
   b. তোমার খারাপ সংস্থার লোকদের সাথে মারামারি করা উচিত
   c. তোমার বাজে লোকদের সাথে মারামারি করা উচিত
   d. তোমার বাজে সঙ্গ এড়িয়ে চলা উচিত
 37. Choose the correct spelling. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. Onomatopeia
   b. Onamatopoeia
   c. Onamotopoeia
   d. Anomatopoeia
 38. I am feeling under the water. What does the underlined phrase mean? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. Felling very cold
   b. Traumatized
   c. Showing sign of torture
   d. Feeling slightly ill
 39. I would have made sure Rana was here ______ were coming. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. if I have known you
   b. if I knew you
   c. if I had known you
   d. when I had known
 40. Choose the correct sentence. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. The kid likes to watch cartoons and eating chocolates
   b. The kid likes watching cartoons and to eat chocolates
   c. The kid likes watching cartoons and eating chocolates
   d. The kid like watching cartoons and eating chocolates
 41. It takes 5 hours to fill a container using machine A. The same container can be filled suing Machin B in 10 hours. When the container is full, Machine C can fully empty the container in 20 containers how long will it take for the container to be completely filled? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 1/4 hours
   b. 4 hours
   c. 2 hours
   d. 15 hours
 42. Two trucks 300 km away are travelling towards each other with a constant speed. Truck A is moving at a constant speed of 50 km/h. How long does it take for them to meet? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 5 hours
   b. 3 hours
   c. 2.5 hours
   d. 6 hours
 43. If 12 men work on a particular task. it takes them 24 days to complete it. On the other hand, 12 women can complete the same task in 12 days. How many days it takes if the 12 men and 12 women cooperated with each other to finish to finish the same task? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 5 days
   b. 6 days
   c. 8 days
   d. 16 days
 44. Ahmed sold a t-shirt for TK. 810, and gain 8%. How much did he purchase it for? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. Tk. 750
   b. Tk. 875
   c. Tk. 745
   d. Tk. 756
 45. x+y=535, x+4y=4, what is the value of 4x² + 20xy + 16y²? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 60
   b. 40
   c. 20
   d. 80
 46. A restaurant makes 20% profit after selling a set menu at a discount of 20%. What is the percentage increase of marked price? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 30%
   b. 20%
   c. 40%
   d. 50%
 47. If a² - b² = 20, a+b= 5, What is the value of a-b? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 123]**
   a. 3
   b. 15
   c. 5
   d. 4
 48. You are looking at a billboard 40m away with an angle of elevation of 30⁰. At what height is the billboard? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 20
   b. 30
   c. 40
   d. 80
 49. What is the probability of getting a sum of six if two dices are thrown at one? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 5/36
   b. 7/36
   c. 2/26
   d. 1/36
 50. A ladder against a wall that tis perpendicular to the ground. If the bottom of the ladder is 4m away from the bottom of the wall, while the tip of the ladders is at a height of 3m, what is the length of the ladder? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 7 m
   b. 35 m
   c. 5 m
   d. 25 m
 51. In a room of 36 people, 20 players play chess while 28 players play poker. How many players pay both? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 48
   b. 20
   c. 12
   d. 28
 52. A fair six-sided die is rolled. Find the probability of getting an odd number or a number less than 4. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 2/3
   b. 2/4
   c. 5/6
   d. 1/6
 53. How many positive integers less than ten thousand are multiples of both eight and eighteen? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 70
   b. 72
   c. 138
   d. 139
 54. The H.S.F and L.C.M of two number are 12 and 288 respectively. If one of the numbers is 96, find the other. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 34
   b. 36
   c. 38
   d. 40
 55. The ratio of male students to female students in a class is 13 to 19. If there are 224 people in the class, including one teacher, one administrator, and thirty evaluators, how many people in the class are male students? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 78
   b. 80
   c. 91
   d. 114
 56. 5 years ago the ration of father's age to son's age was 5:1 and 2 years later father's age will be 3 times his son's age. What is the ration of their present age? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 5:2
   b. 7:3
   c. 10:3
   d. 11:7
 57. What is the value of a, if 3x² + ax + a + 3 is divisible by x+2? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 12
   b. 13
   c. 14
   d. 15
 58. A vegetable cart sells a potato for $0.24 and a tomato for $0.76. Fred bought 12 vegetables in total. He only bought potatoes and tomatoes. If Fred paid $ 6.52 total, how many potatoes did he buy? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 2
   b. 7
   c. 5
   d. 8
 59. A train 220 m long is moving at 45km/h. The time taken by the train to cross a tunnel 260m long. Is **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. 25 sec
   b. 35 sec
   c. 38 sec
   d. 40 sec
 60. Who was the first English translator of Bangladesh national anthem? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. Syed Ahsan Kabir
   b. Kamrul Hasan
   c. Syed Ali Ahsan
   d. Rabindranath Tagore
 61. The factors of 4x⁴ + 1 is- **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. (2x² + 2x + 1) (2x² + 3x - 1)
   b. (2x² + 3x + 1)(2x² + 3x - 1)
   c. (2x² + 3x + 1) (2x² - 3x + 1)
   d. (2x² + 3x + 1) (2x² - 2x + 1)
 62. Which was the world's first electronic computer? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 124]**
   a. ENIAC
   b. EDVAC
   c. UNIVAC
   d. IBM
 63. Who is the new secretary General of BIMSTEC? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Saroj Chavanaviraj (Thailand)
   b. Summit Nakandala (Sri Lanka)
   c. M. Shohidul Islam (Bangladesh)
   d. Tenzin Lekphel (Bhutan)
 64. Who is the writer of the book named A Promise Land? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Joe Biden
   b. Donald Trump
   c. Bill Clinton
   d. Barack Obama
 65. According to the ‘Sustainable Development goals (SFG) Index 2020’ Bangladesh has been ranked ________ **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. 153th
   b. 109th
   c. 104th
   d. 123th
 66. In the keyboard of a computer processing F8 Key for three times selects? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. A paragraph
   b. A sentence
   c. Entire document
   d. A word
 67. Which word is named as “Word of the year 2020” in Cambridge Dictionary? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Lockdown
   b. Quaranitine
   c. Pandemic
   d. Sanitizer
 68. Which one was the Naval Sector in the liberation war of Bangladesh? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. 8
   b. 9
   c. 10
   d. 11
 69. Which project of Bangladesh is related to the concept of “One city Two Towns”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Padma Bridge
   b. Metro Rail
   c. Kuril Flyover
   d. Karnaphuli River tunnel
 70. Dead sea is a ________ **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Sea
   b. River
   c. Lake
   d. Canal
 71. “Concurrent two-factor identity verification” is a biometric identification system that would requires ________. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. finger print and national identity
   b. facial identity and finger print
   c. eye sightedness and blood sample
   d. facial identity and facial motion
 72. Recently HPM record award at UN for ________. **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. SDG
   b. Climate Change
   c. MDG
   d. Women Empowerment
 73. Which of the following is the Scandinavian Country? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Norway
   b. Sweden
   c. Netherland
   d. Denmark
 74. Where did Leandso dis Vind draw his farmers from “The Last Supper”? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Rome
   b. Milan
   c. Venice
   d. Florence
 75. What is the noun of the extent Rover sent by NASA to the man? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. Superior
   b. Opporunity
   c. Perseverance
   d. Sprit
 76. Which of the SDG google speaks about women empowerment? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
   a. SDG 5
   b. SDG 3
   c. SDG 9
   d. SDG 8
 77. In which district the ‘Tin Bigha Corridor’ is located? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
 78. Which Bangladeshi has been awarded the ‘Padma Bhushan 2020’ by the government of India? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
 79. According to WEF’s (World Economic forum) Global Gender Gap Report. what is the ranking of Bangladesh in South Asia? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
 80. What was the theme for the 6th BRICS-Youth summit 2020? **(National Security Intelligence (NSI) Assistant Programmer 08.10.2021) [compact it 125]**
 1. A system has 12 magnetic tape drives and 3 processes: PO, PI, and P2. Process PO requires 10 tape drives, P1 requires 4 and P2 requires 9 tape drives. The current allocation tape drives of processes P0, PI and P2 is 5, 2, 2, respectively. Which of the following sequence is a safe sequence? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) P0, PI, P2
   b) P1, P2, P0
   c) P2, P0, P1
   d) P1, P0, P2
 2. What is the network address for the IP address 178.112.13.10/8? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) 178.0.0.0
   b) 178.112.0.0
   c) 255.0.0.0
   d) 255.255.0.0
 3. Which RAID level creates a mirror of all disks for storing data? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) RAID Level 0
   b) RAID Level 1
   c) RAID Level 2
   d) RAID Level 3
 4. NIC Stands for– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Network Interface Card
   b) Network Interface Circuit
   c) Network Internal Card
   d) Network Input Card
 5. In the priority queue, insertion and deletion take place at – **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Front and rear end
   b) Only at the front end
   c) Only at the rear end
   d) Any position
 6. In Unix operating system, which system call is used for creating a new process? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Exec()
   b) Create Process ()
   c) Fork ()
   d) None of them
 7. Which type of JOIN operation in SQL command is used to returns that do not have matching values? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Natural Join
   b) EQUI Join
   c) Outer Join
   d) All of the above
 8. Consider a magnetic disk packed with 32 surfaces. Each surface is divided into 128 tracks while 256 sectors per track. If the size of a sector is 1024 bytes, then what is the total capacity of the disk? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) 2³⁰ bytes
   b) 2³³ bytes
   c) 2²⁷ bytes
   d) 2²⁰ bytes
 9. Which is the correct definition of BUG? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) A difficult syntax error in a program
   b) A logical error in a program
   c) Documenting programs
   d) All of the above
 10. How can you clear CMOS password? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Changing motherboard's jumper setting
   b) Formatting the system
   c) Removing BIOS battery
   d) None of the above
 11. What is the best way to protect your hard drive data? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Regular Backup
   b) Run a regular diagnosis
   c) Periodically defrag it
   d) Run scandisk at least once a week
 12. Which feature is not applicable for memory mapped I/O? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Device registers can be accessed with any instructions
   b) System memory address space is used up for ports
   c) New instructions are required to access the device registers
   d) Arithmetic and logical operation can be performed directly on data
 13. Which of the following is a device that is used to connect a number of LANs? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Bridge
   b) Switch
   c) Router
   d) Repeater
 14. Which of the following causes the average memory access time to increase in a memory system with cache memory? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Reduction of access time to cache memory
   b) Decrease in hit ratio
   c) Reduction of miss penalty
   d) Decrease in miss ratio
 15. Which searching algorithm can take O (1) time to find a data from a list? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Tree search
   b) Linear Search
   c) Binary Search
   d) Hashing
 16. Which of the following technique uses memorizations? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Greedy algorithms
   b) Dynamic Programming
   c) Divide and Conquer approach
   d) None of them
 17. Consider a virtual memory system with FIFO page replacement policy. For an arbitrary page access pattern, increasing the number of page frames in main memory will– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Always decrease the number of page faults
   b) Always increase the number of page faults
   c) Sometimes increase the number of page faults
   d) Never affect the number of page faults
 18. In binary search, what is the average number of comparison required for search an element in a list is the element number is– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) 2/n
   b) n
   c) log2n
   d) n - 1
 19. Mapping of a known IP address to a MAC layer address is done by which of the following protocols? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Dynamic Host Control Protocol (DHCP)
   b) Open Shorts Path First (OSP) Protocol
   c) Address Resolution Protocol (ARP)
   d) Network Address Translation (NAT)
 20. Applying the LRU page replacement to the reference string 1 2 4 5 2 1 2 4. The main memory can accommodate pages and it already has pages and 2. Pape I came in before page 2 How many page faults will court? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) 3
   b) 4
   c) 5
   d) 6
 21. A student breaks the door of a professor's office to obtain a copy of the next day's examination. Define the type of security attack in this case. **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Snooping
   b) Repudiation
   c) Masquerading
   d) Replaying
 22. Which of the following registers is loaded with the contents of the memory location pointed by the PC? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Memory address registers
   b) Instruction register
   c) Memory data stores
   d) Program counter
 23. Which of the following command is a type of Data Definition language command? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Create
   b) Update
   c) Deleted
   d) Select
 24. Let transaction T1 has obtained a shared mode lock S on data item Q and transaction T2 has obtained an exclusive mode lock X on data item R. Consider the following statement.
   I: T1 can read Q but cannot write Q.
   II: T2 can read R but cannot write R.
   Which of the above statements is / are valid? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Only I
   b) Only II
   c) Both I and II
   d) Neither I nor II
 25. The address bus flow in—— **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Unidirectional
   b) Bidirectional
   c) Multidirectional
   d) Circular
 26. A proxy server is used as the computer– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) With external access
   b) Acting as a backup
   c) Performing file handling
   d) Accessing user permissions
 27. Which would you do first when troubleshooting a faulty monitor? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Check its connections to the computer and power source
   b) Use a meter to check the CRT and internal circuitry for continuity
   c) Power down the monitor, then turn it on again to see if that corrects the problem
   d) Power down the computer, then turn it on a pain to see if that corrects the problem
 28. Which one of the following commands is used to restore the database to the last committed state? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Save point
   b) Rollback
   c) Commit
   d) None of the
 29. A workstation has just been installed on an Ethernet LAN, but cannot communicate with the network. What should you check first? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Reinstall the network protocols
   b) Reinstall the network interface card driver
   c) Verify the IP configuration on the workstation
   d) Verify the link status on the computer's network card
 30. Which is correct characteristic of Selection Sort? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Time complexity O(n)
   b) Not Comparison-based sorting algorithm
   c) Time complexity O(n²)
   d) It is not in place sort
 31. To remove partial dependency from a database, which technique you will use? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCN
 32. Which is the correct output? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
```c
int i = 4; printf("%d %d", +1,i++); printf("%d", i++);

```
a) 4 5 6
b) 5 7 8
c) 6 4 6
d) 1 4 5
 33. Which one is not the flag of the 8086 Microprocessor? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Carry Flag
   b) Parity Flag
   c) Zero Flag
   d) State Plag
 34. Find the correct output: System.out.print('D' + 'E'+ 'F'); **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) 137
   b) DEF
   c) 207
   d) DEF
 35. Which one is the correct SQL statement to find the second highest mark from STUDENT database contains the marks of all students? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Select MAX(marks) from *STUDENT* WHERE marks NOT IN (select MAX(marks) from *STUDENT*
   b) Select MAX(marks) from *STUDENT* WHERE marks IN (select MAX(marks) from *STUDENT*
   c) select MAX(marks) from *STUDENT*
   d) select MAX(marks) from *STUDENT* WHERE marks NOT IN (select MIN(marks) from *STUDENT*
 36. Suppose you have a complete undirected graph with 4 nodes. What is the maximum number of Minimum Spanning Tree (MST) you can form? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) 4
   b) 8
   c) 16
   d) 1
 37. The \Theta notation in asymptotic evaluation represents— **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Best case
   b) Base case
   c) Average case
   d) Worst case
 38. URL stands for– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Universal Resource Locator
   b) Uniform Resource Locator
   c) Unique Resource Locator
   d) None
 39. Find the output of the following code: **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
```java
int a=15, b=15;
if((a-100) == (b-a)) System.out.print(b+a) ;
else System.out.print(b-a) ;

```
a) 100
b) 200
c) 0
d) 3
 40. Which is correct output? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
```c
int a = 100; int *p = &a +2; *p = 22; printf("%d", a);

```
a) 100
b) 22
c) Error
d) Garbage value
 41. Assume we need to download text documents at the rate of 100 pages per second. A page is an average of 24 lines with 80 characters in each line and one character requires 8 bits. What is the required bit rate of the channel? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) 25600 bps
   b) 25800 bps
   c) 4000 bps
   d) 10000 bps
 42. Which is the disadvantage of Optical Fiber? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Resistance to corrosive materials
   b) Greater immunity to tapping
   c) Unidirectional light propagation
   d) None of these
 43. Related records of the different relations can be stored on the same block using which file organization technique? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Heap file organization
   b) Sequential file organization
   c) Hashing file organization
   d) Multi-table Clustering file organization
 44. Find the correct output: **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
```c
int a = 10,b = 20; a ^= b; b ^= a; a ^= b;
printf("%d %d", a, b);

```
a) 20 30
b) 10 30
c) 20 10
d) Garbage Value
 45. Which is wrong statement for BIOS of a computer? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Connect microprocessor and I/O
   b) Manages data flow
   c) Loads the operating system
   d) Provide storage
 46. DHCP is– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Dynamic Host Control Protocol
   b) Distributed Host Configuration Protocol
   c) Dynamic Host Configuration Protocol
   d) Domain Host Configuration Protocol
 47. Which one is not Database Transaction property? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Atomicity
   b) Consistency
   c) Durability
   d) Quality
 48. Which is correct for Merge sort– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Time complexity, O(n²)
   b) Time complexity, O (n log n)
   c) Time complexity, O (log n)
   d) Not stable sort
 49. How many bits in IPv6? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) 32
   b) 64
   c)128
   d) 156
 50. Which one is the loopback address? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) 255.255.255.0
   b) 127.0.0.1
   c) 255.0.0.0
   d) 127.127.127.0
 51. How can we prevent SQL Injection Attack? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Show the database error to the users
   b) Use input validation
   c) Use the user input directly
   d) Do not remove potential malicious code
 52. Which of the following is not a true statement? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Deleted files can be found in recycle bin
   b) Deleted files in recycle bin can be restored
   c) Disk space can be increased by sending files into recycle bin
   d) There may have multiple recycle bin
 53. Which one is not a layer of cloud computing? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Computing as a service (CaaS)
   b) Infrastructure as a service (IaaS)
   c) Platform as a service (PaaS)
   d) Software as a service (SaaS)
 54. What is postfix expression of the string, a+(b-c)*d? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) abc-d*+
   b) abcd - *+
   c) ad* bc -
   d) abc – d+*
 55. Which of the following is not a function of a database administrator? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Database the design
   b) Backing up the database
   c) Query processing
   d) User coordination
 56. In which addressing mode, the effective address of the operand is generated by adding a constant value to the contents of the register? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Absolute mode
   b) Indirect mode
   c) Immediate mode
   d) Index mode
 57. Most PCs give a single beep on boot up to indicate that the hardware is ok. If you do not get any beep, then what will be the first thing to check? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) System board
   b) RAM
   c) Power supply
   d) Speaker
 58. The simplified form of the Boolean expression (A+B+AB) (A+C) is– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) A + B + C
   b) AB + BC
   c) A+BC
   d) ACB
 59. Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) An exclusive logical sum of N with 0Fh
   b) A negative logical product of N with 0Fh
   c) A logical product of N with 0Fh
   d) A logical sum of N with 0Fh
 60. Consider the following relational database–
   *Order (OrderNumber, OrderDate, Promised Date)*
   *Orderline (OrderNumber, ProductID, QuantityOrdered)*
   *Product (Product ID Description, Price)*
   What types of relationship exists in the following Order line table? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) One to One
   b) One to Many
   c) Many to Many
   d) Many to One
 61. ‘সন্ধি’ ব্যাকরণের কোন অংশে আলোচিত হয়? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) ধ্বনিতত্ত্ব
   b) অর্থতত্ত্ব
   c) বাক্যতত্ত্ব
   d) রূপতত্ত্ব
 62. বিভক্তিহীন নাম শব্দকে কী বলে? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) প্রকৃতি
   b) উপধা
   c) ধাতু
   d) প্রাতিপদিক
 63. ‘রক্তাক্ত প্রান্তর’ নাটকের পটভূমি– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) পলাশীর যুদ্ধ
   b) ভাষা আন্দোলন
   c) পানিপথের যুদ্ধ
   d) অসহযোগ আন্দোলন
 64. সঠিক সন্ধি বিচ্ছেদ কোনটি? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) বন + পতি = বনস্পতি
   b) অহঃ + রহ = অহরহ
   c) সং + সার = সংসার
   d) ছেলে + মি = ছেলেমি
 65. নিচের কোনটি মৌলিক শব্দ নয়? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) গোলাপ
   b) গায়ক
   c) হাত
   d) ফুল
 66. ‘ঠিক’, তুমি সত্য বলেছ।’– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) সিদ্ধান্ত আবেগ
   b) প্রশংসা আবেগ
   c) অলংকার আবেগ
   d) সম্বোধন আবেগ
 67. বাংলাদেশের নাটকে ‘কথানাট্যের’ পথিকৃৎ– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) সেলিম আল দীন
   b) সৈয়দ শামসুল হক
   c) আব্দুল্লাহ আল মামুন
   d) মান্নান হীরা
 68. ‘তুমি আসবে বলে হে স্বাধীনতা’- কার রচনা? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) আবু জাফর ওবায়দুল্লাহ
   b) আল মাহমুদ
   c) শামসুর রাহমান
   d) নির্মলেন্দু গুণ
 69. চর্যাপদে কোন পদকর্তার রচনা সর্বাধিক? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) লুই পা
   b) ভুসুক পা
   c) কাহ্ন পা
   d) শবরী পা
 70. ‘অর্ণব’ শব্দের অর্থ কী? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) সাগর
   b) নদী
   c) জলাশয়
   d) ঢেউ
 71. Which one word is closest in meaning to 'Franchise'? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) privilege
   b) superficial
   c) frankness
   d) openness
 72. The complex form of 'A rolling stone gathers no moss' is **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) Though a stone roll, it gathers no moss
   b) A stone what rolls gathers no moss
   c) Since a stone is rolling it gathers no moss
   d) A stone that rolls gathers no moss
 73. Which word is spelt correctly? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) concensus
   b) hierarchy
   c) madieval
   d) posession
 74. The people who carry a coffin at a funeral are called ________ **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) undertakers
   b) supporters
   c) pallbearers
   d) mourners
 75. While living in poverty, the poet had to a great deal of suffering. **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 132]**
   a) see through
   b) put up with
   c) pass by
   d) full back
 76. Which statement is correct? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) Mumbai is the seaport near to Europe
   b) Mumbai is the seaport next to Europe
   c) Mumbai is the seaport nearest to Europe
   d) Mumbai is the seaport nearer to Europe
 77. I differ ____ you ____ this question. **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) against, about
   b) from, on
   c) to, for
   d) with, on
 78. Which phrase contains words opposed to each other in meaning? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) heat and dust
   b) reproduction and death
   c) hopes and aspirations
   d) emerged and advanced
 79. The ________ of the forest will result in the ________ of many animal species. **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) destruction / disappear
   b) destruction / disappearance
   c) destructing / disappear
   d) destruct/disappearance
 80. If 5x+4y=22, 3x+3y-21, what is the value of x and y? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) x=2, y=3
   b) x=2, y=-4
   c) x=3, y=7
   d) x=2, y=-3
 81. It is time to shut up the shop. (Passive) **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) It is time to the shop the be shuted up
   b) It is time for the shop to shut up
   c) It is time for the shop to be shut up
   d) It is time for the shop to be shuted up
 82. If 3x+5y =14 and x-y = 6 then what is the average of x and y? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 1
   b) 1.25
   c) 2
   d) 2.5
 83. Of the series 5+8+11+14 ________ which term is 383? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 122ᵗʰ
   b) 127ᵗʰ
   c) 136ᵗʰ
   d) 144ᵗʰ
 84. If a man rows at 5km/hr in still water and 3.5 km/hr against the current, find his rate along the current. **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 4 .25 km
   b) 4.5 km
   c) 6 km
   d) 6.5km
 85. Alom sold a radio at the cost of 1950 taka at a loss of 25%. At what cost will he have to sell it to get a profit of 30%? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 4000
   b) 3380
   c) 3580
   d) 3400
 86. Of 100 students 90 passed in Bangla, 85 in Mathematics and 80 in both subjects. How many students fasted in both subjects? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 7
   b) 5
   c) 15
   d) 10
 87. If a = \sqrt{3} + \sqrt{2} then value of a^3 + \frac{1}{a^3} = ? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 10\sqrt{3}
   b) 12\sqrt{3}
   c) 12\sqrt{3}
   d) 18\sqrt{3}
 88. The loss is 30% when 10 lemons are sold per taka. How many lemons are to be sold per taka to make a profit of 40%? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 2
   b) 6
   c) 5
   d) 10
 89. The ratio of milk and water in 64 liters of a mixture is 5:3. What amount of water is added to make the ratio 3:5? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) 42\frac{2}{3}
   b) 50\frac{5}{2}
   c) 35\frac{2}{3}
   d) 40\frac{5}{3}
 90. Factorize a^3 - 70a - 6 **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 133]**
   a) (a + 1) (a - 2) (a - 3)
   b) (a - 1) (-2) (a - 3)
 91. Nassau is the capital city of– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) The Bahamas
   b) The Nicobar Islands
   c) Madagascar
   d) The Cubies
 92. What are the small indentations on a golf ball called? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) Birdie
   b) Albatross
   c) Mulligan
   d) Dimples
 93. When did Bangabandhu declared historic six point programme? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) February 4, 1966
   b) February 5, 1966
   c) February 6, 1966
   d) February 7, 1966
 94. The length of Dhaka Metro Rail will be– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) 19.10 km
   b) 20.10 km
   c) 21.10 km
   d) 20.50 km
 95. As per the latest changes in Bengali Calendar, leap year is calculated in which month? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) Boishakh
   b) Bhadro
   c) Ashwin
   d) Falgun
 96. Which country gave the 'Statue of Liberty to the United States of America as a gift? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) France
   b) Great Britain
   c) Germany
   d) Russia
 97. Who is the builder of the 'Sat Gumbad' (Seven-domed) mosque? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) Shaesta Khan
   b) Khan Jahan Ali
   c) Isha Khan
   d) Islam Khan
 98. When is the ‘International Day of the Victims of Enforced Disappearances’ observed? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) August 15
   b) August 30
   c) September 15
   d) September 30
 99. Free Market Economy started in Bangladesh in– **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) 1989
   b) 1990
   c) 1991
   d) 1992
 100. Which countries are jointly called the 'Golden Crescent'? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 134]**
   a) Afghanistan, Iran and Pakistan
   b) Afghanistan, India and Pakistan
   c) Iraq, Lebanon and Syria
   d) Thailand, Laos and Myanmar
 101. ২০২২ ফুটবল বিশ্বকাপ কোথায় হবে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) কাতার
   b) ব্রাজিল
   c) মেক্সিকো
   d) ইংল্যান্ড
 102. শেখ রাসেল কে লিখেছেন? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) শেখ মুজিবুর রহমান
   b) শেখ হাসিনা
   c) শেখ রেহেনা
   d) সজীব ওয়াজেদ জয়
 103. ডিজিটাল বাংলাদেশ দিবস কবে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) ১২ নভেম্বর
   b) ১২ ডিসেম্বর
   c) ৬ ডিসেম্বর
   d) ৬ জুলাই
 104. বঙ্গবন্ধু উপাধি পান কত সালে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) ১৯৭১
   b) ১৯৫২
   c) ১৯৭২
   d) ১৯৬৯
 105. বাংলাদেশ অস্ট্রেলিয়া সিরিজের ফলাফল কি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) ৩-২
   b) ৪-১
   c) ১-৪
   d) ২-৩
 106. অলিম্পিক ২০২০ এ সবচেয়ে বেশি পদকপ্রাপ্ত দেশ কোনটি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) চীন
   b) জাপান
   c) যুক্তরাষ্ট্র
   d) জার্মানী
 107. বাংলাদেশের কত শতাংশ এলাকা বিদ্যুতায়িত হয়েছে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 134]**
   a) ৯৯.৫
   b) ৯৯
   c) ৯৮
   d) ১০০
 8. পল্লীবিদ্যুৎ এর গ্রাহক সংখ্যা কত? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) প্রায় ৩.১৩ কোটি
   b) প্রায় ৩.০২ কোটি
   c) প্রায় ৩.১০ কোটি
   d) প্রায় ৩ কোটি
 9. GPRS এর পূর্ণরূপ কি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) General Packet Ratio Server
   b) General Purpose Reduction Service
   c) General Packet Radio Service
   d) General Purpose Radio Server
 10. কোনটা ওয়্যারলেস নেটওয়ার্ক হটস্পট? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Wi-Fi Hotspot
   b) Ethernet Hotspot
   c) Fiber Hotspot
   d) None
 11. Bluetooth কোন ধরনের device? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) WAN
   b) PAN
   c) LAN
   d) MAN
 12. লক্ষন এর বানান কোনটি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) লক্ষণ
   b) লক্ষন
   c) লক্ষণ
   d) লক্ষন
 13. অলস এর বাগধারা কোনটি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) বালির বাঁধ
   b) অকালকূশ্মাণ্ড
   c) গোঁফখেজুরে
   d) কোনটি নয়
 14. Cinema, Pistol ইংরেজি কিনা? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) ইংরেজি
   b) ফার্সি
   c) পর্তুগীজ
   d) ওলন্দাজ
 15. Initiative এর বিপরীত শব্দ কোনটি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Non Initiative
   b) Iminitiative
   c) Uninitiative
   d) None of these.
 16. Look ________ the word in the dictionary (preposition) **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) In
   b) up
   c) into
   d) at
 17. Girl কোন ধরনের noun? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Collective Noun
   b) Proper Noun
   c) Common Noun
   d) Abstract Noun
 18. Obligate এর adjective form কোনটি? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Obligatory
   b) Obligative
   c) Obligator
   d) Obligate
 19. If \log 2 = a and \log 5 = b, then \log 50 =? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) a + b
   b) a + b^2
   c) ab^2
   d) a + 2b
 20. To do away with meaning. **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) To get rid of something or stop using something
   b) To do pass away
   c) To remove it completely or put an end to it
   d) all of these
 21. Wi-fi কোন ধরনের নেটওয়ার্ক? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Wifi LAN
   b) Wireless PAN
   c) Wifi MAN
   d) Wifi WAN
 22. কি-বোর্ড একটি- **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) ট্রান্সডিউসার
   b) ট্রান্সমিটার
   c) চ্যানেল
   d) সব কযটি
 23. Which is plural – **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Formula
   b) Memoranda
   c) Vertex
   d) Agendam
 24. বাংলাদেশ পল্লী বিদ্যুতায়ন বোর্ড কত পার্সেন্ট বিদ্যুৎ শেয়ার করে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) 00%
   b) 10%
   c) 90%
   d) 50%
 25. Minimum SNR PC a pulg? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) Higher Channel Bandwidth
   b) Lower Signal Power
   c) Higher Signal Power
   d) None
 26. Y-Y Connection এ neutral করা হয় কেন? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 135]**
   a) শূন্য বিদ্যুৎ প্রবাহিত করার জন্য
   b) সম্পূর্ণ বিদ্যুৎ প্রবাহিত করার জন্য
   c) বিদ্যুৎ প্রবাহের হার সমান রাখার জন্য
   d) কোনটি নয়
 27. কোন ধরনের ম্যাটেরিয়ালের Permeability স্পেস এর তুলনায় কম? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Ferromagnetic
   b) Paramagnetic
   c) Diamagnetic
   d) Bipolar
 28. Active region এ BJT এর base-emitter and base collector কোন bias এ থাকে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Forward - Reverse
   b) Reverse - Forward
   c) Forward -Forward
   d) Reverse -Reverse
 29. For an n-channel enhancement type MOSFET, if the source is connected at a higher potential than that of the bulk (i.e. V_{SB} > 0), the threshold voltage V_T of the MOSFET will- **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Remain unchanged
   b) decrease
   c) Change polarity
   d) increase
 30. Wi-Fi for? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Wireless MAN
   b) Wireless PAN
   c) Wireless LAN
   d) all of these
 31. What is the name of the following symbol? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) FET
   b) JFET
   c) Schottky Diode
   d) SCR
 32. Group sms is ________ **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Unicast
   b) Multicast
   c) Telecast
   d) Broadcast
 33. Efficiency এবং power factor বাড়ালে induction motor Gi speed কি হবে? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Neutral
   b) Decrease
   c) Increase
   d) a&b
 34. Op-amp এর ক্ষেত্রে কোনটি সত্য? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Large input impedance
   b) Large output impedance
   c) Small input impedance
   d) All of these
 35. Stator winding single phase motor 97 PETIT RT? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Stator এর ভিতর
   b) Rotor এর ভিতর
   c) Stator এর বাহিরে
   d) Rotor এর বাহিরে
 36. Which type of capacitance form in forward bias. **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Transition
   b) Junction
   c) Diffusion Capacitance
   d) a & b
 37. না কোন পদ? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) অব্যয়
   b) সর্বনাম
   c) বিশেষণ
   d) অব্যয়
 38. Synchronous motor run in What type of power factor at under excitation **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Unity
   b) Lagging
   c) Leading
   d) None of these
 39. What will be speed if pole no is increased in alternator? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Increase
   b) Decrease
   c) Synchronous
   d) None of these
 40. Spring এর past form. **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Sprang
   b) Springed
   c) Spring
   d) All of these
 41. Which of the following modulation is used in data communication? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Pulse Modulation
   b) Amplitude Modulation
   c) Phase Modulation
   d) Frequency Modulation
 42. If an atom loses an e- it will be turned into? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   a) Neutral
   b) Anion
   c) Proton
   d) Cation
 43. What is the range of Font Size available in Font Size drop down toolbar? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 136]**
   A. From 10 to Large 70
   B. From 8 to Large 72
   C. From 5 to Large 75
   D. From 10 to Large 100
 44. What is the word length of a personal computer? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a) 32 bits
   b) 8 bits
   c) 64 bits
   d) 16 bits
 45. By default, Footers are printed on: **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   A. First Page
   B. Last Page
   C. All Pages
   D. Even Pages
 46. Which of the following values is the correct value of this hexadecimal code 1F.01B? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a. 35.0065918
   b. 32.0065918
   c. 31.0065918
   d. 30.0065918
 47. How Many Number of 33/11KV Sub-station? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a. 1136 Nos
   b. 1150 Nos
   c. 1166 Nos
   d. 1200 Nos
 48. What is the peak demand of BREB? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a. 7000 MW
   b. 7100 MW
   c. 7500 MW
   d. 8000 MW
 49. What is the mean of the Booting in the system? **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a. Restarting computer
   b. Install the program
   c. To scan
   d. To turn off
 50. রবীন্দ্রনাথ ঠাকুর ও কাজী নজরুল ইসলামের বয়সের পার্থক্য কত? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   ক) ৩২ বছর
   খ) ৩৮ বছর
   গ) ৪২ বছর
   ঘ) ৪৬ বছর
 51. "সুশিক্ষিত লোক মাত্রই স্বশিক্ষিত" এই উক্তি কার? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   ক) রবীন্দ্রনাথ ঠাকুর
   খ) কাজী আব্দুল ওদুদ
   গ) লুৎফর রহমান
   ঘ) প্রমথ চৌধুরী
 52. প্রত্যেক ভাষারই তিনটি মৌলিক অংশ হলো? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   ক) ধ্বনি, শব্দ, বাক্য
   খ) শব্দ, সন্ধি, সমাস
   গ) ধ্বনি, শব্দ, বর্ণ
   ঘ) অনুসর্গ, উপসর্গ, শব্দ
 53. কোন বানানটি শুদ্ধ? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   ক) সমীচীন
   খ) সমীচিন
   গ) সমিচীন
   ঘ) সমিচিন
 54. “লা, খাস, আম " কোন ধরনের উপসর্গ? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   ক) আরবি
   খ) ফারসি
   গ) উর্দু
   ঘ) ইংরেজি
 55. "Glimpes of world history " was written by **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   a) leo Tolstoy
   b) Jawaharlal Nehru
   c) A.P.J abdul kalam
   d) Rabindranath Tagore
 56. Which sector has the largest contribution in GDP of Bangladesh **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   a) Garments
   b) Man export
   c) Agriculture
   d) industry
 57. Dhaka was the under the sector in liberation war. **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   a) 2
   b) 4
   c) 11
   d) 8
 58. Niagara Falls is located in **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 137]**
   a) South America
   b) Africa
   c) Australia
   d) North America
 10. The name of the parliament of USA is? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) Congress
   b) House of Commons
   c) White House
   d) Capital
 11. Which of the following organization is concerned for the climate change? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) OIC
   b) MIGA
   c) IPCC
   d) WMO
 12. The owner of the Greenland is? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) Denmark
   b) Netherlands
   c) Japan
   d) Russia
 13. The biggest desert of the world is **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) Great Victoria Desert
   b) Sahara Desert
   c) Kalahari Desert
   d) Tabernas Desert
 14. Theme of AIDS day of 2021 is? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) "End Inequalities, End AIDS"
   b) "Global solidarity, resilient HIV services."
   c) Communities Make the Difference
   d) My health, My Right
 15. The city which is known as the city of Culture is **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) Rome
   b) Paris
   c) Athens
   d) London
 16. What is the brightest planet seen from Earth? **(Northern Electricity Supply Company Limited (NESCO) Assistant Engineer (ICT) Exam: 2021 (BUET)) [compact it 138]**
   a) Venus
   b) Mars
   c) Mercury
   d) Jupiter
 17. I wish you ________ the problem. **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) Can Solve
   b) Could Solve
   c) Would
   d) Would Solve
 18. The word “beautiful” is ________? **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) a noun
   b) a verb
   c) a verb
   d) an adjective
 19. The plural form of index is? **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) Indices
   b) Indexes
   c) Indexis
   d) Indicess
 20. He speaks as if he ________ a leader. **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) as
   b) was
   c) were
   d) is
 21. Choose the right sentence. **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) More he gets, more he wants
   b) The more he gets, more he wants
   c) More he gets, the more he wants
   d) The more he gets, the more he wants
 22. নিচের কোনটি সঠিক বানান? **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) সাম্বত
   b) শাশ্বত
   c) শ্বাশত
   d) শাশ্বত
 23. Civil Society এর পারিভাষিক শব্দ কোনটি? **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) সভ্য সমাজ
   b) সুশীল সমাজ
   c) বেসামরিক সমাজ
   d) অসামাজিক সমাজ
 24. জায়া ও পতি এর সমাস করলে কি হবে? **(PGCB Sub-Assistant Engineer (Computer) Exam: 2021 (BUET)) [compact it 138]**
   a) পতি-পত্নী
   b) দম্পতি
   c) জায়া-পতি
   d) স্বামী-স্ত্রী
 25. কোনটি সঠিক বানান? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 138]**
   ক. সমীচীন
   খ. সমিচীন
   গ. সমীচিন
   ঘ. সমিচিন
 2. ছন্দের জাদুকর কোন কবি? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. সুকুমার রায়
   খ. সত্যেন্দ্রনাথ দত্ত
   গ. আল মাহমুদ
   ঘ. জসীম উদ্দীন
 3. সর্বাঙ্গীন এর প্রকৃতি-প্রত্যয়; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. সর্বাঙ্গ+ইন
   খ. সর্ব+অঙ্গীন
   গ. সর্ব+ঙ্গীন
   ঘ. সর্বাঙ্গ+ীন
 4. সূর্য শব্দের সমর্থক কী? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. অর্ণব
   খ. অর্ক
   গ. পলব
   ঘ. কোনটি নয়
 5. শেষের কবিতা কোন ধরনের রচনা? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. কবিতা
   খ. উপন্যাস
   গ. গল্প
   ঘ. নাটক
 6. অরণ্যে রোদন কী? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. বচন কান্না
   খ. বনের কান্না
   গ. পাগলের প্রলাপ
   ঘ. নিষ্ফল আবেদন
 7. বাবা শব্দটি কোন ভাষা থেকে আগত? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. সংস্কৃত
   খ. হিন্দি
   গ. আরবি
   ঘ. তুর্কি
 8. শব্দের মূলকে কি বলে? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. বিভক্তি
   খ. প্রত্যয়
   গ. অব্যয়
   ঘ. প্রকৃতি
 9. If a pen is sold at taka 55 it makes a profit of 10%. What is its purchase cost? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 50
   খ. 110
   গ. 45
   ঘ. 60
 10. When base is 12 inch and height is 8inch of a triangle, its area? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 96 sq-in
   খ. 48 sq-in
   গ. 48 in
   ঘ. 46 in
 11. If, xy = 5, xy = 6, then x+y=? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 7
   খ. \pm 7
   গ. 1
   ঘ. None
 12. How many prime numbers are there from 1 to 10? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 10
   খ. 5
   গ. 4
   ঘ. 3
 13. The solution of equations x-y=2 and x+y=4; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 3 and 1
   খ. 4 and 3
   গ. 5 and 1
   ঘ. -1 and -3
 14. What is 3% of 0.07? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 21
   খ. 0.21
   গ. 0.021
   ঘ. 0.0021
 15. What is the perimeter of a square, if its area is 400sq-m? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 40m
   খ. 80m
   গ. 20m
   ঘ. 20sq-m
 16. If each of the six members of a family gives money as per their membership number, then what will be the total amount? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 216
   খ. 125
   গ. 100
   ঘ. 64
 17. Which one is the smallest? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 0.02
   খ. 1/100
   গ. 10
   ঘ. None
 18. 0.1 \times 0.01 + 1 = ? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. 1.01
   খ. 1.001
   গ. 2.01
   ঘ. 0.001
 19. Who was the director of the film “Let there be Light”? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. Zahir Raihan
   খ. Amjad Hossain
   গ. Khan Ataur Rohman
   ঘ. Humayan Ahmed
 20. Sources its produce electricity in Bangladesh; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. Mineral oil
   খ. Natural gas
   গ. Hilly River
   ঘ. All of them
 21. Which country first gave recognition to Bangladesh? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 139]**
   ক. India
   খ. Russia
   গ. Bhutan
   ঘ. Nepal
 22. 'Dry Ice' is produced from; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Oxygen
   খ. Sulphur di oxide
   গ. Nitrogen
   ঘ. Carbon di oxide
 23. Which symbol must remain in e-mail address? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. $
   খ. N
   গ. @
   ঘ. &
 24. SDG-30 এর কত নম্বর Goal এ বিদ্যুতের বর্ণনা রয়েছে? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. ৭
   খ. ৮
   গ. ৫
   ঘ. ৬
 25. How many accused were in ‘Agartala Conspiracy Case’ including Bangabandhu? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. 36
   খ. 35
   গ. 34
   ঘ. 32
 26. What is LINUX? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Operating System
   খ. Application Program
   গ. Antivirus software
   ঘ. Firewall
 27. Omicron, the new variant of COVID-19 is originated from; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. China
   খ. UK
   গ. America
   ঘ. South Africa
 28. Which one is output device? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Microphone
   খ. CD-Drive
   গ. Monitor
   ঘ. None of them
 29. Who scored the only goal in the final match of 2021 SAFF U-19 Women's Championship? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Shaheda Akter Ripa
   খ. Anai Mogini
   গ. Maria Mauda
   ঘ. Anishka
 30. Under which sector Dhaka was during our Liberation War in 1971? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. 3
   খ. 2
   গ. 4
   ঘ. 1
 31. Who appoints the Chief Justice in Bangladesh? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Prime Minister
   খ. Parliament
   গ. President
   ঘ. None
 32. Who was F.R Khan? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Cancer Specialist
   খ. Nuclear Scientist
   গ. Computer Engineer
   ঘ. Architect
 33. Ping Pong means; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Volleyball
   খ. Table Tennis
   গ. Basketball
   ঘ. Lane Tennis
 34. Country participated as "Observer"in "Victory Day Parade 2021"; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. USA
   খ. Russia
   গ. India
   ঘ. Bhutan
 35. The urgency of rural electrification is described in which article of constitution? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. 8
   খ. 10
   গ. 15
   ঘ. 16
 36. Architect of national monument of Bangladesh is; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Hamidur Rahman
   খ. Quamrul Hassan
   গ. Sayed Mainul Hossian
   ঘ. F.R Khan
 37. Data are entered into a computer through; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Software
   খ. Output device
   গ. Input device
   ঘ. Memory
 38. What is the per capita income ($US) of Bangladesh in 2021? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. 2254
   খ. 2454
   গ. 2554
   ঘ. 3054
 39. How may freedom fighters have received gallantry awards for contributions in our Liberation War-1971? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. 712
   খ. 512
   গ. 175
   ঘ. 676
 40. Who is the Head of the State of Bangladesh? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. President
   খ. Prime Minister
   গ. Speaker
   ঘ. None
 41. The Nobel Laureate Adbulrazak Gurnah is from; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Turkey
   খ. Malaysia
   গ. Indonesia
   ঘ. Tanzania
 42. In which logic gate output is 1 when all inputs are zero? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. AND
   খ. NAND
   গ. OR
   ঘ. NOR
 43. DNA is found in; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Chromosome
   খ. Lissomes
   গ. Ribosome
   ঘ. Galel Complex
 44. What is the maximum operating transmission voltage (KV) in Bangladesh? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. 33
   খ. 132
   গ. 230
   ঘ. 400
 45. The nature of electricity being produced using sun rays is; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. AC
   খ. DC
   গ. Both AC and DC
   ঘ. None
 46. কোনটি এন্টিবায়োটিক? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. ইনসুলিন
   খ. পেপসিন
   গ. ইথিলিন
   ঘ. পেনিসিলিন
 47. Function of distribution sub-station is to; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. step down voltage
   খ. step up voltage
   গ. increase power
   ঘ. increase energy
 48. 'RAPIS' শব্দটি সাজালে হয়; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. মহাসাগর
   খ. শহর
   গ. দেশ
   ঘ. কোনটি নয়
 49. Which one is not correct? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. A+0=A
   খ. A.1=A
   গ. A+A'=1
   ঘ. A.A'=1
 50. BREB has about ________ consumers of the country in its load. **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. 70%
   খ. 80%
   গ. 85%
   ঘ. 90%
 51. Which one is masculine word? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Marc
   খ. Lad
   গ. Pillow
   ঘ. Pony
 52. Fill in the blank of, A seventeen years old is not ________ to vote in an electron. **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. as old enough
   খ. enough old
   গ. old enough
   ঘ. enough older
 53. Which word remains same in plural form? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Aircraft
   খ. Intention
   গ. Mouse
   ঘ. Teach
 54. 'Enough is enough' is used to mean; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Continue
   খ. Stop
   গ. Continue until it is enough
   ঘ. None
 55. Brochure means; **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Opening
   খ. Bureau
   গ. Consor
   ঘ. Pamphlet
 56. Change the voice of, who is calling me? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. By whom am I called?
   খ. By whom I am called?
   গ. By whom I was called?
   ঘ. By Whom am I being called?
 57. "Once in a blue moon" means: **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Always
   খ. Rarely
   গ. Very rarely
   ঘ. Hourly
 58. What is the synonym of 'Incite'? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 141]**
   ক. Urge
   খ. Permit
   গ. Instigate
   ঘ. Deceive
 59. What type of noun is 'Kindness'? **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 142]**
   ক. Abstract
   খ. Proper
   গ. Common
   ঘ. Material
 60. 'Alumni' is the plural of: **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 142]**
   ক. Aluminus
   খ. Alumnous
   গ. Alumnus
   ঘ. Aluminise
 61. ডিলিং মেসিন কর্তৃক কোন অপারেশন সম্পন্ন করা হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) Spot facing
   (খ) Reaming
   (গ) Boring
   (ঘ) সবকটি
 62. বাংলাদেশ কোন সালে আনুষ্ঠানিকভাবে উন্নয়নশীল দেশ হিসাবে স্বীকৃতি লাভ করবে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) ২০২৪
   (খ) ২০২৮
   (গ) ২০২৬
   (ঘ) ২০৩০
 63. রাতারগুল কোন জেলায় অবস্থিত? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) রাঙ্গামাটি
   (খ) সাতক্ষীরা
   (গ) সিলেট
   (ঘ) কক্সবাজার
 64. একটি হিমায়ন চক্রের হিমায়ক কর্তৃক তাপ শোষিত হয় **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) কন্ডেন্সারে
   (খ) ইভাপোরেটরে
   (গ) কম্প্রেসরে
   (ঘ) থ্রোটল ভালবে
 65. Use the right form of verb is the following sentence: I wish I ________ a car. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (a) have
   (b) shall have
   (c) have had
   (d) had
 66. কোন বানানটি বিশুদ্ধ? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) আশার
   (খ) আসার
   (গ) আষাঢ়
   (ঘ) আষাঢ়
 67. Moment of Inertia এর একক হলো- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) \text{mm}^4
   (খ) \text{mm}^3
   (গ) \text{mm}^2
   (ঘ) \text{mm}^5
 68. গিয়ার তৈরিতে সাধারণত ব্যবহৃত হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) Cast Iron
   (খ) Steel
   (গ) Copper
   (ঘ) Wrought Iron
 69. কোনটি রবীন্দ্রনাথ ঠাকুরের কাব্য নয়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) মানসী
   (খ) সোনার তরী
   (গ) চোখের বালি
   (ঘ) গীতাঞ্জলি
 70. গণপ্রজাতন্ত্রী বাংলাদেশের সংবিধানে কয়টি অনুচ্ছেদ আছে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) ১৩৩টি
   (খ) ১৪৩টি
   (গ) ১৫৩টি
   (ঘ) ১৭৩টি
 71. নির্মাণাধীন পদ্মা সেতুর স্প্যান সংখ্যা কতটি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) ৩৯ টি
   (খ) ৪০টি
   (গ) ৪১টি
   (ঘ) ৪২টি
 72. WWW (World Wide Web) এর জনক কে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) বিল গেটস
   (খ) স্টিভ জবস
   (গ) টিম বার্নস লি.
   (ঘ) জেফ বেজোফ
 73. কোন Technical drawing এর ক্ষেত্রে উর্ধ্বরিহম এ দৈর্ঘ্য ও বস্তুর প্রকৃত দৈর্ঘ্যের অনুপাতকে বলে- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) Representative fraction
   (খ) Scale
   (গ) Dimension ratio
   (ঘ) Distance fraction
 74. A barking dog seldom bites. In the sentence, 'barking' is ________ **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (a) a gerund
   (b) an adverb
   (c) a verb
   (d) an adjective
 75. পল্লী কবি জসিম উদ্দীনের জন্মস্থান- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) গোপালগঞ্জ
   (খ) ফরিদপুর
   (গ) পিরোজপুর
   (ঘ) বিক্রমপুর
 76. এক বায়ুমন্ডলীয় চাপ সমান- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (ক) ১৪.৭ কেজি/সে.মি
   (খ) ১ কেজি/মি.
   (গ) ১.০৩৩ কেজি/সে.মি
   (ঘ) ১.০৩৩ কেজি/মি
 77. Choose the correct preposition for the sentence: I reminded him ________ his appointment. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 142]**
   (a) Of
   (b) to
   (c) on
   (d) has
১৮. শিয়ার পীড়ন ও শিয়ার বিকৃতি এর অনুপাত হলো– **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) পয়সনের অনুপাত
(খ) বাল্ক মডুলাস
(গ) মডুলাস অফ রিজিডিটি
(ঘ) মডুলাস অফ ইলাস্টিসিটি
১৯. দুই টাকার নোটে কার স্বাক্ষর থাকে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) অর্থ সচিব
(খ) বাংলাদেশ ব্যাংকের গভর্নর
(গ) অর্থমন্ত্রী
(ঘ) প্রধানমন্ত্রী
২০. বাংলাদেশে কোভিড ১৯ এর ভ্যাকসিন প্রথম ব্যবহৃত হয়েছে– **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) অক্সফোর্ড অ্যাস্ট্রাজেনেকা-কোভিশিল্ড
(খ) সিনোভ্যাক্স এর করোনাভ্যাক
(গ) ফাইজারের বায়োএনটেক
(ঘ) জনসন এন্ড জনসন-জনসেন
২১. The phrase ‘Baker’s dozen’ means ________ **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(a) 13
(b) 12
(c) 11
(d) 24
২২. Fill in the blank with the right option: The poor ________ born to suffer. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(a) are
(b) is
(c) were
(d) has
২৩. Degree of freedom কতটি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ৯টি
(খ) ১২টি
(গ) ১১টি
(ঘ) ১৮টি
২৪. নাচোল বিদ্রোহের নেত্রির নাম কি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) প্রীতিলতা
(খ) লক্ষ্মীরাণী
(গ) কাদম্বিনী
(ঘ) ইলা মিত্র
২৫. বাংলাদেশের মহান মুক্তিযুদ্ধে বীর প্রতীক খেতাব প্রাপ্ত একমাত্র বিদেশি উইলিয়াম এ এস ওডারল্যান্ড কোন দেশের নাগরিক? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ভারত
(খ) যুক্তরাজ্য
(গ) অস্ট্রেলিয়া
(ঘ) জাপান
২৬. IC ইঞ্জিনের জ্বালানী দহন ঘটে- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) সিলিন্ডারের বাইরে
(খ) সিলিন্ডারের অভ্যন্তরে
(গ) কোথাও দহন ঘটে না
(ঘ) উপরের কোনটি নয়।
২৭. বাংলাদেশের সর্বপ্রথম জাদুঘর কোথায় প্রতিষ্ঠিত হয়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ঢাকা
(খ) বরেন্দ্র
(গ) সিলেট
(ঘ) চট্টগ্রাম
২৮. Lami's Theorem কি ধরনের বলের ক্ষেত্রে প্রযোজ্য? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) সমতলীয় বল
(খ) সমবিন্দু বল
(গ) সমতলীয় সমবিন্দু বল
(ঘ) লম্বিক বল
২৯. রেডিয়াস অফ জাইরেশন (k) হলো- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) \sqrt{\frac{A}{I}}
(খ) \sqrt{\frac{I}{A}}
(গ) \sqrt{AI}
(ঘ) \sqrt{\frac{I}{AI}}
৩০. টুল ম্যাটেরিয়াল হিসেবে ব্যবহৃত হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) টুল স্টিল
(খ) কার্বন স্টিল
(গ) সিরামিক স্টিল
(ঘ) ডায়মন্ড স্টিল
৩১. ধাতুর যে ধর্মের কারনে পিটিয়ে পাত (sheet) এ পরিণত করা যায় তা হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) Ductility
(খ) Brittleness
(গ) Malleability
(ঘ) Toughness
৩২. ভাসানচর কোন জেলায় অবস্থিত? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) চট্টগ্রাম
(খ) ভোলা
(গ) নোয়াখালী
(ঘ) কক্সবাজার
৩৩. সন্ধি ব্যাকরণের কোন অংশে আলোচিত হয়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ধ্বনি তত্ত্ব
(খ) রূপতত্ত্ব
(গ) বাক্য তত্ত্ব
(ঘ) বাগার্থ তত্ত্ব
৩৪. যে কোন মুহূর্তে বয়লারের পানির সঠিক লেভেল জানা যায় যে যন্ত্রের সাহায্যে সেটি হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ওয়াটার লেভেল ইন্ডিকেটর
(খ) ফিড চেক ভালব
(গ) ব্লো অফ-কক
(ঘ) স্টপ ভালব
৩৫. ডোমেস্টিক রেফ্রিজারেটরের কো-এফিসিয়েন্ট অফ পারফরমেন্স (COP) হলো- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ১.০ এর সমান
(খ) ১.০ কম
(গ) ১.০ এর বেশি
(ঘ) ক, খ, গ এর যে কোন মান
৩৬. শওকত ওসমান কবে জন্ম গ্রহণ করেন? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 143]**
(ক) ১৯২২ সালে
(খ) ১৯১৭ সালে
(গ) ১৯২৫ সালে
(ঘ) ১৯২৩ সালে
 37. কোনটি নন-পজিটিভ ডিসপ্লেসমেন্ট কম্প্রেসর **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) রেসিপ্রোকেটিং কম্প্রেসর
   (খ) সেন্ট্রিফিউগাল কম্প্রেসর
   (গ) এক্সিয়াল কম্প্রেসর
   (ঘ) খ ও গ উভয়টি সঠিক
 38. Screw thread Gi Major Dia. I Minor dia. এর পার্থক্য- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) Depth of thread
   (খ) Depth of teeth
   (গ) Pitch
   (ঘ) Whole depth
 39. Motion study chart I Therbligs symbol হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) ২১টি
   (খ) ১৭টি
   (গ) ১৮টি
   (ঘ) ১৫টি
 40. Cast Iron তৈরিতে ব্যবহৃত ফার্নেস হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) Blast furnace
   (খ) Cupola furnace
   (গ) Open hearth furnace
   (ঘ) Bessemer Converter
 41. D ব্যাস বিশিষ্ট একটি সলিড শ্যাফটের সেকশন মডুলাস হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) \frac{\pi D^3}{64}
   (খ) \frac{\pi D^3}{32}
   (গ) \frac{\pi D^3}{16}
   (ঘ) \frac{\pi D^3}{64}
 42. Investment casting ব্যবহৃত হয় কোন Pattern? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) Wax Pattern
   (খ) Wooden Pattern
   (গ) Polystyrene Pattern
   (ঘ) Lead Pattern
 43. কিসের ভিত্তিতে শ্যাফট ডিজাইন করা হয়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) স্ট্রেন্থ
   (খ) রিজিডিটি
   (গ) স্ট্রেন্থ ও রিজিডিটি
   (ঘ) ক, খ, গ এর কোনটি নয়
 44. Product life cycle এর পর্যায় কতটি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) ৫টি
   (খ) ৪টি
   (গ) ৩টি
   (ঘ) ২টি
 45. “নীল ময়ূরের যৌবন” উপন্যাস এর রচয়িতার নাম- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) সুফিয়া কামাল
   (খ) রাজিয়া বেগম
   (গ) রাবেয়া খাতুন
   (ঘ) সেলিনা হোসেন
 46. কম্পিউটার মনিটরকে আরও বলা হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) DVU
   (খ) UVD
   (গ) VDU
   (ঘ) CCTV
 47. Which of the following is a compound sentence? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (a) Look before you leap
   (b) Do or die
   (c) All's well that ends well
   (d) A drowning man catches at a straw
 48. প্রধান তলে শিয়ার স্ট্রেস হল- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) সর্বোচ্চ
   (খ) সর্বনিম্ন
   (গ) সর্বোচ্চ ও সর্বনিম্নএর গড়
   (ঘ) শূন্য
 49. “কাশবনের কন্যা”-উপন্যাসের নাম কি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) সৈয়দ ওয়ালিউল্লাহ
   (খ) আবু জাফর শামসুদ্দিন
   (গ) শামসুদ্দিন আবুল কালাম
   (ঘ) জসীমউদ্দিন
 50. বঙ্গবন্ধু টি-২০ কাপ ২০২০ মোট কয়টি দল অংশ নিয়েছিল? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) ৬টি
   (খ) ৭টি
   (গ) ৪টি
   (ঘ) ৫টি
 51. Rubber এর অপর নাম- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) Plastomer
   (খ) Elastomer
   (গ) Resin
   (ঘ) Soft Plastic
 52. ২০২০ সালে শান্তিতে নোবেল পুরস্কার লাভ করে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) ইউনেস্কো
   (খ) বিশ্ব খাদ্য কর্মসূচি
   (গ) ইউনিসেফ
   (ঘ) নিরাপত্তা পরিষদ
 53. একটি বস্তুর দূরত্ব পরিবর্তন হারকে বলা হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 144]**
   (ক) ত্বরণ
   (খ) বেগ
   (গ) মোমেন্টাম
   (ঘ) কোনটি নয়
৫৪. Planer Machine এ কার্যবস্তু- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) স্থির থাকে
(খ) চলমান থাকে
(গ) উভয়ই চলমান থাকে
(ঘ) Tool চলমান থাকে
৫৫. নাট ও বোল্ট কর্তৃক গঠিত জোড়া হলো- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) টার্নিং জোড়া
(খ) রোলিং জোড়া
(গ) স্ক্রু জোড়া
(ঘ) স্ফেরিক্যাল জোড়া
৫৬. ১০০ ওয়াট ও ২০০ ভোল্ট বিশিষ্ট একটি বাতির রোধ কত? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) ১০০ ওহম
(খ) ২০০ ওহম
(গ) ৪০০ ওহম
(ঘ) ৫০ ওহম
৫৭. স্থির তরলের ক্ষেত্রে শেয়ার পীড়ন হল: **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) সর্বোচ্চ
(খ) শূন্য
(গ) অপ্রত্যাশিত
(ঘ) কোনটি নয়।
৫৮. Choose the correct option: You will help me ________ you? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) will
(b) not will
(c) won't
(d) don't
৫৯. বিশ্বস্বাস্থ্য সংস্থার (WHO) সদর দপ্তর কোথায়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) রোম
(খ) প্যারিস
(গ) হেগ
(ঘ) জেনেভা
৬০. বাংলা স্বরধ্বনি কয়টি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) ৯টি
(খ) ১১টি
(গ) ৭টি
(ঘ) ৫টি
৬১. DVD এর চেয়ে বেশী Data store করা যায় কোনটিতে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) CD Rom
(b) Floppy
(c) Blue Ray disk
(d) Red Ray disk
৬২. কোনটি সূর্য এর সমর্থক শব্দ? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) রবি
(খ) শশী
(গ) পবন
(ঘ) বসুধা
৬৩. Which of the following is correct spelt? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) Maintenance
(b) maintainence
(c) maintinance
(d) maintaince
৬৪. ঢাকা বিশ্ববিদ্যালয়ে কোন তারিখে রবীন্দ্রনাথ ঠাকুর তাঁর প্রথম বক্তৃতা করেন- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) ১৯২৬ সালের ১০ই ফেব্রুয়ারি
(খ) ১৯২৮ সালের ১০ই এপ্রিল
(গ) ১৯৩০ সালের ১০ই মে
(ঘ) ১৯৩২ সালের ১০ই আগস্ট
৬৫. কোনটি সার্থক বাক্যের গুণাবলীর মধ্যে পড়ে না- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) আকাঙ্খা
(খ) আসক্তি
(গ) যোগ্যতা
(ঘ) আসত্তি
৬৬. Choose the correct preposition: Be aware ________ lies. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) at
(b) of
(c) about
(d) to
৬৭. একটি সেকশনের যখন শেয়ার ফোর্স শূন্য তখন বেন্ডিং মোমেন্ট। **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) শূন্য
(খ) সর্বোচ্চ
(গ) সর্বনিম্ন
(ঘ) সর্বনিম্ন অথবা সর্বোচ্চ
৬৮. প্রমথ চৌধুরীর ছদ্মনাম কী? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) হুতোমপেঁচা
(খ) অবধূত
(গ) বীরবল
(ঘ) টেকচাঁদ ঠাকুর
৬৯. Which one of the following in an incorrect sentence? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) I owed it to him be honest
(b) I know that he is an honest man
(c) They know that he was honest
(d) He know him to be honest
৭০. Exclusive Economic Zone (EEZ)- এর দৈর্ঘ্য কত? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) ১০০ নটিকেল মাইল
(খ) ২০০ নটিকেল মাইল
(গ) ৪০০ নটিকেল মাইল
(ঘ) ৩০০ নটিকেল মাইল
৭১. Complete the sentence: ________ is observed as the victory Day in Bangladesh. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(a) 16th December
(b) 17th April
(c) 26th March
(d) 14th December
৭২. CMP এর পূর্ণ অভিব্যক্তি হলো- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 145]**
(ক) Common Project Method
(খ) Common Path Method a
(গ) Critical Project Method
(ঘ) Critical Path Method
৭৩. Choose the verb phrase: **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) Ought to obey
(b) what a pity
(c) at the point of
(d) With black eyes.
৭৪. বঙ্গবন্ধু ঐতিহাসিক ছয়দফা কর্মসূচি কোথায় ঘোষণা করেছিলেন? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) ইসলামাবাদ
(খ) ঢাকা
(গ) লাহোর
(ঘ) করাচী
৭৫. রাখাইনের পূর্ব নাম কী? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) রেঙ্গুন
(খ) আরাকান
(গ) কাচিন
(ঘ) শান
৭৬. Choose the correct Option: ________ are present at the metting. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) He, I and you
(b) You, he and I
(c) I, you and he
(d) He, you and I
৭৭. নিচের কোনটি নিত্য সমাস- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) রাজপুত্র
(খ) গৃহান্তর
(গ) সস্ত্রীক
(ঘ) গায়ে হলুদ
৭৮. মুক্তিযুদ্ধের পটভূমিতে লেখা কাব্যগ্রন্থ কোনটি? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) নিষিদ্ধ লোবান
(খ) নেকড়ে অরণ্য
(গ) রাত্রিশেষ
(ঘ) বন্দী শিবির থেকে
৭৯. Which one is the correct spelling? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) desiase
(b) disease
(c) desease
(d) disese
৮০. Choose the correct option: Would you mind ________ the door? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) open
(b) to open
(c) opening.
(d) opened
৮১. হালদা নদী কিসের জন্য বিখ্যাত? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) মাত্র মৎস্য ভান্ডার
(খ) পর্যটক
(গ) রামসা সাইট
(ঘ) নদী বন্দর
৮২. বাংলাদেশের রণসংগীতের রচয়িতা কে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) ফররুখ আহমদ
(খ) মহাদেব সাহা
(গ) আল মাহমুদ
(ঘ) কাজী নজরুল ইসলাম
৮৩. Fill in the blank with the right option: River is a/an ________ noun. **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) Proper
(b) abstract
(c) collective
(d) common
৮৪. What is the antonym of 'noble'? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) Grand
(b) dignified
(c) elevated
(d) mean
৮৫. What is the meaning of the phrase, 'of late'? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(a) long ago
(b) occasionally
(c) long since
(d) recently
৮৬. বাংলা সাহিত্যে সার্থক মহাকাব্যের রচয়িতা- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) নবীন চন্দ্র
(খ) মাইকেল মধুসূদন দত্ত
(গ) মীর মশাররফ হোসেন
(ঘ) কায়কোবাদ
৮৭. “রচনায় শিল্পগুণ” প্রবন্ধটি কার লেখা? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) ঈশ্বর চন্দ্র বিদ্যাসাগর
(খ) বঙ্কিম চন্দ্র চট্টোপাধ্যায়
(গ) প্যারীচাঁদ মিত্র
(ঘ) বিহারীলাল
৮৮. “দৈনিক আজাদ” পত্রিকার সম্পাদকের নাম কী? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) মোহাম্মদ আকরাম খাঁ
(খ) আহমদ ছফা
(গ) সিকান্দার আবু জাফর
(ঘ) রাহাত খান
৮৯. থার্মোডাইনামিক্স এর প্রথম সূত্রটি কোন সমীকরণ দ্বারা প্রকাশ করা হয়। **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) W = JH
(খ) H = JW
(গ) W = J + H
(ঘ) H = J + W
৯০. কান ধাতুর Duetility সর্বোচ্চ? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) Mild steel
(খ) Copper
(গ) Zinc
(ঘ) Aluminum
৯১. “লালসালু” সৈয়দ ওয়ালিউল্লাহর কোনজাতীয় রচনা? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) উপন্যাস
(খ) ছোটগল্প
(গ) নাটক
(ঘ) কাব্যগ্রন্থ
৯২. কোনটি Mechanical Property? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 146]**
(ক) Density
(খ) Thermal conductivity
(গ) Hardness
(ঘ) Porosity
৯৩. উৎপাদন এর ক্ষেত্রে কোন নির্দিষ্ট সময়ে Output/Input এর অনুপাতকে বলে- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(ক) Productivity
(খ) Efficiency
(গ) Production rate
(ঘ) Effectiveness
৯৪. ভাষার ক্ষুদ্রতম একক হচ্ছে- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(ক) ধ্বনি
(খ) বর্ণ
(গ) শব্দ
(ঘ) বাক্য
৯৫. Which one of the following is singular number? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(a) Phenomenon
(b) lice
(c) mice
(d) crises
৯৬. Dead centre কোন মেশিনে থাকে? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(a) Lathe
(b) Shaper
(c) Milling
(d) Drill
৯৭. মুক্তিযুদ্ধে “ক্র্যাক প্লাটুন” কোন শহরে সক্রিয় ছিল? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(ক) চট্টগ্রাম
(খ) খুলনা
(গ) ঢাকা
(ঘ) বরিশাল
৯৮. কোভিড ১৯ ভাইরাস বাংলাদেশে প্রথম কবে সনাক্ত হয়? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(ক) ২০ ডিসেম্বর, ২০১৯
(খ) ১৮ ফেব্রুয়ারি, ২০২০
(গ) ৮ মার্চ, ২০২০
(ঘ) ০১ এপ্রিল, ২০২০
৯৯. What is the synonym of 'pardon'? **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(a) Condemne
(b) accuse
(c) forgive
(d) convict
১০০. একটি গ্যাসের রুদ্ধতাপীয় প্রসারণ কোন সূত্র দ্বারা প্রকাশ করা হয়- **(BPSC Senior Instructor (MEW) Exam: 2021) [compact it 147]**
(a) \text{PV} = \text{constant}
(b) \text{PV}^\gamma = \text{constant}
(c) \text{PV}^\alpha = \text{constant}
(d) \text{PV}^\circ = \text{constant}
১. “যে সবে বঙ্গেতে জন্মি হিংসেই বঙ্গবাণী/ সে সব কাহার জন্ম নির্ণয় ন’ জানি।” কবিতাটি কার রচনা? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. আলাওল
B. আব্দুল হাকিম
C. চণ্ডীদাস
D. কানাইদাস
২. দ্বার বন্ধ করে ভ্রমটাকে রুধি, সত্য বলে, আমি কোথা দিয়ে ঢুকি” নীতিকবিতাংশটির রচয়িতা কে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. লালন শাহ
B. মাইকেল মধুসূদন দত্ত
C. রবীন্দ্রনাথ ঠাকুর
D. কৃষ্ণ চন্দ্র মজুমদার
৩. “For good’ এর অনুবাদ কোনটি? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. ভালর জন্য
B. ক্ষণতরে
C. বড়র জন্য
D. চিরতরে
৪. “দহরম মহরম” এর বিপরীতার্থক বাগধারা কোনটি? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. অহিনকুল
B. দুধের মাছি
C. বসন্তের কোকিল
D. জিলাপীর প্যাচ
৫. লিঙ্গান্তর হয় না, এমন শব্দ কোনটি? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. সাহেব
B. বেয়াই
C. সঙ্গী
D. কবিরাজ
৬. Our Fates Seemed Intertwined. Which one is similar to the underlined word? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. Complicated
B. Destined
C. Linked
D. Complex
৭. Find the synonym of the word Morose. **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. Annoyed
B. Gloomy
C. Moody
D. Displeased
৮. The antonym of the word Terrible is: **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. Soothing
B. Frightening
C. Scaring
D. Horrible
৯. Find the correctly spelt word. **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. Abeyence
B. Abayance
C. Abeyence
D. Abeyance
১০. A legal authorization of debtors to postpone payment is known as: **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. Moratorium
B. Deferment
C. Preemption
D. Bed debt
১১. ১০ টি বইয়ের মধ্যে ৪টি বই কত প্রকারে বাছাই করা যায়, যাতে নির্দিষ্ট দুইটি বই সর্বদা বাদ থাকে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 147]**
A. 210
B. 70
C. 45
D. 360
 12. DIGITAL শব্দটি বর্ণগুলিকে কত প্রকারে সাজানো যায় যাতে স্বরবর্ণগুলি একত্রে থাকে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 320
   B. 430
   C. 210
   D. 360
 13. \tan A = 5/12 হলে, \sin A এর মান কত? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. \frac{5}{13}
   B. \frac{3}{4}
   C. \frac{5}{17}
   D. \frac{5}{12}
 14. \sin A + \cos A = \sin B + \cos B এবং A + B = ? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. \pi
   B. 2\pi
   C. \pi/2
   D. \pi/4
 15. 3\text{N} ও 4\text{N} মানের দুটি বল লম্বভাবে ক্রিয়া করলে লব্ধির মান কত? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 2\text{N}
   B. 3\text{N}
   C. 5\text{N}
   D. 7\text{N}
 16. বিশ্ব টেলিকমিউনিকেশন দিবস কবে পালিত হয়? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 7 May
   B. 14 May
   C. 17 May
   D. 21 May
 17. বাংলাদেশে কোন তারিখ হতে আনুষ্ঠানিকভাবে কোভিড-১৯ এর টিকাদার কর্মসূচী চালু হয়? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. জানুয়ারী ৭, ২০২১
   B. জানুয়ারী ১৭, ২০২১
   C. জানুয়ারী ২৭, ২০২১
   D. জানুয়ারী ২৯, ২০২১
 18. টেস্ট ক্রিকেট বাংলাদেশের দ্রুততম উইকেটের সেঞ্চুরিয়ান বোলার কে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. সাকিব আল হাসান
   B. মোস্তাফিজুর রহমান
   C. মেহেদি হাসান মিরাজ
   D. তাইজুল ইসলাম
 19. একটি বাল্বে 60W-220V লেখা থাকলে তার রোধ কত ওহম? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 16.36
   B. 160.67
   C. 280.36
   D. 806.67
 20. 33 (ohm) resistor সার্কিটে 2amp তড়িৎপ্রবাহ চালিত হলে রেজিস্টারের ভোল্টেজ কত? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 33 V
   B. 66V
   C. 80V
   D. 132V
 21. বর্তনীতে তড়িৎ প্রবাহে সৃষ্টি করে কোনটি? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. প্রোটনের প্রবাহ
   B. নিউট্রনের প্রবাহ
   C. ইলেকট্রনের প্রবাহ
   D. তাপের প্রবাহ
 22. ১০০ ওয়াটের একটি বৈদ্যুতিক বাতি প্রতিদিন ৭ ঘণ্টা জ্বললে ২০২০ সালের ফেব্রুয়ারী মাসে কত তড়িৎ শক্তি খরচ হবে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 20.3k Wh
   B. 203k Wh
   C. 21.3k Wh
   D. 290k Wh
 23. নিচের কোন ইলেকট্রনিক্স যন্ত্র AC থেকে DC তৈরি করতে পারে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. Diode
   B. Transistor
   C. JET
   D. FET
 24. n-p-n ট্রানজিস্টরে 'P' অংশটি কী? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. নিঃসরক
   B. সংগ্রাহক
   C. ভিত্তি
   D. বিাবর্ধক
 25. একটি তেজস্ক্রিয় মৌলের অর্ধায়ু ২০০ বছর। মৌলটির ৭৫% ক্ষয় হতে কত বছর লাগবে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 150
   B. 300
   C. 400
   D. 450
 26. ট্রানজিস্টরের সাথে ডায়াড বা রেজিস্টর এবং ক্যাপাসিটর দিয়ে তৈরি পূর্ণাঙ্গ সার্কিটকে কী বলে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. Motherboard
   B. RAM
   C. Processor
   D. IC
 27. কোন বৈশিষ্ট্যের কারণে অজগ স্থায়ী স্মৃতি-স্টোরেজ হিসেবে ব্যবহার অনুপযোগী? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. Too Slow
   B. Unreliable
   C. Volatility
   D. Too Bulky
 28. In a memory-mapped I/O system, which one is not present? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. LDA
   B. IN
   C. ADD
   D. OUT
 29. সিলিকনের সাথে কোন পদার্থ যোগ করলে তা p-টাইপে পরিণত হয়? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. ফসফরাস
   B. বোরন
   C. হাইড্রোজেন
   D. কার্বন
 30. ঢাকা বেতার কেন্দ্র মিডিয়াম ওয়েভে 630Hz এ অনুষ্ঠান সম্প্রচার করে। রেডিও তরঙ্গে বেগ 3 \times 10^8\text{ ms}^{-1} হলে তরঙ্গ। দৈর্ঘ্য কত হবে? **(BTRC Sub-Assistant Director (Tech.) Exam: 2021 (IBA)) [compact it 148]**
   A. 476190m
   B. 476.19m
   C. 476190cm
   D. 476.19cm
 1. ________ is qualitative measure that refers to the number of connections between a ‘calling’ and a ‘called’ module and the complexity of these connections. **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) Coupling
   b) Cohesion
   c) Both A and B
   d) None of them
 2. Modified software goes through a phase where it is tested in the user’s site or live environment. This is referred as- **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) Alpha testing
   b) Beta testing
   c) Gamma testing
   d) Delta testing
 3. When an ongoing call or data session can communicate with two base stations at the same time, the phenomenon is known as- **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) Soft Roaming
   b) Hard Roaming
   c) Soft Handoff
   d) Hard Handoff
 4. A relationship is given below in an ER diagram. How many tables can be created (preferred) from below diagram? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) Two
   b) Three
   c) Two or Three
   d) No definite numbers
 5. In a Vigenere cipher, plaintext is *mypassword* and key is *stream*. What is the cipher text? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) d q edrdnfgf
   b) e r g e s e o h i h
   c) pm g pkpizoz
   d) f s h f t f p i j i
 6. What is the advantage of using ‘case’ while doing the update operation? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) No proper sequence is required to maintain.
   b) It is much easier to write code with ‘case’ keyword.
   c) Update with ‘case’ provides significant time improvement.
   d) None of these above.
 7. What is the name of below RAID? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) RAID 0+1
   b) RAID 1+0
   c) RAID 01
   d) RAID 10
 8. The table in below violates the Normal Form(s). Which normal form it violates? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) All of normal forms listed here
   b) 3NF
   c) 2NF
   d) 1NF
 9. English scientist ________ invented the World Wide Web in 1989. **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) Vint Cerf
   b) Robert Elliot Kahn
   c) Alan Turing
   d) Tim Berners-Lee
 10. Cyber security Triad means- **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 151]**
   a) Confidentiality, Reliability and Availability
   b) Confidentiality, Reliability and Accessibility
   c) Confidentiality, Integrity and Availability
   d) Privacy, Integrity and Approachability
 11. A line coding scheme of digital to digital conversion in given below. What is the name of this line coding technique? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 151]**
   a) NRZ
   b) RZ
   c) Manchester
   d) AMI
 12. ________ a means of regaining access to a compromised system by installing software or configuring existing software to enable remote access under attacker-defined conditions. **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 151]**
   a) Spyware
   b) Ransomware
   c) Cross-site scripting
   d) Backdoor
 13. ________ is an integration testing that is commonly used when software products are being developed. It is designed as a pacing mechanism for time-critical project, allowing the software team to assess its project on a frequent basis. **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 151]**
   a) Unit testing
   b) Function testing
   c) Regression testing
   d) Smoke testing
 14. ISO 9126 quality factors consist of – **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
   a) process-ability, consistency, usefulness, adaptability, rationality and transportability
   b) functionality, reliability, effectiveness, usability, maintainability and portability
   c) functionality, consistency, effectiveness, adaptability, maintainability and transportability
   d) None of them.
 15. Digital signature is a cryptographic method that ensures- **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
   a) Data confidentiality, integrity, availability
   b) Data integrity, authentication, non-repudiation
   c) Data privacy, integrity, accessibility
   d) Data privacy, integrity, approachability
 16. What will happen if this C program is compiled and executed? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
```c
#include<stdio.h>
int main() {
    return 0;
}

```
a) The program will show some garbage output
b) There will be a compile error and the program will not execute
c) No output (Output screen will be empty)
d) There will be a run-time error
 17. Who is known as the first computer programmer? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
   a) Alan Turing
   b) Ada Lovelace
   c) Charles Babbage
   d) None of the above
 18. Which one is the binary representation of (1234567)_{10}? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
   a) 100101101011010000000
   b) 1101011011111010001010
   c) 1001011010110100000111
   d) 111111111011010000110
 19. A prime number is a number that is divisible only by itself and 1. Which of the following is not a prime number? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
   a) 2
   b) 7
   c) 99
   d) 181
 20. What will be the output of this C program? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
```c
#include<stdio.h>
int main() {
    float p=10.5;
    int a=5*p+5.0;
    printf("%d\n",a);
    return 0;
}

```
a) 57.500000
b) 57
c) 57.000000
d) The program has errors and will not run.
 21. Which of the followings is a Web Framework built with PHP? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
   a) Laravel
   b) Django
   c) MVC
   d) Spring
 22. Which of the followings is not a data encryption algorithm? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
   a) MD5
   b) SHA1
   c) RSA
   d) AES
 23. Suppose, a Class C network address is 192.168.10.0 and subnet mask is 255.255.255.192. How many valid hosts per subnet can be obtainable? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
   a) 62
   b) 30
   c) 14
   d) 6
 24. Given a sequence, S= {1, 2, 3, 8, 15, 10}; which of the following algorithms will be the fasted to sort this sequence in ascending order? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
   a) Bubble sort
   b) Merge sort
   c) Quick sort
   d) Heap sort
 25. What will be the output of this C program? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
```c
#include<stdio.h>
int main() {
    int i=1;
    do{
        printf("%d-",i++);
    }while(i<=0);
    return 0;
}

```
a) 1-2-
b) 1-
c) No output (Output screen will be empty
d) The program will cause an infinite loop and has to be stopped manually
 26. It is a necessary requirement that the transaction is guaranteed to complete or the transaction is never started, so that an inconsistent state would not be visible except during the execution of the transaction. Such a property of transaction is known as- **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 154]**
   a) Atomicity
   b) Consistency
   c) Isolation
   d) Durability
 27. What is the output of this Java program? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 154]**
```java
class Test{
    int i=1;
}
public class main{
    public static void main(String args[]){
        Test t;
        System.out.println(t.i);
    }
}

```
a) The program will cause an runtime exception because the variable ‘i’ was not initialized
b) The program will cause an compile error because the object ‘t’ was not initialized
c) 0
d) A garbage value

 28. Interfaces in Java are meant to be– **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) Extended
   b) Implemented
   c) Overridden
   d) Used by creating object
 29. Which of the following statements is/are true about Inheritance in Java? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   i) Private methods are final
   ii) Protected methods are final
   iii) Private methods cannot be overridden
   iv) Protected members of a class are accessible by inherited classes of another package
   a) i, iii and iv
   b) i and iii only
   c) ii, iii and iv
   d) ii and iv only
 30. Which of the following is not standard compiler of C programming language? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) Microsoft Visual C/C++ Compiler
   b) GNU GCC Compiler
   c) CodeBlocks C Compiler
   d) Borland C Compiler
 31. What is the maximum value that can be stored in a 32-bit signed integer of C language? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) 10^{32}
   b) 2^{32}
   c) 2^{32}-1
   d) 2^{31}-1
 32. Which of the followings can be used in a Java Server Page (JSP) page? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) HTML
   b) AJAX
   c) JSTL
   d) All of the above
 33. Maximum how many nodes can be placed in a binary Tree of N levels? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) 2^N
   b) 2^N - 1
   c) 2^{N-1} - 1
   d) N^2
 34. Which of the following statements is not true for Java Language? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) The number 1 can be used instead of the keyword ‘true’
   b) Trying to store a fraction value in an ‘int’ datatype causes compile error
   c) Static members of a class can be accessed without creating objects of that class
   d) If not specified otherwise, the initial value of an integer variable is 0
 35. Which of the following techniques is popular for Data Compression? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
   a) Alpha-Beta pruning
   b) Checksum
   c) Huffman Coding
   d) Red Black Tree
 36. How many function calls will be performed to execute the following recursive function? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
```c
void function(int N) {
    if (N==0)
        return;
    function(N+1);
}

```
a) N
b) 2*N
c) Infinite
d) The answer can vary depending on the initial value of N
 37. Which algorithm will be the most efficient to find out the shortest path between two given nodes in an undirected weighted graph? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
   a) Breadth First Search
   b) Depth First Search
   c) Dijkstra’s algorithm
   d) Floyd-Warshall algorithm
 38. Which HTML attribute is used to hide characters of an input password? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
   a) href
   b) type
   c) tyle
   d) src
 39. Which following code syntax shows a valid use of curly braces ‘{}’ in python? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
   a) A={'one':1, 'two':2}
   b) if(A>5) {print("Hello")}
   c) A= {range(6)}
   d) B={A=5}
 40. Which of the followings is not a built-in HTML tag? **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 157]**
   a) <script>
   b) <form>
   c) <html>
   d) All of these are valid built-in HTML tags
 41. Which one is not unary operator in relational algebra? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Select
   B) Project
   C) Union
   D) Renames
 42. Which one is an entity? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Roll No.
   B) Student
   C) Passport No.
   D) Department ID
 43. Which one is not part of learning phase of machine learning? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Collect data
   B) Training data
   C) Algorithm
   D) Model
 44. Market basket analysis is part of: **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Classification
   B) Regression
   C) Clustering
   D) Association
 5. Which one is the 7$^{th}$ Generation intel processor? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 158]**
   A) Intel core i7-9850HL
   B) Intel core i5-7200U
   C) Intel core i5-9400H
   D) Intel core i9-10900K
 6. Which one is not contained in MICR code? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 158]**
   A) Account number
   B) Bank number
   C) Cheque number
   D) Country code
 7. Which one is TRUE for FIRD? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 158]**
   A) Uses electromagnetic signal
   B) Uses laser beam
   C) Uses optical signal
   D) Uses infrared
 8. Which factor is not affecting the processing speed of a computer system? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Cache memory
   B) Clock speed
   C) Monitor
   D) RAM
 9. Which one is the part of software vulnerability? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Lack of user knowledge
   B) Hidden bugs
   C) Radiation of Transmission line
   D) Passing internal information by employees
 10. Which of the following language does not need any translation? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Machine language
   B) 4GL
   C) 3GL
   D) Assembly language
 11. Which type of following errors is generated when the program is being execute? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Syntax error
   B) Semantic error
   C) Run-time error
   D) Linker error
 12. How many bit addresses of IPv6 version? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) 24
   B) 32
   C) 64
   D) 128
 13. Class C IP address is for ________ bit network. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) 24
   B) 32
   C) 64
   D) 128
 14. Which one is the modifier key of the keyboard? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Shift
   B) Backspace
   C) Esc
   D) F4
 15. Where is the Boot strapping program stored? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) ROM
   B) Hard disk
   C) CD
   D) RAM
 16. Which operation dose F1 key perform for all types of application? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) Windows shut down
   B) File open
   C) Help
   D) Save
 17. Which one is the first high level programming language? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) C
   B) COBOL
   C) FORTRAN
   D) C++
 18. Which one is the first search engine? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) Google
   B) Archie
   C) Alta vista
   D) WAIS
 19. Which programming language is used extensively for Artificial Intelligence (AI)? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) C
   B) Java
   C) J2EE
   D) Prolog
 20. Open System Interconnection (OSI) model has ________ layer. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) 6
   B) 5
   C) 9
   D) 7
 21. In computers, why is Firewall used for? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Securing the computer
   B) Data Transmission
   C) Authentication
   D) Monitoring
 22. Which one of the first 64-bit operating system? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Windows Vista
   B) Mac
   C) Linux
   D) Windows XP
 23. In computer systems, what is ‘Trojan Horse’? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Virus
   B) Malware
   C) Worm
   D) Spyware
 24. Which of the following protocols is used for receiving e-mails? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) SMTP
   B) POP3
   C) HTTP
   D) FTP
 25. In a computer, folder opening is denied by which of the following names? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) con
   B) com
   C) mak
   D) make
 26. The newest version of HTML is: **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) WML
   B) HTML5
   C) XSL
   D) HTML3
 27. Programmers being roughly out the logic they will use in the ________ stage of software SDLC. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Design
   B) Development
   C) Implementation
   D) Testing
 28. A ________ translate file of program source code into machine language. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Cluster
   B) Datagram
   C) Decoding
   D) Compiler
 29. The study of the way people work with tools is called. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) debugging
   B) programming
   C) ergonomics
   D) kinetics
 30. Viruses that take up residence in the computer’s memory and making hard to detect is called: **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) Cluster Virus
   B) Self-encrypting Virus
   C) Stealth Virus
   D) Macro Virus
 31. All programming languages require users to follow certain rules of ________. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) style
   B) syntax
   C) grammar
   D) procedures
 32. The process of making object code form one system work on another type of system is called ________. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) Porting
   B) Designing
   C) Developing
   D) Coding
 33. The job of ________ is to translate the array of dots into text. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) MICR
   B) VGA
   C) OMR
   D) OCR
 34. A barcode reader emits ________. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) sound
   B) light
   C) beeps
   D) smell
 35. In a plasma display, gas is electrified by grid of ________. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 162]**
   A) electronics
   B) phosphors
   C) electron
   D) electrodes
 36. Object code is the ________ language file that tells the CPU what to do. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) programming
   B) binary
   C) machine
   D) natural
 37. ________ is natural language statements that look like programming code. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) Source code
   B) Object code
   C) Pseudo code
   D) IPO chart
 38. Which of the following contains configuration information of a window? **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) .exe
   B) .ini
   C) .dill
   D) .chm
 39. In a spreadsheet, ________ can help you make sense of a worksheet contents. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) value
   B) Labels
   C) formula
   D) macros
 40. Flat file database is most useful for ________. **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) Large scale users
   B) Banking
   C) Small-group situation.
   D) Chain stores
 41. Which is not the steps of SQL Query processing? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 163]**
   a) Parsing
   b) Translation
   c) Optimization
   d) None
 42. Find the output: **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 163]**
```c
int a= 10, c, b;
c = (a=99)? b = 11:20;
printf("%d, %d", a, c);

```
a) 11, 99
b) 99, 11
c) 20, 11
d) 99, 20
 3. What will be the output of following code? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
```c
int x=5, y=5, z=5;
printf("%d", ++z+y-1-y+z+x++);

```
a) 15
b) 17
c) 16
d) 19
 4. A computer system has 6 type drives and each process may need 3 type drives. What is the maximum number of processes than is guaranteed to be deadlock free? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) 4
   b) 3
   c) 2
   d) None
 5. Consider the following table named “Course”-
| Course Title | Content |
|---|---|
| Web Programming | Python, CSS, JS |
What is the main problem/anomalies in the Course table? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
a) Attribute name is not correct
b) Table is larger
c) Attribute has multiple value
d) It has functional dependency
 6. Which is the immediate addressing mode in an 8086 microprocessor? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) MOV, AX, BX
   b) MOV, AX, [BX]
   c) MOV AX, 1000
   d) MOV Ax, [BX+1000]
 7. Consider the following relation-
| employee |
|---|
| ID |
| name |
| \quad first_name |
| \quad last_name |
| address |
| \quad city |
| \quad zip |
| birth_date |
| age() |
Which is the composite attribute in the “employee” relation? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
a) age, ID
b) birth_date
c) name, address
d) name, age
 8. Which information is not correct for any constructor of a java class? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) Constructor is not inherited
   b) Constructor has no return type
   c) Constructor can be final
   d) Constructor can be overloaded
 9. What will be the output of the given line? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
```c
printf("%d",sizeof(int));

```
a) 2
b) 4
c) 1
d) 8
 10. The collection of information stored in the database at a particular moment is called- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Schema
   b) Instance
   c) Relation
   d) Record
 11. In a table an attribute named interest is defined as follows, **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   
   
   When which one is the correct format for the interest columns?
   a) 65.2
   b) 7.2
   c) 19.02
   d) 1.03
 12. What is the disadvantage of multithreading? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Share the same address space
   b) Simultaneous access to multiple application
   c) Low cost communication
   d) Difficulty in managing concurrency
 13. Which one is the Data Control Language (DCL) in SQL? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Insert
   b) Create
   c) Drop
   d) Grant
 14. The time needs from the process arrival to the completion of that process is called **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Waiting time
   b) Response time
   c) Turnaround time
   d) Throughput
 15. A relationship is given below in an ER diagram How many tables can be created (preferred) from below diagram? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
```
+------------+               +-----------+
| instructor |               |  student  |
+------------+               +-----------+
| ID         |  /---------\  | ID        |
| name       |--< advisor >--| name      |
| salary     |  \---------/  | tot_cred  |
+------------+               +-----------+

```
a) No definite numbers
b) Two
c) Three
d) Two or Three
 16. We can create a “View” of a relation using the “create view_name” command in SQL analyze the following information about view and find which option is correct- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) View is not visible to user
   b) It is not a virtual table
   c) It is not a part of the logical model
   d) View cannot be updated
 17. Which information is wrong for Switch? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Stores MAC address table
   b) Operates of Data Link Layer
   c) Forward the packet to intendent computer
   d) Has no memory
 18. What is postfix expression of the string a+(b-c)*d? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) abc-d*+
   b) abcd-*+
   c) ad*bc-
   d) abc-d+*
 19. Which is not the state of a process in an Operating System? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) New
   b) Sleep
   c) Terminated
   d) Ready
 20. If we represent a binary tree using array, what will be the children of node “n”- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) 2n & 2n+1
   b) 2n & 2-n
   c) (n+1)2
   d) 2n & 2n-1
 21. Find the correct output- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
```c
int a=10, b=20;
a^=b; b^=a; a^=b;
printf("%d%d",a,b);

```
a) 20 30
b) 10 30
c) 20 10
d) Garbage Value
 22. Consider the following “staff” table **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
| staff_name | staff_dep | city |
|---|---|---|
| Riaz | CSE | Dhaka |
| Toha | EEE | Rajshahi |
What should be the query to find the output like “Riaz(CSE)” from the staff table?
a) select staff_name || ‘(‘|| staff_dep ||’)’ FROM staff where city= ‘Dhaka’
b) select staff_name ‘(‘|| staff_dep ||’)’ FROM staff where city== ‘Dhaka’
c) select staff_name || ‘(‘|| staff_dep ’)’|| FROM staff where city= ‘Dhaka’
d) select staff_name || ‘(‘ staff_dep ||’)’ FROM staff where city= ‘Rajshahi’
 23. Among the following which is not a divisor of - (1001011011110000000)_2? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) (2)_{10}
   b) (64)_{10}
   c) (128)_{10}
   d) (256)_{10}
 24. The ________ was the first wide-area packet-switching network with distributed control and one of the first networks to implement the TCP/IP protocol suite. **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) INTRANET
   b) UCLA
   c) CREN
   d) ARPANET
 25. What is the output of this Java program? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
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
 26. Which language was used to build Android Operating System? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) Java
   b) Python
   c) Kotlin
   d) Android is not an operating system
 27. In the following graph, determine the cost of the shortest path between node 1 to node 4 **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
```
     (1)
   2/   \3
   v     v
  (3)   (2)
   |-7   |1
   v     v
     (4)

```
a) 0
b) 4
c) -5
d) -\infty
 28. Suppose, Y is an integer variable whose value is either 0 or 1. Which of the following is the equivalent of the statement: if (Y==0) Y=1; else Y=0;? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) Y=1+Y
   b) Y=1-Y
   c) Y=Y-1
   d) Y=1%Y
 29. Which one is the characteristics of Stack ADT? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) Sequential Index
   b) Last-In-First Out
   c) First-In-First Out
   d) Key indexing
 30. If you are told to remove the inconsistency from the course table which normalization technique you will use- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCNF
 31. What is the maximum length of the “varchar” in the database? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) 35000
   b) 100
   c) 65535
   d) 255
 32. Which for loop statement is invalid? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) for(int x=10; k<=5; x/9)
   b) for(int x=10; x>=2; --x)
   c) for(int x=10; x>=200; x=3*x)
   d) for(int x=10; x>=0; x+=2)
 33. How many IP addresses can be assigned using IPv4 techniques? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) 2^{32}
   b) 2^{64}
   c) 4^{32}
   d) 4^{64}
 34. In which tree structure left to right subtree height differs not more than 1? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Binary tree
   b) BST
   c) AVL tree
   d) Binary Heap
 35. Assume that in a table named “student” the cgpa is calculated using the all course’s gpa. What kind of attribute cgpa is? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Multivalued
   b) Derived
   c) Simple
   d) Composite
 36. Which is the lightweight message format? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) XML
   b) JSON
   c) SQL
   d) HTML
 37. What is wrong statements for SQL? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Non-procedural language
   b) Input can be several tables
   c) Output is always a single table
   d) Output can be multiple table
 38. The ________ operation, denoted by -, allows us to find tuples that are in one relation but are not in another. **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Union
   b) Set-difference
   c) Difference
   d) Intersection
 39. Why RAID is used in database storage? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Improve performance
   b) Reduce Cost
   c) Both a & b
   d) None
 40. Which is not the steps of SQL query processing? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Parsing
   b) Translation
   c) Optimization
   d) None
 41. They while their evenings with books and games. Here while is- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   (a) Noun
   (b) Verb
   (c) Adjective
   (d) Adverb
 42. His evidence bears out, the evidence of the first witness. Here bears out means **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   (a) confirms
   (b) wcount
   (c) attacks
   (d) none
 43. The person with ________ you should ________ registering your complaint is the manager but he’s unavailable ________ the moment. **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   (a) which, be, for
   (b) who, at, for
   (c) which, who,
   (d) whom, be, at
 44. If you had come earlier, you would ________ found a good seat **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   (a) have
   (b) had
   (c) can
   (d) has
 45. People who pay their debts are trusted. Here who pay their debts is **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   (a) Phrase
   (b) Clause
   (c) Idioms
   (d) Gerund
 46. A misconception frequently held by novice writers is that sentence structure mirrors thought: the more convoluted the structure, the more ________ the ideas **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) complicated
   (b) engaged
   (c) essential
   (d) fanciful
 47. I’ve got a week to finish this, ________ is just about long enough **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) what
   (b) which
   (c) whether
   (d) who
 48. He really can’t work out, ________ he has to go to get ________ information he needs **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) what, the
   (b) which, to
   (c) what, to
   (d) for, which
 49. Reading is very good ________ children’s intellectual development **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) at
   (b) on
   (c) for
   (d) in
 50. The quote “All the glitters is not gold” is from which play of Shakespeare? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) The Merchant of Venice
   (b) Othello
   (c) Romeo and Juliet
   (d) None
 51. How many countries are members of Commonwealth? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 47
   (b) 51
   (c) 54
   (d) 61
 52. The total border district of Bangladesh? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 29
   (b) 32
   (c) 45
   (d) 53
 53. What is the position of Bangladesh in the financial Privacy Index 2020? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 29^{\text{th}}
   (b) 37^{\text{th}}
   (c) 43^{\text{th}}
   (d) 54^{\text{th}}
 54. The river Padma enters into Bangladesh through- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) Sylhet
   (b) Rajshahi
   (c) Mymensingh
   (d) Pabna
 55. The headquarter of World Economic Forum is situated in- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) Cologny
   (b) Geneva
   (c) Davos
   (d) San Francisco
 56. The term of a non-permanent member of the UN security council is- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 2 years
   (b) 3 years
   (c) 5 years
   (d) 7 years
 57. The Constitution Drafting Committee of Bangladesh formed in 1972 had- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 21 members
   (b) 24 members
   (c) 31 members
   (d) 34 members
 58. Which bank was the first to Introduce dual-currency debit card system in Bangladesh? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) Mutual Trust Bank
   (b) City Bank
   (c) Dutch Bangla Bank
   (d) AB Bank
 59. Which one of the following is not an official language of United Nations? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) Arabic
   (b) Chinese
   (c) Portuguese
   (d) Spanish
 60. The number of tribes lives in the Chattogram Hill Tracts is- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) 7
   (b) 9
   (c) 11
   (d) 15
 61. অবাক হয়ে ওর দিকে তাকিয়ে থাকে ওরা। এখানে ‘দিকে ’ শব্দটি- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) অনুসর্গ
   (b) বিশেষণ
   (c) অব্যয়
   (d) উপসর্গ
 62. ‘চশমা’ শব্দটি কোন ভাষা থেকে এসেছে? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) আরবি
   (b) ফারসি
   (c) তুর্কি
   (d) পর্তুগীজ
 63. বৃক্ষ শব্দের সমার্থক নয় কোনটি? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) তরু
   (b) বিটপী
   (c) কানন
   (d) মহীরুহ
 64. ‘আমি কি ডরাই সখি ভিখারি রাঘবে?’ কোন কারকে কোন বিভক্তি? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) কর্মে প্রথমা
   (b) অপাদানে সপ্তমী
   (c) অধিকরণে পঞ্চমী
   (d) কর্মে সপ্তমী
 65. নিচের কোনটি দেশী শব্দ? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 169]**
   (a) ডাব
   (b) ধর্ম
   (c) তোশক
   (d) হাত
 66. দুটি ব্যঞ্জনবর্ণের পরস্পর পরিবর্তন কে বলে- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 170]**
   (a) স্বরসঙ্গতি
   (b) বিষমীভবন
   (c) ধ্বনি বিপর্যয়
   (d) ব্যঞ্জনবিকৃতি
 67. ব্রাহ্মণশব্দে ‘হ্ম’-এর বিশ্লেষিত রূপ- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 170]**
   (a) হ্+ম
   (b) ক্+ধ
   (c) ক্+ষ্+ম
   (d) ক্+ষ্+ণ
 68. ‘কাজটি শেষ করার জন্য সে আদা-কাঁচকলা খেয়ে নেমেছে।’ বাক্যটি কী হারিয়েছে? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 170]**
   (a) আকাঙ্ক্ষা
   (b) আসত্তি
   (c) যোগ্যতা
   (d) পদক্রম
 69. ভাষা আন্দোলনের পটভূমিতে কবর নাটকটি রচনা করেন- **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 170]**
   (a) কবীর চৌধুরী
   (b) সৈয়দ শামসুল হক
   (c) সেলিম আল দীন
   (d) মুনীর চৌধুরী
 70. নিচের কোনটি সাধু রীতির বৈশিষ্ট্য নয়? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 170]**
   (a) তৎসম শব্দবহুল
   (b) তদ্ভব শব্দবহুল
   (c) সংলাপের অনুপযোগী
   (d) শব্দবিন্যাস সুনির্দিষ্ট
 71. Which of the following is not a web server attack type? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) DOS attack
   b) Website Defacement using SQLi
   c) Directory Traversal
   d) Password guessing
 72. The ________ loop is especially useful when you process a menu selection? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) while
   b) do-while
   c) for
   d) switch
 73. Which file format can be added to a PowerPoint show? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) .jpg
   b) .gif
   c) .wav
   d) All of the above
 74. Which shortcut key on the keyboard can be used to view slide show? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) F1
   b) F7
   c) F5
   d) F12
 75. Multiple calculation can be made in a single formula using. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) Standard Formula
   b) Array Formula
   c) Complex Formula
   d) Smart Formula
 6. The ________ block used to execute a given set of the statement whether the exception is thrown or not. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) try
   b) tryif
   c) finally
   d) thrown
 7. Which area in an excel window allow entering values and formulas? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) Title bar
   b) Menu bar
   c) Formula bar
   d) Standard tool bar
 8. Java uses a keyword ________ to preface a block of code that is likely to cause an error condition and ‘throw’ an exception. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) throw
   b) catch
   c) finally
   d) try
 9. Which of the following method(s) not included in InputStream class? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) available()
   b) reset()
   c) flush()
   d) close()
 10. A proxy firewall filters at ________. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) Physical layer
   b) Data link layer
   c) Network layer
   d) Application layer
 11. Virtual memory located on: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) RAM
   b) CPU
   c) Flash drive
   d) Hard drive
 12. A number of signal can be carried simultaneously if each signal is modulated that a different carried frequency called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) TDM
   b) FDM
   c) Frequency modulation
   d) Pulse modulation
 13. Convert the binary number (1011010)_2 into hexadecimal? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) 5B
   b) 5F
   c) 5A
   d) 5C
 14. Which of the data structure is linear type? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) Tree
   b) Binary Tree
   c) Queue
   d) Graph
 15. If List= [1,2,3,4,5] and write List[3] = List[1] then what will be List[3]? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) 1
   b) 3
   c) 2
   d) 4
 16. In programming language DRY principle makes the code. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) reusable
   b) loop forever
   c) repetitive
   d) complex
 17. K nearest neighbor algorithm is part of: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) Clustering algorithm
   b) classification algorithm
   c) association algorithm
   d) None of these
 18. If the class levels of training data set are unknown in machine learning, then it is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) classification
   b) clustering
   c) association
   d) reinforcement learning
 19. Communication path between a computer microprocessor and main memory is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) System bus
   b) ISA bus
   c) PCI bus
   d) Local bus
 20. Ice Lake CPU is intel’s code name for the processor of: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 172]**
   a) 11^{\text{th}} generation
   b) 8^{\text{th}} generation
   c) 9^{\text{th}} generation
   d) 10^{\text{th}} generation
 21. Smallest unit of bit coin is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) unit coin
   b) satoshis
   c) etherum
   d) litecoin
 22. In core i7-8650U processor, here U means: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Ultra low power
   b) Ultra high power
   c) Upgrade version
   d) Upgrade processor
 23. Which is not pipeline hazard? **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Resource hazard
   b) Control hazard
   c) Address hazard
   d) Data hazard
 24. In a block chain, a bundle of transaction is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) node
   b) block
   c) chain
   d) nonce
 25. The processor reads an instruction from memory is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Interpret instruction
   b) Fetch instruction
   c) Read instruction
   d) Fetch data
 26. A branch office, location or other data processing centers, where a newly developed system is used under normal operating conditions for several months, to test it, is called: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Beta test data
   b) String test data
   c) Alpha test data
   d) System test data
 27. Microprocessor reference that are available in the cache are called ________: **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Cache hits
   b) Cache line
   c) Cache memory
   d) All of these
 28. If any error occurs due to violation of programming rule is ________. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Syntax error
   b) Run-time Errors
   c) Linker Errors
   d) Logical Errors
 29. Running the given task in less time by increasing the degree of parallelism in DBMS is called ________. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 174]**
   a) scale up
   b) roll up
   c) speedup
   d) Data Warehouse
 30. The most common use of ________ in OOP occurs when a parent class reference is used to refer to a child class object. **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 174]**
   a) Polymorphism
   b) Inheritance
   d) Encapsulation
   d) Method overriding
 31. Which of the following memory devices is not reprogrammable? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   a) Flash memory
   b) ROM
   c) EPROM
   d) EEPROM
 32. With zero volts on both inputs, what is the ideal output of an Operational Amplifier? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   a) Equal to Zero
   b) Same as positive input voltage
   c) None of the above
   d) Same as negative input voltage
 33. A technician testing a logic circuit sees that the output of a particular INVERTER is stuck LOW while its input is pulsing. Which one of the following is the possible reason for this faulty operation? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   a) The output of the INVERTER is internally grounded
   b) The output of the INERTER is externally grounded
   c) The input being driven by output of the INVERTER is internally grounded
   d) All of the above
 34. Consider the activities A1, A2 and A3 related to email: **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   A1: Send an email from a mail client to a mail server
   A2: download an email from mailbox server to a mail client
   A3: Checking email in a web browser
   Which is the application level protocols used in each activity?
   a) A1: HTTP A2: SMTP A3: POP
   b) A1: SMTP A2: FTP A3: HTTP
   c) A1: SMTP A2: POP A3: HTTP
   d) A1: POP A2: SMTP A3: IMAP
 35. Which of the following is the role of Certification Authority (CA) in electronic commerce using public key encryption? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**
   a) To manage a private key shared among the parties to the transaction.
   b) To manage digital signatures of the parties to the transaction
   c) To manage the passwords of the parties to the transaction
   d) To issue a digital certificate for the public key of the parties to the transaction
 36. The pre order traversal of binary tree is 40, 20, 10, 30, 60, 50, 70. Which one of the is the post-order traversal of the tree? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 174]**

a) 10,20,30,40,50,60,70
b) 10,30,20,50,70,60,40
c) 40,20,60,10,30,50,70
d) 70,50,60,30,10,20,40
 7. Suppose you are implementing a Queue of size N using a non-circular linked list having a front and a rare pointer as shown in the figure. The enqueue operation inserts a new node at the front and the dequeue operation deletes a node from the rare. Which one of the following is the time complexity of the most efficient implementation of the enqueue and dequeue operations, respectively on this data structure? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 175]**
```
   +---+---+    +---+---+               +---+---+
-->|   | --+--->|   | --+----.........->|   | / |
   +---+---+    +---+---+               +---+---+
     ^                                    ^
     |                                    |
    head                                 tail

```
a) \theta(1), \theta(1)
b) \theta(1), \theta(n)
c) \theta(n), \theta(1)
d) \theta(n), \theta(n)
 8. Which device converts mechanical energy into electrical energy? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 175]**
   a) Solar cell
   b) Motor
   c) Generator
   c) Chemical cell
 9. Which protocol dynamically assigns IP addresses in a TCP/IP network? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 175]**
   a) ARP
   b) RIP
   c) SMTP
   d) DHCP
 10. Using Loopbacks (plug) which task can be done from the given list? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 176]**
   a) measuring voltage
   b) Test serial and parallel port
   c) Check series connectivity
   d) Check resistivity
 11. ```c
#include<stdio.h>
struct Testnode {
    char x,yxz;
}
int main() {
    struct Testnode node1 = {'1','2','c+3'};
    struct Testnode node2 = &node1;
    printf("%c,%c",*((char*)node2+1),*((char*)node2+2));
    return 0;
}

```
Which one is the output of the above program? **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 176]**
a) 0, f
b) 0, c+3
c) ‘0’, ‘c+6’
d) ‘0’, ‘f’

---

## Function & Recursion (3)

22. What is the following declaration for? int (*a)[10]; **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 192]**
   (a) Pointer to an array of 10 integers
   (b) Array of 10 function Pointers returning integer
   (c) A pointer of to function returning an array to 10 integers
   (d) Array of 10 integers pointers

9. Consider the following recursive function fun (x,y) . What is the value of fun (4,3) ? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 204]**
```c
int fun (int x, int y) {
    if(x==0)
        return y;
    return fun (x-1, x+y)
}

```
A) 9
B) 10
C) 12
D) 13

13. Two sets are called disjoint if the ________ is an empty set. **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 259]**
   A) intersection
   B) union
   C) difference
   D) complement

---

## Pointer (3)

1. Link list can be implement using? **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 215]**
   A) Array
   B) Pointers
   C) Both A & B
   D) None of these

37. Link List can be implemented by using? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) Array
   B) Pointer
   C) Both A and B
   D) None of above

29. Which header file should be included to use functions like malloc() and calloc()? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 271]**
   a. memory.h
   b. stdlib.h
   c. string.h
   d. dos.h

---

## Operator & Expression (7)

10. In Java, which operator is used to create an object? **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 216]**
   A) class
   B) scanf
   C) print
   D) None of these

32. In java, which operator is used to create an object? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 228]**
   A) class
   B) scanf
   C) print
   D) None

31. In java, which operator is used to create an object? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 237]**
   A) class
   B) scanf
   C) print
   D) None of above

48. In Java, which operator is used to create an object? **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 251]**
   A) class
   B) scanf
   C) print
   D) New

7. In Java, which operator is used to create an object- **(Sonali Bank Limited Assistant Programmer Preliminary Exam: 2016) [compact it 252]**
   A) Class
   B) scanf
   C) Print
   D) none of them

9. The escape sequence “\b” in C programming is ----- **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 254]**
   A) Backspace
   B) Next Line
   C) Tab
   D) None of these

18. What is the difference between mnemonic codes & machine codes? **(Bangladesh Bank Assistant Maintenance Engineer Exam: 2011) [compact it 270]**
   a. Machine codes are in shorthand English & Mnemonic codes are high level language
   b. Machine codes are in Binary & Mnemonic codes are in shorthand English
   c. Mnemonic codes are in Binary & Machine codes are in shorthand English
   d. There is no difference

---

## String (1)

17. Which of the following function returns the number of characters in a string variable? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
   a. count($variable)
   b. len($variable)
   c. strlen($variable)
   d. strcount($variable)

---
