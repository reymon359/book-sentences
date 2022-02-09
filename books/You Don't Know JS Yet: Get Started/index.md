---
name: "You Don't Know JS Yet: Get Started"
Read: ['2022']
Genre: ['Software Development', 'Good Practices', 'JavaScript']
---

![Cover](./assets/you-dont-know-js-yet-get-started.jpg)

# You Don't Know JS Yet: Get Started

Kyle Simpson - 2020

## Table of Contents

TODO

## Foreword

This is what this book series is great for. It’s not just for someone picking up the language for the first time (though it’s for them, too); it’s for all software craftspeople who want to master their tools, who want to understand the ins and outs of their trade, and who want to select the proper methods for solving problems.

## Preface

### The Parts

These books approach JavaScript intentionally opposite of how The Good Parts treats the language. No, that doesn’t mean we’re looking at the bad parts, but rather, exploring all the parts.

You may have been told, or felt yourself, that JS is a deeply flawed language that was poorly designed and inconsistently implemented. Many have asserted that it’s the worst most popular language in the world; that nobody writes JS because they want to, only because they have to given its place at the center of the web. That’s a ridiculous, unhealthy, and wholly condescending claim. Millions of developers write JavaScript every day, and many of them appreciate and respect the language. Like any great language, it has its brilliant parts as well as its scars. Even the creator of JavaScript himself, Brendan Eich, laments some of those parts as mistakes. But he’s wrong: they weren’t mistakes at all. JS is what it is today—the world’s most ubiquitous and thus most influential programming language—precisely because of all those parts.

Don’t buy the lie that you should only learn and use a small collection of good parts while avoiding all the bad stuff. Don’t buy the “X is the new Y” snake oil, that some new feature of the language instantly relegates all usage of a previous feature as obsolete and ignorant.

Every part of JS is useful. Some parts are more useful than others. Some parts require you to be more careful and intentional.

You should go about learning all parts of JavaScript, and where appropriate, use them!

### The Title?

Most JS developers don’t take the time to really understand how the code that they write works. They know that it works—that it produces a desired outcome. But they either don’t understand exactly how, or worse, they have an inaccurate mental model for the how that falters on closer scrutiny.

Why is one way better or more appropriate than the other half-dozen ways you could have accomplished it? Why do all the “popular kids” say to do X with your code, but it turns out that Y might be a better choice?

You don’t finish knowing everything about JS, you just keep learning more and more as you spend more time with the language. And the deeper you go, the more you revisit what you knew before, and you re-learn it from that more experienced perspective.

You can always know JS better than you currently do.

### The Mission

Far too often, what counts is generally just the result of the program, not how the program is written or how/why it works.

You will always be more effective in your development work if you more completely understand how your code works than you are solely just getting it to produce a desired outcome.

Good enough to work is not, and should not be, good enough.

All developers regularly struggle with some piece of code not working correctly, and they can’t figure out why. But far too often, JS developers will blame this on the language rather than admitting it’s their own understanding that is falling short.

### The Path

My suggestion is you take your time going through YDKJSY. Take one chapter, read it completely through start to finish, and then go back and re-read it section by section. Stop in between each section, and practice the code or ideas from that section. For larger concepts, it probably is a good idea to expect to spend several days digesting, re-reading, practicing, then digesting some more.

The deeper you understand JS, the more questions you will ask and the more you will have to explore! That’s what I find so exciting!

## Chapter 1: What Is JavaScript?

You don’t know JS, yet. Neither do I, not fully anyway. None of us do. But we can all start getting to know JS better.

We need to start by covering a variety of important background housekeeping details, clearing up some myths and misconceptions about what the language really is (and isn’t!).

### About This Book

Knowing JS is not a destination, it’s a direction

Three main pillars around which the JS language is organized: scope/closures, prototypes/objects, and types/coercion. JS is a broad and sophisticated language, with many features and capabilities. But all of JS is founded on these three foundational pillars.

A good start always depends on a solid first step.

### What’s With That Name?

JavaScript is an artifact of marketing shenanigans. When Brendan Eich first conceived of the language, he code-named it Mocha. Internally at Netscape, the brand LiveScript was used. But when it came time to publicly name the language, “JavaScript” won the vote.

There are some superficial resemblances between JavaScript’s code and Java code... ...both languages targeting developers with assumed syntax expectations from C (and to an extent, C++). For example, we use the { to begin a block of code and the } to end that block of code, just like C/C++ and Java. We also use the ; to punctuate the end of a statement.

The official name of the language specified by TC39 and formalized by the ECMA standards body is ECMAScript. 

“Java is to JavaScript as ham is to hamster.” –Jeremy Keith, 2009

### Language Specification

TC39, the technical steering committee that manages JS. Their primary task is managing the official specification for the language.

ES2019 happens to be the 10th major numbered specification/revision since JS’s inception in 1995, so in the specification’s official URL as hosted by ECMA, you’ll find “10.0”: https://www.ecma-international.org/ecma-262/10.0/

All TC39 proposals progress through a five-stage process—of course, since we’re programmers, it’s 0-based!—Stage 0 through Stage 4. You can read more about the Stage process here: https://tc39.es/process-document/

Lots of ideas that non-TC39 members “propose,” through informal means such as social media or blog posts, are really “pre-stage 0.” You have to get a TC39 member to champion a proposal for it to be considered “Stage 0” officially.

All proposals are managed in the open, on TC39’s Github repository: https://github.com/tc39/proposals

There’s just one JS, the official standard as maintained by TC39 and ECMA.

The Web Rules Everything About (JS)

For the most part, the JS defined in the specification and the JS that runs in browser-based JS engines is the same. But there are some differences that must be considered. Sometimes the JS specification will dictate some new or refined behavior, and yet that won’t exactly match with how it works in browser-based JS engines... ...occasionally, TC39 will decide the specification should stick firm on some point even though it is unlikely that browser-based JS engines will ever conform. The solution? Appendix B, “Additional ECMAScript Features for Web Browsers”.1 The JS specification includes this appendix to detail out any known mismatches between the official JS specification and the reality of JS on the web. In other words, these are exceptions that are allowed only for web JS; other JS environments must stick to the letter of the law... ...additions to JS (syntax and APIs) that web JS includes, again for historical reasons, but which TC39 does not plan to formally specify in the core of JS.

Wherever possible, adhere to the JS specification and don’t rely on behavior that’s only applicable in certain JS engine environments.

Various JS environments (like browser JS engines, Node.js, etc.) add APIs into the global scope of your JS programs that give you environment-specific capabilities, like being able to pop an alert-style box in the user’s browser.

`console.log(..)` (and all the other `console.*` methods!). These are not specified in JS, but because of their universal utility are defined by pretty much every JS environment, according to a roughly agreed consensus.

an `alert(..)` call is JS, but `alert` itself is really just a guest, not part of the official JS specification.

Developer Tools are… tools for developers. Their primary purpose is to make life easier for developers. They prioritize DX (Developer Experience). It is not a goal of such tools to accurately and purely reflect all nuances of strict-spec JS behavior. As such, there’s many quirks that may act as “gotchas” if you’re treating the console as a pure JS environment.

We can’t and shouldn’t expect such tools to always adhere strictly to the way JS programs are handled, because that’s not the purpose of these tools.

some examples of quirks that have been true at various points in different JS console environments, to reinforce my point about not assuming native JS behavior while using them:
- Whether a `var` or `function` declaration in the top-level “global scope” of the console actually creates a real global variable (and mirrored `window` property, and vice versa!).
- What happens with multiple `let` and `const` declarations in the top-level “global scope.”
- Whether `"use strict";` on one line-entry (pressing `<enter>` after) enables strict mode for the rest of that console session, the way it would on the first line of a .js file, as well as whether you can use `"use strict";` beyond the “first line” and still get strict mode turned on for that session.
- How non-strict mode `this` default-binding works for function calls, and whether the “global object” used will contain expected global variables.
- How hoisting (see Book 2, Scope & Closures) works across multiple line entries.
- ...several others

The developer console is not trying to pretend to be a JS compiler that handles your entered code exactly the same way the JS engine handles a .js file. It’s trying to make it easy for you to quickly enter a few lines of code and see the results immediately. These are entirely different use cases, and as such, it’s unreasonable to expect one tool to handle both equally.

Think of the console as a “JS-friendly” environment. That’s useful in its own right.

### Many Faces

No matter what a program’s individual style may be, the big picture divisions around paradigms are almost always evident at first glance of any program.

Paradigm-level code categories include procedural, object-oriented (OO/classes), and functional (FP):
- Procedural style organizes code in a top-down, linear progression through a pre-determined set of operations, usually collected together in related units called procedures.
- OO style organizes code by collecting logic and data together into units called classes.
- FP style organizes code into functions (pure computations as opposed to procedures), and the adaptations of those functions as values.

Paradigms are neither right nor wrong. They’re orientations that guide and mold how programmers approach problems and solutions, how they structure and maintain their code.

JavaScript is most definitely a multi-paradigm language. You can write procedural, class-oriented, or FP-style code, and you can make those decisions on a line-by-line basis instead of being forced into an all-or-nothing choice.

### Backwards & Forwards

One of the most foundational principles that guides JavaScript is preservation of backwards compatibility.

Backwards compatibility means that once something is accepted as valid JS, there will not be a future change to the language that causes that code to become invalid JS.

TC39 members often proclaim, “we don’t break the web!”

Maintaining backwards compatibility, stretched out across almost 25 years of the language’s history, creates an enormous burden and a whole slew of unique challenges. You’d be hard pressed to find many other examples in computing of such a commitment to backwards compatibility.

There are some small exceptions to this rule. JS has had some backwards-incompatible changes, but TC39 is extremely cautious in doing so. They study existing code on the web (via browser data gathering) to estimate the impact of such breakage, and browsers ultimately decide and vote on whether they’re willing to take the heat from users for a very small-scale breakage weighed against the benefits of fixing or improving some aspect of the language for many more sites (and users). These kinds of changes are rare, and are almost always in corner cases of usage that are unlikely to be observably breaking in many sites.

Being forwards-compatible means that including a new addition to the language in a program would not cause that program to break if it were run in an older JS engine. JS is not forwards-compatible, despite many wishing such, and even incorrectly believing the myth that it is.

Though JS isn’t, and can’t be, forwards-compatible, it’s critical to recognize JS’s backwards compatibility, including the enduring benefits to the web and the constraints and difficulties it places on JS as a result.

Since JS is not forwards-compatible, it means that there is always the potential for a gap between code that you can write that’s valid JS, and the oldest engine that your site or application needs to support. If you run a program that uses an ES2019 feature in an engine from 2016, you’re very likely to see the program break and crash.

Transpiling is a contrived and community-invented term to describe using a tool to convert the source code of a program from one form to another (but still as textual source code).

A developer may write a snippet of code like:
```
if (something) {
    let x = 3;
    console.log(x);
}
else {
    let x = 4;
    console.log(x);
}
```

the Babel transpiler might convert that code to look like this:

```
var x$0, x$1;
if (something) {
    x$0 = 3;
    console.log(x$0);
}
else {
    x$1 = 4;
    console.log(x$1);
}
```

Developers should focus on writing the clean, new syntax forms, and let the tools take care of producing a forwards-compatible version of that code that is suitable to deploy and run on the oldest-supported JS engine environments.

Missing API method that was only recently added, the most common solution is to provide a definition for that missing API method that stands in and acts as if the older environment had already had it natively defined. This pattern is called a polyfill (aka “shim”).

Always write code using the most appropriate features to communicate its ideas and intent effectively.

Avoid negatively impacting the code’s readability by trying to manually adjust for the syntax/API gaps. That’s what tools are for!

### What’s in an Interpretation?

A long-debated question for code written in JS: is it an interpreted script or a compiled program? The majority opinion seems to be that JS is an interpreted (scripting) language. But the truth is more complicated than that... ...The real reason it matters to have a clear picture on whether JS is interpreted or compiled relates to the nature of how errors are handled.

Historically, scripted or interpreted languages were executed in generally a top-down and line-by-line fashion; there’s typically not an initial pass through the program to process it before execution begins (see Figure 1).

![Fig. 1: Interpreted/Scripted Execution](./assets/figure1.jpg)

an error on line 5 of a program won’t be discovered until lines 1 through 4 have already executed... ...Depending on context, deferring error handling to the line the error occurs on may be a desirable or undesirable effect. Compare that to languages which do go through a processing step (typically, called parsing) before any execution occurs, as illustrated in Figure 2:

![Fig. 2: Parsing + Compilation + Execution](./assets/figure2.jpg)

All compiled languages are parsed. So a parsed language is quite a ways down the road toward being compiled already. In classic compilation theory, the last remaining step after parsing is code generation: producing an executable form.

Parsed languages usually also perform code generation before execution, so it’s not that much of a stretch to say that, in spirit, they’re compiled languages.

So JS is a parsed language, but is it compiled? The answer is closer to yes than no. The parsed JS is converted to an optimized (binary) form, and that “code” is subsequently executed (Figure 2); the engine does not commonly switch back into line-by-line execution (like Figure 2) mode after it has finished all the hard work of parsing—most languages/engines wouldn’t, because that would be highly inefficient. To be specific, this “compilation” produces a binary byte code (of sorts), which is then handed to the “JS virtual machine” to execute. Some like to say this VM is “interpreting” the byte code. But then that means Java, and a dozen other JVM-driven languages, for that matter, are interpreted rather than compiled. Of course, that contradicts the typical assertion that Java/etc are compiled languages. Interestingly, while Java and JavaScript are very different languages, the question of interpreted/compiled is pretty closely related between them!

The entire flow of a JS source program: 
1. After a program leaves a developer’s editor, it gets transpiled by Babel, then packed by Webpack (and perhaps half a dozen other build processes), then it gets delivered in that very different form to a JS engine.
2. The JS engine parses the code to an AST.
3. Then the engine converts that AST to a kind-of byte code, a binary intermediate representation (IR), which is then refined/converted even further by the optimizing JIT compiler.
4. Finally, the JS VM executes the program.
To visualize thoses steps, again:

![Fig. 3: Parsing, Compiling, and Executing JS](./assets/figure3.jpg)

In spirit, if not in practice, JS is a compiled language. And again, the reason that matters is, since JS is compiled, we are informed of static errors (such as malformed syntax) before our code is executed. That is a substantively different interaction model than we get with traditional “scripting” programs, and arguably more helpful!

Web Assembly (WASM)... ...In 2013, engineers from Mozilla Firefox demonstrated a port of the Unreal 3 game engine from C to JS... ...the JS version of the Unreal engine’s code used a style of code that favored a subset of the JS language, named “ASM.js”... ...ASM.js was introduced as one way of addressing the pressures on the runtime performance of JS. But it’s important to note that ASM.js was never intended to be code that was authored by developers, but rather a representation of a program having been transpiled from another language (such as C), where these typing “annotations” were inserted automatically by the tooling. Several years after ASM.js demonstrated the validity of tooling-created versions of programs that can be processed more efficiently by the JS engine, another group of engineers (also, initially, from Mozilla) released Web Assembly (WASM).

WASM is similar to ASM.js in that its original intent was to provide a path for non-JS programs (C, etc.) to be converted to a form that could run in the JS engine.

WASM is a representation format more akin to Assembly (hence, its name) that can be processed by a JS engine by skipping the parsing/compilation that the JS engine normally does. The parsing/compilation of a WASM-targeted program happen ahead of time (AOT); what’s distributed is a binary-packed program ready for the JS engine to execute with very minimal processing.

In other words, WASM relieves the pressure to add features to JS that are mostly/exclusively intended to be used by transpiled programs from other languages. That means JS feature development can be judged (by TC39) without being skewed by interests/demands in other language ecosystems, while still letting those languages have a viable path onto the web.

WASM isn’t only for the web, and WASM also isn’t JS. Ironically, even though WASM runs in the JS engine, the JS language is one of the least suitable languages to source WASM programs with, because WASM relies heavily on static typing information.

WASM will not replace JS. WASM significantly augments what the web (including JS) can accomplish. That’s a great thing, entirely orthogonal to whether some people will use it as an escape hatch from having to write JS.

### Strictly Speaking

Strict mode shouldn’t be thought of as a restriction on what you can’t do, but rather as a guide to the best way to do things so that the JS engine has the best chance of optimizing and efficiently running the code.

Most strict mode controls are in the form of early errors, meaning errors that aren’t strictly syntax errors but are still thrown at compile time (before the code is run). 

The best mindset is that strict mode is like a linter reminding you how JS should be written to have the highest quality and best chance at performance.

Strict mode can alternatively be turned on per-function scope, with exactly the same rules about its surroundings:

```js
function someOperations() {
    // whitespace and comments are fine here
    "use strict";
    // all this code will run in strict mode
}
```

The only valid reason to use a per-function approach to strict mode is when you are converting an existing non-strict mode program file and need to make the changes little by little over time. Otherwise, it’s vastly better to simply turn strict mode on for the entire file/program.

ES6 modules assume strict mode, so all code in such files is automatically defaulted to strict mode.

### Defined

JS is an implementation of the ECMAScript standard... ...which is guided by the TC39 committee and hosted by ECMA. It runs in browsers and other JS environments such as Node.js. JS is a multi-paradigm language, meaning the syntax and capabilities allow a developer to mix and match (and bend and reshape!) concepts from various major paradigms, such as procedural, object-oriented (OO/classes), and functional (FP). JS is a compiled language, meaning the tools (including the JS engine) process and verify a program (reporting any errors!) before it executes.

## Chapter 2: Surveying JS

The best way to learn JS is to start writing JS.

We’re just going to survey some of the major topic areas of the language... ...Please don’t expect this chapter to be a quick read. It’s long and there’s plenty of detail to chew on. Take your time.

### Each File is a Program

In JS, each standalone file is its own separate program.

The reason this matters is primarily around error handling. Since JS treats files as programs, one file may fail (during parse/compile or execution) and that will not necessarily prevent the next file from being processed.

Ensure that each file works properly, and that to whatever extent possible, they handle failure in other files as gracefully as possible.

Many projects use build process tools that end up combining separate files from the project into a single file to be delivered to a web page. When this happens, JS treats this single combined file as the entire program.

The only way multiple standalone .js files act as a single program is by sharing their state (and access to their public functionality) via the “global scope.” They mix together in this global scope namespace, so at runtime they act as as whole.

Though you wouldn’t typically think about a module—a collection of state and publicly exposed methods to operate on that state—as a standalone program, JS does in fact still treat each module separately. Similar to how “global scope” allows standalone files to mix together at runtime, importing a module into another allows runtime interoperation between them.

Regardless of which code organization pattern (and loading mechanism) is used for a file (standalone or module), you should still think of each file as its own (mini) program, which may then cooperate with other (mini) programs to perform the functions of your overall application.

### Values

The most fundamental unit of information in a program is a value. Values are data. They’re how the program maintains state. 

Values come in two forms in JS: primitive and object.

Values are embedded in programs using literals: `greeting("My name is Kyle.");` In this program, the value `"My name is Kyle."` is a primitive string literal; strings are ordered collections of characters, usually used to represent words and sentences.

The choice of which quote character is entirely stylistic. The important thing, for code readability and maintainability sake, is to pick one and to use it consistently throughout the program.

The better approach is to use `"` or `'` (again, pick one and stick to it!) for strings unless you need interpolation; reserve ` `` ` only for strings that will include interpolated expressions.

Numbers are most often used in programs for counting steps, such as loop iterations, and accessing information in numeric positions (i.e., an array index).

JS array indices are 0-based (0 is the first position).

In addition to strings, numbers, and booleans, two other primitive values in JS programs are null and undefined. While there are differences between them (some historic and some contemporary), for the most part both values serve the purpose of indicating emptiness (or absence) of a value.

#### Arrays And Objects

Arrays are a special type of object that’s comprised of an ordered and numerically indexed list of data

Functions, like arrays, are a special kind (aka, sub-type) of object. 

Objects are more general: an unordered, keyed collection of any various values.

#### Value Type Determination

For distinguishing values, the typeof operator tells you its built-in type, if primitive, or "object" otherwise:

```js
typeof 42;                  // "number"
typeof "abc";               // "string"
typeof true;                // "boolean"
typeof undefined;           // "undefined"
typeof null;                // "object" -- oops, bug!
typeof { "a": 1 };          // "object"
typeof [1,2,3];             // "object"
typeof function hello(){};  // "function"
```

#### Warning

typeof null unfortunately returns "object" instead of the expected "null". Also, typeof returns the specific "function" for functions, but not the expected "array" for arrays.

Converting from one value type to another... ...is referred to in JS as “coercion.” 

### Declaring and Using Variables

Think of variables as just containers for values... ...There are various syntax forms that declare variables (aka, “identifiers”), and each form has different implied behaviors.

The var keyword declares a variable to be used in that part of the program, and optionally allows initial value assignment.

The let keyword has some differences to var, with the most obvious being that let allows a more limited access to the variable than var. This is called “block scoping” as opposed to regular or function scoping.

```
var adult = true;

if (adult) {
    var name = "Kyle";
    let age = 39;
    console.log("Shhh, this is a secret!");
}

console.log(name);
// Kyle

console.log(age);
// Error!
```

The attempt to access age outside of the if statement results in an error, because age was block-scoped to the if, whereas name was not.

Block-scoping is very useful for limiting how widespread variable declarations are in our programs, which helps prevent accidental overlap of their names.

It’s very common to suggest that var should be avoided in favor of let (or const!),... ...I believe this to be overly restrictive advice and ultimately unhelpful. It’s assuming you are unable to learn and use a feature properly in combination with other features. I believe you can and should learn any features available, and use them where appropriate!

const declared variables are not “unchangeable”, they just cannot be re-assigned. It’s ill-advised to use const with object values, because those values can still be changed even though the variable can’t be re-assigned. This leads to potential confusion down the line.

The best semantic use of a const is when you have a simple primitive value that you want to give a useful name to, such as using myBirthday instead of true. This makes programs easier to read.

If you stick to using const only with primitive values, you avoid any confusion of re-assignment (not allowed) vs. mutation (allowed)! That’s the safest and best way to use const.

### Functions

In JS, we should consider “function” to take the broader meaning of another related term: “procedure.” A procedure is a collection of statements that can be invoked one or more times, may be provided some inputs, and may give back one or more outputs.

```js
function awesomeFunction(coolThings) {
    // ..
    return amazingStuff;
}
```

This is called a function declaration because it appears as a statement by itself, not as an expression in another statement. The association between the identifier awesomeFunction and the function value happens during the compile phase of the code, before that code is executed. In contrast to a function declaration statement, a function expression can be defined and assigned like this:

```js
// let awesomeFunction = ..
// const awesomeFunction = ..
var awesomeFunction = function(coolThings) {
    // ..
    return amazingStuff;
};
```

This function is an expression that is assigned to the variable awesomeFunction. Different from the function declaration form, a function expression is not associated with its identifier until that statement during runtime.

In JS, functions are values that can be assigned (as shown in this snippet) and passed around. In fact, JS functions are a special type of the object value type. Not all languages treat functions as values, but it’s essential for a language to support the functional programming pattern, as JS does.

Since functions are values, they can be assigned as properties on objects:
```js
var whatToSay = {
    greeting() {
        console.log("Hello!");
    },
    question() {
        console.log("What's your name?");
    },
    answer() {
        console.log("My name is Kyle.");
    }
};

whatToSay.greeting();
// Hello!
```

### Comparisons

We must be aware of the nuanced differences between an equality comparison and an equivalence comparison.

Specifically, `===` disallows any sort of type conversion (aka, “coercion”) in its comparison, where other JS comparisons do allow coercion.

The `===` operator is designed to lie in two cases of special values: NaN and -0. Consider:

```js
NaN === NaN;            // false
0 === -0;               // true
```

In the case of NaN, the === operator lies and says that an occurrence of NaN is not equal to another NaN. In the case of -0 (yes, this is a real, distinct value you can use intentionally in your programs!), the === operator lies and says it’s equal to the regular 0 value.

You could think of `Object.is(..)` as the “quadruple-equals” `====`, the really-really-strict comparison!

When we consider comparisons of object values (non-primitives). Consider:
```js
[ 1, 2, 3 ] === [ 1, 2, 3 ];    // false
{ a: 42 } === { a: 42 }         // false
(x => x * 2) === (x => x * 2)   // false
```
What’s going on here?... ...JS does not define `===` as structural equality for object values. Instead, `===` uses identity equality for object values.

In JS, all object values are held by reference are assigned and passed by reference-copy, and to our current discussion, are compared by reference (identity) equality. Consider:
```js
var x = [ 1, 2, 3 ];

// assignment is by reference-copy, so
// y references the *same* array as x,
// not another copy of it.
var y = x;

y === x;              // true
y === [ 1, 2, 3 ];    // false
x === [ 1, 2, 3 ];    // false
```
In this snippet, y `===` x is true because both variables hold a reference to the same initial array... ...The array structure and contents don’t matter in this comparison, only the reference identity.

JS doesn’t provide structural equality comparison because it’s almost intractable to handle all the corner cases!

#### Coercive Comparisons

Coercion means a value of one type being converted to its respective representation in another type (to whatever extent possible). 

Few JS features draw more ire in the broader JS community than the `==` operator, generally referred to as the “loose equality” operator. The majority of all writing and public discourse on JS condemns this operator as poorly designed and dangerous/bug-ridden when used in JS programs. Even the creator of the language himself, Brendan Eich, has lamented how it was designed as a big mistake.

The `==` operator performs an equality comparison similarly to how the `===` performs it. In fact, both operators consider the type of the values being compared. And if the comparison is between the same value type, both `==` and `===` do exactly the same thing, no difference whatsoever.

If the value types being compared are different, the `==` differs from `===` in that it allows coercion before the comparison

Relational comparison operators like <, > (and even <= and >=). Just like `==,` these operators will perform as if they’re “strict” if the types being relationally compared already match, but they’ll allow coercion first (generally, to numbers) if the types differ. Consider:
```js
var arr = [ "1", "10", "100", "1000" ];
for (let i = 0; i < arr.length && arr[i] < 500; i++) {
    // will run 3 times
}
```

Relational operators typically use numeric comparisons, except in the case where both values being compared are already strings; in this case, they use alphabetical (dictionary-like) comparison of the strings:

```js
var x = "10";
var y = "9";

x < y;      // true, watch out!
```

There’s no way to get these relational operators to avoid coercion, other than to just never use mismatched types in the comparisons. That’s perhaps admirable as a goal, but it’s still pretty likely you’re going to run into a case where the types may differ.

### How We Organize in JS

Two major patterns for organizing code (data and behavior) are used broadly across the JS ecosystem: classes and modules.

Being proficient in JS requires understanding both patterns and where they are appropriate (and not!).

#### Classes

A class in a program is a definition of a “type” of custom data structure that includes both data and behaviors that operate on that data. Classes define how such a data structure works, but classes are not themselves concrete values. To get a concrete value that you can use in the program, a class must be instantiated (with the new keyword) one or more times.

Behavior (methods) can only be called on instances (not the classes themselves)

The class mechanism allows packaging data (text and pages) to be organized together with their behaviors... ...The same program could have been built without any class definitions, but it would likely have been much less organized, harder to read and reason about, and more susceptible to bugs and subpar maintenance.

Class Inheritance... ...Another aspect inherent to traditional “class-oriented” design, though a bit less commonly used in JS, is “inheritance” (and “polymorphism”)

The fact that both the inherited and overridden methods can have the same name and co-exist is called polymorphism.

Inheritance is a powerful tool for organizing data/behavior in separate logical units (classes), but allowing the child class to cooperate with the parent by accessing/using its behavior and data.

#### Modules

The module pattern has essentially the same goal as the class pattern, which is to group data and behavior together into logical units. Also like classes, modules can “include” or “access” the data and behaviors of other modules, for cooperation sake. But modules have some important differences from classes. Most notably, the syntax is entirely different.

ES6 added a module syntax form to native JS syntax... ...But from the early days of JS, modules was an important and common pattern that was leveraged in countless JS programs, even without a dedicated syntax.

The key hallmarks of a classic module are an outer function (that runs at least once), which returns an “instance” of the module with one or more functions exposed that can operate on the module instance’s internal (hidden) data.

The `class` form stores methods and data on an object instance, which must be accessed with the `this.` prefix. With modules, the methods and data are accessed as identifier variables in scope, without any `this.` prefix. With `class`, the “API” of an instance is implicit in the class definition—also, all data and methods are public. With the module factory function, you explicitly create and return an object with any publicly exposed methods, and any data or other unreferenced methods remain private inside the factory function.

First, there’s no wrapping function to define a module. The wrapping context is a file. ESMs are always file-based; one file, one module. Second, you don’t interact with a module’s “API” explicitly, but rather use the `export` keyword to add a variable or method to its public API definition. If something is defined in a module but not `export`ed, then it stays hidden (just as with classic modules). Third, and maybe most noticeably different from previously discussed patterns, you don’t “instantiate” an ES module, you just `import` it to use its single instance. ESMs are, in effect, “singletons,” in that there’s only one instance ever created, at first `import` in your program, and all other `import`s just receive a reference to that same single instance. If your module needs to support multiple instantiations, you have to provide a classic module-style factory function on your ESM definition for that purpose.

```js
function printDetails(title,author,pubDate) {
    console.log(`
        Title: ${ title }
        By: ${ author }
        ${ pubDate }
    `);
}

export function create(title,author,pubDate) {
    var publicAPI = {
        print() {
            printDetails(title,author,pubDate);

        }
    };

    return publicAPI;
}
```

To import and use this module, from another ES module like `blogpost.js`:

```js
import { create as createPub } from "publication.js";

function printDetails(pub,URL) {
    pub.print();
    console.log(URL);
}

export function create(title,author,pubDate,URL) {
    var pub = createPub(title,author,pubDate);

    var publicAPI = {
        print() {
            printDetails(pub,URL);
        }
    };

    return publicAPI;
}
```

And finally, to use this module, we import into another ES module like `main.js`:

```js
import { create as newBlogPost } from "blogpost.js";

var forAgainstLet = newBlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

ES modules can use classic modules internally if they need to support multiple-instantiation. Alternatively, we could have exposed a `class` from our module instead of a `create(..)` factory function, with generally the same outcome. However, since you’re already using ESM at that point, I’d recommend sticking with classic modules instead of `class`.

If your module only needs a single instance, you can skip the extra layers of complexity: `export` its public methods directly.

### The Rabbit Hole Deepens

In the next chapter, we’re going to dig much deeper into some important aspects of how JS works at its core. But before you follow that rabbit hole deeper, make sure you’ve taken adequate time to fully digest what we’ve just covered here.

## Chapter 3: Digging to the Roots of JS



### Iteration



### Closure



### this Keyword



### Prototypes



### Asking “Why?”



## Chapter 4: The Bigger Picture



### Pillar 1: Scope and Closure



### Pillar 2: Prototypes



### Pillar 3: Types and Coercion



### With the Grain



### In Order



## Appendix A: Exploring Further



### Values vs. References



### So Many Function Forms



### Coercive Conditional Comparison



### Prototypal “Classes”



## Appendix B: Practice, Practice, Practice!



### Practicing Comparisons



### Practicing Closure



### Practicing Prototypes



### Suggested Solutions
