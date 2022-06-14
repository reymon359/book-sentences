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

## Chapter 2: Illustrating Lexical Scope

To properly reason about our programs, it’s important to have a solid conceptual foundation of how scope works. If we rely on guesses and intuition, we may accidentally get the right answers some of the time, but many other times we’re far off. This isn’t a recipe for success.

We need to build accurate and helpful mental models as foundation moving forward.

### Marbles, and Buckets, and Bubbles... Oh My!

One metaphor I’ve found effective in understanding scope is sorting colored marbles into buckets of their matching color. Imagine you come across a pile of marbles, and notice that all the marbles are colored red, blue, or green. Let’s sort all the marbles, dropping the red ones into a red bucket, green into a green bucket, and blue into a blue bucket. After sorting, when you later need a green marble, you already know the green bucket is where to go to get it. In this metaphor, the marbles are the variables in our program. The buckets are scopes (functions and blocks), which we just conceptually assign individual colors for our discussion purposes. The color of each marble is thus determined by which color scope we find the marble originally created in.

```js
// outer/global scope: RED

var students = [
    { id: 14, name: "Kyle" },
    { id: 73, name: "Suzy" },
    { id: 112, name: "Frank" },
    { id: 6, name: "Sarah" }
];

function getStudentName(studentID) {
    // function scope: BLUE

    for (let student of students) {
        // loop scope: GREEN

        if (student.id == studentID) {
            return student.name;
        }
    }
}

var nextStudent = getStudentName(73);
console.log(nextStudent);   // Suzy
```

![Fig. 2: Colored Scope Bubbles](./assets/figure2.png)

Bubble 1 (RED) encompasses the global scope, which holds three identifiers/variables: `students` (line 1), `getStudentName` (line 8), and `nextStudent` (line 16).

Bubble 2 (BLUE) encompasses the scope of the function `getStudentName(..)` (line 8), which holds just one identifier/variable: the parameter `studentID` (line 8).

Bubble 3 (GREEN) encompasses the scope of the `for`-loop (line 9), which holds just one identifier/variable: `student` (line 9).

Scope bubbles are determined during compilation based on where the functions/blocks of scope are written, the nesting inside each other, and so on. Each scope bubble is entirely contained within its parent scope bubble—a scope is never partially in two different outer scopes.

As the JS engine processes a program (during compilation), and finds a declaration for a variable, it essentially asks, “Which color scope (bubble or bucket) am I currently in?” The variable is designated as that same color, meaning it belongs to that bucket/bubble.

References (non-declarations) to variables/identifiers are allowed if there’s a matching declaration either in the current scope, or any scope above/outside the current scope, but not with declarations from lower/nested scopes.

The JS engine doesn’t generally determine these marble colors during runtime; the “lookup” here is a rhetorical device to help you understand the concepts. During compilation, most or all variable references will match already-known scope buckets, so their color is already determined, and stored with each marble reference to avoid unnecessary lookups as the program runs. More on this nuance in Chapter 3.

The key take-aways from marbles & buckets (and bubbles!):
- Variables are declared in specific scopes, which can be thought of as colored marbles from matching-color buckets.
- Any variable reference that appears in the scope where it was declared, or appears in any deeper nested scopes, will be labeled a marble of that same color—unless an intervening scope “shadows” the variable declaration; see “Shadowing” in Chapter 3.
- The determination of colored buckets, and the marbles they contain, happens during compilation. This information is used for variable (marble color) “lookups” during code execution.

### A Conversation Among Friends

- Let’s now meet the members of the JS engine that will have conversations as they process our program:
- Engine: responsible for start-to-finish compilation and execution of our JavaScript program.
- Compiler: one of Engine’s friends; handles all the dirty work of parsing and code-generation (see previous section).
- Scope Manager: another friend of Engine; collects and maintains a lookup list of all the declared variables/identifiers, and enforces a set of rules as to how these are accessible to currently executing code.

For you to fully understand how JavaScript works, you need to begin to think like Engine (and friends) think, ask the questions they ask, and answer their questions likewise.

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

Let’s examine how JS is going to process that program, specifically starting with the first statement... ...JS treats these as two distinct operations, one which Compiler will handle during compilation, and the other which Engine will handle during execution... ...Here’s the steps Compiler will follow to handle that statement: 
1. Encountering `var students`, Compiler will ask Scope Manager to see if a variable named `students` already exists for that particular scope bucket. If so, Compiler would ignore this declaration and move on. Otherwise, Compiler will produce code that (at execution time) asks Scope Manager to create a new variable called `students` in that scope bucket.
2. Compiler then produces code for Engine to later execute, to handle the `students = []` assignment. The code Engine runs will first ask Scope Manager if there is a variable called `students` accessible in the current scope bucket. If not, Engine keeps looking elsewhere (see “Nested Scope” below). Once Engine finds a variable, it assigns the reference of the `[ .. ]` array to it.

The conversation is a question-and-answer exchange, where Compiler asks the current Scope Manager if an encountered identifier declaration has already been encountered. If “no,” Scope Manager creates that variable in that scope. If the answer is “yes,” then it’s effectively skipped over since there’s nothing more for that Scope Manager to do. Compiler also signals when it runs across functions or block scopes, so that a new scope bucket and Scope Manager can be instantiated.

This conversation is another question-and-answer exchange, where Engine first asks the current Scope Manager to look up the hoisted `getStudentName` identifier, so as to associate the function with it. Engine then proceeds to ask Scope Manager about the target reference for `students`, and so on.

To review and summarize how a statement like `var students = [ .. ]` is processed, in two distinct steps:
1. Compiler sets up the declaration of the scope variable (since it wasn’t previously declared in the current scope).
2. While Engine is executing, to process the assignment part of the statement, Engine asks Scope Manager to look up the  variable, initializes it to `undefined` so it’s ready to use, and then assigns the array value to it.

### Nested Scope

Scopes can be lexically nested to any arbitrary depth as the program defines.

Each scope gets its own Scope Manager instance each time that scope is executed (one or more times). Each scope automatically has all its identifiers registered at the start of the scope being executed (this is called “variable hoisting”

If any identifier came from a `var` declaration (as opposed to `let/const`), that variable is automatically initialized to `undefined` so that it can be used; otherwise, the variable remains uninitialized (aka, in its “TDZ,” see Chapter 5) and cannot be used until its full declaration-and-initialization are executed.

In the `for (let student of students)` { statement, `students` is a source reference that must be looked up. But how will that lookup be handled, since the scope of the function will not find such an identifier? To explain, let’s imagine that bit of conversation playing out like this:
- Engine: Hey, Scope Manager (for the function), I have a source reference for `students`, ever heard of it?
- (Function) Scope Manager: Nope, never heard of it. Try the next outer scope.
- Engine: Hey, Scope Manager (for the global scope), I have a source reference for `students`, ever heard of it?
- (Global) Scope Manager: Yep, it was formally declared, here it is.

One of the key aspects of lexical scope is that any time an identifier reference cannot be found in the current scope, the next outer scope in the nesting is consulted; that process is repeated until an answer is found or there are no more scopes to consult.

#### Lookup Failures

When Engine exhausts all lexically available scopes (moving outward) and still cannot resolve the lookup of an identifier, an error condition then exists.

If the variable is a source, an unresolved identifier lookup is considered an undeclared (unknown, missing) variable, which always results in a `ReferenceError` being thrown. Also, if the variable is a target, and the code at that moment is running in strict-mode, the variable is considered undeclared and similarly throws a `ReferenceError.`

The error message for an undeclared variable condition, in most JS environments, will look like, “Reference Error: XYZ is not defined.” The phrase “not defined” seems almost identical to the word “undefined,” as far as the English language goes. But these two are very different in JS, and this error message unfortunately creates a persistent confusion. “Not defined” really means “not declared”—or, rather, “undeclared,” as in a variable that has no matching formal declaration in any lexically available scope. By contrast, “undefined” really means a variable was found (declared), but the variable otherwise has no other value in it at the moment, so it defaults to the `undefined` value.

```js
var studentName;
typeof studentName;     // "undefined"
typeof doesntExist;     // "undefined"
```
These two variable references are in very different conditions, but JS sure does muddy the waters.

Never rely on accidental global variables. Always use strict-mode, and always formally declare your variables. You’ll then get a helpful `ReferenceError` if you ever mistakenly try to assign to a not-declared variable.

#### Building On Metaphors

![Fig. 3: Scope “Building”](./assets/figure3.png)

You resolve a target or source variable reference by first looking on the current floor, and if you don’t find it, taking the elevator to the next floor (i.e., an outer scope), looking there, then the next, and so on. Once you get to the top floor (the global scope), you either find what you’re looking for, or you don’t. But you have to stop regardless.

### Continue the Conversation

## Chapter 3: The Scope Chain
  
It really does help to take the time to reformulate these ideas as explanations to others. That helps our brains digest what we’re learning!


![Fig. 2 (Ch. 2): Colored Scope Bubbles](./assets/figure2.png)

The connections between scopes that are nested within other scopes is called the scope chain, which determines the path along which variables can be accessed. The chain is directed, meaning the lookup moves upward/outward only.

### "Lookup" Is (Mostly) Conceptual

Since the marble’s color is known from compilation, and it’s immutable, this information would likely be stored with (or at least accessible from) each variable’s entry in the AST; that information is then used explicitly by the executable instructions that constitute the program’s runtime. In other words, Engine (from Chapter 2) doesn’t need to lookup through a bunch of scopes to figure out which scope bucket a variable comes from. That information is already known! Avoiding the need for a runtime lookup is a key optimization benefit of lexical scope.

In what case would it ever not be known during compilation? Consider a reference to a variable that isn’t declared in any lexically available scopes in the current file—see Get Started, Chapter 1, which asserts that each file is its own separate program from the perspective of JS compilation. If no declaration is found, that’s not necessarily an error. Another file (program) in the runtime may indeed declare that variable in the shared global scope. So the ultimate determination of whether the variable was ever appropriately declared in some accessible bucket may need to be deferred to the runtime.

Any reference to a variable that’s initially undeclared is left as an uncolored marble during that file’s compilation; this color cannot be determined until other relevant file(s) have been compiled and the application runtime commences. That deferred lookup will eventually resolve the color to whichever scope the variable is found in (likely the global scope).

### Shadowing

if you need to maintain two or more variables of the same name, you must use separate (often nested) scopes. And in that case, it’s very relevant how the different scope buckets are laid out.

```js
var studentName = "Suzy";

function printStudent(studentName) {
    studentName = studentName.toUpperCase();
    console.log(studentName);
}
printStudent("Frank");
// FRANK

printStudent(studentName);
// SUZY

console.log(studentName);
// Suzy
```

The `studentName` variable on line 1 (the var `studentName =` .. statement) creates a RED(1) marble. The same named variable is declared as a BLUE(2) marble on line 3, the parameter in the `printStudent(..)` function definition. What color marble will `studentName` be in the `studentName = studentName.toUpperCase()` assignment statement and the `console.log(studentName)` statement? All three `studentName` references will be BLUE(2).

The BLUE(2) `studentName` variable (parameter) shadows the RED(1) `studentName`. So, the parameter is shadowing the (shadowed) global variable... ...any `studentName` identifier reference will correspond to that parameter variable, never the global `studentName` variable. It’s lexically impossible to reference the global `studentName` anywhere inside of the `printStudent(..)` function (or from any nested scopes).

#### Global Unshadowing Trick

```js
var studentName = "Suzy";

function printStudent(studentName) {
    console.log(studentName);
    console.log(window.studentName);
}

printStudent("Frank");
// "Frank"
// "Suzy"
```

Notice the `window.studentNam`e reference? This expression is accessing the global variable `studentName` as a property on `window` (which we’re pretending for now is synonymous with the global object). That’s the only way to access a shadowed variable from inside a scope where the shadowing variable is present.

Remember: just because you can doesn’t mean you should.

Don’t shadow a global variable that you need to access, and conversely, avoid using this trick to access a global variable that you’ve shadowed. 

Don’t confuse readers of your code by creating global variables as `window` properties instead of with formal declarations!

This little “trick” only works for accessing a global scope variable (not a shadowed variable from a nested scope), and even then, only one that was declared with `var` or `function`. Other forms of global scope declarations do not create mirrored global object properties:
```js
var one = 1;
let notOne = 2;
const notTwo = 3;
class notThree {}

console.log(window.one);       // 1
console.log(window.notOne);    // undefined
console.log(window.notTwo);    // undefined
console.log(window.notThree);  // undefined
```

Variables (no matter how they’re declared!) that exist in any other scope than the global scope are completely inaccessible from a scope where they’ve been shadowed:

```js
var special = 42;

function lookingFor(special) {
    // The identifier `special` (parameter) in this
    // scope is shadowed inside keepLooking(), and
    // is thus inaccessible from that scope.

    function keepLooking() {
        var special = 3.141592;
        console.log(special);
        console.log(window.special);
    }

    keepLooking();
}

lookingFor(112358132134);
// 3.141592
// 42
```

#### Copying Is Not Accessing

```js
var special = 42;

function lookingFor(special) {
    var another = {
        special: special
    };

    function keepLooking() {
        var special = 3.141592;
        console.log(special);
        console.log(another.special);  // Ooo, tricky!
        console.log(window.special);
    }

 
    keepLooking();
}

lookingFor(112358132134);
// 3.141592
// 112358132134
// 42
```

`special: special` is copying the value of the `special` parameter variable into another container (a property of the same name). Of course, if you put a value in another container, shadowing no longer applies (unless `another` was shadowed, too!). But that doesn’t mean we’re accessing the parameter `special`; it means we’re accessing the copy of the value it had at that moment, by way of another container (object property). We cannot reassign the BLUE(2) `special` parameter to a different value from inside `keepLooking()`.

what if I’d used objects or arrays as the values instead of the numbers (`112358132134`, etc.)? Would us having references to objects instead of copies of primitive values “fix” the inaccessibility? No. Mutating the contents of the object value via a reference copy is not the same thing as lexically accessing the variable itself. We still can’t reassign the BLUE(2) `special` parameter.

#### Illegal Shadowing

`let` can shadow `var`, but `var` cannot shadow `let`... ...`let` (in an inner scope) can always shadow an outer scope’s `var`. `var` (in an inner scope) can only shadow an outer scope’s `let` if there is a function boundary in between.


### Function Name Scope

A `function` expression with a name identifier is referred to as a “named function expression,” but one without a name identifier is referred to as an “anonymous function expression.” Anonymous function expressions clearly have no name identifier that affects either scope.

### Arrow Functions

Arrow functions are lexically anonymous, meaning they have no directly related identifier that references the function. The assignment to `askQuestion` creates an inferred name of “askQuestion”, but that’s not the same thing as being non-anonymous:

```js
var askQuestion = () => {
    // ..
};

askQuestion.name;   // askQuestion
```

Arrow functions somehow behave differently with respect to lexical scope from standard function functions. This is incorrect. Other than being anonymous (and having no declarative form), => arrow functions have the same lexical scope rules as function functions do. An arrow function, with or without { .. } around its body, still creates a separate, inner nested bucket of scope. Variable declarations inside this nested scope bucket behave the same as in a function scope.

### Backing Out

## Chapter 4: Around the Global Scope

This chapter first explores how the global scope is (still) useful and relevant to writing JS programs today, then looks at differences in where and how to access the global scope in different JS environments. Fully understanding the global scope is critical in your mastery of using lexical scope to structure your programs.

### Why Global Scope?

How exactly do all those separate files get stitched together in a single runtime context by the JS engine? With respect to browser-executed applications, there are three main ways. First, if you’re directly using ES modules (not transpiling them into some other module-bundle format), these files are loaded individually by the JS environment. Each module then `imports` references to whichever other modules it needs to access. The separate module files cooperate with each other exclusively through these shared imports, without needing any shared outer scope. Second, if you’re using a bundler in your build process, all the files are typically concatenated together before delivery to the browser and JS engine, which then only processes one big file. Even with all the pieces of the application co-located in a single file, some mechanism is necessary for each piece to register a name to be referred to by other pieces, as well as some facility for that access to occur.

And finally, the third way: whether a bundler tool is used for an application, or whether the (non-ES module) files are simply loaded in the browser individually (via `<script>` tags or other dynamic JS resource loading), if there is no single surrounding scope encompassing all these pieces, the global scope is the only way for them to cooperate with each other:

In addition to (potentially) accounting for where an application’s code resides during runtime, and how each piece is able to access the other pieces to cooperate, the global scope is also where: 

- JS exposes its built-ins: 
    - primitives: `undefined`, `null`, `Infinity`, `NaN`
    - natives: `Date()`, `Object()`, `String()`, etc.
    - global functions: `eval()`, `parseInt()`, etc. 
    - namespaces: `Math`, `Atomics`, `JSON` 
    - friends of JS: `Intl`, `WebAssembly`

- The environment hosting the JS engine exposes its own built-ins:
    - `console` (and its methods) 
    - the DOM (`window`, `document`, etc)
    - timers (`setTimeout(..)`, etc) 
    - web platform APIs: `navigator`, `history`, geolocation, WebRTC, etc.

These are just some of the many globals your programs will interact with.

Node also exposes several elements “globally,” but they’re technically not in the `global` scope: `require()`, `__dirname`, `module`, `URL`, and so on.

the global scope is an important glue for practically every JS application.

### Where Exactly is this Global Scope?

#### Browser “Window”

With respect to treatment of the global scope, the most pure environment JS can be run in is as a standalone .js file loaded in a web page environment in a browser. Consider this .js file:

```js
var studentName = "Kyle";

function hello() {
    console.log(`Hello, ${ studentName }!`);
}

hello();
// Hello, Kyle!
```

If you access the global object (commonly, window in the browser), you’ll find properties of those same names there: 

```js
var studentName = "Kyle";

function hello() {
    console.log(`Hello, ${ window.studentName }!`);
}

window.hello();
// Hello, Kyle!
```

That’s the default behavior one would expect from a reading of the JS specification: the outer scope is the global scope and `studentName` is legitimately created as global variable. That’s what I mean by pure. But unfortunately, that won’t always be true of all JS environments you encounter, and that’s often surprising to JS developers.

#### Globals Shadowing Globals

```js
window.something = 42;

let something = "Kyle";

console.log(something);
// Kyle

console.log(window.something);
// 42
```

The `let` declaration adds a `something` global variable but not a global object property (see Chapter 3). The effect then is that the `something` lexical identifier shadows the `something` global object property.

Always use `var` for globals. Reserve `let` and `const` for block scopes.

a DOM element with an `id` attribute automatically creates a global variable that references it. Consider this markup:

```html
<ul id="my-todo-list">
   <li id="first">Write a book</li>
   ..
</ul>
```

And the JS for that page could include:

```html
first;
// <li id="first">..</li>

window["my-todo-list"];
// <ul id="my-todo-list">..</ul>
```

If the id value is a valid lexical name (like `first`), the lexical variable is created. If not, the only way to access that global is through the global object (`window[..]`)... ...never to use these global variables, even though they will always be silently created.

#### What’s in a (Window) Name?

Another global scope oddity in browser-based JS:

```js
var name = 42;

console.log(name, typeof name);
// "42" string
```

`window.name` is a pre-defined “global” in a browser context;... ...We used `var` for our declaration, which does not shadow the pre-defined `name` global property. That means, effectively, the `var` declaration is ignored, since there’s already a global scope object property of that name... ...But the truly surprising behavior is that even though we assigned the number `42` to `name` (and thus `window.name`), when we then retrieve its value, it’s a string `"42"`! In this case, the weirdness is because `name` is actually a pre-defined getter/setter on the `window` object, which insists on its value being a string value. Yikes!

With the exception of some rare corner cases like DOM element ID’s and `window.name`, JS running as a standalone file in a browser page has some of the most pure global scope behavior we will encounter.

#### Web Workers

Web Workers are a web platform extension on top of browser-JS behavior, which allows a JS file to run in a completely separate thread (operating system wise) from the thread that’s running the main JS program.

Since these Web Worker programs run on a separate thread, they’re restricted in their communications with the main application thread, to avoid/limit race conditions and other complications. 

Web Worker code does not have access to the DOM, for example. Some web APIs are, however, made available to the worker, such as `navigator`.

Since there is no DOM access, the `window` alias for the global scope doesn’t exist.

In a Web Worker, the global object reference is typically made using `self`:

The global scope behavior we’re seeing here is about as pure as it gets for running JS programs; perhaps it’s even more pure since there’s no DOM to muck things up!

#### Developer Tools

Developer Tools don’t create a completely adherent JS environment. They do process JS code, but they also lean in favor of the UX interaction being most friendly to developers (aka, developer experience, or DX).

Certain error conditions applicable to a JS program may be relaxed and not displayed when the code is entered into a developer tool.

The take-away is that Developer Tools, while optimized to be convenient and useful for a variety of developer activities, are not suitable environments to determine or verify explicit and nuanced behaviors of an actual JS program context.

#### ES Modules (ESM)

```js
var studentName = "Kyle";

function hello() {
    console.log(`Hello, ${ studentName }!`);
}

hello();
// Hello, Kyle!

export hello;
```

If that code is in a file that’s loaded as an ES module, it will still run exactly the same. However, the observable effects, from the overall application perspective, will be different. Despite being declared at the top level of the (module) file, in the outermost obvious scope, `studentName` and `hello` are not global variables. Instead, they are module-wide, or if you prefer, “module-global.” However, in a module there’s no implicit “module-wide scope object” for these top-level declarations to be added to as properties, as there is when declarations appear in the top-level of non-module JS files. This is not to say that global variables cannot exist or be accessed in such programs. It’s just that global variables don’t get created by declaring variables in the top-level scope of a module.

All variables that exist in the global scope (whether they’re on the global object or not!) are available as lexical identifiers from inside the module’s scope.

ESM encourages a minimization of reliance on the global scope... ...However, as noted earlier, there are still plenty of JS and web globals that you will continue to access from the global scope, whether you realize it or not!

### Node

The top level of your Node programs is never actually the global scope, the way it is when loading a non-module file in the browser. As of time of this writing, Node has recently added support for ES modules. But additionally, Node has from its beginning supported a module format referred to as “CommonJS”, which looks like this:

```js
var studentName = "Kyle";

function hello() {
    console.log(`Hello, ${ studentName }!`);
}

hello();
// Hello, Kyle!

module.exports.hello = hello;
```
Before processing, Node effectively wraps such code in a function, so that the `var` and `function` declarations are contained in that wrapping function’s scope, not treated as global variables.

Node defines a number of “globals” like `require()`, but they’re not actually identifiers in the global scope (nor properties of the global object). They’re injected in the scope of every module, essentially a bit like the parameters listed in the `Module(..)` function declaration.

How do you define actual global variables in Node? The only way to do so is to add properties to another of Node’s automatically provided “globals,” which is ironically called `global`. `global` is a reference to the real global scope object, somewhat like using `window` in a browser JS environment.

Consider:

```js
global.studentName = "Kyle";

function hello() {
    console.log(`Hello, ${ studentName }!`);
}

hello();
// Hello, Kyle!

module.exports.hello = hello;
```

### Global This

Reviewing the JS environments we’ve looked at so far, a program may or may not:

- Declare a global variable in the top-level scope with `var` or `function` declarations—or `let`, `const`, and `class`.
- Also add global variables declarations as properties of the global scope object if `var` or `function` are used for the declaration.
- Refer to the global scope object (for adding or retrieving global variables, as properties) with `window`, `self`, or `global`.

“trick” for obtaining a reference to the global scope object looks like:

```js
const theGlobalScopeObject =
    (new Function("return this"))();
```

As of ES2020, JS has finally defined a standardized reference to the global scope object, called `globalThis`. So, subject to the recency of the JS engines your code runs in, you can use `globalThis` in place of any of those other approaches.

A better name... ...laughably long but accurate!

### Globally Aware

It’s especially important we have a solid grasp on the differences in how the global scope (and global scope object!) behave across different JS environments.

## Chapter 5: The (Not So) Secret Lifecycle of Variables

JS’s particular flavor of lexical scope is rich with nuance in how and when variables come into existence and become available to the program.

### When Can I Use a Variable?

```js
greeting();
// Hello!

function greeting() {
    console.log("Hello!");
}
```

all identifiers are registered to their respective scopes during compile time. Moreover, every identifier is created at the beginning of the scope it belongs to, every time that scope is entered.

a variable being visible from the beginning of its enclosing scope, even though its declaration may appear further down in the scope, is called hoisting.

_function hoisting_. When a `function` declaration’s name identifier is registered at the top of its scope, it’s additionally auto-initialized to that function’s reference. That’s why the function can be called throughout the entire scope!... ...function hoisting and `var`-flavored variable hoisting attach their name identifiers to the nearest enclosing function scope (or, if none, the global scope), not a block scope.

#### Hoisting: Declaration vs. Expression

```js
greeting();
// TypeError

var greeting = function greeting() {
    console.log("Hello!");
};
```

Line 1 (`greeting();`) throws an error. But the kind of error thrown is very important to notice. A `TypeError` means we’re trying to do something with a value that is not allowed. Depending on your JS environment, the error message would say something like, “‘undefined’ is not a function,” or more helpfully, “‘greeting’ is not a function.”... ...`greeting` was found but doesn’t hold a function reference at that moment. 

Only functions can be invoked, so attempting to invoke some non-function value results in an error.

on that first line, `greeting` exists, but it holds only the default `undefined` value. It’s not until line 4 that `greeting` gets assigned the function reference.

Pay close attention to the distinction here. A `function` declaration is hoisted and initialized to its function value (again, called function hoisting). A `var` variable is also hoisted, and then auto-initialized to `undefined`. Any subsequent `function` expression assignments to that variable don’t happen until that assignment is processed during runtime execution.

### Hoisting: Yet Another Metaphor

Rather than hoisting being a concrete execution step the JS engine performs, it’s more useful to think of hoisting as a visualization of various actions JS takes in setting up the program before execution.

```js
studentName = "Suzy";
greeting();
// Hello Suzy!

function greeting() {
    console.log(`Hello ${ studentName }!`);
}
var studentName;
```

The “rule” of the hoisting metaphor is that function declarations are hoisted first, then variables are hoisted immediately after all the functions. Thus, the hoisting story suggests that program is re-arranged by the JS engine to look like this:

```js
function greeting() {
    console.log(`Hello ${ studentName }!`);
}
var studentName;

studentName = "Suzy";
greeting();
// Hello Suzy!
```

If the hoisting metaphor is (at best) inaccurate, what should we do with the term? I think it’s still useful—indeed, even members of TC39 regularly use it!—but I don’t think we should claim it’s an actual re-arrangement of source code.

Hoisting should be used to refer to the compile-time operation of generating runtime instructions for the automatic registration of a variable at the beginning of its scope, each time that scope is entered. That’s a subtle but important shift, from hoisting as a runtime behavior to its proper place among compile-time tasks.

### Re-declaration?

```js
var studentName = "Frank";
console.log(studentName);
// Frank

var studentName;
console.log(studentName);   // ???
```

If you consider this program from the perspective of the hoisting metaphor, the code would be re-arranged like this for execution purposes:

```js
var studentName;
var studentName;    // clearly a pointless no-op!

studentName = "Frank";
console.log(studentName);
// Frank

console.log(studentName);
 
// Frank
```

```js
var greeting;

function greeting() {
    console.log("Hello!");
}

// basically, a no-op
var greeting;

typeof greeting;        // "function"

var greeting = "Hello!";

typeof greeting;        // "string"
```

The first `greeting` declaration registers the identifier to the scope, and because it’s a `var` the auto-initialization will be `undefined`. The `function` declaration doesn’t need to re-register the identifier, but because of function hoisting it overrides the auto-initialization to use the function reference. The second `var` `greeting` by itself doesn’t do anything since `greeting` is already an identifier and function hoisting already took precedence for the auto-initialization.

```js
let studentName = "Frank";

console.log(studentName);

let studentName = "Suzy";
```

This program will not execute, but instead immediately throw a `SyntaxError`. Depending on your JS environment, the error message will indicate something like: “studentName has already been declared.” In other words, this is a case where attempted “re-declaration” is explicitly not allowed!
It’s not just that two declarations involving `let` will throw this error. If either declaration uses `let`, the other can be either `let` or `var`, and the error will still occur, as illustrated with these two variations:

```js
var studentName = "Frank";

let studentName = "Suzy";
```
and:

```js
let studentName = "Frank";

var studentName = "Suzy";
```

In both cases, a `SyntaxError` is thrown on the second declaration. In other words, the only way to “re-declare” a variable is to use `var` for all (two or more) of its declarations.

“Re-declaration” of variables is seen by some, including many on the TC39 body, as a bad habit that can lead to program bugs. So when ES6 introduced `let`, they decided to prevent “re-declaration” with an error.

#### Constants?

`const` declarations create variables that cannot be re-assigned:

```js
const studentName = "Frank";
console.log(studentName);
// Frank

studentName = "Suzy";   // TypeError
```

The `studentName` variable cannot be re-assigned because it’s declared with a `const`.

Syntax errors represent faults in the program that stop it from even starting execution. Type errors represent faults that arise during program execution. In the preceding snippet, `"Frank"` is printed out before we process the re-assignment of `studentName`, which then throws the error.

#### Loops

```js
var keepGoing = true;
while (keepGoing) {
    let value = Math.random();
    if (value > 0.5) {
        keepGoing = false;
    }
}
```

Is `value` being “re-declared” repeatedly in this program? Will we get errors thrown? No. All the rules of scope (including “re-declaration” of `let`-created variables) are applied per scope instance. In other words, each time a scope is entered during execution, everything resets. Each loop iteration is its own new scope instance, and within each scope instance, value is only being declared once. 

One way to keep this all straight is to remember that `var`, `let`, and `const` keywords are effectively removed from the code by the time it starts to execute. They’re handled entirely by the compiler. If you mentally erase the declarator keywords and then try to process the code, it should help you decide if and when (re-)declarations might occur.

```js
for (const i = 0; i < 3; i++) {
    // oops, this is going to fail with
    // a Type Error after the first iteration
}
```

What’s wrong here? We could use `let` just fine in this construct, and we asserted that it creates a new `i` for each loop iteration scope, so it doesn’t even seem to be a “re-declaration.” Let’s mentally “expand” that loop like we did earlier:

```js
{
    // a fictional variable for illustration
    const $$i = 0;

    for ( ; $$i < 3; $$i++) {
        // here's our actual loop `i`!
        const i = $$i;
        // ..
    }
}
```

Do you spot the problem? Our `i` is indeed just created once inside the loop. That’s not the problem. The problem is the conceptual `$$i` that must be incremented each time with the `$$i++` expression. That’s re-assignment (not “re-declaration”), which isn’t allowed for constants.

`const` can’t be used with the classic `for`-loop form because of the required re-assignment.

### Uninitialized Variables (aka, TDZ)

With `var` declarations, the variable is “hoisted” to the top of its scope. But it’s also automatically initialized to the `undefined` value, so that the variable can be used throughout the entire scope. However, `let` and `const` declarations are not quite the same in this respect.

```js
console.log(studentName);
 
// ReferenceError

let studentName = "Suzy";
```

The result of this program is that a `ReferenceError` is thrown on the first line. Depending on your JS environment, the error message may say something like: “Cannot access studentName before initialization.”


```js
// ..

let studentName;

// or:
// let studentName = undefined;

// ..

studentName = "Suzy";

console.log(studentName);
// Suzy
```

we said that var `studentName`; is not the same as `var studentName = undefined;`, but here with `let`, they behave the same. The difference comes down to the fact that `var studentName` automatically initializes at the top of the scope, where `let studentName` does not.

Period of time from the entering of a scope to where the auto-initialization of the variable occurs is: Temporal Dead Zone (TDZ). The TDZ is the time window where a variable exists but is still uninitialized, and therefore cannot be accessed in any way. 

A `var` also has technically has a TDZ, but it’s zero in length and thus unobservable to our programs! Only `let` and `const` have an observable TDZ.

“temporal” in TDZ does indeed refer to time not position in code. 

There’s a common misconception that TDZ means `let` and `const` do not hoist. This is an inaccurate, or at least slightly misleading, claim. They definitely hoist. The actual difference is that `let/const` declarations do not automatically initialize at the beginning of the scope, the way `var` does. The debate then is if the auto-initialization is part of hoisting, or not? I think auto-registration of a variable at the top of the scope (i.e., what I call “hoisting”) and auto-initialization at the top of the scope (to `undefined`) are distinct operations and shouldn’t be lumped together under the single term “hoisting.”

TDZ errors occur because `let/const` declarations do hoist their declarations to the top of their scopes, but unlike `var`, they defer the auto-initialization of their variables until the moment in the code’s sequencing where the original declaration appeared. This window of time (hint: temporal), whatever its length, is the TDZ.

Always put your let and const declarations at the top of any scope. Shrink the TDZ window to zero (or near zero) length, and then it’ll be moot.

### Finally Initialized

Declaration and re-declaration of variables tend to cause confusion when thought of as runtime operations. But if you shift to compile-time thinking for these operations, the quirks and shadows diminish.

## Chapter 6: Limiting Scope Exposure

### Least Exposure

Why do we need blocks to create scopes as well? Software engineering articulates a fundamental discipline, typically applied to software security, called “The Principle of Least Privilege” (POLP). 1 And a variation of this principle that applies to our current discussion is typically labeled as “Least Exposure” (POLE). POLP expresses a defensive posture to software architecture: components of the system should be designed to function with least privilege, least access, least exposure. If each piece is connected with minimum-necessary capabilities, the overall system is stronger from a security standpoint, because a compromise or failure of one piece has a minimized impact on the rest of the system.

The POLE Exposure variant focuses on a lower level... ...what do we want to minimize the exposure of? Simply: the variables registered in each scope.

Why shouldn’t you just place all the variables of your program out in the global scope?... ...When variables used by one part of the program are exposed to another part of the program, via scope, there are three main hazards that often arise:

- Naming Collisions: if you use a common and useful variable/function name in two different parts of the program, but the identifier comes from one shared scope (like the global scope), then name collision occurs, 
- Unexpected Behavior: if you expose variables/functions whose usage is otherwise private to a piece of the program, it allows other developers to use them in ways you didn’t intend, which can violate expected behavior and cause bugs... ...Worse, exposure of private details invites those with mal-intent to try to work around limitations you have imposed, to do things with your part of the software that shouldn’t be allowed.
- Unintended Dependency: if you expose variables/functions unnecessarily, it invites other developers to use and depend on those otherwise private pieces. While that doesn’t break your program today, it creates a refactoring hazard in the future, 

POLE, as applied to variable/function scoping, essentially says, default to exposing the bare minimum necessary, keeping everything else as private as possible. 

```js
function diff(x,y) {
    if (x > y) {
        let tmp = x;
        x = y;
        y = tmp;
    }

    return y - x;
}
diff(3,7);      // 4
diff(7,5);      // 2
```

In this simple example, it doesn’t seem to matter whether `tmp` is inside the `if` block or whether it belongs at the function level—it certainly shouldn’t be a global variable! However, following the POLE principle, `tmp` should be as hidden in scope as possible. So we block scope `tmp` (using `let`) to the `if` block.

### Hiding in Plain (Function) Scope

```js
var factorial = (function hideTheCache() {
    var cache = {};

    function factorial(x) {
        if (x < 2) return 1;
        if (!(x in cache)) {
            cache[x] = x * factorial(x - 1);
        }
        return cache[x];
    }

    return factorial;
})();

factorial(6);
// 720

factorial(7);
// 5040
```

Since `hideTheCache(..)` is defined as a `function` expression instead of a `function` declaration, its name is in its own scope—essentially the same scope as `cache`—rather than in the outer/global scope. That means we can name every single occurrence of such a function expression the exact same name, and never have any collision. More appropriately, we can name each occurrence semantically based on whatever it is we’re trying to hide, and not worry that whatever name we choose is going to collide with any other `function` expression scope in the program.

we surrounded the entire `function` expression in a set of `( .. )`, and then on the end, we added that second () parentheses set; that’s actually calling the `function` expression we just defined... ...Immediately Invoked Function Expression (IIFE).

always surround an IIFE `function` with `( .. )`.

a `return` statement in some piece of code would change its meaning if an IIFE is wrapped around it, because now the `return` would refer to the IIFE’s function.

if the code you need to wrap a scope around has `return`, `this`, `break`, or `continue` in it, an IIFE is probably not the best approach. In that case, you might look to create the scope with a block instead of a function.

### Scoping with Blocks

A block only becomes a scope if necessary, to contain its block-scoped declarations (i.e., `let` or `const`). Consider:

```js
{
    // not necessarily a scope (yet)

    // ..

 
    // now we know the block needs to be a scope
    let thisIsNowAScope = true;

    for (let i = 0; i < 5; i++) {
        // this is also a scope, activated each
        // iteration
        if (i % 2 == 0) {
            // this is just a block, not a scope
            console.log(i);
        }
    }
}
// 0 2 4
```

Explicit standalone `{ .. }` blocks have always been valid JS syntax, but since they couldn’t be a scope prior to ES6’s `let/const`, they are quite rare. However, post ES6, they’re starting to catch on a little bit.

In most languages that support block scoping, an explicit block scope is an extremely common pattern for creating a narrow slice of scope for one or a few variables. So following the POLE principle, we should embrace this pattern more widespread in JS as well; use (explicit) block scoping to narrow the exposure of identifiers to the minimum practical.

```js
if (somethingHappened) {
    // this is a block, but not a scope

    {
        // this is both a block and an
        // explicit scope
        let msg = somethingHappened.message();
        notifyOthers(msg);
    }

    // ..

    recoverFromSomething();
}
```

Does it matter enough to add the extra `{ .. }` pair and indentation level? I think you should follow POLE and always (within reason!) define the smallest block for each variable. So I recommend using the extra explicit block scope as shown.

the benefits of the POLE principle are best achieved when you adopt the mindset of minimizing scope exposure by default, as a habit.

Why not just use `let` in that same location? Because `var` is visually distinct from `let` and therefore signals clearly, “this variable is function-scoped.” Using `let` in the top-level scope, especially if not in the first few lines of a function, and when all the other declarations in blocks use `let`, does not visually draw attention to the difference with the function-scoped declaration.

As long as your programs are going to need both function-scoped and block-scoped variables, the most sensible and readable approach is to use both `var` and `let` together, each for their own best purpose.

WARNING:
My recommendation to use both `var` and `let` is clearly controversial and contradicts the majority. It’s far more common to hear assertions like, “var is broken, let fixes it” and, “never use var, let is the replacement.” Those opinions are valid, but they’re merely opinions, just like mine. `var` is not factually broken or deprecated; it has worked since early JS and it will continue to work as long as JS is around.

how to decide where each declaration in your program belongs? POLE already guides you on those decisions, but let’s make sure we explicitly state it... ...The way to decide is to ask, “What is the most minimal scope exposure that’s sufficient for this variable?”

Since the introduction of `try..catch` back in ES3 (in 1999), the `catch` clause has used an additional (little-known) block-scoping declaration capability:

ES2019 (recently, at the time of writing) changed `catch` clauses so their declaration is optional; if the declaration is omitted, the `catch` block is no longer (by default) a scope; it’s still a block, though! So if you need to react to the condition that an exception occurred (so you can gracefully recover), but you don’t care about the error value itself, you can omit the `catch` declaration:

```js
try {
    doOptionOne();
}
catch {   // catch-declaration omitted
    doOptionTwoInstead();
}
```

This is a small but delightful simplification of syntax for a fairly common use case, and may also be slightly more performant in removing an unnecessary scope!

### Function Declarations in Blocks

`function` declarations that appear directly inside blocks? As a feature, this is called “FiB.”

```js
if (false) {
    function ask() {
        console.log("Does this run?");
    }
}
ask();
```

The JS specification says that `function` declarations inside of blocks are block-scoped, so the answer should be (1). However, most browser-based JS engines (including v8, which comes from Chrome but is also used in Node) will behave as (2), meaning the identifier is scoped outside the `if` block but the function value is not automatically initialized, so it remains `undefined`. Why are browser JS engines allowed to behave contrary to the specification? Because these engines already had certain behaviors around FiB before ES6 introduced block scoping, and there was concern that changing to adhere to the specification might break some existing website JS code.

It’s not my intention to document all these weird corner cases, nor to try to explain why each of them behaves a certain way. That information is, in my opinion, arcane legacy trivia.

the only practical answer to avoiding the vagaries of FiB is to simply avoid FiB entirely. In other words, never place a `function` declaration directly inside any block. Always place `function` declarations anywhere in the top-level scope of a function (or in the global scope).

Even if you test your program and it works correctly, the small benefit you may derive from using FiB style in your code is far outweighed by the potential risks in the future for confusion by other developers, or variances in how your code runs in other JS environments.

FiB is not worth it, and should be avoided.

### Blocked Over

The point of lexical scoping rules in a programming language is so we can appropriately organize our program’s variables, both for operational as well as semantic code communication purposes.

One of the most important organizational techniques is to ensure that no variable is over-exposed to unnecessary scopes (POLE).

## Chapter 7: Using Closures

Our broad goal in this book is not merely to understand scope, but to more effectively use it in the structure of our programs; closure is central to that effort.

for variables we need to use over time, instead of placing them in larger outer scopes, we can encapsulate (more narrowly scope) them but still preserve access from inside functions, for broader use. Functions remember these referenced scoped variables via closure.

If you’ve ever written a callback that accesses variables outside its own scope… guess what!? That’s closure.

Getting comfortable with closure is required for mastering JS and effectively leveraging many important design patterns throughout your code.

### See the Closure

I’m going to focus on a practical perspective. We’ll start by defining closure in terms of what we can observe in different behavior of our programs, as opposed to if closure was not present in JS. However, later in this chapter, we’re going to flip closure around to look at it from an alternative perspective.

Closure is a behavior of functions and only functions. If you aren’t dealing with a function, closure does not apply

For closure to be observed, a function must be invoked, and specifically it must be invoked in a different branch of the scope chain from where it was originally defined. A function executing in the same scope it was defined would not exhibit any observably different behavior with or without closure being possible; by the observational perspective and definition, that is not closure.

Let’s look at some code, annotated with its relevant scope bubble colors (see Chapter 2):

```js
// outer/global scope: RED(1)

function lookupStudent(studentID) {
    // function scope: BLUE(2)

    var students = [
        { id: 14, name: "Kyle" },
 
        { id: 73, name: "Suzy" },
        { id: 112, name: "Frank" },
        { id: 6, name: "Sarah" }
    ];

    return function greetStudent(greeting){
        // function scope: GREEN(3)

        var student = students.find(
            student => student.id == studentID
        );

        return `${ greeting }, ${ student.name }!`;
    };
}

var chosenStudents = [
    lookupStudent(6),
    lookupStudent(112)
];

// accessing the function's name:
chosenStudents[0].name;
// greetStudent
chosenStudents[0]("Hello");
// Hello, Sarah!

chosenStudents[1]("Howdy");
// Howdy, Frank!
```

The first thing to notice about this code is that the `lookupStudent(..)` outer function creates and returns an inner function called `greetStudent(..)`. `lookupStudent(..)` is called twice, producing two separate instances of its inner `greetStudent(..)` function, both of which are saved into the `chosenStudents` array.

We verify that’s the case by checking the `.name` property of the returned function saved in `chosenStudents[0]`, and it’s indeed an instance of the inner `greetStudent(..)`.

After each call to `lookupStudent(..)` finishes, it would seem like all its inner variables would be discarded and GC’d (garbage collected). The inner function is the only thing that seems to be returned and preserved. But here’s where the behavior differs in ways we can start to observe.

While `greetStudent(..)` does receive a single argument as the parameter named `greeting`, it also makes reference to both `students` and `studentID`, identifiers which come from the enclosing scope of `lookupStudent(..)`. 

Each of those references from the inner function to the variable in an outer scope is called a closure. In academic terms, each instance of `greetStudent(..)` closes over the outer variables `students` and `studentID`.

So what do those closures do here, in a concrete, observable sense?

Closure allows `greetStudent(..)` to continue to access those outer variables even after the outer scope is finished (when each call to `lookupStudent(..)` completes). Instead of the instances of `students` and `studentID` being GC’d, they stay around in memory. At a later time when either instance of the `greetStudent(..)` function is invoked, those variables are still there, holding their current values.

If JS functions did not have closure, the completion of each `lookupStudent(..)` call would immediately tear down its scope and GC the students and `studentID` variables. When we later called one of the `greetStudent(..)` functions, what would then happen?

If `greetStudent(..)` tried to access what it thought was a BLUE(2) marble, but that marble did not actually exist (anymore), the reasonable assumption is we should get a `ReferenceError`, right?

But we don’t get an error. The fact that the execution of `chosenStudents[0]("Hello")` works and returns us the message “Hello, Sarah!”, means it was still able to access the students and `studentID` variables. This is a direct observation of closure!

#### Pointed Closure

Even tiny arrow functions can get in on the closure party.

#### Adding Up Closures

```js
function adder(num1) {
    return function addTo(num2){
        return num1 + num2;
    };
}

var add10To = adder(10);
var add42To = adder(42);

add10To(15);    // 25
add42To(9);     // 51
```

Closure is associated with an instance of a function, rather than its single lexical definition. In the preceding snippet, there’s just one inner `addTo(..)` function defined inside `adder(..)`, so it might seem like that would imply a single closure.

But actually, every time the outer `adder(..)` function runs, a new inner `addTo(..)` function instance is created, and for each new instance, a new closure. So each inner function instance (labeled `add10To(..)` and `add42To(..)` in our program) has its own closure over its own instance of the scope environment from that execution of `adder(..)`.

Even though closure is based on lexical scope, which is handled at compile time, closure is observed as a runtime characteristic of function instances.

#### Live Link, Not a Snapshot

Closure might be a snapshot of a value at some given moment. Indeed, that’s a common misconception. Closure is actually a live link, preserving access to the full variable itself. We’re not limited to merely reading a value; the closed-over variable can be updated (re-assigned) as well! By closing over a variable in a function, we can keep using that variable (read and write) as long as that function reference exists in the program, and from anywhere we want to invoke that function. This is why closure is such a powerful technique used widely across so many areas of programming! 

Figure 4 depicts the function instances and scope links:

![ig. 4: Visualizing Closures](./assets/figure4.png)

As shown in Figure 4, each call to `adder(..)` creates a new BLUE(2) scope containing a `num1` variable, as well as a new instance of `addTo(..)` function as a GREEN(3) scope. Notice that the function instances (`addTo10(..)` and `addTo42(..)`) are present in and invoked from the RED(1) scope.

Because it’s so common to mistake closure as value-oriented instead of variable-oriented, developers sometimes get tripped up trying to use closure to snapshot-preserve a value from some moment in time. Consider:

```js
var studentName = "Frank";

var greeting = function hello() {
    // we are closing over `studentName`,
    // not "Frank"
    console.log(
        `Hello, ${ studentName }!`
    );
}

// later

studentName = "Suzy";

// later

greeting();
// Hello, Suzy!
```

By defining `greeting()` (aka, `hello()`) when `studentName` holds the value `"Frank"` (before the re-assignment to `"Suzy"`), the mistaken assumption is often that the closure will capture `"Frank"`. But `greeting()` is closed over the variable `studentName`, not its value. Whenever `greeting()` is invoked, the current value of the variable (`"Suzy"`, in this case) is reflected.

#### Common Closures: Ajax and Events

Closure is most commonly encountered with callbacks:

```js
function lookupStudentRecord(studentID) {
    ajax(
        `https://some.api/student/${ studentID }`,
        function onRecord(record) {
            console.log(
                `${ record.name } (${ studentID })`
            );
        }
    );
}

lookupStudentRecord(114);
// Frank (114)
```

The `onRecord(..)` callback is going to be invoked at some point in the future, after the response from the Ajax call comes back. This invocation will happen from the internals of the `ajax(..)` utility, wherever that comes from. Furthermore, when that happens, the `lookupStudentRecord(..)` call will long since have completed. Why then is `studentID` still around and accessible to the callback? Closure.

#### What If I Can’t See It?

If a tree falls in the forest but nobody is around to hear it, does it make a sound? It’s a silly bit of philosophical gymnastics. Of course from a scientific perspective, sound waves are created. But the real point: does it matter if the sound happens? Remember, the emphasis in our definition of closure is observability. If a closure exists (in a technical, implementation, or academic sense) but it cannot be observed in our programs, does it matter? No.

Any lexically scoped language whose functions didn’t support closure would still behave this same way.

All function invocations can access global variables, regardless of whether closure is supported by the language or not. Global variables don’t need to be closed over.

If there’s no function invocation, closure can’t be observed.

#### Observable Definition

Closure is observed when a function uses variable(s) from outer scope(s) even while running in a scope where those variable(s) wouldn’t be accessible.

- The key parts of this definition are:
- Must be a function involved
- Must reference at least one variable from an outer scope
- Must be invoked in a different branch of the scope chain from the variable(s)

### The Closure Lifecycle and Garbage Collection (GC)

Since closure is inherently tied to a function instance, its closure over a variable lasts as long as there is still a reference to that function.

On building efficient and performant programs. Closure can unexpectedly prevent the GC of a variable that you’re otherwise done with, which leads to run-away memory usage over time. That’s why it’s important to discard function references (and thus their closures) when they’re not needed anymore.

When considering the overall health and efficiency of the program, unsubscribing an event handler when it’s no longer needed can be even more important than the initial subscription!

#### Per Variable or Per Scope?

Another question we need to tackle: should we think of closure as applied only to the referenced outer variable(s), or does closure preserve the entire scope chain with all its variables?

Conceptually, closure is per variable rather than per scope. Ajax callbacks, event handlers, and all other forms of function closures are typically assumed to close over only what they explicitly reference. But the reality is more complicated than that.

Many modern JS engines do apply an optimization that removes any variables from a closure scope that aren’t explicitly referenced. However, as we see with `eval(..)`, there are situations where such an optimization cannot be applied, and the closure scope continues to contain all its original variables. In other words, closure must be per scope, implementation wise, and then an optional optimization trims down the scope to only what was closed over (a similar outcome as per variable closure).

The fact that it’s an optional optimization in the first place, rather than a requirement of the specification, means that we shouldn’t just casually over-assume its applicability.

In cases where a variable holds a large value (like an object or array) and that variable is present in a closure scope, if you don’t need that value anymore and don’t want that memory held, it’s safer (memory usage) to manually discard the value rather than relying on closure optimization/GC.

In many cases JS might automatically optimize the program to the same effect. But it’s still a good habit to be careful and explicitly make sure we don’t keep any significant amount of device memory tied up any longer than necessary.

The takeaway: it’s important to know where closures appear in our programs, and what variables are included. We should manage these closures carefully so we’re only holding onto what’s minimally needed and not wasting memory.

### An Alternative Perspective

Definition for closure... ...functions are “first-class values” that can be passed around the program, just like any other value. Closure is the link-association that connects that function to the scope/variables outside of itself, no matter where that function goes.

Let’s recall a code example from earlier in this chapter, again with relevant scope bubble colors annotated:

```js
// outer/global scope: RED(1)

function adder(num1) {
    // function scope: BLUE(2)

    return function addTo(num2){
        // function scope: GREEN(3)

        return num1 + num2;
    };
}

var add10To = adder(10);
var add42To = adder(42);

add10To(15);    // 25
add42To(9);     // 51
```

![Fig. 4 (repeat): Visualizing Closures](./assets/figure4.png)

There’s another way of thinking about closure, and more precisely the nature of functions being passed around, that may help deepen the mental models. This alternative model de-emphasizes “functions as first-class values,” and instead embraces how functions (like all non-primitive values) are held by reference in JS, and assigned/passed by reference-copy—see Appendix A of the Get Started book for more information. Instead of thinking about the inner function instance of `addTo(..)` moving to the outer RED(1) scope via the `return` and assignment, we can envision that function instances actually just stay in place in their own scope environment, of course with their scope-chain intact. What gets sent to the RED(1) scope is just a reference to the in-place function instance, rather than the function instance itself. Figure 5 depicts the inner function instances remaining in place, pointed to by the RED(1) `addTo10` and `addTo42` references, respectively:

![Fig. 5: Visualizing Closures (Alternative)](./assets/figure5.png)

Each call to `adder(..)` still creates a new BLUE(2) scope containing a `num1` variable, as well as an instance of the GREEN(3) `addTo(..)` scope.

The `addTo10` and `addTo42` references are moved to the RED(1) outer scope, not the function instances themselves. When `addTo10(15)` is called, the `addTo(..)` function instance (still in place in its original BLUE(2) scope environment) is invoked. Since the function instance itself never moved, of course it still has natural access to its scope chain.

In this alternative model, functions stay in place and keep accessing their original scope chain just like they always could. Closure instead describes the magic of keeping alive a function instance, along with its whole scope environment and chain, for as long as there’s at least one reference to that function instance floating around in any other part of the program.

The previous model (Figure 4) is not wrong at describing closure in JS. It’s just more conceptually inspired, an academic perspective on closure. By contrast, the alternative model (Figure 5) could be described as a bit more implementation focused, how JS actually works.

This alternative model for closure does affect whether we classify synchronous callbacks as examples of closure or not. 

### Why Closure?

```js
var APIendpoints = {
    studentIDs:
        "https://some.api/register-students",
    // ..
};

var data = {
    studentIDs: [ 14, 73, 112, 6 ],
    // ..
};

function makeRequest(evt) {
    var btn = evt.target;
    var recordKind = btn.dataset.kind;
    ajax(
        APIendpoints[recordKind],
        data[recordKind]
    );
 
}

// <button data-kind="studentIDs">
//    Register Students
// </button>
btn.addEventListener("click",makeRequest);
```

Let’s try using closure to improve the code:

```js
var APIendpoints = {
    studentIDs:
        "https://some.api/register-students",
    // ..
};

var data = {
    studentIDs: [ 14, 73, 112, 6 ],
    // ..
};

function setupButtonHandler(btn) {
    var recordKind = btn.dataset.kind;

    btn.addEventListener(
        "click",
        function makeRequest(evt){
            ajax(
                APIendpoints[recordKind],
                data[recordKind]
            );
        }
    );
}

// <button data-kind="studentIDs">
//    Register Students
// </button>

setupButtonHandler(btn);
```

With the `setupButtonHandler(..)` approach, the `data-kind` attribute is retrieved once and assigned to the `recordKind` variable at initial setup. `recordKind` is then closed over by the inner `makeRequest(..)` click handler, and its value is used on each event firing to look up the URL and data that should be sent.

By placing `recordKind` inside `setupButtonHandler(..)`, we limit the scope exposure of that variable to a more appropriate subset of the program; storing it globally would have been worse for code organization and readability. Closure lets the inner `makeRequest()` function instance remember this variable and access whenever it’s needed.

```js
function setupButtonHandler(btn) {
    var recordKind = btn.dataset.kind;
    var requestURL = APIendpoints[recordKind];
    var requestData = data[recordKind];

    btn.addEventListener(
        "click",
        function makeRequest(evt){
            ajax(requestURL,requestData);
        }
    );
}
```

Now `makeRequest(..)` is closed over `requestURL` and `requestData`, which is a little bit cleaner to understand, and also slightly more performant.

Partial application and currying. Briefly, with these techniques, we alter the shape of functions that require multiple inputs so some inputs are provided up front, and other inputs are provided later; the initial inputs are remembered via closure. Once all inputs have been provided, the underlying action is performed.

```js
function defineHandler(requestURL,requestData) {
    return function makeRequest(evt){
        ajax(requestURL,requestData);
    };
}

function setupButtonHandler(btn) {
    var recordKind = btn.dataset.kind;
    var handler = defineHandler(
        APIendpoints[recordKind],
        data[recordKind]
    );
    btn.addEventListener("click",handler);
}
```

Behavior-wise, this program is pretty similar to the previous one, with the same type of closure. But by isolating the creation of `makeRequest(..)` in a separate utility (`defineHandler(..)`), we make that definition more reusable across the program. We also explicitly limit the closure scope to only the two variables needed.

### Closer to Closure

two models for mentally tackling closure:

- Observational: closure is a function instance remembering its outer variables even as that function is passed to and invoked in other scopes.
- Implementational: closure is a function instance and its scope environment preserved in-place while any references to it are passed around and invoked from other scopes.

Summarizing the benefits to our programs:

- Closure can improve efficiency by allowing a function instance to remember previously determined information instead of having to compute it each time.
- Closure can improve code readability, bounding scope-exposure by encapsulating variable(s) inside function instances, while still making sure the information in those variables is accessible for future use. The resultant narrower, more specialized function instances are cleaner to interact with, since the preserved information doesn’t need to be passed in every invocation.

## Chapter 8: The Module Pattern

One of the most important code organization patterns in all of programming: the module. As we’ll see, modules are inherently built from what we’ve already covered: the payoff for your efforts in learning lexical scope and closure.

The central theme of this book has been that understanding and mastering scope and closure is key in properly structuring and organizing our code, especially the decisions on where to store information in variables. Our goal in this final chapter is to appreciate how modules embody the importance of these topics, elevating them from abstract concepts to concrete, practical improvements in building programs.

### Encapsulation and Least Exposure (POLE)

The goal of encapsulation is the bundling or co-location of information (data) and behavior (functions) that together serve a common purpose.

The recent trend in modern front-end programming to organize applications around Component architecture pushes encapsulation even further. 

Group alike program bits together, and selectively limit programmatic access to the parts we consider private details. What’s not considered private is then marked as public, accessible to the whole program.

The natural effect of this effort is better code organization. It’s easier to build and maintain software when we know where things are, with clear and obvious boundaries and connection points. It’s also easier to maintain quality if we avoid the pitfalls of over-exposed data and functionality.

### What is a Module?

A module is a collection of related data and functions (often referred to as methods in this context), characterized by a division between hidden private details and public accessible details, usually called the “public API.” A module is also stateful: it maintains some information over time, along with functionality to access and update that information.

#### Namespaces (Stateless Grouping)

If you group a set of related functions together, without data, then you don’t really have the expected encapsulation a module implies. The better term for this grouping of stateless functions is a namespace:

```js
// namespace, not module
var Utils = {
    cancelEvt(evt) {
        evt.preventDefault();
        evt.stopPropagation();
        evt.stopImmediatePropagation();
    },
    wait(ms) {
        return new Promise(function c(res){
            setTimeout(res,ms);
        });
    },
    isValidEmail(email) {
        return /[^@]+@[^@.]+\.[^@.]+/.test(email);
    }
};
```

That doesn’t make this a module. Rather, we’ve defined a `Utils` namespace and organized the functions under it.

#### Data Structures (Stateful Grouping)

Even if you bundle data and stateful functions together, if you’re not limiting the visibility of any of it, then you’re stopping short of the POLE aspect of encapsulation; it’s not particularly helpful to label that a module.

Consider:

```js
// data structure, not module
var Student = {
    records: [
        { id: 14, name: "Kyle", grade: 86 },
        { id: 73, name: "Suzy", grade: 87 },
        { id: 112, name: "Frank", grade: 75 },
        { id: 6, name: "Sarah", grade: 91 }
    ],
    getName(studentID) {
        var student = this.records.find(
            student => student.id == studentID
        );
        return student.name;
    }
};

Student.getName(73);
// Suzy
```

Since `records` is publicly accessible data, not hidden behind a public API, `Student` here isn’t really a module. `Student` does have the data-and-functionality aspect of encapsulation, but not the visibility-control aspect. It’s best to label this an instance of a data structure.

#### Modules (Stateful Access Control)

To embody the full spirit of the module pattern, we not only need grouping and state, but also access control through visibility (private vs. public).

```js
var Student = (function defineStudent(){
    var records = [
        { id: 14, name: "Kyle", grade: 86 },
        { id: 73, name: "Suzy", grade: 87 },
        { id: 112, name: "Frank", grade: 75 },
        { id: 6, name: "Sarah", grade: 91 }
    ];

    var publicAPI = {
        getName
    };

    return publicAPI;

    // ************************

    function getName(studentID) {
        var student = records.find(
            student => student.id == studentID
        );
        return student.name;
    }
})();

Student.getName(73);   // Suzy
```

`Student` is now an instance of a module. It features a public API with a single method: `getName(..)`. This method is able to access the private hidden `records` data.


How does the classic module format work? Notice that the instance of the module is created by the `defineStudent()` IIFE being executed. This IIFE returns an object (named `publicAPI`) that has a property on it referencing the inner `getName(..)` function. Naming the object `publicAPI` is stylistic preference on my part. The object can be named whatever you like (JS doesn’t care), or you can just return an object directly without assigning it to any internal named variable. More on this choice in Appendix A.

By virtue of how lexical scope works, defining variables and functions inside your outer module definition function makes everything by default private.

The use of an IIFE implies that our program only ever needs a single central instance of the module, commonly referred to as a “singleton.” Indeed, this specific example is simple enough that there’s no obvious reason we’d need anything more than just one instance of the `Student` module.

#### Module Factory (Multiple Instances)

But if we did want to define a module that supported multiple instances in our program, we can slightly tweak the code:

```js
// factory function, not singleton IIFE
function defineStudent() {
    var records = [
        { id: 14, name: "Kyle", grade: 86 },
        { id: 73, name: "Suzy", grade: 87 },
        { id: 112, name: "Frank", grade: 75 },
        { id: 6, name: "Sarah", grade: 91 }
    ];

    var publicAPI = {
        getName
    };

    return publicAPI;

    // ************************

 
    function getName(studentID) {
        var student = records.find(
            student => student.id == studentID
        );
        return student.name;
    }
}

var fullTime = defineStudent();
fullTime.getName(73);            // Suzy
```

Rather than specifying `defineStudent()` as an IIFE, we just define it as a normal standalone function, which is commonly referred to in this context as a “module factory” function.

#### Classic Module Definition

- There must be an outer scope, typically from a module factory function running at least once.
- The module’s inner scope must have at least one piece of hidden information that represents state for the module.
- The module must return on its public API a reference to at least one function that has closure over the hidden module state (so that this state is actually preserved).

### Node CommonJS Modules

Unlike the classic module format described earlier, where you could bundle the module factory or IIFE alongside any other code including other modules, CommonJS modules are file-based; one module per file.

```js
module.exports.getName = getName;

// ************************

var records = [
    { id: 14, name: "Kyle", grade: 86 },
    { id: 73, name: "Suzy", grade: 87 },
    { id: 112, name: "Frank", grade: 75 },
    { id: 6, name: "Sarah", grade: 91 }
];

function getName(studentID) {
    var student = records.find(
        student => student.id == studentID
    );
    return student.name;
}
```

Everything here is by default private to the module. To expose something on the public API of a CommonJS module, you add a property to the empty object provided as `module.exports`. 

Some developers have the habit of replacing the default exports object, like this:

```js
// defining a new object for the API
module.exports = {
    // ..exports..
};
```

There are some quirks with this approach, including unexpected behavior if multiple such modules circularly depend on each other. As such, I recommend against replacing the object. If you want to assign multiple exports at once, using object literal style definition, you can do this instead:

```js
Object.assign(module.exports,{
   // .. exports ..
});
```

What’s happening here is defining the `{ .. }` object literal with your module’s public API specified, and then `Object.assign(..)` is performing a shallow copy of all those properties onto the existing `module.exports` object, instead of replacing it This is a nice balance of convenience and safer module behavior. 

To include another module instance into your module/program, use Node’s `require(..)` method. 

```js
var Student = require("/path/to/student.js");

Student.getName(73);
// Suzy
```

`Student` now references the public API of our example module.

CommonJS modules behave as singleton instances, similar to the IIFE module definition style presented before. No matter how many times you `require(..)` the same module, you just get additional references to the single shared module instance.

`require(..)` is an all-or-nothing mechanism; it includes a reference of the entire exposed public API of the module. To effectively access only part of the API, the typical approach looks like this:

```js
var getName = require("/path/to/student.js").getName;

// or alternately:

var { getName } = require("/path/to/student.js");
```

The publicly exported methods of a CommonJS module’s API hold closures over the internal module details. That’s how the module singleton state is maintained across the lifetime of your program.

### Modern ES Modules (ESM)

ESM is file-based, and module instances are singletons, with everything private by default. One notable difference is that ESM files are assumed to be strict-mode, without needing a `"use strict"` pragma at the top... ...Instead of `module.exports` in CommonJS, ESM uses an `export` keyword to expose something on the public API of the module. The `import` keyword replaces the `require(..)` statement. 

```js
export { getName };

// ************************

var records = [
    { id: 14, name: "Kyle", grade: 86 },
    { id: 73, name: "Suzy", grade: 87 },
    { id: 112, name: "Frank", grade: 75 },
    { id: 6, name: "Sarah", grade: 91 }
];

function getName(studentID) {
    var student = records.find(
        student => student.id == studentID
    );
    return student.name;
}
```

ESM offers a fair bit of variation on how the `export` statements can be specified. For example:

```js
export function getName(studentID) {
    // .. 
}
```

Even though `export` appears before the `function` keyword here, this form is still a `function` declaration that also happens to be exported. That is, the `getName` identifier is function hoisted (see Chapter 5), so it’s available throughout the whole scope of the module. Another allowed variation:

```js
export default function getName(studentID) {
    // ..
}
```

This is a so-called “default export,” which has different semantics from other exports. In essence, a “default export” is a shorthand for consumers of the module when they `import`, giving them a terser syntax when they only need this single default API member.

“named import”:

```js
import { getName } from "/path/to/students.js";

getName(73);   // Suzy
```

As you can see, this form imports only the specifically named public API members from a module (skipping anything not named explicitly), and it adds those identifiers to the top-level scope of the current module. This type of import is a familiar style to those used to package imports in languages like Java. Multiple API members can be listed inside the `{ .. }` set, separated with commas. A named import can also be renamed with the `as` keyword:

```js
import { getName as getStudentName }
   from "/path/to/students.js";

getStudentName(73);
// Suzy
```

If `getName` is a “default export” of the module, we can import it like this:

```js
import getName from "/path/to/students.js";

getName(73);   // Suzy
```

The only difference here is dropping the `{ }` around the import binding. If you want to mix a default import with other named imports:

```js
import { default as getName, /* .. others .. */ }
   from "/path/to/students.js";

getName(73);   // Suzy
```

By contrast, the other major variation on `import` is called “namespace import”:

```js
import * as Student from "/path/to/students.js";

Student.getName(73);   // Suzy
As is likely obvious, the * imports everything exported to the API,
```

### Exit Scope
## Appendix A: Exploring Further
### Implied Scopes
### Anonymous vs. Named Functions
### Hoisting: Functions and Variables
### The Case for `var`
### What's the Deal with TDZ?
### Are Synchronous Callbacks Still Closures?
### Classic Module Variations
## Appendix B: Practice
### Buckets of Marbles
### Closure (PART 1)
### Closure (PART 2)
### Closure (PART 3)
### Modules
### Suggested Solutions

