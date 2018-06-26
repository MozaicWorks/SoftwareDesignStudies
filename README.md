# Software Design Studies

## Rationale

Software design is a broad topic, and therefore difficult to master. To makes things even more worse, there's little guidance to help someone who would like to learn it. Moreover, resources such as websites or books are contradicting.

Other design disciplines have found ways to teach the necessary skills to people who want to become designers or to improve their skills as designers. One way is **Design Studies**. Design studies mean to create a solution to a specific problem and getting feedback on the design.

Like [coding katas](https://en.wikipedia.org/wiki/Kata_(programming)), design studies is one way to practice. Unlike coding katas, design studies are based on common problems we find in production and focus on solving the problem within the constraints of production environments.

## Design Qualities

When working on a design study, it's important to clarify what design qualities you want to achieve. The design qualities depend on the production context. It is partly your choice, because you often need to use existing tools, systems or structures that are your constraints.

If you don't know where to start, here is a list of design qualities to start with:

### Changeability
   * If a user comes and asks you for a change in 3 months, how easy it is to add the change?
   * What kind of changes does your design allow?
   * Changeability can typically be achieved through:
      * Clean Code
      * [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)
      * [The Four Elements of Simple Design](https://martinfowler.com/bliki/BeckDesignRules.html)
### Simplicity and Conciseness
   * Can you make the code shorter while maintaining clarity?
   * Can you change to a solution that contains fewer parts, fewer code constructs, fewer conditionals?
   * Can you use immutable data?
### Performance
Are there simple ways to improve the performance without affecting the other qualities? (Hint: a common one is to transform collections in parallel)

## Just exploring

Sometimes, a design study is useful to just explore an idea. For example, read a design study on [functional composability](https://github.com/alexboly/composabilityDesignStudy), and another on [property based testing and immutability](https://github.com/alexboly/pacmanKataPropertyBasedGroovy). More examples can be found in the [React Design Study](https://hackernoon.com/the-react-state-museum-a278c726315).

## Hints for practicing a design study

Here are a few things that can help you when doing design studies:

* Start with a clear goal: "explore X" or "solve problem X with these design qualities"
* Choose an interesting problem or an interesting goal
* Use [Test Driven Development](https://en.wikipedia.org/wiki/Test-driven_development) to drive the design
* First make things work in the simplest way possible, then refactor towards the design qualities you want
* Use very precise names
* Delay performance improvements, unless you have a clear idea how to do it
* Ask interesting questions and explore
* Have fun!

## Most complex problems are composed of simpler problems

A typical complaint about any design exercise is that they are too simple. While a design study is arbitrarily complex (you can build a complete twitter clone if you want to), it's unlikely you will have the time to properly explore a lot of complex problems.

It turns out, however, that most complex problems are composed of simpler problems. These simpler problems tend to be repeated, and are combined in different ways. Knowing how to solve simpler problems and how to split a complex problem into smaller problems are two important software design skills.

Solving the smaller problems will lead to improved design skills, which you can then use for new problems.

## List of problems

This list is a bit random. With your help, we can improve it and make it easier to use. But we had to start somewhere.

### 1) Write your own XML / HTML / JSON parser

#### Features

* Can read data from a file or stream in that format
* Allow for language extensions

#### Learning goals (choose one)

* Try to do it single pass (only read forward, never go back)
* Compare performance with existing parsers (especially for large files)

#### Hint
* Support only a subset of the language. You don't have to support the full language, just enough to learn about the problem and its solutions

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

Writing a programming language sounds like a huge task. And it is, provided that you want other people to use it as well. Fortunately, this is only a design study, so we don't have to do too much. Based on experience, a few days are usually enough to have a minimum programming language working. 

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

* An interpreter is easier to write than a compiler
* Internal DSLs are easier to write than external DSLs or general purpose languages. Some languages support internal DSLs better.
* Don't worry if you don't know how to use grammars, compiler-compilers and other tools; just write your own syntactic and semantic parser. It will work well enough for a small language.
* Single-pass syntactic parsers are easier to implement (aka only read forward, never go back)
* If you know how to use advanced tools, or if you want to learn how to use them, then go for it


#### References

* Compiler-compiler article from [wikipedia](https://en.wikipedia.org/wiki/Compiler-compiler)
* Martin Fowler's book on [DSLs](https://martinfowler.com/dsl.html) and the [patterns catalog](https://martinfowler.com/dslCatalog/)
* Groovy videos on writing [internal DSLs](https://www.youtube.com/results?search_query=groovy+dsl) (very technology specific)


### 4) Implement tetris with a user interface

[Tetris](https://en.wikipedia.org/wiki/Tetris) is a well-known game, and not too hard to implement. There's no need for AI, path-finding, terrain generation etc., but it has the common design characteristics of a game: the game cycle, rendering, colision detection etc. 

Games have specific design needs, and we can reuse these lessons in some of the modern dynamic web/mobile/desktop UIs.

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

   * Measure frames per second, fps, and improve them as much as possible
   * Ensure that fps stays constant while saving / loading etc.

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
