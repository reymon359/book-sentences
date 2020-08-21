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

### Work Ethic

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

Read books, articles, blogs, tweets. Go to conferences. Go to user groups. Participate in reading and study groups. Learn things that are outside your comfort zone.

Professionals practice. True professionals work hard to keep their skills sharp and ready... ...Practice is when you specifically exercise your skills _outside_ of the performance of your job for the sole purpose of refining and enhancing those skills.

The point of the kata is to train your fingers and your brain.

The second best way to learn is to collaborate with other people. Professional software developers make a special effort to program together, practice together, design and plan together. By doing so they learn a lot from each other, and they get more done faster with fewer errors.

The best way to learn is to teach. Nothing will drive facts and values into your head faster and harder than having to communicate them to people you are responsible for. So the benefit of teaching is strongly in favor of the teacher.

Professionals take personal responsibility for mentoring juniors.

It is the responsibility of every software professional to understand the domain of the solutions they are programming.

It is the worst kind of unprofessional behavior to simply code from a spec without understanding why that spec makes sense to the business. Rather, you should know enough about the domain to be able to recognize and challenge specification errors.

Your employer’s problems are _your_ problems. You need to understand what those problems are and work toward the best solutions. 

It’s easy to fall into an _us versus them_ attitude with your employer. Professionals avoid this at all costs.

A professional is confident in his abilities, and takes bold and calculated risks based on that confidence. A professional is not timid.

## Chapter 2 Saying No

> Do; or do not. There is no trying.
> — Yoda

Professionals speak truth to power. Professionals have the courage to say no to their managers.

Slaves are not allowed to say no. Laborers may be hesitant to say no. But professionals are _expected_ to say no.

### Adversarial Roles

The hard decisions are best made through the confrontation of adversarial roles.

Your manager is counting on you to defend your objectives as aggressively as he defends his. That’s how the two of you are going to get to _the best possible outcome_.

The _why_ is a lot less important than the _fact_.

### High Stakes

The higher the stakes, the more valuable no becomes.

### Being a "Team Player"

Being a team player means playing your position as well as you possibly can, and helping out your teammates when they get into a jam. A team-player communicates frequently, keeps an eye out for his or her teammates, and executes his or her own responsibilities as well as possible.

The promise to try is an admission that you’ve been holding back, that you have a reservoir of extra effort that you can apply... ...moreover, it is a commitment to apply that extra effort to achieve the goal.

### The Cost of Saying Yes

Sometimes the only way to get to the right yes is to be unafraid so say no.

### Code Imposible

“Is good code impossible? Is professionalism impossible?” Answer: I say no.

## Chapter 3 Saying Yes

### A Language of commitment

Say. Mean. Do.
There are three parts to making a commitment.
1. You _say_ you’ll do it. 
2. You _mean_ it.
3. You _actually do_ it.

There are very few people who, when they say something, they mean it and then actually get it done. There are some who will say things and _mean_ them, but they never get it done. And there are far more people who promise things and don’t even _mean_ to do them. 

Examples of words and phrases to look for that are telltale signs of noncommitment:
- **Need\should**. “We need to get this done.” “I need to lose weight.” “Someone should make that happen.”
- **Hope\wish**. “I hope to get this done by tomorrow.” “I hope we can meet again some day.” “I wish I had time for that.” “I wish this computer was faster.”
- **Let’s**. (not followed by “I ...”) “Let’s meet sometime.” “Let’s finish this thing.”

Start recognizing lack of commitment around you, and in you.

The real truth is that _you, personally_, ALWAYS have something that’s under _your_ control, so there is always _something_ you can fully commit to doing.

If the end goal depends on someone else, you should commit to specific actions that bring you closer to the end goal.

Something unexpected might happen, and that’s life. But you still want to live up to expectations. In that case, it’s time to change the expectations, _as soon as possible_.

If you can’t make your commitment, the most important thing is to raise a red flag as soon as possible to whoever you committed to.

Creating a language of commitment may sound a bit scary, but it can help solve many of the communication problems programmers face today—estimations, deadlines, and face-to-face communication mishaps. You’ll be taken as a serious developer who lives up to their word, and that’s one of the best things you can hope for in our industry.

### Learning How to Say "Yes"

Breaking disciplines only slows us down.

Professionals know their limits. They know how much overtime they can effectively apply, and they know what the cost will be.

Professionals are not required to say yes to everything that is asked of them. However, they should work hard to find creative ways to make “yes” possible. When professionals say yes, they use the language of commitment so that there is no doubt about what they’ve promised.

## Chapter 4 Coding

Typing blind is all about _confidence_.

Being able to sense your errors is really important... ...in everything. Having error-sense means that you very rapidly close the feedback loop and learn from your errors all the more quickly.

The key to mastery is confidence and error-sense.

### Preparedness

Coding is an intellectually challenging and exhausting activity. It requires a level of concentration and focus that few other disciplines require. The reason for this is that coding requires you to juggle many competing factors at once.

1. First, your code must work.
2. Your code must solve the problem set for you by the customer.
3. Your code must fit well into the existing system... ...your code needs to follow solid engineering principles.
4. Your code must be readable by other programmers... ...this may be the most difficult thing a programmer can master.

Working while distracted creates waste. If you are tired or distracted, _do not code_. You’ll only wind up redoing what you did. Instead, find a way to eliminate the distractions and settle your mind.





