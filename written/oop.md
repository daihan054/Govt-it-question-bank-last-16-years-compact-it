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

2. **(খ) কোন object-oriented programming language ব্যবহার করে একটি program লিখুন, যা recursive function ব্যবহার করে Fibonacci series প্রদান করবে।** **(প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪)**

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

12. **Write down the advantages of OOP over traditional structured programming language** **(Sonali & Janata Bank Officer (IT) Exam: 14.10.2023 (MIST)) [compact it 527]**

13. **What is virtual function?** **(Sheikh Hasina National Institute of Youth Development Instructor ICT Exam: 20.05.2023) [compact it 506]**

14. **Write down the Principle of OOP. What is Polymorphism? Write the name of 3 OOP language.** **(DESCO Sub-Assistant Engineer Exam: 20.05.2023 (DESCO)) [compact it 581]**

15. **(b) What is the diamond problem of multiple inheritance in C++?** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 487]**

16. **(a) Define function overloading and function overriding with examples.** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 492]**

17. **What is virtual function with example?** **(BITAC Assistant Programmer Exam: 27.10.2023 (BUTEX)) [compact it 560]**

18. **How many classes can be used in Hybrid Inheritance?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 547]**

19. **What is Abstraction and Polymorphism expalin with example?** **(Bangladesh Livestock Research Institute Assistant Maintenance Engineer Exam: 20.05.2023) [compact it 497]**

20. **(খ) কী কী ধারণার উপর ভিত্তি করে OOP প্রতিষ্ঠিত? ধারণাগুলো ব্যাখ্যা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 601]**

21. **(গ) Inheritance কী? উদাহরণসহ ব্যাখ্যা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 602]**

22. **(ক) অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং কী? এটা কেন দরকার? অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর মৌলিক ধারণাগুলো লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 619]**

23. **(গ) Overloading এবং overriding এর মধ্যে পার্থক্য কী?** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 619]**

24. **What is Polymorphism? Java language এর আলোকে ব্যাখ্যা কর।** **(BTCL Junior Assistant Manager Exam: 2022 (BUET)) [compact it 640]**

25. **(a) What is Polymorphism? Distinguish between compile time and runtime polymorphisms.** **(BPSC (Ministry of Home Affairs) Senior Computer Operator Exam: 13.09.2022 (ICT)) [compact it 694]**

26. **Write down the principle of OOP?** **(BARI Assistant Maintenance Engineer Exam: 26.08.2022) [compact it 702]** **(BARC Data Entry Officer Exam: 10.09.2022) [compact it 703]**

27. **Write down the properties/function of OOP?** **(Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer Exam: 2022) [compact it 718]**

28. **Write down the main feature of Object Oriented Programming (OOP).** **(BKSP Assistant Programmer Exam: 03.12.2022) [compact it 730]**

29. **Write a Java code with a case where you have to mentioned functionalities with override method.** **(Pubali Bank Limited; Assistant Engineer (SD) Exam: 2022) [compact it 757]**

30. **(ক) Procedural Oriented ও Object Oriented Programming Languages মধ্যে পার্থক্য কি? উভয় Language এর ২টি করে উদাহরণ দিন।** **(BPSC Assistant Programmer (ICT Ministry) Exam: 2021) [compact it 767]**

31. **(i) Object Oriented Programming এর যেকোন দুটি বৈশিষ্ট্য উদাহরণসহ ব্যাখ্যা করুন।** **(BPSC Assistant Programmer (Ministry of Commerce) Exam: 2021) [compact it 781]**

32. **(i) Object Oriented Programming এ Static binding and Dynamic binding কি? ব্যাখ্যা করুন।** **(BPSC Assistant Programmer (Ministry of Commerce) Exam: 2021) [compact it 789]**

33. **Complete the following java program.** **(BCC Assistant Programmer Exam: 12.02.2021 (BUET)) [compact it 814]**
```java
class A{
    int alpha;
    int beta;
    public A(int alpha, int beta){
        this.alpha = alpha;
        this.beta = beta;
    }
    public void display(){
        System.out.println("Alpha"+alpha+ "\nBeta"+beta);
    }
}
class Gamma extends A{
    int gamma;
    public Gamma(int alpha, int beta, int gamma){
        super(alpha, beta);
        this.gamma = gamma;
    }
    @Override
    public void display(){
        super.display();
        System.out.println("Gamma"+gamma);
    }
}
public class main{
    public static void main(String[]args){
        Gamma g = new Gamma(3,30,10);
        g.display();
    }
}
```

34. **Write a C/C++ Program that has a Class Account, Subclass Savings Account, Current Account etc with related hierarchy way.** **(6 Banks & Financial Institutions Assistant Programmer Exam: 2021) [compact it 834]**

35. **Write the definition of Inheritance, Polymorphism with coding example.** **(6 Banks & Financial Institutions Assistant Programmer Exam: 2021) [compact it 835]**

36. **Explain method overloading and Method overriding with example.** **(RAKUB Programmer (PO) Exam: 12.10.2021) [compact it 850-851]**

37. **OOP problem (Inheritance related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** **(RAKUB Maintenance Engineer (PO) Exam: 05.10.2021) [compact it 857]**

38. **Object Oriented Programming (OOP) language -এর প্রধান বৈশিষ্ট্য গুলো কী কী? দুটি OOP language -এর নাম লিখুন।** **(41th BCS Written Exam: 2021) [compact it 881]**

39. **(b) What is function overloading and operator overloading. Give example.** **(BPSC (Security Services Division) Assistant Maintenance Engineer Written Exam: 15.12.2021) [compact it 892]**

40. **১. সাব-ক্লাস এর অপর নাম কি?** **(BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) Exam: 2021) [compact it 941]**

41. **৮. অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর বৈশিষ্ট্য লিখ?** **(BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) Exam: 2021) [compact it 941]**

42. **Inheritance is one of important issues for any object oriented programming language. The main advantage of Inheritance is the ability to reuse the code. Explain in brief different types of Inheritance.** **(Sonali & Janata Bank Officer (IT) Written Exam: 2020 (DU)) [compact it 981]**

43. **Object Oriented Programming এর চারটি গুরুত্বপূর্ণ বৈশিষ্ট্য লিখুন?** **(BPSC Assistant Maintenance Engineer (CSE) Exam: 2020) [compact it 1020-1021]**

44. **What are the difference between Structure Programming and Objest Oriented Progrmamming?** **(BPSC Assistant Maintenance Engineer (ICT) Exam: 2020) [compact it 1023]**

45. **Object Oriented Programming এ Method Overloading and Method Overriding এর মধ্যে পার্থক্য কী?** **(BPSC Assistant Maintenance Engineer (ICT) Exam: 2020) [compact it 1023]**

## Class Design & Object-Oriented Modeling

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** **(Combined 2 Bank (Sonali & Janata) - Officer IT Exam: 04.10.2024 (BIBM)) [compact it 425]**

2. **What are the built in classes?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 546]**

3. **অথবা, (ক) উদাহরণসহ Class এবং Object এর মধ্যে পার্থক্য ব্যাখ্যা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 602]**

4. **(খ) উদাহরণসহ ক্লাস এবং অবজেক্ট এর মধ্যে পার্থক্য লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 619]**

5. **Define Class and Object in C++ with example.** **(BKSP Assistant Programmer Exam: 03.12.2022) [compact it 730]**

6. **What are the common activities on OOP design process?** **(Pubali Bank Limited; Assistant Engineer (SD) Exam: 2022) [compact it 756]**

7. **Write a programme to create an object of type batsman and calculate the average runs scored by the player.** **(RAKUB Programmer (PO) Exam: 12.10.2021) [compact it 846-847]**

## Encapsulation & Access Modifiers

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** **(Bangladesh Oil Gas Mineral Corporation (PetroBangla) - Assistant Manager (CSE/IT) Exam: 31.06.2024 (BUET)) [compact it 1456]**

2. **Explain the various types of access specifiers.** **(DESCO Assistant Engineer Exam: 20.05.2023 (DESCO)) [compact it 579]**

3. **Which type of variable violates encapsulation rules?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 544]** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 548]**

4. **Which members of base class cannot access to derived class?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 547]**

5. **What are the various Access Specification in C++? Explain their purpose with are example.** **(BPSC (Ministry of Home Affairs) Assistant Database Administrator Exam: 2022 (ICT)) [compact it 673]**

6. **How many specifiers are used in C++ programing?** **(CAAB Assistant Programmer (AP) Exam: 2022) [compact it 726]**

## Constructors & Destructors

1. **What is constructor function? Write the properties of it.** **(WZPGCL Assistant Engineer (CSE) Exam: 27.05.2023) [compact it 505]**

2. **Define copy constructor. What Static binding and Dynamic binding?** **(Sheikh Hasina National Institute of Youth Development Instructor ICT Exam: 20.05.2023) [compact it 507]**

3. **What is the constructor invoked in OOP?** **(BPSC (Ministry of Agriculture) Assistant Programmer Exam: 15.02.2022) [compact it 677]**

4. **What is constructor?** **(CAAB Assistant Programmer (AP) Exam: 2022) [compact it 726]**

5. **(b) Why are constructor and destructor functions used in object oriented programming? Give examples of each function in C++ or java language.** **(BPSC Sub-Assistant Engineer (Ministry of Agriculture) Exam: 2021) [compact it 804]**

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

2. **An Abstract class Player with two sub classes Bowler and Batsman, Abstract class has one abstract method average, also have constructor and a string function that display name bowler or batsman. Batsman class implement abstract function average and display result, Batsman class have run and number match data. Now write a Java Program and show Batsman average run.** **(Janata Bank Assistant System Administrator Exam: 2021) [compact it 940]**

## Exception Handling

1. **(b) What is exception? Explain how it can be used for debugging a program.** **(BPSC (Ministry of Home Affairs) Senior Computer Operator Exam: 13.09.2022 (ICT)) [compact it 695]**

2. **What is difference between exception and error in Java?** **(SPCB Sub-Assistant Programmer Exam: 2022) [compact it 737]**

3. **What is exception handling? Write with an example.** **(SPCB Sub-Assistant Programmer Exam: 2022) [compact it 738]**

## Java Programming & Methods

1. **Write a Java Code which return a value.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**

2. **Write a Java Code....** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**

3. **What does run Finalization do?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 547]**

4. **What syntax is used for calling static methods in class?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 548]**

5. **Consider the following code:** **(Bangladesh Bank - Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 436]**
```java
Public class Class A {
    Public void m1() {}
    Public void m2(int i) {}
    Public void m3(int i) {}
    Public static void m4(int i) {}
}
Public class class B extends class A {
    Public static void m1(int i) {}
    Public void m2(int i) {}
    Public void m3(string s) {}
    Public static void m4(int i) {}
}
```
**Mention which of the methods overload, override and hied supper class methods. What about the remaining method?** **(Bangladesh Bank - Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 437]**

6. **অথবা, (ক) ‘Static’ কীওয়ার্ডটি ব্যাখ্যা করার জন্যে Static Variable এবং Static Method ব্যবহার করে একটি প্রোগ্রাম লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 620]**

7. **Write a java program to counting the vowel and consonant into a given strings.** **(BOF Assistant Programmer Exam: 2022 (MIST)) [compact it 735]**

8. **Where will be the most chance of the grabage collector being invoked?** **(BDCCL Assistant Manager (Cyber Security) Exam: 14.10.2022) [compact it 756]**

9. **In Java program. Write the method in given box for the Electric bill calculation if unit is less then 100 then unit rate 4.0 take and after 100-unit rate is 5.50 and reaming unit rate is 6.00. [Bill rate 4.0 if unit<=100, Bill rate 5.50 if (unit>100 && unit<=200), Bill rate 6.00 for remaining units.]** **(BPDB Assistant Engineer (CSE) Exam: 2021 (BUET)) [compact it 816-817]**

10. **C# language এর একটি প্রোগ্রাম লিখুন?** **(PGCB Sub-Assistant Engineer (CSE) Exam: 2020 (BUET)) [compact it 1046]**

11. **Write java program for calculate electricity bill using class and object.** **(Sundharban Gas Assistant Programmer Exam: 2020) [compact it 1047-1048]**
