# Software Design Studies

## Rationale

Software design is a very broad topic, and therefore very difficult to master. To makes things even more difficult, there's little guidance to help someone who would like to learn it. Moreover, online or books often contradict each other.

Other design disciplines have found ways to make this work. Design studies are one of the ways. Design studies mean producing a solution to a very specific problem and getting feedback on your design.

Like [coding katas](https://en.wikipedia.org/wiki/Kata_(programming)), design studies are a way to practice. Unlike coding katas, design studies are based on common problems we find in production and are focused on solving the problem within the constraints of production environments.

## Design Qualities

When working on a design study, it's important to clarify what design qualities you want to achieve. The design qualities depend on the production context, so it's partly your choice.

If you don't know where to start, here is a list of design qualities to start from:

* **Changeability**
   * If a user comes and asks you for a change in 3 months, how easy it is to add it?
   * What kind of changes does youre design allow?
   * Changeability can typically be achieved through:
      * Clean Code
      * SOLID Principles
      * The Four Elements of Simple Design
* **Simplicity** and **conciseness**
   * Can you make the code shorter?
   * Can you reduce to solutions that involve fewer parts, fewer code constructs, fewer conditionals?
   * Can you use immutable data?
* **Performance** - Are there simple ways to improve the performance without affecting the other qualities? (Hint: a common one is to transform collections in parallel)

## Just exploring

Sometimes, a design study is useful to just explore an idea. For example, I did a design study on [functional composability](https://github.com/alexboly/composabilityDesignStudy) and another one on [property based testing and immutability](https://github.com/alexboly/pacmanKataPropertyBasedGroovy). 

## Hints for the practice of a design study

These are things that helped me when doing design studies, and they might help you too:

* Start with a clear goal: "explore X" or "solve problem X with these design qualities"
* Choose an interesting problem or an interesting goal
* Use TDD to drive the design
* First make things work in the easiest way possible, then refactor towards the design qualities you seek
* Use very precise names
* Delay performance improvements, unless you have a clear idea how to do it
* Ask interesting questions and explore
* Have fun!

## Most complex problems have composed simpler solutions

A typical complaint about any design exercise is that they are too simple. While a design study is arbitrarily complex (you can build a complete twitter clone if you want to), it's unlikely you'll have the time to properly explore a lot of complex problems.

It turns out however that most complex problems can be split into smaller problems. These simpler problems tend to repeat, and to compose in different ways. Knowing how to solve the simpler problems and how to split the complex into simple are two important software design skills.

Also, solving the simpler problems will lead to improved design skills, which you can then use for new problems. It's anyway better than not making the effort at all.

## List of problems

This is a rather random list. With your help, we can improve it and make it easier to use. But we had to start somewhere.

### Write your own XML / HTML / JSON parser

Features:

* can read data from a file or stream in that format
* allow for language extensions

Hint:
* support only a subset of the language

Goal ideas: 

* try to do it single pass
* compare performance with existing parsers (especially for large files)

Hint: you don't have to support the full language, just enough to learn about the problem and its solutions

### Write your own database engine

Database engines sound very complex. However, if you pick only a subset (eg. no indexing) and don't support SQL, they become more approachable.


Features:

* Support a few data types (eg: number, string, binary, date)
* CRUD operations
* On disk and in-memory storage

Optional features: 

* users and access rights (keep it simple)
* optimize for read-only or for read/write
* replication
* transactions
* concurrency

You can approach the problem with a few different learning goals:

* storage, indexing and retrieval
* concurrent access and transactions
* performance implications of storage
* distributed storage systems
* easily allow adding other data types

References:

* The book [Database Systems: The Complete Book](https://www.amazon.com/Database-Systems-Complete-Book-2nd/dp/0131873253/) is the ultimate reference.
* For an easier start, the book [Data intensive applications](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321) is very useful.

### Write your own programming language

Writing a programming language sounds like a huge task. And it is, provided that you want other people to use it as well. Fortunately, this is only a design study, so we don't have to do much. From my experience, few days are enough to have a minimum programming language working. 

Features:

* print to console and read from console
* basic data types
* basic collection types (stack, maybe list)
* mathematical and boolean operations
* functions
* branching (if or switch or an alternate syntax)
* loops (or high level functions)

Optional features: 

* classes / objects
* integration with other programming languages
* exceptions
* recursion

You can approach the problem with a few different learning goals:

* General purpose language or DSL (internal / external) for a specific domain
* Extensibility: allow addition of more data types, allow extension of existing collections or data types etc.
* Performance (for specific operations)

Hints:

* an interpretor is easier to write than a compiler
* internal DSLs are easier to write than external DSLs or general purpose languages. Some languages support internal DSLs better.
* don't worry if you don't know how to use grammars, compiler-compilers and other tools; just write your own syntactic and semantic parser. It'll work well enough for a small language.
* single-pass syntactic parsers are easier to implement (aka only read forward, never go back)
* if you know how to use advanced tools, or if you want to learn how to use them, then go for it

References:

* Compiler-compiler article from [wikipedia](https://en.wikipedia.org/wiki/Compiler-compiler)
* Martin Fowler's book on [DSLs](https://martinfowler.com/dsl.html) and the [patterns catalog](https://martinfowler.com/dslCatalog/)
* Groovy videos on writing [internal DSLs](https://www.youtube.com/results?search_query=groovy+dsl) (very technology specific)


### Implement tetris fully (including UI)

Tetris is a well-known game, and quite easy to implement. There's no need for AI, path-finding, terrain generation etc., but it has the common design characteristics of a game: the game cycle, rendering, colision detection etc. 

Games have specific design needs, and we can reuse their lessons in some of the modern dynamic web/ mobile/desktop UIs.

Features:

* all the rules of tetris, with all pieces, rotation and translation
* scoring
* leader board
* save / load game

You can approach the problem with a few different learning goals:

*Changeability*:

* allow control with mouse, keyboard, gamepad, and other devices. That is, separate the actions from the event that triggers them
* allow multiple renderers: text-based in console, opengl, some type of canvas (web, mobile, desktop)
* allow multiple ways to save game data - on disk, on a database, through a web service

*Performance*:

* measure frames per second and improve them as much as possible
* ensure fps stays constant while saving / loading etc.

*Incremental design*:

* start with a well of depth 10 and width 1, and with a single square piece. Grow the design slowly towards the result. Of course, use TDD to do it.

### Implement a chat system

Chat systems are the simplest type of network-based application. They introduce many interesting challenges though.

Features:

* List chat users
* Create a chat room
* Chat (text-only)

Optional features:

* File transfers
* Emoticons
* Special commands (eg. \b = buzz)
* Privacy
* Logging of chats

You can approach the problem with a few different learning goals:

*Design your own protocol*:

* Implement the minimal features, then add different clients: command line, web, desktop. Compare the resulting protocol with IRC (and others)

*Operational concerns*:

* How can you ensure scalability, performance, resilience, security?

*Distributed application models*:

* Peer to peer vs centralized
