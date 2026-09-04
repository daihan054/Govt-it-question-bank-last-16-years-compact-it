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

    Answer: The question is `incomplete` — the paper itself records that the exact problem could not be collected. It is an inheritance problem, and the complete treatment is given below.

    What inheritance is
    - `Inheritance` lets a new class acquire the fields and methods of an existing one. The existing class is the `superclass` (parent, base) and the new one the `subclass` (child, derived). The relationship is `is-a`.
    - Its purposes are `code reuse`, a natural hierarchy, and enabling `runtime polymorphism`.

    The five types
    ```
       1. SINGLE        A -> B
       2. MULTILEVEL    A -> B -> C
       3. HIERARCHICAL  A -> B , A -> C
       4. MULTIPLE      A , B -> C     (Java: interfaces only)
       5. HYBRID        any combination of the above
    ```
    ```
       Single        Multilevel      Hierarchical      Multiple
          A              A                A             A   B
          |              |               / \             \ /
          B              B              B   C             C
                         |
                         C
    ```

    A complete worked problem — the type these questions use
    ```java
    // ---------- SUPERCLASS ----------
    class Employee {
        protected String name;
        protected double basic;

        public Employee(String name, double basic) {
            this.name  = name;
            this.basic = basic;
        }

        public double calculateSalary() {          // to be OVERRIDDEN
            return basic;
        }

        public void display() {                    // reused by every subclass
            System.out.printf("%-10s %-12s %10.2f%n",
                              name, getClass().getSimpleName(), calculateSalary());
        }
    }

    // ---------- SUBCLASSES ----------
    class Manager extends Employee {
        private double allowance;

        public Manager(String name, double basic, double allowance) {
            super(name, basic);                    // MUST be the first statement
            this.allowance = allowance;
        }

        @Override
        public double calculateSalary() {
            return basic + allowance + 0.40 * basic;
        }
    }

    class Officer extends Employee {
        public Officer(String name, double basic) { super(name, basic); }

        @Override
        public double calculateSalary() { return basic + 0.20 * basic; }
    }

    class Clerk extends Employee {
        public Clerk(String name, double basic) { super(name, basic); }
        // calculateSalary() is NOT overridden - the inherited version is used
    }

    // ---------- MAIN ----------
    public class Main {
        public static void main(String[] args) {

            Employee[] staff = {                   // SUPERCLASS references
                new Manager("Rahim", 50000, 10000),
                new Officer("Karim", 50000),
                new Clerk  ("Jamal", 30000)
            };

            double total = 0;
            for (Employee e : staff) {
                e.display();                       // each runs ITS OWN version
                total += e.calculateSalary();
            }
            System.out.printf("%-23s %10.2f%n", "TOTAL", total);
        }
    }
    ```
    Output
    ```
       Rahim      Manager        80000.00
       Karim      Officer        60000.00
       Jamal      Clerk          30000.00
       TOTAL                    170000.00
    ```

    What the program demonstrates
    ```
       INHERITANCE          : name, basic and display() written ONCE
       CONSTRUCTOR CHAINING : super(...) passes values up to the parent
       METHOD OVERRIDING    : each subclass redefines calculateSalary()
       RUNTIME POLYMORPHISM : the array holds Employee references, so the
                              JVM decides at run time which version runs -
                              DYNAMIC METHOD DISPATCH
       OPEN-CLOSED PRINCIPLE: adding a Director class needs NO change to main
    ```

    Rules that such problems test
    ```
       super(...) must be the FIRST statement in a subclass constructor
       Constructors are NOT inherited
       A subclass CANNOT access the PRIVATE members of its parent -
            only public and protected ones, and default ones in the same package
       An overriding method cannot REDUCE the access level
       'final' prevents overriding ; a final CLASS cannot be inherited at all
       'static' methods are HIDDEN, not overridden - resolved by the
            reference type, not the object
       FIELDS are never polymorphic - also resolved by the reference type
       Java forbids multiple inheritance of CLASSES, to avoid the DIAMOND
            PROBLEM ; interfaces provide it safely
    ```

    - The caution worth adding: inheritance creates `tight coupling`, so a change in the superclass can break every subclass. The modern advice is `prefer composition over inheritance` — hold an object as a field when the relationship is really `has-a` rather than `is-a`.

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

   Answer: A method that returns a value must declare a `return type` other than `void`, and every path through it must execute a `return` statement.
   ```java
      returnType methodName(parameters) {
          ...
          return value;         // the type must match returnType
      }
   ```

   Simple example — returning an int
   ```java
   public class Calculator {

       // returns the sum of two integers
       public int add(int a, int b) {
           return a + b;                    // returns an int
       }

       // returns a double
       public double average(int a, int b, int c) {
           return (a + b + c) / 3.0;
       }

       // returns a boolean
       public boolean isEven(int n) {
           return n % 2 == 0;
       }

       // returns a String
       public String grade(int marks) {
           if (marks >= 80) return "A+";
           else if (marks >= 70) return "A";
           else if (marks >= 60) return "A-";
           else if (marks >= 33) return "Pass";
           else return "Fail";
       }

       public static void main(String[] args) {
           Calculator c = new Calculator();

           int sum = c.add(10, 20);
           System.out.println("Sum      : " + sum);            // 30
           System.out.println("Average  : " + c.average(10,20,30));  // 20.0
           System.out.println("Is even  : " + c.isEven(10));   // true
           System.out.println("Grade    : " + c.grade(75));    // A
       }
   }
   ```
   Output
   ```
      Sum      : 30
      Average  : 20.0
      Is even  : true
      Grade    : A
   ```

   Returning an array
   ```java
   public int[] getEvenNumbers(int limit) {
       int count = limit / 2;
       int[] result = new int[count];
       int index = 0;
       for (int i = 2; i <= limit; i += 2)
           result[index++] = i;
       return result;                       // returns an array
   }
   ```

   Returning an object
   ```java
   class Student {
       String name;  int roll;
       Student(String name, int roll) { this.name = name; this.roll = roll; }
   }

   public Student createStudent(String name, int roll) {
       return new Student(name, roll);      // returns an object
   }
   ```

   Rules for `return`
   ```
      The returned value's type must MATCH the declared return type, or be
           automatically convertible to it (int -> long -> double)

      A method declared void must not return a value; a bare 'return;' is
           allowed, to exit early

      Every path must return : a missing return on one branch is a
           compile error, "missing return statement"

      return ends the method IMMEDIATELY - code after it is unreachable

      Only ONE value can be returned. To return several, use an array,
           an object, or a collection.
   ```

   Common mistake
   ```java
      public int check(int n) {
          if (n > 0) return 1;
          // ERROR: missing return statement - the else path returns nothing
      }
   ```
   - The fix is to add a `return` for every path, or a single `return` at the end.

2. **Write a Java Code....** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*

   Answer: The question is `incomplete` — the paper printed only "Write a Java Code...." and the requirement was not captured. The programs that this paper asks for elsewhere are given below, so the answer covers whichever was intended.

   Program 1 — a class with encapsulation, constructor, getters and setters
   ```java
   class BankAccount {

       private String accountNumber;      // PRIVATE - encapsulation
       private String holderName;
       private double balance;

       public BankAccount(String accNo, String name, double opening) {
           this.accountNumber = accNo;
           this.holderName    = name;
           this.balance       = (opening > 0) ? opening : 0;
       }

       public void deposit(double amount) {
           if (amount > 0) balance += amount;
           else System.out.println("Deposit must be positive");
       }

       public void withdraw(double amount) {
           if (amount > 0 && amount <= balance) balance -= amount;
           else System.out.println("Insufficient balance");
       }

       public double getBalance()       { return balance; }
       public String getAccountNumber() { return accountNumber; }
   }

   public class Main {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount("AC1001", "Rahim", 5000);
           acc.deposit(2000);
           acc.withdraw(1500);
           System.out.println("Balance: " + acc.getBalance());   // 5500.0
       }
   }
   ```

   Program 2 — a method that returns a value
   ```java
   public class Calculator {
       public int add(int a, int b)          { return a + b; }
       public double average(int a, int b)   { return (a + b) / 2.0; }
       public boolean isEven(int n)          { return n % 2 == 0; }

       public String grade(int marks) {
           if (marks >= 80) return "A+";
           else if (marks >= 70) return "A";
           else if (marks >= 60) return "B";
           else if (marks >= 33) return "Pass";
           else return "Fail";
       }

       public static void main(String[] args) {
           Calculator c = new Calculator();
           System.out.println(c.add(10, 20));     // 30
           System.out.println(c.grade(75));       // A
       }
   }
   ```

   Program 3 — inheritance and method overriding
   ```java
   class Employee {
       protected String name;
       protected double basic;

       Employee(String name, double basic) {
           this.name = name; this.basic = basic;
       }
       double calculateSalary() { return basic; }
       void display() { System.out.println(name + " : " + calculateSalary()); }
   }

   class Manager extends Employee {
       Manager(String n, double b) { super(n, b); }
       @Override double calculateSalary() { return basic + 0.40 * basic; }
   }

   public class Main {
       public static void main(String[] args) {
           Employee[] staff = { new Manager("Rahim", 50000),
                                new Employee("Karim", 50000) };
           for (Employee e : staff) e.display();
       }
   }
   ```

   Program 4 — exception handling
   ```java
   import java.util.Scanner;

   public class Divide {
       public static void main(String[] args) {
           Scanner sc = new Scanner(System.in);
           try {
               System.out.print("Numerator  : ");
               int a = sc.nextInt();
               System.out.print("Denominator: ");
               int b = sc.nextInt();
               System.out.println("Result: " + (a / b));
           } catch (ArithmeticException e) {
               System.out.println("Cannot divide by zero");
           } catch (Exception e) {
               System.out.println("Invalid input: " + e.getMessage());
           } finally {
               sc.close();
           }
       }
   }
   ```

   Program 5 — string and array handling
   ```java
   public class StringDemo {
       public static void main(String[] args) {

           String s = "Bangladesh";
           System.out.println(s.length());           // 10
           System.out.println(s.toUpperCase());      // BANGLADESH
           System.out.println(s.substring(0, 5));    // Bangl
           System.out.println(new StringBuilder(s).reverse());  // hsedalgnaB

           int[] a = {45, 12, 78, 33, 90};
           int max = a[0], sum = 0;
           for (int x : a) {
               sum += x;
               if (x > max) max = x;
           }
           System.out.println("Sum: " + sum + ", Max: " + max);
       }
   }
   ```

   Program 6 — recursion
   ```java
   public class Recursion {
       static int factorial(int n) {
           return (n <= 1) ? 1 : n * factorial(n - 1);
       }
       static int fib(int n) {
           return (n <= 1) ? n : fib(n - 1) + fib(n - 2);
       }
       public static void main(String[] args) {
           System.out.println(factorial(5));            // 120
           for (int i = 0; i < 8; i++) System.out.print(fib(i) + " ");
           // 0 1 1 2 3 5 8 13
       }
   }
   ```

   - The structure every Java program must have: a `class`, a `public static void main(String[] args)` entry point, and a file named exactly after the public class. `System.out.println` prints, `Scanner` reads input, and every field should be `private` with public methods giving controlled access.

3. **What does run Finalization do?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: `System.runFinalization()` asks the JVM to run the `finalize()` methods of objects that have been found unreachable and are waiting for finalization.

   What finalization is
   - `finalize()` is a method inherited from `Object`. Before the garbage collector reclaims an object's memory, the JVM was designed to call the object's `finalize()` once, giving it a last chance to release resources such as a file handle or a socket.
   ```java
   class Resource {
       @Override
       protected void finalize() throws Throwable {
           System.out.println("Cleaning up before collection");
           super.finalize();
       }
   }
   ```

   What runFinalization does
   ```java
      System.gc();                 // SUGGEST that garbage collection runs
      System.runFinalization();    // SUGGEST that pending finalizers run
   ```
   - It is only a `request`, never a command. The JVM is free to ignore it, exactly as it may ignore `System.gc()`.
   - It does not itself collect anything; it only asks that finalizers already queued be executed sooner rather than later.
   - `Runtime.getRuntime().runFinalization()` is the same call through the Runtime object.

   The order of events
   ```
      1. The object becomes unreachable.
      2. The GC notices it and, if the class overrides finalize(),
         places it on the FINALIZATION QUEUE instead of freeing it.
      3. A finalizer thread runs finalize() at some unspecified later time.
      4. Only on the NEXT collection cycle is the memory actually freed.
   ```
   - This is why a finalizable object needs `at least two` GC cycles to disappear.

   Why finalization is deprecated and should not be used
   ```
      No guarantee it ever runs. If the program exits first, it never does.
      No guarantee of WHEN it runs, or in what order.
      It SLOWS DOWN garbage collection badly - a finalizable object survives
           an extra cycle and needs an extra thread.
      An exception thrown inside finalize() is silently swallowed.
      An object can RESURRECT itself inside finalize() by storing 'this'
           somewhere reachable, which breaks the collector's assumptions.
      It has caused real security vulnerabilities (finalizer attacks).
   ```
   - `finalize()` was deprecated in `Java 9` and `removed in Java 18`.

   What to use instead
   ```java
      // try-with-resources : close() is called automatically, always
      try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
          System.out.println(br.readLine());
      }   // br.close() runs here even if an exception is thrown
   ```
   - Implement `AutoCloseable` and let `try-with-resources` handle cleanup, or use `java.lang.ref.Cleaner` for the rare case where a native resource must be released as a safety net.

   - Short answer: `System.runFinalization()` requests that any pending `finalize()` methods be run. It guarantees nothing, and the whole finalization mechanism is deprecated in favour of `try-with-resources`.

4. **What syntax is used for calling static methods in class?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: A `static` method belongs to the `class` itself, not to any object, so it is called through the class name.
   ```java
      ClassName.methodName(arguments);
   ```

   Example
   ```java
   class MathUtil {

       static int square(int n) {          // static method
           return n * n;
       }

       static double PI = 3.1416;          // static variable

       static double areaOfCircle(double r) {
           return PI * r * r;
       }
   }

   public class Main {
       public static void main(String[] args) {

           int s = MathUtil.square(5);              // CLASS NAME . METHOD
           System.out.println(s);                   // 25

           System.out.println(MathUtil.areaOfCircle(3));   // 28.2744
           System.out.println(MathUtil.PI);                // 3.1416
       }
   }
   ```

   Built-in examples of the same syntax
   ```java
      Math.sqrt(25)                 // 5.0
      Math.max(10, 20)              // 20
      Integer.parseInt("123")       // 123
      String.valueOf(45)            // "45"
      Arrays.sort(myArray)
      System.currentTimeMillis()
   ```

   Calling from inside the same class
   ```java
   class Demo {
       static void greet() { System.out.println("Hello"); }

       public static void main(String[] args) {
           greet();              // no class name needed inside the same class
           Demo.greet();         // also valid, and clearer
       }
   }
   ```

   Calling through an object — legal but bad practice
   ```java
      MathUtil m = new MathUtil();
      m.square(5);              // COMPILES, but misleading
   ```
   - The compiler allows it and simply resolves it to `MathUtil.square(5)`, but it suggests the method belongs to the object when it does not. Most style guides and IDE warnings forbid it.

   Key rules about static methods
   ```
      Called by CLASS NAME, no object needed
      Can access only STATIC variables and other STATIC methods directly
      CANNOT use 'this' or 'super', because there is no object
      Cannot be OVERRIDDEN - a subclass method with the same signature
           HIDES it, and is resolved by the REFERENCE type
      Can be OVERLOADED normally
      Loaded when the class is loaded, before any object exists
      main() is static precisely so the JVM can call it without creating
           an object first
   ```

   Why the distinction matters
   ```java
   class Counter {
       static int count = 0;         // ONE copy, shared by all objects
       int id;                       // one copy PER OBJECT

       Counter() { count++; id = count; }
   }
   ```
   - `Counter.count` belongs to the class; `c1.id` belongs to an object. Using the class name for one and an object reference for the other makes the intent obvious to the reader.

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

   Answer: The code as printed contains typing errors — `Public` should be `public`, `class Class A` should be `class A`, and `string` should be `String`. Corrected, it reads:
   ```java
   public class A {
       public void m1() { }
       public void m2(int i) { }
       public void m3(int i) { }
       public static void m4(int i) { }
   }

   public class B extends A {
       public static void m1(int i) { }
       public void m2(int i) { }
       public void m3(String s) { }
       public static void m4(int i) { }
   }
   ```

   Analysis, method by method

   `m1` — OVERLOADING
   ```
      A : public void m1()             no parameters, instance method
      B : public static void m1(int i) one int parameter, static

      The SIGNATURES DIFFER (no parameters versus one int), so B's method
      does not override or hide A's - it OVERLOADS it.

      Class B therefore has BOTH m1() (inherited) and m1(int) (its own).
   ```
   - This is legal. A compile error would occur only if a static method had the `same` signature as an inherited instance method.

   `m2` — OVERRIDING
   ```
      A : public void m2(int i)        instance method
      B : public void m2(int i)        SAME signature, also an instance method

      -> B.m2(int) OVERRIDES A.m2(int).

      The version that runs is decided at RUN TIME by the actual object :

           A obj = new B();
           obj.m2(5);            // B's version runs
   ```

   `m3` — OVERLOADING
   ```
      A : public void m3(int i)        parameter is int
      B : public void m3(String s)     parameter is String

      Different parameter TYPE, so the signatures differ.
      -> B.m3(String) OVERLOADS A.m3(int).

      Class B has BOTH m3(int) (inherited) and m3(String) (its own).
   ```

   `m4` — HIDING
   ```
      A : public static void m4(int i)
      B : public static void m4(int i)   SAME signature, BOTH static

      A static method cannot be overridden. When a subclass declares a
      static method with the same signature, it HIDES the superclass one.

      Hiding is resolved by the REFERENCE type, not the object :

           A obj = new B();
           A.m4(5);         // A's version
           B.m4(5);         // B's version
           obj.m4(5);       // A's version - decided by the REFERENCE type
   ```

   Summary

   | Method | In A | In B | Relationship |
   |---|---|---|---|
   | `m1` | `void m1()` | `static void m1(int)` | `Overloading` |
   | `m2` | `void m2(int)` | `void m2(int)` | `Overriding` |
   | `m3` | `void m3(int)` | `void m3(String)` | `Overloading` |
   | `m4` | `static void m4(int)` | `static void m4(int)` | `Hiding` |

   The remaining methods
   - `A.m1()` and `A.m3(int)` are simply `inherited` by B unchanged. B does not replace them; it adds new overloads beside them. So an object of B can call all of:
   ```java
      B b = new B();
      b.m1();          // inherited from A
      B.m1(5);         // B's own static overload
      b.m2(5);         // B's override
      b.m3(5);         // inherited from A
      b.m3("hi");      // B's own overload
   ```

   - The essential distinction to state: `overriding` replaces an instance method and is resolved at run time by the object; `hiding` replaces a static method and is resolved at compile time by the reference type; `overloading` adds a new method beside the old one, since the signatures differ.

6. **অথবা, (ক) ‘Static’ কীওয়ার্ডটি ব্যাখ্যা করার জন্যে Static Variable এবং Static Method ব্যবহার করে একটি প্রোগ্রাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 620 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The `static` keyword means a member belongs to the `class itself` rather than to any individual object. There is exactly `one copy`, created when the class is loaded, shared by every object.

   Static variable
   - One copy shared by all objects. Changing it through one object changes it for all.
   - Used for a value common to every instance — a counter, a constant, a bank's interest rate.

   Static method
   - Belongs to the class, so it can be called `without creating an object`.
   - Can access only `static` members directly, and cannot use `this` or `super`, because there is no object.

   Program using both
   ```java
   class Student {

       // ---- STATIC variable : one copy shared by every object ----
       static String collegeName = "Dhaka College";
       static int    studentCount = 0;

       // ---- INSTANCE variables : one copy per object ----
       String name;
       int    roll;

       Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
           studentCount++;                 // the SHARED counter increases
       }

       // ---- INSTANCE method : needs an object ----
       void display() {
           System.out.println(roll + " - " + name + " - " + collegeName);
       }

       // ---- STATIC method : called without any object ----
       static void showCount() {
           System.out.println("Total students: " + studentCount);
           // System.out.println(name);    // ERROR - name is an instance field
       }

       static void changeCollege(String newName) {
           collegeName = newName;          // affects EVERY object at once
       }
   }

   public class Main {
       public static void main(String[] args) {

           Student.showCount();            // 0 - called with NO object

           Student s1 = new Student("Rahim", 101);
           Student s2 = new Student("Karim", 102);
           Student s3 = new Student("Jamal", 103);

           s1.display();
           s2.display();
           s3.display();

           Student.showCount();            // 3

           Student.changeCollege("Notre Dame College");
           System.out.println("After the change:");
           s1.display();                   // every object sees the new name
           s2.display();
       }
   }
   ```

   Output
   ```
      Total students: 0
      101 - Rahim - Dhaka College
      102 - Karim - Dhaka College
      103 - Jamal - Dhaka College
      Total students: 3
      After the change:
      101 - Rahim - Notre Dame College
      102 - Karim - Notre Dame College
   ```

   What the program shows
   - `studentCount` is `static`, so all three constructor calls increase the same variable. An instance variable would have given each object its own count of 1.
   - `collegeName` is `static`, so changing it once changes what every object reports.
   - `showCount()` is `static`, so it is called as `Student.showCount()` before any object exists.
   - `name` and `roll` are instance variables, so each object has its own.

   Memory picture
   ```
      ---- Class area (one copy) ----
           collegeName , studentCount

      ---- Heap (one copy per object) ----
           s1 : name="Rahim" , roll=101
           s2 : name="Karim" , roll=102
           s3 : name="Jamal" , roll=103
   ```

   Rules to state
   ```
      A static method can access only STATIC members directly
      'this' and 'super' cannot be used inside a static method
      A static method cannot be OVERRIDDEN, only HIDDEN
      main() is static so the JVM can call it before any object exists
      A STATIC BLOCK runs once, when the class is loaded :

           static { System.out.println("Class loaded"); }

      'static final' makes a constant :  static final double PI = 3.1416;
   ```

7. **Write a java program to counting the vowel and consonant into a given strings.** *[BOF Assistant Programmer 2022 compact it 735 (ET: MIST)]*

   Answer: A `vowel` is one of a, e, i, o, u (in either case); every other alphabetic character is a `consonant`. Digits, spaces and punctuation are neither.

   ```java
   import java.util.Scanner;

   public class VowelConsonant {

       public static void main(String[] args) {

           Scanner sc = new Scanner(System.in);
           System.out.print("Enter a string: ");
           String str = sc.nextLine();

           int vowels = 0, consonants = 0, digits = 0, others = 0;

           // make the comparison case-insensitive
           str = str.toLowerCase();

           for (int i = 0; i < str.length(); i++) {
               char ch = str.charAt(i);

               if (ch >= 'a' && ch <= 'z') {              // it is a letter
                   if (ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u')
                       vowels++;
                   else
                       consonants++;
               }
               else if (ch >= '0' && ch <= '9')
                   digits++;
               else
                   others++;                              // space, punctuation
           }

           System.out.println("Vowels     : " + vowels);
           System.out.println("Consonants : " + consonants);
           System.out.println("Digits     : " + digits);
           System.out.println("Others     : " + others);

           sc.close();
       }
   }
   ```

   Sample run
   ```
      Enter a string: Bangladesh is my country 2024

      Vowels     : 8
      Consonants : 14
      Digits     : 4
      Others     : 4
   ```

   Shorter version using `Character` methods
   ```java
   public class VowelConsonant {
       public static void main(String[] args) {

           String str = "Bangladesh is my country";
           int vowels = 0, consonants = 0;

           for (char ch : str.toLowerCase().toCharArray()) {
               if (Character.isLetter(ch)) {
                   if ("aeiou".indexOf(ch) >= 0) vowels++;
                   else                          consonants++;
               }
           }

           System.out.println("Vowels     : " + vowels);
           System.out.println("Consonants : " + consonants);
       }
   }
   ```
   - `"aeiou".indexOf(ch)` returns -1 when the character is not a vowel, which makes the test a single line.

   Version using a method, so the logic can be reused
   ```java
   public class VowelConsonant {

       static boolean isVowel(char ch) {
           ch = Character.toLowerCase(ch);
           return ch=='a' || ch=='e' || ch=='i' || ch=='o' || ch=='u';
       }

       public static void main(String[] args) {
           String str = "Bangladesh";
           int v = 0, c = 0;

           for (char ch : str.toCharArray()) {
               if (!Character.isLetter(ch)) continue;
               if (isVowel(ch)) v++; else c++;
           }
           System.out.println("Vowels: " + v + ", Consonants: " + c);
       }
   }
   ```

   Points worth noting
   ```
      Convert to lower case FIRST, or 'A' and 'a' will be counted differently
      Check isLetter() before classifying, so digits and spaces are not
           counted as consonants - the commonest mistake in this question
      str.charAt(i) reads one character; str.toCharArray() gives them all
      The loop runs in O(n) time and uses O(1) extra space
   ```

8. **Where will be the most chance of the grabage collector being invoked?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

   Answer: The garbage collector is most likely to be invoked when an object becomes `unreachable` and the JVM is under `memory pressure` — that is, when the heap is nearly full and a new allocation cannot be satisfied.

   The main trigger
   ```
      A new object is allocated, the young generation (Eden space) is FULL,
      and the JVM must free space  ->  a MINOR GC runs.
   ```
   - This is by far the commonest cause. Garbage collection in Java is `allocation-driven`: it happens because memory is needed, not because objects became garbage.

   Situations that make collection likely
   - `An object goes out of scope` — a local variable's object becomes unreachable when the method returns.
   ```java
      void method() {
          Student s = new Student();     // created on the heap
      }                                  // s is now unreachable -> eligible
   ```
   - `A reference is set to null`
   ```java
      Student s = new Student();
      s = null;                          // the object is now eligible
   ```
   - `A reference is reassigned`
   ```java
      Student s = new Student("A");
      s = new Student("B");              // the first object is now unreachable
   ```
   - `An island of isolation` — two objects referring only to each other, with nothing outside referring to either. Both are unreachable, so both are collected. Reference-counting collectors miss this case; Java's reachability-based collector does not.
   - `The heap is nearly full`, which is the actual trigger for the collector to run.
   - `System.gc()` or `Runtime.getRuntime().gc()` is called — but this is only a `request`, and the JVM may ignore it entirely. It is considered bad practice.

   Where in the program it is most likely
   ```
      Inside a loop that creates many short-lived objects :

           for (int i = 0; i < 1000000; i++) {
               String s = new String("temp");    // becomes garbage immediately
           }

      This fills Eden space quickly, so minor collections run repeatedly.
      Short-lived objects are exactly what the generational collector is
      designed for, and collecting them is very cheap.
   ```

   The generational model
   ```
      YOUNG generation : Eden + two Survivor spaces
           Most objects die young, so MINOR GC runs here often and fast.

      OLD generation (tenured)
           Objects that survive several minor collections are promoted here.
           MAJOR / FULL GC runs here rarely and is much slower.
   ```

   What is NOT a trigger
   ```
      An object is NOT collected merely because finalize() exists
      Setting a reference to null does not COLLECT the object; it only makes
           it eligible
      System.gc() does not guarantee collection
      The JVM shutting down does not guarantee finalizers run
   ```

   - The precise answer: the garbage collector is invoked when `an allocation fails because the heap (usually Eden space) is full`. The objects it then removes are those that have become `unreachable` from any live thread — most often short-lived local objects created inside loops.

9. **In Java program. Write the method in given box for the Electric bill calculation if unit is less then 100 then unit rate 4.0 take and after 100-unit rate is 5.50 and reaming unit rate is 6.00. [Bill rate 4.0 if unit<=100, Bill rate 5.50 if (unit>100 && unit<=200), Bill rate 6.00 for remaining units.]** *[BPDB Assistant Engineer (CSE) 2021 compact it 816-817 (ET: BUET)]*

   Answer: The tariff is `slab-wise`: each block of units is charged at its own rate, and only the units above a slab boundary attract the higher rate.
   ```
      First 100 units          : 4.00 taka per unit
      Next 100 units (101-200) : 5.50 taka per unit
      Above 200 units          : 6.00 taka per unit
   ```

   The method
   ```java
   public static double calculateBill(int unit) {

       double bill = 0;

       if (unit <= 100) {
           bill = unit * 4.0;
       }
       else if (unit <= 200) {
           bill = (100 * 4.0)                      // the first 100 units
                + ((unit - 100) * 5.50);           // the rest at 5.50
       }
       else {
           bill = (100 * 4.0)                      // the first 100
                + (100 * 5.50)                     // the next 100
                + ((unit - 200) * 6.00);           // the remainder at 6.00
       }

       return bill;
   }
   ```

   Complete program
   ```java
   import java.util.Scanner;

   public class ElectricBill {

       public static double calculateBill(int unit) {
           double bill;

           if (unit <= 100)
               bill = unit * 4.0;
           else if (unit <= 200)
               bill = (100 * 4.0) + ((unit - 100) * 5.50);
           else
               bill = (100 * 4.0) + (100 * 5.50) + ((unit - 200) * 6.00);

           return bill;
       }

       public static void main(String[] args) {
           Scanner sc = new Scanner(System.in);
           System.out.print("Enter units consumed: ");
           int unit = sc.nextInt();

           if (unit < 0) {
               System.out.println("Units cannot be negative");
           } else {
               System.out.println("Units : " + unit);
               System.out.println("Bill  : " + calculateBill(unit) + " taka");
           }
           sc.close();
       }
   }
   ```

   Worked examples
   ```
      unit = 80    ->  80 x 4.00                              = 320.00 taka

      unit = 150   ->  100 x 4.00  = 400.00
                       50  x 5.50  = 275.00
                                   --------
                                     675.00 taka

      unit = 350   ->  100 x 4.00  = 400.00
                       100 x 5.50  = 550.00
                       150 x 6.00  = 900.00
                                   --------
                                    1850.00 taka
   ```

   Alternative reading — a flat rate for the whole consumption
   - If the tariff means the `entire` consumption is charged at one rate determined by the slab, the method is simpler:
   ```java
   public static double calculateBillFlat(int unit) {
       double rate;
       if (unit <= 100)      rate = 4.00;
       else if (unit <= 200) rate = 5.50;
       else                  rate = 6.00;
       return unit * rate;
   }
   ```
   ```
      unit = 150  ->  150 x 5.50 = 825.00 taka
      unit = 350  ->  350 x 6.00 = 2100.00 taka
   ```
   - The `slab-wise` version is how real electricity tariffs work in Bangladesh, and is the answer normally expected. Stating the assumption is what earns the marks.

   Points to note
   - A flat-rate tariff has a discontinuity at the boundary: 100 units costs 400 taka but 101 units costs 555.50 — a jump of 155 taka for one extra unit. The slab-wise method avoids this, which is exactly why real tariffs use it.
   - Validate the input: negative units are meaningless, and the method should reject them.

10. **C# language এর একটি প্রোগ্রাম লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) A complete C# program demonstrating classes, objects, encapsulation and inheritance.

    ```csharp
    using System;

    namespace BankApplication
    {
        // ---------------- BASE CLASS ----------------
        class Account
        {
            // private fields - encapsulation
            private string accountNumber;
            private string holderName;
            private double balance;

            // constructor
            public Account(string accNo, string name, double opening)
            {
                accountNumber = accNo;
                holderName    = name;
                balance       = (opening > 0) ? opening : 0;
            }

            // property : controlled access to a private field
            public double Balance
            {
                get { return balance; }
                protected set { balance = value; }
            }

            public string AccountNumber { get { return accountNumber; } }

            public void Deposit(double amount)
            {
                if (amount <= 0) {
                    Console.WriteLine("Deposit must be positive");
                    return;
                }
                balance += amount;
                Console.WriteLine($"Deposited {amount:F2}");
            }

            public virtual void Withdraw(double amount)      // virtual
            {
                if (amount > 0 && amount <= balance) {
                    balance -= amount;
                    Console.WriteLine($"Withdrawn {amount:F2}");
                } else {
                    Console.WriteLine("Insufficient balance");
                }
            }

            public virtual double CalculateInterest() { return 0; }

            public virtual void Display()
            {
                Console.WriteLine("--------------------------------");
                Console.WriteLine($"Account : {accountNumber}");
                Console.WriteLine($"Holder  : {holderName}");
                Console.WriteLine($"Balance : {balance:F2}");
            }
        }

        // ---------------- DERIVED CLASS ----------------
        class SavingsAccount : Account
        {
            private double rate;

            public SavingsAccount(string accNo, string name, double opening,
                                  double r = 6.0)
                : base(accNo, name, opening)          // call the base constructor
            {
                rate = r;
            }

            public override double CalculateInterest()
            {
                return Balance * rate / 100;
            }

            public override void Display()
            {
                base.Display();                       // reuse the base version
                Console.WriteLine($"Type    : Savings");
                Console.WriteLine($"Interest: {CalculateInterest():F2}");
            }
        }

        // ---------------- MAIN ----------------
        class Program
        {
            static void Main(string[] args)
            {
                Console.Write("Enter account holder name: ");
                string name = Console.ReadLine();

                Console.Write("Enter opening balance: ");
                double opening = Convert.ToDouble(Console.ReadLine());

                SavingsAccount acc = new SavingsAccount("SB1001", name, opening);

                acc.Deposit(5000);
                acc.Withdraw(2000);
                acc.Withdraw(1000000);        // rejected
                acc.Display();

                Console.ReadKey();
            }
        }
    }
    ```

    Sample run
    ```
       Enter account holder name: Rahim Uddin
       Enter opening balance: 10000

       Deposited 5000.00
       Withdrawn 2000.00
       Insufficient balance
       --------------------------------
       Account : SB1001
       Holder  : Rahim Uddin
       Balance : 13000.00
       Type    : Savings
       Interest: 780.00
    ```

    A shorter program, if only the basics are wanted
    ```csharp
    using System;

    class Program
    {
        static void Main()
        {
            Console.Write("Enter first number : ");
            int a = Convert.ToInt32(Console.ReadLine());

            Console.Write("Enter second number: ");
            int b = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine($"Sum        = {a + b}");
            Console.WriteLine($"Difference = {a - b}");
            Console.WriteLine($"Product    = {a * b}");

            if (b != 0)
                Console.WriteLine($"Quotient   = {(double)a / b:F2}");
            else
                Console.WriteLine("Division by zero is not allowed");

            Console.ReadKey();
        }
    }
    ```

    C# features worth pointing out
    ```
       using System;        imports the base namespace
       namespace            groups related classes
       Console.WriteLine    output;  Console.ReadLine  input
       $"{...}"             string interpolation, like printf
       :F2                  format to two decimal places
       Property             get/set accessors replace Java's getX()/setX()
       virtual / override   explicit keywords - unlike Java, C# requires
                            'virtual' in the base class, exactly like C++
       base                 refers to the superclass, like Java's 'super'
       : base(...)          calls the base constructor
    ```
    - C# is developed by Microsoft and runs on the `.NET` platform. It is very close to Java in design, with properties, `virtual`/`override` and value-type `struct` as its main differences.

11. **Write java program for calculate electricity bill using class and object.** *[Sundharban Gas Assistant Programmer 2020 compact it 1047-1048 (ET: N/A)]*

    Answer: The program uses a `class` to hold the customer's data and the billing logic, and an `object` for each customer.
    ```
       Slab tariff :  first 100 units       -> 4.00 taka per unit
                      next 100 (101-200)    -> 5.50 taka per unit
                      above 200             -> 6.00 taka per unit
    ```

    ```java
    import java.util.Scanner;

    class ElectricityBill {

        // ---- private data members : encapsulation ----
        private String customerName;
        private String meterNumber;
        private int    unitsConsumed;
        private double billAmount;

        // ---- constructor ----
        public ElectricityBill(String name, String meter, int units) {
            this.customerName  = name;
            this.meterNumber   = meter;
            this.unitsConsumed = (units > 0) ? units : 0;
        }

        // ---- slab-wise bill calculation ----
        public void calculateBill() {
            int units = unitsConsumed;

            if (units <= 100)
                billAmount = units * 4.0;
            else if (units <= 200)
                billAmount = (100 * 4.0) + ((units - 100) * 5.50);
            else
                billAmount = (100 * 4.0) + (100 * 5.50) + ((units - 200) * 6.00);
        }

        // ---- add the service charge and VAT ----
        public double totalPayable() {
            double serviceCharge = 20.0;
            double vat = billAmount * 0.05;          // 5 % VAT
            return billAmount + serviceCharge + vat;
        }

        // ---- display the bill ----
        public void display() {
            System.out.println("========================================");
            System.out.println("Customer      : " + customerName);
            System.out.println("Meter Number  : " + meterNumber);
            System.out.println("Units         : " + unitsConsumed);
            System.out.println("Energy Charge : " + billAmount);
            System.out.println("Service Charge: 20.0");
            System.out.printf ("VAT (5%%)      : %.2f%n", billAmount * 0.05);
            System.out.printf ("Total Payable : %.2f taka%n", totalPayable());
            System.out.println("========================================");
        }

        public double getBillAmount() { return billAmount; }
    }

    public class Main {
        public static void main(String[] args) {

            Scanner sc = new Scanner(System.in);

            System.out.print("Enter customer name : ");
            String name = sc.nextLine();

            System.out.print("Enter meter number  : ");
            String meter = sc.nextLine();

            System.out.print("Enter units consumed: ");
            int units = sc.nextInt();

            // create the OBJECT
            ElectricityBill bill = new ElectricityBill(name, meter, units);

            bill.calculateBill();
            bill.display();

            sc.close();
        }
    }
    ```

    Sample run
    ```
       Enter customer name : Rahim Uddin
       Enter meter number  : DESCO-45231
       Enter units consumed: 350

       ========================================
       Customer      : Rahim Uddin
       Meter Number  : DESCO-45231
       Units         : 350
       Energy Charge : 1850.0
       Service Charge: 20.0
       VAT (5%)      : 92.50
       Total Payable : 1962.50 taka
       ========================================
    ```

    Working of the slab calculation for 350 units
    ```
       First 100 units  : 100 x 4.00 =  400.00
       Next 100 units   : 100 x 5.50 =  550.00
       Remaining 150    : 150 x 6.00 =  900.00
                                      ---------
       Energy charge                  = 1850.00
       Service charge                 =   20.00
       VAT 5 % of 1850                =   92.50
                                      ---------
       Total payable                  = 1962.50 taka
    ```

    Handling several customers with an array of objects
    ```java
    ElectricityBill[] customers = {
        new ElectricityBill("Rahim", "M-101", 80),
        new ElectricityBill("Karim", "M-102", 150),
        new ElectricityBill("Jamal", "M-103", 350)
    };

    double total = 0;
    for (ElectricityBill c : customers) {
        c.calculateBill();
        c.display();
        total += c.getBillAmount();
    }
    System.out.println("Total revenue: " + total);
    ```

    OOP concepts the program uses
    ```
       CLASS         : ElectricityBill is the blueprint
       OBJECT        : each customer is an instance
       ENCAPSULATION : the data members are private; all access is through
                       public methods, so units can never be set negative
       CONSTRUCTOR   : initialises the object at creation
       METHODS       : calculateBill(), totalPayable() and display() keep
                       the logic beside the data it works on
    ```

12. **What are the difference among JDK, JRE and JVM?** *[Islami Bank Bangladesh Limited Officer (Software Engineer) 2019 compact it 1098 (ET: N/A)]*

    Answer: The three are separate pieces of the Java platform, and they nest inside one another.
    ```
       +---------------------------------------------------+
       |  JDK  (Java Development Kit)                      |
       |   compiler (javac), debugger, jar, javadoc ...    |
       |   +-------------------------------------------+   |
       |   |  JRE  (Java Runtime Environment)          |   |
       |   |   class libraries (rt.jar), property files|   |
       |   |   +-----------------------------------+   |   |
       |   |   |  JVM  (Java Virtual Machine)      |   |   |
       |   |   |   class loader, bytecode verifier,|   |   |
       |   |   |   interpreter, JIT, GC            |   |   |
       |   |   +-----------------------------------+   |   |
       |   +-------------------------------------------+   |
       +---------------------------------------------------+

       JDK = JRE + development tools
       JRE = JVM + class libraries
    ```

    JVM — Java Virtual Machine
    - An `abstract machine` that actually `executes` the bytecode. It is a `specification`, and different vendors provide different implementations (HotSpot, OpenJ9).
    - It is `platform dependent` — a separate JVM exists for Windows, Linux and macOS — and this is exactly what makes `Java itself platform independent`.
    ```
       Main components :
          Class loader     : loads .class files into memory
          Bytecode verifier: checks the code is safe and well formed
          Runtime areas    : method area, heap, stacks, PC register
          Execution engine : interpreter + JIT compiler
          Garbage collector: reclaims unreachable objects
    ```
    - It cannot compile source code and cannot run a program on its own; it needs the libraries.

    JRE — Java Runtime Environment
    - The `JVM plus the standard class libraries` and supporting files needed to `run` a Java application.
    - It is what an `end user` installs to run a Java program. It cannot compile anything.
    ```
       JRE = JVM + java.lang, java.util, java.io, java.net ... + property files
    ```

    JDK — Java Development Kit
    - The `JRE plus the development tools` needed to `write and build` Java programs.
    - It is what a `developer` installs.
    ```
       Tools included :
          javac     : the compiler, .java -> .class bytecode
          java      : launcher, runs a program
          javadoc   : generates documentation
          jar       : packages classes into a .jar archive
          jdb       : debugger
          javap     : disassembler
    ```

    Comparison

    | Point | JDK | JRE | JVM |
    |---|---|---|---|
    | Full form | Java Development Kit | Java Runtime Environment | Java Virtual Machine |
    | Contains | JRE + development tools | JVM + class libraries | Class loader, verifier, engine, GC |
    | Purpose | Develop and run | Run only | Execute bytecode |
    | Can compile | `Yes` (javac) | No | No |
    | Can run a program | Yes | Yes | Only with libraries |
    | Installed by | Developers | End users | Comes inside the JRE |
    | Platform dependent | Yes | Yes | Yes |
    | Physical or abstract | Physical (a set of files) | Physical | `Abstract` — a specification |

    How a program flows through them
    ```
       Hello.java
          |  javac   (JDK tool)
          v
       Hello.class  (bytecode - platform INDEPENDENT)
          |  java    (JRE launcher)
          v
       JVM : class loader -> verifier -> interpreter / JIT -> machine code
          |
          v
       Output
    ```

    - The key idea: bytecode is `written once` and runs on `any` JVM. The platform difference is absorbed by the JVM, not by the program — which is what "write once, run anywhere" means.
    - From Java 11 onward Oracle no longer ships a separate JRE; the JDK is the single distribution, and `jlink` builds a trimmed runtime when one is needed.

13. **(c) Why Java is called platform independent language?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

    Answer: Java is called `platform independent` because a Java program is compiled once into `bytecode`, and that same bytecode runs unchanged on any operating system that has a `JVM`.

    - The slogan is `WORA` — Write Once, Run Anywhere.

    How it works
    ```
       Hello.java          (source code)
            |
            |  javac  - the Java compiler
            v
       Hello.class         (BYTECODE - platform INDEPENDENT)
            |
            +--------------+--------------+
            |              |              |
         JVM for        JVM for        JVM for
         Windows         Linux          macOS
            |              |              |
            v              v              v
       Windows        Linux          macOS
       machine code   machine code   machine code
    ```
    - The `same Hello.class` file is copied to any machine and runs there. Nothing is recompiled.

    The two-stage compilation
    ```
       Stage 1 : javac converts source to BYTECODE
                 - an intermediate instruction set for a virtual machine
                 - not tied to any real processor

       Stage 2 : the JVM converts bytecode to the NATIVE machine code of
                 whatever processor it is running on, by interpreting it and
                 by compiling the hot paths with the JIT compiler
    ```

    The key point that examiners look for
    ```
       JAVA is platform independent.
       The JVM is platform DEPENDENT.

       A different JVM is written for each operating system and processor.
       That JVM absorbs all the differences, so the program does not have to.
    ```
    - This is the opposite of C or C++, where the compiler produces machine code for one specific platform, and the program must be `recompiled` — often with source changes — for every other one.
    ```
       C program   : source -> Windows .exe   (runs only on Windows)
                     source -> Linux binary   (must be recompiled)

       Java program: source -> ONE .class file (runs on all of them)
    ```

    What else supports the independence
    - `Fixed data type sizes.` In Java an `int` is always 32 bits and a `char` always 16 bits, on every platform. In C the size of `int` varies with the compiler and machine.
    - `Standard class libraries.` `java.io`, `java.net` and the rest behave identically everywhere, so file and network code needs no changes.
    - `No pointers and no direct memory access`, so a program cannot depend on a particular memory layout.
    - `Unicode` for characters, so text behaves the same in every locale.

    Limits worth stating honestly
    ```
       The JVM itself must be installed, and it is platform specific.
       Native code called through JNI is NOT portable.
       File paths, line separators and GUI look-and-feel still differ, so
            File.separator and System.lineSeparator() must be used rather
            than hard-coded "\\" or "\n".
       Performance depends on the JVM implementation.
    ```

    - So the accurate statement is: Java achieves platform independence by `moving the platform-specific work out of the program and into the JVM`. The program is portable; the runtime is not.

14. **Suppose you've a method name “totalAmount” and there three properties (transactionName, transactionType, amount). Write down the full code using JAVA where totalAmount method return total balance after debit or credited.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

    Answer: The class holds the three properties, and `totalAmount` returns the computed value.

    ```java
    import java.util.ArrayList;
    import java.util.List;

    class Transaction {

        // ---- the three properties ----
        private String transactionName;
        private String transactionType;      // "credit" or "debit"
        private double amount;

        // ---- constructor ----
        public Transaction(String transactionName, String transactionType,
                           double amount) {
            this.transactionName = transactionName;
            this.transactionType = transactionType;
            this.amount = amount;
        }

        // ---- getters ----
        public String getTransactionName() { return transactionName; }
        public String getTransactionType() { return transactionType; }
        public double getAmount()          { return amount; }

        // ---- setters ----
        public void setAmount(double amount) {
            if (amount >= 0) this.amount = amount;
        }

        // ---- the method that RETURNS a value ----
        public double totalAmount() {
            if (transactionType.equalsIgnoreCase("credit"))
                return amount;               // money in  -> positive
            else
                return -amount;              // money out -> negative
        }

        public void display() {
            System.out.printf("%-15s %-10s %10.2f%n",
                              transactionName, transactionType, amount);
        }
    }

    public class Main {

        // a static version that totals a whole list
        public static double totalAmount(List<Transaction> list) {
            double total = 0;
            for (Transaction t : list)
                total += t.totalAmount();
            return total;                    // returns the net total
        }

        public static void main(String[] args) {

            List<Transaction> transactions = new ArrayList<>();
            transactions.add(new Transaction("Salary",   "credit", 50000));
            transactions.add(new Transaction("Rent",     "debit",  15000));
            transactions.add(new Transaction("Bonus",    "credit", 10000));
            transactions.add(new Transaction("Utility",  "debit",   3500));

            System.out.printf("%-15s %-10s %10s%n", "NAME", "TYPE", "AMOUNT");
            System.out.println("-------------------------------------");
            for (Transaction t : transactions)
                t.display();
            System.out.println("-------------------------------------");

            double net = totalAmount(transactions);
            System.out.printf("Net total : %.2f taka%n", net);
        }
    }
    ```

    Output
    ```
       NAME            TYPE           AMOUNT
       -------------------------------------
       Salary          credit       50000.00
       Rent            debit        15000.00
       Bonus           credit       10000.00
       Utility         debit         3500.00
       -------------------------------------
       Net total : 41500.00 taka
    ```

    Working
    ```
       Salary   credit  +50000
       Rent     debit   -15000
       Bonus    credit  +10000
       Utility  debit    -3500
                        -------
       Net total        +41500
    ```

    Simpler version, if `totalAmount` should just return the amount
    ```java
    class Transaction {
        private String transactionName;
        private String transactionType;
        private double amount;

        public Transaction(String name, String type, double amount) {
            this.transactionName = name;
            this.transactionType = type;
            this.amount = amount;
        }

        public double totalAmount() {
            return amount;               // returns the value
        }
    }

    public class Main {
        public static void main(String[] args) {
            Transaction t = new Transaction("Salary", "credit", 50000);
            System.out.println("Total: " + t.totalAmount());   // 50000.0
        }
    }
    ```

    Points to note
    ```
       The return type is 'double', not 'void', so the method can return a value
       Every path through the method must return - the if/else above does
       The properties are PRIVATE with public getters : encapsulation
       equalsIgnoreCase() is used, not ==, because Strings must be compared
            by VALUE and the type may be typed in any case
       printf with %-15s and %10.2f aligns the output into columns
    ```

15. **Write the full form of following topics:** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*
   i) JAR
   ii) JRE
   iii) WAR
   iv) JDK

    Answer: The four full forms.
    ```
       i)   JAR  =  Java ARchive
       ii)  JRE  =  Java Runtime Environment
       iii) WAR  =  Web Application aRchive
       iv)  JDK  =  Java Development Kit
    ```

    i) JAR — Java Archive
    - A single compressed file, in ZIP format, that packages `.class` files, images, configuration files and a `MANIFEST.MF` together.
    - Purpose: distribute a whole library or application as one file, with compression and optional digital signing.
    ```
       MyApp.jar
          +-- META-INF/MANIFEST.MF        (declares the Main-Class)
          +-- com/example/Main.class
          +-- com/example/Helper.class
          +-- resources/logo.png
    ```
    ```bash
       jar cf MyApp.jar *.class          # create
       java -jar MyApp.jar               # run an executable jar
    ```

    ii) JRE — Java Runtime Environment
    - The `JVM plus the standard class libraries` needed to `run` a Java program.
    - Installed by an `end user`. It cannot compile source code.
    ```
       JRE = JVM + java.lang, java.util, java.io, java.net ...
    ```

    iii) WAR — Web Application Archive
    - A JAR file with a fixed internal structure, holding a complete `web application`: servlets, JSPs, HTML, CSS, JavaScript and their configuration.
    - Deployed to a servlet container such as `Tomcat`, `JBoss` or `WebLogic`.
    ```
       MyWeb.war
          +-- index.html , style.css
          +-- WEB-INF/
                 +-- web.xml              (deployment descriptor)
                 +-- classes/             (compiled servlets)
                 +-- lib/                 (dependency jar files)
    ```
    - The related `EAR` (Enterprise Archive) packages several WAR and JAR modules into one enterprise application.

    iv) JDK — Java Development Kit
    - The `JRE plus the development tools` needed to `write and build` Java programs.
    - Installed by a `developer`.
    ```
       Tools : javac (compiler) , java (launcher) , javadoc , jar , jdb , javap
    ```

    How they relate
    ```
       JDK = JRE + development tools
       JRE = JVM + class libraries

       JAR = a package of classes and resources
       WAR = a JAR with the standard web-application layout
       EAR = a package of WAR and JAR modules
    ```

    Comparison of the archive types

    | Point | JAR | WAR |
    |---|---|---|
    | Full form | Java Archive | Web Application Archive |
    | Contains | Classes, resources, manifest | Servlets, JSP, HTML, CSS, `WEB-INF` |
    | Structure | Free | Fixed — `WEB-INF` is required |
    | Deployed to | Any JVM | A servlet container (Tomcat, JBoss) |
    | Runs standalone | Yes, with `Main-Class` | No — needs a web server |
    | Used for | Libraries and desktop applications | Web applications |

16. **Write a java program using 2D array and array output will be-** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1191 (ET: N/A)]*
```text
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

    Answer: The required output is a `right triangle` of numbers, in which row `i` prints the numbers 1 to `i`.
    ```
       1
       1 2
       1 2 3
       1 2 3 4
       1 2 3 4 5
    ```

    Program using a 2-D array
    ```java
    public class TrianglePattern {

        public static void main(String[] args) {

            int n = 5;

            // a JAGGED array : row i has i+1 columns
            int[][] arr = new int[n][];

            // ---- fill the array ----
            for (int i = 0; i < n; i++) {
                arr[i] = new int[i + 1];              // row i has i+1 elements
                for (int j = 0; j <= i; j++) {
                    arr[i][j] = j + 1;                // values 1, 2, 3, ...
                }
            }

            // ---- print the array ----
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < arr[i].length; j++) {
                    System.out.print(arr[i][j] + " ");
                }
                System.out.println();
            }
        }
    }
    ```

    Output
    ```
       1
       1 2
       1 2 3
       1 2 3 4
       1 2 3 4 5
    ```

    How it works
    ```
       i = 0 : arr[0] has 1 element  -> 1
       i = 1 : arr[1] has 2 elements -> 1 2
       i = 2 : arr[2] has 3 elements -> 1 2 3
       i = 3 : arr[3] has 4 elements -> 1 2 3 4
       i = 4 : arr[4] has 5 elements -> 1 2 3 4 5
    ```
    - `int[][] arr = new int[n][]` creates a `jagged` array — the number of rows is fixed but each row's length is decided separately. This matches the triangle exactly, with no wasted memory.

    Version using a rectangular 2-D array
    ```java
    public class TrianglePattern {
        public static void main(String[] args) {

            int n = 5;
            int[][] arr = new int[n][n];              // full 5 x 5 array

            for (int i = 0; i < n; i++)
                for (int j = 0; j <= i; j++)
                    arr[i][j] = j + 1;                // upper cells stay 0

            for (int i = 0; i < n; i++) {
                for (int j = 0; j <= i; j++)          // print only up to j = i
                    System.out.print(arr[i][j] + " ");
                System.out.println();
            }
        }
    }
    ```
    - This wastes the cells above the diagonal, which stay 0, but it is simpler to write.

    Version taking the size from the user
    ```java
    import java.util.Scanner;

    public class TrianglePattern {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
            System.out.print("Enter number of rows: ");
            int n = sc.nextInt();

            int[][] arr = new int[n][];
            for (int i = 0; i < n; i++) {
                arr[i] = new int[i + 1];
                for (int j = 0; j <= i; j++) arr[i][j] = j + 1;
            }

            for (int[] row : arr) {
                for (int value : row) System.out.print(value + " ");
                System.out.println();
            }
            sc.close();
        }
    }
    ```

    Related patterns produced by changing one line
    ```
       arr[i][j] = i + 1;      ->   1
                                    2 2
                                    3 3 3
                                    4 4 4 4

       arr[i][j] = 1;          ->   1
                                    1 1
                                    1 1 1
    ```

    Points worth noting
    ```
       A jagged array uses exactly n(n+1)/2 cells; a rectangular one uses n^2
       The inner loop condition j <= i is what makes the triangle
       arr[i].length gives the length of that particular row
       The enhanced for loop (for (int[] row : arr)) is the cleanest way
            to walk a jagged array
    ```

17. **Write simple Java program to convert string into camel case and display camel case string.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1191-1192 (ET: N/A)]*

    Answer: `Camel case` writes the first word in lower case and capitalises the first letter of every following word, with all spaces removed.
    ```
       "hello world program"  ->  "helloWorldProgram"        lower camel case
       "hello world program"  ->  "HelloWorldProgram"        upper camel case (Pascal)
    ```

    Program
    ```java
    import java.util.Scanner;

    public class CamelCase {

        public static String toCamelCase(String str) {

            if (str == null || str.isEmpty()) return str;

            String[] words = str.trim().toLowerCase().split("\\s+");
            StringBuilder result = new StringBuilder();

            // the FIRST word stays entirely in lower case
            result.append(words[0]);

            // every later word gets its first letter capitalised
            for (int i = 1; i < words.length; i++) {
                result.append(Character.toUpperCase(words[i].charAt(0)));
                result.append(words[i].substring(1));
            }

            return result.toString();
        }

        public static void main(String[] args) {

            Scanner sc = new Scanner(System.in);
            System.out.print("Enter a string: ");
            String input = sc.nextLine();

            System.out.println("Original  : " + input);
            System.out.println("CamelCase : " + toCamelCase(input));

            sc.close();
        }
    }
    ```

    Sample run
    ```
       Enter a string: bangladesh water development board

       Original  : bangladesh water development board
       CamelCase : bangladeshWaterDevelopmentBoard
    ```

    How it works
    ```
       1. trim()        removes leading and trailing spaces
       2. toLowerCase() normalises everything, so "HELLO World" behaves
                        the same as "hello world"
       3. split("\\s+") splits on ONE OR MORE whitespace characters, so
                        multiple spaces and tabs are handled correctly
       4. The first word is appended unchanged.
       5. For each later word, its first character is upper-cased and the
          rest appended with substring(1).
    ```

    Step by step for "hello world program"
    ```
       words = ["hello", "world", "program"]

       result = "hello"
       i = 1 : 'w' -> 'W' , + "orld"    -> "helloWorld"
       i = 2 : 'p' -> 'P' , + "rogram"  -> "helloWorldProgram"
    ```

    Upper camel case (Pascal case) — capitalise the first word too
    ```java
    public static String toPascalCase(String str) {
        String[] words = str.trim().toLowerCase().split("\\s+");
        StringBuilder result = new StringBuilder();

        for (String w : words) {
            result.append(Character.toUpperCase(w.charAt(0)));
            result.append(w.substring(1));
        }
        return result.toString();
    }
    ```
    ```
       "hello world program"  ->  "HelloWorldProgram"
    ```

    Version handling other separators as well
    ```java
       String[] words = str.trim().toLowerCase().split("[\\s_\\-]+");
    ```
    - This also splits on underscores and hyphens, so `snake_case` and `kebab-case` convert too.

    Points worth noting
    ```
       Use StringBuilder, not repeated string concatenation. In a loop,
            s = s + x creates a new String object every time - O(n^2) work.

       split("\\s+") rather than split(" ") : the first handles multiple
            consecutive spaces, the second produces empty strings.

       Guard against an empty input, or charAt(0) throws
            StringIndexOutOfBoundsException.

       Java's own naming convention IS camel case for variables and methods
            (totalAmount, calculateBill) and Pascal case for class names
            (ElectricityBill), which is why this conversion is a common
            interview question.
    ```

18. **Discus architecture of Java virtual machine.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1218-1219 (ET: N/A)]*

    Answer: The `JVM (Java Virtual Machine)` is an abstract machine that loads, verifies and executes Java bytecode. It is a `specification`, implemented by HotSpot, OpenJ9 and others.

    Architecture
    ```mermaid
    flowchart TB
        A[.class bytecode] --> B[Class Loader Subsystem]
        B --> C[Runtime Data Areas]
        C --> D[Execution Engine]
        D --> E[Native Method Interface JNI]
        E --> F[Native Method Libraries]
    ```
    ```
       +---------------------------------------------------------+
       |                    CLASS LOADER SUBSYSTEM               |
       |     Loading  ->  Linking  ->  Initialization            |
       +---------------------------------------------------------+
                                |
       +---------------------------------------------------------+
       |                   RUNTIME DATA AREAS                    |
       |  +-------------+  +--------+  +----------------------+  |
       |  | Method Area |  |  Heap  |  |  JVM Stacks          |  |
       |  |  (shared)   |  |(shared)|  |  (per thread)        |  |
       |  +-------------+  +--------+  +----------------------+  |
       |  +----------------------+  +------------------------+   |
       |  | PC Register(per thr) |  | Native Method Stacks   |   |
       |  +----------------------+  +------------------------+   |
       +---------------------------------------------------------+
                                |
       +---------------------------------------------------------+
       |                    EXECUTION ENGINE                     |
       |   Interpreter  |  JIT Compiler  |  Garbage Collector    |
       +---------------------------------------------------------+
                                |
       +---------------------------------------------------------+
       |     JNI  ->  Native Method Libraries (.dll / .so)       |
       +---------------------------------------------------------+
    ```

    1. Class Loader Subsystem

    `Loading` — reads the `.class` file and creates a `Class` object in the method area. Three built-in loaders work by delegation:
    ```
       Bootstrap loader  : loads the core API (java.lang, java.util) from rt.jar
       Extension loader  : loads from the ext directory
       Application loader: loads the application's own classes from the classpath

       Delegation : a request goes UP to the parent first, so a user class
                    cannot replace java.lang.String
    ```

    `Linking` — three steps
    ```
       Verification : the bytecode verifier checks the code is well formed and
                      safe - no stack overflow, no illegal type conversion.
                      This is the heart of Java's security.
       Preparation  : static variables are allocated and set to default values
       Resolution   : symbolic references are replaced by direct references
    ```

    `Initialization` — static variables get their real values and `static` blocks run.

    2. Runtime Data Areas
    ```
       METHOD AREA (shared by all threads)
            Class-level data : the runtime constant pool, field and method
            data, the code of methods, and static variables.
            Called METASPACE from Java 8 onward, and it lives in native memory.

       HEAP (shared by all threads)
            All OBJECTS and ARRAYS. This is what the garbage collector manages.
            Divided into Young (Eden + 2 Survivor spaces) and Old generations.
            Throws OutOfMemoryError when exhausted.

       JVM STACK (one per thread)
            One FRAME per method call, holding the local variables, the
            operand stack and a reference to the constant pool.
            The frame is popped when the method returns.
            Throws StackOverflowError on unbounded recursion.

       PC REGISTER (one per thread)
            Holds the address of the instruction currently executing.

       NATIVE METHOD STACK (one per thread)
            For methods written in C or C++ and called through JNI.
    ```

    3. Execution Engine
    ```
       INTERPRETER
            Reads and executes bytecode one instruction at a time.
            Starts immediately, but is slow for code that repeats.

       JIT COMPILER (Just-In-Time)
            Detects HOT SPOTS - methods and loops executed many times - and
            compiles them to native machine code, which is then cached and
            reused. This is what gives Java near-native speed.
            Includes the intermediate code generator, code optimiser and
            the target code generator, plus a profiler to find the hot spots.

       GARBAGE COLLECTOR
            Reclaims objects on the heap that are no longer REACHABLE.
            Generational : minor GC on the young generation is frequent and
            cheap; major/full GC on the old generation is rare and costly.
            Collectors : Serial, Parallel, CMS, G1, ZGC.
    ```

    4. Java Native Interface (JNI) and native libraries
    - The bridge that lets Java call functions written in C or C++, and lets native code call back into Java. Used for hardware access and for parts of the standard library itself.

    How a program flows through it
    ```
       Hello.java --javac--> Hello.class
            |
            v
       Class loader : load -> verify -> prepare -> resolve -> initialise
            |
            v
       Runtime data areas : the class goes to the method area,
                            objects to the heap, the call to a stack frame
            |
            v
       Execution engine : interpret, JIT-compile the hot paths, collect garbage
            |
            v
       Output
    ```

    - The essential point: `bytecode is platform independent, the JVM is platform dependent`. A separate JVM implementation exists for each operating system, and it absorbs every platform difference so the program need not.

## Class Design & Object-Oriented Modeling (11)

1. **Suppose we want to develop software for a graphic package and we are given the task to implement circle class. The circle class has to be translatable from its origin. And it should also be able to give perimeter and area of the circle. Identify the data and method requirements for the class and give the data flow of translation method.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 425 (ET: BIBM)]*

   Answer: Data requirements (attributes)
   ```
      double x       : the x-coordinate of the centre
      double y       : the y-coordinate of the centre
      double radius  : the radius of the circle

      static final double PI = 3.14159   (a shared constant)
   ```
   - The centre is needed because the circle must be `translatable`; the radius because it must give area and perimeter. Nothing else is required.

   Method requirements
   ```
      Circle(x, y, radius)          constructor - create and initialise
      translate(dx, dy)             move the circle by dx and dy
      double area()                 PI x r^2
      double perimeter()            2 x PI x r
      getX() , getY() , getRadius() accessors
      setRadius(r)                  mutator, with validation
      display()                     show the current state
   ```

   Implementation
   ```java
   class Circle {

       // ---- data members ----
       private double x;
       private double y;
       private double radius;
       private static final double PI = 3.14159;

       // ---- constructor ----
       public Circle(double x, double y, double radius) {
           this.x = x;
           this.y = y;
           this.radius = (radius > 0) ? radius : 1;
       }

       // ---- TRANSLATION : move the centre, radius unchanged ----
       public void translate(double dx, double dy) {
           this.x = this.x + dx;
           this.y = this.y + dy;
       }

       // ---- area and perimeter ----
       public double area()      { return PI * radius * radius; }
       public double perimeter() { return 2 * PI * radius; }

       // ---- accessors ----
       public double getX()      { return x; }
       public double getY()      { return y; }
       public double getRadius() { return radius; }

       public void setRadius(double r) {
           if (r > 0) this.radius = r;
       }

       public void display() {
           System.out.printf("Centre (%.1f, %.1f)  radius %.1f%n", x, y, radius);
           System.out.printf("Area %.2f   Perimeter %.2f%n", area(), perimeter());
       }
   }

   public class Main {
       public static void main(String[] args) {
           Circle c = new Circle(0, 0, 5);
           c.display();

           c.translate(3, 4);          // move 3 right and 4 up
           System.out.println("After translation by (3, 4):");
           c.display();
       }
   }
   ```

   Output
   ```
      Centre (0.0, 0.0)  radius 5.0
      Area 78.54   Perimeter 31.42
      After translation by (3, 4):
      Centre (3.0, 4.0)  radius 5.0
      Area 78.54   Perimeter 31.42
   ```
   - Note that area and perimeter are unchanged. `Translation moves a shape without changing its size` — that is exactly what makes it a translation rather than a scaling.

   Data flow of the translate method
   ```mermaid
   flowchart LR
       A[Caller supplies dx, dy] --> B[translate dx, dy]
       B --> C[read current x, y]
       C --> D[x_new = x + dx<br/>y_new = y + dy]
       D --> E[write back to x, y]
       E --> F[radius UNCHANGED]
   ```
   ```
      INPUT                PROCESS                    OUTPUT / STATE CHANGE
      -----                -------                    ---------------------
      dx, dy      -->   read current x, y      -->    x = x + dx
      (parameters)      compute x + dx                y = y + dy
                        compute y + dy                radius unchanged
                                                      area unchanged
                                                      perimeter unchanged
   ```

   Worked trace
   ```
      Before : x = 0 , y = 0 , radius = 5
      Call   : translate(3, 4)

           x = 0 + 3 = 3
           y = 0 + 4 = 4

      After  : x = 3 , y = 4 , radius = 5
   ```

   Design points worth stating
   - The data members are `private`, so the circle cannot be given a negative radius from outside — encapsulation.
   - `area()` and `perimeter()` are `computed on demand` rather than stored. Storing them would create a second copy of the same information, which could fall out of step when the radius changes.
   - `PI` is `static final`, so there is one shared copy and it cannot be altered.
   - If the package needs many shapes, `Circle` should extend an abstract `Shape` class declaring `area()`, `perimeter()` and `translate()`, so that all shapes can be handled polymorphically.

2. **What are the built in classes?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer: `Built-in classes` are the ready-made classes supplied with the language in its standard library. They are already written, tested and optimised, so a programmer uses them instead of writing the same code again.

   - In Java they are organised into `packages` and shipped in the JDK.

   Main built-in packages and their classes

   `java.lang` — imported automatically, no `import` needed
   ```
      Object       the root of every class hierarchy
      String       immutable text
      StringBuilder / StringBuffer   mutable text
      Math         sqrt, pow, abs, max, min, random
      System       in, out, err, currentTimeMillis, exit
      Thread       threads
      Exception , RuntimeException , Throwable
      Wrapper classes : Integer, Double, Float, Long, Short,
                        Byte, Character, Boolean
   ```

   `java.util` — collections and utilities
   ```
      ArrayList , LinkedList , Vector , Stack
      HashMap , TreeMap , LinkedHashMap , Hashtable
      HashSet , TreeSet , LinkedHashSet
      Scanner      keyboard input
      Arrays       sort, search, fill, copy
      Collections  sort, reverse, shuffle
      Date , Calendar , Random , Optional
   ```

   `java.io` and `java.nio` — input and output
   ```
      File , FileReader , FileWriter
      BufferedReader , BufferedWriter
      InputStream , OutputStream
      FileInputStream , FileOutputStream
      PrintWriter , ObjectInputStream
   ```

   `java.net` — networking
   ```
      Socket , ServerSocket , URL , URLConnection , InetAddress
   ```

   `java.sql` — database access
   ```
      Connection , Statement , PreparedStatement , ResultSet , DriverManager
   ```

   `java.time` — modern date and time (Java 8 onward)
   ```
      LocalDate , LocalTime , LocalDateTime , Duration , Period
   ```

   Others
   ```
      java.awt , javax.swing , javafx    graphical user interfaces
      java.text                          formatting numbers and dates
      java.security                      cryptography
   ```

   Example using several of them
   ```java
   import java.util.*;

   public class Demo {
       public static void main(String[] args) {

           String s = "Bangladesh";                 // java.lang.String
           System.out.println(s.toUpperCase());     // BANGLADESH
           System.out.println(s.length());          // 10

           System.out.println(Math.sqrt(25));       // java.lang.Math -> 5.0
           System.out.println(Math.max(10, 20));    // 20

           ArrayList<String> list = new ArrayList<>();   // java.util
           list.add("Dhaka");
           list.add("Chattogram");
           Collections.sort(list);
           System.out.println(list);                // [Chattogram, Dhaka]

           Scanner sc = new Scanner(System.in);     // java.util.Scanner
           // int n = sc.nextInt();

           int x = Integer.parseInt("123");         // wrapper class
           System.out.println(x + 1);               // 124
       }
   }
   ```

   Why they matter
   ```
      No need to reinvent common data structures and algorithms
      Already TESTED and OPTIMISED by the platform's own engineers
      STANDARD, so any Java developer recognises them immediately
      Portable - they behave identically on every platform
   ```

   - The corresponding term in C++ is the `Standard Template Library (STL)`, with `vector`, `map`, `set`, `string`, `iostream` and the algorithm header. In C#, the `.NET Base Class Library` plays the same role.

3. **অথবা, (ক) উদাহরণসহ Class এবং Object এর মধ্যে পার্থক্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 602 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Class
   - A `class` is a `blueprint` or template that defines what data an object will hold and what it will be able to do. It is a `logical` entity — writing a class allocates no memory for data.
   ```java
   class Student {
       String name;                    // attribute (what it HAS)
       int    roll;
       double cgpa;

       void display() {                // method (what it DOES)
           System.out.println(roll + " " + name + " " + cgpa);
       }
   }
   ```

   Object
   - An `object` is an `instance` of a class — a real thing created from the blueprint, occupying memory on the heap. Each object has its `own copy` of the instance variables.
   ```java
   Student s1 = new Student();         // object 1
   Student s2 = new Student();         // object 2
   ```

   Complete example
   ```java
   class Student {
       String name;
       int    roll;

       Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
       }

       void display() {
           System.out.println(roll + " - " + name);
       }
   }

   public class Main {
       public static void main(String[] args) {

           Student s1 = new Student("Rahim", 101);   // object 1
           Student s2 = new Student("Karim", 102);   // object 2

           s1.display();       // 101 - Rahim
           s2.display();       // 102 - Karim
       }
   }
   ```
   - One class, two objects, each with its own `name` and `roll`.

   An everyday analogy
   ```
      CLASS                       OBJECT
      -----                       ------
      The plan of a house         The houses actually built from it
      A cake recipe               The cakes baked from it
      The design of a car         The individual cars produced
      A blank passport form       Each person's completed passport
   ```
   - One plan can produce any number of houses, and each house is separate: repainting one does not repaint the others.

   Difference

   | Point | Class | Object |
   |---|---|---|
   | Nature | A blueprint or template | An instance of the class |
   | Entity | `Logical` | `Physical` — it exists in memory |
   | Memory | None allocated for data | Allocated on the heap |
   | Created by | The `class` keyword | The `new` keyword |
   | Declared | Once | Any number of times |
   | Contains | Attributes and methods | Actual values for those attributes |
   | Analogy | The recipe | The cake |
   | Example | `class Student { ... }` | `Student s1 = new Student();` |
   | Destroyed | Never during the program | By the garbage collector when unreachable |

   Memory picture
   ```
      ---- Class area ----
           Student : the method code, static members

      ---- Heap ----
           s1 -> [ name = "Rahim" , roll = 101 ]
           s2 -> [ name = "Karim" , roll = 102 ]
   ```
   - The `method code exists once` in the class area and is shared. Only the `data` is duplicated per object, which is why creating many objects is inexpensive.

4. **(খ) উদাহরণসহ ক্লাস এবং অবজেক্ট এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Class
   - A `class` is a blueprint or template that defines what data an object will hold and what it can do. It is a `logical` entity — declaring a class allocates no memory for data.
   ```java
   class Car {
       String brand;                // attribute
       int    speed;

       void drive() {               // method
           System.out.println(brand + " is running at " + speed + " km/h");
       }
   }
   ```

   Object
   - An `object` is an `instance` of a class — a real entity created from the blueprint, occupying memory on the heap. Each object keeps its `own copy` of the instance variables.
   ```java
   Car c1 = new Car();          // object 1
   Car c2 = new Car();          // object 2
   ```

   Full example
   ```java
   class Car {
       String brand;
       int    speed;

       Car(String brand, int speed) {
           this.brand = brand;
           this.speed = speed;
       }

       void drive() {
           System.out.println(brand + " is running at " + speed + " km/h");
       }
   }

   public class Main {
       public static void main(String[] args) {

           Car c1 = new Car("Toyota", 120);     // object 1
           Car c2 = new Car("Honda", 100);      // object 2

           c1.drive();      // Toyota is running at 120 km/h
           c2.drive();      // Honda is running at 100 km/h
       }
   }
   ```

   Analogy
   ```
      CLASS                     OBJECT
      -----                     ------
      A house plan              The houses built from it
      A cake recipe             The cakes baked from it
      A blank passport form     Each person's completed passport
   ```
   - One plan, many houses. Painting one house does not change the others, because each is a separate object with its own state.

   Difference

   | Point | Class | Object |
   |---|---|---|
   | Nature | Blueprint or template | Instance of the class |
   | Entity | `Logical` | `Physical` — exists in memory |
   | Memory | None allocated for data | Allocated on the heap |
   | Created with | The `class` keyword | The `new` keyword |
   | How many | Declared once | Any number |
   | Contains | Attributes and methods | Actual values for those attributes |
   | Example | `class Car { ... }` | `Car c1 = new Car();` |
   | Destroyed | Never during the program | By the garbage collector |

   Memory picture
   ```
      ---- Class area ----
           Car : the method code, static members  (ONE copy)

      ---- Heap ----
           c1 -> [ brand = "Toyota" , speed = 120 ]
           c2 -> [ brand = "Honda"  , speed = 100 ]
   ```
   - The method `code` exists once and is shared by every object; only the `data` is duplicated. That is why creating many objects is cheap.

5. **Define Class and Object in C++ with example.** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

   Answer: Class
   - A `class` in C++ is a user-defined data type that binds `data members` and `member functions` into one unit. It is a `blueprint` — declaring a class allocates no memory for data.
   - Members are `private by default`, which is what distinguishes a class from a `struct`.
   ```cpp
   class ClassName {
   private:
       // data members - hidden
   public:
       // member functions - the interface
   };
   ```

   Object
   - An `object` is an `instance` of a class — a real entity occupying memory. Each object has its own copy of the data members.
   ```cpp
      ClassName objectName;
   ```

   Complete example
   ```cpp
   #include <iostream>
   #include <string>
   using namespace std;

   class Student {
   private:                              // encapsulation
       string name;
       int    roll;
       double cgpa;

   public:
       // ---- constructor ----
       Student(string n, int r, double c) {
           name = n;
           roll = r;
           cgpa = (c >= 0 && c <= 4.0) ? c : 0;
       }

       // ---- member functions ----
       void display() {
           cout << roll << " - " << name << " - CGPA " << cgpa << endl;
       }

       void setCgpa(double c) {
           if (c >= 0 && c <= 4.0) cgpa = c;
       }

       double getCgpa() { return cgpa; }
   };

   int main() {
       Student s1("Rahim", 101, 3.75);      // object 1
       Student s2("Karim", 102, 3.40);      // object 2

       s1.display();                        // 101 - Rahim - CGPA 3.75
       s2.display();                        // 102 - Karim - CGPA 3.4

       s1.setCgpa(3.90);
       s1.display();                        // 101 - Rahim - CGPA 3.9

       // s1.cgpa = 5.0;    // COMPILE ERROR - cgpa is private

       return 0;
   }
   ```

   Defining a member function outside the class, with the scope resolution operator
   ```cpp
   class Rectangle {
   private:
       double length, width;
   public:
       void setDimensions(double l, double w);   // declaration only
       double area();
   };

   void Rectangle::setDimensions(double l, double w) {   // definition
       length = l;
       width  = w;
   }

   double Rectangle::area() {
       return length * width;
   }
   ```

   Creating objects in C++
   ```cpp
      Student s1("Rahim", 101, 3.75);          // on the STACK, automatic
      Student* p = new Student("Karim",102,3.4); // on the HEAP, needs delete
      p->display();
      delete p;                                // C++ has no garbage collector
      Student arr[3] = { ... };                // an array of objects
   ```

   Difference

   | Point | Class | Object |
   |---|---|---|
   | Nature | Blueprint or template | Instance of the class |
   | Entity | Logical | Physical — occupies memory |
   | Memory | None for data | Allocated when created |
   | Declared | Once | Any number of times |
   | Contains | Members and functions | Actual values |
   | Default access | `private` | — |
   | Created by | The `class` keyword | `ClassName obj;` or `new` |

   Access specifiers in C++
   ```
      private   : accessible inside the class only          (the default)
      protected : the class and its derived classes
      public    : accessible everywhere
   ```

   - The difference from `struct` is only the default: a struct's members are `public` by default and a class's are `private`. Everything else — methods, constructors, inheritance — is available to both.

6. **What are the common activities on OOP design process?** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 756 (ET: N/A)]*

   Answer: `Object-oriented design` is the stage between analysis and coding, in which the problem is expressed as a set of collaborating objects. The common activities are the following.

   1. Identify the objects and classes
   - Read the requirement statement and pick out the `nouns`. Each significant noun is a candidate class.
   ```
      "A CUSTOMER opens an ACCOUNT at a BRANCH and makes TRANSACTIONS."

      Candidate classes : Customer , Account , Branch , Transaction
   ```
   - Discard nouns that are attributes rather than entities, and those outside the system's scope.

   2. Identify the attributes
   - For each class, decide what data it must hold — its `state`.
   ```
      Account : accountNumber , balance , openingDate , type
   ```

   3. Identify the methods (responsibilities)
   - Pick out the `verbs`. Each becomes a method on the class that owns the data it needs.
   ```
      "The customer DEPOSITS and WITHDRAWS money."

      Account : deposit() , withdraw() , getBalance() , calculateInterest()
   ```

   4. Identify the relationships between classes
   ```
      IS-A       -> inheritance      : SavingsAccount IS-A Account
      HAS-A      -> composition      : Account HAS-A Customer
      USES-A     -> association      : Teller USES-A Account
      Aggregation -> a weaker HAS-A, where the part can outlive the whole
   ```

   5. Determine the cardinality of each relationship
   ```
      One customer  --  many accounts        (1 : N)
      One account   --  many transactions    (1 : N)
   ```

   6. Build the class hierarchy
   - Factor the common attributes and behaviour into a `superclass`, and specialise in subclasses.
   ```
                   Account
                  /       \
       SavingsAccount   CurrentAccount
   ```

   7. Apply encapsulation and define the interface
   - Decide which members are `private` and which `public`. The public members are the class's `contract` with the rest of the system, and should be as small as possible.

   8. Identify abstraction points
   - Where several classes share a responsibility but implement it differently, declare an `abstract class` or an `interface`.

   9. Draw the design
   ```
      Class diagram        : classes, attributes, methods, relationships
      Sequence diagram     : the order of messages between objects
      Use case diagram     : what the actors need the system to do
      State diagram        : how one object's state changes
   ```
   - `UML` is the standard notation for all of these.

   10. Apply design principles and patterns
   ```
      SOLID :
         S - Single Responsibility : one class, one reason to change
         O - Open-Closed           : open for extension, closed for modification
         L - Liskov Substitution   : a subclass must be usable as its superclass
         I - Interface Segregation : many small interfaces beat one large one
         D - Dependency Inversion  : depend on abstractions, not concretions

      Patterns : Factory, Singleton, Observer, Strategy, MVC
   ```

   11. Review, refine and iterate
   - Check for classes with too many responsibilities, duplicated code, deep inheritance chains and circular dependencies. Object-oriented design is `iterative`, not a single pass.

   12. Implement and test
   - Translate the design into code, and write unit tests for each class in isolation.

   Worked illustration — a small banking system
   ```
      Nouns -> classes      : Customer, Account, Transaction, Branch
      Verbs -> methods      : deposit, withdraw, transfer, calculateInterest
      Relationships         : Customer HAS-A Account (1:N)
                              SavingsAccount IS-A Account
                              Account HAS-MANY Transaction
      Abstraction           : abstract class Account with abstract
                              calculateInterest()
      Encapsulation         : balance is private; deposit() validates
   ```

   - The core question the whole process answers is: `what things exist in this problem, what does each know, and what is each responsible for doing?` Getting the responsibilities in the right place is what makes an object-oriented design good or bad.

7. **Write a programme to create an object of type batsman and calculate the average runs scored by the player.** *[RAKUB Programmer (PO) 12.10.2021 compact it 846-847 (ET: N/A)]*

   Answer: The `Batsman` class holds the player's data, and `calculateAverage()` returns the batting average.
   ```
      Batting average = total runs / number of times OUT
   ```
   - Note that the divisor is the number of `dismissals`, not the number of innings — an innings in which the batsman was `not out` does not count in the denominator. This is the point the question is really testing.

   ```java
   import java.util.Scanner;

   class Batsman {

       // ---- data members ----
       private String name;
       private int    innings;
       private int    notOuts;
       private int    totalRuns;

       // ---- constructor ----
       public Batsman(String name, int innings, int notOuts, int totalRuns) {
           this.name      = name;
           this.innings   = innings;
           this.notOuts   = notOuts;
           this.totalRuns = totalRuns;
       }

       // ---- calculate the batting average ----
       public double calculateAverage() {
           int dismissals = innings - notOuts;

           if (dismissals == 0)
               return totalRuns;          // never out - average is the runs
           return (double) totalRuns / dismissals;
       }

       // ---- simple average per innings, for comparison ----
       public double runsPerInnings() {
           if (innings == 0) return 0;
           return (double) totalRuns / innings;
       }

       public void display() {
           System.out.println("=================================");
           System.out.println("Player      : " + name);
           System.out.println("Innings     : " + innings);
           System.out.println("Not outs    : " + notOuts);
           System.out.println("Total runs  : " + totalRuns);
           System.out.printf ("Average     : %.2f%n", calculateAverage());
           System.out.printf ("Runs/innings: %.2f%n", runsPerInnings());
           System.out.println("=================================");
       }

       public String getName()          { return name; }
       public double getAverageValue()  { return calculateAverage(); }
   }

   public class Main {
       public static void main(String[] args) {

           Scanner sc = new Scanner(System.in);

           System.out.print("Enter player name : ");
           String name = sc.nextLine();

           System.out.print("Enter innings     : ");
           int innings = sc.nextInt();

           System.out.print("Enter not outs    : ");
           int notOuts = sc.nextInt();

           System.out.print("Enter total runs  : ");
           int runs = sc.nextInt();

           // create the OBJECT of type Batsman
           Batsman player = new Batsman(name, innings, notOuts, runs);
           player.display();

           sc.close();
       }
   }
   ```

   Sample run
   ```
      Enter player name : Shakib Al Hasan
      Enter innings     : 50
      Enter not outs    : 5
      Enter total runs  : 1800

      =================================
      Player      : Shakib Al Hasan
      Innings     : 50
      Not outs    : 5
      Total runs  : 1800
      Average     : 40.00
      Runs/innings: 36.00
      =================================
   ```

   Working
   ```
      Dismissals = innings - not outs = 50 - 5 = 45

      Batting average = 1800 / 45 = 40.00
      Runs per innings = 1800 / 50 = 36.00
   ```

   Version taking the score of each innings
   ```java
   class Batsman {
       private String name;
       private int[]  scores;
       private boolean[] notOut;

       public Batsman(String name, int[] scores, boolean[] notOut) {
           this.name   = name;
           this.scores = scores;
           this.notOut = notOut;
       }

       public double calculateAverage() {
           int total = 0, dismissals = 0;

           for (int i = 0; i < scores.length; i++) {
               total += scores[i];
               if (!notOut[i]) dismissals++;
           }
           return (dismissals == 0) ? total : (double) total / dismissals;
       }

       public int highestScore() {
           int max = 0;
           for (int s : scores) if (s > max) max = s;
           return max;
       }
   }
   ```

   Several players, compared
   ```java
   Batsman[] team = {
       new Batsman("Shakib", 50, 5, 1800),
       new Batsman("Tamim",  60, 3, 2100),
       new Batsman("Mushfiq",55, 8, 1650)
   };

   Batsman best = team[0];
   for (Batsman b : team) {
       b.display();
       if (b.getAverageValue() > best.getAverageValue()) best = b;
   }
   System.out.println("Best average: " + best.getName());
   ```

   Points worth noting
   ```
      (double) totalRuns / dismissals - the CAST is essential, or integer
           division would discard the fraction and give 40 instead of 40.00

      Guard against dismissals == 0, or the program throws
           ArithmeticException (for integers) or returns Infinity

      The data members are private with public methods : encapsulation
   ```

8. **(ক) Object কী? কীভাবে Object তৈরি করতে হয় উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1085 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What an object is
   - An `object` is a real entity created from a `class`. It is an `instance` of the class, occupying memory on the heap, and it has three characteristics:
   ```
      STATE    : the values of its attributes  (what it HAS)
      BEHAVIOUR: the methods it can perform    (what it DOES)
      IDENTITY : a unique reference, so two objects with identical values
                 are still two different objects
   ```
   ```
      Object : a Car
         State     : brand = "Toyota" , colour = "white" , speed = 0
         Behaviour : start() , accelerate() , brake()
         Identity  : the reference held in the variable c1
   ```

   How an object is created
   ```java
      ClassName referenceVariable = new ClassName(arguments);
           |            |            |      |
           |            |            |      +-- calls the CONSTRUCTOR
           |            |            +--------- allocates memory on the HEAP
           |            +---------------------- the reference variable
           +----------------------------------- the type
   ```

   Three steps
   ```
      1. DECLARATION  : Student s1;
                        creates a reference variable; it holds null so far

      2. INSTANTIATION: new Student(...)
                        allocates memory on the heap for the object

      3. INITIALISATION: the CONSTRUCTOR runs and sets the initial values
   ```

   Complete example
   ```java
   class Student {
       String name;
       int    roll;

       // constructor
       Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
       }

       void display() {
           System.out.println(roll + " - " + name);
       }
   }

   public class Main {
       public static void main(String[] args) {

           // creating objects
           Student s1 = new Student("Rahim", 101);
           Student s2 = new Student("Karim", 102);

           s1.display();       // 101 - Rahim
           s2.display();       // 102 - Karim
       }
   }
   ```

   Other ways to create an object in Java
   ```java
      // 1. the new keyword - the normal way
      Student s = new Student("Rahim", 101);

      // 2. Class.forName() with reflection
      Student s = (Student) Class.forName("Student").newInstance();

      // 3. clone() - copy an existing object
      Student s2 = (Student) s1.clone();

      // 4. deserialization - read an object back from a file or stream
      ObjectInputStream in = new ObjectInputStream(new FileInputStream("f.ser"));
      Student s = (Student) in.readObject();

      // 5. a factory method
      Student s = Student.create("Rahim", 101);
   ```
   - The `new` keyword is by far the commonest; the others exist for specific purposes such as frameworks, copying and persistence.

   An array of objects
   ```java
      Student[] batch = new Student[3];              // 3 REFERENCES, all null
      batch[0] = new Student("Rahim", 101);          // now the objects
      batch[1] = new Student("Karim", 102);
      batch[2] = new Student("Jamal", 103);

      for (Student s : batch) s.display();
   ```
   - Note that `new Student[3]` creates only the array of references. Each element must still be given an object, or using it throws `NullPointerException`.

   Memory picture
   ```
      ---- Stack ----              ---- Heap ----
        s1  ----------------->  [ name="Rahim" , roll=101 ]
        s2  ----------------->  [ name="Karim" , roll=102 ]
   ```
   - The `reference` lives on the stack; the `object` lives on the heap. When no reference points to an object any more, it becomes eligible for garbage collection.

   In C++
   ```cpp
      Student s1("Rahim", 101);              // on the stack - destroyed automatically
      Student* p = new Student("Karim",102); // on the heap - needs delete
      delete p;                              // C++ has no garbage collector
   ```

9. **Suppose, you are implementing “Overdraft Account (OD)” class using java for a banking app. An OD type account is opened with an approved loan limit (ex. 100000/-). The account holder can deposit any amount of money in the OD account at any time. S/he can draw an amount of money from the account (acn) until sufficient acn balance. S/he allowed to draw money beyond his/her acn balance if the total over-drawing amount remains within the loan limit. A java sketch for OD acn is given bellow & code is expected to run in multi-threading mode. (same code with run by different counter in the Bank)** *[Bangladesh Bank Assistant Programmer 2019 compact it 1157 (ET: DU)]*

   Answer: The account must allow the balance to go negative, but only as far as the approved `loan limit`. Because several bank counters run the same code at the same time, the withdrawal must be `thread-safe` — otherwise two tellers could both pass the limit check and overdraw the account.

   ```java
   class OverdraftAccount {

       private final String accountNumber;
       private final String holderName;
       private final double loanLimit;        // e.g. 100000
       private double balance;                // may go NEGATIVE

       public OverdraftAccount(String accNo, String name,
                               double openingBalance, double loanLimit) {
           this.accountNumber = accNo;
           this.holderName    = name;
           this.balance       = openingBalance;
           this.loanLimit     = loanLimit;
       }

       // ---------- DEPOSIT : any amount, at any time ----------
       public synchronized void deposit(double amount) {
           if (amount <= 0) {
               System.out.println("Deposit must be positive");
               return;
           }
           balance += amount;
           System.out.println(Thread.currentThread().getName() +
                              " deposited " + amount + " | balance = " + balance);
       }

       // ---------- WITHDRAW : allowed down to -loanLimit ----------
       public synchronized boolean withdraw(double amount) {
           if (amount <= 0) {
               System.out.println("Withdrawal must be positive");
               return false;
           }

           // the CHECK and the UPDATE must be ATOMIC
           if (balance - amount >= -loanLimit) {
               balance -= amount;
               System.out.println(Thread.currentThread().getName() +
                                  " withdrew " + amount + " | balance = " + balance);
               if (balance < 0)
                   System.out.println("   (overdrawn by " + (-balance) + ")");
               return true;
           } else {
               System.out.println(Thread.currentThread().getName() +
                   " DENIED " + amount + " : would exceed the loan limit. " +
                   "Available = " + availableFunds());
               return false;
           }
       }

       // total money the holder may still draw
       public synchronized double availableFunds() {
           return balance + loanLimit;
       }

       public synchronized double getBalance() { return balance; }

       public synchronized void display() {
           System.out.println("--------------------------------");
           System.out.println("Account   : " + accountNumber);
           System.out.println("Holder    : " + holderName);
           System.out.println("Balance   : " + balance);
           System.out.println("Loan limit: " + loanLimit);
           System.out.println("Available : " + availableFunds());
           System.out.println("--------------------------------");
       }
   }
   ```

   Testing it with several counters running at once
   ```java
   public class Main {
       public static void main(String[] args) throws InterruptedException {

           OverdraftAccount acc =
               new OverdraftAccount("OD-1001", "Karim Traders", 20000, 100000);

           acc.display();     // balance 20000, available 120000

           Runnable counter = () -> {
               for (int i = 0; i < 3; i++) {
                   acc.withdraw(30000);
                   try { Thread.sleep(10); } catch (InterruptedException e) { }
               }
           };

           Thread t1 = new Thread(counter, "Counter-1");
           Thread t2 = new Thread(counter, "Counter-2");

           t1.start();  t2.start();
           t1.join();   t2.join();

           acc.display();
       }
   }
   ```

   Sample output
   ```
      Counter-1 withdrew 30000.0 | balance = -10000.0
         (overdrawn by 10000.0)
      Counter-2 withdrew 30000.0 | balance = -40000.0
         (overdrawn by 40000.0)
      Counter-1 withdrew 30000.0 | balance = -70000.0
         (overdrawn by 70000.0)
      Counter-2 DENIED 30000.0 : would exceed the loan limit. Available = 30000.0
      ...
      --------------------------------
      Balance   : -100000.0
      Available : 0.0
      --------------------------------
   ```
   - The balance never falls below `-100000`, whatever order the threads run in.

   Why `synchronized` is essential — the race condition it prevents
   ```
      WITHOUT synchronized, with balance = 20000 and limit = 100000 :

      Counter-1 : reads balance 20000, checks 20000-100000 >= -100000  OK
      Counter-2 : reads balance 20000, checks 20000-100000 >= -100000  OK
                               <- both passed the check
      Counter-1 : balance = 20000 - 100000 = -80000
      Counter-2 : balance = -80000 - 100000 = -180000   <- LIMIT BREACHED

      The check and the update are two separate steps. Another thread can
      act BETWEEN them - a "check-then-act" race condition.
   ```
   - `synchronized` makes the whole check-and-update sequence `atomic`: only one thread may be inside any synchronized method of that object at a time.

   An alternative using an explicit lock
   ```java
   import java.util.concurrent.locks.ReentrantLock;

   private final ReentrantLock lock = new ReentrantLock();

   public boolean withdraw(double amount) {
       lock.lock();
       try {
           if (balance - amount >= -loanLimit) {
               balance -= amount;
               return true;
           }
           return false;
       } finally {
           lock.unlock();          // ALWAYS in a finally block
       }
   }
   ```
   - `ReentrantLock` adds `tryLock()` with a timeout and fairness options, which `synchronized` does not offer.

   Design points worth stating
   ```
      The balance is PRIVATE and may only be changed through synchronized
           methods - encapsulation is what makes thread safety possible at all

      Only the BALANCE needs protection; accountNumber, holderName and
           loanLimit are final and never change

      getBalance() and availableFunds() are also synchronized, so a reader
           never sees a half-completed update

      Interest on an overdraft is charged on the NEGATIVE balance only :

           double overdraftInterest() {
               return (balance < 0) ? -balance * rate / 100 : 0;
           }

      In a real banking system this logic would sit in a DATABASE
           TRANSACTION, so that atomicity survives a crash as well as
           concurrency. Java-level synchronization protects one JVM only.
   ```

10. **There was a java program where you have to create a class, constructor, setter function, getter function.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1214-1215 (ET: N/A)]*

    Answer: The program below shows the standard structure of a Java class: `private` fields, a `constructor`, `setter` methods that validate, and `getter` methods that read.

    ```java
    class Student {

        // ---- 1. PRIVATE data members : encapsulation ----
        private String name;
        private int    roll;
        private double cgpa;

        // ---- 2. CONSTRUCTORS ----

        // default constructor
        public Student() {
            this.name = "Unknown";
            this.roll = 0;
            this.cgpa = 0.0;
        }

        // parameterised constructor
        public Student(String name, int roll, double cgpa) {
            this.name = name;
            this.roll = roll;
            setCgpa(cgpa);                 // reuse the setter, so it is validated
        }

        // ---- 3. SETTER methods : write, with validation ----
        public void setName(String name) {
            if (name != null && !name.trim().isEmpty())
                this.name = name;
            else
                System.out.println("Name cannot be empty");
        }

        public void setRoll(int roll) {
            if (roll > 0)
                this.roll = roll;
            else
                System.out.println("Roll must be positive");
        }

        public void setCgpa(double cgpa) {
            if (cgpa >= 0.0 && cgpa <= 4.0)
                this.cgpa = cgpa;
            else
                System.out.println("CGPA must be between 0.00 and 4.00");
        }

        // ---- 4. GETTER methods : read only ----
        public String getName() { return name; }
        public int    getRoll() { return roll; }
        public double getCgpa() { return cgpa; }

        // ---- 5. other behaviour ----
        public String getGrade() {
            if (cgpa >= 3.75) return "A+";
            else if (cgpa >= 3.50) return "A";
            else if (cgpa >= 3.00) return "B";
            else if (cgpa >= 2.00) return "C";
            else return "F";
        }

        public void display() {
            System.out.println("--------------------------------");
            System.out.println("Roll  : " + roll);
            System.out.println("Name  : " + name);
            System.out.println("CGPA  : " + cgpa);
            System.out.println("Grade : " + getGrade());
            System.out.println("--------------------------------");
        }
    }

    public class Main {
        public static void main(String[] args) {

            // using the parameterised constructor
            Student s1 = new Student("Rahim Uddin", 101, 3.75);
            s1.display();

            // using the default constructor and setters
            Student s2 = new Student();
            s2.setName("Karim Ali");
            s2.setRoll(102);
            s2.setCgpa(3.40);
            s2.display();

            // the setters REJECT invalid values
            s2.setCgpa(5.0);            // "CGPA must be between 0.00 and 4.00"
            s2.setRoll(-5);             // "Roll must be positive"
            System.out.println("CGPA is still: " + s2.getCgpa());   // 3.4

            // direct access is impossible
            // s2.cgpa = 5.0;           // COMPILE ERROR - cgpa is private
        }
    }
    ```

    Output
    ```
       --------------------------------
       Roll  : 101
       Name  : Rahim Uddin
       CGPA  : 3.75
       Grade : A+
       --------------------------------
       --------------------------------
       Roll  : 102
       Name  : Karim Ali
       CGPA  : 3.4
       Grade : B
       --------------------------------
       CGPA must be between 0.00 and 4.00
       Roll must be positive
       CGPA is still: 3.4
    ```

    The four elements the question asks for
    ```
       CLASS       : Student - the blueprint holding data and behaviour
       CONSTRUCTOR : runs automatically when an object is created;
                     same name as the class, no return type;
                     can be OVERLOADED, as shown by the two versions here
       SETTER      : setX(value) - writes a private field, after validating
       GETTER      : getX()      - reads a private field
    ```

    Why getters and setters matter
    ```
       Without them the field must be public :

            student.cgpa = 5.0;      // legal, and the data is now corrupt

       With them, every write passes through ONE validation point, so an
       invalid value can never enter the object. The internal representation
       can also be changed later without breaking a single caller.
    ```
    - Naming convention: `getX()` / `setX()` for ordinary fields, and `isX()` for a boolean. Following it exactly is what makes a class a `JavaBean`, which frameworks such as Spring and Hibernate rely on.
    - A field that should be read but never changed simply has a getter and `no setter` — that is how a read-only property is expressed.

11. **In java language: write a class named Bicycle having 3 integer variables (speed, gear, cost) and a constructor to initialize the variables. Also write a class named MountBike that inherits Bicycle class, having an extra variable speedcost and a constructor to initialize the variable.** *[DESCO Assistant Engineer (CSE) 2016 compact it 1269 (ET: N/A)]*

    Answer: `MountBike` extends `Bicycle`, so it inherits `speed`, `gear` and `cost` and adds `speedcost` of its own.

    ```java
    // ---------------- SUPERCLASS ----------------
    class Bicycle {

        int speed;
        int gear;
        int cost;

        // constructor to initialise the three variables
        public Bicycle(int speed, int gear, int cost) {
            this.speed = speed;
            this.gear  = gear;
            this.cost  = cost;
        }

        public void display() {
            System.out.println("Speed : " + speed);
            System.out.println("Gear  : " + gear);
            System.out.println("Cost  : " + cost);
        }
    }

    // ---------------- SUBCLASS ----------------
    class MountBike extends Bicycle {

        int speedcost;                  // the extra variable

        // constructor to initialise all four variables
        public MountBike(int speed, int gear, int cost, int speedcost) {
            super(speed, gear, cost);   // MUST be the first statement
            this.speedcost = speedcost;
        }

        @Override
        public void display() {
            super.display();            // print the inherited values first
            System.out.println("SpeedCost : " + speedcost);
        }
    }

    // ---------------- MAIN ----------------
    public class Main {
        public static void main(String[] args) {

            Bicycle b = new Bicycle(20, 5, 15000);
            System.out.println("--- Bicycle ---");
            b.display();

            MountBike m = new MountBike(35, 8, 45000, 1200);
            System.out.println("--- MountBike ---");
            m.display();
        }
    }
    ```

    Output
    ```
       --- Bicycle ---
       Speed : 20
       Gear  : 5
       Cost  : 15000
       --- MountBike ---
       Speed : 35
       Gear  : 8
       Cost  : 45000
       SpeedCost : 1200
    ```

    How the constructors chain
    ```
       new MountBike(35, 8, 45000, 1200)
            |
            v
       MountBike constructor
            |
            +--> super(35, 8, 45000)  ---> Bicycle constructor
            |                                 speed = 35
            |                                 gear  = 8
            |                                 cost  = 45000
            |
            +--> this.speedcost = 1200
    ```
    - `super(...)` must be the `first statement` in the subclass constructor. If it is omitted, Java inserts an implicit `super()` — which would fail here, because `Bicycle` has no no-argument constructor.

    Better version, with encapsulation
    ```java
    class Bicycle {
        private int speed, gear, cost;

        public Bicycle(int speed, int gear, int cost) {
            this.speed = speed;
            this.gear  = gear;
            this.cost  = cost;
        }

        public int getSpeed() { return speed; }
        public int getGear()  { return gear; }
        public int getCost()  { return cost; }

        public void display() {
            System.out.println("Speed: " + speed + ", Gear: " + gear +
                               ", Cost: " + cost);
        }
    }

    class MountBike extends Bicycle {
        private int speedcost;

        public MountBike(int speed, int gear, int cost, int speedcost) {
            super(speed, gear, cost);
            this.speedcost = speedcost;
        }

        public int totalCost() { return getCost() + speedcost; }

        @Override
        public void display() {
            super.display();
            System.out.println("SpeedCost: " + speedcost +
                               ", Total: " + totalCost());
        }
    }
    ```
    - With `private` fields the subclass must use the getters. Declaring them `protected` instead would let the subclass access them directly, which is often preferred inside a class hierarchy.

    Concepts the program demonstrates
    ```
       INHERITANCE          : MountBike extends Bicycle - an IS-A relationship
       CONSTRUCTOR CHAINING : super(...) passes values up to the parent
       METHOD OVERRIDING    : MountBike.display() replaces Bicycle.display()
       super KEYWORD        : super(...) for the constructor,
                              super.display() for the method
       this KEYWORD         : distinguishes a field from a parameter
       CODE REUSE           : speed, gear and cost are declared once
    ```

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

   Answer: The output is `19`.

   The key point
   - `x` is a `static` variable, so there is `one copy shared by every call`. Each call adds 2 to that single shared value.
   - In `return fun(n-1) + x;` Java evaluates `left to right`. So `fun(n-1)` runs completely `first` — increasing x further — and only `then` is x read.

   Trace
   ```
      Initially x = 5

      main calls fun(3)
      ------------------
      fun(3) : n = 3, not <= 1
               x = 5 + 2 = 7
               evaluate fun(2) FIRST

          fun(2) : n = 2, not <= 1
                   x = 7 + 2 = 9
                   evaluate fun(1) FIRST

              fun(1) : n = 1 <= 1  ->  return 1

                   return 1 + x
                        = 1 + 9        (x is 9 NOW)
                        = 10

               return 10 + x
                    = 10 + 9           (x is still 9)
                    = 19
   ```
   ```
      Output : 19
   ```

   Step-by-step table
   ```
      Call      x before   x after   value of fun(n-1)   returns
      --------  ---------  --------  -----------------   -------
      fun(3)        5         7            10            10 + 9 = 19
      fun(2)        7         9             1             1 + 9 = 10
      fun(1)        9         9             -             1
   ```
   - Note that by the time either `+ x` is evaluated, x has already reached its final value of `9`, because the recursion had already finished increasing it.

   The trap in this question
   ```
      A common WRONG answer is 17, obtained by assuming x is read BEFORE
      the recursive call :

           fun(3) : x = 7 , return fun(2) + 7
           fun(2) : x = 9 , return fun(1) + 9 = 10
           total  : 10 + 7 = 17          <- WRONG

      Java's left-to-right evaluation means fun(n-1) is fully evaluated
      first, so x has already become 9 when it is read. The answer is 19.
   ```

   What makes it behave this way
   ```
      static int x        one copy shared by ALL calls, not one per call
                          If x were a LOCAL variable, each call would have
                          its own and the answer would be different.

      left-to-right       Java guarantees that in a + b, a is evaluated
                          completely before b. C and C++ do NOT guarantee
                          this, so the same program is undefined there.
   ```

2. **(খ) কোন object-oriented programming language ব্যবহার করে একটি program লিখুন, যা recursive function ব্যবহার করে Fibonacci series প্রদান করবে।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.) The `Fibonacci series` is a sequence in which each term is the sum of the two before it.
   ```
      F(0) = 0
      F(1) = 1
      F(n) = F(n-1) + F(n-2)     for n >= 2

      0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
   ```

   Java program using recursion
   ```java
   import java.util.Scanner;

   class Fibonacci {

       // recursive method
       public int fib(int n) {
           if (n == 0) return 0;               // base case 1
           if (n == 1) return 1;               // base case 2
           return fib(n - 1) + fib(n - 2);     // recursive case
       }

       // print the whole series
       public void printSeries(int count) {
           System.out.print("Fibonacci series: ");
           for (int i = 0; i < count; i++)
               System.out.print(fib(i) + " ");
           System.out.println();
       }
   }

   public class Main {
       public static void main(String[] args) {

           Scanner sc = new Scanner(System.in);
           System.out.print("How many terms? ");
           int n = sc.nextInt();

           Fibonacci f = new Fibonacci();       // object of the class
           f.printSeries(n);

           sc.close();
       }
   }
   ```

   Sample run
   ```
      How many terms? 10
      Fibonacci series: 0 1 1 2 3 5 8 13 21 34
   ```

   How the recursion works for fib(5)
   ```
                          fib(5)
                         /      \
                    fib(4)      fib(3)
                   /     \      /     \
               fib(3)  fib(2) fib(2) fib(1)
               /   \    /  \   /  \
           fib(2) fib(1)...  ...
           /   \
       fib(1) fib(0)

      fib(5) = fib(4) + fib(3)
             = (fib(3)+fib(2)) + (fib(2)+fib(1))
             = ...
             = 5
   ```

   The problem with plain recursion
   ```
      fib(2) is computed 3 times, fib(3) twice, and so on.
      Time complexity is EXPONENTIAL : O(2^n)

      fib(40) takes about a second; fib(50) takes minutes.
   ```

   Efficient version — recursion with memoization
   ```java
   class Fibonacci {
       private long[] memo;

       public long fib(int n) {
           if (memo == null) memo = new long[100];
           if (n <= 1) return n;
           if (memo[n] != 0) return memo[n];        // already computed
           memo[n] = fib(n - 1) + fib(n - 2);       // store it
           return memo[n];
       }
   }
   ```
   - Each value is computed once, so the time falls from `O(2^n)` to `O(n)`.

   Iterative version, for comparison
   ```java
   public void printIterative(int count) {
       long a = 0, b = 1;
       for (int i = 0; i < count; i++) {
           System.out.print(a + " ");
           long next = a + b;
           a = b;
           b = next;
       }
   }
   ```
   - `O(n)` time and `O(1)` space — the best of the three, but recursion is what the question asks for.

   C++ version
   ```cpp
   #include <iostream>
   using namespace std;

   class Fibonacci {
   public:
       int fib(int n) {
           if (n <= 1) return n;
           return fib(n - 1) + fib(n - 2);
       }
   };

   int main() {
       Fibonacci f;
       int n;
       cout << "How many terms? ";
       cin >> n;
       for (int i = 0; i < n; i++) cout << f.fib(i) << " ";
       return 0;
   }
   ```

   Points worth stating
   ```
      Every recursion needs a BASE CASE, or it never stops and the program
           dies with StackOverflowError

      Each recursive call adds a FRAME to the call stack, so deep recursion
           costs memory as well as time

      Recursion is elegant here but INEFFICIENT; memoization or iteration
           should be used for any real value of n
   ```

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

   Answer: The output is `19`.

   Why `x` behaves as it does
   - `x` is declared `static`, so there is `one copy shared by every call` of `fun`. Each call adds 2 to that same variable.
   - In `return fun(n-1) + x;` Java evaluates `strictly left to right`. The recursive call `fun(n-1)` therefore runs to completion first — pushing x higher — and `only then` is x read.

   Trace
   ```
      Initially x = 5

      fun(3) : n = 3
               x = 5 + 2 = 7
               evaluate fun(2) first

           fun(2) : n = 2
                    x = 7 + 2 = 9
                    evaluate fun(1) first

                fun(1) : n = 1 <= 1  ->  return 1

                    return 1 + x  =  1 + 9  =  10      (x is 9 now)

               return 10 + x  =  10 + 9  =  19         (x is still 9)
   ```
   ```
      Output : 19
   ```

   Summary table
   ```
      Call      x before   x after   fun(n-1) returns   this call returns
      --------  ---------  --------  ----------------   -----------------
      fun(3)        5         7            10           10 + 9 = 19
      fun(2)        7         9             1            1 + 9 = 10
      fun(1)        9         9             -            1
   ```
   - By the time either `+ x` is evaluated, the recursion has already finished raising x to `9`, so both additions use 9.

   The trap
   ```
      A common WRONG answer is 17, from assuming x is read BEFORE the
      recursive call :

           fun(3) : x = 7 , "return fun(2) + 7"
           fun(2) : x = 9 , "return fun(1) + 9" = 10
           total  = 10 + 7 = 17          <- WRONG
   ```
   - Java's evaluation order settles it: `a + b` evaluates `a` completely before `b`, so `fun(n-1)` finishes first and x is already 9.

   What the question is testing
   ```
      static variable : ONE copy shared by all calls, not one per call.
                        If x were local, each call would keep its own value.

      evaluation order: Java guarantees left to right in an expression.
                        C and C++ do NOT, so the same program is
                        undefined behaviour there.

      recursion       : the calls unwind from the base case upward, and the
                        additions happen on the way back up.
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

   Answer: The program prints an `inverted right triangle` of asterisks: 10 stars on the first line, then 9, and so on down to 1.

   Output
   ```
      **********
      *********
      ********
      *******
      ******
      *****
      ****
      ***
      **
      *
   ```

   How it works
   ```
      Outer loop : i = 1 to 10       (one line per value of i)
      Inner loop : j = 10 down to 1

      Inside the inner loop :
           a '*' is printed EITHER way - in the if branch and in the else
           the ONLY difference is that the if branch also BREAKS

      So the inner loop prints one star per iteration and stops as soon
      as j reaches i.
   ```

   Counting the stars on each line
   ```
      j runs 10, 9, 8, ... down to i, and stops there.

      Number of iterations = 10 - i + 1 = 11 - i

      i = 1  ->  j = 10 down to 1   ->  10 stars
      i = 2  ->  j = 10 down to 2   ->   9 stars
      i = 3  ->  j = 10 down to 3   ->   8 stars
      ...
      i = 10 ->  j = 10 only        ->   1 star
   ```

   Trace of the first two lines
   ```
      i = 1 :
         j=10 : 10 != 1 -> print '*'      (1)
         j=9  :  9 != 1 -> print '*'      (2)
         ...
         j=2  :  2 != 1 -> print '*'      (9)
         j=1  :  1 == 1 -> print '*' and BREAK   (10)
         newline
         -> 10 stars

      i = 2 :
         j=10 down to 3 : 8 stars
         j=2  :  2 == 2 -> print '*' and BREAK   (9th)
         newline
         -> 9 stars
   ```

   Why the if and the else look pointless
   ```java
      if (i == j) { System.out.print("*"); break; }
      else        { System.out.print("*"); }
   ```
   - Both branches print the same thing. The `break` is the only real effect, so the code is equivalent to the much clearer:
   ```java
      for (j = n; j >= i; j--)
          System.out.print("*");
   ```
   - Written that way, the inner loop obviously runs `n - i + 1` times, which is the same count.

   A cleaner equivalent program
   ```java
   public class Pattern {
       public static void findOutput(int n) {
           for (int i = 1; i <= n; i++) {
               for (int j = n; j >= i; j--)
                   System.out.print("*");
               System.out.println();
           }
       }
       public static void main(String[] args) {
           findOutput(10);
       }
   }
   ```

   Total number of stars printed
   ```
      10 + 9 + 8 + ... + 1  =  n(n+1)/2  =  10 x 11 / 2  =  55
   ```

   - Points worth noting: the inner loop counts `downward`, which is what makes the triangle inverted. Changing it to `for (j = 1; j <= i; j++)` would produce the usual increasing triangle instead.

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

   Answer: The output is
   ```
      Audi is running
   ```

   Why
   - This is `runtime polymorphism`, achieved by `method overriding`.
   ```java
      car b = new Audi();
      b.run();
   ```
   - The `reference type` is `car`, but the `actual object` is an `Audi`. In Java the method that runs is decided by the `object`, not by the reference — this is called `dynamic method dispatch`.
   - `Audi.run()` overrides `car.run()`, so the Audi version executes.

   Step by step
   ```
      1. new Audi()      creates an Audi object on the heap
      2. car b = ...     a car reference is allowed to hold it, because
                         Audi IS-A car (upcasting, and it is automatic)
      3. b.run()         the compiler checks that car HAS a run() method - it does
                         the JVM then looks at the ACTUAL object (Audi)
                         and calls Audi's run()
   ```
   ```
      Compile time : is run() available on type 'car'?   YES  -> compiles
      Run time     : what is the real object?            Audi -> Audi.run()
   ```

   What would change the answer
   ```java
      car b = new car();
      b.run();               // "Car is running" - the object really is a car

      Audi a = new Audi();
      a.run();               // "Audi is running"
   ```

   If `run()` were `static`, the answer would be different
   ```java
      class car { static void run() { System.out.println("Car is running"); } }
      class Audi extends car { static void run() { System.out.println("Audi is running"); } }

      car b = new Audi();
      b.run();               // "Car is running"  <- HIDING, not overriding
   ```
   - A static method cannot be overridden, only `hidden`, and hiding is resolved by the `reference type` at compile time. The same is true of `fields`:
   ```java
      class car  { String name = "Car"; }
      class Audi extends car { String name = "Audi"; }

      car b = new Audi();
      System.out.println(b.name);     // "Car"  - fields are NOT polymorphic
   ```

   In C++ the base method must be `virtual`
   ```cpp
      class car {
      public:
          void run() { cout << "Car is running"; }        // NOT virtual
      };
      class Audi : public car {
      public:
          void run() { cout << "Audi is running"; }
      };

      car* b = new Audi();
      b->run();          // "Car is running"  <- because run() is not virtual
   ```
   - Adding `virtual` to `car::run()` makes C++ behave like Java. In Java every non-static, non-final method is virtual automatically.

   - The rule to remember: `overridden instance methods are chosen by the OBJECT; static methods and fields are chosen by the REFERENCE`.

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

   Answer: The output is
   ```
       0 5 1 6 2 7
   ```

   The loop
   ```java
      int i = 0;
      for (int j = 5; i < 3 && j < 10; i++, j++) {
          System.out.print(" " + i + " " + j);
      }
   ```
   - Note the unusual shape: `i` is declared `outside` the loop, `j` inside it, and the condition tests `both`. The update section increments both with the comma operator.

   Trace
   ```
      Initialisation : i = 0 (before the loop) , j = 5

      Iteration 1 : condition  0 < 3 && 5 < 10  -> true
                    print " 0 5"
                    update    i = 1 , j = 6

      Iteration 2 : condition  1 < 3 && 6 < 10  -> true
                    print " 1 6"
                    update    i = 2 , j = 7

      Iteration 3 : condition  2 < 3 && 7 < 10  -> true
                    print " 2 7"
                    update    i = 3 , j = 8

      Iteration 4 : condition  3 < 3  -> FALSE   -> loop ends
   ```
   ```
      Output :  0 5 1 6 2 7
   ```
   - Note there is no newline anywhere, so everything appears on one line, and each pair is preceded by a space because the print begins with `" "`.

   Which condition stops the loop
   ```
      i < 3   fails first, when i reaches 3
      j < 10  would not fail until j reached 10, which needs 5 iterations

      Since && requires BOTH to be true, the loop stops after 3 iterations.
   ```
   - The `&&` operator also `short-circuits`: once `i < 3` is false, `j < 10` is not even evaluated.

   Variants worth noticing
   ```
      If the condition were  i < 3 || j < 10  :
           the loop would continue while EITHER holds, so it would run
           5 times, until j reached 10 :
           " 0 5 1 6 2 7 3 8 4 9"

      If i were declared INSIDE the for statement :
           for (int i = 0, j = 5; ...)
           the behaviour would be identical here, but i would then be
           invisible after the loop.
   ```

   - Points the question is testing: the `comma operator` in the update section, a `compound condition` with `&&`, and the fact that a variable declared before the loop `survives` it — after the loop, `i` is 3 and `j` is out of scope.

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

   Answer: The output is
   ```
      a=100 ,b=100
   ```

   Why b is 100 and not 200
   - The bug is in `getValues`:
   ```cpp
      void getValues(int x, int y) {
          set_a(x);      // passes x  = 100   correct
          set_b(x);      // passes x  again!  should be set_b(y)
      }
   ```
   - `set_b(x)` is called instead of `set_b(y)`, so `b` receives 100 as well. The parameter `y` is never used at all.

   Trace
   ```
      objA.getValues(100, 200)
           x = 100 , y = 200

           set_a(x)  ->  set_a(100)  ->  this->a = 100
           set_b(x)  ->  set_b(100)  ->  this->b = 100      <- y ignored

      objA.putValues()
           prints  a=100 ,b=100
   ```

   The corrected program
   ```cpp
      void getValues(int x, int y) {
          set_a(x);
          set_b(y);        // now b gets 200
      }
   ```
   ```
      Corrected output :  a=100 ,b=200
   ```

   Other points the program demonstrates

   `Private member functions`
   ```cpp
      private:
          void set_a(int a) { this->a = a; }
          void set_b(int b) { this->b = b; }
   ```
   - `set_a` and `set_b` are `private`, so they cannot be called from `main`:
   ```cpp
      objA.set_a(100);      // COMPILE ERROR - set_a is private
   ```
   - But a `public` member function of the same class `can` call them, which is exactly what `getValues()` does. This is legal and is a normal way to keep an internal helper hidden while exposing a controlled public entry point.

   `The this pointer`
   ```cpp
      void set_a(int a) { this->a = a; }
   ```
   - The parameter `a` and the data member `a` have the same name, so the parameter `shadows` the member. `this->a` refers unambiguously to the member. Without `this->`, the statement `a = a;` would assign the parameter to itself and leave the member uninitialised.

   `Encapsulation`
   - `a` and `b` are private, so `main` cannot touch them directly:
   ```cpp
      objA.a = 500;         // COMPILE ERROR
   ```
   - Everything must go through `getValues()` and `putValues()`.

   A note on the code as printed
   ```
      The program is missing  #include <iostream>  before
      'using namespace std;'. Without it, cout and endl are undefined
      and the program will not compile.
   ```

   - The lesson the question is teaching: a `copy-paste error` of exactly this kind — passing the wrong parameter — compiles cleanly and produces a silently wrong result. It is the sort of bug that unit tests catch and the compiler cannot.

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

   Answer: The output is
   ```
      false
      false
      true
   ```

   The code
   ```java
      String s1 = "test1";                    // string LITERAL  -> string pool
      String s2 = new String("test1");        // new  -> a fresh HEAP object

      System.out.println(s1 == s2);           // false
      String s3 = new String("test1");        // another fresh HEAP object
      System.out.println(s2 == s3);           // false
      s3 = s1;                                // s3 now points where s1 points
      System.out.println(s3 == s1);           // true
   ```

   Why — `==` compares references, not contents
   ```
      ==       compares whether two references point to the SAME object
      .equals() compares the CONTENTS of the two strings
   ```

   Memory picture
   ```
      ---- String pool ----          ---- Heap ----
         "test1"  <---- s1              [ "test1" ]  <---- s2
             ^                          [ "test1" ]  <---- s3
             |
           s3 (after s3 = s1)
   ```

   Line by line
   ```
      1. String s1 = "test1";
           A literal. The JVM interns it in the STRING POOL and s1 points there.

      2. String s2 = new String("test1");
           'new' ALWAYS creates a fresh object on the heap, even though an
           identical string already exists in the pool.

      3. s1 == s2   ->  FALSE
           Different objects : one in the pool, one on the heap.

      4. String s3 = new String("test1");
           Another fresh heap object, separate from s2.

      5. s2 == s3   ->  FALSE
           Two distinct heap objects, with identical contents.

      6. s3 = s1;
           s3 now holds the same REFERENCE as s1 - both point to the pooled
           "test1". The old heap object s3 pointed to becomes garbage.

      7. s3 == s1   ->  TRUE
           The same object, so the same reference.
   ```

   What `.equals()` would have given
   ```java
      s1.equals(s2)      // TRUE  - the contents are identical
      s2.equals(s3)      // TRUE
      s3.equals(s1)      // TRUE
   ```
   - All three are true, because `equals()` compares character by character.

   The string pool, demonstrated
   ```java
      String a = "hello";
      String b = "hello";
      System.out.println(a == b);        // TRUE - both point to the pooled object

      String c = new String("hello");
      System.out.println(a == c);        // FALSE - c is a new heap object

      String d = c.intern();             // put/find it in the pool
      System.out.println(a == d);        // TRUE
   ```

   The practical rule
   ```
      ALWAYS compare strings with .equals() , never with ==

      if (name == "Rahim")        // WRONG - may be false even when the
                                  //         text matches
      if (name.equals("Rahim"))   // CORRECT
      if ("Rahim".equals(name))   // BEST - also safe when name is null
   ```
   - Comparing with `==` sometimes appears to work, because literals are pooled. That is exactly what makes it dangerous: the bug shows up only when the string came from user input, a file or a database rather than from a literal.

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

   Answer: The program as printed will `not compile`, because the array is declared as `number` but referred to as `numbers` inside the loop. Once that typing error is corrected, the output is the following.

   Output
   ```
      The chosen number, 4, isacceptable
      The chosen number, 8, isacceptable
      The chosen number, 12, isacceptable
      The chosen number, 21, isacceptable
      The chosen number, 30, isacceptable
   ```
   - Note that `100` is never printed, because the loop condition is `i < 5` while the array holds `6` elements.
   - Note also the missing space: the string is `" is" + result(...)`, so it reads `isacceptable`.

   Why every number gives the same answer

   The method
   ```java
      public static int performOperations(int i) {
          int original = i;
          return i = ((10 + (i * 2)) / 2 - original);
      }
   ```
   Simplify it algebraically
   ```
      (10 + 2i) / 2 - i
           = 5 + i - i
           = 5
   ```
   - The result is `always 5`, whatever `i` is. The `i * 2` and the `/ 2` cancel exactly, and subtracting `original` removes the remaining `i`.

   Verification for each element
   ```
      i = 4   :  (10 + 8)/2  - 4  = 9  - 4  = 5
      i = 8   :  (10 + 16)/2 - 8  = 13 - 8  = 5
      i = 12  :  (10 + 24)/2 - 12 = 17 - 12 = 5
      i = 21  :  (10 + 42)/2 - 21 = 26 - 21 = 5
      i = 30  :  (10 + 60)/2 - 30 = 35 - 30 = 5
   ```
   - Integer division causes no trouble here, because `10 + 2i` is always even.

   The switch then always takes the same branch
   ```java
      switch (5) {
          case 3: ... 
          case 5: result = "acceptable"; break;      // <- always this one
          case 7: ...
          default: ...
      }
   ```

   The three defects in the program
   ```
      1. numbers[i] should be number[i]        -> compile error as written

      2. i < 5 should be i < number.length     -> the last element (100)
                                                  is silently skipped

      3. " is" + result(...)                   -> missing a space, so the
                                                  output reads "isacceptable"
   ```

   The corrected program
   ```java
   public class WhatTheOutput {

       public static int performOperations(int i) {
           int original = i;
           return ((10 + (i * 2)) / 2) - original;
       }

       public static String result(int i) {
           switch (i) {
               case 3:  return "a multiple of 3";
               case 5:  return "acceptable";
               case 7:  return "a multiple of 7";
               default: return "unacceptable";
           }
       }

       public static void main(String[] args) {
           int[] number = {4, 8, 12, 21, 30, 100};

           for (int i = 0; i < number.length; i++) {
               System.out.println("The chosen number, " + number[i] +
                                  ", is " + result(performOperations(number[i])));
           }
       }
   }
   ```
   Corrected output
   ```
      The chosen number, 4, is acceptable
      The chosen number, 8, is acceptable
      The chosen number, 12, is acceptable
      The chosen number, 21, is acceptable
      The chosen number, 30, is acceptable
      The chosen number, 100, is acceptable
   ```

   - What the question is really testing: whether the candidate `simplifies the expression` instead of computing it six times. Once `(10 + 2i)/2 - i = 5` is seen, the whole program collapses to a single answer. It is also testing the habit of using `array.length` rather than a hard-coded bound.

10. **You are required to trace the changes in value for each of the numbers, before and after each method are called for each of iterations and finally write down output of the program.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1195-1196 (ET: N/A)]*

    Answer: The question is `incomplete` — the program whose values were to be traced is not present. The complete method for tracing a program, and the traces that such a question uses, are given below.

    How to trace a program
    ```
       1. Draw a TABLE with one column per variable, plus a column for
          the output.
       2. Write the INITIAL value of every variable.
       3. Work through the code ONE STATEMENT at a time, updating the table
          after each statement.
       4. Note the values BEFORE and AFTER every method call.
       5. Record every print statement in the output column, in order.
    ```

    Trace 1 — pass by value, the commonest such question
    ```java
    public class Main {
        static void change(int x) {
            System.out.println("  inside, before: " + x);
            x = x * 2;
            System.out.println("  inside, after : " + x);
        }
        public static void main(String[] args) {
            int a = 10;
            System.out.println("before call: " + a);
            change(a);
            System.out.println("after call : " + a);
        }
    }
    ```
    ```
       Iteration   a (caller)   x (callee)   output
       ---------   ----------   ----------   -----------------------
       start           10            -       before call: 10
       enter change    10           10         inside, before: 10
       x = x*2         10           20         inside, after : 20
       return          10            -       after call : 10
    ```
    ```
       Output :
          before call: 10
            inside, before: 10
            inside, after : 20
          after call : 10

       Java passes PRIMITIVES BY VALUE. change() works on a COPY, so the
       caller's 'a' is untouched. This is the whole point of the question.
    ```

    Trace 2 — an object reference, where the caller IS affected
    ```java
    class Box { int value; }

    public class Main {
        static void change(Box b) { b.value = 99; }
        static void reassign(Box b) { b = new Box(); b.value = 500; }

        public static void main(String[] args) {
            Box box = new Box();
            box.value = 10;
            System.out.println("before  : " + box.value);   // 10
            change(box);
            System.out.println("after change  : " + box.value);   // 99
            reassign(box);
            System.out.println("after reassign: " + box.value);   // 99
        }
    }
    ```
    ```
       change()   MODIFIES the object the reference points to  -> 99
       reassign() rebinds the LOCAL copy of the reference, so the caller's
                  object is untouched  -> still 99

       Java is ALWAYS pass by value. What is passed by value for an object
       is the REFERENCE, not the object itself.
    ```

    Trace 3 — a loop with a swap in each iteration
    ```java
    public class Main {
        static void swap(int[] a, int i, int j) {
            int t = a[i]; a[i] = a[j]; a[j] = t;
        }
        public static void main(String[] args) {
            int[] a = {5, 3, 8, 1};
            for (int i = 0; i < a.length - 1; i++)
                for (int j = 0; j < a.length - 1 - i; j++)
                    if (a[j] > a[j+1]) swap(a, j, j+1);
            for (int x : a) System.out.print(x + " ");
        }
    }
    ```
    ```
       Pass 1 :  5 3 8 1  ->  3 5 8 1  ->  3 5 8 1  ->  3 5 1 8
       Pass 2 :  3 5 1 8  ->  3 5 1 8  ->  3 1 5 8
       Pass 3 :  3 1 5 8  ->  1 3 5 8

       Output : 1 3 5 8

       ARRAYS are objects, so swap() DOES change the caller's array.
    ```

    Trace 4 — a static variable across several calls
    ```java
    public class Main {
        static int count = 0;
        static void increment() { count++; System.out.print(count + " "); }
        public static void main(String[] args) {
            increment(); increment(); increment();
            System.out.println("| final = " + count);
        }
    }
    ```
    ```
       Call   count before   count after   output
       ----   ------------   -----------   ------
        1          0              1          1
        2          1              2          2
        3          2              3          3

       Output : 1 2 3 | final = 3

       A static field belongs to the CLASS, so all calls share one copy.
    ```

    The rules such questions test
    ```
       Java is ALWAYS pass by value.
            - For a PRIMITIVE, the value is copied -> the caller is unaffected.
            - For an OBJECT, the REFERENCE is copied -> the object CAN be
              modified, but REASSIGNING the parameter cannot affect the caller.

       A STATIC variable is shared by every call ; a LOCAL variable is
            created fresh each time.

       Arrays are objects, so a method CAN change their contents.

       Strings are IMMUTABLE, so a method can never change the caller's
            string - it can only return a new one.
    ```

## Constructors & Destructors (8)

1. **What is constructor function? Write the properties of it.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 505 (ET: N/A)]*

   Answer: A `constructor` is a special member function that is called `automatically` when an object is created. Its job is to `initialise` the object, so that it is never used in an uninitialised state.

   ```java
   class Student {
       String name;
       int    roll;

       Student(String name, int roll) {      // constructor
           this.name = name;
           this.roll = roll;
       }
   }

   Student s = new Student("Rahim", 101);    // the constructor runs here
   ```

   Properties of a constructor
   ```
      1. Its NAME is exactly the same as the class name.

      2. It has NO RETURN TYPE - not even void. Writing a return type
         turns it into an ordinary method, which is a classic silent bug :

              void Student() { ... }     // this is a METHOD, not a constructor

      3. It is called AUTOMATICALLY when the object is created; it cannot
         be called explicitly like a normal method.

      4. It is called ONLY ONCE per object, at the moment of creation.

      5. It can be OVERLOADED - several constructors with different
         parameter lists, so an object can be created in different ways.

      6. It can take PARAMETERS, but cannot return a value.

      7. It CANNOT be inherited, though a subclass constructor calls its
         parent's with super(...).

      8. It CANNOT be virtual, static, final or abstract.

      9. If NO constructor is written, the compiler supplies a DEFAULT
         no-argument constructor that sets fields to their default values
         (0, 0.0, false, null).

     10. Once ANY constructor is written, that free default constructor
         disappears. This causes the common error "constructor X in class X
         cannot be applied to given types" when 'new X()' is then used.

     11. It is usually PUBLIC, but may be private - which is how the
         Singleton pattern prevents outside code from creating objects.
   ```

   Types of constructor
   ```java
   class Student {
       String name;  int roll;

       // 1. DEFAULT (no-argument) constructor
       Student() {
           name = "Unknown";
           roll = 0;
       }

       // 2. PARAMETERISED constructor
       Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
       }

       // 3. COPY constructor - build one object from another
       Student(Student other) {
           this.name = other.name;
           this.roll = other.roll;
       }
   }
   ```
   ```java
      Student s1 = new Student();                  // default
      Student s2 = new Student("Rahim", 101);      // parameterised
      Student s3 = new Student(s2);                // copy
   ```

   Constructor chaining
   ```java
   class Student {
       String name;  int roll;  double cgpa;

       Student() {
           this("Unknown", 0, 0.0);       // this(...) calls another constructor
       }
       Student(String name, int roll, double cgpa) {
           this.name = name;  this.roll = roll;  this.cgpa = cgpa;
       }
   }
   ```
   - `this(...)` calls another constructor of the `same` class; `super(...)` calls the `parent's`. Either must be the `first statement`.

   - The complementary function is the `destructor`. C++ has one, `~ClassName()`, called automatically when the object is destroyed. Java has none, because the `garbage collector` frees memory; cleanup is done with `try-with-resources` instead.

2. **Define copy constructor. What Static binding and Dynamic binding?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

   Answer: Copy constructor
   - A `copy constructor` creates a new object as a `copy of an existing object of the same class`. It takes a single parameter: a reference to another object of that class.
   ```cpp
      ClassName(const ClassName &obj) { ... }
   ```

   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
   private:
       char* name;
       int roll;

   public:
       // parameterised constructor
       Student(const char* n, int r) {
           roll = r;
           name = new char[strlen(n) + 1];
           strcpy(name, n);
       }

       // COPY CONSTRUCTOR - deep copy
       Student(const Student &other) {
           roll = other.roll;
           name = new char[strlen(other.name) + 1];   // NEW memory
           strcpy(name, other.name);                  // copy the CONTENTS
       }

       ~Student() { delete[] name; }

       void display() { cout << roll << " - " << name << endl; }
   };

   int main() {
       Student s1("Rahim", 101);
       Student s2 = s1;          // the COPY CONSTRUCTOR is called here
       Student s3(s1);           // and here

       s2.display();             // 101 - Rahim
       return 0;
   }
   ```

   When it is called
   ```
      1. Student s2 = s1;             initialising one object from another
      2. Student s3(s1);              explicit construction
      3. passing an object BY VALUE to a function
      4. returning an object BY VALUE from a function
   ```

   Why it matters — shallow versus deep copy
   ```
      If no copy constructor is written, C++ supplies a DEFAULT one that
      copies member by member - a SHALLOW copy.

      With a pointer member, both objects then point to the SAME memory :

           s1.name ----+
                       +----> "Rahim"
           s2.name ----+

      Consequences : changing one changes the other, and when both
      destructors run, the same memory is deleted TWICE - a crash.

      A user-written copy constructor allocates NEW memory and copies the
      contents - a DEEP copy - so the two objects are independent.
   ```
   - The `rule of three` in C++: a class that needs a destructor almost certainly needs a copy constructor and a copy assignment operator too.
   - Java has no copy constructor keyword; the same effect is written by hand, or `clone()` is used, though a hand-written copy constructor is preferred.

   Static binding versus dynamic binding
   - `Binding` means connecting a method call to the actual method body that will run. The question is `when` that connection is made.

   `Static binding` (early binding, compile-time binding)
   - Decided by the `compiler`, from the `declared type` of the reference.
   - Applies to methods that cannot be overridden:
   ```
      static methods , private methods , final methods ,
      overloaded methods , and all FIELDS
   ```

   `Dynamic binding` (late binding, runtime binding)
   - Decided by the `JVM` at run time, from the `actual object`.
   - Applies to `overridden` instance methods, and is what makes runtime polymorphism possible.

   Example showing both
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

           b.instanceMethod();      // "Derived instance"  -> DYNAMIC binding
           b.staticMethod();        // "Base static"       -> STATIC binding
           System.out.println(b.x); // 10                  -> STATIC binding
       }
   }
   ```

   Comparison

   | Point | Static binding | Dynamic binding |
   |---|---|---|
   | Also called | Early binding | Late binding |
   | Decided at | Compile time | Run time |
   | Decided by | The compiler | The JVM |
   | Based on | The reference type | The actual object |
   | Applies to | static, private, final, overloaded methods, fields | Overridden instance methods |
   | Speed | Faster — no lookup | Slightly slower — a vtable lookup |
   | Polymorphism | Compile-time (overloading) | Runtime (overriding) |
   | C++ equivalent | Non-virtual functions | `virtual` functions |

   - The trap to remember: `fields and static methods are never polymorphic`. Only overridden instance methods are chosen by the object.

3. **What is the constructor invoked in OOP?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

   Answer: A `constructor` is invoked `automatically at the moment an object is created` — that is, when the `new` keyword allocates memory for the object.
   ```java
      Student s = new Student("Rahim", 101);
                    ^^^
                    the constructor runs here, immediately after the memory
                    is allocated and before the reference is handed back
   ```

   The exact sequence
   ```
      1. 'new' allocates memory on the heap for the object
      2. All fields are set to their DEFAULT values (0, 0.0, false, null)
      3. If the class has a superclass, super(...) runs first, so the
         PARENT is fully constructed before the child
      4. Instance initialiser blocks and field initialisers run, in the
         order they appear in the source
      5. The constructor BODY runs
      6. The reference to the finished object is returned
   ```

   Order in an inheritance chain
   ```java
   class A {
       A() { System.out.println("A's constructor"); }
   }
   class B extends A {
       B() { System.out.println("B's constructor"); }
   }
   class C extends B {
       C() { System.out.println("C's constructor"); }
   }

   public class Main {
       public static void main(String[] args) {
           new C();
       }
   }
   ```
   Output
   ```
      A's constructor
      B's constructor
      C's constructor
   ```
   - Construction proceeds `top-down`: the most general class is built first, so a subclass constructor can safely rely on its parent's fields already being initialised. In C++ `destruction` then happens in the opposite order, bottom-up.

   Other occasions on which a constructor is invoked
   ```java
      new Student(...)              // 1. the normal case

      Student[] a = new Student[3]; // NO constructor runs - only 3 null
                                    //    references are created
      a[0] = new Student(...);      //    the constructor runs HERE

      Class.forName("Student").newInstance();   // 2. reflection

      Student s2 = new Student(s1);             // 3. a copy constructor
   ```
   - Note that `new Student[3]` does `not` call the constructor. It creates an array of three `null` references, and each element must still be given an object.

   When it is `not` invoked
   ```
      Deserialization - reading an object back from a stream does NOT call
           the constructor; the fields are restored directly

      clone() - copies the fields without running the constructor

      A static method call on the class does not create an object at all
   ```

   Points worth noting
   ```
      The constructor has the SAME NAME as the class and NO return type
      It runs exactly ONCE per object
      It cannot be called explicitly like an ordinary method
      this(...) calls another constructor of the same class, and
           super(...) calls the parent's - either must be the FIRST statement
      If no constructor is written, the compiler supplies a default one;
           writing any constructor removes that free default
   ```

4. **What is constructor?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

   Answer: A `constructor` is a special member function that is called `automatically` when an object is created. Its purpose is to `initialise` the object, so that it is never used in an uninitialised state.

   ```java
   class Student {
       String name;
       int    roll;

       Student(String name, int roll) {       // constructor
           this.name = name;
           this.roll = roll;
       }
   }

   Student s = new Student("Rahim", 101);     // the constructor runs here
   ```

   Key properties
   ```
      Same NAME as the class
      NO return type - not even void
      Called AUTOMATICALLY at object creation, exactly once
      Can be OVERLOADED, so an object can be created in several ways
      Cannot be inherited, virtual, static, final or abstract
      If none is written, the compiler supplies a default no-argument one;
           writing any constructor removes that free default
   ```

   Types
   ```java
   class Student {
       String name;  int roll;

       Student() {                            // 1. DEFAULT constructor
           name = "Unknown";  roll = 0;
       }

       Student(String name, int roll) {       // 2. PARAMETERISED constructor
           this.name = name;  this.roll = roll;
       }

       Student(Student other) {               // 3. COPY constructor
           this.name = other.name;  this.roll = other.roll;
       }
   }
   ```
   ```java
      Student s1 = new Student();                 // default
      Student s2 = new Student("Rahim", 101);     // parameterised
      Student s3 = new Student(s2);               // copy
   ```

   Why a constructor is needed
   ```
      WITHOUT one, an object starts with default values and every caller
      must remember to set each field :

           Student s = new Student();
           s.name = "Rahim";
           s.roll = 101;          // easy to forget one, leaving it invalid

      WITH one, the object cannot exist in an incomplete state :

           Student s = new Student("Rahim", 101);
   ```
   - It also gives one place to `validate` the initial values, which is exactly what encapsulation requires.

   The complementary function
   ```
      C++  : ~ClassName()  - the DESTRUCTOR, called automatically when the
             object goes out of scope or is deleted. Used to release memory
             and other resources.

      Java : no destructor. The GARBAGE COLLECTOR frees memory, and
             try-with-resources handles other cleanup.
   ```

5. **(b) Why are constructor and destructor functions used in object oriented programming? Give examples of each function in C++ or java language.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

   Answer: Why constructors are used
   - To `initialise an object automatically` at the moment it is created, so it can never be used in an incomplete or invalid state.
   - To give a `single place to validate` the initial values, which is what encapsulation requires.
   - To allow an object to be created in `several ways`, through constructor overloading.
   - To `acquire the resources` the object needs — open a file, obtain a connection, allocate memory.
   - To ensure the `parent part` of an inherited object is built first, through `super(...)`.

   Why destructors are used
   - To `release the resources` the object acquired, at the moment it is destroyed.
   - To `free dynamically allocated memory`, which in C++ the programmer must do explicitly.
   - To close files, sockets and database connections deterministically.
   - Without one, a program that creates and destroys many objects `leaks memory` until it exhausts the heap.

   C++ example — both together
   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
   private:
       char* name;
       int   roll;

   public:
       // ---------- CONSTRUCTOR ----------
       Student(const char* n, int r) {
           roll = r;
           name = new char[strlen(n) + 1];      // acquire memory
           strcpy(name, n);
           cout << "Constructor called for " << name << endl;
       }

       // ---------- DESTRUCTOR ----------
       ~Student() {
           cout << "Destructor called for " << name << endl;
           delete[] name;                       // release memory
       }

       void display() { cout << roll << " - " << name << endl; }
   };

   int main() {
       cout << "--- entering block ---" << endl;
       {
           Student s1("Rahim", 101);
           Student s2("Karim", 102);
           s1.display();
           s2.display();
       }                                  // both destructors run HERE
       cout << "--- left block ---" << endl;
       return 0;
   }
   ```
   Output
   ```
      --- entering block ---
      Constructor called for Rahim
      Constructor called for Karim
      101 - Rahim
      102 - Karim
      Destructor called for Karim
      Destructor called for Rahim
      --- left block ---
   ```
   - Note that destruction happens in `reverse order` of construction — the last object created is the first destroyed, because the objects live on the stack.

   Java example — constructor, and cleanup without a destructor
   ```java
   class Student {
       String name;
       int    roll;

       // ---------- CONSTRUCTOR ----------
       Student(String name, int roll) {
           this.name = name;
           this.roll = roll;
           System.out.println("Constructor called for " + name);
       }

       void display() { System.out.println(roll + " - " + name); }
   }

   public class Main {
       public static void main(String[] args) {
           Student s = new Student("Rahim", 101);
           s.display();
           s = null;                 // now eligible for garbage collection
       }
   }
   ```
   - Java has `no destructor`. The `garbage collector` frees the memory at some unspecified later time, so cleanup of other resources is done with `try-with-resources`:
   ```java
      try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
          System.out.println(br.readLine());
      }   // br.close() runs here automatically, even if an exception is thrown
   ```
   - `finalize()` existed for this purpose but was deprecated in Java 9 and removed in Java 18, because it gave no guarantee of when — or whether — it would run.

   Comparison

   | Point | Constructor | Destructor |
   |---|---|---|
   | Purpose | Initialise, acquire resources | Clean up, release resources |
   | Name | Same as the class | `~ClassName` |
   | Called when | The object is created | The object is destroyed |
   | Parameters | Allowed | `Never` |
   | Overloading | Allowed | `Not allowed` — only one per class |
   | Return type | None | None |
   | Order in a hierarchy | Base first, then derived | Derived first, then base |
   | In Java | Yes | `No` — the GC frees memory instead |

6. **What is Constructor function? Write an example of Constructor function?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*

   Answer: A `constructor` is a special member function that is called `automatically` when an object is created, in order to `initialise` it.
   ```
      Same NAME as the class
      NO return type, not even void
      Called AUTOMATICALLY, exactly once per object
      Can be OVERLOADED, so objects can be created in several ways
      Cannot be inherited, static, final or virtual
   ```

   Example — all three kinds of constructor in one class
   ```java
   class BankAccount {

       private String accountNumber;
       private String holderName;
       private double balance;

       // ---- 1. DEFAULT (no-argument) constructor ----
       public BankAccount() {
           accountNumber = "UNKNOWN";
           holderName    = "UNKNOWN";
           balance       = 0.0;
           System.out.println("Default constructor called");
       }

       // ---- 2. PARAMETERISED constructor ----
       public BankAccount(String accNo, String name, double opening) {
           accountNumber = accNo;
           holderName    = name;
           balance       = (opening > 0) ? opening : 0;   // validation
           System.out.println("Parameterised constructor called");
       }

       // ---- 3. COPY constructor ----
       public BankAccount(BankAccount other) {
           this.accountNumber = other.accountNumber;
           this.holderName    = other.holderName;
           this.balance       = other.balance;
           System.out.println("Copy constructor called");
       }

       public void display() {
           System.out.println(accountNumber + " | " + holderName +
                              " | " + balance);
       }
   }

   public class Main {
       public static void main(String[] args) {

           BankAccount a1 = new BankAccount();
           a1.display();

           BankAccount a2 = new BankAccount("AC1001", "Rahim Uddin", 5000);
           a2.display();

           BankAccount a3 = new BankAccount(a2);        // copy of a2
           a3.display();
       }
   }
   ```

   Output
   ```
      Default constructor called
      UNKNOWN | UNKNOWN | 0.0
      Parameterised constructor called
      AC1001 | Rahim Uddin | 5000.0
      Copy constructor called
      AC1001 | Rahim Uddin | 5000.0
   ```

   C++ version, with a destructor as well
   ```cpp
   #include <iostream>
   using namespace std;

   class BankAccount {
   private:
       string accountNumber;
       double balance;

   public:
       BankAccount() {                                  // default
           accountNumber = "UNKNOWN";
           balance = 0;
       }

       BankAccount(string accNo, double opening) {      // parameterised
           accountNumber = accNo;
           balance = (opening > 0) ? opening : 0;
       }

       ~BankAccount() {                                 // DESTRUCTOR
           cout << "Account " << accountNumber << " closed" << endl;
       }

       void display() { cout << accountNumber << " : " << balance << endl; }
   };
   ```

   Constructor chaining with `this(...)`
   ```java
   class Student {
       String name;  int roll;  double cgpa;

       Student() {
           this("Unknown", 0, 0.0);          // calls the three-argument one
       }
       Student(String name, int roll, double cgpa) {
           this.name = name;  this.roll = roll;  this.cgpa = cgpa;
       }
   }
   ```
   - `this(...)` calls another constructor of the same class; `super(...)` calls the parent's. Either must be the `first statement` in the constructor.

   Common mistakes
   ```java
      void Student() { ... }        // a METHOD, not a constructor -
                                    // the return type gives it away

      class Student {
          Student(String n) { ... } // once ANY constructor is written,
      }                             // the free default one disappears

      Student s = new Student();    // COMPILE ERROR - no such constructor
   ```

7. **Differentiate constructor and destructor with example.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1167-1168 (ET: N/A)]*

   Answer: A `constructor` initialises an object when it is created; a `destructor` cleans it up when it is destroyed. They are the two ends of an object's life.

   Constructor
   ```
      Same NAME as the class
      No return type
      Called AUTOMATICALLY when the object is created
      May take parameters, and may be OVERLOADED
      Purpose : initialise the fields, acquire resources
   ```

   Destructor
   ```
      Name is  ~ClassName  - the class name preceded by a tilde
      No return type and NO PARAMETERS
      Called AUTOMATICALLY when the object goes out of scope or is deleted
      Only ONE per class - it cannot be overloaded
      Purpose : release memory and other resources
   ```

   C++ example showing both
   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   class Student {
   private:
       char* name;
       int   roll;

   public:
       // ---------- CONSTRUCTOR ----------
       Student(const char* n, int r) {
           roll = r;
           name = new char[strlen(n) + 1];         // ACQUIRE memory
           strcpy(name, n);
           cout << "Constructor : " << name << " created" << endl;
       }

       // ---------- DESTRUCTOR ----------
       ~Student() {
           cout << "Destructor  : " << name << " destroyed" << endl;
           delete[] name;                          // RELEASE memory
       }

       void display() { cout << roll << " - " << name << endl; }
   };

   int main() {
       cout << "--- entering block ---" << endl;
       {
           Student s1("Rahim", 101);
           Student s2("Karim", 102);
           s1.display();
           s2.display();
       }                                  // both destructors run HERE
       cout << "--- left block ---" << endl;
       return 0;
   }
   ```
   Output
   ```
      --- entering block ---
      Constructor : Rahim created
      Constructor : Karim created
      101 - Rahim
      102 - Karim
      Destructor  : Karim destroyed
      Destructor  : Rahim destroyed
      --- left block ---
   ```
   - Note the `reverse order` of destruction: the last object created is destroyed first, because objects on the stack are removed in LIFO order.

   Difference

   | Point | Constructor | Destructor |
   |---|---|---|
   | Purpose | Initialise, acquire resources | Clean up, release resources |
   | Name | Same as the class | `~ClassName` |
   | Called when | The object is created | The object is destroyed |
   | Parameters | Allowed | `Never` |
   | Overloading | Allowed | `Not allowed` — only one |
   | Return type | None | None |
   | Number per class | Many (overloaded) | Exactly one |
   | Order in a hierarchy | Base first, then derived | Derived first, then base |
   | Can be virtual | No | `Yes`, and it usually should be |
   | Called explicitly | No | Rarely, and only in unusual cases |
   | In Java | Yes | `No` — the garbage collector frees memory |

   Why a base destructor should be `virtual`
   ```cpp
      class Base  { public: ~Base()  { } };            // NOT virtual
      class Derived : public Base { public: ~Derived() { } };

      Base* p = new Derived();
      delete p;          // only ~Base() runs - ~Derived() is SKIPPED
                         // any resource the Derived part held is LEAKED
   ```
   - Declaring `virtual ~Base()` makes `delete p` run `~Derived()` first and then `~Base()`, which is correct. This is a standard rule for any class meant to be inherited from.

   The Java position
   ```
      Java has NO destructor. The garbage collector frees memory
      automatically at an unspecified later time.

      For other resources - files, sockets, connections - use
      try-with-resources :

           try (BufferedReader br = new BufferedReader(new FileReader(f))) {
               ...
           }   // close() runs here automatically

      finalize() existed for this purpose but was deprecated in Java 9
      and REMOVED in Java 18, because it guaranteed neither when nor
      whether it would run.
   ```

8. **What is main difference Destructor and constructor with example?** *[Palli Sanchay Bank Programmer 2018 compact it 1171 (ET: N/A)]*

   Answer: The main difference is `purpose and timing`: a constructor `builds` an object when it is created, and a destructor `cleans it up` when it is destroyed.
   ```
      CONSTRUCTOR : initialise fields, acquire resources   -> at creation
      DESTRUCTOR  : release those resources                -> at destruction
   ```

   Constructor
   ```
      Same NAME as the class
      No return type
      May take parameters, and may be OVERLOADED
      Called automatically when the object is created
   ```

   Destructor
   ```
      Name is  ~ClassName
      No return type and NO PARAMETERS
      Cannot be overloaded - exactly ONE per class
      Called automatically when the object goes out of scope or is deleted
   ```

   C++ example
   ```cpp
   #include <iostream>
   using namespace std;

   class FileHandler {
   private:
       string filename;
       int*   buffer;

   public:
       // ---------- CONSTRUCTOR ----------
       FileHandler(string fname, int size) {
           filename = fname;
           buffer   = new int[size];            // ACQUIRE
           cout << "Constructor: opened " << filename << endl;
       }

       // ---------- DESTRUCTOR ----------
       ~FileHandler() {
           delete[] buffer;                     // RELEASE
           cout << "Destructor : closed " << filename << endl;
       }
   };

   int main() {
       cout << "start" << endl;
       {
           FileHandler f1("data.txt", 100);
           FileHandler f2("log.txt", 50);
       }                                        // destructors run HERE
       cout << "end" << endl;
       return 0;
   }
   ```
   Output
   ```
      start
      Constructor: opened data.txt
      Constructor: opened log.txt
      Destructor : closed log.txt
      Destructor : closed data.txt
      end
   ```
   - Destruction is in `reverse order` of construction — the objects live on the stack, which is LIFO.

   Full comparison

   | Point | Constructor | Destructor |
   |---|---|---|
   | Purpose | Initialise and acquire | Clean up and release |
   | Name | Same as the class | `~ClassName` |
   | When called | Object creation | Object destruction |
   | Parameters | Allowed | `Never` |
   | Overloading | Allowed | `Not allowed` |
   | Return type | None | None |
   | Number per class | Many | Exactly one |
   | Order in inheritance | Base -> Derived | Derived -> Base |
   | Can be virtual | No | Yes, and usually should be |
   | Present in Java | Yes | No |

   What happens without a destructor
   ```cpp
      class Student {
          char* name;
      public:
          Student(const char* n) { name = new char[strlen(n)+1]; strcpy(name,n); }
          // NO destructor
      };

      for (int i = 0; i < 1000000; i++) {
          Student s("Rahim");     // each object leaks its char array
      }                           // -> the program eventually runs out of memory
   ```
   - This is a `memory leak`. In C++ the programmer must release what was acquired; in Java the garbage collector does it, which is why Java has no destructor at all.

   Java's replacement
   ```java
      try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
          System.out.println(br.readLine());
      }   // close() runs here automatically, even if an exception is thrown
   ```
   - `try-with-resources` gives the deterministic cleanup that a C++ destructor provides, without the risk of forgetting it.

## Encapsulation & Access Modifiers (7)

1. **You have three access specifiers in java object oriented language. You have to find which access specifiers are worked with Public, Private and Protected Mode. If yes you have to right Y and if No you have to write N.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

   Answer: Java has `four` access levels, of which three have keywords — `public`, `private` and `protected` — plus the `default` (package-private) level, which has no keyword.

   The access table, marked Y (accessible) and N (not accessible)
   ```
      Accessible from        | private | default | protected | public
      -----------------------+---------+---------+-----------+--------
      Same class             |    Y    |    Y    |     Y     |   Y
      Same package,          |    N    |    Y    |     Y     |   Y
        non-subclass         |         |         |           |
      Same package, subclass |    N    |    Y    |     Y     |   Y
      Different package,     |    N    |    N    |     Y     |   Y
        SUBCLASS             |         |         |           |
      Different package,     |    N    |    N    |     N     |   Y
        non-subclass         |         |         |           |
   ```

   For the three named specifiers only

   | Accessible from | `public` | `private` | `protected` |
   |---|---|---|---|
   | Within the same class | `Y` | `Y` | `Y` |
   | Another class, same package | `Y` | `N` | `Y` |
   | Subclass in the same package | `Y` | `N` | `Y` |
   | Subclass in a different package | `Y` | `N` | `Y` |
   | Non-subclass, different package | `Y` | `N` | `N` |

   What each means
   ```
      public    : visible EVERYWHERE - any class, any package.
                  The widest access.

      protected : visible inside the class, throughout the same package,
                  AND to SUBCLASSES in other packages.
                  Designed for inheritance.

      default   : (no keyword) visible only within the SAME PACKAGE.
                  Also called package-private.

      private   : visible ONLY inside the class that declares it.
                  The narrowest access, and the basis of encapsulation.
   ```

   Ordering from widest to narrowest
   ```
      public  >  protected  >  default  >  private
   ```

   Demonstration
   ```java
   package pack1;

   public class A {
       public    int p = 1;      // everywhere
       protected int q = 2;      // package + subclasses anywhere
                 int r = 3;      // package only (default)
       private   int s = 4;      // this class only

       void test() {
           System.out.println(p + " " + q + " " + r + " " + s);  // all Y
       }
   }
   ```
   ```java
   package pack2;
   import pack1.A;

   public class B extends A {          // a SUBCLASS in another package
       void test() {
           System.out.println(p);      // Y - public
           System.out.println(q);      // Y - protected, and B is a subclass
           // System.out.println(r);   // N - default, different package
           // System.out.println(s);   // N - private
       }
   }

   class C {                           // NOT a subclass, different package
       void test() {
           A a = new A();
           System.out.println(a.p);    // Y - public
           // System.out.println(a.q); // N - protected, and C is not a subclass
       }
   }
   ```

   Rules worth stating
   ```
      A top-level CLASS may only be public or default - never private
           or protected.

      A subclass CANNOT reduce the access of an overridden method :
           a public method cannot become protected in the subclass.
           It may WIDEN it.

      protected access from another package works only through
           INHERITANCE - a subclass may use its OWN inherited member,
           but not another object's.

      The rule of good design : make every field PRIVATE and expose
           behaviour through public methods. That is encapsulation.
   ```

2. **Explain the various types of access specifiers.** *[DESCO Assistant Engineer 20.05.2023 compact it 579 (ET: DESCO)]*

   Answer: An `access specifier` (access modifier) controls `where` a class member may be used. It is the mechanism by which `encapsulation` is actually enforced.

   Java has `four` levels
   ```
      public  >  protected  >  default  >  private
      widest                              narrowest
   ```

   1. `public`
   - Accessible from `everywhere` — any class, any package.
   - Used for the class's `interface`: the methods other code is meant to call.
   ```java
      public class Student {
          public void display() { ... }
      }
   ```

   2. `protected`
   - Accessible inside the class, throughout the `same package`, and to `subclasses in any package`.
   - Designed for inheritance: it lets a subclass reach the parent's internals while keeping unrelated classes out.
   ```java
      protected double balance;      // subclasses may use it directly
   ```

   3. `default` (package-private, no keyword)
   - Accessible only within the `same package`. Writing no specifier at all gives this level.
   ```java
      int roll;          // visible to other classes in the same package only
   ```

   4. `private`
   - Accessible `only inside the class` that declares it. The narrowest level, and the foundation of encapsulation.
   ```java
      private double balance;        // nothing outside can touch it
   ```

   Access table
   ```
      Accessible from             | private | default | protected | public
      ----------------------------+---------+---------+-----------+--------
      Same class                  |    Y    |    Y    |     Y     |   Y
      Same package, non-subclass  |    N    |    Y    |     Y     |   Y
      Same package, subclass      |    N    |    Y    |     Y     |   Y
      Other package, SUBCLASS     |    N    |    N    |     Y     |   Y
      Other package, non-subclass |    N    |    N    |     N     |   Y
   ```

   Example
   ```java
   public class BankAccount {

       private   double balance;         // only this class
       protected String accountType;     // this class + subclasses
                 String branchCode;      // same package only (default)
       public    String accountNumber;   // everywhere

       public void deposit(double amt) {          // public interface
           if (amt > 0) balance += amt;           // private data, validated
       }

       public double getBalance() { return balance; }

       private void auditLog(String msg) { ... }  // internal helper, hidden
   }
   ```

   C++ has `three` specifiers
   ```
      public    : accessible everywhere
      protected : the class and its derived classes
      private   : the class only  (the DEFAULT for a class)
   ```
   ```cpp
   class Student {
   private:                 // default for a class
       int roll;
   protected:
       string name;
   public:
       void display() { ... }
   };
   ```
   - In C++ the default for a `struct` is `public` and for a `class` is `private` — that is the only real difference between the two.
   - C++ also has `friend`, which lets a named function or class reach private members. Java has no equivalent.

   Rules and good practice
   ```
      A top-level class may only be public or default - never private
           or protected.

      An overriding method CANNOT reduce access :
           public in the parent cannot become protected in the child.

      protected across packages works only through INHERITANCE - a
           subclass may use its OWN inherited member, not another object's.

      DESIGN RULE : make every field PRIVATE and expose behaviour through
           public methods. Fields should almost never be public, because a
           public field can be set to any value by anyone, which destroys
           every invariant the class tries to maintain.
   ```

3. **Which type of variable violates encapsulation rules?** *[BCC Assistant Programmer 11.11.2023 compact it 544 (ET: N/A)], [BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: A `public instance variable` violates encapsulation.

   - `Encapsulation` requires that an object's data be `hidden` and reachable only through its own methods. A public field is directly readable and writable by any code anywhere, so the class loses all control over its own state.

   The problem
   ```java
   class BankAccount {
       public double balance;         // VIOLATES encapsulation
   }

   public class Main {
       public static void main(String[] args) {
           BankAccount acc = new BankAccount();

           acc.balance = -99999;      // legal! The account is now corrupt.
           acc.balance = 1000000;     // legal! Money created from nothing.
       }
   }
   ```
   - There is no validation, no audit trail and no way to stop it. Every rule the class was supposed to enforce is bypassed.

   The correct design
   ```java
   class BankAccount {
       private double balance;                    // hidden

       public void deposit(double amount) {
           if (amount > 0) balance += amount;     // VALIDATED
           else System.out.println("Invalid amount");
       }

       public void withdraw(double amount) {
           if (amount > 0 && amount <= balance) balance -= amount;
           else System.out.println("Insufficient balance");
       }

       public double getBalance() { return balance; }   // read-only access
   }
   ```
   ```java
      acc.balance = -99999;      // COMPILE ERROR - balance is private
      acc.deposit(-500);         // rejected by the validation
   ```

   Which variables violate encapsulation, ranked
   ```
      public    field  : the WORST - anyone anywhere can change it
      protected field  : weaker violation - any subclass, in any package,
                         can change it, so the parent cannot enforce its
                         own invariants
      default   field  : any class in the same package can change it
      private   field  : correct - encapsulation preserved
   ```

   Other ways encapsulation is broken, even with private fields
   ```java
      // 1. a setter with NO validation - private in name only
      public void setBalance(double b) { this.balance = b; }   // as bad as public

      // 2. returning a MUTABLE object directly
      private List<String> items;
      public List<String> getItems() { return items; }   // the caller can now
                                                         // modify the internal list
      // fix :
      public List<String> getItems() { return new ArrayList<>(items); }

      // 3. a public STATIC mutable field - shared global state, the worst of all
      public static int counter;
   ```

   The acceptable exception
   ```java
      public static final double PI = 3.14159;
   ```
   - A `public static final` constant of an immutable type is safe, because it can be read but never changed. `final` on a mutable object is `not` safe: the reference cannot be reassigned, but the object it points to can still be modified.

   - The rule to state: `make every field private and expose behaviour, not data`. Getters and setters are then the single controlled entry point, where validation, logging and future changes of representation can all live.

4. **Which members of base class cannot access to derived class?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: The `private` members of a base class cannot be accessed by a derived class.

   - A `private` member belongs to the class that declares it and to nothing else — not even to its own subclasses. This is what keeps encapsulation intact through an inheritance chain.

   ```java
   class Base {
       private   int a = 1;      // NOT accessible in the subclass
       protected int b = 2;      // accessible
                 int c = 3;      // accessible if in the SAME package
       public    int d = 4;      // accessible everywhere
   }

   class Derived extends Base {
       void test() {
           // System.out.println(a);   // COMPILE ERROR - a is private
           System.out.println(b);      // OK - protected
           System.out.println(c);      // OK - same package (default)
           System.out.println(d);      // OK - public
       }
   }
   ```

   What each specifier allows a subclass to do
   ```
      Member in the base | Subclass in the SAME package | Subclass in ANOTHER package
      -------------------+------------------------------+---------------------------
      private            |          NO                  |          NO
      default            |          YES                 |          NO
      protected          |          YES                 |          YES
      public             |          YES                 |          YES
   ```

   An important subtlety
   - A private member is still `inherited` in the sense that it `exists inside` the subclass object and occupies memory. It simply cannot be `named` there.
   ```java
   class Base {
       private int balance = 1000;
       public int getBalance() { return balance; }    // a public accessor
   }

   class Derived extends Base {
       void show() {
           // System.out.println(balance);   // ERROR - cannot name it
           System.out.println(getBalance()); // OK - reach it through the
       }                                     //      inherited public method
   }
   ```
   - So the data is there, and can be reached `indirectly` through an inherited public or protected method. Only direct naming is forbidden.

   In C++
   ```cpp
   class Base {
   private:   int a;          // NOT accessible in Derived
   protected: int b;          // accessible in Derived
   public:    int c;          // accessible everywhere
   };

   class Derived : public Base {
       void test() {
           // a = 1;          // ERROR
           b = 2;             // OK
           c = 3;             // OK
       }
   };
   ```
   - C++ adds the `friend` keyword, which can grant a named class or function access to private members. Java has no equivalent.
   - C++ also has three `inheritance modes`, which further restrict what the derived class exposes:
   ```
      class D : public    B   // public stays public, protected stays protected
      class D : protected B   // public becomes protected
      class D : private   B   // public and protected both become private
   ```

   Other things a subclass cannot access or change
   ```
      private members       - not accessible at all
      final methods         - inherited but cannot be OVERRIDDEN
      static methods        - can be HIDDEN, not overridden
      constructors          - not inherited; call them with super(...)
      a final class         - cannot be inherited from at all
   ```

   - Design point: making a field `protected` rather than `private` weakens encapsulation, because every subclass — including ones written years later by other people — can then change it directly, and the base class can no longer enforce its own invariants. The usual advice is to keep fields `private` and expose `protected methods` instead.

5. **What are the various Access Specification in C++? Explain their purpose with are example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*

   Answer: C++ has `three` access specifiers, and their purpose is to enforce `encapsulation` by controlling where each member may be used.
   ```
      private    : accessible only inside the class itself   (the DEFAULT)
      protected  : the class and its DERIVED classes
      public     : accessible from everywhere
   ```

   1. `private`
   - Accessible only within the class that declares it. Not even a derived class can name it.
   - Purpose: `hide the implementation`. Data members are normally private so the class controls every change to its own state.

   2. `protected`
   - Accessible inside the class and inside any `derived` class, but not from outside.
   - Purpose: let a subclass work with the parent's data while keeping unrelated code out. It is the specifier designed for inheritance.

   3. `public`
   - Accessible from anywhere.
   - Purpose: the class's `interface` — the members other code is meant to use.

   Access table
   ```
      Accessible from      | private | protected | public
      ---------------------+---------+-----------+--------
      Inside the class     |    Y    |     Y     |   Y
      Derived class        |    N    |     Y     |   Y
      Outside (main, etc.) |    N    |     N     |   Y
   ```

   Example
   ```cpp
   #include <iostream>
   using namespace std;

   class Base {
   private:
       int privateVar = 1;

   protected:
       int protectedVar = 2;

   public:
       int publicVar = 3;

       void showAll() {                 // inside the class : all three
           cout << privateVar << " " << protectedVar << " "
                << publicVar << endl;
       }
   };

   class Derived : public Base {
   public:
       void test() {
           // cout << privateVar;       // ERROR - private
           cout << protectedVar << endl;   // OK
           cout << publicVar    << endl;   // OK
       }
   };

   int main() {
       Base b;
       // cout << b.privateVar;         // ERROR
       // cout << b.protectedVar;       // ERROR
       cout << b.publicVar << endl;     // OK
       b.showAll();

       Derived d;
       d.test();
       return 0;
   }
   ```

   A practical class using all three
   ```cpp
   class BankAccount {
   private:
       double balance;                       // hidden - the invariant
       void auditLog(string msg) { }         // internal helper

   protected:
       string accountType;                   // subclasses may need it

   public:
       BankAccount(double opening) {
           balance = (opening > 0) ? opening : 0;
       }

       void deposit(double amount) {         // the interface
           if (amount > 0) { balance += amount; auditLog("deposit"); }
       }

       double getBalance() { return balance; }
   };
   ```
   - `balance` is private, so it can only change through `deposit()`, which validates. That is encapsulation working.

   The default in C++
   ```cpp
      class X { int a; };      // 'a' is PRIVATE by default
      struct Y { int a; };     // 'a' is PUBLIC by default
   ```
   - This default is the only real difference between `class` and `struct` in C++.

   Inheritance modes — a second use of the same keywords
   ```cpp
      class D : public    B    // public stays public , protected stays protected
      class D : protected B    // public becomes protected
      class D : private   B    // public and protected both become private (DEFAULT)
   ```

   The `friend` exception
   ```cpp
   class Box {
   private:
       double width;
       friend void printWidth(Box b);        // this function may see width
   };

   void printWidth(Box b) {
       cout << b.width;                      // legal because it is a friend
   }
   ```
   - `friend` deliberately breaks encapsulation for one named function or class. It is used for operator overloading — especially `<<` and `>>` — and should be used sparingly. Java has no equivalent.

   - Design rule: make every data member `private`, expose behaviour through `public` methods, and use `protected` only when a subclass genuinely needs direct access.

6. **How many specifiers are used in C++ programing?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

   Answer: C++ uses `three` access specifiers.
   ```
      1. private
      2. protected
      3. public
   ```

   What each means
   ```
      private    : accessible ONLY inside the class that declares it.
                   This is the DEFAULT for a class.

      protected  : accessible inside the class and inside any DERIVED class,
                   but not from outside.

      public     : accessible from EVERYWHERE.
   ```

   Access table
   ```
      Accessible from      | private | protected | public
      ---------------------+---------+-----------+--------
      Inside the class     |    Y    |     Y     |   Y
      Derived class        |    N    |     Y     |   Y
      Outside the class    |    N    |     N     |   Y
   ```

   Example
   ```cpp
   class Student {
   private:                     // the default for a class
       int roll;
   protected:
       string name;
   public:
       void setRoll(int r) { roll = r; }
       int  getRoll()      { return roll; }
   };
   ```

   The defaults
   ```cpp
      class X { int a; };       // 'a' is PRIVATE   by default
      struct Y { int a; };      // 'a' is PUBLIC    by default
   ```
   - This is the only genuine difference between `class` and `struct` in C++.

   The same three keywords in inheritance
   ```cpp
      class D : public    B     // public stays public, protected stays protected
      class D : protected B     // public becomes protected
      class D : private   B     // both become private   (the DEFAULT for a class)
   ```
   - So the three specifiers appear in two roles: controlling `member` access, and controlling how a base class's members are `re-exposed` by a derived class.

   Comparison with Java
   ```
      C++  : 3 specifiers  - private , protected , public
             plus 'friend', which can grant access to a named function
             or class

      Java : 4 levels      - private , default (package-private) ,
             protected , public
             no 'friend' equivalent
   ```
   - Java's extra level is `default`, which applies when no keyword is written and limits access to the same package. C++ has no notion of a package, so it has no such level.

   - Short answer: `three` — private, protected and public. Counting the `friend` mechanism as a fourth is a reasonable point to add, but it is a declaration rather than an access specifier.

7. **Briefly Describe Abstraction, Encapsulation.** *[Bangladesh Competition Commission Programmer 2019 compact it 1059-1060 (ET: DU)]*

   Answer: Abstraction
   - `Abstraction` means showing only the `essential features` of an object and hiding the implementation. The user learns `what` a class does, not `how` it does it.
   - Achieved in Java with `abstract classes` and `interfaces`.
   ```java
   abstract class Shape {
       abstract double area();          // WHAT, with no HOW

       void describe() {                // a concrete method is allowed too
           System.out.println("Area = " + area());
       }
   }

   class Circle extends Shape {
       double r;
       Circle(double r) { this.r = r; }
       @Override double area() { return 3.1416 * r * r; }    // the HOW
   }
   ```
   - Real-world analogy: a driver uses the `steering wheel, accelerator and brake`. How the rack, the fuel injection and the discs work is hidden. That hiding is abstraction.
   - An `interface` gives complete abstraction, since (before Java 8) it contained no implementation at all:
   ```java
      interface Payable { void pay(double amount); }
   ```
   - Benefits: it reduces complexity, enforces a `contract` that every subclass must honour, and lets the implementation be replaced without breaking a single caller.

   Encapsulation
   - `Encapsulation` binds the data and the methods that act on it into one unit — the class — and `hides the internal state` behind private fields with public accessor methods.
   ```java
   class BankAccount {
       private double balance;                    // hidden

       public void deposit(double amount) {
           if (amount > 0) balance += amount;     // validated
       }
       public void withdraw(double amount) {
           if (amount > 0 && amount <= balance) balance -= amount;
       }
       public double getBalance() { return balance; }
   }
   ```
   ```java
      acc.balance = -99999;      // COMPILE ERROR - balance is private
      acc.deposit(-500);         // rejected by the validation
   ```
   - Benefits: `data security` (the object cannot be put into an invalid state), a single place for validation, and the freedom to change the internal representation later without breaking any caller.
   - It is enforced by the `access modifiers`: `private`, `protected`, `public` and default.

   Difference

   | Point | Abstraction | Encapsulation |
   |---|---|---|
   | Hides | The `implementation` — how it works | The `data` — the internal state |
   | Question it answers | `What` does it do? | `How is the data protected?` |
   | Focus | Design level | Implementation level |
   | Achieved by | Abstract classes, interfaces | Access modifiers, getters and setters |
   | Solves | Complexity — the user sees less | Security — the data cannot be corrupted |
   | Applied at | The class's outward design | The class's internal members |
   | Java keyword | `abstract`, `interface` | `private`, `public`, `protected` |

   How they work together
   ```java
      interface Payment { void pay(double amount); }     // ABSTRACTION

      class CardPayment implements Payment {
          private String cardNumber;                     // ENCAPSULATION
          private String cvv;

          public void pay(double amount) {               // the abstraction's
              validateCard();                            // contract, fulfilled
              processTransaction(amount);
          }

          private void validateCard() { ... }            // hidden helper
          private void processTransaction(double a) { ... }
      }
   ```
   - The caller sees only `pay(amount)` — that is abstraction. The card number and CVV are private and unreachable — that is encapsulation. The two are complementary: abstraction hides the `complexity`, encapsulation hides the `data`.

## Exception Handling (4)

1. **(b) What is exception? Explain how it can be used for debugging a program.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

   Answer: What an exception is
   - An `exception` is an `abnormal event that occurs during execution` and disrupts the normal flow of the program. It is not a syntax error — the program compiles perfectly and then fails while running.
   ```java
      int[] a = new int[5];
      a[10] = 1;                  // ArrayIndexOutOfBoundsException at run time

      int x = 10 / 0;             // ArithmeticException

      String s = null;
      s.length();                 // NullPointerException
   ```
   - In Java an exception is an `object` of a class descended from `Throwable`, carrying the type of the fault, a message and a `stack trace`.

   The hierarchy
   ```
                    Throwable
                   /         \
              Error          Exception
           (unrecoverable)   /        \
                     Checked          RuntimeException
                     IOException      (unchecked)
                     SQLException     NullPointerException
                                      ArithmeticException
                                      ArrayIndexOutOfBounds
   ```
   ```
      CHECKED   : the compiler forces you to handle or declare them
                  IOException, SQLException, ClassNotFoundException

      UNCHECKED : the compiler does not - they are programming faults
                  NullPointerException, ArithmeticException,
                  ArrayIndexOutOfBoundsException

      ERROR     : serious JVM problems that a program should not catch
                  OutOfMemoryError, StackOverflowError
   ```

   Handling it
   ```java
   try {
       int result = 10 / 0;
   } catch (ArithmeticException e) {
       System.out.println("Error: " + e.getMessage());
   } finally {
       System.out.println("This always runs");
   }
   ```

   How exceptions help in debugging

   1. `The stack trace pinpoints the failure`
   ```
      Exception in thread "main" java.lang.ArithmeticException: / by zero
           at Calculator.divide(Calculator.java:15)
           at Calculator.compute(Calculator.java:8)
           at Main.main(Main.java:5)
   ```
   - It gives the `exception type`, a `message`, the `exact line`, and the `whole chain of calls` that led there. That is usually enough to locate the bug without any debugging tools.

   2. `The exception type names the category of fault`
   ```
      NullPointerException            -> an object reference was never assigned
      ArrayIndexOutOfBoundsException  -> a loop bound is wrong
      NumberFormatException           -> input was not a valid number
      ClassCastException              -> a wrong downcast
      FileNotFoundException           -> a path or permission problem
   ```
   - Reading the type alone usually tells the programmer what kind of mistake to look for.

   3. `The program fails immediately, at the point of the fault`
   - Without exceptions, a wrong value propagates silently and the symptom appears far from the cause. `Fail fast` is what makes debugging tractable.

   4. `Custom exceptions carry the program's own meaning`
   ```java
   class InsufficientBalanceException extends Exception {
       public InsufficientBalanceException(String msg) { super(msg); }
   }

   void withdraw(double amount) throws InsufficientBalanceException {
       if (amount > balance)
           throw new InsufficientBalanceException(
               "Requested " + amount + " but balance is " + balance);
       balance -= amount;
   }
   ```
   - The message states the business fault in the developer's own words, with the actual values.

   5. `Logging the exception preserves the evidence`
   ```java
   try {
       processTransaction();
   } catch (Exception e) {
       logger.error("Transaction failed for account " + accNo, e);
       throw e;                         // rethrow after logging
   }
   ```
   - In production, where a debugger cannot be attached, the logged stack trace is the only record of what happened.

   6. `finally guarantees cleanup even on failure`
   ```java
   try (Connection con = getConnection()) {
       ...
   }   // con.close() runs whether or not an exception was thrown
   ```

   7. `assert and validation catch faults early`
   ```java
      if (amount <= 0)
          throw new IllegalArgumentException("Amount must be positive: " + amount);
   ```
   - Checking preconditions and throwing immediately turns a silent corruption into a clear, located failure.

   Practices that destroy the debugging value
   ```java
      catch (Exception e) { }             // swallowing it - the WORST habit
      catch (Exception e) { System.out.println("error"); }   // loses the trace

      Correct :
      catch (SpecificException e) {
          logger.error("what was being attempted", e);       // keeps the trace
      }
   ```
   - Catching `Exception` broadly, or catching and ignoring, removes exactly the information that would have identified the bug.

2. **What is difference between exception and error in Java?** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*

   Answer: Both `Exception` and `Error` are subclasses of `Throwable`, but they represent completely different kinds of problem.
   ```
                    Throwable
                   /         \
              Error          Exception
        (serious, do NOT     (recoverable,
         catch)               SHOULD handle)
   ```

   Exception
   - An `abnormal condition that a well-written program can anticipate and recover from`.
   - Usually caused by the application itself or by its environment — a missing file, a bad input, a dropped connection.
   - The program `should` catch it and take sensible action.
   ```java
      IOException , SQLException , FileNotFoundException      (checked)
      NullPointerException , ArithmeticException ,            (unchecked)
      ArrayIndexOutOfBoundsException , NumberFormatException
   ```
   ```java
   try {
       FileReader f = new FileReader("data.txt");
   } catch (FileNotFoundException e) {
       System.out.println("File missing, using defaults instead");
   }
   ```

   Error
   - A `serious problem in the JVM or the environment` that an application `cannot reasonably recover from`.
   - Caused by resource exhaustion or a broken runtime, not by ordinary program logic.
   - The program should `not` catch it; there is normally nothing useful it could do.
   ```java
      OutOfMemoryError , StackOverflowError , VirtualMachineError ,
      NoClassDefFoundError , AssertionError
   ```
   ```java
      void recurse() { recurse(); }      // StackOverflowError
      int[] a = new int[Integer.MAX_VALUE];   // OutOfMemoryError
   ```

   Difference

   | Point | Exception | Error |
   |---|---|---|
   | Represents | A recoverable abnormal condition | A serious unrecoverable problem |
   | Caused by | The application or its environment | The JVM or resource exhaustion |
   | Should be caught | `Yes` | `No` |
   | Can be recovered from | Usually yes | Usually no |
   | Checked / unchecked | Both kinds exist | Always `unchecked` |
   | Compiler enforces handling | For checked exceptions, yes | Never |
   | Declared with `throws` | Yes, for checked ones | Not required |
   | Occurs at | Run time | Run time |
   | Examples | IOException, SQLException, NullPointerException | OutOfMemoryError, StackOverflowError |
   | Package | `java.lang.Exception` | `java.lang.Error` |

   Checked versus unchecked exceptions, since the question often follows
   ```
      CHECKED   : the compiler INSISTS that you either catch them or declare
                  them with 'throws'. They represent conditions outside the
                  program's control.
                  IOException , SQLException , ClassNotFoundException

      UNCHECKED : subclasses of RuntimeException. The compiler says nothing,
                  because they represent PROGRAMMING FAULTS that should be
                  prevented rather than caught.
                  NullPointerException , ArithmeticException ,
                  ArrayIndexOutOfBoundsException , IllegalArgumentException
   ```
   ```java
      // checked - MUST be handled or declared
      public void read() throws IOException {
          FileReader f = new FileReader("data.txt");
      }

      // unchecked - compiles without any handling
      public void divide() {
          int x = 10 / 0;
      }
   ```

   Can an Error be caught? Technically yes, practically no
   ```java
      try {
          recurse();
      } catch (StackOverflowError e) {          // LEGAL, but almost never right
          System.out.println("stack overflow");
      }
   ```
   - It compiles and runs, but the JVM may already be in an unusable state. The only defensible case is a top-level handler in a server that logs the failure before shutting down cleanly.

   - The rule to state: `handle exceptions, do not handle errors`. An exception means "something went wrong that I can deal with"; an error means "the runtime itself is broken".

3. **What is exception handling? Write with an example.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

   Answer: `Exception handling` is the mechanism that lets a program `detect an abnormal condition at run time and respond to it`, instead of terminating abruptly.

   - Without it, a single bad input crashes the whole program and any work in progress is lost.

   The five keywords
   ```
      try     : the block of code that might throw an exception
      catch   : handles a particular type of exception
      finally : always runs, whether or not an exception occurred
      throw   : raises an exception explicitly
      throws  : declares that a method may raise a checked exception
   ```

   Basic structure
   ```java
   try {
       // risky code
   } catch (SpecificException e) {
       // handle that type
   } catch (AnotherException e) {
       // handle another type
   } finally {
       // cleanup - ALWAYS runs
   }
   ```

   Complete example
   ```java
   import java.util.Scanner;

   public class ExceptionDemo {

       public static void main(String[] args) {

           Scanner sc = new Scanner(System.in);
           int[] marks = {75, 82, 90, 68, 55};

           try {
               System.out.print("Enter an index (0-4): ");
               int index = sc.nextInt();

               System.out.print("Enter a divisor: ");
               int divisor = sc.nextInt();

               System.out.println("Mark    : " + marks[index]);
               System.out.println("Divided : " + (marks[index] / divisor));

           } catch (ArrayIndexOutOfBoundsException e) {
               System.out.println("Invalid index. Please enter 0 to 4.");

           } catch (ArithmeticException e) {
               System.out.println("Cannot divide by zero.");

           } catch (Exception e) {                 // the general catch, LAST
               System.out.println("Unexpected error: " + e.getMessage());

           } finally {
               sc.close();
               System.out.println("Scanner closed. Program continues.");
           }

           System.out.println("Program finished normally.");
       }
   }
   ```

   Sample runs
   ```
      Enter an index (0-4): 2
      Enter a divisor: 3
      Mark    : 90
      Divided : 30
      Scanner closed. Program continues.
      Program finished normally.

      ---

      Enter an index (0-4): 10
      Invalid index. Please enter 0 to 4.
      Scanner closed. Program continues.
      Program finished normally.

      ---

      Enter an index (0-4): 2
      Enter a divisor: 0
      Cannot divide by zero.
      Scanner closed. Program continues.
      Program finished normally.
   ```
   - In every case the program continues and closes its resources. Without the try-catch, the second and third runs would terminate with a stack trace.

   Using `throw` and `throws`, with a custom exception
   ```java
   class InsufficientBalanceException extends Exception {
       public InsufficientBalanceException(String msg) { super(msg); }
   }

   class Account {
       private double balance = 5000;

       // 'throws' DECLARES that this method may raise it
       public void withdraw(double amount) throws InsufficientBalanceException {
           if (amount > balance)
               // 'throw' RAISES it
               throw new InsufficientBalanceException(
                   "Requested " + amount + " but balance is only " + balance);
           balance -= amount;
           System.out.println("Withdrawn " + amount);
       }
   }

   public class Main {
       public static void main(String[] args) {
           Account acc = new Account();
           try {
               acc.withdraw(10000);
           } catch (InsufficientBalanceException e) {
               System.out.println("Failed: " + e.getMessage());
           }
       }
   }
   ```
   Output
   ```
      Failed: Requested 10000.0 but balance is only 5000.0
   ```

   try-with-resources — the modern form
   ```java
   try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
       System.out.println(br.readLine());
   } catch (IOException e) {
       System.out.println("Cannot read the file: " + e.getMessage());
   }   // br.close() runs automatically, even if an exception is thrown
   ```

   Rules and good practice
   ```
      Catch the MOST SPECIFIC exception first; a general catch(Exception e)
           must come LAST, or the specific ones become unreachable code.

      finally ALWAYS runs - even after a return - so it is the right place
           for cleanup. try-with-resources is better still.

      Never swallow an exception :  catch (Exception e) { }
           This hides the fault and destroys the stack trace.

      Do not use exceptions for ordinary control flow; they are slow
           and obscure the logic.

      Log the exception OBJECT, not just its message, so the stack
           trace is preserved.
   ```

   Benefits
   ```
      The program survives the fault and can clean up properly
      Error-handling code is SEPARATED from the normal logic
      Faults propagate up the call stack to whoever can actually handle them
      The stack trace makes debugging far easier
      Custom exceptions express the application's own rules
   ```

4. **Write the difference between throw and throws using Exception handling?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1172-1173 (ET: N/A)]*

   Answer: `throw` and `throws` look alike but do entirely different jobs. The single letter `s` is the whole difference.

   `throw` — raises an exception
   ```
      Used INSIDE a method body
      Followed by an OBJECT :  throw new SomeException("message");
      Raises exactly ONE exception
      Execution of the method stops immediately at that point
   ```
   ```java
   public void setAge(int age) {
       if (age < 0 || age > 150)
           throw new IllegalArgumentException("Invalid age: " + age);
       this.age = age;
   }
   ```

   `throws` — declares that an exception may be raised
   ```
      Used in the method SIGNATURE, after the parameter list
      Followed by CLASS NAMES :  throws IOException, SQLException
      May declare SEVERAL exceptions, separated by commas
      Raises nothing itself - it only warns the caller
   ```
   ```java
   public void readFile(String path) throws IOException, FileNotFoundException {
       FileReader f = new FileReader(path);
       ...
   }
   ```

   The two used together
   ```java
   class InsufficientBalanceException extends Exception {
       public InsufficientBalanceException(String msg) { super(msg); }
   }

   class Account {
       private double balance = 5000;

       //                                     'throws' DECLARES
       public void withdraw(double amount) throws InsufficientBalanceException {

           if (amount > balance)
               //          'throw' RAISES
               throw new InsufficientBalanceException(
                   "Requested " + amount + " but balance is " + balance);

           balance -= amount;
       }
   }

   public class Main {
       public static void main(String[] args) {
           Account acc = new Account();
           try {
               acc.withdraw(10000);
           } catch (InsufficientBalanceException e) {
               System.out.println("Failed: " + e.getMessage());
           }
       }
   }
   ```
   - `throws` tells the compiler and the reader "this method can fail in this way, so be ready". `throw` is the moment it actually does.

   Difference

   | Point | `throw` | `throws` |
   |---|---|---|
   | Purpose | Raises an exception | Declares that one may be raised |
   | Where written | Inside the method body | In the method signature |
   | Followed by | An `object` (`new XException()`) | One or more `class names` |
   | How many | Exactly one at a time | Several, separated by commas |
   | Effect | Execution stops there | Nothing at run time |
   | Checked exceptions | Must be caught or declared | Passes the duty to the caller |
   | Used with | An instance | A class name |
   | Syntax | `throw new IOException("msg");` | `void m() throws IOException { }` |

   Why `throws` matters for checked exceptions
   ```java
      // WITHOUT throws - COMPILE ERROR for a checked exception
      public void read() {
          FileReader f = new FileReader("data.txt");   // ERROR: unhandled
      }

      // Option 1 : declare it, passing the duty upward
      public void read() throws FileNotFoundException {
          FileReader f = new FileReader("data.txt");
      }

      // Option 2 : handle it here
      public void read() {
          try {
              FileReader f = new FileReader("data.txt");
          } catch (FileNotFoundException e) {
              System.out.println("File not found");
          }
      }
   ```
   - For `unchecked` exceptions — `NullPointerException`, `ArithmeticException` — `throws` is optional, because the compiler does not enforce handling.

   Rules worth stating
   ```
      Only ONE object may be thrown at a time; it must be Throwable
           or a subclass.

      Code immediately after a throw is UNREACHABLE and will not compile.

      An overriding method cannot declare a BROADER checked exception
           than the method it overrides.

      'throws' does not handle anything - it delegates. Eventually some
           method must actually catch it, or the program terminates.
   ```

   - Memory aid: `throw` is an action taken now; `throws` is a warning about what might happen.

## C++ OOP Concepts & Friend Functions (3)

1. **(b) What is friend function? Given the following class, show how to add a friend function, named isneg() that takes one parameter of type myclass and return true if num is negative and false otherwise.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1355 (ET: N/A)]*
```cpp
class myclass{
    int num;
public:
    myclass (int i) {num = i;}
};
```

   Answer: What a friend function is
   - A `friend function` is a function that is `not a member` of a class but is granted access to its `private` and `protected` members.
   - It is declared inside the class with the `friend` keyword, but defined outside it and called like an ordinary function — with no object and no `::`.
   ```cpp
      class X {
          friend returnType functionName(parameters);   // declaration only
      };
   ```

   Adding `isneg()` to the given class
   ```cpp
   #include <iostream>
   using namespace std;

   class myclass {
       int num;                                    // PRIVATE

   public:
       myclass(int i) { num = i; }

       // ---- declare the friend ----
       friend bool isneg(myclass obj);
   };

   // ---- define it OUTSIDE the class, with NO 'friend' keyword ----
   bool isneg(myclass obj) {
       return (obj.num < 0);          // legal: it is a friend, so it sees num
   }

   int main() {
       myclass a(10);
       myclass b(-25);
       myclass c(0);

       cout << boolalpha;                       // print true/false, not 1/0
       cout << "a is negative : " << isneg(a) << endl;   // false
       cout << "b is negative : " << isneg(b) << endl;   // true
       cout << "c is negative : " << isneg(c) << endl;   // false

       return 0;
   }
   ```
   Output
   ```
      a is negative : false
      b is negative : true
      c is negative : false
   ```

   Points about the code
   ```
      The declaration goes INSIDE the class, in any section - public,
           private or protected. Its position makes no difference.

      The definition goes OUTSIDE, WITHOUT the 'friend' keyword and
           WITHOUT myclass:: - it is not a member function.

      It is called as  isneg(a)  , not  a.isneg()  , because it has
           no 'this' pointer and belongs to no object.

      Passing by const reference is better for a large object :

           friend bool isneg(const myclass &obj);
           bool isneg(const myclass &obj) { return obj.num < 0; }
   ```

   Passing by reference, to avoid copying
   ```cpp
      friend bool isneg(const myclass &obj);

      bool isneg(const myclass &obj) {
          return obj.num < 0;
      }
   ```

   Why a friend is sometimes needed
   ```cpp
      // Overloading << requires the left operand to be an ostream, so the
      // function CANNOT be a member of myclass. A friend is the only way.

      class myclass {
          int num;
      public:
          myclass(int i) { num = i; }
          friend ostream& operator<<(ostream &out, const myclass &obj);
      };

      ostream& operator<<(ostream &out, const myclass &obj) {
          out << obj.num;
          return out;
      }

      // now : cout << a;   works directly
   ```
   - The other classic case is a function that needs the private data of `two different classes` at once, such as adding a `Matrix` to a `Vector`.

   Properties of a friend function
   ```
      NOT a member of the class - it has no 'this' pointer
      Can be a global function, or a member of another class
      Access is NOT reciprocal : if A declares B a friend, B is not
           automatically a friend of A
      Friendship is NOT inherited by derived classes
      Friendship is NOT transitive : a friend of a friend is not a friend
      It can be declared in any section; access specifiers do not apply to it
   ```

   - Disadvantage: it `breaks encapsulation` deliberately. Every friend is a hole in the class's wall, so friends should be few, named explicitly and used only where a member function genuinely cannot do the job. Java has no equivalent at all.

2. **(ক) Friend Function কী? উহার সুবিধা অসুবিধাগুলো লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a friend function is
   - A `friend function` is a function that is `not a member` of a class but is granted access to its `private` and `protected` members.
   - It is declared inside the class with the `friend` keyword, but defined outside it and called like an ordinary function.
   ```cpp
   #include <iostream>
   using namespace std;

   class Box {
   private:
       double width;

   public:
       Box(double w) { width = w; }

       friend void printWidth(Box b);       // DECLARATION only
   };

   // defined OUTSIDE, without 'friend' and without Box::
   void printWidth(Box b) {
       cout << "Width = " << b.width << endl;   // legal - it is a friend
   }

   int main() {
       Box box(15.5);
       printWidth(box);          // called like a normal function
       return 0;
   }
   ```

   Advantages
   - `Access to private data when a member function cannot be used.` The classic case is overloading `<<`, where the left operand must be an `ostream`, so the function cannot be a member of the user's class.
   ```cpp
      friend ostream& operator<<(ostream &out, const Complex &c) {
          out << c.real << " + " << c.imag << "i";
          return out;
      }
      // now : cout << myComplex;   works directly
   ```
   - `Works with two different classes at once.` A function that needs the private members of both a `Matrix` and a `Vector` can be a friend of both — no member function of either could do that.
   - `Natural syntax for symmetric operations.` `add(a, b)` reads better than `a.add(b)` for a mathematical operation where neither operand is privileged.
   - `Allows implicit conversion on the LEFT operand.` `2 * myComplex` works with a friend `operator*`, but not with a member one, because a member's left operand must already be of the class type.
   - `Can improve efficiency` by avoiding accessor calls in performance-critical code.
   - `Useful for testing`, where a test class may be made a friend to inspect internal state.

   Disadvantages
   - `It breaks encapsulation.` A friend is a deliberate hole in the class's wall. The class no longer controls all access to its own data, which is the whole point of making members private.
   - `It increases coupling.` The friend function depends on the class's internal representation, so changing that representation breaks the friend as well as the class.
   - `Harder to maintain.` Reading a class no longer tells you everything that can modify it; the friends must be found and read too.
   - `Not inherited.` A friend of a base class is `not` a friend of a derived class, which surprises people.
   - `Not reciprocal.` If A declares B a friend, B is not automatically a friend of A.
   - `Not transitive.` A friend of a friend is not a friend.
   - `Overuse turns a class into a struct.` If several functions need private access, the design is probably wrong.
   - `No equivalent in Java or C#`, so code using friends does not translate.

   Properties
   ```
      NOT a member - it has no 'this' pointer
      Declared inside the class, defined outside
      Called without an object :  printWidth(box)  not  box.printWidth()
      May be declared in any section - public, private or protected -
           and it makes no difference
      A whole class may be a friend :  friend class Manager;
   ```

   - The guideline: use a friend only where a member function genuinely `cannot` do the job — chiefly for `operator<<` and `operator>>`, and for operations spanning two classes. Everywhere else, a public accessor is the better answer.

3. **(খ) Friend Function কী? উহার সুবিধা ও অসুবিধা গুলো লিখুন?** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1086 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a friend function is
   - A `friend function` is a non-member function that is granted access to the `private` and `protected` members of a class.
   - It is declared inside the class with the `friend` keyword, defined outside it, and called like an ordinary function — with no object and no `::`.
   ```cpp
   #include <iostream>
   using namespace std;

   class Student {
   private:
       int roll;
       double cgpa;

   public:
       Student(int r, double c) { roll = r; cgpa = c; }

       friend void showDetails(Student s);      // DECLARATION
       friend bool isBetter(Student a, Student b);
   };

   void showDetails(Student s) {                 // DEFINITION, no 'friend'
       cout << s.roll << " - " << s.cgpa << endl;    // sees private members
   }

   bool isBetter(Student a, Student b) {         // needs BOTH objects' privates
       return a.cgpa > b.cgpa;
   }

   int main() {
       Student s1(101, 3.75), s2(102, 3.40);

       showDetails(s1);                 // called WITHOUT an object
       cout << (isBetter(s1, s2) ? "s1 is better" : "s2 is better") << endl;
       return 0;
   }
   ```
   Output
   ```
      101 - 3.75
      s1 is better
   ```

   Advantages
   - `Access where a member function is impossible.` Overloading `<<` needs an `ostream` as its left operand, so it cannot be a member of the user's class. A friend is the only way.
   ```cpp
      friend ostream& operator<<(ostream &out, const Student &s) {
          out << s.roll << " : " << s.cgpa;
          return out;
      }
      // now : cout << s1;
   ```
   - `Works across two classes.` A function needing the private data of both a `Matrix` and a `Vector` can be a friend of both.
   - `Natural syntax` for symmetric operations — `isBetter(a, b)` reads better than `a.isBetter(b)`.
   - `Allows conversion on the left operand`, so `2 * myComplex` works with a friend `operator*` but not with a member one.
   - `Efficiency` in tight code, by avoiding a chain of accessor calls.

   Disadvantages
   - `It breaks encapsulation` deliberately. Every friend is a hole in the class's wall, and the class can no longer guarantee its own invariants.
   - `Increases coupling` — the friend depends on the internal representation, so changing that representation breaks it.
   - `Harder to maintain`: reading the class no longer shows everything that can modify it.
   - `Not inherited` — a friend of a base class is not a friend of a derived class.
   - `Not reciprocal` — if A declares B a friend, B is not a friend of A.
   - `Not transitive` — a friend of a friend is not a friend.
   - `Overuse` turns a class into a struct with extra ceremony, which means the design is wrong.
   - `No equivalent in Java or C#`, so such code does not port.

   Friend class
   ```cpp
      class Engine {
      private:
          int power;
          friend class Car;         // EVERY member of Car may see Engine's privates
      };

      class Car {
      public:
          void show(Engine e) { cout << e.power; }    // legal
      };
   ```

   - The guideline: use `friend` only where a member function genuinely cannot do the job — chiefly `operator<<` and `operator>>`, and operations that span two classes. Everywhere else, a public accessor is the better answer.

## Interfaces & Abstract Classes (2)

1. **Class/Interface implementation of code?** *[BCIC Assistant Programmer 14.02.2025 compact it 1329 (ET: BUET)]*

   Answer: An `interface` declares `what` a class must be able to do, without saying `how`. A class then `implements` it and supplies the bodies. This gives complete abstraction, and it is Java's way of achieving multiple inheritance of type.

   ```java
   // ---------------- INTERFACE ----------------
   interface Payable {
       double RATE = 0.15;                 // implicitly public static final

       void pay(double amount);            // implicitly public abstract
       String getPaymentType();

       // default method (Java 8 onward) - has a body
       default void printReceipt(double amount) {
           System.out.println("Paid " + amount + " by " + getPaymentType());
       }
   }

   // ---------------- another INTERFACE ----------------
   interface Refundable {
       void refund(double amount);
   }

   // ---------------- IMPLEMENTING CLASS ----------------
   class CardPayment implements Payable, Refundable {   // MULTIPLE interfaces

       private String cardNumber;

       public CardPayment(String cardNumber) {
           this.cardNumber = cardNumber;
       }

       @Override
       public void pay(double amount) {
           System.out.println("Charging card ending " +
               cardNumber.substring(cardNumber.length() - 4) +
               " with " + amount);
       }

       @Override
       public String getPaymentType() { return "Debit Card"; }

       @Override
       public void refund(double amount) {
           System.out.println("Refunding " + amount + " to the card");
       }
   }

   class BkashPayment implements Payable {

       private String mobile;

       public BkashPayment(String mobile) { this.mobile = mobile; }

       @Override
       public void pay(double amount) {
           System.out.println("Sending " + amount + " from " + mobile);
       }

       @Override
       public String getPaymentType() { return "bKash"; }
   }

   // ---------------- MAIN ----------------
   public class Main {
       public static void main(String[] args) {

           Payable[] payments = {                     // INTERFACE reference
               new CardPayment("4532123456781234"),
               new BkashPayment("01712345678")
           };

           for (Payable p : payments) {
               p.pay(5000);
               p.printReceipt(5000);        // the default method
               System.out.println("---");
           }

           // an interface reference can be narrowed when the type is known
           Refundable r = new CardPayment("4532123456781234");
           r.refund(1000);
       }
   }
   ```

   Output
   ```
      Charging card ending 1234 with 5000.0
      Paid 5000.0 by Debit Card
      ---
      Sending 5000.0 from 01712345678
      Paid 5000.0 by bKash
      ---
      Refunding 1000.0 to the card
   ```

   Rules for an interface
   ```
      All methods are implicitly PUBLIC ABSTRACT (before Java 8)
      All fields are implicitly PUBLIC STATIC FINAL - they are constants
      It CANNOT be instantiated :  new Payable();   is an error
      It has NO constructor
      A class uses 'implements' and MUST provide every abstract method,
           or be declared abstract itself
      A class may implement ANY NUMBER of interfaces - this is Java's
           multiple inheritance of TYPE
      An interface may EXTEND other interfaces

      Java 8  : default and static methods, which have bodies
      Java 9  : private methods, for shared helper code
   ```

   Interface versus abstract class

   | Point | Interface | Abstract class |
   |---|---|---|
   | Keyword to use it | `implements` | `extends` |
   | Multiple inheritance | `Yes`, many interfaces | No, only one class |
   | Methods | Abstract, plus default and static | Abstract and concrete |
   | Fields | `public static final` constants only | Any kind, any modifier |
   | Constructor | `No` | Yes |
   | Access modifiers on methods | Public (implicitly) | Any |
   | Purpose | A `contract` — what a class can DO | A `base` — shared state and code |
   | Relationship | CAN-DO | IS-A |

   When to use which
   ```
      INTERFACE      : unrelated classes need a common ability
                       (Comparable, Runnable, Serializable, Payable)

      ABSTRACT CLASS : related classes share both state and code
                       (Shape with a colour field and a draw() outline)
   ```

   - The design rule usually quoted: `program to an interface, not an implementation`. Declaring `Payable p` rather than `CardPayment p` means the code works with any payment type, including ones written later.

2. **An Abstract class Player with two sub classes Bowler and Batsman, Abstract class has one abstract method average, also have constructor and a string function that display name bowler or batsman. Batsman class implement abstract function average and display result, Batsman class have run and number match data. Now write a Java Program and show Batsman average run.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

   Answer: The abstract class `Player` declares the contract; `Batsman` and `Bowler` supply their own `average()`.

   ```java
   // ---------------- ABSTRACT CLASS ----------------
   abstract class Player {

       protected String name;

       // an abstract class CAN have a constructor
       public Player(String name) {
           this.name = name;
       }

       // ---- ABSTRACT method : no body, subclasses MUST implement it ----
       public abstract double average();

       // ---- a concrete method returning a String ----
       public String getType() {
           return "Player";
       }

       public void display() {
           System.out.println("--------------------------------");
           System.out.println("Name    : " + name);
           System.out.println("Type    : " + getType());
           System.out.printf ("Average : %.2f%n", average());
           System.out.println("--------------------------------");
       }
   }

   // ---------------- SUBCLASS : BATSMAN ----------------
   class Batsman extends Player {

       private int runs;
       private int matches;

       public Batsman(String name, int runs, int matches) {
           super(name);                       // call the parent constructor
           this.runs    = runs;
           this.matches = matches;
       }

       @Override
       public double average() {              // implement the abstract method
           if (matches == 0) return 0;
           return (double) runs / matches;    // the CAST is essential
       }

       @Override
       public String getType() {
           return "Batsman";
       }

       public void showResult() {
           System.out.println(name + " scored " + runs + " runs in "
                              + matches + " matches");
           System.out.printf("Batting average = %.2f%n", average());
       }
   }

   // ---------------- SUBCLASS : BOWLER ----------------
   class Bowler extends Player {

       private int runsGiven;
       private int wickets;

       public Bowler(String name, int runsGiven, int wickets) {
           super(name);
           this.runsGiven = runsGiven;
           this.wickets   = wickets;
       }

       @Override
       public double average() {              // bowling average = runs / wickets
           if (wickets == 0) return 0;
           return (double) runsGiven / wickets;
       }

       @Override
       public String getType() {
           return "Bowler";
       }
   }

   // ---------------- MAIN ----------------
   public class Main {
       public static void main(String[] args) {

           Batsman b = new Batsman("Shakib Al Hasan", 1800, 45);
           b.showResult();
           b.display();

           // POLYMORPHISM : one array holds both kinds of player
           Player[] team = {
               new Batsman("Tamim Iqbal", 2100, 50),
               new Bowler ("Taskin Ahmed", 1200, 60)
           };

           for (Player p : team)
               p.display();          // each calls ITS OWN average()

           // Player p = new Player("X");   // ERROR - abstract, cannot instantiate
       }
   }
   ```

   Output
   ```
      Shakib Al Hasan scored 1800 runs in 45 matches
      Batting average = 40.00
      --------------------------------
      Name    : Shakib Al Hasan
      Type    : Batsman
      Average : 40.00
      --------------------------------
      --------------------------------
      Name    : Tamim Iqbal
      Type    : Batsman
      Average : 42.00
      --------------------------------
      --------------------------------
      Name    : Taskin Ahmed
      Type    : Bowler
      Average : 20.00
      --------------------------------
   ```

   Working
   ```
      Batting average = runs / matches     = 1800 / 45 = 40.00
      Bowling average = runs given / wickets = 1200 / 60 = 20.00
   ```
   - Note that `average()` means something quite different for a batsman and a bowler. That is exactly why it is `abstract` in `Player`: the parent knows every player `has` an average, but not `how` to compute it.

   Concepts the program demonstrates
   ```
      ABSTRACT CLASS : Player cannot be instantiated; it defines the contract

      ABSTRACT METHOD: average() has no body; every concrete subclass MUST
                       implement it, or itself be declared abstract

      CONSTRUCTOR in an abstract class : Player(String name) is called by
                       the subclasses through super(name)

      CONCRETE METHOD in an abstract class : getType() and display() have
                       bodies and are inherited as they are, or overridden

      POLYMORPHISM   : the Player[] array holds both subclasses, and
                       p.display() calls each object's own average()

      ENCAPSULATION  : runs, matches and wickets are private
   ```

   Points worth stating
   ```
      An abstract class CAN have constructors, fields and concrete methods.
           Only an INTERFACE (before Java 8) was purely abstract.

      (double) runs / matches - without the cast, integer division would
           give 40 instead of 40.00, which is the commonest error here.

      Guard against a zero denominator, or the result is Infinity or NaN.

      A subclass that does not implement every abstract method must itself
           be declared abstract.
   ```
