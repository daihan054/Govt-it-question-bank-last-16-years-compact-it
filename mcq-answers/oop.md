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
answer: a
explanation: জাভাতে একটি সাধারণ বা অ্যাবস্ট্রাক্ট ক্লাস কমা দিয়ে পৃথক করে একাধিক ইন্টারফেস ইমপ্লিমেন্ট (implement) করতে পারে (যেমন: `abstract class A implements B, C`)।

2. **Which of the following correctly describes the meaning of "Class", "&&", and "&" in Java?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*
   a) Class is a keyword to define a new class; && is a bitwise AND operator; & is a logical AND operator.
   b) Class is used to create objects; && is a bitwise OR operator; & is a logical OR operator.
   c) Class is used to create objects; && is a logical OR operator; & is a bitwise OR operator.
   d) Class is a keyword to define a new class; && is a logical AND operator; & is a bitwise AND operator.
answer: d
explanation: `class` হলো নতুন ক্লাস ডিফাইন করার সংরক্ষিত কীওয়ার্ড; `&&` হলো শর্ট-সার্কিট লজিক্যাল AND অপারেটর; এবং `&` হলো বিটওয়াইজ AND (বা নন-শর্ট-সার্কিট লজিক্যাল) অপারেটর।

3. **What is Java's machine code?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 7 (ET: BIBM)]*
   a) Java source code is directly executed by the CPU.
   b) Java source code is compiled into platform-specific machine code by the Java compiler.
   c) Java source code is compiled into assembly code, which is then executed by the CPU.
   d) Java source code is compiled into bytecode, which is interpreted or compiled to native machine code by the Java Virtual Machine (JVM).
answer: d
explanation: জাভা সোর্স কোড javac কম্পাইলার দ্বারা প্ল্যাটফর্ম-নিরপেক্ষ বাইটকোডে (.class) সংকলিত হয়, যা পরবর্তীতে JVM দ্বারা নেটিভ মেশিন কোডে রূপান্তরিত ও চালিত হয়।

4. **What type of variable should be used to store data that is important throughout an object's lifespan?** *[Combined Bank Officer (IT) 04.10.2024 compact it 14 (ET: BIBM)]*
   (a) A reference variable
   (b) A method variable
   (c) An instance variable
   (d) A parameter variable
answer: c
explanation: একটি অবজেক্টের সামগ্রিক জীবনকাল জুড়ে তার নিজস্ব স্টেট ও ডেটা সংরক্ষণের জন্য ইন্সট্যান্স ভেরিয়েবল (Instance variable) ব্যবহৃত হয়।

5. **A collection of objects that use common structure and a common behavior is knownas-** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   (a) Object
   (b) Entity
   (c) Instance
   (d) Class
answer: d
explanation: অভিন্ন গঠন (অ্যাট্রিবিউট) এবং অভিন্ন আচরণ (মেথড) বিশিষ্ট অবজেক্টসমূহের সমন্বিত সাধারণ নকশাকে Class বলা হয়।

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
answer: c
explanation: এখানে `max` এর মান 0 দিয়ে শুরু করা হয়েছে। যদি অ্যারেতে কেবল ঋণাত্মক সংখ্যা থাকে (যেমন: [-7, -3, -9]), তবে শর্ত সত্য হবে না এবং মেথডটি ভুলবশত সর্বোচ্চ মান হিসেবে 0 রিটার্ন করবে।

7. **Read the following statement in a Java program that compiles and executes-** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*
   **submarine.dive (depth); What can you say for sure?**
   (a) depth must be an int
   (b) dive must be the name of an instance field
   (c) dive must be a method
   (d) submarine must be the name of a class
answer: c
explanation: আর্গুমেন্ট ব্র্যাকেট `(depth)` সহকারে কল করার কারণে `dive` নিশ্চিতভাবেই একটি মেথডের নাম।

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
answer: b
explanation: মেথডের অভ্যন্তরে ঘোষিত লোকাল ভেরিয়েবল (এখানে `t`) স্বয়ংক্রিয়ভাবে ইনিশিয়ালাইজ হয় না। আন-ইনিশিয়ালাইজড লোকাল রেফারেন্সের ফিল্ড অ্যাক্সেস করায় কম্পাইল-টাইম এরর (The local variable t may not have been initialized) ঘটবে।

9. **Interfaces in Java are meant to be-** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)], [Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
   a) Extended
   b) Implemented
   c) Overridden
   d) Used by creating object
answer: b
explanation: জাভাতে ইন্টারফেস মূলত ক্লাস দ্বারা `implements` কীওয়ার্ডের মাধ্যমে তাদের বিমূর্ত মেথডসমূহ বাস্তবায়িত (Implemented) করার জন্য ব্যবহৃত হয়।

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
answer: a
explanation: জাভাতে 0 দৈর্ঘ্যের অ্যারে তৈরি করা সম্পূর্ণ বৈধ (`new int[0]`) এবং এর `length` প্রোপার্টির আউটপুট হবে 0।

11. **What are the inbuit classes?** *[BCC Assistant Programmer 11.11.2023 compact it 35 (ET: N/A)]*
    **Ans:** Predefined Method
answer: Predefined Classes (Built-in Classes)
explanation: জাভা ল্যাঙ্গুয়েজ এবং স্ট্যান্ডার্ড লাইব্রেরিতে পূর্ব থেকেই তৈরি থাকা ক্লাসসমূহকে (যেমন String, Math, System, Scanner) Built-in বা Inbuilt ক্লাস বলা হয়।

12. **What is syntax for call static method in class?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
    **Ans:** class name, Method name
answer: ClassName.methodName()
explanation: অবজেক্ট তৈরি না করেই সরাসরি ক্লাসের নাম ডট মেথডের নাম দিয়ে স্ট্যাটিক মেথড কল করার সিনট্যাক্স হলো `ClassName.methodName()`।

13. **What does runFinalize() do?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
    **Ans:** The runFinalization() method is a part of the Runtime class, and its purpose is to trigger the execution of the finalization methods of any objects that are awaiting finalization. Its sentence structure is as follows: public void runFinalization()
answer: Triggers execution of pending finalization methods
explanation: `runFinalization()` মেথডটি গার্বেজ কালেকশনের অপেক্ষায় থাকা সকল অবজেক্টের `finalize()` মেথড অবিলম্বে সম্পন্ন করার জন্য JVM-কে অনুরোধ জানায়।

14. **Find the correct output: System.out.print('D' + 'E'+ 'F');** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
    a) 137
    b) DEF
    c) 207
    d) DEF
answer: c
explanation: ক্যারেক্টার লিটারেলসমূহ যোগ চিহ্নে থাকলে তাদের অ্যাসকি মান যোগ হয়: 'D'(68) + 'E'(69) + 'F'(70) = 207।

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
answer: c
explanation: (a - 100) = (15 - 100) = -85 এবং (b - a) = (15 - 15) = 0। যেহেতু -85 == 0 মিথ্যা (False), তাই else ব্লকে গিয়ে `b - a` অর্থাৎ 0 প্রিন্ট হবে।

16. **Java Virtual Machine is-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*
    (a) Acts as a full-fledged hypervisor
    (b) Converts bytecodes to Operating System dependent code
    (c) Is known as the Compiler of Java programming language
    (d) Manages system memory and provides a portable execution environment for Java-bases applications
answer: d
explanation: JVM হলো এমন একটি ভার্চুয়াল মেশিন যা সিস্টেম মেমরি পরিচালনা করে (গার্বেজ কালেকশন) এবং জাভা অ্যাপ্লিকেশনের জন্য প্ল্যাটফর্ম-নিরপেক্ষ নির্বাহ পরিবেশ প্রদান করে।

17. **Which of the following is not a method of the Thread class?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
    a. sleep (long msec)
    b. stop()
    c. go()
    d. yield()
answer: c
explanation: `java.lang.Thread` ক্লাসে `sleep()`, `stop()`, `yield()`, `start()`, `run()` মেথড থাকলেও `go()` নামে কোনো মেথড নেই।

18. **Which of the following statements is correct regarding abstract classes?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
    a. An abstract class cannot be extended
    b. A subclass of a non-abstract superclass cannot be abstract
    c. A subclass can override a concreate method in a superclass to declare it abstract
    d. An abstract class cannot be used as a data type
answer: c
explanation: জাভাতে একটি অ্যাবস্ট্রাক্ট সাবক্লাস তার সুপারক্লাসের কংক্রিট মেথডকে ওভাররাইড করে পুনরায় `abstract` হিসেবে ঘোষণা করতে পারে।

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
answer: c
explanation: লোকাল রেফারেন্স ভেরিয়েবল `t` ইনিশিয়ালাইজ না করে তার মেম্বার অ্যাক্সেস করায় জাভাতে কম্পাইলার এরর (compile-time error) হবে।

20. **Converting a primitive type data into its corresponding wrapper class object instance is called-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 86 (ET: N/A)]*
    a. Boxing
    b. Wrapping
    c. Instantiation
    d. Auto boxing
answer: a
explanation: প্রিমিটিভ ডেটা টাইপকে সংশ্লিষ্ট র‍্যাপার ক্লাস অবজেক্টে রূপান্তর করার প্রক্রিয়াকে Boxing বলা হয় (কম্পাইলার স্বয়ংক্রিয়ভাবে করলে তাকে Autoboxing বলে)।

21. **Which information is not correct for any constructor of a java class?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
    a) Constructor is not inherited
    b) Constructor has no return type
    c) Constructor can be final
    d) Constructor can be overloaded
answer: c
explanation: জাভাতে কনস্ট্রাক্টরের সাথে `final`, `static`, বা `abstract` কিউওয়ার্ড ব্যবহার করা নিষিদ্ধ; তাই Constructor can be final উক্তিটি ভুল।

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
answer: d
explanation: এখানে `new Test()` দিয়ে অবজেক্ট তৈরি করা হয়েছে। অবজেক্ট তৈরির সময় পূর্ণসংখ্যা ইন্সট্যান্স ভেরিয়েবল `i` স্বয়ংক্রিয়ভাবে ডিফল্ট মান 0 পায়।

23. **Which of the following statements is/are true about Inheritance in Java?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
    i) Private methods are final
    ii) Protected methods are final
    iii) Private methods cannot be overridden
    iv) Protected members of a class are accessible by inherited classes of another package
    a) i, iii and iv
    b) i and iii only
    c) ii, iii and iv
    d) ii and iv only
answer: a
explanation: প্রাইভেট মেথড সাবক্লাসে দৃশ্যমান না হওয়ায় তা ওভাররাইড করা যায় না (কার্যত final); এবং protected মেম্বার অন্য প্যাকেজের সাবক্লাস থেকে অ্যাক্সেসযোগ্য। সুতরাং i, iii ও iv সত্য।

24. **Which of the followings can be used in a Java Server Page (JSP) page?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
    a) HTML
    b) AJAX
    c) JSTL
    d) All of the above
answer: d
explanation: একটি JSP পেজে সাধারণ HTML কোড, ক্লায়েন্ট-সাইড AJAX রিকোয়েস্ট এবং সার্ভার-সাইড JSTL ট্যাগসমূহ সবগুলোই ব্যবহার করা যায়।

25. **Which of the following statements is not true for Java Language?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
    a) The number 1 can be used instead of the keyword ‘true’
    b) Trying to store a fraction value in an ‘int’ datatype causes compile error
    c) Static members of a class can be accessed without creating objects of that class
    d) If not specified otherwise, the initial value of an integer variable is 0
answer: a
explanation: জাভাতে boolean একটি কঠোর স্বতন্ত্র টাইপ, যেখানে 1 বা 0 ব্যবহার করা যায় না; শুধুমাত্র `true` অথবা `false` ব্যবহার করতে হয়।

26. **Find the output of following Java code line: System.out.println (math.floor (-7.4)** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*
    A) -7
    B) -7.4
    C) -8
    D) -7.2
answer: C
explanation: `Math.floor()` মানটির চেয়ে ছোট বা সমান নিকটবর্তী পূর্ণসংখ্যা রিটার্ন করে। -7.4 এর চেয়ে ছোট নিকটবর্তী পূর্ণসংখ্যা হলো -8।

27. **Which of the following is not an operator in Java?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*
    A) instanceof
    B) sizeof
    C) new
    D) All of this
answer: B
explanation: C/C++ এ `sizeof` অপারেটর থাকলেও জাভাতে কোনো `sizeof` অপারেটর নেই।

28. **In Java, which operator is used to create an object?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 216 (ET: AUST)]*
    A) class
    B) scanf
    C) print
    D) None of these
answer: D
explanation: জাভাতে হিপ মেমরিতে অবজেক্ট তৈরি করতে `new` অপারেটর ব্যবহৃত হয়, যা অপশনে না থাকায় সঠিক উত্তর None of these।

29. **Which of the following produce an answer that is closest in value to a double, d, while not being greater than d?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)], [Combined Bank Maintenance Engineer 2018 compact it 229 (ET: N/A)]*
    A) (int.Math.min(d))
    B) (int.Math.max(d))
    C) int.Math.abs(d))
    D) (int).Math.floor(d))
answer: D
explanation: `Math.floor(d)` মেথড d-এর মানের চেয়ে বড় না হয়ে তার নিকটতম সর্বনিম্ন পূর্ণসংখ্যার মান প্রদান করে।

30. **Which keyword must be used to inherit class in java?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
    A) extends
    B) super
    C) this
    D) extend
answer: A
explanation: জাভাতে একটি ক্লাসকে অন্য ক্লাস দ্বারা ইনহেরিট করতে `extends` কীওয়ার্ড ব্যবহার করা হয়।

31. **A class that is inherited in java is called a ________.** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
    A) sub class
    B) super class
    C) state class
    D) implement class
answer: B
explanation: যে ক্লাসটিকে ইনহেরিট করা হয় (The class that is inherited) তাকে প্যারেন্ট ক্লাস বা Super class বলা হয়।

32. **Which one of these interfaces is implemented by thread class?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) Set
    B) Connections
    C) Runnable
    D) None of above
answer: C
explanation: জাভার `Thread` ক্লাসটি `Runnable` ইন্টারফেস ইমপ্লিমেন্ট করে থাকে।

33. **In java, which operator is used to create an object?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) class
    B) scanf
    C) print
    D) None of above
answer: D
explanation: জাভাতে অবজেক্ট তৈরির জন্য `new` অপারেটর ব্যবহৃত হয়।

34. **In java, which one will be used for comprising whether the two String object str1 and str2 are same?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*
    A) str1=str2
    B) str1.equalsIgnoreCase(str2)
    C) str1==str2
    D) All of above
answer: B
explanation: দুটি স্ট্রিং অবজেক্টের কনটেন্ট বা মান একই কিনা তা তুলনা করতে `equals()` বা `equalsIgnoreCase()` মেথড ব্যবহার করতে হয়। (`==` কেবল মেমরি অ্যাড্রেস তুলনা করে)।

35. **Which of these data types is used by operating system to manage the Recursion in Java?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
    A) Array
    B) Stack
    C) Queue
    D) Tree
answer: B
explanation: রিকার্সিভ ফাংশন কলের এক্সিকিউশন ট্র্যাক করতে অপারেটিং সিস্টেম ও JVM স্ট্যাক (Call Stack) ব্যবহার করে।

36. **Which of the following is an incorrect statement about packages?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
    A) Package defines a namespace in which classes are stored
    B) A package can contain other packages within
    C) A package can be renamed without renaming the directory, in which the classes are stored
    D) Java uses file system directories to store packages
answer: C
explanation: জাভাতে প্যাকেজের নাম এবং ফাইল ডিরেক্টরির নাম পরস্পর অঙ্গাঙ্গিভাবে জড়িত; ডিরেক্টরির নাম না বদলে প্যাকেজের নাম পরিবর্তন করা সম্ভব নয়।

37. **Multiple inheritances in Java can be implemented using which of the following?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
    A) Interfaces
    B) Multithreading
    C) Protected methods
    D) Private methods
answer: A
explanation: ক্লাসের ক্ষেত্রে মাল্টিপল ইনহেরিটেন্স সমর্থিত না হলেও একাধিক Interface ইমপ্লিমেন্ট করার মাধ্যমে জাভাতে মাল্টিপল ইনহেরিটেন্সের সুবিধা পাওয়া যায়।

38. **Which component is used to compile, debug and execute in Java program?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
    A) JVM
    B) JDK
    C) JIT
    D) JRE
answer: B
explanation: Java Development Kit (JDK)-এ কম্পাইলার (javac), এক্সিকিউশন এনভায়রনমেন্ট (JRE/JVM) এবং ডিবাগারসহ প্রোগ্রাম তৈরির সকল উপাদান অন্তর্ভুক্ত থাকে।

39. **int C=10; System.out.println(C--); gives a output of-** *[Combined Bank Senior Officer (IT) 2018 compact it 224 (ET: DU)]*
    A) 10
    B) 11
    C) 9
    D) 8
answer: A
explanation: Post-decrement (`C--`) অপারেশনে বর্তমান মান (১০) আগে ব্যবহৃত বা প্রদর্শিত হয়, পরবর্তীতে এর মান ১ কমে ৯ হয়।

40. **In java, which operator is used to create an object?** *[Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)]*
    A) class
    B) scanf
    C) print
    D) None
answer: D
explanation: জাভাতে অবজেক্ট তৈরির অপারেটর হলো `new`।

41. **Which of the keywords can be used in a subclass to call the constructor of superclass?** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
    A) Extent
    B) Extends
    C) Super
    D) This
answer: C
explanation: সাবক্লাসের কনস্ট্রাক্টর থেকে সুপারক্লাসের কনস্ট্রাক্টরকে ইনভোক করতে `super()` কীওয়ার্ড ব্যবহার করা হয়।

42. **Which of the following is a valid declaration of an object of class Box?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
    A) Box obj = new Box();
    B) Box obj = new Box;
    C) obj = new Box();
    D) new Box obj;
answer: A
explanation: জাভাতে ক্লাস অবজেক্ট ডিক্লেয়ার ও ইনিশিয়ালাইজ করার সঠিক সিনট্যাক্স হলো `Box obj = new Box();`।

43. **In Java, which operator is used to create an object-** *[Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*
    A) Class
    B) scanf
    C) Print
    D) none of them
answer: D
explanation: জাভাতে অবজেক্ট তৈরির জন্য `new` অপারেটর ব্যবহৃত হয়।

44. **A class that is inherited in java is called a ________.** *[Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*
    A) Subclass
    B) Super class
    C) Static class
    D) Implement class
answer: B
explanation: যে মূল ক্লাসটি থেকে অন্য ক্লাস তৈরি বা ইনহেরিট করা হয়, তাকে Super class বলা হয়।

45. **In Java, which operator is used to create an object?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*
    A) class
    B) scanf
    C) print
    D) New
answer: D
explanation: জাভাতে অবজেক্ট ইনস্ট্যানশিয়েট করার মূল অপারেটর হলো `new`।

46. **Java source code is compiled into ________** *[BREB Assistant General Manager (IT) 2016 compact it 256 (ET: N/A)]*
    A) Source Code
    B) Byte Code
    C) Object
    D) .exe
answer: B
explanation: জাভা সোর্স কোড (.java) কম্পাইল হয়ে মধ্যবর্তী প্ল্যাটফর্ম-নিরপেক্ষ বাইটকোডে (.class) পরিণত হয়।

47. **Which one of these lists contains only Java programming language keywords?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
    a. class, if, void, long, int, continue
    b. goto, instanceof, native, finally, default, throws
    c. try, virtual, throw, final, volatile, transient
    d. strictfp, constant, super, implements, do
answer: a
explanation: প্রদত্ত তালিকায় `class, if, void, long, int, continue`—প্রতিটি শব্দই জাভা প্রোগ্রামিং ভাষার সক্রিয় ও বৈধ সংরক্ষিত কীওয়ার্ড (Keyword)।

48. **Which method must be defined by a class implementing java.lang.Runnable interface?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
    a. void run()
    b. public void run()
    c. public void start()
    d. void run(int priority)
answer: b
explanation: `java.lang.Runnable` ইন্টারফেসে `public void run()` মেথডটি সংজ্ঞায়িত থাকে। ইন্টারফেসের মেথড ডিফল্টভাবে পাবলিক হওয়ায় ইমপ্লিমেন্টকারী ক্লাসে অবশ্যই `public void run()` হিসেবেই সংজ্ঞায়িত করতে হয়।

## Polymorphism & Overloading (16)

1. **Which of the following operators should be preferred to overload as a global function rather than a member method?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xxii (ET: DU)]*
   (a) Postfix ++
   (b) Comparison Operator
   (c) Insertion Operator <<
   (d) Prefix++
answer: c
explanation: Stream Insertion (`<<`) এবং Extraction (`>>`) অপারেটরের বাম পাশের অপারেন্ডটি একটি স্ট্রিম অবজেক্ট (যেমন `ostream& cout`), যা ইউজার ক্লাসের অবজেক্ট নয়। তাই একে ক্লাসের মেম্বার মেথড হিসেবে না করে গ্লোবাল বা ফ্রেন্ড ফাংশন হিসেবে ওভারলোড করা হয়।

2. **Which of the following operators cannot be overloaded in C/C++ ?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*
   (a) Bitwise right shift assignment
   (b) Address of
   (c) Indirection
   (d) Structure reference
answer: d
explanation: C++ এ মেম্বার সিলেকশন বা স্ট্রাকচার রেফারেন্স ডট অপারেটর `.` (dot), পয়েন্টার-টু-মেম্বার `.*`, স্কোপ রেজোলিউশন `::`, টার্নারি `?:` এবং `sizeof` অপারেটরসমূহ ওভারলোড করা যায় না।

3. **A feature of Object oriented programming languages that allows a specific routine to use variables of different types at different times, is called OOP?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** Polymorphism
answer: Polymorphism
explanation: পলিমরফিজম (বহুরূপিতা) অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ের এমন একটি বৈশিষ্ট্য যা একই ইন্টারফেস বা মেথড নাম ব্যবহার করে বিভিন্ন ডেটা টাইপ বা ক্লাসের অবজেক্ট পরিচালনা করার সুযোগ দেয়।

4. **A function having more than one distinct meaning is called ______ function** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*
   (ক) Parameter
   (খ) Prototype
   (গ) Overloaded
   (ঘ) Polymorphism
answer: গ
explanation: একই নামের একটি ফাংশন যখন প্যারামিটারের তালিকাভেদে ভিন্ন ভিন্ন উদ্দেশ্যে একাধিকবার সংজ্ঞায়িত হয়, তখন তাকে ওভারলোডেড (Overloaded) ফাংশন বলা হয়।

5. **The feature in object-oriented programming that allows the same operation to be carried out differently, depending on the object, is-** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 85 (ET: N/A)]*
   a. Inheritance
   b. Polymorphism
   c. Over functioning
   d. Overriding
answer: b
explanation: অবজেক্টের প্রকারভেদে একই অপারেশন ভিন্ন ভিন্ন রূপে কার্যকর হওয়ার সক্ষমতাকে পলিমরফিজম (Polymorphism) বলে।

6. **The most common use of ________ in OOP occurs when a parent class reference is used to refer to a child class object.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 174 (ET: N/A)]*
   a) Polymorphism
   b) Inheritance
   d) Encapsulation
   d) Method overriding
answer: a
explanation: প্যারেন্ট ক্লাসের রেফারেন্স দ্বারা চাইল্ড ক্লাসের অবজেক্ট ধারণ করে রানটাইমে গতিশীল মেথড ডেসপ্যাচ নিশ্চিত করাই হলো পলিমরফিজমের (Polymorphism) সবচেয়ে সাধারণ ও কার্যকর ব্যবহার।

7. **Which of the following is the destructor of class Vehicle?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*
   A) *Vehicle()
   B) ~Vehicle ()
   C) ~Vehicle (int value)
   D) *Vehicle (int value)
answer: B
explanation: C++ এ ডিস্ট্রাক্টরের নাম ক্লাসের নামের অনুরূপ হয় যার পূর্বে টিল্ডা (`~`) প্রতীক থাকে এবং এর কোনো আর্গুমেন্ট বা রিটার্ন টাইপ থাকে না।

8. **The operator that cannot be overloaded is ________.** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*
   A) ++
   B) ()
   C) ~
   D) ::
answer: D
explanation: C++ এ স্কোপ রেজোলিউশন অপারেটর `::` কোনোভাবেই ওভারলোড করা যায় না।

9. **Which functions overloads the ">>" operator?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*
   A) gt()
   B) more()
   C) ge()
   D) None of this
answer: D
explanation: C++ এ `>>` অপারেটর ওভারলোড করতে মেথডের নাম হতে হয় `operator>>`; gt(), more() বা ge() নামে কোনো অপারেটর ওভারলোডিং ফাংশন হয় না।

10. **Which of the following operator functions cannot be global i.e. must be a member function?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*
    A) Conversion operator
    B) new
    C) delete
    D) all of these
answer: A
explanation: C++ এ টাইপ কনভার্সন অপারেটর (যেমন `operator int()`), অ্যাসাইনমেন্ট অপারেটর `=`, সাবস্ক্রিপ্ট `[]` এবং অ্যারো `->` অপারেটরসমূহকে অবশ্যই ক্লাসের মেম্বার ফাংশন হতে হয়; এগুলো কখনোই গ্লোবাল ফাংশন হতে পারে না।

11. **Which of the following is the destructor for class “vehicle”?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
    A) *vehicle()
    B) *vehicle (int value)
    C) ~vehicle()
    D) ~vehicle (int value)
answer: C
explanation: “vehicle” ক্লাসের ডিস্ট্রাক্টরের সিনট্যাক্স হলো `~vehicle()`।

12. **Which operator that can be overloaded is?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) ++
    B) ::
    C) . (dot)
    D) 0
answer: A
explanation: অপশনগুলোর মধ্যে ইনক্রিমেন্ট অপারেটর `++` ওভারলোডযোগ্য। অন্যদিকে `::` এবং `.` অপারেটর ওভারলোড করা যায় না।

13. **How many instances of an abstract can be created?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) 0
    B) 1
    C) 2
    D) 13
answer: A
explanation: একটি অ্যাবস্ট্রাক্ট ক্লাসের কোনো প্রত্যক্ষ অবজেক্ট বা ইন্সট্যান্স তৈরি করা যায় না; তাই এর ইন্সট্যান্স সংখ্যা শূন্য (0)।

14. **If same message is passed to objects of several different classes and all of those can respond in a different way, what is this feature called?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
    A) Inheritance
    B) Overloading
    C) Polymorphism
    D) Overriding
answer: C
explanation: ভিন্ন ভিন্ন ক্লাসের অবজেক্টে একই মেসেজ পাঠানো হলে তাদের নিজ নিজ ক্লাসের সংজ্ঞানুযায়ী ভিন্নভাবে সাড়া দেওয়াকে পলিমরফিজম (Polymorphism) বলা হয়।

15. **What is the process of defining two or more methods within the same class that have same name but different parameters declaration?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
    A) Method overriding
    B) Method overloading
    C) Method hiding
    D) Method duplicating
answer: B
explanation: একই ক্লাসে একই নামের একাধিক মেথড যদি ভিন্ন ভিন্ন প্যারামিটার তালিকা নিয়ে সংজ্ঞায়িত হয়, তবে সেই প্রক্রিয়াকে Method overloading বলা হয়।

16. **Overloaded functions are ________** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*
    a. Very long functions that can hardly run
    b. One function containing another one or more functions inside it
    c. Two or more functions with same name but different number of parameter or type
    d. None of above
answer: c
explanation: ওভারলোডেড ফাংশন বলতে বোঝায় একই নামের একাধিক ফাংশন যাদের প্যারামিটার সংখ্যা বা ডেটা টাইপের মধ্যে ভিন্নতা রয়েছে।

## OOP Concepts & Principles (11)

1. **Which of the following is not property of the Object Oriented Programming Concept?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   a) Encapsulation
   b) Inheritance
   c) Exception
   d) Abstraction
answer: c
explanation: অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ের (OOP) মূল স্তম্ভ চারটি: Encapsulation, Abstraction, Inheritance এবং Polymorphism। Exception হলো ত্রুটি মোকাবিলার একটি প্রক্রিয়া, যা OOP-র মৌলিক বৈশিষ্ট্য নয়।

2. **Which of the following modifiers cannot be applied to a method in C++?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 54 (ET: N/A)]*
   (ক) Protected
   (খ) Private
   (গ) Public
   (ঘ) Abstract
answer: ঘ
explanation: C++ প্রোগ্রামিং ভাষায় `abstract` নামে কোনো কিউওয়ার্ড বা মেথড মডিফায়ার নেই (C++ এ অ্যাবস্ট্রাক্ট মেথড তৈরিতে Pure Virtual Function `= 0` ব্যবহৃত হয়)।

3. **Which is not the feature of JAVA OOP?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 180 (ET: N/A)]*
   a) Multiple Inheritance
   b) Multi-level inheritance
   c) Compile time Polymorphism
   d) Runtime Polymorphism
answer: a
explanation: ডায়মন্ড সমস্যা ও কোড জটিলতা পরিহার করতে জাভাতে ক্লাসের ক্ষেত্রে সরাসরি মাল্টিপল ইনহেরিটেন্স (Multiple Inheritance) সমর্থন করে না (ইন্টারফেসের মাধ্যমে তা অর্জন করা হয়)।

4. **Object Oriented programming এর বৈশিষ্ট্য কোনটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*
   A) Polymorphism
   B) Friend function
   C) Structure
   D) Loop
answer: A
explanation: পলিমরফিজম (Polymorphism) হলো অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ের প্রধান চারটি মৌলিক বৈশিষ্ট্যের একটি।

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 189 (ET: N/A)]*
   A) Inheritance
   B) Abstraction
   C) Polymorphism
   D) Overloading
answer: B
explanation: এনক্যাপসুলেশন (Encapsulation) অভ্যন্তরীণ ডেটা ও জটিল বাস্তবায়ন পদ্ধতি আড়াল (Data Hiding) করার মাধ্যমে বাইরে প্রয়োজনীয় ইন্টারফেস প্রকাশ করে, যা মূলত Abstraction নিশ্চিত করে।

6. **Which of the following provides a programmer with the facility of using object of a class inside other classes?** *[Probashi Kallyan Bank Programmer: 2019 compact it 209 (ET: AUST)]*
   A) Inheritance
   B) Abstraction
   C) Encapsulation
   D) Composition
answer: D
explanation: একটি ক্লাসের অবজেক্টকে অন্য কোনো ক্লাসের মেম্বার হিসেবে ধারণ বা ব্যবহার করার ধারণাকে Composition (বা Aggregation / "has-a" relationship) বলা হয়।

7. **Which one is pure object-oriented language?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 219 (ET: N/A)]*
   A) C++
   B) C+
   C) Java
   D) None
answer: D
explanation: খাঁটি বা পিওর অবজেক্ট ওরিয়েন্টেড ভাষায় সবকিছুই অবজেক্ট হতে হয়। জাভা ও C++ কোনোটিই পিওর নয় কারণ এগুলোতে প্রিমিটিভ ডেটা টাইপ (int, float ইত্যাদি) রয়েছে যা অবজেক্ট নয়। Smalltalk হলো একটি খাঁটি অবজেক্ট ওরিয়েন্টেড ভাষা।

8. **Which is not feature of object-oriented programming?** *[Combined Bank Maintenance Engineer 2018 compact it 225 (ET: N/A)]*
   A) inheritance
   B) recursion
   C) encapsulation
   D) abstraction
answer: B
explanation: রিকার্শন (Recursion) একটি সাধারণ ফাংশনাল অ্যালগরিদমিক কৌশল; এটি কোনো অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং প্যারাডাইমের মূল বৈশিষ্ট্য নয়।

9. **Which is not a feature of object-oriented programming?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*
   A) Inheritance
   B) Encapsulation
   C) Recursion
   B) Abstraction
answer: C
explanation: রিকার্শন (Recursion) OOP-র বৈশিষ্ট্য নয়।

10. **Which one of the following is the core property of Object-Oriented Programming?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 259 (ET: N/A)]*
    A) Encapsulation, inheritance
    B) Encapsulation, Object
    C) polymorphism, overloading
    D) Encapsulation, polymorphism and inheritance
    Answer: D
explanation: অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ের সবচেয়ে প্রধান ও মৌলিক স্তম্ভগুলো হলো Encapsulation, Polymorphism এবং Inheritance (পাশাপাশি Abstraction)।

11. **In object Oriented Programming, a property can be accessed from ________** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
    A) Anywhere the project
    B) Only from its own class
    C) Parent class
    D) Child class
answer: B
explanation: এনক্যাপসুলেশন নীতিতে ক্লাসের ফিল্ড বা প্রোপার্টিগুলো সাধারণত `private` রাখা হয়, যা কেবল সংশ্লিষ্ট ক্লাসের নিজস্ব মেথড দ্বারাই সরাসরি অ্যাক্সেসযোগ্য (Only from its own class)। (পাবলিক হলে যেকোনো স্থান থেকে অ্যাক্সেস করা যায়)।

## Encapsulation & Access Modifiers (7)

1. **Which of the following does NOT achieve encapsulation?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*
   (a) Using private access specifier
   (b) Using classes in object-oriented programming
   (c) Using getter and setter methods
   (d) Using global variables
answer: d
explanation: গ্লোবাল ভেরিয়েবল (Global variables) যে কোনো জায়গা থেকে সরাসরি অ্যাক্সেস ও পরিবর্তনযোগ্য হওয়ায় এটি ডেটা হাইডিং ও এনক্যাপসুলেশন লঙ্ঘন করে।

2. **Which variable violates the principle of ecvapsulation?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** Gobal variable
answer: Global variable
explanation: গ্লোবাল ভেরিয়েবল কোনো নির্দিষ্ট ক্লাসের অভ্যন্তরে আবদ্ধ না থেকে উন্মুক্ত অবস্থায় থাকে, যা এনক্যাপসুলেশন নীতির পরিপন্থী।

3. **Which of the following is a technique for hiding the internal implementation details of an object?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 115 (ET: N/A)]*
   a) Encapsulation
   b) Polymorphism
   c) Inheritance
   d) All of the above
answer: a
explanation: অবজেক্টের অভ্যন্তরীণ ডেটা ও বাস্তবায়নের বিবরণ বাইরে থেকে গোপন রাখার (Data Hiding) প্রাথমিক কৌশল হলো এনক্যাপসুলেশন (Encapsulation)।

4. **What is the characteristic of OOP programming that allows binding data and methods to work as a unit?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)]*
   a. Inheritance
   b. Encapsulation
   c. Polymorphism
   d. Projection
answer: b
explanation: ডেটা এবং সেই ডেটা নিয়ন্ত্রণকারী মেথডসমূহকে একক ইউনিটে (Class) আবদ্ধ করার ধারণাকে এনক্যাপসুলেশন (Encapsulation) বলা হয়।

5. **Encapsulation এর মাধ্যমে object oriented programming এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?** *[Bangladesh Bank Data Entry Operator (IT) 2020 compact it 189 (ET: N/A)]*
answer: Data Hiding (ডেটা হাইডিং / নিরাপত্তা)
explanation: এনক্যাপসুলেশনের মাধ্যমে ক্লাসের ডেটা মেম্বারসমূহ প্রাইভেট রেখে অননুমোদিত সরাসরি পরিবর্তন রোধ করা হয়, যা ডেটা হাইডিং (Data Hiding) নিশ্চিত করে।

6. **In C++, the idea to hiding the details of how something is implemented is known as** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) inheritance
   B) encapsulation
   C) recursion
   D) polymorphism
answer: B
explanation: কোনো ফাংশন বা অবজেক্টের অভ্যন্তরীণ জটিল বাস্তবায়ন পদ্ধতি ক্লাসের ভেতরে আড়াল রাখাকে Encapsulation বলা হয়।

7. **In C++, the idea to hiding the details of how something is implemented is known as-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 251 (ET: N/A)]*
   A) inheritance
   B) polymorphism
   C) recursion
   D) encapsulation
answer: D
explanation: অবজেক্টের অভ্যন্তরীণ ডেটা ও বাস্তবায়নের বিশদ আড়াল রাখার পদ্ধতি হলো Encapsulation।

## Inheritance (6)

1. **When a class serves as base class for many derived classes, the situation is called-** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) Polymorphism
   b) hierarchical inheritance
   c) Hybrid inheritance
   d) Multipath inheritance
answer: b
explanation: একটি বেস ক্লাস থেকে যখন একাধিক সাবক্লাস ইনহেরিট করে বিস্তার লাভ করে, তখন সেই ইনহেরিটেন্স কাঠামোকে হায়ারার্কিকাল ইনহেরিটেন্স (Hierarchical inheritance) বলা হয়।

2. **Which language is not support OOP four Inheritance feature?** *[BREB Assistant Programmer 2023 compact it 33 (ET: N/A)]*
   (a) Smaltalk
   (b) Java
   (c) C
   (d) C++
answer: c
explanation: সি (C) একটি স্ট্রাকচার্ড/প্রসিডিউরাল ভাষা; এতে অবজেক্ট ও ইনহেরিটেন্সের কোনো সুবিধা নেই।

3. **Which type of members can't accessed in derived classes of a base class?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** Private members
answer: Private members
explanation: বেস ক্লাসের প্রাইভেট মেম্বারসমূহ শুধুমাত্র সেই ক্লাসের অভ্যন্তরে সীমাবদ্ধ থাকে; ডিরাইভড ক্লাস থেকে তাদের সরাসরি অ্যাক্সেস করা যায় না।

4. **What is default level of inheritance has to be specified in C++?** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*
   (a) Public
   (b) Private
   (c) Protected
   (d) Compile time error
answer: b
explanation: C++ এ ক্লাসের ইনহেরিটেন্সের ধরন (Access specifier) উল্লেখ না করা থাকলে ডিফল্টভাবে তা `private` ইনহেরিটেন্স হিসেবে গণ্য হয়।

5. **A derived class inherits attributes from a-** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
   A) Super Class
   B) Sub Class
   C) Inner Class
   D) Upper Class
answer: A
explanation: একটি সাবক্লাস বা Derived class তার প্যারেন্ট বা Super class থেকে বৈশিষ্ট্য ও মেথড উত্তরাধিকার সূত্রে লাভ করে।

6. **How to access the overridden method of base class from the derived class?** *[Combined Bank Senior Officer (IT) 2018 compact it 222 (ET: DU)]*
   A) Using arrow operator
   B) Using dot operator
   C) Using scope resolution operator
   D) Can't be accessed once overridden
answer: C
explanation: C++ এ সাবক্লাস থেকে বেস ক্লাসের ওভাররিডেন মেথড কল করতে স্কোপ রেজোলিউশন অপারেটর `::` ব্যবহৃত হয় (যেমন: `BaseClass::methodName()`)।

## Constructors & Destructors (6)

1. **Which of the following is true regarding a constructor in Object Oriented Programming?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) May consist of a return type
   b) Does not consist of any return type
   c) has some return type
   d) None of the above
answer: b
explanation: অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিংয়ে কনস্ট্রাক্টরের কোনো রিটার্ন টাইপ থাকে না (এমনকি void-ও নয়)।

2. **A constructor is a special type of-** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*
   (a) Class
   (b) Field
   (c) Method
   (d) Property
answer: c
explanation: কনস্ট্রাক্টর হলো একটি বিশেষ ধরণের মেথড (Special Method / Member Function), যার নাম ক্লাসের নামের হুবহু সমান হয় এবং অবজেক্ট তৈরির সময় স্বয়ংক্রিয়ভাবে কল হয়।

3. **Which part of a class is invoked when an object is initialized in java?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 239 (ET: N/A)]*
   A) constructor
   B) fields
   C) methods
   D) class
answer: A
explanation: জাভাতে `new` অপারেটর দিয়ে অবজেক্ট তৈরি বা ইনিশিয়ালাইজ করার মুহূর্তে ক্লাসের কনস্ট্রাক্টর (Constructor) ইনভোক বা কল হয়।

4. **Which operator is used to declare the destructor in C++?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
   A) #
   B) ~
   C) @
   D) $
answer: B
explanation: C++ এ ডিস্ট্রাক্টর ডিক্লেয়ার করার জন্য ক্লাসের নামের ঠিক পূর্বে টিল্ডা (`~`) অপারেটর ব্যবহৃত হয়।

5. **Object being passed to a copy constructor-** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
   A) Must be passed by reference
   B) Must not be mentioned in parameter list
   C) Must be passed with integer type
   D) Must be passed by value
answer: A
explanation: C++ এ কপি কনস্ট্রাক্টরে অবজেক্টকে অবশ্যই রেফারেন্সের মাধ্যমে পাঠাতে হয় (Pass by reference, যেমন: `MyClass(const MyClass &obj)`); অন্যথায় ভ্যালু পাস করতে গেলে আবারও কপি কনস্ট্রাক্টর কল হয়ে ইনফাইনাইট রিকার্শন তৈরি হবে।

6. **Does constructor overloading include different return types for constructors to be overloaded?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
   A) Yes, if return types are different, signature becomes different
   B) Yes, because return types can differentiate two functions
   C) No, return type can't differentiate two functions
   D) No, constructors don't have any return type
answer: D
explanation: কনস্ট্রাক্টরের কোনো রিটার্ন টাইপই থাকে না, ফলে কনস্ট্রাক্টর ওভারলোডিং কেবল প্যারামিটারের সংখ্যা ও ডেটা টাইপের পার্থক্যের মাধ্যমে সম্পন্ন হয়।

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
