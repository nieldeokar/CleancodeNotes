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




[1]: https://www.amazon.com/gp/product/B001GSTOAM
