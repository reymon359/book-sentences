# The Pragmatic Programmer. Your Journey to Mastery, 20th Anniversary Edition 
Andy Hunt and Dave Thomas - 2019

## Foreword

Programming is about trying to make the future less painful. It's about making things easier for our teammates. It's about getting things wrong and being able to bounce back. It's about forming good habits. It's about understanding your toolset. 

## From the Preface to the First Edition

The word pragmatic comes from the Latin pragmaticus—“skilled in business”—which in turn is derived from the Greek πραγματικός, meaning “fit for use.”

You shouldn’t be wedded to any particular technology, but have a broad enough background and experience base to allow you to choose good solutions in particular situations.

There is no point in developing software unless you care about doing it well.

Think about what you’re doing while you’re doing it.

We who cut mere stones must always be envisioning cathedrals.

“Kaizen” is a Japanese term that captures the concept of continuously making many small improvements.

## Chapter 1 A Pragmatic Philosophy

### 1 It’s your Life

> I’m not in this world to live up to your expectations and you’re not in this world to live up to mine. 
> — Bruce Lee

Does your work environment suck? Is your job boring? Try to fix it. But don’t try forever. As Martin Fowler says, “you can change your organization or change your organization.


### 2 The Cat Ate My Source Code

> The greatest of all weaknesses is the fear of appearing weak. 
> — J.B. Bossuet, Politics from Holy Writ, 1709

Take Responsibility. Responsibility is something you actively agree to.











I’m not in this world to live up to your expectations and you’re not in this world to live up to mine.
Bruce Lee

Does your work environment suck? Is your job boring? Try to fix it. But don’t try forever. As Martin Fowler says, “you can change your organization or change your organization.

 The greatest of all weaknesses is the fear of appearing weak.
J.B. Bossuet, Politics from Holy Writ, 1709

TAKE RESPONSIBILITY
Responsibility is something you actively agree to.

When disorder increases in software, we call it “software rot.” Some folks might call it by the more optimistic term, “technical debt,” with the implied notion that they’ll pay it back someday. They probably won’t.


Don’t leave “broken windows’’ (bad designs, wrong decisions, or poor code) unrepaired. Fix each one as soon as it is discovered. If there is insufficient time to fix it properly, then board it up. Perhaps you can comment out the offending code, or display a “Not Implemented” message, or substitute dummy data instead. Take some action to prevent further damage and to show that you’re on top of the situation.

don’t cause collateral damage just because there’s a crisis of some sort. One broken window is one too many. One broken window—a badly designed piece of code, a poor management decision that the team must live with for the duration of the project—is all it takes to start the decline. 

if you find yourself on a project where the code is pristinely beautiful—cleanly written, well designed, and elegant—you will likely take extra special care not to mess it up

People find it easier to join an ongoing success. Show them a glimpse of the future and you’ll get them

Rear Admiral Dr. Grace Hopper: “It’s easier to ask forgiveness than it is to get permission.’’

Keep an eye on the big picture. Constantly review what’s happening around you, not just what you personally are doing.

Striving to better, oft we mar what’s well. Shakespeare, King Lear 1.4

As Ed Yourdon described in an article in IEEE Software, When good-enough software is best [You95], you can discipline yourself to write software that’s good enough—good enough for your users, for future maintainers, for your own peace of mind. You’ll find that you are more productive and your users are happier

Great software today is often preferable to the fantasy of perfect software tomorrow. If you give your users something to play with early, their feedback will often lead you to a better eventual solution

Don’t spoil a perfectly good program by overembellishment and overrefinement. Move on, and let your code stand in its own right for a while.

Your knowledge and experience are your most important day-to-day professional assets.

It’s not a good idea to invest all of your money in high-risk stocks that might collapse suddenly, nor should you invest all of it conservatively and miss out on possible opportunities.

Don’t forget the human side of the equation, as that requires an entirely different skill set (we ironically call these soft skills, but they are actually quite hard to master).
The process of learning will expand your thinking, opening you to new possibilities and new ways of doing things

Critically Analyze What You Read and Hear

Don’t stop with first-order thinking (what will happen next), but use second-order thinking: what will happen after that?

Treat English (or whatever your native tongue may be) as just another programming language. Write natural language as you would write code: honor the DRY principle, ETC, automation, and so on.

“The meaning of your communication is the response you get.” Continuously improve your knowledge of your audience as you communicate.

Make what you’re saying relevant in time, as well as in content. Sometimes all it takes is the simple question, “Is this a good time to talk about...?’’

Your ideas are important. They deserve a good-looking vehicle to convey them to your audience… ...Any chef (or watcher of the Food Network) will tell you that you can slave in the kitchen for hours only to ruin your efforts with poor presentation.

There’s one technique that you must use if you want people to listen to you: listen to them

The code already shows how it is done, so commenting on this is redundant—and is a violation of the DRY principle.

The next time you have to give a presentation… ...If appropriate, talk to your audience afterward and see how accurate your assessment of their needs was.

Don’t flame or act like a troll unless you want it to come back and haunt you later. If you wouldn’t say it to someone’s face, don’t say it online.

email and social media posts are forever. Try to give the same attention and care to email as you would to any written memo or report.

Good Design Is Easier to Change Than Bad Design… ...As far as we can tell, every design principle out there is a special case of ETC. Why is decoupling good? Because by isolating concerns we make each easier to change. ETC. Why is the single responsibility principle useful? Because a change in requirements is mirrored by a change in just one module. ETC. Why is naming important? Because good names make code easier to read, and you have to read it to change it. ETC!

try to make what you write replaceable. That way, whatever happens in the future, this chunk of code won’t be a roadblock… ...It’s really just thinking about keeping code decoupled and cohesive.

Most people assume that maintenance begins when an application is released, that maintenance means fixing bugs and enhancing features. We think these people are wrong. Programmers are constantly in maintenance mode. Our understanding changes day by day.

DRY is about the duplication of knowledge, of intent. It’s about expressing the same thing in two different places, possibly in two totally different ways.

For internal APIs, look for tools that let you specify the API in some kind of neutral format. These tools will typically generate documentation, mock APIs, functional tests, and API clients,

foster an environment where it’s easier to find and reuse existing stuff than to write it yourself. If it isn’t easy, people won’t do it. And if you fail to reuse, you risk duplicating knowledge.

Two or more things are orthogonal if changes in one do not affect any of the others. In a well- designed system, the database code will be orthogonal to the user interface: you can change the interface without affecting the database, and swap databases without changing the interface.

When components are isolated from one another, you know that you can change one without having to worry about the rest. As long as you don’t change that component’s external interfaces, you can be confident that you won’t cause problems that ripple through the entire system.
You get two major benefits if you write orthogonal systems: increased productivity and reduced risk.

Once you have your components mapped out, ask yourself: If I dramatically change the requirements behind a particular function, how many modules are affected? In an orthogonal system, the answer should be “one.’’

Also ask yourself how decoupled your design is from changes in the real world… ...Don’t rely on the properties of things you can’t control. 

An orthogonally designed and implemented system is easier to test. Because the interactions between the system’s components are formalized and limited, more of the system testing can be performed at the individual module level.

With DRY, you’re looking to minimize duplication within a system, whereas with orthogonality you reduce the interdependency among the system’s components. It may be a clumsy word, but if you use the principle of orthogonality, combined closely with the DRY principle, you’ll find that the systems you develop are more flexible, more understandable, and easier to debug, test, and maintain. 

Nothing is more dangerous than an idea if it’s the only one you have. Emil-Auguste Chartier (Alain), Propos sur la religion, 1938

Nothing is forever—and if you rely heavily on some fact, you can almost guarantee that it will change

The problem is that critical decisions aren’t easily reversible.

Requirements, users, and hardware change faster than we can get the software developed

The mistake lies in assuming that any decision is cast in stone— and in not preparing for the contingencies that might arise. Instead of carving decisions in stone, think of them more as being written in the sand at the beach. A big wave can come along and wipe them out at any time. 

### 12 Tracer bullets

Look for the important requirements, the ones that define the system. Look for the areas where you have doubts, and where you see the biggest risks. Then prioritize your development so that these are the first areas you code. 

Tracer development is consistent with the idea that a project is never finished: there will always be changes required and functions to add. It is an incremental approach.

Prototyping generates disposable code. Tracer code is lean but complete, and forms part of the skeleton of the final system. Think of prototyping as the reconnaissance and intelligence gathering that takes place before a single tracer bullet is fired.

### 13 Prototypes and Post-it Notes

We build software prototypes... ...to analyze and expose risk, and to offer chances for correction at a greatly reduced cost.

If you find yourself in an environment where you cannot give up the details, then you need to ask yourself if you are really building a prototype at all. Perhaps a tracer bullet style of development would be more appropriate in this case

Prototyping is a learning experience. Its value lies not in the code produced, but in the lessons learned. That’s really the point of prototyping.

### 14 Domain Languages

> The limits of language are the limits of one’s world. --Ludwig Wittgenstein

One of the reasons that the classic gather requirements, design, code, ship approach doesn’t work is that it is anchored by the concept that we know what the requirements are. But we rarely do. Your business users will have a vague idea of what they want to achieve, but they neither know nor care about the details. That’s part of our value: we intuit intent and convert it to code.

Don’t spend more effort than you save. Writing a domain language adds some cost to your project, and you’ll need to be convinced that there are offsetting savings (potentially in the long term).

### 15 Estimating

By learning to estimate, and by developing this skill to the point where you have an intuitive feel for the magnitudes of things, you will be able to show an apparent magical ability to determine their feasibility.

The first question you have to ask yourself when someone asks you for an estimate is the context in which your answer will be taken. Do they need high accuracy, or are they looking for a ballpark figure?

| Duration      | Quote estimate in                    |
| ------------- |:------------------------------------:|
| 1–15 days     | Days                                 |
| 3–6	weeks     | Weeks                                |
| 8–20	weeks    | Months                               |
| 20+	weeks     | Think hard before giving an estimate |  	

Choose the units of your answer to reflect the accuracy you intend to convey.

A basic estimating trick that always gives good answers: ask someone who’s already done it

The first part of any estimation exercise is building an understanding of what’s being asked... ...you need to have a grasp of the scope of the domain.
