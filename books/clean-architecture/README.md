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
## Behavior
## Architecture
## The Greater Value
## Eisenhower’s Matrix
## Fight for the Architecture
## PART II Starting with the Bricks: Programming Paradigms
## Chapter 3 Paradigm Overview
## Structured Programming
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
