<!-- TOC START -->
**Table of Contents** — 9 subtopics · 117 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [OOP Concepts (Inheritance & Polymorphism)](#oop-concepts-inheritance--polymorphism-54) | 54 |
| 2 | [Java Programming & Methods](#java-programming--methods-18) | 18 |
| 3 | [Class Design & Object-Oriented Modeling](#class-design--object-oriented-modeling-11) | 11 |
| 4 | [Output Tracing & Recursion](#output-tracing--recursion-10) | 10 |
| 5 | [Constructors & Destructors](#constructors--destructors-8) | 8 |
| 6 | [Encapsulation & Access Modifiers](#encapsulation--access-modifiers-7) | 7 |
| 7 | [Exception Handling](#exception-handling-4) | 4 |
| 8 | [C++ OOP Concepts & Friend Functions](#c-oop-concepts--friend-functions-3) | 3 |
| 9 | [Interfaces & Abstract Classes](#interfaces--abstract-classes-2) | 2 |

<!-- TOC END -->

---

## OOP Concepts (Inheritance & Polymorphism) (54)

1. Explain the concepts of Inheritance and Polymorphism in Java. Write a Java program to demonstrate method overriding. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: Inheritance
   - `Inheritance` lets one class acquire the fields and methods of another. The existing class is the `superclass` (parent) and the new one the `subclass` (child).
   - Its purpose is `code reuse` and expressing an "is-a" relationship: a Dog `is a` Animal.
   ```java
   class Animal {
       void eat() { System.out.println("This animal eats food"); }
   }
   class Dog extends Animal {      // Dog inherits eat()
       void bark() { System.out.println("Dog barks"); }
   }
   ```
   - Java supports single, multilevel and hierarchical inheritance through classes, and `multiple` inheritance only through `interfaces` — avoiding the diamond problem.

   Polymorphism
   - `Polymorphism` means "many forms": the same method name behaves differently depending on the object it is called on.
   ```
      Compile-time  (static)  : method OVERLOADING  - resolved by the compiler
      Runtime      (dynamic)  : method OVERRIDING   - resolved by the JVM
   ```

   Program demonstrating method overriding
   ```java
   class Animal {
       String name;

       Animal(String name) { this.name = name; }

       void sound() {                       // the method to be overridden
           System.out.println(name + " makes a sound");
       }
   }

   class Dog extends Animal {
       Dog(String name) { super(name); }

       @Override
       void sound() {
           System.out.println(name + " barks: Bhow Bhow");
       }
   }

   class Cat extends Animal {
       Cat(String name) { super(name); }

       @Override
       void sound() {
           System.out.println(name + " meows: Meow");
       }
   }

   public class Main {
       public static void main(String[] args) {
           Animal[] animals = {           // superclass reference,
               new Animal("Generic"),     // subclass objects
               new Dog("Tommy"),
               new Cat("Kitty")
           };

           for (Animal a : animals) {
               a.sound();                 // which version runs is decided
           }                              // at RUNTIME, by the object's type
       }
   }
   ```

   Output
   ```
      Generic makes a sound
      Tommy barks: Bhow Bhow
      Kitty meows: Meow
   ```

   Why this is runtime polymorphism
   - The reference type is `Animal` in every case, so the compiler cannot know which `sound()` will run. The JVM looks at the `actual object` at run time and calls that class's version. This is called `dynamic method dispatch`.

   Rules for overriding in Java
   ```
      Same method name, same parameter list, compatible return type
      The method must be inherited (not private, final or static)
      Access cannot be made more restrictive
      @Override is optional but strongly recommended - the compiler then
           catches a mistyped signature
   ```

   Overloading, for contrast
   ```java
   class Calculator {
       int add(int a, int b)          { return a + b; }
       double add(double a, double b) { return a + b; }
       int add(int a, int b, int c)   { return a + b + c; }
   }
   ```
   - Same name, `different parameter lists`, resolved by the `compiler`.

   | Point | Overloading | Overriding |
   |---|---|---|
   | Resolved | At compile time | At run time |
   | Parameters | Must differ | Must be identical |
   | Classes | Same class | Superclass and subclass |
   | Inheritance | Not needed | Required |
   | Also called | Static / early binding | Dynamic / late binding |

2. **What is Object-Oriented Programming (OOP)? What are the main principles of OOP? What is the difference between Method Overloading and Method Overriding?** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer: What OOP is
   - `Object-Oriented Programming` organises a program around `objects` — bundles of `data` (attributes) and the `methods` that operate on that data — rather than around functions and logic.
   - A `class` is the blueprint; an `object` is an instance made from it.
   ```java
   class Student {              // class = blueprint
       String name;             // attribute
       int roll;
       void display() { ... }   // method
   }

   Student s1 = new Student();  // object = instance
   ```

   The four main principles

   1. `Encapsulation` — binding data and methods together and hiding the internal state
   ```java
   class Account {
       private double balance;                  // hidden

       public void deposit(double amt) {        // controlled access
           if (amt > 0) balance += amt;
       }
       public double getBalance() { return balance; }
   }
   ```
   - The balance cannot be set to a negative value from outside, because the only way in is through a method that validates.

   2. `Inheritance` — a new class acquires the members of an existing one
   ```java
   class Animal { void eat() { ... } }
   class Dog extends Animal { void bark() { ... } }   // Dog IS-A Animal
   ```
   - Gives code reuse and a natural hierarchy.

   3. `Polymorphism` — one name, many forms
   ```
      Compile-time : method OVERLOADING
      Runtime      : method OVERRIDING
   ```

   4. `Abstraction` — showing only the essential features and hiding the implementation
   ```java
   abstract class Shape { abstract double area(); }
   ```
   - A car's driver uses the steering wheel without knowing how the rack works.

   Method overloading versus method overriding

   `Overloading` — same method name in the `same class`, with `different parameter lists`.
   ```java
   class Calculator {
       int    add(int a, int b)          { return a + b; }
       double add(double a, double b)    { return a + b; }
       int    add(int a, int b, int c)   { return a + b + c; }
   }
   ```
   - The compiler picks the right version from the arguments supplied. Return type alone cannot distinguish two overloads.

   `Overriding` — a subclass provides its `own version` of a method inherited from its superclass, with the `same signature`.
   ```java
   class Animal {
       void sound() { System.out.println("Some sound"); }
   }
   class Dog extends Animal {
       @Override
       void sound() { System.out.println("Bhow Bhow"); }
   }

   Animal a = new Dog();
   a.sound();          // prints "Bhow Bhow" - decided at RUNTIME
   ```

   | Point | Method overloading | Method overriding |
   |---|---|---|
   | Where | Same class | Superclass and subclass |
   | Parameters | Must be `different` | Must be `identical` |
   | Return type | May differ | Must be the same or covariant |
   | Inheritance needed | No | `Yes` |
   | Resolved | At `compile time` | At `run time` |
   | Also called | Static / early binding | Dynamic / late binding |
   | Access modifier | Any | Cannot be made more restrictive |
   | `static` methods | Can be overloaded | Cannot be overridden (only hidden) |
   | `private` / `final` | Can be overloaded | Cannot be overridden |
   | Purpose | Convenience — one name for related operations | Specialisation — change inherited behaviour |
   | Performance | Slightly faster | Small runtime lookup cost |

   - The memory aid: `overloading changes the parameters, overriding changes the body`.

3. **What is runtime polymorphism and compile time polymorphism? Explain it's with example.** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)]*

   Answer: `Polymorphism` means "many forms" — the same method name behaves differently depending on the context. It comes in two kinds, distinguished by `when` the decision is made.

   Compile-time polymorphism (static, early binding)
   - The compiler decides which method to call, by looking at the `number, types and order of the arguments`.
   - Achieved by `method overloading` and, in C++, `operator overloading`.
   ```java
   class Calculator {
       int add(int a, int b)                 { return a + b; }
       double add(double a, double b)        { return a + b; }
       int add(int a, int b, int c)          { return a + b + c; }
       String add(String a, String b)        { return a + b; }
   }

   public class Main {
       public static void main(String[] args) {
           Calculator c = new Calculator();
           System.out.println(c.add(5, 3));           // 8    -> int version
           System.out.println(c.add(5.5, 3.2));       // 8.7  -> double version
           System.out.println(c.add(1, 2, 3));        // 6    -> three-arg version
           System.out.println(c.add("Ban","gladesh")); // Bangladesh
       }
   }
   ```
   - The compiler resolves each call by matching the argument list. Nothing is decided at run time, so it is `faster`.
   - Return type alone cannot distinguish two overloads — the compiler would have no way to choose.

   Runtime polymorphism (dynamic, late binding)
   - The `JVM` decides at run time, by looking at the `actual object` the reference points to — not at the reference's declared type.
   - Achieved by `method overriding` and requires `inheritance`.
   ```java
   class Payment {
       void pay(double amount) {
           System.out.println("Paying " + amount + " by generic method");
       }
   }
   class CardPayment extends Payment {
       @Override
       void pay(double amount) {
           System.out.println("Paying " + amount + " by debit card");
       }
   }
   class MobilePayment extends Payment {
       @Override
       void pay(double amount) {
           System.out.println("Paying " + amount + " by bKash");
       }
   }

   public class Main {
       public static void main(String[] args) {
           Payment p;                     // SUPERCLASS reference

           p = new CardPayment();
           p.pay(500);                    // "by debit card"

           p = new MobilePayment();
           p.pay(300);                    // "by bKash"
       }
   }
   ```
   - The reference `p` is of type `Payment` in both cases, so the compiler cannot know which `pay()` will run. The JVM checks the real object and calls that class's version. This is `dynamic method dispatch`.
   - In C++ the same effect requires the method to be declared `virtual`; in Java every non-static, non-final method is virtual by default.

   Comparison

   | Point | Compile-time polymorphism | Runtime polymorphism |
   |---|---|---|
   | Also called | Static / early binding | Dynamic / late binding |
   | Achieved by | Method overloading, operator overloading | Method overriding |
   | Decided by | The compiler | The JVM, at run time |
   | Based on | The argument list | The actual object type |
   | Inheritance needed | No | `Yes` |
   | Speed | Faster — resolved once | Slightly slower — a lookup per call |
   | Flexibility | Less | More |
   | In C++ | Normal functions | Requires `virtual` |
   | Example | `add(int,int)` and `add(double,double)` | `Animal a = new Dog(); a.sound();` |

   - Why runtime polymorphism matters: it lets one piece of code work with objects whose exact type is unknown when the code is written. A single loop over an array of `Payment` objects handles cards, mobile money and cash correctly, and a new payment type can be added later without changing that loop at all — the `open-closed principle`.

4. **What is polymorphism?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: `Polymorphism` comes from Greek — "poly" means many and "morph" means form. In programming it means that the `same method name behaves differently` depending on the object it acts on or the arguments it is given.

   - A single interface serves many implementations, so the caller does not need to know which one it is using.

   Two types
   ```
      Compile-time polymorphism (static, early binding)
           -> method OVERLOADING, and operator overloading in C++
           -> the COMPILER decides, from the argument list

      Runtime polymorphism (dynamic, late binding)
           -> method OVERRIDING
           -> the JVM decides at run time, from the actual object
   ```

   Compile-time example
   ```java
   class Calculator {
       int    add(int a, int b)       { return a + b; }
       double add(double a, double b) { return a + b; }
       int    add(int a, int b, int c){ return a + b + c; }
   }
   ```
   - Same name, different parameter lists; the compiler picks the right one.

   Runtime example
   ```java
   class Animal {
       void sound() { System.out.println("Some sound"); }
   }
   class Dog extends Animal {
       @Override void sound() { System.out.println("Bhow Bhow"); }
   }
   class Cat extends Animal {
       @Override void sound() { System.out.println("Meow"); }
   }

   Animal a;
   a = new Dog();   a.sound();   // Bhow Bhow
   a = new Cat();   a.sound();   // Meow
   ```
   - The reference type is `Animal` in both cases; the JVM looks at the real object and calls that version.

   A real-world analogy
   ```
      The word "run" behaves differently by context :
           a person runs , a program runs , a nose runs

      The + operator :
           5 + 3        -> 8            (numeric addition)
           "Ban"+"gla"  -> "Bangla"     (string concatenation)
   ```

   Why it is useful
   - `One interface, many implementations.` A loop over an array of `Shape` objects calls `area()` on each, and each shape computes its own.
   - `Extensibility.` A new subclass can be added without changing any existing code — the `open-closed principle`.
   - `Cleaner code` — no long chains of `if (type == circle) ... else if (type == square)`.

   - Polymorphism is one of the four pillars of OOP, along with `encapsulation`, `inheritance` and `abstraction`. It depends on inheritance, which is why the two are usually taught together.

5. **Explain OOP Feature.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: `Object-Oriented Programming` organises a program around `objects` — bundles of data and the methods that act on that data — instead of around functions and logic. Its features are the following.

   1. Class and Object
   - A `class` is a blueprint that defines attributes and methods. An `object` is an instance created from it, occupying real memory.
   ```java
   class Student {
       String name;  int roll;              // attributes
       void display() { ... }               // method
   }
   Student s1 = new Student();              // object
   ```

   2. Encapsulation
   - Binding data and the methods that work on it into one unit, and `hiding` the internal state behind `private` fields with public getters and setters.
   ```java
   class Account {
       private double balance;
       public void deposit(double amt) { if (amt > 0) balance += amt; }
       public double getBalance() { return balance; }
   }
   ```
   - Benefit: the object cannot be put into an invalid state from outside, and the internal representation can be changed later without breaking any caller.

   3. Abstraction
   - Showing only the `essential features` and hiding the implementation. Achieved with `abstract classes` and `interfaces`.
   ```java
   abstract class Shape { abstract double area(); }
   ```
   - Benefit: the user of a class works with `what` it does, not `how` it does it — like driving a car without knowing the engine.

   4. Inheritance
   - A new class acquires the members of an existing one, expressing an `is-a` relationship.
   ```java
   class Animal { void eat() { ... } }
   class Dog extends Animal { void bark() { ... } }
   ```
   ```
      Types : single, multilevel, hierarchical, multiple (via interfaces
              in Java), hybrid
   ```
   - Benefit: `code reuse`, and a natural way to model a hierarchy.

   5. Polymorphism
   - The same method name behaving differently by context.
   ```
      Compile-time : method OVERLOADING  - the compiler decides
      Runtime      : method OVERRIDING   - the JVM decides
   ```
   - Benefit: one interface serves many implementations, so new types can be added without changing existing code.

   6. Message passing
   - Objects communicate by `calling each other's methods`, which is how work gets done in an OOP program.

   7. Dynamic binding
   - Which method body runs is decided at `run time`, based on the actual object. This is what makes runtime polymorphism possible.

   Advantages of OOP
   ```
      Reusability      : inheritance and composition avoid rewriting code
      Maintainability  : a change is confined to one class
      Modularity       : each class is a self-contained unit
      Data security    : encapsulation hides the internal state
      Extensibility    : new classes are added without disturbing old ones
      Models reality   : objects map naturally onto real-world entities
      Team development : different people can work on different classes
   ```

   Disadvantages
   ```
      Steeper learning curve than procedural programming
      Larger program size and some runtime overhead
      Over-engineering is easy: a simple script does not need classes
   ```

   - Languages: `Java, C++, C#, Python, Ruby, Kotlin, Swift`. Of these, Java and C# are almost purely object-oriented, while C++ and Python allow both procedural and object-oriented styles.

6. **Write a program using any object-oriented language (e.g., C++ / Java / Python) to represent a Bank Account. Your program should include:**
 * **A class BankAccount with data members for account holder's name, account number, and balance.**
 * **Member functions to deposit() money, withdraw() money (ensuring sufficient balance), and display() account details.**
**Demonstrate the concept of encapsulation by keeping data member's private and providing appropriate public methods for accessing and modifying them.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*

   Answer: The program demonstrates `encapsulation`: the data members are `private`, and all access goes through `public` methods that validate what they are given.

   Java version
   ```java
   class BankAccount {

       // ---- private data members : nothing outside can touch them ----
       private String accountHolder;
       private String accountNumber;
       private double balance;

       // ---- constructor ----
       public BankAccount(String accountHolder, String accountNumber,
                          double openingBalance) {
           this.accountHolder = accountHolder;
           this.accountNumber = accountNumber;
           this.balance = (openingBalance > 0) ? openingBalance : 0;
       }

       // ---- deposit ----
       public void deposit(double amount) {
           if (amount <= 0) {
               System.out.println("Deposit amount must be positive");
               return;
           }
           balance += amount;
           System.out.println("Deposited: " + amount);
       }

       // ---- withdraw, with a sufficient-balance check ----
       public void withdraw(double amount) {
           if (amount <= 0) {
               System.out.println("Withdrawal amount must be positive");
           } else if (amount > balance) {
               System.out.println("Insufficient balance. Available: " + balance);
           } else {
               balance -= amount;
               System.out.println("Withdrawn: " + amount);
           }
       }

       // ---- display ----
       public void display() {
           System.out.println("--------------------------------");
           System.out.println("Account Holder : " + accountHolder);
           System.out.println("Account Number : " + accountNumber);
           System.out.println("Balance        : " + balance);
           System.out.println("--------------------------------");
       }

       // ---- getters and setters : controlled access ----
       public double getBalance()        { return balance; }
       public String getAccountHolder()  { return accountHolder; }
       public void setAccountHolder(String name) {
           if (name != null && !name.isEmpty()) this.accountHolder = name;
       }
   }

   public class Main {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount("Rahim Uddin", "AC1001", 5000);

           acc.display();
           acc.deposit(2000);
           acc.withdraw(1500);
           acc.withdraw(10000);        // rejected - insufficient balance
           acc.deposit(-500);          // rejected - invalid amount
           acc.display();

           // acc.balance = 999999;    // COMPILE ERROR - balance is private
       }
   }
   ```

   Output
   ```
      --------------------------------
      Account Holder : Rahim Uddin
      Account Number : AC1001
      Balance        : 5000.0
      --------------------------------
      Deposited: 2000.0
      Withdrawn: 1500.0
      Insufficient balance. Available: 5500.0
      Deposit amount must be positive
      --------------------------------
      Account Holder : Rahim Uddin
      Account Number : AC1001
      Balance        : 5500.0
      --------------------------------
   ```

   C++ version
   ```cpp
   #include <iostream>
   #include <string>
   using namespace std;

   class BankAccount {
   private:                                    // ---- encapsulated data ----
       string accountHolder;
       string accountNumber;
       double balance;

   public:
       BankAccount(string holder, string number, double opening) {
           accountHolder = holder;
           accountNumber = number;
           balance = (opening > 0) ? opening : 0;
       }

       void deposit(double amount) {
           if (amount <= 0) { cout << "Deposit must be positive\n"; return; }
           balance += amount;
           cout << "Deposited: " << amount << endl;
       }

       void withdraw(double amount) {
           if (amount <= 0)
               cout << "Withdrawal must be positive\n";
           else if (amount > balance)
               cout << "Insufficient balance. Available: " << balance << endl;
           else {
               balance -= amount;
               cout << "Withdrawn: " << amount << endl;
           }
       }

       void display() {
           cout << "Holder : " << accountHolder << endl;
           cout << "Number : " << accountNumber << endl;
           cout << "Balance: " << balance << endl;
       }

       double getBalance() { return balance; }
   };

   int main() {
       BankAccount acc("Rahim Uddin", "AC1001", 5000);
       acc.display();
       acc.deposit(2000);
       acc.withdraw(1500);
       acc.withdraw(10000);
       acc.display();
       return 0;
   }
   ```

   How encapsulation is demonstrated
   ```
      1. balance, accountHolder and accountNumber are PRIVATE, so no outside
         code can read or change them directly.
      2. The only way in is through PUBLIC methods, which VALIDATE the input:
           - deposit() rejects a negative amount
           - withdraw() refuses to overdraw the account
      3. accountNumber has a getter but no setter, so it can be read but
         never altered once the account exists.
      4. The internal representation could be changed later - storing paisa
         as an integer, say - without breaking any caller.
   ```
   - Without encapsulation, `acc.balance = -50000;` would be legal and would corrupt the account. This is precisely the risk encapsulation removes.

7. **b) What is polymorphism in the context of an object-oriented paradigm? Explain the method of overloading and method of overriding with suitable examples.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*

   Answer: What polymorphism is
   - `Polymorphism` means "many forms". The same method name behaves differently depending on the object it acts on or the arguments it is given, so one interface serves many implementations.
   - It is one of the four pillars of OOP, with encapsulation, inheritance and abstraction.
   ```
      Compile-time (static)  : method OVERLOADING  - the compiler decides
      Runtime (dynamic)      : method OVERRIDING   - the JVM decides
   ```

   Method overloading
   - Two or more methods in the `same class` share a name but have `different parameter lists` — a different number of parameters, different types, or a different order.
   ```java
   class Calculator {
       int    add(int a, int b)          { return a + b; }
       double add(double a, double b)    { return a + b; }
       int    add(int a, int b, int c)   { return a + b + c; }
       String add(String a, String b)    { return a + b; }
   }

   public class Main {
       public static void main(String[] args) {
           Calculator c = new Calculator();
           System.out.println(c.add(5, 3));            // 8
           System.out.println(c.add(5.5, 3.2));        // 8.7
           System.out.println(c.add(1, 2, 3));         // 6
           System.out.println(c.add("Bangla","desh")); // Bangladesh
       }
   }
   ```
   - The `compiler` chooses the version by matching the argument list, so nothing is decided at run time. Return type alone cannot distinguish two overloads.
   - Purpose: one meaningful name for a family of related operations, instead of `addInt`, `addDouble`, `addThree`.

   Method overriding
   - A `subclass` supplies its own version of a method it inherited, with `exactly the same signature`.
   ```java
   class Employee {
       double calculateSalary(double basic) {
           return basic;
       }
   }

   class Manager extends Employee {
       @Override
       double calculateSalary(double basic) {
           return basic + 0.40 * basic;      // 40 % allowance
       }
   }

   class Officer extends Employee {
       @Override
       double calculateSalary(double basic) {
           return basic + 0.20 * basic;      // 20 % allowance
       }
   }

   public class Main {
       public static void main(String[] args) {
           Employee[] staff = { new Manager(), new Officer(), new Employee() };

           for (Employee e : staff)
               System.out.println(e.calculateSalary(50000));
       }
   }
   ```
   Output
   ```
      70000.0        Manager
      60000.0        Officer
      50000.0        plain Employee
   ```
   - The reference type is `Employee` throughout, so the compiler cannot know which version will run. The `JVM` looks at the actual object at run time — `dynamic method dispatch`.
   - Purpose: specialising inherited behaviour, so that a general algorithm works correctly with every subclass.

   Comparison

   | Point | Method overloading | Method overriding |
   |---|---|---|
   | Where | Same class | Superclass and subclass |
   | Parameter list | Must `differ` | Must be `identical` |
   | Return type | May differ | Same or covariant |
   | Inheritance | Not needed | `Required` |
   | Resolved | At compile time | At run time |
   | Also called | Static / early binding | Dynamic / late binding |
   | Access modifier | Any | Cannot be more restrictive |
   | `static` methods | Can be overloaded | Cannot be overridden |
   | `private` / `final` | Can be overloaded | Cannot be overridden |
   | Purpose | Convenience | Specialisation |

   - Why runtime polymorphism matters most: it lets code written today work with classes written tomorrow. The salary loop above needs no change when a new `Director` subclass is added — the `open-closed principle`, open for extension and closed for modification.

8. **Explain the concept of polymorphism in Object-oriented Programming with example?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1336 (ET: N/A)]*

   Answer: `Polymorphism` means "many forms". In OOP it means the same method name behaves differently depending on the object it is called on or the arguments given to it, so that `one interface serves many implementations`.

   Two types
   ```
      Compile-time (static, early binding)  -> method OVERLOADING
      Runtime      (dynamic, late binding)  -> method OVERRIDING
   ```

   Compile-time polymorphism — overloading
   ```java
   class Area {
       double calculate(double side)            { return side * side; }
       double calculate(double l, double w)     { return l * w; }
       double calculate(double r, boolean isCircle) { return 3.1416 * r * r; }
   }
   ```
   - The compiler picks the version that matches the arguments. Nothing is decided at run time, so it costs nothing extra.

   Runtime polymorphism — overriding
   ```java
   abstract class Shape {
       abstract double area();
       void describe() { System.out.println("Area = " + area()); }
   }

   class Circle extends Shape {
       double r;
       Circle(double r) { this.r = r; }
       @Override double area() { return 3.1416 * r * r; }
   }

   class Rectangle extends Shape {
       double l, w;
       Rectangle(double l, double w) { this.l = l; this.w = w; }
       @Override double area() { return l * w; }
   }

   class Triangle extends Shape {
       double b, h;
       Triangle(double b, double h) { this.b = b; this.h = h; }
       @Override double area() { return 0.5 * b * h; }
   }

   public class Main {
       public static void main(String[] args) {
           Shape[] shapes = {
               new Circle(5),
               new Rectangle(4, 6),
               new Triangle(3, 8)
           };

           for (Shape s : shapes)
               s.describe();          // each object runs ITS OWN area()
       }
   }
   ```
   Output
   ```
      Area = 78.54
      Area = 24.0
      Area = 12.0
   ```
   - The array holds `Shape` references, so the compiler cannot know which `area()` will run. The JVM examines the real object at run time and calls that class's version — `dynamic method dispatch`.
   - In C++ the base method would have to be declared `virtual` for this to work; in Java it happens automatically.

   Everyday analogies
   ```
      The word "run"   : a person runs , a program runs , a nose runs
      The + operator   : 5 + 3 -> 8 ,  "Ban" + "gla" -> "Bangla"
      One remote control button behaves differently on a TV and an AC
   ```

   Why it is valuable
   - `One interface, many implementations` — the loop above handles every shape with one line of code.
   - `Extensibility` — adding a `Square` class needs no change at all to `Main`. This is the `open-closed principle`: open for extension, closed for modification.
   - `Cleaner code` — it removes long chains of `if (type == circle) ... else if (type == rectangle) ...`.
   - `Enables frameworks` — a library can call methods on objects whose classes did not exist when the library was written.

   - Polymorphism depends on `inheritance` (or on interfaces), which is why the two are always taught together. Together with `encapsulation` and `abstraction` they form the four pillars of object-oriented programming.

9. **Write down the difference between Structure and Class.** *[BCIC Assistant Programmer 14.02.2025 compact it 1324 (ET: BUET)]*

   Answer: A `structure` and a `class` both group related data together. In C++ the only technical difference is the `default access level`; in C they are far more different, and in Java and C# a struct is a value type.

   In C++

   `struct` — members are `public` by default
   ```cpp
   struct Point {
       int x;              // public by default
       int y;
       void display() { cout << x << "," << y; }
   };

   Point p;
   p.x = 10;               // legal - public
   ```

   `class` — members are `private` by default
   ```cpp
   class Point {
       int x;              // PRIVATE by default
       int y;
   public:
       void setX(int a) { x = a; }
       void display() { cout << x << "," << y; }
   };

   Point p;
   p.x = 10;               // COMPILE ERROR - x is private
   ```
   - Inheritance follows the same rule: `struct B : A` is public inheritance by default, `class B : A` is private inheritance by default.
   - Everything else is identical — a C++ struct can have methods, constructors, destructors, inheritance and access specifiers, exactly like a class.

   Difference

   | Point | Structure (struct) | Class |
   |---|---|---|
   | Default member access | `public` | `private` |
   | Default inheritance | Public | Private |
   | Methods allowed | Yes in C++, `no` in C | Yes |
   | Constructor / destructor | Yes in C++, no in C | Yes |
   | Inheritance | Yes in C++ | Yes |
   | Data hiding | Not by default | Yes, by default |
   | Memory allocation | Usually stack (value type) | Usually heap in Java and C# |
   | Type | Value type in C# | Reference type |
   | Null value | Cannot be null (C#) | Can be null |
   | Purpose | Grouping plain data | Full object with behaviour |
   | Used for | Small, simple data records | Complete objects, encapsulation |
   | In Java | `Not available` | Yes |

   In C, the difference is much larger
   ```c
   struct Student {
       char name[50];
       int  roll;
   };                      /* data ONLY - no functions, no access control */
   ```
   - A C structure is a plain data container: no methods, no constructors, no inheritance, no encapsulation. It is a grouping mechanism, nothing more.

   In Java
   - There is `no struct` at all. A class with public fields is used instead, or a `record` in modern Java:
   ```java
   record Point(int x, int y) { }     // a compact immutable data carrier
   ```

   In C#
   ```
      struct : a VALUE type, stored on the stack, copied on assignment,
               cannot inherit from another struct or class, cannot be null
      class  : a REFERENCE type, stored on the heap, assignment copies the
               reference, supports inheritance, can be null
   ```

   When to use which, in C++
   ```
      struct : a plain bundle of data with no invariant to protect -
               coordinates, an RGB colour, a configuration record.
               Signals to the reader "this is just data".

      class  : anything with behaviour or an invariant to maintain -
               a bank account, a linked list, a database connection.
   ```
   - The choice is therefore a matter of `intent and readability` in C++, not of capability. Most style guides say: use `struct` when everything is public data, and `class` otherwise.

10. **What is Polymorphism? Discuss about different types of Polymorphism with example?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 296 (ET: BIBM)]*

    Answer: `Polymorphism` means "many forms". The same method name behaves differently depending on the object it acts on or the arguments it is given, so one interface serves many implementations.

    Types of polymorphism
    ```
       Polymorphism
            |
            +-- Compile-time (static, early binding)
            |        |-- Method overloading
            |        +-- Operator overloading  (C++, not Java)
            |
            +-- Runtime (dynamic, late binding)
                     +-- Method overriding
    ```

    1. Method overloading — compile-time
    - Several methods in the `same class` share a name but take `different parameter lists`.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }

    Calculator c = new Calculator();
    c.add(5, 3);        // 8
    c.add(5.5, 3.2);    // 8.7
    c.add(1, 2, 3);     // 6
    ```
    - The `compiler` matches the call to a version by its arguments. Return type alone cannot distinguish overloads.

    2. Operator overloading — compile-time (C++)
    - An existing operator is given a new meaning for a user-defined type.
    ```cpp
    class Complex {
        int real, imag;
    public:
        Complex(int r = 0, int i = 0) : real(r), imag(i) {}

        Complex operator+(const Complex& c) {       // + is overloaded
            return Complex(real + c.real, imag + c.imag);
        }
        void display() { cout << real << " + " << imag << "i" << endl; }
    };

    int main() {
        Complex a(3, 4), b(1, 2);
        Complex c = a + b;          // calls operator+
        c.display();                // 4 + 6i
    }
    ```
    - Java does not allow user-defined operator overloading; the only built-in case is `+` for String concatenation.

    3. Method overriding — runtime
    - A subclass supplies its own version of an inherited method, with the `same signature`.
    ```java
    class Vehicle {
        void start() { System.out.println("Vehicle starting"); }
    }
    class Car extends Vehicle {
        @Override void start() { System.out.println("Car starts with a key"); }
    }
    class ElectricCar extends Vehicle {
        @Override void start() { System.out.println("Electric car starts silently"); }
    }

    public class Main {
        public static void main(String[] args) {
            Vehicle[] v = { new Vehicle(), new Car(), new ElectricCar() };
            for (Vehicle x : v) x.start();
        }
    }
    ```
    Output
    ```
       Vehicle starting
       Car starts with a key
       Electric car starts silently
    ```
    - The reference type is `Vehicle` in every case, so the `JVM` must look at the actual object at run time — `dynamic method dispatch`.

    Comparison

    | Point | Compile-time | Runtime |
    |---|---|---|
    | Also called | Static / early binding | Dynamic / late binding |
    | Achieved by | Overloading | Overriding |
    | Decided by | The compiler | The JVM |
    | Based on | The argument list | The actual object |
    | Inheritance | Not needed | Required |
    | Speed | Faster | Slightly slower |
    | Flexibility | Less | More |

    - Why runtime polymorphism is the more important of the two: it lets a program written today work with classes written tomorrow. Adding a new `Vehicle` subclass requires no change at all to the loop above — the `open-closed principle`.

11. **Explain how encapsulation and inheritance are advantageous in object oriented programming.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 420 (ET: BIBM)]*

    Answer: Encapsulation
    - `Encapsulation` binds the data and the methods that operate on it into a single unit, and `hides the internal state` behind private fields with public accessor methods.
    ```java
    class Account {
        private double balance;                    // hidden from outside

        public void deposit(double amt) {
            if (amt > 0) balance += amt;           // validated
        }
        public void withdraw(double amt) {
            if (amt > 0 && amt <= balance) balance -= amt;
        }
        public double getBalance() { return balance; }
    }
    ```

    Advantages of encapsulation
    - `Data security.` The field cannot be set to an invalid value from outside. Without it, `acc.balance = -50000;` would be legal and would corrupt the account.
    - `Controlled access.` The class decides what may be read and what may be written. `accountNumber` can have a getter but no setter, making it read-only.
    - `Validation in one place.` Every deposit passes through the same check, so the rule cannot be forgotten by a caller.
    - `Freedom to change the implementation.` The balance could later be stored as an integer number of paisa, or moved to a database, without breaking a single caller — because nobody outside ever touched the field.
    - `Reduced coupling.` Classes depend on each other's `interfaces`, not their internals, so a change in one does not ripple through the program.
    - `Easier maintenance and debugging.` If the balance is wrong, only the few methods of `Account` could have caused it, so the search is small.
    - `Reusability.` A well-encapsulated class is a self-contained unit that can be dropped into another program.

    Inheritance
    - `Inheritance` lets a new class acquire the fields and methods of an existing one, expressing an `is-a` relationship.
    ```java
    class Employee {
        protected String name;
        protected double basic;

        double calculateSalary() { return basic; }
        void display() { System.out.println(name + " : " + calculateSalary()); }
    }

    class Manager extends Employee {                 // Manager IS-A Employee
        @Override
        double calculateSalary() { return basic + 0.40 * basic; }
    }

    class Officer extends Employee {
        @Override
        double calculateSalary() { return basic + 0.20 * basic; }
    }
    ```

    Advantages of inheritance
    - `Code reuse.` `name`, `basic` and `display()` are written once and used by every subclass. Without inheritance each class would repeat them.
    - `Less code to maintain.` Fixing a bug in `display()` fixes it for every subclass at once.
    - `Natural hierarchy.` The class structure mirrors the real world, so the design is easier to understand — Manager and Officer really are kinds of Employee.
    - `Enables polymorphism.` Because a `Manager` is an `Employee`, one array of `Employee` can hold all staff and one loop can pay them all correctly. This is inheritance's most valuable consequence.
    - `Extensibility.` A new `Director` class needs only its own `calculateSalary()`; nothing else in the program changes — the `open-closed principle`.
    - `Method overriding` lets a subclass specialise inherited behaviour without touching the superclass.
    - `Consistent interface.` Every subclass is guaranteed to provide the superclass's methods, so callers can rely on them.

    Cautions worth stating
    ```
       Encapsulation : writing a getter and a setter for every private field
                       defeats the purpose; expose only what callers need.

       Inheritance   : it creates TIGHT COUPLING - a change in the superclass
                       can break every subclass. Deep hierarchies become
                       fragile, and "prefer composition over inheritance"
                       is the standard modern advice. Use inheritance only
                       for a genuine "is-a" relationship.
    ```

    - Together with `abstraction` and `polymorphism`, these two form the four pillars of OOP. Encapsulation protects an object's data; inheritance shares an object's behaviour.

12. **(খ) Function Overloading উদাহরণসহ ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `Function overloading` means defining two or more functions with the `same name` in the same scope, distinguished by their `parameter lists`. The compiler decides which one to call from the arguments supplied.

    - It is a form of `compile-time (static) polymorphism`.

    How the compiler distinguishes them
    ```
       1. Different NUMBER of parameters
       2. Different TYPES of parameters
       3. Different ORDER of parameter types

       NOT sufficient : a different RETURN TYPE alone.
                        The compiler cannot choose on that basis, because the
                        return value may be discarded.
    ```

    C++ example
    ```cpp
    #include <iostream>
    using namespace std;

    class Calculator {
    public:
        int add(int a, int b) {                    // 1. two ints
            return a + b;
        }
        double add(double a, double b) {           // 2. two doubles
            return a + b;
        }
        int add(int a, int b, int c) {             // 3. three ints
            return a + b + c;
        }
        string add(string a, string b) {           // 4. two strings
            return a + b;
        }
    };

    int main() {
        Calculator c;
        cout << c.add(5, 3)              << endl;  // 8         -> version 1
        cout << c.add(5.5, 3.2)          << endl;  // 8.7       -> version 2
        cout << c.add(1, 2, 3)           << endl;  // 6         -> version 3
        cout << c.add("Bangla","desh")   << endl;  // Bangladesh-> version 4
        return 0;
    }
    ```

    Java example
    ```java
    class Area {
        double area(double side)          { return side * side; }        // square
        double area(double l, double w)   { return l * w; }              // rectangle
        double area(double b, double h, boolean tri) { return 0.5*b*h; } // triangle
    }
    ```

    Constructor overloading — the same idea applied to constructors
    ```java
    class Student {
        String name;  int roll;

        Student()                       { name = "Unknown"; roll = 0; }
        Student(String n)               { name = n; roll = 0; }
        Student(String n, int r)        { name = n; roll = r; }
    }
    ```
    - This is why an object can be created in several different ways.

    What is NOT valid overloading
    ```cpp
       int  f(int a);
       void f(int a);          // ERROR - differs only by return type

       int  g(int a);
       int  g(const int a);    // ERROR - top-level const is ignored
    ```

    Advantages
    ```
       One meaningful name instead of addInt, addDouble, addThree
       Easier to read and remember
       Consistent interface for related operations
       Resolved at COMPILE TIME, so there is no runtime cost
    ```

    - Difference from `function overriding`: overloading happens in the `same class` with `different parameters` and is resolved by the compiler; overriding happens between a `superclass and a subclass` with an `identical signature` and is resolved at run time. The memory aid is `overloading changes the parameters, overriding changes the body`.

13. **Write down the advantages of OOP over traditional structured programming language** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 527 (ET: MIST)]*

    Answer: `Structured (procedural) programming` organises a program around `functions` that act on data held separately. `OOP` organises it around `objects` that hold data and behaviour together.

    Advantages of OOP over structured programming

    1. `Data security through encapsulation`
    - In structured programming, global data is accessible to every function, so any function can corrupt it and finding the culprit is hard.
    - In OOP the data is `private` inside the object, reachable only through methods that validate.
    ```java
    class Account {
        private double balance;                 // no outside code can touch it
        public void deposit(double a) { if (a > 0) balance += a; }
    }
    ```

    2. `Code reuse through inheritance`
    - A subclass inherits everything from its parent, so common code is written once. Structured programming can only reuse by copying functions or calling them, with no automatic sharing of related structure.

    3. `Easier maintenance`
    - A change is confined to `one class`. In a large procedural program, changing a data structure means finding and editing every function that touches it.

    4. `Modularity`
    - Each class is a self-contained unit with a clear boundary. Several developers can work on different classes at once with little interference.

    5. `Models the real world naturally`
    - An `Account`, a `Customer` and a `Loan` are real things, so the program structure matches the problem. Procedural design has to translate the problem into steps first.

    6. `Extensibility — the open-closed principle`
    - A new subclass can be added without touching existing code. In procedural code, adding a new case usually means editing every `switch` statement that enumerates the cases.
    ```java
       for (Shape s : shapes) s.area();     // works for a NEW Shape subclass
                                            // with no change to this loop
    ```

    7. `Polymorphism removes long conditional chains`
    ```
       Procedural : if (type == CIRCLE) area = ... ;
                    else if (type == RECT) area = ... ;
                    else if (type == TRIANGLE) ...

       OOP        : shape.area();           each object knows its own formula
    ```

    8. `Abstraction`
    - The user of a class works with `what` it does, not `how`. The implementation can be replaced entirely without breaking callers.

    9. `Better for large programs`
    - Procedural programming works well up to a few thousand lines. Beyond that the web of functions and shared data becomes unmanageable, which is precisely the problem OOP was invented to solve.

    10. `Supports design patterns and frameworks`
    - Reusable solutions such as Factory, Observer and Strategy, and every modern framework — Spring, Django, .NET — rest on object-oriented mechanisms.

    Comparison

    | Point | Structured programming | OOP |
    |---|---|---|
    | Organised around | Functions and procedures | Objects |
    | Data and functions | Separate | Bound together |
    | Data access | Global, open to all functions | Private, controlled by methods |
    | Approach | Top-down | Bottom-up |
    | Reuse | Copy or call functions | Inheritance and composition |
    | Extending | Often needs editing existing code | Add a new class |
    | Maintenance | Harder as size grows | Easier, changes are localised |
    | Real-world mapping | Weak | Strong |
    | Suited to | Small and medium programs | Large, evolving systems |
    | Examples | C, Pascal, FORTRAN | Java, C++, C#, Python |

    Where structured programming is still better
    ```
       Small scripts and utilities - a class hierarchy would be over-engineering
       Embedded systems with tight memory - objects carry overhead
       Purely mathematical or signal-processing code
       Performance-critical loops, where indirection costs measurable time
    ```
    - So OOP is not universally superior; it is superior for `large, long-lived programs that must evolve`, which is most business software.

14. **Write down the Principle of OOP. What is Polymorphism? Write the name of 3 OOP language.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

    Answer: Principles of OOP

    The four pillars.

    1. `Encapsulation` — binding data and methods into one unit and hiding the internal state
    ```java
    class Account {
        private double balance;                     // hidden
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```
    - Benefit: the object cannot be put into an invalid state from outside, and the implementation can change without breaking callers.

    2. `Abstraction` — showing only the essential features and hiding the implementation
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - Benefit: the user works with `what` a class does, not `how` — like driving a car without knowing the engine.

    3. `Inheritance` — a new class acquires the members of an existing one
    ```java
    class Animal { void eat() { ... } }
    class Dog extends Animal { void bark() { ... } }
    ```
    - Benefit: code reuse and a natural hierarchy. Types: single, multilevel, hierarchical, multiple (via interfaces in Java), hybrid.

    4. `Polymorphism` — one name, many forms
    ```
       Compile-time : method OVERLOADING  - the compiler decides
       Runtime      : method OVERRIDING   - the JVM decides
    ```
    - Benefit: one interface serves many implementations, so new types can be added without changing existing code.

    Some texts add `message passing` (objects communicate by calling each other's methods) and `dynamic binding` (the method body is chosen at run time).

    What polymorphism is
    - `Polymorphism` means "many forms": the same method name behaves differently depending on the object it is called on or the arguments given.
    ```java
    class Animal { void sound() { System.out.println("Some sound"); } }
    class Dog extends Animal { @Override void sound() { System.out.println("Bhow Bhow"); } }
    class Cat extends Animal { @Override void sound() { System.out.println("Meow"); } }

    Animal a;
    a = new Dog();  a.sound();     // Bhow Bhow
    a = new Cat();  a.sound();     // Meow
    ```
    - The reference type is `Animal` in both lines; the JVM looks at the real object and calls that version — `dynamic method dispatch`.
    - Its value is `extensibility`: a new subclass can be added without changing any code that uses the superclass.

    Three OOP languages
    ```
       1. Java    - purely object-oriented (except for its primitive types),
                    platform independent through the JVM
       2. C++     - multi-paradigm; supports both procedural and object-oriented
                    styles, and adds operator overloading and multiple inheritance
       3. Python  - object-oriented and dynamically typed; everything, including
                    a number, is an object
    ```
    - Others worth naming: `C#`, `Ruby`, `Kotlin`, `Swift`, `PHP`, `Objective-C` and `Smalltalk`, the language in which the term "object-oriented" was coined.

15. **(b) What is the diamond problem of multiple inheritance in C++?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 487 (ET: N/A)]*

    Answer: The `diamond problem` is the ambiguity that arises in `multiple inheritance` when a class inherits from two classes that share a common base class. The inheritance graph forms a diamond shape.

    The situation
    ```
                  A
                 / \
                /   \
               B     C          B and C both inherit from A
                \   /
                 \ /
                  D             D inherits from BOTH B and C
    ```
    - `D` therefore receives `two copies` of everything in `A` — one through B and one through C. When code refers to an inherited member of A, the compiler cannot tell which copy is meant.

    The problem in code
    ```cpp
    #include <iostream>
    using namespace std;

    class A {
    public:
        int value = 10;
        void show() { cout << "Class A" << endl; }
    };

    class B : public A { };        // inherits one copy of A
    class C : public A { };        // inherits another copy of A

    class D : public B, public C { };   // D now has TWO copies of A

    int main() {
        D obj;
        obj.show();      // ERROR: request for member 'show' is ambiguous
        cout << obj.value;  // ERROR: 'value' is ambiguous
        return 0;
    }
    ```
    - The compiler reports `ambiguous` because `D::B::A::show()` and `D::C::A::show()` both exist and it has no rule to prefer one.

    Solution 1 — scope resolution (works, but ugly)
    ```cpp
       obj.B::show();       // explicitly use the copy that came through B
       obj.C::show();       // explicitly use the copy that came through C
    ```
    - This resolves the call, but the object still carries `two separate copies` of A's data, which is usually not what was wanted.

    Solution 2 — virtual inheritance (the real fix)
    ```cpp
    class A {
    public:
        int value = 10;
        void show() { cout << "Class A" << endl; }
    };

    class B : virtual public A { };     // note: VIRTUAL
    class C : virtual public A { };     // note: VIRTUAL

    class D : public B, public C { };   // now only ONE shared copy of A

    int main() {
        D obj;
        obj.show();          // works - no ambiguity
        cout << obj.value;   // 10 - a single shared copy
        return 0;
    }
    ```
    - `virtual` inheritance tells the compiler that B and C should `share` one instance of A rather than each keeping its own. The ambiguity disappears, and so does the duplicated data.
    - Cost: virtual base classes need an extra pointer per object and an indirection on access, so they are slightly slower and larger.

    How other languages avoid it entirely
    ```
       Java and C# : a class may extend only ONE class, so the diamond cannot
                     arise. Multiple inheritance of TYPE is allowed through
                     interfaces, which (before Java 8) had no implementation
                     to be ambiguous about.

       Java 8+     : default methods in interfaces reintroduced a mild version
                     of the problem. Java requires the class to resolve it
                     explicitly :

                        class D implements B, C {
                            public void show() { B.super.show(); }
                        }

       Python      : allows multiple inheritance but resolves it with the
                     C3 linearisation MRO (Method Resolution Order), which
                     defines a single deterministic order.
    ```

    - The lesson usually drawn: multiple inheritance of `implementation` creates more problems than it solves, which is why most languages designed after C++ allow multiple inheritance only of `interfaces`. Where shared behaviour is needed, `composition` is preferred over inheritance.

16. **(a) Define function overloading and function overriding with examples.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

    Answer: Function overloading
    - Two or more functions in the `same scope` share a name but have `different parameter lists`. The compiler chooses which one to call from the arguments supplied.
    - It is `compile-time (static) polymorphism`, and needs no inheritance.
    ```
       Distinguished by :  different NUMBER of parameters
                           different TYPES of parameters
                           different ORDER of parameter types

       NOT distinguished by return type alone.
    ```
    ```cpp
    class Calculator {
    public:
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
        string add(string a, string b)    { return a + b; }
    };

    int main() {
        Calculator c;
        cout << c.add(5, 3);              // 8          -> int version
        cout << c.add(5.5, 3.2);          // 8.7        -> double version
        cout << c.add(1, 2, 3);           // 6          -> three-arg version
        cout << c.add("Bangla","desh");   // Bangladesh -> string version
    }
    ```

    Function overriding
    - A `subclass` provides its own version of a function inherited from its superclass, with `exactly the same signature`.
    - It is `runtime (dynamic) polymorphism`, and `requires inheritance`.
    ```java
    class Employee {
        double calculateSalary(double basic) { return basic; }
    }

    class Manager extends Employee {
        @Override
        double calculateSalary(double basic) { return basic + 0.40 * basic; }
    }

    class Officer extends Employee {
        @Override
        double calculateSalary(double basic) { return basic + 0.20 * basic; }
    }

    public class Main {
        public static void main(String[] args) {
            Employee[] staff = { new Manager(), new Officer(), new Employee() };
            for (Employee e : staff)
                System.out.println(e.calculateSalary(50000));
        }
    }
    ```
    Output
    ```
       70000.0     Manager
       60000.0     Officer
       50000.0     Employee
    ```
    - The reference type is `Employee` throughout, so the JVM must look at the actual object at run time — `dynamic method dispatch`.

    In C++, overriding requires `virtual`
    ```cpp
    class Base {
    public:
        virtual void show() { cout << "Base" << endl; }   // must be virtual
    };
    class Derived : public Base {
    public:
        void show() override { cout << "Derived" << endl; }
    };

    int main() {
        Base* p = new Derived();
        p->show();          // "Derived" - because show() is virtual
    }
    ```
    - Without `virtual`, `p->show()` would print "Base", since the call would be bound at compile time. Java makes every non-final method virtual automatically.

    Comparison

    | Point | Function overloading | Function overriding |
    |---|---|---|
    | Where | Same class or scope | Superclass and subclass |
    | Parameter list | Must `differ` | Must be `identical` |
    | Return type | May differ | Same or covariant |
    | Inheritance | Not needed | `Required` |
    | Resolved | Compile time | Run time |
    | Also called | Static / early binding | Dynamic / late binding |
    | C++ keyword | None | `virtual` in the base class |
    | `static` / `private` / `final` | Can be overloaded | Cannot be overridden |
    | Access modifier | Any | Cannot be more restrictive |
    | Purpose | Convenience — one name, related operations | Specialisation — change inherited behaviour |

    - Memory aid: `overloading changes the parameters; overriding changes the body`.

17. **What is virtual function with example?** *[BITAC Assistant Programmer 27.10.2023 compact it 560 (ET: BUTEX)], [Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 506 (ET: N/A)]*

    Answer: A `virtual function` is a member function declared with the `virtual` keyword in a base class, so that a call through a base-class `pointer or reference` is resolved at `run time` according to the object's actual type, not the pointer's declared type.

    - This is what makes `runtime polymorphism` possible in C++.

    Without virtual — the wrong version runs
    ```cpp
    #include <iostream>
    using namespace std;

    class Shape {
    public:
        void draw() { cout << "Drawing a shape" << endl; }   // NOT virtual
    };

    class Circle : public Shape {
    public:
        void draw() { cout << "Drawing a circle" << endl; }
    };

    int main() {
        Shape* p = new Circle();
        p->draw();          // prints "Drawing a shape"  <- WRONG
        return 0;
    }
    ```
    - The compiler binds the call at compile time, using the pointer's declared type `Shape*`. The `Circle` version is never reached.

    With virtual — the correct version runs
    ```cpp
    #include <iostream>
    using namespace std;

    class Shape {
    public:
        virtual void draw() { cout << "Drawing a shape" << endl; }
        virtual ~Shape() {}                     // virtual destructor - important
    };

    class Circle : public Shape {
    public:
        void draw() override { cout << "Drawing a circle" << endl; }
    };

    class Rectangle : public Shape {
    public:
        void draw() override { cout << "Drawing a rectangle" << endl; }
    };

    int main() {
        Shape* shapes[3];
        shapes[0] = new Shape();
        shapes[1] = new Circle();
        shapes[2] = new Rectangle();

        for (int i = 0; i < 3; i++)
            shapes[i]->draw();       // each object draws ITSELF

        for (int i = 0; i < 3; i++)
            delete shapes[i];
        return 0;
    }
    ```
    Output
    ```
       Drawing a shape
       Drawing a circle
       Drawing a rectangle
    ```

    How it works internally
    ```
       Every class with a virtual function gets a VTABLE - a table of pointers
       to its virtual function implementations. Every object of that class
       carries a hidden VPTR pointing to its class's vtable.

       p->draw()  becomes  (p->vptr[index of draw])()

       The object itself decides which function runs.
    ```

    Pure virtual function and abstract class
    ```cpp
    class Shape {
    public:
        virtual double area() = 0;      // PURE virtual - no body
        virtual ~Shape() {}
    };
    ```
    - A class with at least one pure virtual function is `abstract`: it cannot be instantiated, and every concrete subclass must provide the implementation. It is C++'s equivalent of a Java interface.

    Rules
    ```
       Virtual functions must be MEMBER functions
       A constructor cannot be virtual; a DESTRUCTOR SHOULD be, otherwise
            deleting through a base pointer leaks the derived part
       They work only through a POINTER or REFERENCE, not through an object
       A static function cannot be virtual
       In Java, EVERY non-static, non-final method is virtual by default
    ```

    - Why the virtual destructor matters: `delete shapes[1];` with a non-virtual destructor calls only `~Shape()`, so `Circle`'s own resources are never released. Making the base destructor virtual is a standard rule whenever a class is meant to be inherited from.

18. **How many classes can be used in Hybrid Inheritance?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

    Answer: `Hybrid inheritance` is a combination of two or more types of inheritance in one program — for example hierarchical inheritance together with multiple inheritance.

    - There is `no fixed number` of classes. A hybrid arrangement needs `at least four` classes to be meaningful, because it must combine at least two inheritance types, and in practice it may involve any number.

    The common four-class form — the diamond
    ```
                  A                 (base class)
                 / \
                /   \               hierarchical inheritance
               B     C
                \   /
                 \ /                multiple inheritance
                  D                 (derived from both B and C)

       Minimum : 4 classes
    ```
    ```cpp
    class A { public: void showA() { cout << "A"; } };
    class B : virtual public A { };          // hierarchical
    class C : virtual public A { };          // hierarchical
    class D : public B, public C { };        // multiple  -> HYBRID
    ```

    Another hybrid form — multilevel plus multiple
    ```
            A
            |            multilevel
            B      C
             \    /      multiple
               D

       Also 4 classes
    ```

    The five types of inheritance, for context
    ```
       1. Single        : A -> B                          2 classes
       2. Multilevel    : A -> B -> C                     3 classes
       3. Hierarchical  : A -> B , A -> C                 3 classes
       4. Multiple      : A , B -> C                      3 classes
       5. Hybrid        : any combination of the above    4 or more
    ```

    The problem hybrid inheritance creates
    - When the diamond shape appears, `D` inherits `two copies` of A — one through B and one through C — so any reference to a member of A is `ambiguous`.
    ```cpp
       D obj;
       obj.showA();     // ERROR: ambiguous - which copy of A?
    ```
    - The fix in C++ is `virtual inheritance`, which makes B and C share a single copy of A:
    ```cpp
       class B : virtual public A { };
       class C : virtual public A { };
    ```

    Language support

    | Language | Hybrid inheritance |
    |---|---|
    | C++ | Supported, with `virtual` base classes to resolve the diamond |
    | Java | Not through classes; only through `interfaces`, which a class may implement any number of |
    | C# | Same as Java |
    | Python | Supported, ambiguity resolved by the C3 linearisation MRO |

    Java equivalent
    ```java
    interface A { void showA(); }
    interface B extends A { }
    interface C extends A { }
    class D implements B, C {          // multiple inheritance of TYPE
        public void showA() { System.out.println("A"); }
    }
    ```

    - Short answer for the exam: `at least four classes`, and there is no upper limit. The classic diamond form uses exactly four — one base, two intermediate and one derived.

19. **What is Abstraction and Polymorphism expalin with example?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*

    Answer: Abstraction
    - `Abstraction` means showing only the `essential features` of an object and hiding the implementation details. The user is told `what` a class does, not `how` it does it.
    - Achieved with `abstract classes` and `interfaces`.
    ```java
    abstract class Shape {
        String name;
        Shape(String name) { this.name = name; }

        abstract double area();          // WHAT - no body, no "how"

        void display() {                 // a concrete method is also allowed
            System.out.println(name + " area = " + area());
        }
    }

    class Circle extends Shape {
        double r;
        Circle(double r) { super("Circle"); this.r = r; }
        @Override double area() { return 3.1416 * r * r; }      // the HOW
    }

    class Rectangle extends Shape {
        double l, w;
        Rectangle(double l, double w) { super("Rectangle"); this.l = l; this.w = w; }
        @Override double area() { return l * w; }               // a different HOW
    }

    public class Main {
        public static void main(String[] args) {
            Shape s1 = new Circle(5);
            Shape s2 = new Rectangle(4, 6);
            s1.display();          // Circle area = 78.54
            s2.display();          // Rectangle area = 24.0
            // Shape s = new Shape("x");   // ERROR - abstract class
        }
    }
    ```
    - Real-world analogy: a driver uses the `steering wheel, accelerator and brake`. How the rack, the fuel injection and the discs work is hidden. That hiding is abstraction.
    - An `interface` gives 100 per cent abstraction, since (before Java 8) it contained no implementation at all:
    ```java
    interface Payable { void pay(double amount); }
    ```

    Benefits of abstraction
    ```
       Reduces complexity - the user sees a small, clear interface
       The implementation can be replaced without breaking any caller
       Enforces a contract - every subclass MUST provide area()
       Improves security - internal working is not exposed
    ```

    Polymorphism
    - `Polymorphism` means "many forms": the same method name behaves differently depending on the object it acts on or the arguments given.
    ```
       Compile-time (static)  : method OVERLOADING  - the compiler decides
       Runtime (dynamic)      : method OVERRIDING   - the JVM decides
    ```
    ```java
    // compile-time : overloading
    class Calculator {
        int    add(int a, int b)       { return a + b; }
        double add(double a, double b) { return a + b; }
        int    add(int a, int b, int c){ return a + b + c; }
    }

    // runtime : overriding
    class Animal { void sound() { System.out.println("Some sound"); } }
    class Dog extends Animal { @Override void sound() { System.out.println("Bhow Bhow"); } }
    class Cat extends Animal { @Override void sound() { System.out.println("Meow"); } }

    Animal a;
    a = new Dog();  a.sound();      // Bhow Bhow
    a = new Cat();  a.sound();      // Meow
    ```
    - In the runtime case the reference type is `Animal`, so the compiler cannot know which version will run; the JVM inspects the real object — `dynamic method dispatch`.

    How the two work together
    - In the Shape program above, `abstraction` declares that every shape `has` an area, and `polymorphism` makes each shape compute it its own way. The loop
    ```java
       for (Shape s : shapes) s.display();
    ```
    works for every shape, and for shapes not yet written — abstraction defines the contract, polymorphism supplies the many behaviours.

    | Point | Abstraction | Polymorphism |
    |---|---|---|
    | Meaning | Hide the implementation, show the essentials | One name, many forms |
    | Question it answers | `What` does it do? | `Which` version runs? |
    | Achieved by | Abstract classes, interfaces | Overloading, overriding |
    | Decided | At design time | At compile time or run time |
    | Purpose | Reduce complexity, define a contract | Flexibility and extensibility |

20. **(খ) কী কী ধারণার উপর ভিত্তি করে OOP প্রতিষ্ঠিত? ধারণাগুলো ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Object-Oriented Programming is founded on `four` core concepts, usually called the four pillars.

    1. Encapsulation
    - Binding the `data` and the `methods` that operate on it into a single unit — the class — and `hiding` the internal state behind private fields with public accessor methods.
    ```java
    class Account {
        private double balance;                  // hidden from the outside

        public void deposit(double amt) {
            if (amt > 0) balance += amt;         // access is validated
        }
        public double getBalance() { return balance; }
    }
    ```
    - Benefit: the object cannot be put into an invalid state from outside, and the internal representation can be changed later without breaking any caller.

    2. Abstraction
    - Showing only the `essential features` and hiding the implementation. The user learns `what` a class does, not `how`.
    ```java
    abstract class Shape {
        abstract double area();            // WHAT, with no HOW
    }
    class Circle extends Shape {
        double r;
        @Override double area() { return 3.1416 * r * r; }
    }
    ```
    - Benefit: reduces complexity and defines a `contract` that every subclass must honour. A driver uses the steering wheel without knowing the mechanism.

    3. Inheritance
    - A new class acquires the fields and methods of an existing one, expressing an `is-a` relationship.
    ```java
    class Animal { void eat() { System.out.println("eats food"); } }
    class Dog extends Animal { void bark() { System.out.println("barks"); } }
    ```
    ```
       Types : single , multilevel , hierarchical ,
               multiple (through interfaces in Java) , hybrid
    ```
    - Benefit: `code reuse`, a natural hierarchy, and it is what makes runtime polymorphism possible.

    4. Polymorphism
    - One method name behaving differently depending on the object or the arguments.
    ```java
    // compile-time : overloading
    int add(int a, int b);      double add(double a, double b);

    // runtime : overriding
    Animal a = new Dog();
    a.sound();                  // the Dog version runs
    ```
    - Benefit: one interface serves many implementations, and a new subclass can be added without changing existing code — the `open-closed principle`.

    Two supporting concepts often added
    ```
       Message passing : objects communicate by calling each other's methods
       Dynamic binding : which method body runs is decided at RUN TIME,
                         from the actual object - this is what enables
                         runtime polymorphism
    ```

    The building blocks these concepts rest on
    ```
       CLASS  : the blueprint - it defines attributes and methods
       OBJECT : an instance of a class, occupying real memory
    ```
    ```java
    class Student {          // class = blueprint
        String name; int roll;
        void display() { ... }
    }
    Student s1 = new Student();     // object = instance
    ```

    - Together these ideas give OOP its practical advantages: `reusability, maintainability, modularity, data security and extensibility`. Languages built on them include `Java, C++, C#, Python, Kotlin` and `Swift`.

21. **(গ) Inheritance কী? উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `Inheritance` is the mechanism by which one class acquires the fields and methods of another. The existing class is the `superclass` (parent, base) and the new one the `subclass` (child, derived).

    - It expresses an `is-a` relationship: a `Dog is an Animal`, a `Manager is an Employee`.
    - Its purposes are `code reuse` and the creation of a natural hierarchy. It is also what makes runtime polymorphism possible.

    Basic example
    ```java
    class Animal {                       // superclass
        String name;

        void eat()   { System.out.println(name + " eats food"); }
        void sleep() { System.out.println(name + " sleeps"); }
    }

    class Dog extends Animal {           // subclass - inherits eat() and sleep()
        void bark() { System.out.println(name + " barks: Bhow Bhow"); }
    }

    public class Main {
        public static void main(String[] args) {
            Dog d = new Dog();
            d.name = "Tommy";
            d.eat();      // inherited from Animal
            d.sleep();    // inherited from Animal
            d.bark();     // its own
        }
    }
    ```
    Output
    ```
       Tommy eats food
       Tommy sleeps
       Tommy barks: Bhow Bhow
    ```
    - `eat()` and `sleep()` were written once and are used by every subclass — that is the reuse.

    Types of inheritance
    ```
       1. SINGLE            A -> B
       2. MULTILEVEL        A -> B -> C
       3. HIERARCHICAL      A -> B , A -> C
       4. MULTIPLE          A , B -> C     (Java: interfaces only)
       5. HYBRID            a combination of the above
    ```
    ```
       Single           Multilevel        Hierarchical         Multiple
          A                 A                  A                A   B
          |                 |                 / \                \ /
          B                 B                B   C                C
                            |
                            C
    ```

    Multilevel example
    ```java
    class Animal      { void eat()  { ... } }
    class Dog extends Animal { void bark() { ... } }
    class Puppy extends Dog  { void weep() { ... } }
    // Puppy inherits from BOTH Dog and Animal
    ```

    Practical example — a bank account hierarchy
    ```java
    class Account {
        protected String accNo;
        protected double balance;

        void deposit(double a) { balance += a; }
        double getInterest()   { return 0; }
    }

    class SavingsAccount extends Account {
        @Override double getInterest() { return balance * 0.06; }
    }

    class CurrentAccount extends Account {
        @Override double getInterest() { return 0; }   // no interest
    }
    ```
    - `deposit()` is written once; each subclass supplies only what differs.

    Keywords used with inheritance
    ```
       extends   : Java class inheritance
       implements: Java interface inheritance
       super     : refers to the parent - super() calls its constructor,
                   super.method() calls its version
       @Override : marks a method that redefines an inherited one
       protected : visible to the class itself and to its subclasses
       final     : a final class cannot be inherited; a final method cannot
                   be overridden
    ```

    Advantages
    ```
       Code reuse - common members written once
       Easier maintenance - fix a bug once, every subclass benefits
       Natural modelling of a real hierarchy
       Enables polymorphism, which is its most valuable consequence
       Extensibility - a new subclass needs no change to existing code
    ```

    Cautions
    ```
       It creates TIGHT COUPLING : a change in the superclass can break every
           subclass. Deep hierarchies become fragile.
       Java forbids multiple inheritance of classes, to avoid the DIAMOND
           PROBLEM; interfaces provide it safely instead.
       Modern advice is "prefer COMPOSITION over inheritance" - use
           inheritance only for a genuine is-a relationship.
    ```

22. **(ক) অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং কী? এটা কেন দরকার? অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর মৌলিক ধারণাগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What OOP is
    - `Object-Oriented Programming` organises a program around `objects` — bundles of `data` and the `methods` that act on that data — rather than around functions operating on separate data.
    - A `class` is the blueprint; an `object` is an instance of it, occupying real memory.
    ```java
    class Student {                 // class = blueprint
        String name;  int roll;     // attributes (state)
        void display() { ... }      // methods (behaviour)
    }
    Student s1 = new Student();     // object = instance
    ```

    Why it is needed — the problems it solves
    - `Procedural programs do not scale.` In C, data is global and any function can change it. Beyond a few thousand lines, finding which function corrupted a value becomes very difficult.
    - `Data was unprotected.` OOP makes fields `private`, so an object cannot be put into an invalid state from outside.
    - `Code was duplicated.` Procedural reuse means copying functions. OOP gives `inheritance`, so common code is written once.
    - `Change was expensive.` Altering a data structure meant editing every function that touched it. In OOP a change is confined to one class.
    - `Programs did not match the problem.` A bank has customers, accounts and loans — real things. OOP models them directly as objects, so the design mirrors the problem.
    - `Extension required editing.` Adding a new case in procedural code means editing every `switch` statement. With polymorphism, a new subclass is simply added.
    - `Team development was hard.` Classes are self-contained, so different developers can work on different classes at once.

    The four pillars

    1. `Encapsulation` — bind data and methods together and hide the internal state
    ```java
    class Account {
        private double balance;
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```

    2. `Abstraction` — show the essentials, hide the implementation
    ```java
    abstract class Shape { abstract double area(); }
    ```

    3. `Inheritance` — a new class acquires the members of an existing one
    ```java
    class Dog extends Animal { void bark() { ... } }
    ```

    4. `Polymorphism` — one name, many forms
    ```
       Compile-time : method overloading
       Runtime      : method overriding
    ```

    Advantages
    ```
       Reusability      : inheritance and composition
       Maintainability  : changes stay inside one class
       Modularity       : each class is a self-contained unit
       Data security    : encapsulation protects the state
       Extensibility    : add a class, do not edit existing ones
       Real-world model : objects map onto real entities
       Team development : parallel work on separate classes
    ```

    Disadvantages
    ```
       Steeper learning curve
       Larger programs and some runtime overhead
       Over-engineering is easy - a short script does not need classes
       Deep inheritance hierarchies become fragile
    ```

    - Languages: `Java, C++, C#, Python, Kotlin, Swift, Ruby`. Java and C# are almost purely object-oriented; C++ and Python allow both procedural and object-oriented styles.

23. **(গ) Overloading এবং overriding এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Both are forms of `polymorphism`, but they differ in `where` they occur and `when` the decision is made.

    Overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` chooses which one to call.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }
    ```
    - No inheritance is needed. It is `compile-time (static, early) binding`.
    - Return type alone cannot distinguish two overloads.

    Overriding
    - A `subclass` supplies its own version of a method inherited from its superclass, with `exactly the same signature`. The `JVM` decides at run time which body to execute.
    ```java
    class Animal {
        void sound() { System.out.println("Some sound"); }
    }
    class Dog extends Animal {
        @Override void sound() { System.out.println("Bhow Bhow"); }
    }

    Animal a = new Dog();
    a.sound();          // "Bhow Bhow" - decided at RUN TIME
    ```
    - Inheritance is required. It is `runtime (dynamic, late) binding`.

    Difference

    | Point | Overloading | Overriding |
    |---|---|---|
    | Where it occurs | Within the `same class` | Between `superclass and subclass` |
    | Parameter list | Must be `different` | Must be `identical` |
    | Return type | May differ | Same or covariant |
    | Inheritance | Not required | `Required` |
    | Binding | Static, at compile time | Dynamic, at run time |
    | Also called | Early binding | Late binding |
    | Access modifier | Any | Cannot be more restrictive |
    | `static` methods | Can be overloaded | Cannot be overridden (only hidden) |
    | `private` methods | Can be overloaded | Cannot be overridden |
    | `final` methods | Can be overloaded | Cannot be overridden |
    | Constructors | Can be overloaded | Cannot be overridden |
    | C++ keyword needed | None | `virtual` in the base class |
    | Performance | Slightly faster | A small runtime lookup |
    | Purpose | Convenience — one name for related operations | Specialisation — change inherited behaviour |
    | Number of classes | 1 | 2 or more |

    Worked contrast
    ```java
    class Base {
        void show(int a)        { System.out.println("Base int"); }
        void show(String s)     { System.out.println("Base String"); }  // OVERLOAD
    }
    class Derived extends Base {
        @Override
        void show(int a)        { System.out.println("Derived int"); }  // OVERRIDE
    }

    public class Main {
        public static void main(String[] args) {
            Base b = new Derived();
            b.show(5);          // "Derived int"   -> overriding, runtime
            b.show("hi");       // "Base String"   -> overloading, compile time
        }
    }
    ```

    - The memory aid: `overloading changes the parameters; overriding changes the body`.

24. **What is Polymorphism? Java language এর আলোকে ব্যাখ্যা কর।** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) `Polymorphism` means "many forms". The same method name behaves differently depending on the object it is called on or the arguments it is given, so one interface serves many implementations.

    In Java it takes two forms.

    1. Compile-time polymorphism — method overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` selects the version by matching the arguments.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
        String add(String a, String b)    { return a + b; }
    }

    public class Main {
        public static void main(String[] args) {
            Calculator c = new Calculator();
            System.out.println(c.add(5, 3));             // 8
            System.out.println(c.add(5.5, 3.2));         // 8.7
            System.out.println(c.add(1, 2, 3));          // 6
            System.out.println(c.add("Bangla","desh"));  // Bangladesh
        }
    }
    ```
    - Also called `static` or `early binding`. Return type alone cannot distinguish overloads.
    - `Constructor overloading` is the same idea applied to constructors, which is why an object can be created in several different ways.

    2. Runtime polymorphism — method overriding
    - A `subclass` supplies its own version of an inherited method, with the same signature. The `JVM` decides at run time which body to run, based on the `actual object` rather than the reference type. This is `dynamic method dispatch`.
    ```java
    class Payment {
        void pay(double amount) { System.out.println("Generic payment: " + amount); }
    }
    class CardPayment extends Payment {
        @Override void pay(double amount) { System.out.println("Card: " + amount); }
    }
    class BkashPayment extends Payment {
        @Override void pay(double amount) { System.out.println("bKash: " + amount); }
    }

    public class Main {
        public static void main(String[] args) {
            Payment p;                         // SUPERCLASS reference

            p = new CardPayment();   p.pay(500);   // Card: 500.0
            p = new BkashPayment();  p.pay(300);   // bKash: 300.0
        }
    }
    ```

    Java-specific points
    - Every non-static, non-final method in Java is `virtual by default`, so no `virtual` keyword is needed as it is in C++.
    - `@Override` is optional but strongly recommended — the compiler then catches a mistyped signature that would silently become an overload instead.
    - `static`, `private` and `final` methods `cannot be overridden`. A static method with the same signature in a subclass is `hidden`, not overridden, and is resolved by the reference type.
    - Polymorphism also works through `interfaces`, which is how Java achieves multiple inheritance of type:
    ```java
    interface Payable { void pay(double amount); }
    ```
    - The relationship `Dog IS-A Animal` is what allows `Animal a = new Dog();`. Assigning the other way needs an explicit `downcast` and can throw `ClassCastException`.

    Comparison

    | Point | Compile-time | Runtime |
    |---|---|---|
    | Achieved by | Overloading | Overriding |
    | Decided by | The compiler | The JVM |
    | Based on | The argument list | The actual object |
    | Inheritance | Not needed | Required |
    | Binding | Early / static | Late / dynamic |
    | Speed | Faster | Slightly slower |

    - Why runtime polymorphism matters most: it lets code written today work with classes written tomorrow. A loop over `Payment` objects needs no change when a new payment type is added — the `open-closed principle`.

25. **(a) What is Polymorphism? Distinguish between compile time and runtime polymorphisms.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

    Answer: What polymorphism is
    - `Polymorphism` means "many forms". The same method name behaves differently depending on the object it is called on or the arguments given to it, so `one interface serves many implementations`.
    - It is one of the four pillars of OOP, alongside encapsulation, inheritance and abstraction.

    Compile-time polymorphism (static, early binding)
    - The `compiler` decides which method to call, from the `number, types and order of the arguments`.
    - Achieved by `method overloading` and, in C++, `operator overloading`.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }

    Calculator c = new Calculator();
    c.add(5, 3);          // 8    -> the int version
    c.add(5.5, 3.2);      // 8.7  -> the double version
    c.add(1, 2, 3);       // 6    -> the three-argument version
    ```
    - No inheritance is needed, and there is no runtime cost, since everything is settled before the program runs.

    Runtime polymorphism (dynamic, late binding)
    - The `JVM` decides at run time, from the `actual object` the reference points to — not from the reference's declared type.
    - Achieved by `method overriding`, and it requires inheritance.
    ```java
    class Shape {
        void draw() { System.out.println("Drawing a shape"); }
    }
    class Circle extends Shape {
        @Override void draw() { System.out.println("Drawing a circle"); }
    }
    class Square extends Shape {
        @Override void draw() { System.out.println("Drawing a square"); }
    }

    public class Main {
        public static void main(String[] args) {
            Shape[] shapes = { new Shape(), new Circle(), new Square() };
            for (Shape s : shapes) s.draw();
        }
    }
    ```
    Output
    ```
       Drawing a shape
       Drawing a circle
       Drawing a square
    ```
    - Every element of the array is declared as `Shape`, so the compiler cannot know which `draw()` will run. The JVM inspects the real object — `dynamic method dispatch`.

    Distinction

    | Point | Compile-time polymorphism | Runtime polymorphism |
    |---|---|---|
    | Also called | Static / early binding | Dynamic / late binding |
    | Achieved by | Method overloading, operator overloading | Method overriding |
    | Decided by | The compiler | The JVM, while running |
    | Based on | The argument list | The actual object type |
    | Inheritance required | No | `Yes` |
    | Number of classes | One is enough | Two or more |
    | Parameters | Must differ | Must be identical |
    | Speed | Faster — resolved once | Slightly slower — a vtable lookup |
    | Flexibility | Less | More |
    | C++ requirement | None | The base method must be `virtual` |
    | `static` / `private` / `final` | Can be overloaded | Cannot be overridden |
    | Example | `add(int,int)` and `add(double,double)` | `Shape s = new Circle(); s.draw();` |

    - Why runtime polymorphism is the more powerful of the two: it lets code written today operate on classes written tomorrow. Adding a `Triangle` subclass requires no change at all to the loop above — the `open-closed principle`, open for extension and closed for modification.

26. **Write down the principle of OOP?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)], [BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

    Answer: OOP rests on `four` core principles, usually called the four pillars.

    1. Encapsulation
    - Binding the data and the methods that operate on it into one unit, and `hiding` the internal state behind private fields with public accessor methods.
    ```java
    class Account {
        private double balance;                    // hidden

        public void deposit(double amt) {
            if (amt > 0) balance += amt;           // validated access
        }
        public double getBalance() { return balance; }
    }
    ```
    - Benefit: the object cannot be put into an invalid state from outside, and the internal representation can be changed without breaking callers.

    2. Abstraction
    - Showing only the `essential features` and hiding the implementation, so the user knows `what` a class does but not `how`.
    ```java
    abstract class Shape {
        abstract double area();          // WHAT, without the HOW
    }
    ```
    - Achieved with `abstract classes` and `interfaces`. Benefit: reduces complexity and defines a contract every subclass must honour.

    3. Inheritance
    - A new class acquires the fields and methods of an existing one, expressing an `is-a` relationship.
    ```java
    class Animal { void eat() { ... } }
    class Dog extends Animal { void bark() { ... } }
    ```
    ```
       Types : single , multilevel , hierarchical ,
               multiple (via interfaces in Java) , hybrid
    ```
    - Benefit: `code reuse`, a natural hierarchy, and it is what makes runtime polymorphism possible.

    4. Polymorphism
    - One method name behaving differently depending on the object or the arguments.
    ```
       Compile-time : method OVERLOADING - the compiler decides
       Runtime      : method OVERRIDING  - the JVM decides
    ```
    ```java
    Animal a = new Dog();
    a.sound();                // the Dog version runs, chosen at run time
    ```
    - Benefit: one interface serves many implementations, and new subclasses can be added without changing existing code.

    Two supporting concepts often listed as well
    ```
       Message passing : objects communicate by calling each other's methods
       Dynamic binding : the method body is chosen at RUN TIME from the actual
                         object - this is what enables runtime polymorphism
    ```

    The building blocks they rest on
    ```
       CLASS  : the blueprint - defines attributes and methods
       OBJECT : an instance of the class, occupying real memory
    ```

    - The practical consequences are `reusability, maintainability, modularity, data security` and `extensibility`, which is why OOP became the standard approach for large, long-lived software.

27. **Write down the properties/function of OOP?** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer: The properties of OOP are the four pillars together with the mechanisms that support them.

    1. Encapsulation
    - Binds data and the methods that act on it into a single unit, and `hides` the internal state.
    ```java
    class Account {
        private double balance;
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```
    - Function: `data protection`. Nothing outside can put the object into an invalid state.

    2. Abstraction
    - Shows only the `essential features` and hides the implementation.
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - Function: `reduces complexity` and defines a contract that every subclass must fulfil.

    3. Inheritance
    - A new class acquires the members of an existing one, an `is-a` relationship.
    ```java
    class Dog extends Animal { void bark() { ... } }
    ```
    - Function: `code reuse` and a natural hierarchy.

    4. Polymorphism
    - One method name, many behaviours.
    ```
       Compile-time : overloading    Runtime : overriding
    ```
    - Function: `flexibility` — one interface serves many implementations.

    5. Class and Object
    ```
       CLASS  : the blueprint, defining attributes and methods
       OBJECT : an instance of the class, occupying real memory
    ```
    - Function: they are the unit of organisation; everything else is built on them.

    6. Message passing
    - Objects communicate by `calling each other's methods`, passing data as arguments.
    - Function: this is how work actually gets done between collaborating objects.

    7. Dynamic binding
    - Which method body runs is decided at `run time`, from the actual object.
    - Function: it is the mechanism that makes runtime polymorphism work.

    8. Constructor and destructor
    ```java
    class Student {
        Student() { ... }             // constructor - runs when the object is created
    }
    ```
    - Function: automatic initialisation and cleanup, so an object is never used uninitialised.

    9. Access modifiers
    ```
       private   : visible inside the class only
       protected : the class and its subclasses
       public    : everywhere
       default   : the same package (Java)
    ```
    - Function: they are the tool by which encapsulation is actually enforced.

    Overall functions of OOP
    ```
       Reusability      : write once, inherit or compose many times
       Maintainability  : a change stays inside one class
       Modularity       : each class is a self-contained unit
       Data security    : private fields, validated access
       Extensibility    : add a class instead of editing existing ones
       Real-world model : objects correspond to real entities
       Team development : different developers own different classes
    ```

    - Languages built on these properties: `Java, C++, C#, Python, Kotlin, Swift, Ruby`.

28. **Write down the main feature of Object Oriented Programming (OOP).** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

    Answer: The main features of OOP are the four pillars, plus the class and object mechanism on which they rest.

    1. Class and Object
    ```
       CLASS  : a blueprint that defines attributes and methods
       OBJECT : an instance of that class, occupying real memory
    ```
    ```java
    class Student {
        String name;  int roll;          // attributes
        void display() { ... }           // method
    }
    Student s1 = new Student();          // object
    ```

    2. Encapsulation
    - Binding data and methods into one unit and `hiding` the internal state behind private fields with public accessors.
    ```java
    class Account {
        private double balance;
        public void deposit(double a) { if (a > 0) balance += a; }
    }
    ```
    - The balance cannot be set to a negative value from outside, because the only way in validates.

    3. Abstraction
    - Showing only the `essential features` and hiding the implementation.
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - The caller learns `what` a class does, not `how`.

    4. Inheritance
    - A new class acquires the fields and methods of an existing one.
    ```java
    class Animal { void eat() { ... } }
    class Dog extends Animal { void bark() { ... } }
    ```
    ```
       Types : single , multilevel , hierarchical , multiple , hybrid
    ```

    5. Polymorphism
    - One method name, many behaviours.
    ```
       Compile-time : method OVERLOADING
       Runtime      : method OVERRIDING
    ```
    ```java
    Animal a = new Dog();
    a.sound();                   // the Dog version runs
    ```

    6. Message passing
    - Objects cooperate by `calling each other's methods` and passing data as arguments.

    7. Dynamic binding
    - The method body is chosen at `run time`, from the actual object — the mechanism behind runtime polymorphism.

    8. Constructor and destructor
    - Automatic initialisation when an object is created, and cleanup when it is destroyed, so an object is never used uninitialised.

    9. Access modifiers
    ```
       private , protected , public , default
    ```
    - The tool by which encapsulation is actually enforced.

    Benefits these features deliver
    ```
       Reusability      : inheritance and composition
       Maintainability  : a change stays inside one class
       Modularity       : classes are self-contained units
       Data security    : private state, validated access
       Extensibility    : add a class rather than edit existing ones
       Real-world model : objects match real entities
       Team development : parallel work on separate classes
    ```

    - Languages: `Java, C++, C#, Python, Kotlin, Swift, Ruby`. Java and C# are almost purely object-oriented, while C++ and Python support both procedural and object-oriented styles.

29. **Write a Java code with a case where you have to mentioned functionalities with override method.** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 757 (ET: N/A)]*

    Answer: The example below models a bank's payment system, in which each payment type overrides the general behaviour with its own.

    ```java
    // ---------- superclass ----------
    class Payment {
        protected String customerName;
        protected double amount;

        Payment(String customerName, double amount) {
            this.customerName = customerName;
            this.amount = amount;
        }

        // the method that subclasses will OVERRIDE
        void processPayment() {
            System.out.println("Processing a generic payment of " + amount);
        }

        double serviceCharge() {          // will also be overridden
            return 0;
        }

        // a concrete method shared by every subclass
        void printReceipt() {
            System.out.println("--------------------------------");
            System.out.println("Customer : " + customerName);
            System.out.println("Amount   : " + amount);
            System.out.println("Charge   : " + serviceCharge());
            System.out.println("Total    : " + (amount + serviceCharge()));
            System.out.println("--------------------------------");
        }
    }

    // ---------- subclass 1 ----------
    class CardPayment extends Payment {
        private String cardNumber;

        CardPayment(String name, double amount, String cardNumber) {
            super(name, amount);
            this.cardNumber = cardNumber;
        }

        @Override
        void processPayment() {
            System.out.println("Charging card ending " +
                cardNumber.substring(cardNumber.length() - 4) +
                " for " + amount);
        }

        @Override
        double serviceCharge() {
            return amount * 0.015;        // 1.5 % card fee
        }
    }

    // ---------- subclass 2 ----------
    class MobileBanking extends Payment {
        private String mobileNumber;

        MobileBanking(String name, double amount, String mobileNumber) {
            super(name, amount);
            this.mobileNumber = mobileNumber;
        }

        @Override
        void processPayment() {
            System.out.println("Sending " + amount + " from " + mobileNumber);
        }

        @Override
        double serviceCharge() {
            return amount * 0.0185;       // 1.85 % cash-out fee
        }
    }

    // ---------- subclass 3 ----------
    class CashPayment extends Payment {
        CashPayment(String name, double amount) {
            super(name, amount);
        }

        @Override
        void processPayment() {
            System.out.println("Receiving " + amount + " in cash at the counter");
        }
        // serviceCharge() is NOT overridden, so the inherited 0 is used
    }

    // ---------- main ----------
    public class Main {
        public static void main(String[] args) {

            Payment[] payments = {                 // superclass references
                new CardPayment("Rahim", 5000, "4532123456781234"),
                new MobileBanking("Karim", 3000, "01712345678"),
                new CashPayment("Jamal", 2000)
            };

            for (Payment p : payments) {
                p.processPayment();     // the OVERRIDDEN version runs
                p.printReceipt();       // inherited, but calls the overridden
            }                           // serviceCharge() inside it
        }
    }
    ```

    Output
    ```
       Charging card ending 1234 for 5000.0
       --------------------------------
       Customer : Rahim
       Amount   : 5000.0
       Charge   : 75.0
       Total    : 5075.0
       --------------------------------
       Sending 3000.0 from 01712345678
       --------------------------------
       Customer : Karim
       Amount   : 3000.0
       Charge   : 55.5
       Total    : 3055.5
       --------------------------------
       Receiving 2000.0 in cash at the counter
       --------------------------------
       Customer : Jamal
       Amount   : 2000.0
       Charge   : 0.0
       Total    : 2000.0
       --------------------------------
    ```

    Points the example demonstrates
    - `processPayment()` and `serviceCharge()` are `overridden` — same name, same parameters, same return type, different body.
    - The array holds `Payment` references, so the compiler cannot know which version will run. The JVM chooses from the actual object — `dynamic method dispatch`.
    - `printReceipt()` is `not` overridden, yet it produces the right charge for every subclass, because the `serviceCharge()` it calls is resolved polymorphically. This is the real power of overriding.
    - `CashPayment` deliberately omits `serviceCharge()`, so the inherited version is used — overriding is optional.
    - `@Override` is not required by the compiler, but it makes it report an error if the signature is mistyped, which would otherwise silently create an overload instead.
    - Adding a new payment type, say `ChequePayment`, requires no change at all to `main` — the `open-closed principle`.

30. **(ক) Procedural Oriented ও Object Oriented Programming Languages মধ্যে পার্থক্য কি? উভয় Language এর ২টি করে উদাহরণ দিন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `Procedure-oriented programming (POP)` organises a program around `functions` that act on data held separately. `Object-oriented programming (OOP)` organises it around `objects` that hold data and behaviour together.

    Procedure-oriented programming
    - The program is a sequence of `functions` or procedures, designed `top-down`: the problem is broken into smaller tasks, each a function.
    - Data is largely `global`, so any function can read or change it.
    - Reuse means calling or copying a function.
    ```c
    struct Student { char name[50]; int roll; };   /* data */

    void display(struct Student s) {               /* separate function */
        printf("%s %d", s.name, s.roll);
    }
    ```

    Object-oriented programming
    - The program is a set of `objects` that hold data and the methods that act on it, designed `bottom-up`: the entities are identified first, then their behaviour.
    - Data is `private` inside the object, reachable only through its methods.
    - Reuse comes from `inheritance` and composition.
    ```java
    class Student {
        private String name;  private int roll;    // data AND
        public void display() {                    // behaviour together
            System.out.println(name + " " + roll);
        }
    }
    ```

    Difference

    | Point | Procedure-oriented | Object-oriented |
    |---|---|---|
    | Organised around | Functions | Objects |
    | Data and functions | Separate | Bound together |
    | Data access | Global, open to every function | Private, controlled by methods |
    | Approach | Top-down | Bottom-up |
    | Data security | Weak | Strong, through encapsulation |
    | Reuse | Copy or call functions | Inheritance and composition |
    | Polymorphism | Not supported | Supported |
    | Inheritance | Not supported | Supported |
    | Extending the program | Often requires editing existing code | Add a new class |
    | Real-world modelling | Weak | Strong |
    | Program division | Into functions | Into classes and objects |
    | Overloading | Not supported | Supported |
    | Suited to | Small and medium programs | Large, evolving systems |
    | Debugging | Harder as size grows | Easier — errors are localised |

    Two examples of each

    `Procedure-oriented languages`
    ```
       1. C        - the classic structured language; functions plus structs
       2. Pascal   - designed for teaching structured programming
       Others : FORTRAN, COBOL, BASIC, ALGOL
    ```

    `Object-oriented languages`
    ```
       1. Java     - almost purely object-oriented, platform independent
       2. C++      - multi-paradigm; adds classes to C, plus operator
                     overloading and multiple inheritance
       Others : C#, Python, Ruby, Kotlin, Swift, Smalltalk
    ```

    - A practical note: `C++ and Python are multi-paradigm`, so the same language can be used in either style. The distinction is therefore about `how a program is designed`, not only about the language chosen.
    - Neither is universally better. POP suits small scripts, embedded code and numerical work; OOP suits large business systems that must be maintained and extended for years.

31. **(i) Object Oriented Programming এর যেকোন দুটি বৈশিষ্ট্য উদাহরণসহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 781 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Two features of OOP are explained below.

    1. Encapsulation
    - `Encapsulation` binds the data and the methods that act on it into a single unit — the class — and `hides` the internal state behind private fields, exposing only controlled public methods.
    ```java
    class BankAccount {
        private String accountNumber;          // hidden
        private double balance;                // hidden

        public BankAccount(String accNo, double opening) {
            this.accountNumber = accNo;
            this.balance = (opening > 0) ? opening : 0;
        }

        public void deposit(double amount) {
            if (amount > 0) {
                balance += amount;
                System.out.println("Deposited " + amount);
            } else {
                System.out.println("Invalid amount");
            }
        }

        public void withdraw(double amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
            } else {
                System.out.println("Insufficient balance or invalid amount");
            }
        }

        public double getBalance() { return balance; }   // read-only access
    }

    public class Main {
        public static void main(String[] args) {
            BankAccount acc = new BankAccount("AC1001", 5000);
            acc.deposit(2000);
            acc.withdraw(10000);        // rejected
            System.out.println(acc.getBalance());   // 7000.0

            // acc.balance = -99999;    // COMPILE ERROR - balance is private
        }
    }
    ```
    - What it achieves: the account can never hold a negative balance, because the only routes in are `deposit()` and `withdraw()`, and both validate. Without encapsulation, `acc.balance = -99999;` would be legal and would corrupt the data.
    - It also means the internal representation could later be changed — storing paisa as an integer, say — without breaking a single caller.

    2. Inheritance
    - `Inheritance` lets a new class acquire the fields and methods of an existing one, expressing an `is-a` relationship.
    ```java
    class Vehicle {                              // superclass
        protected String brand;
        protected int wheels;

        Vehicle(String brand, int wheels) {
            this.brand = brand;
            this.wheels = wheels;
        }

        void start() { System.out.println(brand + " is starting"); }
        void display() { System.out.println(brand + " has " + wheels + " wheels"); }
    }

    class Car extends Vehicle {                  // Car IS-A Vehicle
        Car(String brand) { super(brand, 4); }

        void openBoot() { System.out.println("Boot opened"); }
    }

    class Motorcycle extends Vehicle {           // Motorcycle IS-A Vehicle
        Motorcycle(String brand) { super(brand, 2); }
    }

    public class Main {
        public static void main(String[] args) {
            Car c = new Car("Toyota");
            c.start();        // inherited from Vehicle
            c.display();      // inherited
            c.openBoot();     // its own

            Motorcycle m = new Motorcycle("Honda");
            m.display();      // Honda has 2 wheels
        }
    }
    ```
    Output
    ```
       Toyota is starting
       Toyota has 4 wheels
       Boot opened
       Honda has 2 wheels
    ```
    - What it achieves: `start()` and `display()` were written once and are used by both subclasses. Fixing a bug in `display()` fixes it for every vehicle type at once.
    - It also enables `polymorphism`: because a `Car` is a `Vehicle`, one array of `Vehicle` can hold every kind and one loop can start them all.

    - The other two features, for completeness, are `abstraction` (show the essentials, hide the implementation) and `polymorphism` (one name, many forms). Together these four are the pillars of object-oriented programming.

32. **(i) Object Oriented Programming এ Static binding and Dynamic binding কি? ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `Binding` means connecting a method call to the actual method body that will run. The question is `when` that connection is made.

    Static binding (early binding, compile-time binding)
    - The link is decided by the `compiler`, before the program runs, from the `declared type` of the reference.
    - It applies to methods that cannot be overridden:
    ```
       static methods
       private methods
       final methods
       overloaded methods
       variables (fields), which are ALWAYS statically bound
    ```
    ```java
    class Calculator {
        static void show()          { System.out.println("Static method"); }
        private void hidden()       { System.out.println("Private method"); }
        final void locked()         { System.out.println("Final method"); }

        int add(int a, int b)       { return a + b; }      // overloaded
        double add(double a, double b) { return a + b; }   // overloaded
    }
    ```
    - The compiler knows exactly which body each call refers to, so it can be resolved once and for all. This makes it `faster`, with no lookup at run time.

    Dynamic binding (late binding, runtime binding)
    - The link is decided by the `JVM` while the program runs, from the `actual object` the reference points to — not from the reference's declared type.
    - It applies to `overridden` instance methods, and it is what makes runtime polymorphism possible.
    ```java
    class Animal {
        void sound() { System.out.println("Some sound"); }
    }
    class Dog extends Animal {
        @Override void sound() { System.out.println("Bhow Bhow"); }
    }
    class Cat extends Animal {
        @Override void sound() { System.out.println("Meow"); }
    }

    public class Main {
        public static void main(String[] args) {
            Animal a;

            a = new Dog();   a.sound();      // Bhow Bhow
            a = new Cat();   a.sound();      // Meow
        }
    }
    ```
    - The reference `a` is declared `Animal` in both lines, so the compiler cannot choose. The JVM checks the real object each time — `dynamic method dispatch`.

    A worked contrast that shows both at once
    ```java
    class Base {
        static void staticMethod()   { System.out.println("Base static"); }
        void instanceMethod()        { System.out.println("Base instance"); }
        int x = 10;
    }
    class Derived extends Base {
        static void staticMethod()   { System.out.println("Derived static"); }
        @Override void instanceMethod() { System.out.println("Derived instance"); }
        int x = 20;
    }

    public class Main {
        public static void main(String[] args) {
            Base b = new Derived();

            b.instanceMethod();     // "Derived instance"  -> DYNAMIC binding
            b.staticMethod();       // "Base static"       -> STATIC binding
            System.out.println(b.x);// 10                  -> STATIC binding
        }
    }
    ```
    - Note the trap: `fields and static methods are bound by the reference type`, so they do `not` behave polymorphically. Only overridden instance methods do.

    Comparison

    | Point | Static binding | Dynamic binding |
    |---|---|---|
    | Also called | Early binding | Late binding |
    | Decided at | Compile time | Run time |
    | Decided by | The compiler | The JVM |
    | Based on | The reference's declared type | The actual object |
    | Applies to | static, private, final, overloaded methods, fields | Overridden instance methods |
    | Speed | Faster — no lookup | Slightly slower — vtable lookup |
    | Flexibility | Less | More |
    | Polymorphism | Compile-time (overloading) | Runtime (overriding) |
    | C++ equivalent | Non-virtual functions | `virtual` functions |

    - Why dynamic binding matters: it lets code written today call methods on classes written tomorrow. In C++ this requires the `virtual` keyword; in Java every non-static, non-final method is virtual by default.

33. **Complete the following java program.** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*
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

    Answer: The program as printed is already complete and compiles. The only fault is a `formatting` one — the print statements run the label and the value together, giving `Alpha3` instead of `Alpha: 3`.

    The completed and corrected program
    ```java
    class A {
        int alpha;
        int beta;

        public A(int alpha, int beta) {
            this.alpha = alpha;              // 'this' distinguishes the field
            this.beta  = beta;               // from the parameter
        }

        public void display() {
            System.out.println("Alpha: " + alpha);
            System.out.println("Beta : " + beta);
        }
    }

    class Gamma extends A {
        int gamma;

        public Gamma(int alpha, int beta, int gamma) {
            super(alpha, beta);              // MUST be the first statement
            this.gamma = gamma;
        }

        @Override
        public void display() {
            super.display();                 // run the parent's version first
            System.out.println("Gamma: " + gamma);
        }
    }

    public class Main {
        public static void main(String[] args) {
            Gamma g = new Gamma(3, 30, 10);
            g.display();
        }
    }
    ```

    Output
    ```
       Alpha: 3
       Beta : 30
       Gamma: 10
    ```

    How it works, line by line
    ```
       1. new Gamma(3, 30, 10) calls the Gamma constructor.
       2. super(alpha, beta) immediately calls A's constructor, which sets
          alpha = 3 and beta = 30.
       3. Control returns to Gamma's constructor, which sets gamma = 10.
       4. g.display() calls the OVERRIDDEN version in Gamma.
       5. super.display() runs A's version first, printing Alpha and Beta.
       6. Gamma's own line then prints Gamma.
    ```

    Concepts the program demonstrates
    ```
       INHERITANCE          : Gamma extends A, so it inherits alpha and beta
       CONSTRUCTOR CHAINING : super(alpha, beta) passes values up to the parent
       METHOD OVERRIDING    : Gamma.display() replaces A.display()
       super KEYWORD        : super(...) calls the parent constructor;
                              super.display() calls the parent method
       this KEYWORD         : distinguishes a field from a parameter of the
                              same name
       @Override            : tells the compiler to verify the signature
    ```

    Rules worth stating in an exam
    - `super(...) must be the first statement` in a constructor. If it is omitted, Java inserts an implicit `super()` — and here that would fail to compile, because class A has no no-argument constructor.
    - Without `this.alpha = alpha;`, the assignment `alpha = alpha` would assign the parameter to itself and leave the field at 0.
    - Calling `super.display()` inside the override is what lets the subclass `add to` the parent's behaviour instead of replacing it entirely.
    - The class holding `main` is normally named `Main` with a capital letter, and Java requires a public class to live in a file of the same name.

    Demonstrating polymorphism with the same classes
    ```java
       A obj = new Gamma(3, 30, 10);    // superclass reference, subclass object
       obj.display();                    // Gamma's version runs - dynamic dispatch
    ```
    - The reference is of type `A`, so the compiler cannot know which `display()` will run; the JVM decides from the actual object.

34. **Write a C/C++ Program that has a Class Account, Subclass Savings Account, Current Account etc with related hierarchy way.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 834 (ET: N/A)]*

    Answer: A `Savings Account` and a `Current Account` are both kinds of `Account`, so the hierarchy is a natural case of inheritance. The common data and behaviour live in the base class; each subclass supplies only what differs.

    Class hierarchy
    ```
                        Account            (base class)
                       /       \
                      /         \
            SavingsAccount    CurrentAccount     (derived classes)
    ```

    ```cpp
    #include <iostream>
    #include <string>
    using namespace std;

    // ---------------- BASE CLASS ----------------
    class Account {
    protected:                       // protected -> visible to subclasses
        string accNo;
        string holder;
        double balance;

    public:
        Account(string no, string name, double opening) {
            accNo   = no;
            holder  = name;
            balance = (opening > 0) ? opening : 0;
        }

        void deposit(double amount) {
            if (amount <= 0) { cout << "Invalid amount\n"; return; }
            balance += amount;
            cout << "Deposited " << amount << endl;
        }

        virtual void withdraw(double amount) {        // VIRTUAL - overridden
            if (amount > 0 && amount <= balance) {
                balance -= amount;
                cout << "Withdrawn " << amount << endl;
            } else {
                cout << "Insufficient balance\n";
            }
        }

        virtual double calculateInterest() {          // VIRTUAL
            return 0;
        }

        virtual void display() {
            cout << "-----------------------------\n";
            cout << "Account : " << accNo  << endl;
            cout << "Holder  : " << holder << endl;
            cout << "Balance : " << balance << endl;
        }

        virtual ~Account() {}                         // virtual destructor
    };

    // ---------------- SAVINGS ACCOUNT ----------------
    class SavingsAccount : public Account {
    private:
        double rate;
        double minBalance;

    public:
        SavingsAccount(string no, string name, double opening, double r = 6.0)
            : Account(no, name, opening) {
            rate = r;
            minBalance = 500;
        }

        void withdraw(double amount) override {
            if (balance - amount < minBalance) {
                cout << "Cannot go below the minimum balance of "
                     << minBalance << endl;
            } else {
                balance -= amount;
                cout << "Withdrawn " << amount << endl;
            }
        }

        double calculateInterest() override {
            return balance * rate / 100;
        }

        void display() override {
            Account::display();                       // reuse the base version
            cout << "Type    : Savings\n";
            cout << "Interest: " << calculateInterest() << endl;
        }
    };

    // ---------------- CURRENT ACCOUNT ----------------
    class CurrentAccount : public Account {
    private:
        double overdraftLimit;

    public:
        CurrentAccount(string no, string name, double opening, double limit = 50000)
            : Account(no, name, opening) {
            overdraftLimit = limit;
        }

        void withdraw(double amount) override {
            if (amount <= balance + overdraftLimit) {
                balance -= amount;                    // overdraft allowed
                cout << "Withdrawn " << amount << endl;
                if (balance < 0)
                    cout << "Account is overdrawn by " << -balance << endl;
            } else {
                cout << "Overdraft limit exceeded\n";
            }
        }

        double calculateInterest() override {
            return 0;                                 // no interest on current
        }

        void display() override {
            Account::display();
            cout << "Type    : Current\n";
            cout << "Overdraft limit: " << overdraftLimit << endl;
        }
    };

    // ---------------- MAIN ----------------
    int main() {
        Account* accounts[2];
        accounts[0] = new SavingsAccount("SB1001", "Rahim Uddin", 10000);
        accounts[1] = new CurrentAccount("CA2001", "Karim Traders", 20000);

        for (int i = 0; i < 2; i++) {
            accounts[i]->deposit(5000);
            accounts[i]->withdraw(30000);
            accounts[i]->display();
        }

        for (int i = 0; i < 2; i++) delete accounts[i];
        return 0;
    }
    ```

    Output
    ```
       Deposited 5000
       Cannot go below the minimum balance of 500
       -----------------------------
       Account : SB1001
       Holder  : Rahim Uddin
       Balance : 15000
       Type    : Savings
       Interest: 900

       Deposited 5000
       Withdrawn 30000
       Account is overdrawn by 5000
       -----------------------------
       Account : CA2001
       Holder  : Karim Traders
       Balance : -5000
       Type    : Current
       Overdraft limit: 50000
    ```

    Concepts the program demonstrates
    ```
       INHERITANCE   : SavingsAccount and CurrentAccount extend Account,
                       inheriting accNo, holder, balance and deposit()

       POLYMORPHISM  : withdraw(), calculateInterest() and display() are
                       virtual, so the loop over Account* calls each object's
                       own version - runtime polymorphism

       ENCAPSULATION : balance is protected, rate and overdraftLimit are
                       private; all access goes through validating methods

       ABSTRACTION   : main() works only with Account*, and knows nothing
                       about how each type calculates interest

       CODE REUSE    : deposit() is written once; display() in each subclass
                       calls Account::display() rather than repeating it
    ```

    Points worth stating
    - The base methods are declared `virtual`, without which `accounts[i]->withdraw()` would always call the `Account` version — the classic C++ mistake.
    - The destructor is also `virtual`, so `delete` through a base pointer destroys the derived part as well.
    - Adding a new account type — `FixedDepositAccount`, say — needs only a new class; `main()` does not change at all. This is the `open-closed principle`.

35. **Write the definition of Inheritance, Polymorphism with coding example.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 835 (ET: N/A)]*

    Answer: Inheritance
    - `Inheritance` is the mechanism by which one class acquires the fields and methods of another. The existing class is the `superclass` (parent) and the new one the `subclass` (child).
    - It expresses an `is-a` relationship and gives `code reuse`.
    ```java
    class Employee {                          // superclass
        protected String name;
        protected double basic;

        Employee(String name, double basic) {
            this.name  = name;
            this.basic = basic;
        }

        double calculateSalary() { return basic; }

        void display() {
            System.out.println(name + " earns " + calculateSalary());
        }
    }

    class Manager extends Employee {          // Manager IS-A Employee
        Manager(String name, double basic) { super(name, basic); }

        @Override
        double calculateSalary() { return basic + 0.40 * basic; }
    }

    class Officer extends Employee {
        Officer(String name, double basic) { super(name, basic); }

        @Override
        double calculateSalary() { return basic + 0.20 * basic; }
    }
    ```
    - `name`, `basic` and `display()` are written once in `Employee` and used by both subclasses.
    ```
       Types : single , multilevel , hierarchical ,
               multiple (through interfaces in Java) , hybrid
    ```

    Polymorphism
    - `Polymorphism` means "many forms": the same method name behaves differently depending on the object or the arguments.
    ```
       Compile-time (static)  : method OVERLOADING - the compiler decides
       Runtime (dynamic)      : method OVERRIDING  - the JVM decides
    ```

    Compile-time example — overloading
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }
    ```

    Runtime example — overriding, using the classes above
    ```java
    public class Main {
        public static void main(String[] args) {

            Employee[] staff = {                    // superclass references
                new Manager("Rahim", 50000),
                new Officer("Karim", 50000),
                new Employee("Jamal", 50000)
            };

            for (Employee e : staff)
                e.display();          // each object runs ITS OWN calculateSalary()
        }
    }
    ```
    Output
    ```
       Rahim earns 70000.0
       Karim earns 60000.0
       Jamal earns 50000.0
    ```

    Why the two are always taught together
    - The array is declared as `Employee[]`, which is legal only `because` Manager and Officer inherit from Employee. Inheritance creates the `is-a` relationship, and polymorphism then exploits it: the compiler cannot know which `calculateSalary()` will run, so the JVM decides from the actual object — `dynamic method dispatch`.
    - `display()` is not overridden at all, yet it prints the right salary for every subclass, because the method it calls is resolved polymorphically.

    | Point | Inheritance | Polymorphism |
    |---|---|---|
    | Meaning | A class acquires another's members | One name, many behaviours |
    | Purpose | Code reuse and hierarchy | Flexibility and extensibility |
    | Keyword | `extends`, `implements` | `@Override`, or `virtual` in C++ |
    | Relationship | Is-a | — |
    | Decided | At design time | At compile time or run time |
    | Depends on the other | No | `Yes` — runtime polymorphism needs inheritance |

    - The practical payoff: adding a `Director` subclass needs no change at all to the loop in `main`. This is the `open-closed principle` — open for extension, closed for modification.

36. **Explain method overloading and Method overriding with example.** *[RAKUB Programmer (PO) 12.10.2021 compact it 850-851 (ET: N/A)]*

    Answer: Both are forms of polymorphism, but they occur in different places and are resolved at different times.

    Method overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` picks the right one from the arguments supplied.
    ```
       Distinguished by : different NUMBER of parameters
                          different TYPES of parameters
                          different ORDER of parameter types

       NOT by return type alone.
    ```
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
        String add(String a, String b)    { return a + b; }
    }

    public class Main {
        public static void main(String[] args) {
            Calculator c = new Calculator();
            System.out.println(c.add(5, 3));             // 8
            System.out.println(c.add(5.5, 3.2));         // 8.7
            System.out.println(c.add(1, 2, 3));          // 6
            System.out.println(c.add("Bangla","desh"));  // Bangladesh
        }
    }
    ```
    - Called `compile-time`, `static` or `early` binding. No inheritance is needed, and there is no runtime cost.
    - `Constructor overloading` is the same idea applied to constructors, which is why an object can be created in several ways.

    Method overriding
    - A `subclass` supplies its own version of a method inherited from its superclass, with `exactly the same signature`. The `JVM` decides at run time which body to run.
    ```java
    class Employee {
        double calculateSalary(double basic) { return basic; }
        void display(double basic) {
            System.out.println("Salary: " + calculateSalary(basic));
        }
    }

    class Manager extends Employee {
        @Override
        double calculateSalary(double basic) { return basic + 0.40 * basic; }
    }

    class Officer extends Employee {
        @Override
        double calculateSalary(double basic) { return basic + 0.20 * basic; }
    }

    public class Main {
        public static void main(String[] args) {
            Employee[] staff = { new Manager(), new Officer(), new Employee() };
            for (Employee e : staff) e.display(50000);
        }
    }
    ```
    Output
    ```
       Salary: 70000.0
       Salary: 60000.0
       Salary: 50000.0
    ```
    - Called `runtime`, `dynamic` or `late` binding. Inheritance is required.
    - Note that `display()` is not overridden, yet it produces the right figure for every subclass, because the `calculateSalary()` it calls is resolved polymorphically.

    Comparison

    | Point | Method overloading | Method overriding |
    |---|---|---|
    | Where | Same class | Superclass and subclass |
    | Parameter list | Must `differ` | Must be `identical` |
    | Return type | May differ | Same or covariant |
    | Inheritance | Not needed | `Required` |
    | Resolved | Compile time | Run time |
    | Also called | Static / early binding | Dynamic / late binding |
    | Access modifier | Any | Cannot be more restrictive |
    | `static` methods | Can be overloaded | Cannot be overridden (only hidden) |
    | `private` / `final` | Can be overloaded | Cannot be overridden |
    | Constructors | Can be overloaded | Cannot be overridden |
    | C++ requirement | None | `virtual` in the base class |
    | Number of classes | 1 | 2 or more |
    | Purpose | Convenience — one name for related operations | Specialisation — change inherited behaviour |

    - Memory aid: `overloading changes the parameters; overriding changes the body`.

37. **OOP problem (Inheritance related) [হুবহু প্রশ্ন সংগ্রহ করা সম্ভব হয়নি]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

38. **Object Oriented Programming (OOP) language -এর প্রধান বৈশিষ্ট্য গুলো কী কী? দুটি OOP language -এর নাম লিখুন।** *[41th BCS 2021 compact it 881 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The main features of an object-oriented programming language are the four pillars, together with the class and object mechanism they rest on.

    1. Class and Object
    ```
       CLASS  : a blueprint defining attributes and methods
       OBJECT : an instance of that class, occupying real memory
    ```
    ```java
    class Student {
        String name;  int roll;          // attributes
        void display() { ... }           // method
    }
    Student s1 = new Student();          // object
    ```

    2. Encapsulation
    - Binding data and methods into one unit and `hiding` the internal state behind private fields with public accessors.
    ```java
    class Account {
        private double balance;
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```
    - Gives `data security`: the object cannot be put into an invalid state from outside.

    3. Abstraction
    - Showing only the `essential features` and hiding the implementation.
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - The caller learns `what` a class does, not `how`.

    4. Inheritance
    - A new class acquires the members of an existing one, an `is-a` relationship.
    ```java
    class Dog extends Animal { void bark() { ... } }
    ```
    - Gives `code reuse` and a natural hierarchy.

    5. Polymorphism
    - One method name behaving differently by context.
    ```
       Compile-time : method OVERLOADING
       Runtime      : method OVERRIDING
    ```
    - Gives `flexibility`: one interface serves many implementations.

    6. Message passing
    - Objects cooperate by calling each other's methods.

    7. Dynamic binding
    - The method body is chosen at `run time` from the actual object — the mechanism behind runtime polymorphism.

    Two OOP languages
    ```
       1. Java  - almost purely object-oriented (apart from its primitive
                  types), platform independent through the JVM, with automatic
                  garbage collection. Used for enterprise systems, Android
                  applications and banking software.

       2. C++   - multi-paradigm; it adds classes to C and also supports
                  procedural style. It offers operator overloading and
                  multiple inheritance, which Java deliberately omits, and
                  gives direct control of memory. Used for system software,
                  game engines and performance-critical applications.
    ```
    - Others worth naming: `C#`, `Python`, `Ruby`, `Kotlin`, `Swift`, `PHP` and `Smalltalk`, in which the term "object-oriented" was first used.

39. **(b) What is function overloading and operator overloading. Give example.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892 (ET: N/A)]*

    Answer: Function overloading
    - Defining two or more functions with the `same name` in the same scope, distinguished by their `parameter lists`. The compiler chooses which to call from the arguments supplied.
    ```
       Distinguished by : different NUMBER, TYPE or ORDER of parameters
       NOT by return type alone
    ```
    ```cpp
    #include <iostream>
    using namespace std;

    class Calculator {
    public:
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
        string add(string a, string b)    { return a + b; }
    };

    int main() {
        Calculator c;
        cout << c.add(5, 3)            << endl;   // 8          -> int version
        cout << c.add(5.5, 3.2)        << endl;   // 8.7        -> double version
        cout << c.add(1, 2, 3)         << endl;   // 6          -> three arguments
        cout << c.add("Bangla","desh") << endl;   // Bangladesh -> string version
        return 0;
    }
    ```
    - It is `compile-time polymorphism`, so it costs nothing at run time.
    - Purpose: one meaningful name for a family of related operations, instead of `addInt`, `addDouble` and `addThree`.

    Operator overloading
    - Giving an `existing operator` a new meaning for a user-defined type, so that objects can be combined with the familiar symbols.
    ```cpp
    #include <iostream>
    using namespace std;

    class Complex {
    private:
        int real, imag;

    public:
        Complex(int r = 0, int i = 0) { real = r; imag = i; }

        Complex operator+(const Complex& c) {        // + overloaded
            return Complex(real + c.real, imag + c.imag);
        }

        Complex operator-(const Complex& c) {        // - overloaded
            return Complex(real - c.real, imag - c.imag);
        }

        bool operator==(const Complex& c) {          // == overloaded
            return (real == c.real && imag == c.imag);
        }

        void display() { cout << real << " + " << imag << "i" << endl; }
    };

    int main() {
        Complex a(3, 4), b(1, 2);

        Complex sum  = a + b;        // calls a.operator+(b)
        Complex diff = a - b;

        sum.display();               // 4 + 6i
        diff.display();              // 2 + 2i

        cout << (a == b) << endl;    // 0 (false)
        return 0;
    }
    ```
    - Without it the code would read `a.add(b)`, which is far less natural for a mathematical type.

    Another example — overloading `<<` for output
    ```cpp
       friend ostream& operator<<(ostream& out, const Complex& c) {
           out << c.real << " + " << c.imag << "i";
           return out;
       }

       cout << sum;                 // now works directly
    ```

    Rules for operator overloading in C++
    ```
       At least one operand must be a USER-DEFINED type - the meaning of
           5 + 3 for built-in types cannot be changed

       These operators CANNOT be overloaded :
           .    .*    ::    ?:    sizeof    typeid

       The number of operands, the precedence and the associativity CANNOT
           be changed

       These must be MEMBER functions : =  [ ]  ( )  ->
       These are usually FRIEND functions : <<  >>
    ```

    Comparison

    | Point | Function overloading | Operator overloading |
    |---|---|---|
    | What is overloaded | A function name | An operator symbol |
    | Distinguished by | The parameter list | The operand types |
    | Available in Java | `Yes` | `No` (except the built-in `+` for String) |
    | Available in C++ | Yes | Yes |
    | Purpose | One name for related operations | Natural syntax for user-defined types |
    | Binding | Compile time | Compile time |

    - Both are `compile-time polymorphism`. Java deliberately omits operator overloading, on the grounds that it is frequently misused and makes code harder to read.

40. **১. সাব-ক্লাস এর অপর নাম কি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `subclass` is also called a
    ```
       Derived class
       Child class
       Extended class
       Sub type
    ```
    - The most common alternatives are `derived class` (the usual C++ term) and `child class`.

    The class it inherits from has its own set of names
    ```
       Superclass  =  Parent class  =  Base class  =  Super type
    ```

    Summary

    | Inherits from | Inherits to |
    |---|---|
    | Superclass | Subclass |
    | Parent class | Child class |
    | Base class | Derived class |

    Which term each language prefers
    ```
       Java , C#   : superclass and subclass
       C++         : base class and derived class
       Python      : parent class and child class
    ```

    Example
    ```java
    class Animal { }                  // superclass / parent / base
    class Dog extends Animal { }      // subclass / child / derived
    ```
    ```cpp
    class Animal { };                 // base class
    class Dog : public Animal { };    // derived class
    ```

    - The relationship between them is `is-a`: a `Dog is an Animal`. The subclass inherits everything accessible from the superclass and may add new members of its own or `override` inherited methods to specialise them.
    - In Java a subclass reaches its parent through the `super` keyword — `super()` calls the parent's constructor and `super.method()` its version of a method.

41. **৮. অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং এর বৈশিষ্ট্য লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The characteristics of object-oriented programming are the four pillars, together with the mechanisms that support them.

    1. Encapsulation
    - Binding data and the methods that operate on it into one unit, and `hiding` the internal state behind private fields with public accessors.
    ```java
    class Account {
        private double balance;                   // hidden
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```
    - Effect: the object cannot be put into an invalid state from outside.

    2. Abstraction
    - Showing only the `essential features` and hiding the implementation.
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - Effect: the caller works with `what` a class does, not `how`.

    3. Inheritance
    - A new class acquires the members of an existing one — an `is-a` relationship.
    ```java
    class Dog extends Animal { void bark() { ... } }
    ```
    - Effect: `code reuse` and a natural hierarchy.

    4. Polymorphism
    - One method name behaving differently by context.
    ```
       Compile-time : method OVERLOADING
       Runtime      : method OVERRIDING
    ```
    - Effect: one interface serves many implementations.

    5. Class and Object
    ```
       CLASS  : the blueprint
       OBJECT : an instance of it, occupying real memory
    ```

    6. Message passing
    - Objects cooperate by `calling each other's methods` and passing data as arguments.

    7. Dynamic binding
    - The method body is chosen at `run time` from the actual object — the mechanism behind runtime polymorphism.

    8. Constructor and destructor
    - Automatic initialisation when an object is created and cleanup when it is destroyed, so an object is never used uninitialised.

    9. Access modifiers
    ```
       private , protected , public , default
    ```
    - The tool by which encapsulation is actually enforced.

    Benefits these characteristics produce
    ```
       Reusability      : inheritance and composition
       Maintainability  : a change stays inside one class
       Modularity       : each class is self-contained
       Data security    : private state, validated access
       Extensibility    : add a class rather than edit existing ones
       Real-world model : objects match real entities
       Team development : parallel work on separate classes
    ```

    - Languages built on them: `Java, C++, C#, Python, Kotlin, Swift, Ruby`.

42. **Inheritance is one of important issues for any object oriented programming language. The main advantage of Inheritance is the ability to reuse the code. Explain in brief different types of Inheritance.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 981 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The main types of inheritance are the following. In each, the arrow points from the superclass to the subclass.

    1. Single inheritance
    ```
            A
            |
            B          one subclass, one superclass
    ```
    ```java
    class Animal { void eat() { ... } }
    class Dog extends Animal { void bark() { ... } }
    ```
    - The simplest and most common form. `Dog` reuses everything in `Animal`.

    2. Multilevel inheritance
    ```
            A
            |
            B          B inherits from A
            |
            C          C inherits from B, and therefore from A too
    ```
    ```java
    class Animal { void eat()  { ... } }
    class Dog extends Animal { void bark() { ... } }
    class Puppy extends Dog   { void weep() { ... } }
    ```
    - `Puppy` can use `eat()`, `bark()` and `weep()`. Reuse accumulates down the chain, but a deep chain becomes fragile.

    3. Hierarchical inheritance
    ```
              A
             / \
            B   C      several subclasses share one superclass
    ```
    ```java
    class Vehicle { void start() { ... } }
    class Car extends Vehicle { }
    class Bike extends Vehicle { }
    class Truck extends Vehicle { }
    ```
    - Maximum reuse of one common base — `start()` is written once for every vehicle type.

    4. Multiple inheritance
    ```
          A   B
           \ /
            C          one subclass, TWO superclasses
    ```
    - Supported in C++ and Python. `Not supported through classes in Java`, because of the `diamond problem`: if A and B share a common base, C receives two copies of it and any reference is ambiguous. C++ solves this with `virtual` base classes.
    - Java achieves it safely through `interfaces`:
    ```java
    interface Printable { void print(); }
    interface Showable  { void show(); }
    class Document implements Printable, Showable {
        public void print() { ... }
        public void show()  { ... }
    }
    ```

    5. Hybrid inheritance
    ```
            A
           / \
          B   C        hierarchical
           \ /
            D          multiple  -> HYBRID
    ```
    - Any combination of the above. It needs at least four classes, and it is where the diamond problem appears.

    Comparison

    | Type | Superclasses | Subclasses | Java support |
    |---|---|---|---|
    | Single | 1 | 1 | Yes |
    | Multilevel | 1 per level | Chain | Yes |
    | Hierarchical | 1 | Many | Yes |
    | Multiple | Many | 1 | Only via interfaces |
    | Hybrid | Combination | Combination | Only via interfaces |

    The main advantage — code reuse, and what follows from it
    - `Write once, use many times.` A method in the superclass serves every subclass, so the same logic is never repeated.
    - `Fix once, fixed everywhere.` A bug corrected in the superclass is corrected for every subclass at the same moment.
    - `Less code to test.` Only the differences in each subclass need new tests.
    - `Enables polymorphism`, which is inheritance's most valuable consequence: because `Dog is-a Animal`, one array of `Animal` can hold every kind and one loop can treat them all.
    - `Extensibility.` A new subclass requires no change to existing code — the `open-closed principle`.

    Cautions worth stating
    ```
       Inheritance creates TIGHT COUPLING : a change in the superclass can
            break every subclass. Deep hierarchies are fragile.
       Use it only for a genuine IS-A relationship. A Stack is not a
            Vector, even though it can be built from one.
       Modern advice : "prefer COMPOSITION over inheritance" - hold an object
            as a field rather than inheriting from its class, whenever the
            relationship is really HAS-A rather than IS-A.
    ```

43. **Object Oriented Programming এর চারটি গুরুত্বপূর্ণ বৈশিষ্ট্য লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1020-1021 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The four important characteristics of OOP are the following.

    1. Encapsulation
    - Binding the `data` and the `methods` that operate on it into a single unit — the class — and `hiding` the internal state behind private fields with public accessor methods.
    ```java
    class Account {
        private double balance;                    // hidden from outside

        public void deposit(double amt) {
            if (amt > 0) balance += amt;           // access is validated
        }
        public double getBalance() { return balance; }
    }
    ```
    - Benefit: `data security`. The object cannot be put into an invalid state from outside, and the internal representation can be changed later without breaking any caller.

    2. Abstraction
    - Showing only the `essential features` and hiding the implementation, so the user knows `what` a class does but not `how` it does it.
    ```java
    abstract class Shape {
        abstract double area();          // WHAT, without the HOW
    }
    class Circle extends Shape {
        double r;
        @Override double area() { return 3.1416 * r * r; }
    }
    ```
    - Achieved with `abstract classes` and `interfaces`. Benefit: it reduces complexity and defines a `contract` that every subclass must honour.

    3. Inheritance
    - A new class acquires the fields and methods of an existing one, expressing an `is-a` relationship.
    ```java
    class Animal { void eat() { System.out.println("eats food"); } }
    class Dog extends Animal { void bark() { System.out.println("barks"); } }
    ```
    ```
       Types : single , multilevel , hierarchical ,
               multiple (through interfaces in Java) , hybrid
    ```
    - Benefit: `code reuse`, a natural hierarchy, and it is what makes runtime polymorphism possible.

    4. Polymorphism
    - One method name behaving differently depending on the object or the arguments given.
    ```java
    // compile-time : overloading
    int add(int a, int b);           double add(double a, double b);

    // runtime : overriding
    Animal a = new Dog();
    a.sound();                       // the Dog version runs
    ```
    - Benefit: one interface serves many implementations, so a new subclass can be added without changing existing code — the `open-closed principle`.

    How they fit together
    ```
       ENCAPSULATION protects an object's data
       ABSTRACTION   hides its implementation
       INHERITANCE   shares its behaviour with related classes
       POLYMORPHISM  lets those related classes be used interchangeably
    ```

    - Two supporting concepts often added: `message passing` (objects communicate by calling each other's methods) and `dynamic binding` (the method body is chosen at run time from the actual object).

44. **What are the difference between Structure Programming and Objest Oriented Progrmamming?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*

    Answer: `Structured (procedural) programming` organises a program around `functions` acting on separately held data. `Object-oriented programming` organises it around `objects` that hold data and behaviour together.

    Structured programming
    - The program is a set of `functions`, designed `top-down`: the problem is split into tasks, each becoming a function.
    - Data is largely `global`, so any function can read or change it.
    - Reuse means calling or copying a function.
    ```c
    struct Student { char name[50]; int roll; };   /* data */

    void display(struct Student s) {               /* separate function */
        printf("%s %d", s.name, s.roll);
    }
    ```
    - Languages: `C, Pascal, FORTRAN, COBOL`.

    Object-oriented programming
    - The program is a set of `objects`, designed `bottom-up`: the entities are identified first, then their behaviour.
    - Data is `private` inside the object, reachable only through its methods.
    - Reuse comes from `inheritance` and composition.
    ```java
    class Student {
        private String name;  private int roll;    // data AND
        public void display() {                    // behaviour together
            System.out.println(name + " " + roll);
        }
    }
    ```
    - Languages: `Java, C++, C#, Python`.

    Difference

    | Point | Structured programming | Object-oriented programming |
    |---|---|---|
    | Organised around | Functions and procedures | Objects |
    | Data and functions | Kept separate | Bound together |
    | Data access | Global, open to all functions | Private, controlled by methods |
    | Approach | Top-down | Bottom-up |
    | Data security | Weak | Strong, through encapsulation |
    | Program divided into | Functions | Classes and objects |
    | Reuse | Copy or call functions | Inheritance and composition |
    | Inheritance | Not supported | Supported |
    | Polymorphism | Not supported | Supported |
    | Overloading | Not supported | Supported |
    | Abstraction | Limited | Through abstract classes and interfaces |
    | Extending | Often requires editing existing code | Add a new class |
    | Maintenance | Harder as size grows | Easier — changes are localised |
    | Debugging | Harder — any function may have altered the data | Easier — errors are localised |
    | Real-world modelling | Weak | Strong |
    | Suited to | Small and medium programs | Large, evolving systems |
    | Examples | C, Pascal, FORTRAN | Java, C++, C#, Python |

    The essential distinction
    ```
       Structured : "What should the program DO?"  -> functions first
       Object-oriented : "What things EXIST in the problem?" -> objects first
    ```

    Where structured programming is still preferable
    ```
       Small scripts and utilities - classes would be over-engineering
       Embedded systems with very tight memory
       Numerical and signal-processing code
       Performance-critical loops, where indirection costs measurable time
    ```
    - So OOP is not universally better. It is better for `large, long-lived programs that must be extended and maintained`, which is most business and government software.

45. **Object Oriented Programming এ Method Overloading and Method Overriding এর মধ্যে পার্থক্য কী?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Both are forms of polymorphism, but they occur in different places and are resolved at different times.

    Method overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` chooses which to call.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }
    ```
    - No inheritance is needed. It is `compile-time (static, early) binding`, so there is no runtime cost.
    - Return type alone cannot distinguish two overloads.

    Method overriding
    - A `subclass` supplies its own version of a method inherited from its superclass, with `exactly the same signature`. The `JVM` decides at run time which body to run.
    ```java
    class Animal {
        void sound() { System.out.println("Some sound"); }
    }
    class Dog extends Animal {
        @Override void sound() { System.out.println("Bhow Bhow"); }
    }

    Animal a = new Dog();
    a.sound();          // "Bhow Bhow" - decided at RUN TIME
    ```
    - Inheritance is required. It is `runtime (dynamic, late) binding`.

    Difference

    | Point | Method overloading | Method overriding |
    |---|---|---|
    | Where it occurs | Within the `same class` | Between `superclass and subclass` |
    | Parameter list | Must `differ` | Must be `identical` |
    | Return type | May differ | Same or covariant |
    | Inheritance | Not required | `Required` |
    | Binding | Static, at compile time | Dynamic, at run time |
    | Also called | Early binding | Late binding |
    | Access modifier | Any | Cannot be made more restrictive |
    | `static` methods | Can be overloaded | Cannot be overridden (only hidden) |
    | `private` methods | Can be overloaded | Cannot be overridden |
    | `final` methods | Can be overloaded | Cannot be overridden |
    | Constructors | Can be overloaded | Cannot be overridden |
    | Number of classes | 1 | 2 or more |
    | Exception rules | Any exception may be declared | Cannot declare a broader checked exception |
    | Performance | Slightly faster | A small runtime lookup |
    | Purpose | Convenience — one name for related operations | Specialisation — change inherited behaviour |

    A worked contrast showing both in one program
    ```java
    class Base {
        void show(int a)     { System.out.println("Base int"); }
        void show(String s)  { System.out.println("Base String"); }   // OVERLOAD
    }
    class Derived extends Base {
        @Override
        void show(int a)     { System.out.println("Derived int"); }   // OVERRIDE
    }

    public class Main {
        public static void main(String[] args) {
            Base b = new Derived();
            b.show(5);          // "Derived int"  -> overriding, resolved at run time
            b.show("hi");       // "Base String"  -> overloading, resolved at compile time
        }
    }
    ```

    - Memory aid: `overloading changes the parameters; overriding changes the body`.

46. **Inheritance, Polymorphism and Encapsulation ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1078 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Inheritance
    - `Inheritance` is the mechanism by which one class acquires the fields and methods of another. The existing class is the `superclass` and the new one the `subclass`, and the relationship is `is-a`.
    ```java
    class Animal {
        protected String name;
        void eat()   { System.out.println(name + " eats food"); }
        void sleep() { System.out.println(name + " sleeps"); }
    }

    class Dog extends Animal {
        void bark() { System.out.println(name + " barks"); }
    }
    ```
    ```
       Types : single , multilevel , hierarchical ,
               multiple (through interfaces in Java) , hybrid
    ```
    - Purpose: `code reuse` and a natural hierarchy. `eat()` and `sleep()` are written once and used by every subclass.
    - Keywords: `extends`, `implements`, `super`, `@Override`, `protected`, `final`.
    - Caution: it creates `tight coupling`, so a change in the superclass can break every subclass. Use it only for a genuine is-a relationship.

    Polymorphism
    - `Polymorphism` means "many forms": the same method name behaves differently depending on the object or the arguments.
    ```
       Compile-time (static)  : method OVERLOADING - the compiler decides
       Runtime (dynamic)      : method OVERRIDING  - the JVM decides
    ```
    ```java
    // overloading
    class Calculator {
        int    add(int a, int b)       { return a + b; }
        double add(double a, double b) { return a + b; }
    }

    // overriding
    class Dog extends Animal {
        @Override void sound() { System.out.println("Bhow Bhow"); }
    }
    class Cat extends Animal {
        @Override void sound() { System.out.println("Meow"); }
    }

    Animal a;
    a = new Dog();  a.sound();        // Bhow Bhow
    a = new Cat();  a.sound();        // Meow
    ```
    - In the second case the reference type is `Animal`, so the compiler cannot decide; the JVM inspects the real object — `dynamic method dispatch`.
    - Purpose: one interface serves many implementations, so new subclasses can be added without changing existing code.

    Encapsulation
    - `Encapsulation` binds the data and the methods that act on it into one unit and `hides` the internal state behind private fields with public accessors.
    ```java
    class Account {
        private double balance;                     // hidden

        public void deposit(double amt) {
            if (amt > 0) balance += amt;            // validated
        }
        public void withdraw(double amt) {
            if (amt > 0 && amt <= balance) balance -= amt;
        }
        public double getBalance() { return balance; }
    }
    ```
    - Purpose: `data security`. Without it, `acc.balance = -50000;` would be legal and would corrupt the account.
    - It also lets the internal representation change — storing paisa as an integer, say — without breaking any caller.
    - Enforced by the `access modifiers`: `private`, `protected`, `public` and default.

    How the three relate
    ```
       ENCAPSULATION protects an object's data
       INHERITANCE   shares an object's behaviour with related classes
       POLYMORPHISM  lets those related classes be used interchangeably
    ```
    - Runtime polymorphism `depends on` inheritance, which is why the two are always taught together. Encapsulation is independent of both and applies to every class.
    - The fourth pillar, not asked here, is `abstraction` — showing only the essential features and hiding the implementation.

47. **Function overloading and Operator overloading বলতে কী বুঝেন? উদাহরণ দিন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1082 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Function overloading
    - Defining two or more functions with the `same name` in the same scope, distinguished by their `parameter lists`. The compiler chooses which to call from the arguments given.
    ```
       Distinguished by : different NUMBER, TYPE or ORDER of parameters
       NOT by return type alone
    ```
    ```cpp
    #include <iostream>
    using namespace std;

    class Calculator {
    public:
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
        string add(string a, string b)    { return a + b; }
    };

    int main() {
        Calculator c;
        cout << c.add(5, 3)            << endl;   // 8
        cout << c.add(5.5, 3.2)        << endl;   // 8.7
        cout << c.add(1, 2, 3)         << endl;   // 6
        cout << c.add("Bangla","desh") << endl;   // Bangladesh
    }
    ```
    - It is `compile-time polymorphism`, so it costs nothing at run time.
    - Purpose: one meaningful name for a family of related operations, instead of `addInt`, `addDouble` and `addThree`.

    Operator overloading
    - Giving an `existing operator` a new meaning for a user-defined type, so objects can be combined with familiar symbols.
    ```cpp
    #include <iostream>
    using namespace std;

    class Complex {
    private:
        int real, imag;

    public:
        Complex(int r = 0, int i = 0) { real = r; imag = i; }

        Complex operator+(const Complex& c) {           // + overloaded
            return Complex(real + c.real, imag + c.imag);
        }
        Complex operator*(const Complex& c) {           // * overloaded
            return Complex(real*c.real - imag*c.imag,
                           real*c.imag + imag*c.real);
        }
        void display() { cout << real << " + " << imag << "i" << endl; }
    };

    int main() {
        Complex a(3, 4), b(1, 2);

        Complex sum  = a + b;        // calls a.operator+(b)
        Complex prod = a * b;

        sum.display();               // 4 + 6i
        prod.display();              // -5 + 10i
        return 0;
    }
    ```
    - Without it the code would read `a.add(b)`, which is far less natural for a mathematical type.

    Rules for operator overloading in C++
    ```
       At least one operand must be a USER-DEFINED type

       CANNOT be overloaded :  .   .*   ::   ?:   sizeof   typeid

       The number of operands, the precedence and the associativity
           CANNOT be changed

       Must be MEMBER functions : =  [ ]  ( )  ->
       Usually FRIEND functions : <<  >>
    ```

    Comparison

    | Point | Function overloading | Operator overloading |
    |---|---|---|
    | What is overloaded | A function name | An operator symbol |
    | Distinguished by | The parameter list | The operand types |
    | Purpose | One name for related operations | Natural syntax for user-defined types |
    | In C++ | Supported | Supported |
    | In Java | `Supported` | `Not supported` (except the built-in `+` for String) |
    | Binding | Compile time | Compile time |

    - Both are `compile-time (static) polymorphism`. Java deliberately omits operator overloading, on the grounds that it is easily misused and can make code harder to read — `a + b` giving a surprising result is far worse than `a.add(b)` being verbose.

48. **(a) What is method overloading?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

    Answer: `Method overloading` means defining two or more methods with the `same name` in the same class, distinguished by their `parameter lists`. The compiler chooses which one to call from the arguments supplied.

    - It is a form of `compile-time (static) polymorphism`, also called `early binding`.

    How the compiler distinguishes them
    ```
       1. Different NUMBER of parameters
       2. Different TYPES of parameters
       3. Different ORDER of parameter types

       NOT sufficient : a different RETURN TYPE alone, because the return
                        value may be discarded, leaving the compiler no
                        basis on which to choose.
    ```

    Example
    ```java
    class Calculator {

        int add(int a, int b) {                  // 1. two ints
            return a + b;
        }
        double add(double a, double b) {         // 2. two doubles
            return a + b;
        }
        int add(int a, int b, int c) {           // 3. three ints
            return a + b + c;
        }
        String add(String a, String b) {         // 4. two strings
            return a + b;
        }
        void add(int a, String b) { }            // 5. different ORDER
        void add(String a, int b) { }            //    of the same types
    }

    public class Main {
        public static void main(String[] args) {
            Calculator c = new Calculator();
            System.out.println(c.add(5, 3));             // 8    -> version 1
            System.out.println(c.add(5.5, 3.2));         // 8.7  -> version 2
            System.out.println(c.add(1, 2, 3));          // 6    -> version 3
            System.out.println(c.add("Bangla","desh"));  // Bangladesh -> 4
        }
    }
    ```

    Constructor overloading — the same idea applied to constructors
    ```java
    class Student {
        String name;  int roll;

        Student()                { name = "Unknown"; roll = 0; }
        Student(String n)        { name = n; roll = 0; }
        Student(String n, int r) { name = n; roll = r; }
    }
    ```
    - This is why an object can be created in several different ways.

    What is NOT valid overloading
    ```java
       int  f(int a) { ... }
       void f(int a) { ... }        // ERROR - differs only by return type
    ```

    Type promotion
    ```java
       void show(long a) { ... }
       show(5);            // an int argument is PROMOTED to long
    ```
    - If no exact match exists, Java widens the argument automatically: `byte -> short -> int -> long -> float -> double`. An exact match is always preferred over a promotion.

    Advantages
    ```
       One meaningful name instead of addInt, addDouble, addThree
       Easier to read, remember and use
       A consistent interface for related operations
       Resolved at COMPILE TIME, so there is no runtime cost
    ```

    - Difference from `method overriding`: overloading occurs in the `same class` with `different parameters` and is resolved by the compiler; overriding occurs between a `superclass and a subclass` with an `identical signature` and is resolved at run time by the JVM.

49. **(b) Explain Polymorphism concept of OOP language.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1140 (ET: N/A)]*

    Answer: `Polymorphism` means "many forms". The same method name behaves differently depending on the object it is called on or the arguments it is given, so `one interface serves many implementations`.

    - It is one of the four pillars of OOP, with encapsulation, inheritance and abstraction.

    Two types
    ```
       Compile-time (static, early binding)   -> method OVERLOADING
                                                 operator overloading (C++)
       Runtime (dynamic, late binding)        -> method OVERRIDING
    ```

    Compile-time polymorphism — overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` chooses by matching the arguments.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }

    Calculator c = new Calculator();
    c.add(5, 3);        // 8    -> int version
    c.add(5.5, 3.2);    // 8.7  -> double version
    c.add(1, 2, 3);     // 6    -> three-argument version
    ```
    - No inheritance is needed, and nothing is decided at run time, so it costs nothing.

    Runtime polymorphism — overriding
    - A `subclass` supplies its own version of an inherited method, with the same signature. The `JVM` decides at run time from the `actual object`, not the reference type.
    ```java
    class Shape {
        double area() { return 0; }
        void display() { System.out.println("Area = " + area()); }
    }
    class Circle extends Shape {
        double r;
        Circle(double r) { this.r = r; }
        @Override double area() { return 3.1416 * r * r; }
    }
    class Rectangle extends Shape {
        double l, w;
        Rectangle(double l, double w) { this.l = l; this.w = w; }
        @Override double area() { return l * w; }
    }

    public class Main {
        public static void main(String[] args) {
            Shape[] shapes = { new Circle(5), new Rectangle(4, 6) };
            for (Shape s : shapes) s.display();
        }
    }
    ```
    Output
    ```
       Area = 78.54
       Area = 24.0
    ```
    - The array holds `Shape` references, so the compiler cannot know which `area()` will run — the JVM decides. This is `dynamic method dispatch`.
    - Note that `display()` is not overridden at all, yet it prints the right value for every subclass, because the `area()` it calls is resolved polymorphically. This is where the real power lies.

    Comparison

    | Point | Compile-time | Runtime |
    |---|---|---|
    | Achieved by | Overloading | Overriding |
    | Decided by | The compiler | The JVM |
    | Based on | The argument list | The actual object |
    | Inheritance | Not needed | Required |
    | Parameters | Must differ | Must be identical |
    | Binding | Early / static | Late / dynamic |
    | Speed | Faster | Slightly slower |
    | C++ requirement | None | `virtual` in the base class |

    Java-specific points
    ```
       Every non-static, non-final method is VIRTUAL by default, so no
            'virtual' keyword is needed as in C++
       @Override is optional but recommended - the compiler then catches
            a mistyped signature
       static, private and final methods CANNOT be overridden
       Polymorphism also works through INTERFACES, which is how Java
            provides multiple inheritance of type
    ```

    - Why it matters: polymorphism lets code written today operate on classes written tomorrow. Adding a `Triangle` subclass needs no change at all to the loop above — the `open-closed principle`, open for extension and closed for modification.

50. **Explain feature of OOP.** *[Palli Sanchay Bank Programmer 2018 compact it 1170-1171 (ET: N/A)]*

    Answer: The features of OOP are the four pillars, together with the class and object mechanism on which they rest.

    1. Class and Object
    ```
       CLASS  : a blueprint defining attributes and methods
       OBJECT : an instance of that class, occupying real memory
    ```
    ```java
    class Student {
        String name;  int roll;          // attributes
        void display() { ... }           // method
    }
    Student s1 = new Student();          // object
    ```

    2. Encapsulation
    - Binding data and methods into one unit and `hiding` the internal state behind private fields with public accessors.
    ```java
    class Account {
        private double balance;
        public void deposit(double a) { if (a > 0) balance += a; }
        public double getBalance() { return balance; }
    }
    ```
    - Gives `data security`: the object cannot be put into an invalid state from outside.

    3. Abstraction
    - Showing only the `essential features` and hiding the implementation. Achieved with `abstract classes` and `interfaces`.
    ```java
    abstract class Shape { abstract double area(); }
    ```
    - The caller learns `what` a class does, not `how`.

    4. Inheritance
    - A new class acquires the members of an existing one, an `is-a` relationship.
    ```java
    class Dog extends Animal { void bark() { ... } }
    ```
    ```
       Types : single , multilevel , hierarchical , multiple , hybrid
    ```
    - Gives `code reuse` and a natural hierarchy.

    5. Polymorphism
    - One method name behaving differently by context.
    ```
       Compile-time : method OVERLOADING - the compiler decides
       Runtime      : method OVERRIDING  - the JVM decides
    ```
    - Gives `flexibility`: one interface serves many implementations.

    6. Message passing
    - Objects cooperate by `calling each other's methods` and passing data as arguments.

    7. Dynamic binding
    - The method body is chosen at `run time` from the actual object — the mechanism behind runtime polymorphism.

    8. Constructor and destructor
    - Automatic initialisation when an object is created and cleanup when it is destroyed, so an object is never used uninitialised.

    9. Access modifiers
    ```
       private   : the class only
       protected : the class and its subclasses
       public    : everywhere
       default   : the same package (Java)
    ```
    - The tool by which encapsulation is actually enforced.

    Advantages these features deliver
    ```
       Reusability      : inheritance and composition
       Maintainability  : a change stays inside one class
       Modularity       : each class is self-contained
       Data security    : private state, validated access
       Extensibility    : add a class rather than edit existing ones
       Real-world model : objects match real entities
       Team development : parallel work on separate classes
    ```

    Disadvantages
    ```
       A steeper learning curve than procedural programming
       Larger programs and some runtime overhead
       Over-engineering is easy - a short script does not need classes
       Deep inheritance hierarchies become fragile
    ```

    - Languages: `Java, C++, C#, Python, Kotlin, Swift, Ruby`.

51. **What do you mean by Polymorphism and Inheritance in Object Oriented Programming (OOP)? Give appropriate example.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1173 (ET: N/A)]*

    Answer: Polymorphism
    - `Polymorphism` means "many forms": the same method name behaves differently depending on the object it acts on or the arguments given.
    ```
       Compile-time (static)  : method OVERLOADING - the compiler decides
       Runtime (dynamic)      : method OVERRIDING  - the JVM decides
    ```

    Inheritance
    - `Inheritance` lets a new class acquire the fields and methods of an existing one. The existing class is the `superclass` and the new one the `subclass`, and the relationship is `is-a`.
    - Its purposes are `code reuse` and creating a natural hierarchy.
    ```
       Types : single , multilevel , hierarchical ,
               multiple (through interfaces in Java) , hybrid
    ```

    A single example showing both
    ```java
    // ---------- inheritance : the superclass ----------
    class Employee {
        protected String name;
        protected double basic;

        Employee(String name, double basic) {
            this.name  = name;
            this.basic = basic;
        }

        double calculateSalary() { return basic; }

        void display() {                       // written ONCE, used by all
            System.out.println(name + " earns " + calculateSalary());
        }
    }

    // ---------- inheritance : subclasses ----------
    class Manager extends Employee {
        Manager(String n, double b) { super(n, b); }

        @Override                              // polymorphism : overriding
        double calculateSalary() { return basic + 0.40 * basic; }
    }

    class Officer extends Employee {
        Officer(String n, double b) { super(n, b); }

        @Override
        double calculateSalary() { return basic + 0.20 * basic; }
    }

    // ---------- polymorphism : overloading in the same class ----------
    class Bonus {
        double give(double salary)               { return salary * 0.10; }
        double give(double salary, int years)    { return salary * 0.10 * years; }
    }

    public class Main {
        public static void main(String[] args) {

            // RUNTIME polymorphism through inheritance
            Employee[] staff = {
                new Manager("Rahim", 50000),
                new Officer("Karim", 50000),
                new Employee("Jamal", 50000)
            };
            for (Employee e : staff) e.display();

            // COMPILE-TIME polymorphism through overloading
            Bonus b = new Bonus();
            System.out.println(b.give(50000));        // 5000.0
            System.out.println(b.give(50000, 3));     // 15000.0
        }
    }
    ```
    Output
    ```
       Rahim earns 70000.0
       Karim earns 60000.0
       Jamal earns 50000.0
       5000.0
       15000.0
    ```

    What the example shows
    - `Inheritance`: `name`, `basic` and `display()` are written once in `Employee` and reused by both subclasses. Nothing is duplicated.
    - `Runtime polymorphism`: the array is declared `Employee[]`, so the compiler cannot know which `calculateSalary()` will run. The JVM decides from the actual object — `dynamic method dispatch`.
    - Notice that `display()` is `not` overridden, yet it prints the right salary for every subclass, because the method it calls is resolved polymorphically. That is the real power of overriding.
    - `Compile-time polymorphism`: the two `give()` methods share a name but differ in parameters, and the compiler picks the right one.

    How the two relate

    | Point | Inheritance | Polymorphism |
    |---|---|---|
    | Meaning | A class acquires another's members | One name, many behaviours |
    | Purpose | Code reuse and hierarchy | Flexibility and extensibility |
    | Relationship expressed | Is-a | — |
    | Keyword | `extends`, `implements` | `@Override`, or `virtual` in C++ |
    | Depends on the other | No | `Yes` — runtime polymorphism needs inheritance |

    - The practical payoff: adding a `Director` subclass requires no change at all to `main`. This is the `open-closed principle` — open for extension, closed for modification.

52. **Consider a base class Shape and its derived class Rectangle. Design a code inheritance code using C++.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1193 (ET: N/A)]*

    Answer: `Rectangle` is a kind of `Shape`, so the relationship is `is-a` and inheritance is the right tool. The base class declares what every shape must provide; the derived class supplies the formulas.

    ```cpp
    #include <iostream>
    #include <string>
    using namespace std;

    // ---------------- BASE CLASS ----------------
    class Shape {
    protected:                          // visible to derived classes
        string name;

    public:
        Shape(string n = "Shape") { name = n; }

        virtual double area()      { return 0; }     // VIRTUAL - to be overridden
        virtual double perimeter() { return 0; }

        virtual void display() {
            cout << "Shape   : " << name << endl;
            cout << "Area    : " << area() << endl;
            cout << "Perimeter: " << perimeter() << endl;
            cout << "-----------------------------" << endl;
        }

        virtual ~Shape() {}                          // virtual destructor
    };

    // ---------------- DERIVED CLASS ----------------
    class Rectangle : public Shape {
    private:
        double length;
        double width;

    public:
        Rectangle(double l, double w) : Shape("Rectangle") {
            length = l;
            width  = w;
        }

        double area() override {
            return length * width;
        }

        double perimeter() override {
            return 2 * (length + width);
        }

        void display() override {
            Shape::display();                        // reuse the base version
            cout << "Length  : " << length << endl;
            cout << "Width   : " << width  << endl;
            cout << "-----------------------------" << endl;
        }
    };

    // ---------------- ANOTHER DERIVED CLASS ----------------
    class Circle : public Shape {
    private:
        double radius;

    public:
        Circle(double r) : Shape("Circle") { radius = r; }

        double area() override      { return 3.1416 * radius * radius; }
        double perimeter() override { return 2 * 3.1416 * radius; }
    };

    // ---------------- MAIN ----------------
    int main() {
        Rectangle r(5, 3);
        r.display();

        // polymorphism : a base pointer holding derived objects
        Shape* shapes[2];
        shapes[0] = new Rectangle(4, 6);
        shapes[1] = new Circle(5);

        for (int i = 0; i < 2; i++)
            shapes[i]->display();       // each object uses ITS OWN area()

        for (int i = 0; i < 2; i++) delete shapes[i];
        return 0;
    }
    ```

    Output
    ```
       Shape   : Rectangle
       Area    : 15
       Perimeter: 16
       -----------------------------
       Length  : 5
       Width   : 3
       -----------------------------
       Shape   : Rectangle
       Area    : 24
       Perimeter: 20
       -----------------------------
       Length  : 4
       Width   : 6
       -----------------------------
       Shape   : Circle
       Area    : 78.54
       Perimeter: 31.416
       -----------------------------
    ```

    Better design — an abstract base class
    ```cpp
    class Shape {
    protected:
        string name;
    public:
        Shape(string n) { name = n; }
        virtual double area() = 0;          // PURE virtual - no body
        virtual double perimeter() = 0;
        virtual ~Shape() {}
    };
    ```
    - With a pure virtual function, `Shape` becomes `abstract`: it cannot be instantiated, and every concrete subclass `must` implement `area()` and `perimeter()`. This is usually the correct model, since a "shape" with no particular form has no area of its own.

    Concepts the program demonstrates
    ```
       INHERITANCE   : Rectangle : public Shape  -> reuses name and display()
       POLYMORPHISM  : area() and perimeter() are virtual, so the loop over
                       Shape* calls each object's own version at RUN TIME
       ENCAPSULATION : length and width are private, name is protected
       ABSTRACTION   : main() works only with Shape*, knowing nothing about
                       how each shape computes its area
       CODE REUSE    : Rectangle::display() calls Shape::display() instead
                       of repeating it
    ```

    Points worth stating
    - The base methods must be declared `virtual`, otherwise `shapes[i]->area()` would always call `Shape::area()` and return 0 — the classic C++ mistake.
    - The destructor is also `virtual`, so `delete` through a base pointer destroys the derived part as well.
    - Adding a `Triangle` class requires no change at all to `main` — the `open-closed principle`.

53. **Difference between method overloading and overriding in java.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1220 (ET: N/A)]*

    Answer: Both are forms of polymorphism in Java, but they occur in different places and are resolved at different times.

    Method overloading
    - Several methods in the `same class` share a name but take `different parameter lists`. The `compiler` chooses which to call.
    ```java
    class Calculator {
        int    add(int a, int b)          { return a + b; }
        double add(double a, double b)    { return a + b; }
        int    add(int a, int b, int c)   { return a + b + c; }
    }
    ```
    - No inheritance is needed. It is `compile-time`, `static` or `early` binding.

    Method overriding
    - A `subclass` supplies its own version of an inherited method, with `exactly the same signature`. The `JVM` decides at run time.
    ```java
    class Animal {
        void sound() { System.out.println("Some sound"); }
    }
    class Dog extends Animal {
        @Override void sound() { System.out.println("Bhow Bhow"); }
    }

    Animal a = new Dog();
    a.sound();          // "Bhow Bhow" - decided at RUN TIME
    ```
    - Inheritance is required. It is `runtime`, `dynamic` or `late` binding.

    Difference

    | Point | Method overloading | Method overriding |
    |---|---|---|
    | Where | Same class | Superclass and subclass |
    | Parameter list | Must `differ` | Must be `identical` |
    | Return type | May differ | Same or covariant |
    | Inheritance | Not required | `Required` |
    | Binding | Compile time (static) | Run time (dynamic) |
    | Also called | Early binding | Late binding |
    | Access modifier | Any | Cannot be more restrictive |
    | `static` methods | Can be overloaded | Cannot be overridden (only hidden) |
    | `private` methods | Can be overloaded | Cannot be overridden |
    | `final` methods | Can be overloaded | Cannot be overridden |
    | Constructors | Can be overloaded | Cannot be overridden |
    | Exceptions | Any may be declared | Cannot declare a broader checked exception |
    | Number of classes | 1 | 2 or more |
    | Performance | Slightly faster | A small runtime lookup |
    | Purpose | Convenience | Specialisation |

    Java-specific details worth stating
    ```
       @Override is optional but recommended : the compiler then reports an
            error if the signature is mistyped, which would otherwise become
            a silent OVERLOAD instead of an override

       Overloading cannot be distinguished by RETURN TYPE alone

       A static method with the same signature in a subclass is HIDDEN, not
            overridden, and is resolved by the REFERENCE type :

               Base b = new Derived();
               b.staticMethod();      // the BASE version runs

       FIELDS are never polymorphic - they too are resolved by the
            reference type
    ```

    Worked contrast showing both together
    ```java
    class Base {
        void show(int a)     { System.out.println("Base int"); }
        void show(String s)  { System.out.println("Base String"); }  // OVERLOAD
    }
    class Derived extends Base {
        @Override
        void show(int a)     { System.out.println("Derived int"); }  // OVERRIDE
    }

    public class Main {
        public static void main(String[] args) {
            Base b = new Derived();
            b.show(5);          // "Derived int"  -> overriding, run time
            b.show("hi");       // "Base String"  -> overloading, compile time
        }
    }
    ```

    - Memory aid: `overloading changes the parameters; overriding changes the body`.

54. **What is polymorphism? What is the difference between method overriding and method overloading?** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265 (ET: N/A)]*

    Answer: What polymorphism is
    - `Polymorphism` means "many forms". The same method name behaves differently depending on the object it is called on or the arguments it is given, so `one interface serves many implementations`.
    - It is one of the four pillars of OOP, with encapsulation, inheritance and abstraction.
    ```
       Compile-time (static, early binding)  -> method OVERLOADING
       Runtime (dynamic, late binding)       -> method OVERRIDING
    ```
    ```java
    // compile-time
    class Calculator {
        int    add(int a, int b)       { return a + b; }
        double add(double a, double b) { return a + b; }
    }

    // runtime
    class Animal { void sound() { System.out.println("Some sound"); } }
    class Dog extends Animal { @Override void sound() { System.out.println("Bhow Bhow"); } }

    Animal a = new Dog();
    a.sound();                    // "Bhow Bhow" - decided at run time
    ```
    - In the runtime case the reference type is `Animal`, so the compiler cannot choose; the JVM inspects the real object — `dynamic method dispatch`.

    Difference between overriding and overloading

    | Point | Method overriding | Method overloading |
    |---|---|---|
    | Where it occurs | Between a `superclass and a subclass` | Within the `same class` |
    | Parameter list | Must be `identical` | Must be `different` |
    | Return type | Same or covariant | May differ |
    | Inheritance | `Required` | Not required |
    | Resolved | At `run time` by the JVM | At `compile time` by the compiler |
    | Also called | Dynamic / late binding | Static / early binding |
    | Number of classes | 2 or more | 1 |
    | Access modifier | Cannot be made more restrictive | Any |
    | `static` methods | Cannot be overridden (only hidden) | Can be overloaded |
    | `private` / `final` methods | Cannot be overridden | Can be overloaded |
    | Constructors | Cannot be overridden | Can be overloaded |
    | C++ requirement | `virtual` in the base class | None |
    | Performance | A small runtime lookup | Slightly faster |
    | Purpose | Specialise inherited behaviour | One name for related operations |

    Worked contrast
    ```java
    class Base {
        void show(int a)     { System.out.println("Base int"); }
        void show(String s)  { System.out.println("Base String"); }   // OVERLOAD
    }
    class Derived extends Base {
        @Override
        void show(int a)     { System.out.println("Derived int"); }   // OVERRIDE
    }

    public class Main {
        public static void main(String[] args) {
            Base b = new Derived();
            b.show(5);          // "Derived int"  -> overriding, run time
            b.show("hi");       // "Base String"  -> overloading, compile time
        }
    }
    ```

    - Memory aid: `overriding changes the body, overloading changes the parameters`.
    - Why overriding matters more: it lets code written today work with classes written tomorrow. A loop over `Animal` objects needs no change when a new subclass is added — the `open-closed principle`.

## Java Programming & Methods (18)

1. **Write a Java Code which return a value.** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*

2. **Write a Java Code....** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*

3. **What does run Finalization do?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **What syntax is used for calling static methods in class?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

5. **Consider the following code:** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*
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
**Mention which of the methods overload, override and hied supper class methods. What about the remaining method?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 437 (ET: BIBM)]*

6. **অথবা, (ক) ‘Static’ কীওয়ার্ডটি ব্যাখ্যা করার জন্যে Static Variable এবং Static Method ব্যবহার করে একটি প্রোগ্রাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*

7. **Write a java program to counting the vowel and consonant into a given strings.** *[BOF Assistant Programmer 2022 compact it 735 (ET: MIST)]*

8. **Where will be the most chance of the grabage collector being invoked?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

9. **In Java program. Write the method in given box for the Electric bill calculation if unit is less then 100 then unit rate 4.0 take and after 100-unit rate is 5.50 and reaming unit rate is 6.00. [Bill rate 4.0 if unit<=100, Bill rate 5.50 if (unit>100 && unit<=200), Bill rate 6.00 for remaining units.]** *[BPDB Assistant Engineer (CSE) 2021 compact it 816-817 (ET: BUET)]*

10. **C# language এর একটি প্রোগ্রাম লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

11. **Write java program for calculate electricity bill using class and object.** *[Sundharban Gas Assistant Programmer 2020 compact it 1047-1048 (ET: N/A)]*

12. **What are the difference among JDK, JRE and JVM?** *[Islami Bank Bangladesh Limited Officer (Software Engineer) 2019 compact it 1098 (ET: N/A)]*

13. **(c) Why Java is called platform independent language?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

14. **Suppose you've a method name “totalAmount” and there three properties (transactionName, transactionType, amount). Write down the full code using JAVA where totalAmount method return total balance after debit or credited.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

15. **Write the full form of following topics:** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*
   i) JAR
   ii) JRE
   iii) WAR
   iv) JDK

16. **Write a java program using 2D array and array output will be-** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1191 (ET: N/A)]*
```text
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

17. **Write simple Java program to convert string into camel case and display camel case string.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1191-1192 (ET: N/A)]*

18. **Discus architecture of Java virtual machine.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1218-1219 (ET: N/A)]*

## Class Design & Object-Oriented Modeling (11)

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 425 (ET: BIBM)]*

2. **What are the built in classes?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

3. **অথবা, (ক) উদাহরণসহ Class এবং Object এর মধ্যে পার্থক্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

4. **(খ) উদাহরণসহ ক্লাস এবং অবজেক্ট এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

5. **Define Class and Object in C++ with example.** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

6. **What are the common activities on OOP design process?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*

7. **Write a programme to create an object of type batsman and calculate the average runs scored by the player.** *[RAKUB Programmer (PO) 12.10.2021 compact it 846-847 (ET: N/A)]*

8. **(ক) Object কী? কীভাবে Object তৈরি করতে হয় উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1085 (ET: N/A)]*

9. **Suppose, you are implementing “Overdraft Account (OD)” class using java for a banking app. An OD type account is opened with an approved loan limit (ex. 100000/-). The account holder can deposit any amount of money in the OD account at any time. S/he can draw an amount of money from the account (acn) until sufficient acn balance. S/he allowed to draw money beyond his/her acn balance if the total over-drawing amount remains within the loan limit. A java sketch for OD acn is given bellow & code is expected to run in multi-threading mode. (same code with run by different counter in the Bank)** *[Bangladesh Bank Assistant Programmer 2019 compact it 1157 (ET: DU)]*

10. **There was a java program where you have to create a class, constructor, setter function, getter function.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1214-1215 (ET: N/A)]*

11. **In java language: write a class named Bicycle having 3 integer variables (speed, gear, cost) and a constructor to initialize the variables. Also write a class named MountBike that inherits Bicycle class, having an extra variable speedcost and a constructor to initialize the variable.** *[DESCO Assistant Engineer (CSE) 2016 compact it 1269 (ET: N/A)]*

## Output Tracing & Recursion (10)

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

2. **(খ) কোন object-oriented programming language ব্যবহার করে একটি program লিখুন, যা recursive function ব্যবহার করে Fibonacci series প্রদান করবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **6.13 Consider the following Java program and determine the integer value printed by the execution of the main() method:** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*
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

4. **Show the output following program.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1115-1116 (ET: DU)]*
```java
public class main {
    public static void find_output(int n) {
        int i, j;
        for(i=1; i<=n; i++) {
            for(j=n; j>0; j--) {
                if(i==j) {
                    System.out.print("*");
                    break;
                }
                else {
                    System.out.print("*");
                }
            }
            System.out.print("\n");
        }
    }
    public static void main(String[] args) {
        find_output(10);
    }
}
```

5. **What is the output of the following java code?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1117 (ET: BUET)]*
```java
class car {
    void run() {
        System.out.println("Car is running");
    }
}
public class Audi extends car {
    void run() {
        System.out.println("Audi is running");
    }
    public static void main(String[] args) {
        car b = new Audi();
        b.run();
    }
}
```

6. **Find the output of Java program:** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*
```java
public class Main{
    public static void main(String[] args) {
        int i=0;
        for(int j=5; i<3 && j<10; i++, j++) {
            System.out.print(" "+i + " "+j);
        }
    }
}
```

7. **What will be the output of following program?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1192-1193 (ET: N/A)]*
```cpp
using namespace std;
class A{
    private:
        int a;
        int b;
        void set_a(int a) {
            this->a=a;
        }
        void set_b(int b) {
            this->b=b;
        }
    public:
        void getValues(int x, int y) {
            set_a(x); //calling private number
            set_b(x); //calling private number
        }
        void putValues() {
            cout << "a=" << a << " ,b=" << b << endl;
        }
};
int main() {
    A objA; //creating object
    objA.getValues(100,200);
    objA.putValues(); //print values
    return 0;
}
```

8. **Find the output below following code.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1194 (ET: N/A)]*
```java
public class Test {
    public static void main(String[] args) {
        String s1 = "test1";
        String s2 = new String("test1");
        System.out.println(s1==s2);
        String s3 = new String("test1");
        System.out.println(s2==s3);
        s3 = s1;
        System.out.println(s3==s1);
    }
}
```

9. **Consider the following program and perform the task that follow:** *[Combined 3 Banks Assistant Programmer 2018 compact it 1194-1195 (ET: N/A)]*
```java
public class WhatTheOutput{
    public static int performOperations(int i){
        int original=i;
        return i=((10+(i*2))/2-original);
    }
    public static String result(int i){
        String result;
        switch(i){
            case 3:{
                result="a multiple of 3";
                break;
            }
            case 5:{
                result ="acceptable";
                break;
            }
            case 7:{
                result="a multiple of 7";
                break;
            }
            default:{
                result="unacceptable";
                break;
            }
        }
        return result;
    }
    public static void main(String[] args){
        int number[]={4,8,12,21,30,100};
        for(int i=0; i<5; i++){
            System.out.println("The chosen number, "+number[i]+", is" +result(performOperations (numbers[i])));
        }
    }
}
```

10. **You are required to trace the changes in value for each of the numbers, before and after each method are called for each of iterations and finally write down output of the program.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1195-1196 (ET: N/A)]*

## Constructors & Destructors (8)

1. **What is constructor function? Write the properties of it.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

2. **Define copy constructor. What Static binding and Dynamic binding?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

3. **What is the constructor invoked in OOP?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

4. **What is constructor?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

5. **(b) Why are constructor and destructor functions used in object oriented programming? Give examples of each function in C++ or java language.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

6. **What is Constructor function? Write an example of Constructor function?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*

7. **Differentiate constructor and destructor with example.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1167-1168 (ET: N/A)]*

8. **What is main difference Destructor and constructor with example?** *[Palli Sanchay Bank Programmer 2018 compact it 1171 (ET: N/A)]*

## Encapsulation & Access Modifiers (7)

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

2. **Explain the various types of access specifiers.** *[DESCO Assistant Engineer 20.05.2023 compact it 579 (ET: DESCO)]*

3. **Which type of variable violates encapsulation rules?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

4. **Which members of base class cannot access to derived class?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

5. **What are the various Access Specification in C++? Explain their purpose with are example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*

6. **How many specifiers are used in C++ programing?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

7. **Briefly Describe Abstraction, Encapsulation.** *[Bangladesh Competition Commission Programmer 2019 compact it 1059-1060 (ET: DU)]*

## Exception Handling (4)

1. **(b) What is exception? Explain how it can be used for debugging a program.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

2. **What is difference between exception and error in Java?** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*

3. **What is exception handling? Write with an example.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

4. **Write the difference between throw and throws using Exception handling?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1172-1173 (ET: N/A)]*

## C++ OOP Concepts & Friend Functions (3)

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1355 (ET: N/A)]*
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```

2. **(ক) Friend Function কী? উহার সুবিধা অসুবিধাগুলো লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

3. **(খ) Friend Function কী? উহার সুবিধা ও অসুবিধা গুলো লিখুন?** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1086 (ET: N/A)]*

## Interfaces & Abstract Classes (2)

1. **Class/Interface implementation of code?** *[BCIC Assistant Programmer 14.02.2025 compact it 1329 (ET: BUET)]*

2. **An Abstract class Player with two sub classes Bowler and Batsman, Abstract class has one abstract method average, also have constructor and a string function that display name bowler or batsman. Batsman class implement abstract function average and display result, Batsman class have run and number match data. Now write a Java Program and show Batsman average run.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*
