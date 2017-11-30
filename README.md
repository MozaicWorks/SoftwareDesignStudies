# Software Design Studies

## Rationale

Software design is a very broad topic, and therefore very difficult to master. To makes things even more difficult, there's little guidance to help someone who would like to learn it. Moreover, online or books often contradict each other.

Other design disciplines have found ways to make this work. Design studies are one of the ways. Design studies mean producing a solution to a very specific problem and getting feedback on your design.

Like coding katas, design studies are a way to practice. Unlike coding katas, design studies are based on common problems we find in production and are focused on solving the problem within the constraints of production environments.

## Design qualities

When working on a design study, it's important to clarify what design qualities you want to achieve. The design qualities depend on the production context, so it's partly your choice.

If you don't know where to start, here's a list of design qualities to start from:

* **Changeability** - if a user comes and asks you for a change in 3 months, how easy it is to add it? What kind of changes does youre design allow? Changeability can typically be achieved through: clean code, SOLID principles, the four elements of simple design
* **Simplicity** and **conciseness** - can you make the code shorter? Can you reduce to solutions that involve fewer parts, fewer code constructs, fewer conditionals? Can you use immutable data?
* **Performance** - are there simple ways to improve the performance without affecting the other qualities? (Hint: a common one is to transform collections in parallel)

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

Database engines sound very complex. However, if you pick only a subset (eg. no indexing) and don't support SQL, they pose interesting challenges.

If you want to go in depth, the book [Data intensive applications](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/) is very useful. 

Features:

* CRUD operations
* on disk and in-memory storage

Optional features: 

* users and access rights (keep it simple)
* optimize for read-only or for read/write
* replication
