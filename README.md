# Software Design Studies

## Rationale

Software design is a very broad topic, and therefore very difficult to master. To makes things even more difficult, there's little guidance to help someone who would like to learn it. Moreover, online or books often contradict each other.

Other design disciplines have found ways to make this work. Design studies are one of the ways. Design studies mean producing a solution to a very specific problem and getting feedback on your design.

Like [coding katas](https://en.wikipedia.org/wiki/Kata_(programming)), design studies are a way to practice. Unlike coding katas, design studies are based on common problems we find in production and are focused on solving the problem within the constraints of production environments.

## Design Qualities

When working on a design study, it's important to clarify what design qualities you want to achieve. The design qualities depend on the production context. So it's partly your choice, because you often need to use existing tools, systems or structures that are your constraints.

If you don't know where to start, here is a list of design qualities to start from:

### Changeability
   * If a user comes and asks you for a change in 3 months, how easy it is to add it?
   * What kind of changes does your design allow?
   * Changeability can typically be achieved through:
      * Clean Code
      * [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
      * [The Four Elements of Simple Design](https://martinfowler.com/bliki/BeckDesignRules.html)
### Simplicity and Conciseness
   * Can you make the code shorter while maintaining clarity?
   * Can you reduce to solutions that involve fewer parts, fewer code constructs, fewer conditionals?
   * Can you use immutable data?
### Performance
Are there simple ways to improve the performance without affecting the other qualities? (Hint: a common one is to transform collections in parallel)

## Just exploring

Sometimes, a design study is useful to just explore an idea. For example, check a design study on [functional composability](https://github.com/alexboly/composabilityDesignStudy), and another one on [property based testing and immutability](https://github.com/alexboly/pacmanKataPropertyBasedGroovy). Check also the [React Design Study](https://hackernoon.com/the-react-state-museum-a278c726315) that has more examples and details.

## Hints for the practice of a design study

These are things that can help you when doing design studies:

* Start with a clear goal: "explore X" or "solve problem X with these design qualities"
* Choose an interesting problem or an interesting goal
* Use [Test Driven Development](https://en.wikipedia.org/wiki/Test-driven_development) to drive the design
* First make things work in the easiest way possible, then refactor towards the design qualities you seek
* Use very precise names
* Delay performance improvements, unless you have a clear idea how to do it
* Ask interesting questions and explore
* Have fun!

## Most complex problems have composed simpler solutions

A typical complaint about any design exercise is that they are too simple. While a design study is arbitrarily complex (you can build a complete twitter clone if you want to), it's unlikely you will have the time to properly explore a lot of complex problems.

It turns out however that most complex problems can simpler composed solutions. These simpler problems tend to repeat, and to compose in different ways. Knowing how to solve the simpler problems and how to split the complex into simple are two important software design skills.

Also, solving the simpler problems will lead to improved design skills, which you can then use for new problems. It's anyway better than not making the effort at all.

## List of problems

This is a rather random list. With your help, we can improve it and make it easier to use. But we had to start somewhere.

### 1) Write your own XML / HTML / JSON parser

Features:

* Can read data from a file or stream in that format
* Allow for language extensions

Hint:
* Support only a subset of the language

Goal ideas: 

* Try to do it single pass (only read forward, never go back)
* Compare performance with existing parsers (especially for large files)

Hint: you don't have to support the full language, just enough to learn about the problem and its solutions

### 2) Write your own database engine

Database engines sound very complex. However, if you pick only a subset (eg. no indexing), and don't support SQL, they become more approachable.


#### Features

* Support a few data types (eg: number, string, binary, date)
* CRUD operations
* On disk and in-memory storage


#### Optional features

* Users and access rights (keep it simple)
* Optimize for read-only or for read/write
* Replication
* Transactions
* Concurrency


#### Learning goals (choose one)

* Storage, indexing and retrieval
* Concurrent access and transactions
* Performance implications of storage
* Distributed storage systems
* Easily allow adding other data types


#### References

* The book [Database Systems: The Complete Book](https://www.amazon.com/Database-Systems-Complete-Book-2nd/dp/0131873253/) is the ultimate reference.
* For an easier start, the book [Data intensive applications](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321) is very useful.

### 3) Write your own programming language

Writing a programming language sounds like a huge task. And it is, provided that you want other people to use it as well. Fortunately, this is only a design study, so we don't have to do much. From my experience, a few days are enough to have a minimum programming language working. 


#### Features

* Print to console and read from console
* Basic data types
* Basic collection types (stack, maybe list)
* Mathematical and boolean operations
* Functions
* Branching (if or switch or an alternate syntax)
* Loops (or [higher order functions](https://en.wikipedia.org/wiki/Higher-order_function))


#### Optional features

* Classes / objects
* Integration with other programming languages
* Exceptions
* Recursion

#### Learning goals (choose one)

* General purpose language or DSL (internal / external) for a specific domain
* Extensibility: allow addition of more data types, allow extension of existing collections or data types etc.
* Performance (for specific operations)


#### Hints

* An interpretor is easier to write than a compiler
* Internal DSLs are easier to write than external DSLs or general purpose languages. Some languages support internal DSLs better.
* Don't worry if you don't know how to use grammars, compiler-compilers and other tools; just write your own syntactic and semantic parser. It'll work well enough for a small language.
* Single-pass syntactic parsers are easier to implement (aka only read forward, never go back)
* If you know how to use advanced tools, or if you want to learn how to use them, then go for it


#### References

* Compiler-compiler article from [wikipedia](https://en.wikipedia.org/wiki/Compiler-compiler)
* Martin Fowler's book on [DSLs](https://martinfowler.com/dsl.html) and the [patterns catalog](https://martinfowler.com/dslCatalog/)
* Groovy videos on writing [internal DSLs](https://www.youtube.com/results?search_query=groovy+dsl) (very technology specific)


### 4) Implement tetris fully (including UI)

Tetris is a well-known game, and quite easy to implement. There's no need for AI, path-finding, terrain generation etc., but it has the common design characteristics of a game: the game cycle, rendering, colision detection etc. 

Games have specific design needs, and we can reuse their lessons in some of the modern dynamic web/ mobile/desktop UIs.

#### Features

* All the rules of tetris, with all pieces, rotation and translation
* Scoring
* Leader board
* Save / load game

#### Learning goals (choose one)

* *Changeability*:

   * Allow control with mouse, keyboard, gamepad, and other devices. That is, separate the actions from the event that triggers them
   * Support multiple renderers: text-based in console, opengl, some type of canvas (web, mobile, desktop)
   * Enable multiple ways to save game data - on disk, on a database, through a web service

* *Performance*:

   * Measure frames per second and improve them as much as possible
   * Ensure fps stays constant while saving / loading etc.

* *Incremental design*:

   * Start with a well of depth 10 and width 1, and with a single square piece. Grow the design slowly towards the result. Of course, use TDD to do it.

### 5) Implement a chat system

Chat systems are the simplest type of network-based application. They introduce many interesting challenges though.

#### Features

* List chat users
* Create a chat room
* Chat (text-only)

#### Optional features

* File transfers
* Emoticons
* Special commands (eg. \b = buzz)
* Privacy
* Logging of chats

#### Learning goals (choose one)

* *Design your own protocol*:

   * Implement the minimal features, then add different clients: command line, web, desktop. Compare the resulting protocol with IRC (and others)

* *Operational concerns*:

   * How can you ensure scalability, performance, resilience, security?

* *Distributed application models*:

   * Peer to peer vs centralized
