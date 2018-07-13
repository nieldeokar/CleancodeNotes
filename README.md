# Clean Code Notes
This repo contains notes from book [Clean Code : A Handbook of Agile Software Craftsmanship by Robert C. Martin][1]


### What is clean code ?
**Bjarne Stroustrup** inventor of C++ :  
*I like my code to be elegant and efficient. The logic should be straightforward to make it hard for bugs to hide, the dependencies minimal to ease maintenance, error handling complete according to an articulated strategy, and performance close to optimal so as not to tempt people to make the code messy with unprincipled optimizations. Clean code does one thing well.*  

**Grady Booch** author of Object :  
*Oriented Analysis and Design with Applications Clean code is simple and direct. Clean code reads like well-written prose. Clean code never obscures the designer’s intent but rather is full of crisp abstractions and straightforward lines of control.*  

**Big Dave Thomas** founder of OTI, godfather of the Eclipse strategy :  
*Clean code can be read, and enhanced by a developer other than its original author. It has unit and acceptance tests. It has meaningful names. It provides one way rather than many ways for doing one thing. It has minimal dependencies, which are explicitly defined, and provides a clear and minimal API. Code should be literate since depending on the language, not all necessary information can be expressed clearly in code alone.*

**Michael Feathers** author of Working Effectively with Legacy Code :  
*I could list all of the qualities that I notice in clean code, but there is one overarching quality that leads to all of them. Clean code always looks like it was written by someone who cares. There is nothing obvious that you can do to make it better. All of those things were thought about by the code’s author, and if you try to imagine improvements, you’re led back to where you are, sitting in appreciation of the code someone left for you—code left by someone who cares deeply about the craft.*  

**Ron Jeffries** author of Extreme Programming Installed and Extreme Programming Adventures in C# :  
*In recent years I begin, and nearly end, with Beck’s rules of simple code. In priority order, simple code:  
• Runs all the tests;  
• Contains no duplication;  
• Expresses all the design ideas that are in the
system;  
• Minimizes the number of entities such as classes,
methods, functions, and the like.*  

**Ward Cunningham**  inventor of Wiki, inventor of Fit, coinventor of eXtreme Programming. Motive force behind Design Patterns. Smalltalk and OO thought leader. The godfather of all those who care about code :  
*You know you are working on clean code when each routine you read turns out to be pretty much what you expected. You can call it beautiful code when the code also makes it look like the language was made for the problem.*  

## Chapter 2 : meaningful Names  

1. Use Intention-Revealing Names  
2. Avoid Disinformation  
3. Make Meaningful Distinctions : Noise words  
4. Use Pronounceable Names  
5. Use Searchable Names  
6. Avoid Encodings  
7. Hungarian Notation   
8. Class Names :
Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in the name of a class. A class name should not be a verb.  
9. Don’t Pun :
Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.  

## Chapter 3 : Function

1. The first rule of functions is that they should be small. The second rule of functions is that *they should be smaller than that.*  
2. FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.  
3. Functions should either do something or answer something, but not both.  
4. Function Arguments
The ideal number of arguments for a function is zero (*niladic*). Next comes one (*monadic*), followed closely by two (dyadic). Three arguments (*triadic*) should be avoided where possible. More than three (*polyadic*) requires very special justification and then shouldn’t be used anyway.  
5. Anything that forces you to check the function signature is equivalent to a double-take. It’s a cognitive break like  `appendFooter(s);` should be avoided.  
6. Functions should do **one thing**. Error handing is one thing. Thus, a function that handles errors should do nothing else. This implies (as in the example above) that if the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.  
7. Structured Programming
Some programmers follow Edsger Dijkstra’s rules of structured programming.14 Dijkstra said that every function, and every block within a function, should have *one entry and one exit*. Following these rules means that there should only be one `return` statement in a function, no `break` or `continue` statements in a loop, and never, ever, any `goto` statements.

####  How to write function :
Writing software is like any other kind of writing. When you write a paper or an article, you get your thoughts down first, then you massage it until it reads well. The first draft might be clumsy and disorganized, so you wordsmith it and restructure it and refine it until it reads the way you want it to read.

When I write functions, they come out long and complicated. They have lots of indenting and nested loops. They have long argument lists. The names are arbitrary, and there is duplicated code. But I also have a suite of unit tests that cover every one of those clumsy lines of code.
So then I massage and refine that code, splitting out functions, changing names, eliminating duplication. I shrink the methods and reorder them. Sometimes I break out whole classes, all the while keeping the tests passing.

In the end, I wind up with functions that follow the rules I’ve laid down in this chapter. I don’t write them that way to start. I don’t think anyone could.


## Chapter 4 : Comments
Comments ok to have are :
- Warning of Consequences  
- TODO  
- Amplification  

Comments to avoid :
- Noise Comments  
  `protected AnnualDateRule() { } //  Default constructor`  
- Mandated Comments : It is just plain silly to have a rule that says that every function must have a javadoc, or every variable must have a comment.
```   
  // @param title The title of the CD
  // @param author The author of the CD
  public void addCD(String title, String author) {
      CD cd = new CD();
      cd.title = title;
      cd.author = author;
      cdList.add(cd);
}
```
- Scary Noise :
```
// The name
  private String name;
//  The version
  private String version;
```
- Don’t Use a Comment When You Can Use a Function or a Variable  
- Position Markers   
`// Actions //////////////////////////////////`
- Closing Brace Comments   
```
while{  
   for(){  
   }// end of for  
}// end of while  
```  
- Attributions and Bylines  
`/* Added by Rick *`
- Commented-Out Code   
  * Others who see that commented-out code won’t have the courage to delete it. They’ll think it is there for a reason and is too important to delete.
- HTML Comments
- Nonlocal Information  
- Too Much Information *Very long 8-10 lines of comments*
- Inobvious Connection  
- Function Headers

## Chapter 5 Formatting :
- The Newspaper Metaphor  
- In code each blank line is a visual cue that identifies a new and separate concept.
- Vertical Density : it implies close association.  So lines of code that are tightly related should appear vertically dense.  
- Vertical Distance : Concepts that are closely related should be kept vertically close to each other.  
- **Variable Declarations** Variables should be declared as close to their usage as possible. Because our functions are very short, local variables should appear a the top of each function.  
- **Instance variables** on the other hand, should be declared at the top of the class. This should not increase the vertical distance of these variables.
- **Dependent Functions** If one function calls another, they should be vertically close, and the caller should be above the callee.  
- **Conceptual Affinity** Certain bits of code want to be near other bits. They have a certain conceptual affinity. The stronger that affinity, the less vertical distance there should be between them.  
- **Vertical Ordering** In general we want function call dependencies to point in the downward direction. That is, a function that is called should be below a function that does the calling.
- Team Rules  
- [Uncle Bob’s Formatting Rules](Examples/CodeAnalyzer.java)

## Chapter 6 Objects and Data Structures :
We do not want to expose the details of our data. Rather we want to express our data in abstract terms. This is not merely accomplished by using interfaces and/or getters and setters. Serious thought needs to be put into the best way to represent the data that an object contains. The worst option is to blithely add *getters* and *setters*.  

*Procedural code (code using data structures) makes it easy to add new functions without changing the existing data structures. OO code, on the other hand, makes it easy to add new classes without changing existing functions.*
The complement is also true:  
*Procedural code makes it hard to add new data structures because all the functions must change. OO code makes it hard to add new functions because all the classes must change.*  

- The method should not invoke methods on objects that are returned by any of the allowed functions. In other words, talk to friends, not to strangers.  
- Train Wrecks   
`final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();`  
  can become :
  `BufferedOutputStream bos = ctxt.createScratchFileStream(classFileName);
`
### Conclusion :
In any given system we will sometimes want the flexibility to add new data types, and so we prefer objects for that part of the system. Other times we will want the flexibility to add new behaviors, and so in that part of the system we prefer data types and procedures. Good software developers understand these issues without prejudice and choose the approach that is best for the job at hand.

## Chapter 7 Error Handling :

- Use Exceptions Rather Than Return Codes  
- Write Your `Try-Catch-Finally` Statement First : When you execute code in the `try` portion of a `try-catch-finally` statement, you are stating that execution can abort at any point and then resume at the `catch`. `try` blocks are like transactions. Your `catch` has to leave your program in a consistent state, no matter what happens in the `try`.   
- Use Unchecked Exceptions  
- Provide Context with Exceptions : Create informative error messages and pass them along with your exceptions. Mention the operation that failed and the type of failure. If you are logging in your application, pass along enough information to be able to log the error in your catch.  
- When we define exception classes in an application, our most important concern should be *how they are caught*.  
- Don’t Return **Null**.
- Don’t Pass Null : *Returning null from methods is bad, but passing null into methods is worse*.

## Conclusion
Clean code is readable, but it must also be robust. These are not conflicting goals. We can write robust clean code if we see error handling as a separate concern, something that is viewable independently of our main logic. To the degree that we are able to do that, we can reason about it independently, and we can make great strides in the maintainability of our code.


## Chapter 8 Boundaries :

If you use a boundary interface like `Map`, keep it inside the class, or close family of classes, where it is used. Avoid returning it from, or accepting it as an argument to, public APIs.
Rather than using :  
`Map<Sensor> sensors = new HashMap<Sensor>();`  
If implementation of `map` changes anytime in future we would have trouble changing the codebase everywhere instead :

`public class Sensors {
    private Map sensors = new HashMap();  

    public Sensor getById(String id) {   
       return (Sensor) sensors.get(id);  
    }  
}`

- Exploring and learning boundaries :  
Learning the third-party code is hard. Integrating the third-party code is hard too. Doing both at the same time is doubly hard. What if we took a different approach? Instead of experimenting and trying out the new stuff in our production code, we could write some tests to explore our understanding of the third-party code. Jim Newkirk calls such tests *learning tests*.

- Clean Boundaries  
Interesting things happen at boundaries. Change is one of those things. Good software designs accommodate change without huge investments and rework. When we use code that is out of our control, special care must be taken to protect our investment and make sure future change is not too costly.  
Code at the boundaries needs clear separation and tests that define expectations. We should avoid letting too much of our code know about the third-party particulars. It’s better to depend on something you control than on something you don’t control, lest it end up controlling you.

## Chapter 9 Unit Tests :

#### The Three Laws of TDD
By now everyone knows that TDD asks us to write unit tests first, before we write production code. But that rule is just the tip of the iceberg. Consider the following three laws:  
**First Law** : You may not write production code until you have written a failing unit test.  
**Second Law** : You may not write more of a unit test than is sufficient to fail, and not compiling is failing.  
**Third Law** : You may not write more production code than is sufficient to pass the currently failing test.  

-  *Test code is just as important as production code*.  
- Tests Enable the -ilities :
If you don’t keep your tests clean, you will lose them. And without them, you lose the very thing that keeps your production code flexible.  
- Clean Tests : What makes a clean test? Three things. Readability, readability, and readability.   
- One Assert per Test  
- Single Concept per Test  
- F.I.R.S.T.
  - Fast
  - Independent
  - Repeatable
  - Self-Validating
  - Timely

## Chapter 10 : The Single Responsibility Principle

The Single Responsibility Principle (SRP) states that a class or module should have one, *and only one, reason to change.*  

We want our systems to be composed of many small classes, not a few large ones. Each small class encapsulates a single responsibility, has a single reason to change, and collaborates with a few others to achieve the desired system behaviors.  

Cohesion :  
Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables. In general the more variables a method manipulates the more cohesive that method is to its class. A class in which each variable is used by each method is maximally cohesive.  


Isolating from Change :  
A client class depending upon concrete details is at risk when those details change. We can introduce interfaces and abstract classes to help isolate the impact of those details.

## Chapter 11 : Systems

*“Complexity kills. It sucks the life out of developers, it makes products difficult to plan, build, and test.”*

#### Separation of Main
One way to separate construction from use is simply to move all aspects of construction to main, or modules called by main, and to design the rest of the system assuming that all objects have been constructed and wired up appropriately.   

#### Factories  
Sometimes, of course, we need to make the application responsible for when an object gets created. For example, in an order processing system the application must create the Separating construction in `main()`
`LineItem` instances to add to an Order. In this case we can use the `ABSTRACT FACTORY` pattern to give the application control of when to build the `LineItems`, but keep the details of that construction separate from the application code.

#### Dependency Injection
A powerful mechanism for separating construction from use is Dependency Injection (DI).

#### Scaling Up
Growth is not without pain. How many times have you driven, bumper to bumper through a road “improvement” project and asked yourself, “Why didn’t they build it wide enough the first time!?”. It is a myth that we can get systems “right the first time.” Instead, we should imple- ment only today’s stories, then refactor and expand the system to implement new stories tomorrow.  
*Software systems are unique compared to physical systems. Their architectures can grow incrementally, if we maintain the proper separation of concerns.*   

#### Test Drive the System Architecture
The power of separating concerns through aspect-like approaches can’t be overstated. If you can write your application’s domain logic using POJOs, decoupled from any architecture concerns at the code level, then it is possible to truly test drive your architecture.  
*An optimal system architecture consists of modularized domains of concern, each of which is implemented with Plain Old Java (or other) Objects. The different domains are integrated together with minimally invasive Aspects or Aspect-like tools. This architecture can be test-driven, just like the code.*  

#### Optimize Decision Making
*The agility provided by a POJO system with modularized concerns allows us to make optimal, just-in-time decisions, based on the most recent knowledge. The complexity of these decisions is also reduced.*

#### Use Standards Wisely, When They Add Demonstrable Value
*Standards make it easier to reuse ideas and components, recruit people with relevant experience, encapsulate good ideas, and wire components together. However, the process of creating standards can sometimes take too long for industry to wait, and some standards lose touch with the real needs of the adopters they are intended to serve.*

#### Systems Need Domain-Specific Languages
*Domain-Specific Languages allow all levels of abstraction and all domains in the application to be expressed as POJOs, from high-level policy to low-level details.*

### Conclusion
Systems must be clean too. An invasive architecture overwhelms the domain logic and impacts agility. When the domain logic is obscured, quality suffers because bugs find it easier to hide and stories become harder to implement. If agility is compromised, productivity suffers and the benefits of TDD are lost.
At all levels of abstraction, the intent should be clear. This will only happen if you write POJOs and you use aspect-like mechanisms to incorporate other implementation concerns noninvasively.
Whether you are designing systems or individual modules, *never forget to use the simplest thing that can possibly work.*

## Chapter 12 : Emergence

#### Kent Beck’s four rules of Simple Design :  
1. Runs all the tests.  
2. Contains no duplication.  
3. Expresses the intent of the programmer.  
4. Minimizes the number of classes and methods.

### Conclusion
Is there a set of simple practices that can replace experience? Clearly not. On the other hand, the practices described in this chapter and in this book are a crystallized form of the many decades of experience enjoyed by the authors. Following the practice of simple design can and does encourage and enable developers to adhere to good principles and patterns that otherwise take years to learn.  

## Chapter 13 : Concurrency
Writing clean concurrent programs is hard—very hard. It is much easier to write code that executes in a single thread. It is also easy to write multithreaded code that looks fine on the surface but is broken at a deeper level. Such code works fine until the system is placed under stress.

#### Myths and Misconceptions
And so there are compelling reasons to adopt concurrency. However, as we said before, concurrency is hard. If you aren’t very careful, you can create some very nasty situations. Consider these common myths and misconceptions:  
- *Concurrency always improves performance.*  
Concurrency can sometimes improve performance, but only when there is a lot of wait time that can be shared between multiple threads or multiple processors. Neither situation is trivial.  
- *Design does not change when writing concurrent programs.*  
In fact, the design of a concurrent algorithm can be remarkably different from the design of a single-threaded system. The decoupling of what from when usually has a huge effect on the structure of the system.  
- *Understanding concurrency issues is not important when working with a container such as a Web or EJB container.*  
In fact, you’d better know just what your container is doing and how to guard against the issues of concurrent update and deadlock.

- *Concurrency incurs some overhead, both in performance as well as writing additional code.*
- *Correct concurrency is complex, even for simple problems.*  
- *Concurrency bugs aren’t usually repeatable, so they are often ignored as one-offs instead of the true defects they are.*  
- *Concurrency often requires a fundamental change in design strategy.*

#### Concurrency Defense Principles

###### Single Responsibility Principle
  - Concurrency-related code has its own life cycle of development, change, and tuning.
  - Concurrency-related code has its own challenges, which are different from and often more difficult than nonconcurrency-related code.  
  - The number of ways in which miswritten concurrency-based code can fail makes it challenging enough without the added burden of surrounding application code.   

**Recommendation**: Keep your concurrency-related code separate from other code.




## Quotes :

1. It was the bad code that brought the company down.  
2. LeBlanc’s law: Later equals never.  
3. But the fault, dear Dilbert, is not in our stars, but in ourselves. We are unprofessional.  
4. Writing clean code is a lot like painting a picture. Being able to recognize good art from
bad does not mean that we know how to paint.  
5. Being able to recognize clean code from dirty code does not mean that we know how to write clean code!  
6. When the same thing is done over and over, it’s a sign that there is an idea in our mind that is not well represented in the code. I try to figure out what it is. Then I try to express that idea more clearly.  
7. Beautiful code makes the language look like it was made for the problem!  
8. Making Code easy to read actually makes it easier to write.  
9. Continuous improvement is an intrinsic part of professionalism.  
10. Choosing good names takes time but saves more than it takes.  
11. The problem isn’t the simplicity of the code but the implicity of the code.  
12. Programmers create problems for themselves when they write code solely to satisfy a compiler or interpreter.  
13. The length of a name should correspond to the size of its scope.  
14. Choose clarity over entertainment. e.g. `HolyHandGrenade` vs `DeleteItems`.  
15. Duplication may be the root of all evil in software.  
16. Master programmers think of systems as stories to be told rather than programs to be written.  
17. *"Don’t comment bad code rewrite it."* - —Brian W. Kernighan and P. J. Plaugher1  
18. The proper use of comments is to compensate for our failure to express ourself in code.   
19. Every time you write a comment in code, you should grimace and feel the failure of your ability of expression.  
20. Truth can only be found in one place: the code.   
21. Commented-out code gathers like dregs at the bottom of a bad bottle of wine.  
22. Code formatting is about communication, and communication is the professional developer’s first order of business.   
23. Your style and discipline survives, even though your code does not.  
24. Hiding implementation is about abstractions!  
25. Objects hide their data behind abstractions and expose functions that operate on that data. Data structure expose their data and have no meaningful functions.  
26. Mature programmers know that the idea that everything is an object is a myth.  
27. Without tests every change is a possible bug.  
28. If you let the tests rot, then your code will rot too. Keep your tests clean.  
29. For most systems, change is continual. Every change subjects us to the risk that the remainder of the system no longer works as intended.  
30. Needs will change, therefore code will change.   
31. The fact that we have tests, eliminates the fear that cleaning up the code will break it!  
32. Duplication is the primary enemy of a well-designed system.  
33. It’s easy to write code that *we* understand, but to write a code which can be understood by everyone takes real efforts.



[1]: https://www.amazon.com/gp/product/B001GSTOAM
