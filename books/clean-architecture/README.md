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

## Structured Programming

Dijkstra in 1968... ...showed that the use of unrestrained jumps (`goto` statements) is harmful to program structure... ...he replaced those jumps with... ...`if/then/else` and `do/while/until` constructs.

_Structured programming imposes discipline on direct transfer of control._

## Object-Oriented Programming
## Functional Programming
## Food for Thought
## Conclusion
## Chapter 4 Structured Programming
## Proof
## A Harmful Proclamation
## Functional Decomposition
## No Formal Proofs
## Science to the Rescue
## Tests
## Conclusion
## Chapter 5 Object-Oriented Programming
## Encapsulation?
## Inheritance?
## Polymorphism?
## Conclusion
## Chapter 6 Functional Programming
## Squares of Integers
## Immutability and Architecture
## Segregation of Mutability
## Event Sourcing
## Conclusion
## PART III Design Principles
## Chapter 7 SRP: The Single Responsibility Principle
## Symptom 1: Accidental Duplication
## Symptom 2: Merges
## Solutions
## Conclusion
## Chapter 8 OCP: The Open-Closed Principle
## A Thought Experiment
## Directional Control
## Information Hiding
## Conclusion
## Chapter 9 LSP: The Liskov Substitution Principle
## Guiding the Use of Inheritance
## The Square/Rectangle Problem
## LSP and Architecture
## Example LSP Violation
## Conclusion
## Chapter 10 ISP: The Interface Segregation Principle
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
