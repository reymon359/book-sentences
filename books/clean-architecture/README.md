<p align="center"><img alt="clean-architecture" src="./clean-architecture.png" width="250" /></p> 

<h1 align="center">Clean Architecture. A Craftsman's Guide to Software Structure and Design.</h1>

<h3 align="center">Robert Martin - 2017</h3> 

## Table of Contents

TODO

## Foreword

As with any metaphor, describing software through the lens of architecture can hide as much as it can reveal. It can both promise more than it can deliver and deliver more than it promises.

It’s not obvious that software structure obeys our intuition the way building structure does.

Software is made of software. Large software constructs are made from smaller software components, which are in turn made of smaller software components still, and so on.

Software is recursive and fractal in nature, etched and sketched in code. Everything is details.

You can even argue quite convincingly that there is more design activity and focus in software than in building architecture—in this sense, it’s not unreasonable to consider software architecture more architectural than building architecture!

To mistake boxes for _the_ big picture— for _the_ architecture—is to miss the big picture and the architecture: Software architecture doesn’t look like anything.

Software may be such stuff as dreams are made on, but it runs in the physical world.

> This is the monstrosity in love, lady, that the will is infinite, and the execution confined; that the desire is boundless, and the act a slave to limit.
> — William Shakespeare

> Architecture represents the significant design decisions that shape a system, where significant is measured by cost of change.
> — Grady Booch

A good architecture meet the needs of its users, developers, and owners at a given point in time, but it also meets them over time.

> If you think good architecture is expensive, try bad architecture.
> — Brian Foote and Joseph Yoder

The kinds of changes a system’s development typically experiences should not be the changes that are costly, that are hard to make, that take managed projects of their own rather than being folded into the daily and weekly flow of work.

> Architecture is the decisions that you wish you could get right early in a project, but that you are not necessarily more likely to get them right than any other.
> — Ralph Johnson

Understanding the past is hard enough as it is; our grasp of the present is slippery at best; predicting the future is nontrivial.

The darkest path... ...strong and stable architecture comes from authority and rigidity. If change is expensive, change is eliminated... ...The architect’s mandate is total and totalitarian, with the architecture becoming a dystopia for its developers and a constant source of frustration for all... ...another path... ...speculative generality. A route filled with hard-coded guesswork, countless parameters, tombs of dead code, and more accidental complexity than you can shake a maintenance budget at... ...The path...cleanest... ...recognizes the softness of software and aims to preserve it as a first-class property of the system. It recognizes that we operate with incomplete knowledge, but it also understands that, as humans, operating with incomplete knowledge is something we do, something we’re good at. It plays more to our strengths than to our weaknesses. We create things and we discover things. We ask questions and we run experiments. A good architecture comes from understanding it more as a journey than as a destination, more as an ongoing process of enquiry than as a frozen artifact.

A good architecture comes from understanding it more as a journey than as a destination, more as an ongoing process of enquiry than as a frozen artifact.

> Architecture is a hypothesis, that needs to be proven by implementation and measurement.
> — Tom Gilb

> The only way to go fast, is to go well.
> — Robert C. Martin

## Preface

_The rules of software architecture are independent of every other variable._

There is one thing about the software we have now, compared to the software from back then: _It’s made of the same stuff._ It’s made of `if` statements, assignment statements, and `while` loops... ...you might object and say that we’ve got much better languages and superior paradigms... ...True—and yet the code is still just an assemblage of sequence, selection, and iteration, just as it was back in the 1960s and 1950s.

Changelessness of the code is the reason that the rules of software architecture are so consistent across system types. The rules of software architecture are the rules of ordering and assembling the building blocks of programs. And since those building blocks are universal and haven’t changed, the rules for ordering them are likewise universal and changeless.

## PART I Introduction

It doesn’t take a huge amount of knowledge and skill to get a program working... ...Getting it right is another matter entirely.

Getting software right is _hard._ It takes knowledge and skills... ...discipline and dedication... ...Mostly, it takes a passion for the craft and the desire to be a professional.

When software is done right, it requires a fraction of the human resources to create and maintain.

It is far more common to fight your way through terrible software designs than it is to enjoy the pleasure of working with a good one.

## Chapter 1 What Is Design and Architecture?

What is design? What is architecture? What are the differences between the two?... ...there is no difference between them. _None at all._

The low-level details and the high-level structure are all part of the same whole. They form a continuous fabric that defines the shape of the system. You can’t have one without the other; indeed, no clear dividing line separates them. There is simply a continuum of decisions from the highest to the lowest levels.

### The Goal?

_The goal of software architecture is to minimize the human resources required to build and maintain the required system._

The measure of design quality is simply the measure of the effort required to meet the needs of the customer. If that effort is low, and stays low... ...the design is good. If that effort grows with each new release, the design is bad.

### Case Study

“The race is not to the swift, nor the battle to the strong.”

“The more haste, the less speed.”

Modern developers... ...work their butts off. But a part of their brain _does_ sleep—the part that knows that good, clean, well-designed code _matters._

A familiar lie: “We can clean it up later; we just have to get to market first!” Of course, things never do get cleaned up later, because market pressures never abate. Getting to market first simply means that you’ve now got a horde of competitors on your tail, and you have to stay ahead of them by running as fast as you can.

Developers are overconfident in their ability to remain productive. But the creeping mess of code that saps their productivity never sleeps and never relents. If given its way, it will reduce productivity to zero in a matter of months.

The bigger lie that developers buy into is the notion that writing messy code makes them go fast in the short term, and just slows them down in the long term. Developers who accept this lie exhibit... ...overconfidence in their ability to switch modes from making messes to cleaning up messes sometime in the future, but they also make a simple error of fact. The fact is that _making messes is always slower than staying clean,_ no matter which time scale you are using.

_Making messes is always slower than staying clean._

_The only way to go fast, is to go well._

The only way to reverse the decline in productivity and the increase in cost is to get the developers to stop thinking... ...overconfident... ...and start taking responsibility for the mess that they’ve made.

_Their overconfidence will drive the redesign into the same mess as the original project._

### Conclusion

The best option is for the development organization to recognize and avoid its own overconfidence and to start taking the quality of its software architecture seriously.

To take software architecture seriously, you need to know what good software architecture is.

## Chapter 2 A Tale of Two Values

Every software system provides two different values to the stakeholders: behavior and structure.

### Behavior

The first value of software is its behavior. Programmers are hired to make machines behave in a way that makes or saves money for the stakeholders... ...Many programmers believe that is the entirety of their job. They believe their job is to make the machine implement the requirements and to fix any bugs. They are sadly mistaken.

### Architecture

Software was invented to be “soft.” It was intended to be a way to easily change the behavior of machines. If we’d wanted the behavior of machines to be hard to change, we would have called it _hardware._

Software must be soft—that is, it must be easy to change.

The difficulty in making a change should be proportional only to the scope of the change, and not to the _shape_ of the change.

It is this difference between scope and shape that often drives the growth in software development costs... ...From the stakeholders’ point of view, they are simply providing a stream of changes of roughly similar scope. From the developers’ point of view, the stakeholders are giving them a stream of jigsaw puzzle pieces that they must fit into a puzzle of ever-increasing complexity. Each new request is harder
to fit than the last, because the shape of the system does not match the shape of the request.

The more architecture prefers one shape over another, the more likely new features will be harder and harder to fit into that structure. Therefore architectures should be as shape agnostic are practical.

### The Greater Value

Function or architecture? Which of these two provides the greater value? Is it more important for the software system to work, or is it more important for the software system to be easy to change?... ...simple logical tool of examining the extremes

- _If you give me a program that works perfectly but is impossible to change, then it won’t work when the requirements change, and I won’t be able to make it work. Therefore the program will become useless._
- _If you give me a program that does not work but is easy to change, then I can make it work, and keep it working as requirements change. Therefore the program will remain continually useful._

If you ask the business managers if they want to be able to make changes, they’ll say that of course they do, but may then qualify their answer by noting that the current functionality is more important than any later flexibility. In contrast, if the business managers ask you for a change, and your estimated costs for that change are unaffordably high, the business managers will likely be furious that you allowed the system to get to the point where the change was impractical.

### Eisenhower’s Matrix

> I have two kinds of problems, the urgent and the important. The urgent are not important, and the important are never urgent.
> — Dwight D. Eisenhower

| **Important Urgent**   | **Important Not Urgent**   |
|------------------------|----------------------------|
| **Unimportant Urgent** | **Unimportant Not Urgent** |
Figure 2.1 Eisenhower matrix

The first value of software—behavior—is urgent but not always particularly important. The second value of software—architecture—is important but never particularly urgent.

four couplets into priorities:
1. Urgent and important
2. Not urgent and important
3. Urgent and not important
4. Not urgent and not important

The architecture of the code... ...is in the top two... ...whereas the behavior... ...occupies the first and _third_ positions.

The mistake... ...is to elevate items in position 3 to position 1... ...fail to separate those features that are urgent but not important from those features that truly are urgent and important... ...leads to ignoring the important architecture... ...in favor of the unimportant features.

Business managers are not equipped to evaluate the importance of architecture. _That’s what software developers were hired to do._ Therefore it is the responsibility of the software development team to assert the importance of architecture over the urgency of features.

### Fight for the Architecture

Remember, as a software developer, _you are a stakeholder._ You have a stake in the software that you need to safeguard. That’s part of your role, and part of your duty. And it’s a big part of why you were hired.

Software architects are... ...more focused on the structure of the system than on its features and functions... ...create an architecture that allows those features and functions to be easily developed, modified, and extended.

If architecture comes last, then the system will become ever more costly to develop, and eventually change will become practically impossible for part or all of the system.

## PART II Starting with the Bricks: Programming Paradigms

Software architecture begins with the code.

Alan Turing... ...was the first to understand that programs were simply data... ...writing real programs on real computers... ...in the late 1940s, came assemblers... ...relieved the programmers... ...of translating their programs into binary. In 1951, Grace Hopper invented A0, the first compiler. In fact, she coined the term _compiler._ Fortran was invented in 1953... ...What followed was an unceasing flood of new programming languages.

Paradigms are ways of programming, relatively unrelated to languages. A paradigm tells you which programming structures to use, and when to use them. 

## Chapter 3 Paradigm Overview

### Structured Programming

Dijkstra in 1968... ...showed that the use of unrestrained jumps (`goto` statements) is harmful to program structure... ...he replaced those jumps with... ...`if/then/else` and `do/while/until` constructs.

_Structured programming imposes discipline on direct transfer of control._

### Object-Oriented Programming

1966... ...Ole Johan Dahl and Kristen Nygaard... ...noticed that the function call stack frame in the `ALGOL` language could be moved to a heap, thereby allowing local variables declared by a function to exist long after the function returned. The function became a constructor for a class, the local variables became instance variables, and the nested functions became methods. This led inevitably to the discovery of polymorphism through the disciplined use of function pointers.

_Object-oriented programming imposes discipline on indirect transfer of control._

### Functional Programming

Its invention predates computer programming itself... ...Alonzo Church, in 1936 invented λ-calculus while pursuing the same mathematical problem that was motivating Alan Turing at the same time. His λ-calculus is the foundation of the LISP language, invented in 1958 by John McCarthy. A foundational notion of λ-calculus is immutability—that is, the notion that the values of symbols do not change. This effectively means that a functional language has no assignment statement.

_Functional programming imposes discipline upon assignment._

### Food for Thought

Each of the paradigms _removes_ capabilities from the programmer. None of them adds new capabilities. Each imposes some extra discipline that is _negative_ in its intent. The paradigms tell us what _not_ to do, more than they tell us what _to_ do.

The three paradigms together remove `goto` statements, function pointers, and assignment.

These three paradigms are likely to be the only three we will see... ...they were all discovered within the ten years between 1958 and 1968. In the many decades that have followed, no new paradigms have been added.

### Conclusion

What... ...paradigms have to do with architecture? Everything. We use polymorphism as the mechanism to cross architectural boundaries; we use functional programming to impose discipline on the location of and access to data; and we use structured programming as the algorithmic foundation of our modules... ...those three align with the three big concerns of architecture: function, separation of components, and data management.

## Chapter 4 Structured Programming

### Proof

Dijkstra recognized... ...that programming is _hard,_ and that programmers don’t do it very well... ...Dijkstra’s solution was to apply the mathematical discipline of _proof_... ...Dijkstra discovered that certain uses of `goto`... ...preventing use of the divide-and-conquer approach necessary for reasonable proofs. Other uses of `goto`, however, did not have this problem... ...these “good” uses of `goto` corresponded to... ...structures such as `if/then/else` and `do/while.` Modules that used those kinds of control structures _could_ be recursively subdivided into provable units... ...those control structures, when combined with sequential execution, were special... ...Böhm and Jacopini, who proved that all programs can be constructed from just three structures: sequence, selection, and iteration... ...The very control structures that made a module provable were the same minimum set of control structures from which all programs can be built. Thus structured programming was born.

### A Harmful Proclamation

Nowadays we are all structured programmers, though not necessarily by choice. It’s just that our languages don’t give us the option to use undisciplined direct transfer of control.

### Functional Decomposition

Structured programming allows modules to be recursively decomposed into provable units, which in turn means that modules can be functionally decomposed.

By following these disciplines, programmers could break down large proposed systems into modules and components that could be further broken down into tiny provable functions.

### No Formal Proofs

But the proofs never came. The Euclidean hierarchy of theorems was never built. And programmers at large never saw the benefits of working through the laborious process of formally proving each and every little function correct. In the end, Dijkstra’s dream faded and died.

### Science to the Rescue

Science is fundamentally different from mathematics, in that scientific theories and laws cannot be proven correct... ...I can demonstrate these laws to you, and I can make measurements that show them correct to many decimal places, but I cannot prove them in the sense of a mathematical proof...there is always the chance that some experiment will show that those laws... ...are incorrect.

Scientific theories and laws are _falsifiable_ but not provable.

Science does not work by proving statements true, but rather by _proving statements false._ Those statements that we cannot prove false, after much effort, we deem to be true enough for our purposes.

Not all statements are provable. The statement "This is a lie" is neither true nor false.

Mathematics is the discipline of proving provable statements true. Science, in contrast, is the discipline of proving provable statements false.

### Tests

> Testing shows the presence, not the absence, of bugs.
> — Dijkstra

A program can be proven incorrect by a test, but it cannot be proven correct.

Tests... ...after sufficient testing effort allow us to deem a program to be correct enough for our purposes.

Software development is not a mathematical endeavor, even though it seems to manipulate mathematical constructs. Rather, software is like a science. We show correctness by failing to prove incorrectness, despite our best efforts.

A program that is not provable... ...cannot be deemed correct no matter how many tests are applied to it.

Structured programming forces us to recursively decompose a program into a set of small provable functions. We can then use tests to try to prove those small provable functions incorrect. If such tests fail to prove incorrectness, then we deem the functions to be correct enough for our purposes.

### Conclusion

It is this ability to create falsifiable units of programming that makes structured programming valuable today... ...Moreover, at the architectural level, this is why we still consider _functional decomposition_ to be one of our best practices.

Software is like a science... ...is driven by falsifiability. Software architects strive to define modules, components, and services that are easily falsifiable (testable). To do so, they employ restrictive disciplines similar to structured programming, albeit at a much higher level.

## Chapter 5 Object-Oriented Programming

The basis of a good architecture is the understanding and application of the principles of object-oriented design (OO).

Three magic words to explain the nature of OO: _encapsulation, inheritance, and polymorphism_... ...an OO language must support these three things.

### Encapsulation?

OO languages provide easy and effective encapsulation of data and function.

A line can be drawn around a cohesive set of data and functions. Outside of that line, the data is hidden and only some of the functions are known. We see this concept in action as the private data members and the public member functions of a class.

This idea is certainly not unique to OO. Indeed, we had perfect encapsulation in C... ...But then came OO in the form of C++—and the perfect encapsulation of C was broken. Java and C# simply abolished the header/implementation split altogether, thereby weakening encapsulation even more. In these languages, it is impossible to separate the declaration and definition of a class. For these reasons, it is difficult to accept that OO depends on strong encapsulation... ...the languages that claim to provide OO have only weakened the once perfect encapsulation we enjoyed with C.

### Inheritance?

Inheritance is simply the redeclaration of a group of variables and functions within an enclosing scope.

We might say that we had a kind of inheritance long before OO languages were invented. That statement wouldn’t quite be true, though. We had a trick, but it’s not nearly as convenient as true inheritance. Moreover, multiple inheritance is a considerably more difficult to achieve by such trickery.

While OO languages did not give us something completely brand new, it did make the masquerading of data structures significantly more convenient.

### Polymorphism?

Polymorphic behavior before OO languages? Of course... ...Consider this simple C `copy` program.

```c
#include <stdio.h>
void copy() {
  int c;
  while ((c=getchar()) != EOF)
    putchar(c);
}
```

These functions are _polymorphic_—their behavior depends on the type of `STDIN` and `STDOUT`... ...The UNIX operating system requires that every IO device driver provide five standard functions: `open`, `close`, `read`, `write`, and `seek`. The signatures of those functions must be identical for every IO driver.

The bottom line is that polymorphism is an application of pointers to functions... ...since Von Neumann architectures were first implemented in the late 1940s... ...OO languages may not have given us polymorphism, but they have made it much safer and much more convenient.

The problem with explicitly using pointers to functions to create polymorphic behavior is that pointers to functions are _dangerous._ Such use is driven by a set of manual conventions... ...OO languages eliminate these conventions and, therefore, these dangers.

OO imposes discipline on indirect transfer of control.

#### The Power of Polymorphism

The IO devices have become plugins... ...our programs should be _device independent._

OO allows the plugin architecture to be used anywhere, for anything.

#### Dependency Inversion

Before a safe and convenient mechanism for polymorphism was available. In the typical calling tree, main functions called high-level functions, which called mid-level functions, which called low-level functions... ...source code dependencies inexorably followed the flow of control (Figure 5.1).

![Figure 5.1 Source code dependencies versus flow of control](./figure5.1.jpg)
Figure 5.1 Source code dependencies versus flow of control

![Figure 5.2 Dependency inversion](./figure5.2.jpg)
Figure 5.2 Dependency inversion

In Figure 5.2, module `HL1` calls the `F()` function in module `ML1`... ...At runtime, the interface doesn’t exist. `HL1` simply calls `F()` within `ML1`... ...the source code dependency (the inheritance relationship) between `ML1` and the interface `I` points in the opposite direction compared to the flow of control. This is called _dependency inversion,_ and its implications for the software architect are profound... ...convenient polymorphism means that _any source code dependency, no matter where it is, can be inverted_... ...software architects... ...have _absolute control_ over the direction of all source code dependencies in the system. They are not constrained to align those dependencies with the flow of control. No matter which module does the calling and which module is called, the software architect can point the source code dependency in either direction... ...That is the power that OO provides.

UI and the database can be plugins to the business rules... ...the source code of the business rules never mentions the UI or the database.

When the source code in a component changes, only that component needs to be redeployed. This is _independent deployability._

If the modules in your system can be deployed independently, then they can be developed independently by different teams. That’s _independent developability._

### Conclusion

OO is the ability, through the use of polymorphism, to gain absolute control over every source code dependency in the system.

It allows... ...to create a plugin architecture,... ...The low-level details are relegated to plugin modules that can be deployed and developed independently from the modules that contain high-level policies.

## Chapter 6 Functional Programming

Functional programming predate programming itself... ...is based on the λ-calculus invented by Alonzo Church in the 1930s.

### Squares of Integers

Java Program

```java
public class Squint {
  public static void main(String args[]) {
    for (int i=0; i<25; i++)
    System.out.println(i*i);
  }
}
```

Clojure Program

```clojure
(println (take 25 (map (fn [x] (* x x)) (range))))
```

```clojure
(println ;___________________ Print
  (take 25 ;_________________ the first 25
    (map (fn [x] (* x x)) ;__ squares 
      (range)))) ;___________ of Integers
```

The Java program uses a _mutable variable_—a variable that changes state during the execution of the program... ...In the Clojure program, variables like x are initialized, but they are never modified.

Variables in functional languages _do not vary._

### Immutability and Architecture

All race conditions, deadlock conditions, and concurrent update problems are due to mutable variables... ...all the problems that we face in concurrent applications—all the problems we face in applications that require multiple threads, and multiple processors—cannot happen if there are no mutable variables.

Immutability is practicable... ...if you have infinite storage and infinite processor speed. Lacking those infinite resources, the answer is a bit more nuanced.

### Segregation of Mutability

One of the most common compromises in regard to immutability is to segregate the application... ...into mutable and immutable components. The immutable components perform their tasks in a purely functional way, without using any mutable variables... ...communicate with... ...other components that are not purely functional, and allow for the state of variables to be mutated (Figure 6.1).

![Figure 6.1 Mutating state and transactional memory](./figure6.1.jpg)
Figure 6.1 Mutating state and transactional memory

It is common practice to use... ..._transactional memory_ to protect the mutable variables from concurrent updates and race conditions... ...It protects those variables with a transaction-or retry-based scheme.

Well-structured applications will be segregated into those components that do not mutate variables and those that do... ...by the use of appropriate disciplines to protect those mutated variables. Architects would be wise to push as much processing as possible into the immutable components, and to drive as much code as possible out of those components that must allow mutation.

### Event Sourcing

The more memory we have, and the faster our machines are, the less we need mutable state.

Imagine a banking application that maintains the account balances of its customers. It mutates those balances when deposit and withdrawal transactions are executed. Now imagine that instead of storing the account balances, we store only the transactions. Whenever anyone wants to know the balance of an account, we simply add up all the transactions for that account, from the beginning of time. This scheme requires no mutable variables... ...Over time, the number of transactions would grow without bound, and the processing power required to compute the totals would become intolerable. To make this scheme work forever, we would need infinite storage and infinite processing power. But perhaps we don’t have to make the scheme work forever. And perhaps we have enough storage and enough processing power to make the scheme work for the reasonable lifetime of the application. This is the idea behind _event sourcing._

Event sourcing is a strategy wherein we store the transactions, but not the state. When state is required, we simply apply all the transactions from the beginning of time.

We can take shortcuts... ...and save the state every midnight. Then... ...we need compute only the transactions since midnight.

Nothing ever gets deleted or updated from such a data store. As a consequence, our applications are not CRUD; they are just CR... ...there cannot be any concurrent update issues.

If we have enough storage and enough processor power, we can make our applications entirely immutable—and, therefore, _entirely functional._

This is the way your source code control system works.

### Conclusion

- Structured programming is discipline imposed upon direct transfer of control.
- Object-oriented programming is discipline imposed upon indirect transfer of control.
- Functional programming is discipline imposed upon variable assignment.

Each of these three paradigms has taken something away from us. Each restricts some aspect of the way we write code. None of them has added to our power or our capabilities.

Software is not a rapidly advancing technology. The rules of software are the same today as they were in 1946, when Alan Turing wrote the very first code... ...The tools have changed, and the hardware has changed, but the essence of software remains the same.

Software—the stuff of computer programs—is composed of sequence, selection, iteration, and indirection. Nothing more. Nothing less.

## PART III Design Principles

Good software systems begin with clean code. On the one hand, if the bricks aren’t well made, the architecture of the building doesn’t matter much. On the other hand, you can make a substantial mess with well-made bricks. This is where the SOLID principles come in.

The SOLID principles tell us how to arrange our functions and data structures into classes, and how those classes should be interconnected. The use of the word "class" does not imply that these principles are applicable only to object-oriented software. A class is simply a coupled grouping of functions and data. Every software system has such groupings, whether they are called classes or not. The SOLID principles apply to those groupings.

The goal of the principles is the creation of mid-level software structures that:
- Tolerate change,
- Are easy to understand, and
- Are the basis of components that can be used in many software systems.

The term "mid-level" refers to the fact that... ...They are applied just above the level of the code and help to define the kinds of software structures used within modules and components.

The executive summary:
- **SRP:** The Single Responsibility Principle. An active corollary to Conway’s law: The best structure for a software system is heavily influenced by the social structure of the organization that uses it so that each software module has one, and only one, reason to change.
- **OCP:** The Open-Closed Principle. Bertrand Meyer made this principle famous in the 1980s. The gist is that for software systems to be easy to change, they must be designed to allow the behavior of those systems to be changed by adding new code, rather than changing existing code.
- **LSP:** The Liskov Substitution Principle. Barbara Liskov’s famous definition of subtypes, from 1988. In short, this principle says that to build software systems from interchangeable parts, those parts must adhere to a contract that allows those parts to be substi- tuted one for another.
- **ISP:** The Interface Segregation Principle. This principle advises software designers to avoid depending on things that they don’t use.
- **DIP:** The Dependency Inversion Principle. The code that implements high-level policy should not depend on the code that implements low-level details. Rather, details should depend on policies.

> Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure.
> — Melvin E. Conway

## Chapter 7 SRP: The Single Responsibility Principle

The Single Responsibility Principle (SRP) might be the least well understood... ...It is too easy for programmers to hear the name and then assume that it means that every module should do just one thing... ...there _is_ a principle like that. A _function_ should do one, and only one, thing. We use that... ...when we are refactoring... ...at the lowest levels. But it is not one of the SOLID principles—it is not the SRP.

Historically, the SRP has been described this way: _A module should have one, and only one, reason to change_... ...satisfy users and stakeholders... ..._are_ the "reason to change"... ...Indeed, we can rephrase the principle to... ..._A module should be responsible to one, and only one, user or stakeholder_... ...the words "user" and "stakeholder" aren’t really the right words to use here... ...we’re really referring to a group... ...We’ll refer to that group as an _actor._ Thus the final version of the SRP is: _A module should be responsible to one, and only one, actor._

A module is just a cohesive set of functions and data structures... ..."cohesive" implies the SRP. Cohesion is the force that binds together the code responsible to a single actor.

The best way to understand this principle is by looking at the symptoms of violating it.

### Symptom 1: Accidental Duplication

![Figure 7.1 The Employee class](./figure7.1.jpg)
Figure 7.1 The `Employee` class

`Employee` class three methods: _calculatePay()_, _reportHours()_, and _save()_ (Figure 7.1)... ...violates the SRP because those three methods are responsible to... ...different actors.
- The `calculatePay()`... ...by the accounting department, which reports to the CFO.
- The `reportHours()`... ...by the human resources department, which reports to the COO.
- The `save()`... ...by the database administrators (DBAs), who report to the CTO
By putting... ...these three methods into a single `Employee` class, the developers have coupled each of these actors to the others. This Symptom 1: Accidental Duplication coupling can cause the actions of the CFO’s team to affect something that the COO’s team depends on.

These problems occur because we put code that different actors depend on into close proximity. The SRP says to _separate the code that different actors depend on._

### Symptom 2: Merges

Merges will be common in source files that contain many different methods. This situation is especially likely if those methods are responsible to different actors.

Merges are risky affairs... ...no tool can deal with every merge case. In the end, there is always risk.

Multiple people changing the same source file for different reasons... ...to avoid this problem is to _separate code that supports different actors._

### Solutions

Many different solutions to this problem. Each moves the functions into different classes.

The most obvious way to solve the problem is to separate the data from the functions... ...

![Figure 7.3 The three classes do not know about each other](./figure7.3.jpg)
Figure 7.3 The three classes do not know about each other

The downside of this solution is that the developers now have three classes that they have to instantiate and track. A common solution to this dilemma is to use the _Facade_ pattern (Figure 7.4).

![Figure 7.4 The Facade pattern](./figure7.4.jpg)
Figure 7.4 The `Facade` pattern

The `EmployeeFacade` contains very little code. It is responsible for instantiating and delegating to the classes with the functions.

To keep the most important business rules closer to the data... ...can be done by keeping the most important method in the original Employee class and then using that class as a Facade for the lesser functions (Figure 7.5).

![Figure 7.5 The most important method is kept in the original Employee class and used as a Facade for the lesser functions](./figure7.5.jpg)
Figure 7.5 The most important method is kept in the original `Employee` class and used as a Facade for the lesser functions

Every class would contain just one function. This is hardly the case. The number of functions required... ...is likely to be large in each case. Each of those classes would have many _private_ methods in them.

Each of the classes that contain such a family of methods is a scope. Outside of that scope, no one knows that the private members of the family exist.

### Conclusion

The Single Responsibility Principle is about functions and classes... ...At the level of components, it becomes the Common Closure Principle. At the architectural level, it becomes the Axis of Change responsible for the creation of Architectural Boundaries.

## Chapter 8 OCP: The Open-Closed Principle

The Open-Closed Principle (OCP) was coined in 1988 by Bertrand Meyer.

> A software artifact should be open for extension but closed for modification.
> — Bertrand Meyer.

The behavior of a software artifact ought to be extendible, without having to modify that artifact... ...is the most fundamental reason that we study software architecture... ...if simple extensions to the requirements force massive changes to the software, then the architects... ...have engaged in a spectacular failure.

## A Thought Experiment

Imagine... ...that we have a system... ...some new code must be written. But how much old code will have to change? A good software architecture would reduce the amount of changed code to the barest minimum. Ideally, zero. How? By properly separating the things that change for different reasons (the Single Responsibility Principle), and then organizing the dependencies between those things properly (the Dependency Inversion Principle).

![Figure 8.1 Applying the SRP](./figure8.1.jpg)
Figure 8.1 Applying the SRP

Applying the SRP, we... ...come up with the data-flow view shown in Figure 8.1.... ...generating the report involves two separate responsibilities: the calculation of the reported data, and the presentation of that data into a web- and printer-friendly form.

Having made this separation, we need to organize the source code dependencies to ensure that changes to one of those responsibilities do not cause changes in the other. Also, the new organization should ensure that the behavior can be extended without undo modification.

Partitioning the processes into classes, and separating those classes into components, as shown... ...in the diagram in Figure 8.2. In this figure, the component at the upper left is the _Controller._ At the upper right, we have the _Interactor._ At the lower right, there is the _Database._ Finally, at the lower left, there are four components that represent the _Presenters_ and the _Views._ Classes marked with `<I>` are interfaces; those marked with `<DS>` are data structures. Open arrowheads are _using_ relationships. Closed arrowheads are _implements_ or _inheritance_ relationships.

![Figure 8.2 Partitioning the processes into classes and separating the classes into components](./figure8.2.jpg)
Figure 8.2 Partitioning the processes into classes and separating the classes into components

All the dependencies are _source code_ dependencies. An arrow pointing from class A to class B means that the source code of class A mentions the name of class B, but class B mentions nothing about class A. 

all component relationships are unidirectional, as shown in the component graph in Figure 8.3. These arrows point toward the components that we want to protect from change.

![Figure 8.3 The component relationships are unidirectional](./figure8.3.jpg)
Figure 8.3 The component relationships are unidirectional

If component A should be protected from changes in component B, then component B should depend on component A.

We want to protect the _Controller_ from changes in the _Presenters._ We want to protect the _Presenters_ from changes in the _Views._ We want to protect the _Interactor_ from changes in—well, _anything._... ...Because it contains the business rules. The Interactor contains the highest-level policies of the application. All the other components are dealing with peripheral concerns. The _Interactor_ deals with the central concern.

This creates a hierarchy of protection based on the notion of "level." _Interactors_ are the highest-level concept, so they are the most protected. _Views_ are among the lowest-level concepts, so they are the least protected. _Presenters_ are higher level than _Views,_ but lower level than the _Controller_ or the _Interactor._

How the OCP works at the architectural level. Architects separate functionality based on how, why, and when it changes, and then organize that separated functionality into a hierarchy of components. Higher-level components in that hierarchy are protected from the changes made to lower-level components.

### Directional Control

Much of the complexity... ...was intended to make sure that the dependencies between the components pointed in the correct direction. For example, the `FinancialDataGateway` interface between the `FinancialReportGenerator` and the `FinancialDataMapper` exists to invert the dependency that would otherwise have pointed from the _Interactor_ component to the _Database_ component.

### Information Hiding

The `FinancialReportRequester` is there to protect the `FinancialReportController` from knowing too much about the internals of the _Interactor._ If that interface were not there, then the _Controller_ would have transitive dependencies on the `FinancialEntities`.

Transitive dependencies are a violation of the general principle that software entities should not depend on things they don’t directly use.

Even though our first priority is to protect the _Interactor_ from changes to the _Controller,_ we also want to protect the _Controller_ from changes to the _Interactor_ by hiding the internals of the _Interactor._

### Conclusion

The OCP... ...goal is to make the system easy to extend without incurring a high impact of change. Accomplished by partitioning the system into components, and arranging those components into a dependency hierarchy that protects higher-level components from changes in lower-level components.

## Chapter 9 LSP: The Liskov Substitution Principle

> What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.
> — Barbara Liskov, “Data Abstraction and Hierarchy,” SIGPLAN Notices 23, 5 (May 1988).

### Guiding the Use of Inheritance

Imagine... ...a class named `License`, as shown in Figure 9.1... ...`calcFee()`, is called by the `Billing` application... ...This design conforms to the LSP because the behavior of the `Billing` application does not depend,... ...on which of the two subtypes it uses. Both of the subtypes are substitutable for the `License` type.

![Figure 9.1 License, and its derivatives, conform to LSP](./figure9.1.jpg)
Figure 9.1 `License`, and its derivatives, conform to LSP

### The Square/Rectangle Problem

![Figure 9.2 The infamous square/rectangle problem](./figure9.2.jpg)
Figure 9.2 The infamous square/rectangle problem

The canonical example of a violation of the LSP is the... ...square/rectangle problem (Figure 9.2)... ...`Square` is not a proper subtype of `Rectangle` because the height and width of the `Rectangle` are independently mutable; in contrast, the height and width of the `Square` must change together... ...to defend against this kind of LSP violation... ...add mechanisms to the `User` (such as an `if` statement) that detects whether the `Rectangle` is, in fact, a `Square`. Since the behavior of the `User` depends on the types it uses, those types are not substitutable.

### LSP and Architecture

In the early years... ...LSP... ...way to guide the use of inheritance... ...However, over the years... ...has morphed into a broader principle of software design... ...to interfaces and implementations.

The LSP is applicable because there are users who depend on well-defined interfaces, and on the substitutability of the implementations of those interfaces.

The best way to understand the LSP from an architectural viewpoint is to look at what happens to the architecture of a system when the principle is violated.

### Example LSP Violation

No architect worth his or her salt would allow... ...Putting word... ...into the code itself creates an opportunity for all kinds of horrible and mysterious errors, not to mention security breaches.

### Conclusion

The LSP can, and should, be extended to the level of architecture. A simple violation of substitutability, can cause a system’s architecture to be polluted with a significant amount of extra mechanisms.

## Chapter 10 ISP: The Interface Segregation Principle

![Figure 10.1 The Interface Segregation Principle](./figure10.1.jpg)
Figure 10.1 The Interface Segregation Principle

The Interface Segregation Principle (ISP) derives... ...from the diagram... ...in Figure 10.1... ...several users who use the operations of the `OPS` class... ...the source code of `User1` will... ...depend on `op2` and `op3`, even though it doesn’t call them... ...a change to the source code of `op2` in `OPS` will force `User1` to be recompiled and redeployed... ...This problem can be resolved by segregating the operations into interfaces as shown in Figure 10.2... ...`User1` will depend on `U1Ops`, and `op1`, but will not depend on `OPS`. Thus a change to `OPS` that `User1` does not care about will not cause `User1` to be recompiled and redeployed.

![Figure 10.2 Segregated operations](./figure10.2.jpg)
Figure 10.2 Segregated operations

## ISP and Language
## ISP and Architecture
## Conclusion
## Chapter 11 DIP: The Dependency Inversion Principle
## Stable Abstractions
## Factories
## Concrete Components
## Conclusion
## PART IV Component Principles
## Chapter 12 Components
## A Brief History of Components
## Relocatability
## Linkers
## Conclusion
## Chapter 13 Component Cohesion
## The Reuse/Release Equivalence Principle
## The Common Closure Principle
## The Common Reuse Principle
## The Tension Diagram for Component Cohesion
## Conclusion
## Chapter 14 Component Coupling
## The Acyclic Dependencies Principle
## Top-Down Design
## The Stable Dependencies Principle
## The Stable Abstractions Principle
## Conclusion
## PART V Architecture
## Chapter 15 What Is Architecture?
## Development
## Deployment
## Operation
## Maintenance
## Keeping Options Open
## Device Independence
## Junk Mail
## Physical Addressing
## Conclusion
## Chapter 16 Independence
## Use Cases
## Operation
## Development
## Deployment
## Leaving Options Open
## Decoupling Layers
## Decoupling Use Cases
## Decoupling Mode
## Independent Develop-ability
## Independent Deployability
## Duplication
## Decoupling Modes (Again)
## Conclusion
## Chapter 17 Boundaries: Drawing Lines
## A Couple of Sad Stories
## FitNesse
## Which Lines Do You Draw, and When Do You Draw Them?
## What About Input and Output?
## Plugin Architecture
## The Plugin Argument
## Conclusion
## Chapter 18 Boundary Anatomy
## Boundary Crossing
## The Dreaded Monolith
## Deployment Components
## Threads
## Local Processes
## Services
## Conclusion
## Chapter 19 Policy and Level
## Level
## Conclusion
## Chapter 20 Business Rules
## Entities
## Use Cases
## Request and Response Models
## Conclusion
## Chapter 21 Screaming Architecture
## The Theme of an Architecture
## The Purpose of an Architecture
## But What About the Web?
## Frameworks Are Tools, Not Ways of Life
## Testable Architectures
## Conclusion
## Chapter 22 The Clean Architecture
## The Dependency Rule
## A Typical Scenario
## Conclusion
## Chapter 23 Presenters and Humble Objects
## The Humble Object Pattern
## Presenters and Views
## Testing and Architecture
## Database Gateways
## Data Mappers
## Service Listeners
## Conclusion
## Chapter 24 Partial Boundaries
## Skip the Last Step
## One-Dimensional Boundaries
## Facades
## Conclusion
## Chapter 25 Layers and Boundaries
## Hunt the Wumpus
## Clean Architecture?
## Crossing the Streams
## Splitting the Streams
## Conclusion
## Chapter 26 The Main Component
## The Ultimate Detail
## Conclusion
## Chapter 27 Services: Great and Small
## Service Architecture?
## Service Benefits?
## The Kitty Problem
## Objects to the Rescue
## Component-Based Services
## Cross-Cutting Concerns
## Conclusion
## Chapter 28 The Test Boundary
## Tests as System Components
## Design for Testability
## The Testing API
## Conclusion
## Chapter 29 Clean Embedded Architecture
## App-titude Test
## The Target-Hardware Bottleneck
## Conclusion
## PART VI Details
## Chapter 30 The Database Is a Detail
## Relational Databases
## Why Are Database Systems So Prevalent?
## What If There Were No Disk?
## Details
## But What about Performance?
## Anecdote
## Conclusion
## Chapter 31 The Web Is a Detail
## The Endless Pendulum
## The Upshot
## Conclusion
## Chapter 32 Frameworks Are Details
## Framework Authors
## Asymmetric Marriage
## The Risks
## The Solution
## I Now Pronounce You …
## Conclusion
## Chapter 33 Case Study: Video Sales
## The Product
## Use Case Analysis
## Component Architecture
## Dependency Management
## Conclusion
## Chapter 34 The Missing Chapter
## Package by Layer
## Package by Feature
## Ports and Adapters
## Package by Component
## The Devil Is in the Implementation Details
## Organization versus Encapsulation
## Other Decoupling Modes
## Conclusion: The Missing Advice
## Afterword
## PART VII Appendix
## Appendix A Architecture Archaeology
## Index
