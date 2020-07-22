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

Never store a phone number in a numeric field.

### Topic 39 Algorithm Speed

The larger the input, the longer the running time or the more memory used.

The Big-O notation, written _O()_, is a mathematical way of dealing with approximations... ...Think of the _O()_ as meaning _on the order of_.

Big-O is never going to give you actual numbers for time or memory or whatever: it simply tells you how these values will change as the input changes.

- _O(1)_ Constant (access element in array, simple statements)
- _O(lg n)_ Logarithmic (binary search). The base of the logarithm doesn’t matter, so this is equivalent _O(log n)_
- _O(n)_ Linear (sequential search)
- _O(nlg n)_ Worse than linear, but not much worse. (Average runtime of quicksort, heapsort)
- _O(n^2)_ Square law (selection and insertion sorts)
- _O(n^3)_ Cubic (multiplication of two matrices)
- _O(C^n)_ Exponential (traveling salesman problem, set partitioning)

Figure 3 - Runtimes of various algorithms
TODO: ADD FIGURE 3

_Simple loops_
If a simple loop runs from _1_ to _n_, then the algorithm is likely to be _O(n)_—time increases linearly with .

_Nested loops_
If you nest a loop inside another, then your algorithm becomes _O(m x n)_, where   and   are the two loops’ limits. This commonly occurs in simple sorting algorithms, such as bubble sort... ...Such sorting algorithms tend to be _O(n^2)_.

_Binary chop_
If your algorithm halves the set of things it considers each time around the loop, then it is likely to be logarithmic, _O(lg n)_.


_Divide and conquer_
Algorithms that partition their input work on the two halves independently, and then combine the result can be _O(nlg n)_. Although technically _O(n^2)_, because its behavior degrades when it is fed sorted input, the average runtime of quicksort is _O(nlg n)_.

_Combinatoric_
Whenever algorithms start looking at the permutations of things, their running times may get out of hand. This is because permutations involve factorials... ...Often, heuristics are used to reduce the running times of these types of algorithms in particular problem domains.

Estimate the Order of Your Algorithms... ...If you’re not sure how long your code will take, or how much memory it will use, try running it, varying the input record count or whatever is likely to impact the runtime. Then plot the results. You should soon get a good idea of the shape of the curve.

Try to cover both the theoretical and practical bases. After all this estimating, the only timing that counts is the speed of your code, running in the production environment, with real data.

Best Isn’t Always Best. You also need to be pragmatic about choosing appropriate algorithms—the fastest one is not always the best for the job.

### Topic 40 Refactoring

As a program evolves, it will become necessary to rethink earlier decisions and rework portions of the code. This process is perfectly natural. Code needs to evolve; it’s not a static thing.

Rather than construction, software is more like _gardening_—it is more organic than concrete. You plant many things in a garden according to an initial plan and conditions... ...You constantly monitor the health of the garden, and make adjustments as needed.

_Refactoring_ is defined by Martin Fowler as a: 
> disciplined technique for restructuring an existing body of code, altering its internal structure without changing its external behavior.

In order to guarantee that the external behavior hasn’t changed, you need good, automated unit testing that validates the behavior of the code.

Anything at all strikes you as being "wrong," _don’t hesitate to change it_. There’s no time like the present.

Things may cause code to qualify for refactoring:

- _Duplication_ You’ve discovered a violation of the DRY principle.

- _Nonorthogonal design_ You’ve discovered something that could be made more orthogonal.

- _Outdated knowledge_ Things change, requirements drift, and your knowledge of the problem increases. Code needs to keep up.

- _Usage_ As the system gets used by real people under real circumstances, you realize some features are now more important than previously thought, and “must have” features perhaps weren’t.

- _Performance_ You need to move functionality from one area of the system to another to improve performance.

- _The Tests Pass_ Yes. Seriously. We did say that refactoring should be a small scale activity, backed up by good tests. So when you’ve added a small amount of code, and that one extra test passes, you now have a great opportunity to dive in and tidy up what you just wrote.

Fail to refactor now, and there’ll be a far greater time investment to fix the problem down the road—when there are more dependencies to reckon with. Will there be more time available then? Nope.

Refactoring as "a growth." Removing it requires invasive surgery. You can... ...take it out while it is still small. Or, you could wait while it grows and spreads—but removing it then will be both more expensive and more dangerous. Wait even longer, and you may lose the patient entirely.

Refactoring, as with most things, is easier to do while the issues are small, as an ongoing activity while coding.

Refactoring is redesign. Anything that you or others on your team designed can be redesigned in light of new facts, deeper understandings, changing requirements, and so on. 

Martin Fowler... ...tips on how to refactor without doing more harm than good:
1. Don’ttrytorefactorandaddfunctionalityatthesametime.
2. Makesureyouhavegoodtestsbeforeyoubeginrefactoring. Run the tests as often as possible.
3. Takeshort,deliberatesteps:moveafieldfromoneclasstoanother, split a method, rename a variable. Refactoring often involves making many localized changes that result in a larger-scale change.

Next time you see a piece of code that isn’t quite as it should be, fix it. Manage the pain: if it hurts now, but is going to hurt even more later, you might as well get it over with. RememberNext time you see a piece of code that isn’t quite as it should be, fix it. Manage the pain: if it hurts now, but is going to hurt even more later, you might as well get it over with. Remember: don’t live with broken windows.

### Topic 41 Test to Code

Testing Is Not About Finding Bugs... ...the major benefits of testing happen when you think about and write the tests, not when you run them.

A Test Is the First User of Your Code... ...testing is vital feedback that guides your coding.

If you think about testing boundary conditions and how that will work before you start coding, you may well find the patterns in the logic that'll simplify the function. If you think about the error conditions you’ll need to test, you’ll structure your function accordingly.

Test-Driven Development... ...The basic cycle of TDD is:
1. Decide on a small piece of functionality you want to add.
2. Write a test that will pass once that functionality is implemented.
3. Run all tests. Verify that the only failure is the one you just wrote.
4. Write the smallest amount of code needed to get the test to pass, and verify that the tests now run cleanly.
5. Refactor your code: see if there is a way to improve on what you just wrote (the test or the function). Make sure the tests still pass when you’re done.

However... ...people become slaves to TDD in a number of ways:... ...They have lots of redundant tests... ...Their designs tend to start at the bottom and work their way up.

Practice TDD. But, if you do, don’t forget to stop every now and then and look at the big picture. It is easy to become seduced by the green "tests passed" message, writing lots of code that doesn’t actually get you closer to a solution.

TDD: You Need To Know Where You're Going... ...When you can’t comprehend the whole problem, take small steps, one test at a time. However, this approach can mislead you, encouraging you to focus on and endlessly polish the easy problems while ignoring the real reason you’re coding.

Bottom-Up vs. Top-Down... ...Neither school actually works, because both ignore one of the most important aspects of software development: we don’t know what we’re doing when we start. The top-down folks assume they can express the whole requirement up front: they can’t. The bottom- up folks assume they can build a list of abstractions which will take them eventually to a single top-level solution, but how can they decide on the functionality of layers when they don’t know where they are heading?

The only way to build software is incrementally. Build small pieces of end-to-end functionality, learning about the problem as you go.

Tests can definitely help drive development. But, as with every drive, unless you have a destination in mind, you can end up going in circles.

We need to build testability into the software from the very beginning, and test each piece thoroughly before trying to wire them together.

A software unit test is code that exercises a module.

We want to write test cases that ensure that a given unit honors its contract... ...We want to test that the module delivers the functionality it promises, over a wide range of test cases and boundary conditions.

Above all, we want to avoid creating a "time bomb"—something that sits around unnoticed and blows up at an awkward moment later in the project. 

To test a piece of software once it has been deployed... ...Log files containing trace messages are one such mechanism. Log messages should be in a regular, consistent format.

All software you write _will_ be tested—if not by you and your team, then by the eventual users.

You really only have a few choices:
- Test First 
- Test During 
- Test Never
Test First, including Test-Driven Design, is probably your best choice in most circumstances, as it ensures that testing happens. But sometimes that’s not as convenient or useful, so Test During coding can be a good fallback, where you write some code, fiddle with it, write the tests for it, then move on to the next bit. The worst choice is often called "Test Later," but who are you kidding? "Test Later" really means "Test Never."

Treat test code with the same care as any production code. Keep it decoupled, clean, and robust. Don’t rely on unreliable things.

Make no mistake, testing is part of programming. It’s not something left to other departments or staff. Testing, design, coding—it’s all programming.

### Topic 42 Property-Based Testing

> Доверяй, но проверяй (Trust, but verify)
> — Russian proverb
 
If you write the original code and you write the tests, is it possible that an incorrect assumption could be expressed in both? The code passes the tests, because it does what it is supposed to based on your understanding.

Code _invariants_, things that remain true about some piece of state when it’s passed through a function.

Use Property-Based Tests to Validate Your Assumptions.

When a property-based test fails, find out what parameters it was passing to the test function, and then use those values to create a separate, regular, unit test. That unit test does two things for you. First, it lets you focus in on the problem without all the additional calls being made into your code by the property-based testing framework. Second, that unit test acts as a _regression test_. Because property-based tests generate random values that get passed to your test, there’s no guarantee that the same values will be used the next time you run tests. Having a unit test that forces those values to be used ensures that this bug won’t slip through.

### Topic 43 Stay Safe Out There

> Good fences make good neighbors.
> — Robert Frost, Mending Wall

Analyze the code for ways it can go wrong and add those to your test suite.

You need to consider how an external actor could deliberately screw up the system.

Security through obscurity just doesn’t work.

Pragmatic Programmers have a healthy amount of paranoia. We know we have faults and limitations, and that external attackers will seize on _any_ opening we leave to compromise our systems.

Minimize Attack Surface Area... ...is the sum of all access points where an attacker can enter data, extract data, or invoke execution of a service.

Less code means fewer bugs, fewer opportunities for a crippling security hole. Simpler, tighter, less complex code is easier to reason about, easier to spot potential weaknesses.

Never trust data from an external entity, always sanitize it before passing it on to a database, view rendering, or other processing.

Keep the number of authorized users at an absolute minimum. Cull unused, old, or outdated users and services.

Don’t give away information. Make sure that the data you report is appropriate for the authorization of that user.

> Every program and every privileged user of the system should operate using the least amount of privilege necessary to complete the job.
> — Jerome Saltzer, Communications of the ACM, 1974.

The default settings on your app, or for your users on your site, should be the _most_ secure values.

Don’t check in secrets, API keys, SSH keys, encryption passwords or other credentials alongside your source code in version control.

Apply Security Patches Quickly.

Rely only on reliable things: well- vetted, thoroughly examined, well-maintained, frequently updated, preferably open source libraries and frameworks.

### Topic 44 Naming Things

> The beginning of wisdom is to call things by their proper name.
> — Confucius

What’s in a name? When we’re programming, the answer is “everything!”... ...we’re constantly creating new things and bestowing names on them. And those names are very, very important, because they reveal a lot about your intent and belief.

Your brain treats written words as something to be respected. We need to make sure the names we use live up to this.

When naming things, you’re constantly looking for ways of clarifying what you mean, and that act of clarification will lead you to a better understanding of your code as _you write it_.

Honor the local culture... ...Get a sense of what the community expects.

Encourage a lot of communication. If everyone pair programs, and pairs switch frequently, then jargon will spread osmotically.

No matter how much effort you put in up front, things change.

If you aren’t vigilant about updating names as you go, you can quickly descend into a nightmare much worse than meaningless names: _misleading_ names.
 
When you spot a problem, fix it—right here and now. When you see a name that no longer expresses the intent, or is misleading or confusing, fix it.  
 
If for some reason you can’t change the now-wrong name, then you’ve got a bigger problem: an ETC violation. Fix that first, then change the offending name. Make renaming easy, and do it often. Otherwise you’ll have to explain to the new folks on the team that `getData` really writes data to a file, and you’ll have to do it with a straight face.

## Chapter 8 Before the Project

### Topic 45 The Requirements Pit

> Perfection is achieved, not when there is nothing left to add but when there is nothing left to take away...
> — Antoine de St. Exupery, Wind, Sand, and Stars, 1939
 
No One Knows Exactly What They Want.

The real world is messy, conflicted, and unknown. In that world, exact specifications of anything are rare, if not downright impossible.

Our job is to help people understand what they want. In fact, that’s probably our most valuable attribute.

Your role in this is to interpret what the client says and to feed back to them the implications. This is both an intellectual process and a creative one.

Requirements Are Learned in a Feedback Loop.

Sometimes you honestly won’t know enough about the domain to be as specific as that. In those cases, Pragmatic Programmers rely on the "is this what you meant?" school of feedback. We produce mockups and prototypes, and let the client play with them.

The Pragmatic Programmer looks at _all_ of the project as a requirements gathering exercise. That’s why we prefer short iterations; ones that end with direct client feedback. This keeps us on track, and makes sure that if we _do_ go in the wrong direction, the amount of time lost is minimized.

For getting inside your clients’ heads... ...become a client... ...As well as giving you insight into how the system will _really_ be used... ...helps build trust and establishes a basis for communication with your clients.

Policy Is Metadata.

Implement the general case, with the policy information as an example of the type of thing the system needs to support.

Successful tools adapt to the hands that use them. Successful requirements gathering takes this into account. And this is why early feedback, with prototypes or tracer bullets, will let your clients say "yes, it does _what_ I want, but not _how_ I want."

The client doesn’t really know what they want up front. So when we take what they say and expand it into what is almost a legal document, we are building an incredibly complex castle on quicksand... ...And... ...the client never reads them.

Giving them a large technical document is like giving the average developer a copy of the _Iliad_ in Homeric Greek and asking them to code the video game from it.

By keeping this statement of requirements short, you’re encouraging developers to ask clarifying questions. You’re enhancing the feedback process between clients and coders before and during the creation of each piece of code.

Another big danger in producing a requirements document is being too specific. Good requirements are abstract.

Requirements are not architecture. Requirements are not design, nor are they the user interface. Requirements are _need_.

Create and maintain a _project glossary_—one place that defines all the specific terms and vocabulary used in a project.

It’s hard to succeed on a project if users and developers call the same thing by different names or, even worse, refer to different things by the same name.

### Topic 46 Solving Impossible Puzzles

Identify the real (not imagined) constraints, and find a solution therein. Some constraints are _absolute_; others are merely _preconceived notions_. Absolute constraints _must_ be honored, however distasteful or stupid they may appear to be... ...some apparent constraints may not be real constraints at all.

The key to solving puzzles is both to recognize the constraints placed on you and to recognize the degrees of freedom you _do_ have, for in those you’ll find your solution.

It’s not whether you think inside the box or outside the box. The problem lies in _finding_ the box—identifying the real constraints.

Categorize and prioritize your constraints... ...identify the most restrictive constraints first, and fit the remaining constraints within them.

> To put it plainly—people who were distracted did better on a complex problem-solving task than people who put in conscious effort.
> — [_Psychology Today_](https://www.psychologytoday.com/us/blog/your-brain-work/201209/stop-trying-solve-problems)

Ask you questions such as:
- Why are you solving this problem?
- What’s the benefit of solving it?
- Are the problems you’re having related to edge cases? Can you eliminate them?
- Is there a simpler, related problem you can solve?

### Topic 47 Working Together

Working closely with users; they are part of your team... ..._pair programming or mob programming:_... ...It’s a powerful way of working together that transcends endless meetings, memos, and overstuffed legalistic documentation prized for weight over usefulness.

> Organizations which design systems are constrained to produce designs which are copies of the communication structures of these organizations.
> — 1967, Melvin Conway

The social structures and communication pathways of the team and the organization will be mirrored in the application, website, or product being developed.

Development teams that include users will produce software that clearly reflects that involvement, and teams that don’t bother will reflect that, too.

_Pair programming_ is one of the practices of eXtreme Programming that has become popular outside of XP itself... ...There are many benefits to pair programming. Different people bring different backgrounds and experience, different problem- solving techniques and approaches, and differing levels of focus and attention to any given problem.

_Mob programming_,... ...It’s an extension of pair programming that involves more than just two developers.

Here are just a few tips to get started:
- Build the code, not your ego. It’s not about who’s brightest; we all have our moments, good and bad.
- Start small. Mob with only 4-5 people, or start with just a few pairs, in short sessions.
- Criticize the code, not the person. “Let’s look at this block” sounds much better than “you’re wrong.”
- Listen and try to understand others’ viewpoints. Different isn’t wrong.
- Conduct frequent retrospectives to try and improve for next time.

### Topic 48 The Essence of Agility

_Agile_ is an adjective: it’s how you do something... ...Agility is your style, not you.

The [Manifesto for Agile Software Development](https://agilemanifesto.org/): 
We are uncovering better ways of developing software by doing it and helping others do it. Through this work we have come to value:
- **Individuals and interactions** over processes and tools
- **Working software** over comprehensive documentation
- **Customer collaboration** over contract negotiation
- **Responding to change** over following a plan
That is, while there is value in the items on the right, we value the items on the left more.

Agility... ...is all about responding to change, responding to the unknowns you encounter after you set out.

The values don’t tell you what to do. They tell you what to look for when you decide for yourself what to do.

Working in an agile way:
1. Work out where you are.
2. Make the smallest meaningful step towards where you want to be.
3. Evaluate where you end up, and fix anything you broke.
Repeat these steps until you’re done. And use them recursively, at every level of everything you do.

Teams should... ....review their process and how well it worked. A team that doesn’t continuously experiment with their process is not an agile team.

To make this whole agile thing work, we need to practice good design, because good design makes things easy to change. And if it’s easy to change, we can adjust, at every level, without any hesitation.
That is agility.











































