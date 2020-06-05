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

### Topic 1 It’s your Life

> I’m not in this world to live up to your expectations and you’re not in this world to live up to mine. 
> — Bruce Lee

Does your work environment suck? Is your job boring? Try to fix it. But don’t try forever. As Martin Fowler says, “you can change your organization or change your organization.


### Topic 2 The Cat Ate My Source Code

> The greatest of all weaknesses is the fear of appearing weak. 
> — J.B. Bossuet, Politics from Holy Writ, 1709

Take Responsibility. Responsibility is something you actively agree to.

### Topic 3 Software Entropy

When disorder increases in software, we call it “software rot.” Some folks might call it by the more optimistic term, “technical debt,” with the implied notion that they’ll pay it back someday. They probably won’t.

Don’t leave “broken windows’’ (bad designs, wrong decisions, or poor code) unrepaired. Fix each one as soon as it is discovered. If there is insufficient time to fix it properly, then board it up. Perhaps you can comment out the offending code, or display a “Not Implemented” message, or substitute dummy data instead. Take some action to prevent further damage and to show that you’re on top of the situation.

Don’t cause collateral damage just because there’s a crisis of some sort. One broken window is one too many. One broken window—a badly designed piece of code, a poor management decision that the team must live with for the duration of the project—is all it takes to start the decline. 

If you find yourself on a project where the code is pristinely beautiful—cleanly written, well designed, and elegant—you will likely take extra special care not to mess it up.

### Topic 4 Stone Soup and Boiled Frogs

People find it easier to join an ongoing success. Show them a glimpse of the future and you’ll get them.

> It’s easier to ask forgiveness than it is to get permission.
> — Rear Admiral Dr. Grace Hopper

Keep an eye on the big picture. Constantly review what’s happening around you, not just what you personally are doing.

### Topic 5 Good-Enough Software

> Striving to better, oft we mar what’s well.
> — Shakespeare, King Lear 1.4

As Ed Yourdon described in an article in IEEE Software, When good-enough software is best, you can discipline yourself to write software that’s good enough—good enough for your users, for future maintainers, for your own peace of mind. You’ll find that you are more productive and your users are happier.

Great software today is often preferable to the fantasy of perfect software tomorrow. If you give your users something to play with early, their feedback will often lead you to a better eventual solution.

Don’t spoil a perfectly good program by overembellishment and overrefinement. Move on, and let your code stand in its own right for a while.

### Topic 6 Your Knowledge Portfolio

> An investment in knowledge always pays the best interest.
> — Benjamin Franklin

Your knowledge and experience are your most important day-to-day professional assets.

It’s not a good idea to invest all of your money in high-risk stocks that might collapse suddenly, nor should you invest all of it conservatively and miss out on possible opportunities.

Don’t forget the human side of the equation, as that requires an entirely different skill set (we ironically call these soft skills, but they are actually quite hard to master).

The process of learning will expand your thinking, opening you to new possibilities and new ways of doing things.

Critically Analyze What You Read and Hear.

Don’t stop with first-order thinking (what will happen next), but use second-order thinking: what will happen after that?

### Topic 7 Communicate!

Treat English (or whatever your native tongue may be) as just another programming language. Write natural language as you would write code: honor the DRY principle, ETC, automation, and so on.

“The meaning of your communication is the response you get.” Continuously improve your knowledge of your audience as you communicate.

Make what you’re saying relevant in time, as well as in content. Sometimes all it takes is the simple question, "Is this a good time to talk about...?"

Your ideas are important. They deserve a good-looking vehicle to convey them to your audience... ...Any chef (or watcher of the Food Network) will tell you that you can slave in the kitchen for hours only to ruin your efforts with poor presentation.

There’s one technique that you must use if you want people to listen to you: listen to them.

The code already shows how it is done, so commenting on this is redundant—and is a violation of the DRY principle.

The next time you have to give a presentation... ...If appropriate, talk to your audience afterward and see how accurate your assessment of their needs was.

Don’t flame or act like a troll unless you want it to come back and haunt you later. If you wouldn’t say it to someone’s face, don’t say it online.

Email and social media posts are forever. Try to give the same attention and care to email as you would to any written memo or report.

## Chapter 2 A Pragmatic Approach

### Topic 8 The Essence of Good Design

Good Design Is Easier to Change Than Bad Design... ...As far as we can tell, every design principle out there is a special case of ETC. Why is decoupling good? Because by isolating concerns we make each easier to change. ETC. Why is the single responsibility principle useful? Because a change in requirements is mirrored by a change in just one module. ETC. Why is naming important? Because good names make code easier to read, and you have to read it to change it. ETC!

Try to make what you write replaceable. That way, whatever happens in the future, this chunk of code won’t be a roadblock...  ...It’s really just thinking about keeping code decoupled and cohesive.

### Topic 9 DRY—The Evils of Duplication

Most people assume that maintenance begins when an application is released, that maintenance means fixing bugs and enhancing features. We think these people are wrong. Programmers are constantly in maintenance mode. Our understanding changes day by day.

DRY is about the duplication of knowledge, of intent. It’s about expressing the same thing in two different places, possibly in two totally different ways.

For internal APIs, look for tools that let you specify the API in some kind of neutral format. These tools will typically generate documentation, mock APIs, functional tests, and API clients,

Foster an environment where it’s easier to find and reuse existing stuff than to write it yourself. If it isn’t easy, people won’t do it. And if you fail to reuse, you risk duplicating knowledge.

### Topic 10 Orthogonality

Two or more things are orthogonal if changes in one do not affect any of the others. In a well- designed system, the database code will be orthogonal to the user interface: you can change the interface without affecting the database, and swap databases without changing the interface.

When components are isolated from one another, you know that you can change one without having to worry about the rest. As long as you don’t change that component’s external interfaces, you can be confident that you won’t cause problems that ripple through the entire system. You get two major benefits if you write orthogonal systems: increased productivity and reduced risk.

Once you have your components mapped out, ask yourself: If I dramatically change the requirements behind a particular function, how many modules are affected? In an orthogonal system, the answer should be "one."

Ask yourself how decoupled your design is from changes in the real world... ...Don’t rely on the properties of things you can’t control.

An orthogonally designed and implemented system is easier to test. Because the interactions between the system’s components are formalized and limited, more of the system testing can be performed at the individual module level.

With DRY, you’re looking to minimize duplication within a system, whereas with orthogonality you reduce the interdependency among the system’s components. It may be a clumsy word, but if you use the principle of orthogonality, combined closely with the DRY principle, you’ll find that the systems you develop are more flexible, more understandable, and easier to debug, test, and maintain. 

### Topic 11 Reversibility

> Nothing is more dangerous than an idea if it’s the only one you have.
> — Emil-Auguste Chartier (Alain), Propos sur la religion, 1938

Nothing is forever—and if you rely heavily on some fact, you can almost guarantee that it will change.

The problem is that critical decisions aren’t easily reversible.

Requirements, users, and hardware change faster than we can get the software developed

The mistake lies in assuming that any decision is cast in stone— and in not preparing for the contingencies that might arise. Instead of carving decisions in stone, think of them more as being written in the sand at the beach. A big wave can come along and wipe them out at any time. 

### Topic 12 Tracer bullets

Look for the important requirements, the ones that define the system. Look for the areas where you have doubts, and where you see the biggest risks. Then prioritize your development so that these are the first areas you code. 

Tracer development is consistent with the idea that a project is never finished: there will always be changes required and functions to add. It is an incremental approach.

Prototyping generates disposable code. Tracer code is lean but complete, and forms part of the skeleton of the final system. Think of prototyping as the reconnaissance and intelligence gathering that takes place before a single tracer bullet is fired.

### Topic 13 Prototypes and Post-it Notes

We build software prototypes... ...to analyze and expose risk, and to offer chances for correction at a greatly reduced cost.

If you find yourself in an environment where you cannot give up the details, then you need to ask yourself if you are really building a prototype at all. Perhaps a tracer bullet style of development would be more appropriate in this case

Prototyping is a learning experience. Its value lies not in the code produced, but in the lessons learned. That’s really the point of prototyping.

### Topic 14 Domain Languages

> The limits of language are the limits of one’s world.
> — Ludwig Wittgenstein

One of the reasons that the classic gather requirements, design, code, ship approach doesn’t work is that it is anchored by the concept that we know what the requirements are. But we rarely do. Your business users will have a vague idea of what they want to achieve, but they neither know nor care about the details. That’s part of our value: we intuit intent and convert it to code.

don’t spend more effort than you save. Writing a domain language adds some cost to your project, and you’ll need to be convinced that there are offsetting savings (potentially in the long term).

### Topic 15 Estimating

By learning to estimate, and by developing this skill to the point where you have an intuitive feel for the magnitudes of things, you will be able to show an apparent magical ability to determine their feasibility.

The first question you have to ask yourself when someone asks you for an estimate is the context in which your answer will be taken. Do they need high accuracy, or are they looking for a ballpark figure?

| Duration      | Quote estimate in                    |
| ------------- |:------------------------------------:|
| 1–15 days     | Days                                 |
| 3–6	weeks     | Weeks                                |
| 8–20	weeks   | Months                               |
| 20+	weeks     | Think hard before giving an estimate |  	

Choose the units of your answer to reflect the accuracy you intend to convey.

A basic estimating trick that always gives good answers: ask someone who’s already done it

The first part of any estimation exercise is building an understanding of what’s being asked... ...you need to have a grasp of the scope of the domain.

_Program Evaluation Review Technique_, or PERT. Every PERT task has an optimistic, a most likely, and a pessimistic estimate. The tasks are arranged into a dependency network, and then you use some simple statistics to identify likely best and worst times for the overall project.

To determine the timetable for a project is by gaining experience on that same project... ...practice incremental development, repeating the following steps with very thin slices of functionality:

- Check requirements
- Analyze risk (and prioritize riskiest items earlier) 
- Design, implement, integrate
- Validate with the users

... ...That’s also how the old joke says to eat an elephant: one bite at a time. 

## Chapter 3 The Basic Tools

Every maker starts their journey with a basic set of good-quality tools.

Tools amplify your talent. The better your tools, and the better you know how to use them, the more productive you can be. Start with a basic set of generally applicable tools. As you gain experience, and as you come across special requirements, you’ll add to this basic set.

Always be on the lookout for better ways of doing things.

Let need drive your acquisitions.

### Topic 16 The Power of Plain Text

As Pragmatic Programmers, our base material isn’t wood or iron, it’s knowledge.

_Plain text_ is made up of printable characters in a form that conveys information.

Human-readable forms of data, and self-describing data, will outlive all other forms of data and the applications that created them. Period. As long as the data survives, you will have a chance to be able to use it—potentially long after the original application that wrote it is defunct.

All software becomes legacy software as soon as it’s written.

You need to ensure that all parties can communicate using a common standard. Plain text is that standard.

### Topic 17 Shell Games

Every woodworker needs a good, solid, reliable workbench, somewhere to hold work pieces at a convenient height while they’re being shaped. The workbench becomes the center of the woodshop, the maker returning to it time and time again as a piece takes shape.
For a programmer manipulating files of text, that workbench is the command shell. From the shell prompt, you can invoke your full repertoire of tools, using pipes to combine them in ways never dreamt of by their original developers.

If you do all your work using GUIs, you are missing out on the full capabilities of your environment.

A benefit of GUIs is WYSIWYG— what you see is what you get. The disadvantage is WYSIAYG— what you see is all you get.

You’ll spend a lot of time living in one of these shells. Be like a hermit crab and make it your own home.

### Topic 18 Power Editing

By becoming fluent, you no longer have to think about the mechanics of editing... ...Your thoughts will flow, and your programming will benefit.

What counts as being fluent? Here’s the challenge list:

- When editing text, move and make selections by character, word, line, and paragraph.
- When editing code, move by various syntactic units (matching delimiters, functions, modules, ...).
- Reindent code following changes.
- Comment and uncomment blocks of code with a single command.
- Undo and redo changes.
- Split the editor window into multiple panels, and navigate between them.
- Navigate to a particular line number. Sort selected lines.
- Search for both strings and regular expressions, and repeat previous searches.
- Temporarily create multiple cursors based on a selection or on a pattern match, and edit the text at each in parallel.
- Display compilation errors in the current project. 
- Run the current project’s tests.

Can you do all this without using a mouse/trackpad?
You might say that your current editor can’t do some of these things. Maybe it’s time to switch?

Every time you find yourself doing something repetitive, get into the habit of thinking “there must be a better way.” Then find it.

Edit using just the keyboard... ...as you learn to do stuff without moving your hands away from the home position, you’ll find that your editing becomes faster and more fluent than it ever was in the past.

### Topic 19 Version Control

> Progress, far from consisting in change, depends on retentiveness. Those who cannot remember the past are condemned to repeat it.
> — George Santayana, Life of Reason

A good VCS will let you track changes, answering questions such as: Who made changes in this line of code? What’s the difference between the current version and last week’s? How many lines of code did we change in this release? Which files get changed most often? This kind of information is invaluable for bug-tracking, audit, performance, and quality purposes.

Always. Even if you are a single-person team on a one-week project. Even if it’s a “throw-away’’ prototype. Even if the stuff you’re working on isn’t source code. Make sure that everything is under version control.

### Topic 20 Debugging

> It is a painful thing to look at your own trouble and know that you yourself and no one else has made it.
> — Sophocles, Ajax

Unfortunately, modern computer systems are still limited to doing what you tell them to do, not necessarily what you want them to do. No one writes perfect software, so it’s a given that debugging will take up a major portion of your day.

It doesn’t really matter whether the bug is your fault or someone else’s. It is still your problem.

> The easiest person to deceive is one’s self.
> — Edward Bulwer-Lytton, The Disowned.

Don’t waste a single neuron on the train of thought that begins “but that can’t happen” because quite clearly it can, and has.

Beware of myopia when debugging. Resist the urge to fix just the symptoms you see... ...Always try to discover the root cause of a problem, not just this particular appearance of it.

Artificial tests... ...don’t exercise enough of an application. You must brutally test both boundary conditions and realistic end-user usage patterns. You need to do this systematically.

Once you think you know what is going on, it’s time to find out what the program thinks is going on.

The best way to start fixing a bug is to make it reproducible.

Read the Damn Error Message... ...’nuf said.

The Binary Chop... ...(sometimes called a binary search)... ...it’s faster to use a divide and conquer approach... ...When you’re facing a massive stacktrace and you’re trying to find out exactly which function mangled the value in error, you do a chop by choosing a stack frame somewhere in the middle and seeing if the error is manifest there. If it is, then you know to focus on the frames before, otherwise the problem is in the frames after. Chop again.

A very simple but particularly useful technique for finding the cause of a problem is simply to explain it to someone else... ...but in explaining the problem to another person you must explicitly state things that you may take for granted when going through the code yourself. By having to verbalize some of these assumptions, you may suddenly gain new insight into the problem.

Remember, if you see hoof prints, think horses—not zebras. 

The amount of surprise you feel when something goes wrong is proportional to the amount of trust and faith you have in the code being run.

### Topic 21 Text Manipulation

Text manipulation languages are to programming what routers are to woodworking. They are noisy, messy, and somewhat brute force. Make mistakes with them, and entire pieces can be ruined. Some people swear they have no place in the toolbox. But in the right hands, both routers and text manipulation languages can be incredibly powerful and versatile. 

### Topic 22 Engineering Daybooks

Try keeping an engineering daybook. Use paper, not a file or a wiki: there’s something special about the act of writing compared to typing. Give it a month, and see if you’re getting any benefits. If nothing else, it’ll make writing your memoir easier when you’re rich and famous.

## Chapter 4 Pragmatic Paranoia

No one in the brief history of computing has ever written a piece of perfect software. It’s unlikely that you’ll be the first. And unless you accept this as a fact, you’ll end up wasting time and energy chasing an impossible dream.

Knowing that no one writes perfect code, including themselves, Pragmatic Programmers build in defenses against their own mistakes.

We stick to small steps always... ...so we don’t fall off the edge of the cliff.

### Topic 23 Design by Contract

Dealing with computer systems is hard. Dealing with people is even harder.

What is a correct program? One that does no more and no less than it claims to do. Documenting and verifying that claim is the heart of Design by Contract

If all the routine’s preconditions are met by the caller, the routine shall guarantee that all postconditions and invariants will be true when it completes.

Preconditions should not be used to perform things such as user-input validation.

“lazy” code: be strict in what you will accept before you begin, and promise as little as possible in return.

In any programming language, whether it’s functional, object- oriented, or procedural, DBC forces you to think.

Implementing DBC. Simply enumerating what the input domain range is, what the boundary conditions are, and what the routine promises to deliver—or, more importantly, what it doesn’t promise to deliver —before you write the code is a huge leap forward in writing better software. 

By using an assert or DBC mechanism to validate the preconditions, postconditions, and invariants, you can crash early and report more accurate information about the problem.

Be sure not to confuse requirements that are fixed, inviolate laws with those that are merely policies that might change with a new management regime... ...When you find a requirement that qualifies, make sure it becomes a well-known part of whatever documentation you are producing.

How many numbers are in the series 0, 5, 10, 15, ..., 100? 
There are 21 terms in the series. If you said 20, you just experienced a fencepost error (not knowing whether to count the fenceposts or the spaces between them).

### Topic 24 Dead Programs Tell No Lies

If something is starting to go awry with one of our programs, sometimes it is a library or framework routine that catches it first.

All errors give you information. You could convince yourself that the error can’t happen, and choose to ignore it. Instead, Pragmatic Programmers tell themselves that if there is an error, something very, very bad has happened. Don’t forget to Read the Damn Error Message

Crash, Don’t Trash. One of the benefits of detecting problems as soon as you can is that you can crash earlier, and crashing is often the best thing you can do. 

> Defensive programming is a waste of time. Let it crash!
> — Joe Armstrong, inventor of Erlang.

A dead program normally does a lot less damage than a crippled one.

### Topic 25 Assertive Programming

> There is a luxury in self-reproach. When we blame ourselves we feel no one else has a right to blame us.
> — Oscar Wilde, The Picture of Dorian Gray.

Whenever you find yourself thinking “but of course that could never happen,” add code to check  it. The easiest way to do this is with assertions.

Don’t use assertions in place of real error handling.

Turning off assertions when you deliver a program to production is like crossing a high wire without a net because you once made it across in practice. There’s dramatic value, but it’s hard to get life insurance.

### Topic 26 How to Balance Resources

> To light a candle is to cast a shadow...
> — Ursula K. Le Guin, A Wizard of Earthsea.

The function or object that allocates a resource should be responsible for deallocating it.

When in doubt, it always pays to reduce scope.

Whoever allocates a resource should be responsible for deallocating it.

The correct pattern for handling resource deallocation in an environment with exceptions is:

```
thing = allocate_resource()
begin
    process(thing)
finally
    deallocate(thing)
end
```

Because Pragmatic Programmers trust no one, including ourselves, we feel that it is always a good idea to build code that actually checks that resources are indeed freed appropriately.

### Topic 27 Don’t Outrun Your Headlights

We can’t see too far ahead into the future, and the further off- axis you look, the darker it gets. So Pragmatic Programmers have a firm rule: Take Small Steps—Always. Always take small, deliberate steps, checking for feedback and adjusting before proceeding.

What’s a task that’s too big? Any task that requires “fortune telling.”... ...we can only see into the future perhaps one or two steps, maybe a few hours or days at most. Beyond that, you can quickly get past educated guess and into wild speculation.

The more you have to predict what the future will look like, the more risk you incur that you’ll be wrong. Instead of wasting effort designing for an uncertain future, you can always fall back on designing your code to be replaceable.

Making code replaceable will also help with cohesion, coupling, and DRY, leading to a better design overall.

Much of the time, tomorrow looks a lot like today. But don’t count on it.

## Chapter 5 Bend, or Break

Life doesn’t stand still. Neither can the code that we write. In order to keep up with today’s near-frantic pace of change, we need to make every effort to write code that’s as loose—as flexible—as possible. Otherwise we may find our code quickly becoming outdated, or too brittle to fix, and may ultimately be left behind in the mad dash toward the future.

### Topic 28 Decoupling

> When we try to pick out anything by itself, we find it hitched to everything else in the Universe.
> — John Muir, My First Summer in the Sierra.

Coupling is the enemy of change, because it links together things that must change in parallel.

When you’re designing software that you’ll want to change... ...you want it to be flexible. And to be flexible, individual components should be coupled to as few other components as possible.

Tell, Don’t Ask. This principle says that you shouldn’t make decisions based on the internal state of an object and then update that object. Doing so totally destroys the benefits of encapsulation and, in doing so, spreads the knowledge of the implementation throughout the code.

The Law of Demeter LoD says that a method defined in a class C should only call:

- Other instance methods in C
- Its parameters
- Methods in objects that it creates, both on the stack and in the heap 
- Global variables

Anything in a third-party library should be considered volatile, particularly if the maintainers of that library are known to change APIs between releases.

Globally accessible data is an insidious source of coupling between application components. Each piece of global data acts as if every method in your application suddenly gained an additional parameter: after all, that global data is available inside every method.

Reuse should probably not be a primary concern when creating code, but the thinking that goes into making code reusable should be part of your coding routine. When you make code reusable, you give it clean interfaces, decoupling it from the rest of your code. This allows you to extract a method or module without dragging everything else along with it.

Any mutable external resource is global data... ...make sure you always wrap these resources behind code that you control.

If It’s Important Enough to Be Global, Wrap It in an API

Keeping your code shy: having it only deal with things it directly knows about, will help keep your applications decoupled, and that will make them more amenable to change.

### Topic 29 Juggling the Real World

> Things don’t just happen; they are made to happen.
> — John F. Kennedy.

Write applications that respond to events, and adjust what they do based on those events, those applications will work better in the real world... ...four strategies that help.
1. FiniteStateMachines
2. TheObserverPattern
3. Publish/Subscribe
4. ReactiveProgrammingandStreams

A state machine is basically just a specification of how to handle events. It consists of a set of states, one of which is the current state. For each state, we list the events that are significant to that state. For each of those events, we define the new current state of the system.

A pure FSM... ...is an event stream parser. Its only output is the final state. We can beef it up by adding actions that are triggered on certain transitions.

The Observer Pattern. In the observer pattern we have a source of events, called the observable and a list of clients, the observers, who are interested in those events.
An observer registers its interest with the observable, typically by passing a reference to a function to be called. Subsequently, when the event occurs, the observable iterates down its list of observers and calls the function that each passed it. The event is given as a parameter to that call.

The observer pattern has a problem: because each of the observers has to register with the observable, it introduces coupling. In addition, because in the typical implementation the callbacks are handled inline by the observable, synchronously, it can introduce performance bottlenecks. This is solved by the next strategy, Publish/Subscribe.

Publish/Subscribe (pubsub) generalizes the observer pattern, at the same time solving the problems of coupling and performance. In the pubsub model, we have publishers and subscribers. These are connected via channels. The channels are implemented in a separate body of code: sometimes a library, sometimes a process, and sometimes a distributed infrastructure. All this implementation detail is hidden from your code.
Every channel has a name. Subscribers register interest in one or more of these named channels, and publishers write events to them. Unlike the observer pattern, the communication between the publisher and subscriber is handled outside your code, and is potentially asynchronous.

Compared to the observer pattern, pubsub is a great example of reducing coupling by abstracting up through a shared interface (the channel). However, it is still basically just a message passing system.

Streams let us treat events as if they were a collection of data. It’s as if we had a list of events, which got longer when new events arrive. The beauty of that is that we can treat streams just like any other collection: we can manipulate, combine, filter, and do all the other data-ish things we know so well. We can even combine event streams and regular collections. And streams can be asynchronous, which means your code gets the opportunity to respond to events as they arrive.

This is a very powerful abstraction: we no longer need to think about time as being something we have to manage. Event streams unify synchronous and asynchronous processing behind a common, convenient API.

### Topic 30 Transforming Programming

> If you can’t describe what you are doing as a process, you don’t know what you’re.
> — W. Edwards Deming, (attr)

We need to get back to thinking of programs as being something that transforms inputs into outputs. When we do, many of the details we previously worried about just evaporate. The structure becomes clearer, the error handling more consistent, and the coupling drops way down.

Feed raw data in one end and the finished product (information) comes out the other. And we like to think about all code this way.

Programming Is About Code, But Programs Are About Data.

If your background is object- oriented programming, then your reflexes demand that you hide data, encapsulating it inside objects. These objects then chatter back and forth, changing each other’s state. This introduces a lot of coupling, and it is a big reason that OO systems can be hard to change.

Don’t Hoard State; Pass It Around... ...This means that we can greatly reduce coupling: a function can be used (and reused) anywhere its parameters match the output of some other function.

We never pass raw values between transformations. Instead, we wrap them in a data structure (or type) which also tells us if the contained value is valid... ...you can handle checking for errors inside your transformations or outside them.

### Topic 31 Inheritance Tax


> You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.
> — Joe Armstrong

Do you program in an object-oriented language? Do you use inheritance? If so, stop! It probably isn’t what you want to do.

Now we’re faced with a generation of OO developers who use inheritance for one of two reasons: they don’t like typing, or they like types.

Inheritance is coupling. Not only is the child class coupled to the parent, the parent’s parent, and so on, but the code that uses the child is also coupled to all the ancestors.

Don’t Pay Inheritance Tax. The Alternatives are Better... ...Interfaces and protocols, Delegation, Mixins and traits.

Interfaces and protocols give us polymorphism without inheritance.

Inheritance is rarely the answer... ...alternatives to traditional class inheritance:
- Interfaces and protocols
- Delegation 
- Mixins and traits
Each of these methods may be better for you in different circumstances, depending on whether your goal is sharing type information, adding functionality, or sharing methods. 

As with anything in programming, aim to use the technique that best expresses your intent.

### Topic 32 configuration 

When code relies on values that may change after the application has gone live, keep those values external to the app... ...In this way, you’re parameterizing your application; the code adapts to the places it runs.

Wrap the configuration information behind a (thin) API. This decouples your code from the details of the representation of configuration.

Configuration-As-A-Service... ...has a number of benefits:
- Multiple applications can share configuration information, with authentication and access control limiting what each can see
- Configuration changes can be made globally
- The configuration data can be maintained via a specialized UI 
- The configuration data becomes dynamic

If there’s genuine debate about whether a feature should work this way or that, or if it should be the users’ choice, try it out one way and get feedback on whether the decision was a good one.

## Chapter 6 Concurrency

_Concurrency_ is when the execution of two or more pieces of code act as if they run at the same time. _Parallelism_ is when they do run at the same time.

Concurrency is a requirement if you want your application to be able to deal with the real world, where things are asynchronous.

Any time two or more chunks of code hold references to the same piece of mutable data, you have shared state. And Shared State Is _Incorrect State_.  

_Blackboards_... ...are systems which act like a combination of an object store and a smart publish/subscribe broker... ...Used correctly, these types of systems offer a serious amount of decoupling. 	 	

Concurrent and parallel code used to be exotic. Now it is required.

### Topic 33 Breaking Temporal Coupling

There are two aspects of time that are important to us: concurrency (things happening at the same time) and ordering (the relative positions of things in time).

We need to allow for concurrency and to think about decoupling any time or order dependencies. In doing so, we can gain flexibility and reduce any time-based dependencies in many areas of development: workflow analysis, architecture, design, and deployment. The result will be systems that are easier to reason about, that potentially respond faster and more reliably.

Find out what _can_ happen at the same time, and what _must_ happen in a strict order.
 	
Remember the distinction: concurrency is a software mechanism, and parallelism is a hardware concern.

### Topic 34 Shared State Is Incorrect State

You can create a semaphore and then use it to control access to some other resource.

A lot of attention is given to shared memory as a source of concurrency problems, but in fact the problems can pop up _anywhere_ where your application code shares mutable resources: files, databases, external services, and so on. Whenever two or more instances of your code can access some resource at the same time, you’re looking at a potential problem.

Functional languages, with their tendency to make all data immutable, make concurrency simpler. However, they still face the same challenges, because at some point they are forced to step into the real, mutable world.

### Topic 35 Actors and Processes

Actors and processes offer interesting ways of implementing concurrency without the burden of synchronizing access to shared memory.

Actors execute concurrently, asynchronously, and share nothing... ...the code running in the actors is the same.

[Concurrency Actors Example](https://gist.github.com/reymon359/f9a1563d744a4d0d29a3289584c9ae38)

### Topic 36 Blackboards

Use Blackboards to Coordinate Workflow Messaging Systems Can Be Like Blackboards

These messaging systems do far more than simply send data from A to B. In particular, they offer persistence (in the form of an event log) and the ability to retrieve messages through a form of pattern matching. This means you can use them both as a blackboard system and/or as a platform on which you can run a bunch of actors.

These kinds of system can be more troublesome to deploy and manage, as there are more moving parts. To some extent this is offset by the fact that the system is more granular, and can be updated by replacing individual actors, and not the whole system.

## Chapter 7 While You Are Coding

Coding is not mechanical. If it were, all the CASE tools that people pinned their hopes on way back in the early 1980s would have replaced programmers long ago. There are decisions to be made every minute—decisions that require careful thought and judgment if the resulting program is to enjoy a long, accurate, and productive life.

Developers who don’t actively think about their code are programming by coincidence—the code might work, but there’s no particular reason why. 

The major benefits of testing happen when you think about and write the tests, not just when you run them. 

### Topic 37 Listen to Your Lizard Brain

Instincts are simply a response to patterns packed into our nonconscious brain. Some are innate, others are learned through repetition.

As you gain experience as a programmer, your brain is laying down layers of tacit knowledge.

Instincts make you feel, not think.

As a developer, you’ve been trying things and seeing which worked and which didn’t. You’ve been accumulating experience and wisdom. When you feel a nagging doubt, or experience some reluctance when faced with a task, it might be that experience trying to speak to you. Heed it. You may not be able to put your finger on exactly what’s wrong, but give it time and your doubts will probably crystallize into something more solid, something you can address.

Let your instincts contribute to your performance.

First, stop what you’re doing... ...Let the ideas percolate up through the layers of your brain on their own: you can’t force it.

A large part of our job is dealing with existing code, often written by other people. Those people will have different instincts to you, and so the decisions they made will be different. Not necessarily worse; just different... ...When you spot things done in a way that seems strange, jot it down. Continue doing this, and look for patterns. If you can see what drove them to write code that way, you may find that the job of understanding it becomes a lot easier. You’ll be able consciously to apply the patterns that they applied tacitly.
And you might just learn something new along the way.

### Topic 38 Programming by Coincidence

As developers, we also work in minefields. There are hundreds of traps waiting to catch us each day... ...We should avoid programming by coincidence—relying on luck and accidental successes—in favor of _programming deliberately_.

For routines you call, rely only on documented behavior. If you can’t, for whatever reason, then document your assumption well.

[Correlation does not imply causation](https://en.wikipedia.org/wiki/Correlation_does_not_imply_causation)

Don’t assume it, prove it.

Finding an answer that happens to fit is not the same as the right answer.

Don’t Program by Coincidence

Catch and fix errors as early in the development cycle as possible, and create fewer errors to begin with.

Can you explain the code, in detail, to a more junior programmer? If not, perhaps you are relying on coincidences.

Don’t code in the dark.... ...If you’re not sure why it works, you won’t know why it fails.

Proceed from a plan, whether that plan is in your head, on the back of a cocktail napkin, or on a whiteboard.

Rely only on reliable things. Don’t depend on assumptions. If you can’t tell if something is reliable, assume the worst.

Don’t just test your code, but test your assumptions as well. Don’t guess; actually try it. Write an assertion to test your assumptions. If your assertion is right, you have improved the documentation in your code. If you discover your assumption is wrong, then count yourself lucky.

Prioritize your effort. Spend time on the important aspects; more than likely, these are the hard parts. If you don’t have fundamentals or infrastructure correct, brilliant bells and whistles will be irrelevant.

Don’t be a slave to history. Don’t let existing code dictate future code. All code can be replaced if it is no longer appropriate.



















