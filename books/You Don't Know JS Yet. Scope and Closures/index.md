---
name: "You Don't Know JS Yet. Scope and Closures"
Read: ['2022']
Genre: ['Software Development', 'Good Practices', 'JavaScript']
---

![Cover](./assets/you-dont-know-js-yet-scope-closures.jpg)

# You Don't Know JS Yet. Scope and Closures

Kyle Simpson - 2020

## Table of Contents

- Foreword
- Preface
- Chapter 1: What's the Scope?
    - About This Book
    - Compiled vs. Interpreted
    - Compiling Code
    - Compiler Speak
    - Cheating: Run-Time Scope Modifications
    - Lexical Scope
- Chapter 2: Illustrating Lexical Scope
    - Marbles, and Buckets, and Bubbles... Oh My!
    - A Conversation Among Friends
    - Nested Scope
    - Continue the Conversation
- Chapter 3: The Scope Chain
    - "Lookup" Is (Mostly) Conceptual
    - Shadowing
    - Function Name Scope
    - Arrow Functions
    - Backing Out
- Chapter 4: Around the Global Scope
    - Why Global Scope?
    - Where Exactly is this Global Scope?
    - Global This
    - Globally Aware
- Chapter 5: The (Not So) Secret Lifecycle of Variables
    - When Can I Use a Variable?
    - Hoisting: Yet Another Metaphor
    - Re-declaration?
    - Uninitialized Variables (aka, TDZ)
    - Finally Initialized
- Chapter 6: Limiting Scope Exposure
    - Least Exposure
    - Hiding in Plain (Function) Scope
    - Scoping with Blocks
    - Function Declarations in Blocks
    - Blocked Over
- Chapter 7: Using Closures
    - See the Closure
    - The Closure Lifecycle and Garbage Collection (GC)
    - Why Closure?
    - An Alternative Perspective
    - Closer to Closure
- Chapter 8: The Module Pattern
    - Encapsulation and Least Exposure (POLE)
    - What is a Module?
    - Node CommonJS Modules
    - Modern ES Modules (ESM)
    - Exit Scope
- Appendix A: Exploring Further
    - Implied Scopes
    - Anonymous vs. Named Functions
    - Hoisting: Functions and Variables
    - The Case for `var`
    - What's the Deal with TDZ?
    - Are Synchronous Callbacks Still Closures?
    - Classic Module Variations
- Appendix B: Practice
    - Buckets of Marbles
    - Closure (PART 1)
    - Closure (PART 2)
    - Closure (PART 3)
    - Modules
    - Suggested Solutions


## Foreword

What’s ironic to me is that the most loved of my books often look the least cared for, though honestly the opposite is true.

Over the years, even though I wasn’t necessarily feeling my own improvement on a day-to-day basis, each one of the concepts became more approachable. I’d smile to myself, realizing how far I’d come with the help of these guides. It became apparent there was an inverse correlation between how well I treated the book and how much I loved it.

## Preface

These books approach JavaScript intentionally opposite of how The Good Parts treats the language. No, that doesn’t mean we’re looking at the bad parts, but rather, exploring all the parts.

You may have been told, or felt yourself, that JS is a deeply flawed language that was poorly designed and inconsistently implemented. Many have asserted that it’s the worst most popular language in the world; that nobody writes JS because they want to, only because they have to given its place at the center of the web. That’s a ridiculous, unhealthy, and wholly condescending claim.

Like any great language, it has its brilliant parts as well as its scars.

Don’t buy the “X is the new Y” snake oil, that some new feature of the language instantly relegates all usage of a previous feature as obsolete and ignorant.

Every part of JS is useful. Some parts are more useful than others. Some parts require you to be more careful and intentional.

Ask why for every line of code you write. Why does it do what it does? Why is one way better or more appropriate than the other half-dozen ways you could have accomplished it? Why do all the “popular kids” say to do X with your code, but it turns out that Y might be a better choice?

You don’t finish knowing everything about JS, you just keep learning more and more as you spend more time with the language. And the deeper you go, the more you revisit what you knew before, and you re-learn it from that more experienced perspective.

You can always know JS better than you currently do.

You will always be more effective in your development work if you more completely understand how your code works than you are solely just getting it to produce a desired outcome.

In other words, good enough to work is not, and should not be, good enough.

These books serve as both the question and answer: why did it do this, and here’s how to get it to do that instead. My mission with YDKJSY is to empower every single JS developer to fully own the code they write, to understand it and to write with intention and clarity.

You could spend a week or two on each chapter, and a month or two on each book, and a year or more on the whole series, and you would still not be squeezing every ounce of YDKJSY out.

## Chapter 1: What's the Scope?

How does JS know which variables are accessible by any given statement, and how does it handle two variables of the same name?

Our first step is to uncover how the JS engine processes our program before it runs.

### About This Book

JS is typically classified as an interpreted scripting language, so it’s assumed by most that JS programs are processed in a single, top-down pass. But JS is in fact parsed/compiled in a separate phase before execution begins. The code author’s decisions on where to place variables, functions, and blocks with respect to each other are analyzed according to the rules of scope, during the initial parsing/compilation phase. The resulting scope structure is generally unaffected by runtime conditions.

JS functions are themselves first-class values; they can be assigned and passed around just like numbers or strings. But since these functions hold and access variables, they maintain their original scope no matter where in the program the functions are eventually executed. This is called closure.

Modules are a code organization pattern characterized by public methods that have privileged access (via closure) to hidden variables and functions in the internal scope of the module.

### Compiled vs. Interpreted

Code compilation is a set of steps that process the text of your code and turn it into a list of instructions the computer can understand. 

Interpretation performs a similar task to compilation, in that it transforms your program into machine-understandable instructions. But the processing model is different. Unlike a program being compiled all at once, with interpretation the source code is transformed line by line; each line or statement is executed before immediately proceeding to processing the next line of the source code.

![Fig. 1: Compiled vs. Interpreted Code](./assets/figure1.jpg)

JS is most accurately portrayed as a compiled language

### Compiling Code

Scope is primarily determined during compilation, so understanding how compilation and execution relate is key in mastering scope.

In classic compiler theory, a program is processed by a compiler in three basic stages:

1. Tokenizing/Lexing: breaking up a string of characters into meaningful (to the language) chunks, called tokens. For instance, consider the program: `var a = 2;`. This program would likely be broken up into the following tokens: `var, a, =, 2`, and ;. (The difference between tokenizing and lexing is subtle and academic, but it centers on whether or not these tokens are identified in a stateless or stateful way. Put simply, if the tokenizer were to invoke stateful parsing rules to figure out whether a should be considered a distinct token or just part of another token, that would be lexing.)

2. Parsing: taking a stream (array) of tokens and turning it into a tree of nested elements, which collectively represent the grammatical structure of the program. This is called an Abstract Syntax Tree (AST).

3. Code Generation: taking an AST and turning it into executable code. This part varies greatly depending on the language, the platform it’s targeting, and other factors.

The JS engine is vastly more complex than just these three stages. In the process of parsing and code generation, there are steps to optimize the performance of the execution (i.e., collapsing redundant elements).

JS engines don’t have the luxury of an abundance of time to perform their work and optimizations, because JS compilation doesn’t happen in a build step ahead of time, as with other languages. It usually must happen in mere microseconds

To ensure the fastest performance under these constraints, JS engines use all kinds of tricks (like JITs, which lazy compile and even hot re-compile); these are well beyond the “scope” of our discussion here.

#### Required: Two Phases

The separation of a parsing/compilation phase from the subsequent execution phase is observable fact, not theory or opinion. While the JS specification does not require “compilation” explicitly, it requires behavior that is essentially only practical with a compile-then-execute approach.

There are three program characteristics you can observe to prove this to yourself: syntax errors, early errors, and hoisting. Syntax Errors from the Start. Consider this program:

```js
var greeting = "Hello";

console.log(greeting);

greeting = ."Hi";
// SyntaxError: unexpected token .
```

This program produces no output (`"Hello"` is not printed), but instead throws a `SyntaxError` about the unexpected . token right before the `"Hi"` string. Since the syntax error happens after the well-formed `console.log(..)` statement, if JS was executing top-down line by line, one would expect the `"Hello"` message being printed before the syntax error being thrown. That doesn’t happen.

In fact, the only way the JS engine could know about the syntax error on the third line, before executing the first and second lines, is by the JS engine first parsing the entire program before any of it is executed.

Early errors. Next, consider:

```js
console.log("Howdy");

saySomething("Hello","Hi");
// Uncaught SyntaxError: Duplicate parameter name not
// allowed in this context

function saySomething(greeting,greeting) {
    "use strict";
    console.log(greeting);
}
```

The `"Howdy"` message is not printed, despite being a well-formed statement. Instead, just like the snippet in the previous section, the `SyntaxError` here is thrown before the program is executed. In this case, it’s because strict-mode (opted in for only the `saySomething(..)` function here) forbids, among many other things, functions to have duplicate parameter names; this has always been allowed in non-strict-mode.

How does it know that the `saySomething(..)` function is even in strict-mode while processing the parameter list (the `"use strict"` pragma appears only later, in the function body)?

Again, the only reasonable explanation is that the code must first be fully parsed before any execution occurs.

Hoisting. Finally, consider:

```js
function saySomething() {
    var greeting = "Hello";
    {
        greeting = "Howdy";  // error comes from here
        let greeting = "Hi";
        console.log(greeting);
    }
}

 
saySomething();
// ReferenceError: Cannot access 'greeting' before
// initialization
```

The only way the JS engine could know, at the line where the error is thrown, that the next statement would declare a block-scoped variable of the same name (`greeting`) is if the JS engine had already processed this code in an earlier pass, and already set up all the scopes and their variable associations. This processing of scopes and declarations can only accurately be accomplished by parsing the program before execution. The `ReferenceError` here technically comes from `greeting = "Howdy"` accessing the `greeting` variable too early, a conflict referred to as the Temporal Dead Zone (TDZ). Chapter 5 will cover this in more detail.

WARNING:

Hopefully you’re now convinced that JS programs are parsed before any execution begins. But does it prove they are compiled? This is an interesting question to ponder. Could JS parse a program, but then execute that program by interpreting operations represented in the AST without first compiling the program? Yes, that is possible. But it’s extremely unlikely, mostly because it would be extremely inefficient performance wise.

In spirit and in practice, what the engine is doing in processing JS programs is much more alike compilation than not.

Classifying JS as a compiled language is not concerned with the distribution model for its binary (or byte-code) executable representations, but rather in keeping a clear distinction in our minds about the phase where JS code is processed and analyzed; this phase observably and indisputedly happens before the code starts to be executed.

### Compiler Speak

Let’s examine a simple JS program to use for analysis over the next several chapters:

```js
var students = [
    { id: 14, name: "Kyle" },
    { id: 73, name: "Suzy" },
    { id: 112, name: "Frank" },
    { id: 6, name: "Sarah" }
];

function getStudentName(studentID) {
    for (let student of students) {
        if (student.id == studentID) {
            return student.name;
        }
    }
}

var nextStudent = getStudentName(73);

console.log(nextStudent);
// Suzy
```

Other than declarations, all occurrences of variables/identifiers in a program serve in one of two “roles”: either they’re the target of an assignment or they’re the source of a value... ...How do you know if a variable is a target? Check if there is a value that is being assigned to it; if so, it’s a target. If not, then the variable is a source. For the JS engine to properly handle a program’s variables, it must first label each occurrence of a variable as target or source.

#### Targets

Target assignment operations in the code:

```js
for (let student of students) {
```

That statement assigns a value to `student` for each iteration of the loop. Another target reference:

```js
getStudentName(73)
```

But how is that an assignment to a target? Look closely: the argument `73` is assigned to the parameter `studentID`.

```js
function getStudentName(studentID) {
```

A `function` declaration is a special case of a target reference. You can think of it sort of like `var getStudentName = function(studentID)`, but that’s not exactly accurate. An identifier `getStudentName` is declared (at compile time), but the `= function(studentID)` part is also handled at compilation; the association between `getStudentName` and the function is automatically set up at the beginning of the scope rather than waiting for an `=` assignment statement to be executed... ...NOTE: This automatic association of function and variable is referred to as “function hoisting”,

#### Sources

`students` is a source reference. In the statement `if (student.id == studentID)`, both `student` and `studentID` are source references. `student` is also a source reference in `return student.name`.

In `getStudentName(73)`, `getStudentName` is a source reference (which we hope resolves to a function reference value). In `console.log(nextStudent)`, `console` is a source reference, as is `nextStudent`.

What’s the practical importance of understanding targets vs. sources? In Chapter 2, we’ll revisit this topic and cover how a variable’s role impacts its lookup (specifically, if the lookup fails).

### Cheating: Run-Time Scope Modifications

In non-strict-mode, there are technically still two ways to cheat this rule, modifying a program’s scopes during runtime. Neither of these techniques should be used... ...The `eval(..)` function receives a string of code to compile and execute on the fly during the program runtime. If that string of code has a `var` or `function` declaration in it, those declarations will modify the current scope that the `eval(..)` is currently executing in:

```js
function badIdea() {
    eval("var oops = 'Ugh!';");
    console.log(oops);
}
badIdea();   // Ugh!
```
If the `eval(..)` had not been present, the `oops` variable in `console.log(oops)` would not exist, and would throw a `ReferenceError`. But `eval(..)` modifies the scope of the `badIdea()` function at runtime. This is bad for many reasons, including the performance hit of modifying the already compiled and optimized scope, every time `badIdea()` runs.

The second cheat is the `with` keyword, which essentially dynamically turns an object into a local scope—its properties are treated as identifiers in that new scope’s block:

```js
var badIdea = { oops: "Ugh!" };

with (badIdea) {
    console.log(oops);   // Ugh!
}
```

The global scope was not modified here, but `badIdea` was turned into a scope at runtime rather than compile time, and its property `oops` becomes a variable in that scope. Again, this is a terrible idea, for performance and readability reasons.

#### Lexical Scope

JS’s scope is determined at compile time; the term for this kind of scope is “lexical scope”. “Lexical” is associated with the “lexing” stage of compilation, as discussed earlier in this chapter. To narrow this chapter down to a useful conclusion, the key idea of “lexical scope” is that it’s controlled entirely by the placement of functions, blocks, and variable declarations, in relation to one another.

A reference (target or source role) for a variable must be resolved as coming from one of the scopes that are lexically available to it; otherwise the variable is said to be “undeclared” (which usually results in an error!).

It’s important to note that compilation doesn’t actually do anything in terms of reserving memory for scopes and variables. None of the program has been executed yet.

While scopes are identified during compilation, they’re not actually created until runtime, each time a scope needs to run.




















    
    
    
    - 
    - 
    - 
- Chapter 2: Illustrating Lexical Scope
    - Marbles, and Buckets, and Bubbles... Oh My!
    - A Conversation Among Friends
    - Nested Scope
    - Continue the Conversation
- Chapter 3: The Scope Chain
    - "Lookup" Is (Mostly) Conceptual
    - Shadowing
    - Function Name Scope
    - Arrow Functions
    - Backing Out
- Chapter 4: Around the Global Scope
    - Why Global Scope?
    - Where Exactly is this Global Scope?
    - Global This
    - Globally Aware
- Chapter 5: The (Not So) Secret Lifecycle of Variables
    - When Can I Use a Variable?
    - Hoisting: Yet Another Metaphor
    - Re-declaration?
    - Uninitialized Variables (aka, TDZ)
    - Finally Initialized
- Chapter 6: Limiting Scope Exposure
    - Least Exposure
    - Hiding in Plain (Function) Scope
    - Scoping with Blocks
    - Function Declarations in Blocks
    - Blocked Over
- Chapter 7: Using Closures
    - See the Closure
    - The Closure Lifecycle and Garbage Collection (GC)
    - Why Closure?
    - An Alternative Perspective
    - Closer to Closure
- Chapter 8: The Module Pattern
    - Encapsulation and Least Exposure (POLE)
    - What is a Module?
    - Node CommonJS Modules
    - Modern ES Modules (ESM)
    - Exit Scope
- Appendix A: Exploring Further
    - Implied Scopes
    - Anonymous vs. Named Functions
    - Hoisting: Functions and Variables
    - The Case for `var`
    - What's the Deal with TDZ?
    - Are Synchronous Callbacks Still Closures?
    - Classic Module Variations
- Appendix B: Practice
    - Buckets of Marbles
    - Closure (PART 1)
    - Closure (PART 2)
    - Closure (PART 3)
    - Modules
    - Suggested Solutions

