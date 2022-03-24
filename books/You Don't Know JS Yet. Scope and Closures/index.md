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

