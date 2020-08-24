<p align="center"><img alt="the-clean-coder" src="./the-clean-coder.png" width="250" /></p> 

<h1 align="center">The Clean Coder. A code of conduct for professional programmers.</h1>

<h3 align="center">Robert C. Martin - 2011</h3> 

# Table of contents // TODO

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

Don’t write code when you are tired. Dedication and professionalism are more about discipline than hours. Make sure that your sleep, health, and lifestyle are tuned so that you can put in eight _good_ hours per day.

Professional developers allocate their personal time in order to ensure that the time spent at the office is as productive as possible.

### The Flow Zone

“The Zone”... ...is the highly focused, tunnel-vision state of consciousness that programmers can get into while they write code. In this state they feel _productive_. In this state they feel _infallible_. And so they desire to attain that state... ...a little hint from someone whose been there and back: _Avoid the Zone_... ...It’s really just a mild meditative state in which certain rational faculties are diminished in favor of a sense of speed.

Pairing can be very helpful as a way to deal with interruptions. Your pair partner can hold the context of the problem at hand.. ...When you return to your pair partner, he quickly helps you reconstruct the mental context you had before the interruption... ...TDD is another big help. If you have a failing test, that test holds the context of where you are.

_There will be interruptions_ that distract you and cause you to lose time... ...remember that next time you may be the one who needs to interrupt someone else. So the professional attitude is a polite willingness to be helpful.

### Writer's Block

Sometimes the code just doesn’t come... ...You sit at your workstation and nothing happens... ...many of the factors are...not getting enough sleep...worry, fear, and depression... ...The solution: Find a pair partner.

Creative output depends on creative input... ...creativity breeds creativity.

### Debugging

Debugging time is just as expensive to the business as coding time is, and therefore anything we can do to avoid or diminish it is good.

It is incumbent upon you as a professional to reduce your debugging time as close to zero as you can get. Clearly zero is an asymptotic goal, but it is the goal nonetheless.

### Pacing Yourself

Software development is a marathon, not a sprint... ...A marathon runner takes care of her body both before and _during_ the race. Professional programmers conserve their energy and creativity with the same care.

When you are stuck, when you are tired, disengage for awhile.

There is something about _disengagement_ that allows your mind to hunt for solutions in a different and more creative way.

When you are working on a problem, you sometimes get so close to it that you can’t see all the options.

Sometimes the best way to solve a problem is to go home, eat dinner, watch TV, go to bed, and then wake up the next morning and take a shower.

### Being Late

You _will_ be late... ...Sometimes we just blow our estimates and wind up late.

The trick to managing lateness is early detection and transparency... ..._regularly_ measure your progress against your goal... ...Be as honest as you can about all dates. _Do not incorporate hope into your estimates!_

Hope is the project killer. Hope destroys schedules and ruins reputations. Hope will get you into deep trouble.

The only way to improve the schedule is to reduce scope. _Do not be tempted to rush_.

Woe to the poor developer who buckles under pressure and agrees to try to make the deadline... ...This is a recipe for disaster because it gives you, your team, and your stakeholders false hope.

There is no way to rush. You can’t make yourself code faster. You can’t make yourself solve problems faster.

You should _not agree_ to work overtime unless (1) you can personally afford it, (2) it is short term, two weeks or less, and (3) _your boss has a fall-back plan_ in case the overtime effort fails.

Of all the unprofessional behaviors... ...perhaps the worst of all is saying you are done when you know you aren’t... ...This is a contagious practice. If one programmer does it, others will see and follow suit... ...When a team falls into this trap... ...It’s like blind men having a picnic on the railroad tracks.

You avoid the problem of false delivery by creating an independent definition of “done.” The best way to do this is to have... ...automated acceptance tests.

### Help

Programming is hard. The younger you are the less you believe this... ...you have to carefully partition the system into small understandable units that have as little to do with each other as possible—and that’s hard.

No matter how skilled you are, you will certainly benefit from another programmer’s thoughts and ideas.

It is the responsibility of programmers to be available to help each other.

As a professional you are honor bound to offer that help whenever it is needed.

If you see someone who appears to be in trouble, you should offer your help.

When you help someone, sit down and write code together... ...You will likely come away having learned more than you gave.

When someone offers to help you, be gracious about it. Accept the help gratefully and give yourself to that help. 

Just as you are honor bound to offer help, you are honor bound to accept help.

It is unprofessional to remain stuck when help is easily accessible.

Collaboration is critical to effective programming. 

The training of less experienced programmers is the responsibility of those who have more experience... ...Nothing can bring a young software developer to high performance quicker than his own drive, and effective mentoring by his seniors.

## Chapter 5 Test Driven Development

### The Jury Is In

### The Three Laws of TDD

The Three laws of TDD:
1. You are not allowed to write any production code until you have first written a failing unit test.
2. You are not allowed to write more of a unit test than is sufficient to fail—and not compiling is failing.
3. You are not allowed to write more production code that is sufficient to pass the currently failing unit test.

**Certainty**. 

If you adopt TDD as a professional discipline, then you will write dozens of tests every day... ...And you will keep all those tests on hand and run them any time you make any changes to the code.

How certain is “nearly certain”? Certain enough to ship!

**Defect Injection Rate**.

**Courage**. 

When you have a suite of tests that you trust, then you lose all fear of making changes... ...The code becomes clay that you can safely sculpt into simple and pleasing structures.

When programmers lose the fear of cleaning, they clean! And clean code is easier to understand, easier to change, and easier to extend.

**Documentation**. 

If you want to know how to use code you need to read code.

The unit tests are documents. They describe the lowest-level design of the system... ...They are the best kind of low-level documentation that can exist.

**Design**

The need to test first forces you to think about _good design_.

But the tests you write after the fact are _defense_. The tests you write first are _offense_.

TDD is the professional option. It is a discipline that enhances certainty, courage, defect reduction, documentation, and design... ...it could be considered _unprofessional_ not to use it.

### What TDD Is Not

No professional developer should ever follow a discipline when that discipline does more harm than good.

