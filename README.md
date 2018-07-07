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




## Chapter 5 :


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


[1]: https://www.amazon.com/gp/product/B001GSTOAM
