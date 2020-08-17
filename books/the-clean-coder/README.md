<p align="center"><img alt="the-clean-coder" src="./the-clean-coder.png" width="250" /></p> 

<h1 align="center">The Clean Coder. A code of conduct for professional programmers.</h1>

<h3 align="center">Robert C. Martin - 2011</h3> 

# Table of contents

## Foreword

It was the sort of environment in which some people complain, and others point out that “pressure makes diamonds.”

## Preface

As an engineer, you have a depth of knowledge about your systems and projects that no managers can possibly have. With that knowledge comes the responsibility to _act_.

## Acknowledgments

No one in your life will teach you more than your children will.

## On the Cover

![Crab Nebula On the Cover](./crab_nebula_on_the_cover.jpg)

The crab nebula is the remnant of a super-nova... ...At the very center of the target is a bright blue dot. That’s where the _pulsar_ is... ...The pulsar is spinning about 30 times per second; and it flashes as it spins... ...Those pulses of light are the reason we call it a pulsar, which is short for Pulsating Star.

## Pre-Requisite Introduction

Never quit without having a new job, and you always quit calmly, coolly, and alone.

## Chapter 1 Professionalism

### Be Careful what you ask for

Professionalism is... ...responsibility and accountability... ...You can’t take pride and honor in something that you can’t be held accountable for.

When a professional makes a mistake, _he_ cleans up the mess.

Professionalism is all about taking responsibility.

### Taking Responsibility

### First, Do No Harm

Software _is_ too complex to create without bugs... ...The fact that the task to write perfect software is virtually impossible does not mean you aren’t responsible for the imperfection.

The first thing you must practice is apologizing. Apologies are necessary, but insufficient.

As you mature in your profession, your error rate should rapidly decrease towards the asymptote of zero. It won’t ever get to zero, but it is your responsibility to get as close as possible to it.

Releasing code to QA that you don’t know works is unprofessional. It violates the “do no harm” rule.

How can you _know_ your code works? That’s easy. Test it. Test it again. Test it up. Test it down. Test it seven ways to Sunday!

Automate your tests... ...and run those tests as often as you can.

Every single line of code that you write should be tested.

Design your code to be _easy_ to test. And the best way to do that is to write your tests first, before you write the code that passes them.

So, at the very least, your automated tests should tell you that the system is _very likely_ to pass QA.

It is the structure of your code that allows it to be flexible. If you compromise the structure, you compromise the future... ...Software is easy to change. If you violate this assumption by creating inflexible structures, then you undercut the economic model that the entire industry is based on. In short: _You must be able to make changes without exorbitant costs_.

The only way to prove that your software is easy to change is to make easy changes to it. And when you find that the changes aren’t as easy as you thought, you refine the design so that the next change is easier. When do you make these easy changes? _All the time_!... ...This philosophy is sometimes called _merciless refactoring_.

If you have an automated suite of tests that covers virtually 100% of the code... ..._you simply will not be afraid to change the code._

### First, Do No Harm

Your career is _your_ responsibility... ...Woe to the software developer who entrusts his career to his employer.

You owe your employer a certain amount of time and effort... ...These... ...should be spent on _your employer’s_ problems, not on _your_ problems.

Do the math. In a week there are 168 hours. Give your employer 40, and your career another 20. That leaves 108. Another 56 for sleep leaves 52 for everything else.

Professionals spend _time_ caring for their profession.

Presumably you became a software developer because you are passionate about software and your desire to be a professional is motivated by that passion.

Our field is progressing and at a ferocious pace... ..., however, that progress is in many respects peripheral.

The vast majority of the hard-won ideas of the last 50 years are as valuable today as they were then. Perhaps they are even more valuable now.

> Those who cannot remember the past are condemned to repeat it.
> — Santayana.

_Minimal_ list of the things that every software professional should be conversant with:
- Design patterns. You ought to be able to describe all 24 patterns in the GOF book and have a working knowledge of many of the patterns in the POSA books.
- Design principles. You should know the SOLID principles and have a good understanding of the component principles.
- Methods. You should understand XP, Scrum, Lean, Kanban, Waterfall, Structured Analysis, and Structured Design.
- Disciplines. You should practice TDD, Object-Oriented design, Structured Programming, Continuous Integration, and Pair Programming.
- Artifacts: You should know how to use: UML, DFDs, Structure Charts, Petri Nets, State Transition Diagrams and Tables, flow charts, and decision tables.
