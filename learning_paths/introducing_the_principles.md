
# Introducing the Principles

## Understanding Context

Before we embark on designing software we need to understand the context in which it will be both developed and used. This understanding will inform our decision making later on. We would introduce significant risk if we committed to a language, frameworks or infrastructure without an understanding of expectations and constraints 

### The Made Tech Architecture Playbook

Our current playbook focuses on these activities and making yourself familiar with the approach will help you get started on any project.

 [Playbook Part 1 - 'Holistic Thinking'](https://docs.google.com/presentation/d/1RwBxzT37oZNXWZzJBgZ9e-IzXfYOlf7FnGIPdjEZV-Q/edit?usp=sharing)

## Software Architecture

Once the context is understood and the architect knows (more or less) how to make decisions around trade offs and where value lies (e.g scaleability and performance is important but only up to a point and but not as important as correctness or use-ability) then they are better equipped to design the system.

Whether you are designing Microservices or monoliths or something else entirely the basic principles remain.

 - The codebase needs to be easy to test in small chunks or as a whole
 - The code base needs to be easy to change and adapt
 - The codebase (and therefore design) is always changing and adapting
 - When a change is made the impact needs to be minimal (it should not trigger many subsequent changes through other components or even services causing developers pain)

So the goal is a responsive software design whether thats the design of classes and functions or services and systems. The goal and approach is always the same (it's just the scale you are looking at it from might change).

With that in mind it's worth looking at a number of well known approaches to attempt to solve this problem that we believe work well.

There is no *'one true way'* to design systems but good software developers would have a knowledge of many techniques and apply as needed.

You don't need to know all these (and other approaches not mentioned) inside out but have an awareness so when you see the problem space you might relate it back to a known pattern well suited to solve it.

### Code design principles

A good foundation (or place to start) is the design of code and an understanding of best practice.

#### TDD

It's worth revisiting why we do TDD (Test Driven Development) as it's not just to ensure our code is tested but to promote good code design.

It is possible to recognise code written using TDD practices at is is intrinsically different from code which was written without TDD. You also find adding tests retrospectively is hard and frustrating and you end up leaning on BDD (behavioural tests).

*Why is this ?*

Code written using TDD has to be small, have a single purpose and therefore a single test. We compose these testable units together into more complex behaviours.

> TDD will force you to write testable code, i.e., *loosely coupled* and *highly cohesive,* which means your code has a higher quality. If the testing becomes difficult, it is a tell-tale sign your design could use improvement. Thus, TDD is an effective way to get feedback on your code’s *internal quality*.
> 
> https://www.codecraftr.nl/why-use-tdd/

#### SOLID

The SOLID principles for Object Oriented Programming are important to understand as their use cases can be scaled beyond classes and functions within a single codebase.

-   **S**  - Single-responsibility Principle
-   **O**  - Open-closed Principle
-   **L**  - Liskov Substitution Principle
-   **I**  - Interface Segregation Principle
-   **D**  - Dependency Inversion Principle

[SOLID Principles for Programming and Software Design](https://www.freecodecamp.org/news/solid-principles-for-programming-and-software-design/)

### Responsive Architecture Approaches

Taking a step further back and thinking more abstractly about designing software and services we encounter design patterns which attempt to make larger scale designs more responsive to change.

You don't need to know these in depth but being aware of their existence and what they are trying to achieve will help you in your design process.

The patterns below are some good starting points but you will find many more if you dig deeper.

####  Onion Architecture

[Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)

#### Domain Driven Design

[Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)

#### Hexagonal Architecture

[Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))

####  DCI (Data, context, and interaction)  Architecture

A slightly different twist on the above approaches where users and their behaviour are moved to the fore.
> Objects are principally about people and their mental models—not polymorphism, coupling and cohesion
>  ... but in spite of capturing structure, OO fails to capture behavior


-   To improve the readability of  [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming")  code by giving system behavior first-class status;
-   To cleanly separate code for rapidly changing system behavior (what a system  _does_) versus slowly changing  [domain knowledge](https://en.wikipedia.org/wiki/Domain_knowledge "Domain knowledge")  (what a system  _is_), instead of combining both in one class interface;
-   To help software developers reason about system-level state and behavior instead of only object state and behavior;
-   To support an object style of thinking that is close to programmers' mental models, rather than the class style of thinking that overshadowed object thinking early in the history of object-oriented programming languages.

[DCI Architecture](https://www.artima.com/articles/the-dci-architecture-a-new-vision-of-object-oriented-programming)

#### Clean Architecture

Clean architecture is an amalgamation of a number of architecture strategies. It is an attempt to create a separation of concerns. This separation is achieved by dividing the software into layers such as decoupling UI from the Business logic or external dependancies to increase testability and changeability of components increasing your softwares responsiveness to change.
  
The overriding rule that makes this architecture work is _The Dependency Rule_. This rule says that _source code dependencies_ can only point _inwards_.

A simple [explanation](https://www.youtube.com/watch?v=Ys_W6MyWOCw) that nicely explains when and when not to follow dogma based on trade offs. (15 minutes)

### Software Architecture Principles we believe are important

 - **Designing Components** so they are *stable* (balancing cohesion and coupling)
 - **Setting Boundaries** between software elements. Boundaries  separate things that matter from things that don’t, i.e. high-level components from low-level components
 - **Separating layers** and organising them using the *dependency rule*: outer layers should depend on inner layers (at the source-level), and not vice versa.

### A word on Microservices vs Monoliths

Microservices are popular as (in theory) they force a number of the above principals onto teams by splitting up services into small domain concerns with clear interfaces. They provide other advantages such as (but not limited to):

-   Scalability improvements
-   Improved fault isolation
-   Program language and technology agnostic
-   Reusability across different areas of business

However they also have a management overhead and if designed poorly can be unintentionally tightly coupled (e.g a distributed monolith) which can become a nightmare to maintain.

I would argue a team should be understand how to create a loosely coupled Monolith before embarking on Microservices so I recommend the video below.

[Creating a Loosely Coupled Monolith](https://www.youtube.com/watch?v=48C-RsEu0BQ)

## Day to day Activities

### Continually visualise the technical architecture

-   Fosters common understanding of architecture to technical and non-technical stakeholders
-   Aligns to evolving architecture through techniques such as minimum viable architecture (MVA)
-   Provides value for enabling techniques such as risk storming
-   Can help with speeding up comprehension of architecture for new team members

[C4 model](https://www.google.com/url?q=https%3A%2F%2Fc4model.com%2F&sa=D&sntz=1&usg=AOvVaw37D_ZkAp1YMSvEpByhY17H)
    
-   C4 model provides a lean approach to diagramming a software architecture at multiple levels
-   Focus on providing clear meaning
-   Useful as starting point for other techniques such as risk storming

### Keeping documentation close to code
We have observed that proximity of documentation to code leads to increased freshness of documentation     

 - Simplifies checking updates have been done as part of Definition of
   Done
 - Documentation / diagrams as code Change from static
 - diagrams done at the start/end of a delivery to living parts of the  
   delivery that add value in terms of domain context

### Identifying 'non' requirements

Quality Attributes or Non Functional Requirements need to be considered and balanced as they are normally a trade off, examples could be:

 - Performance
 - Interoperability
 - Deployability
 - Reliability
 - Availability
 - Security  
 - Maintainability
 - Observability
 - Testability
 - Scaleability
 - Modifiability
 - Reusability
 - Audibility

###  Managing risk

[Risk Storming](https://www.google.com/url?q=https%3A%2F%2Friskstorming.com%2F&sa=D&sntz=1&usg=AOvVaw3BVCnFt1o6K9xYXddpDFY9)
    
-   A visual and collaborative risk identification technique
-   Can be applied to architectures, business processes, workflows, etc
-   Can be applied multiple times during the lifetime of the thing being risk stormed
-   More information [here](https://sites.google.com/madetech.com/signpost/home/software-engineering/technical-architecture/processes/risk-storming)

### Communicating into the future

-   Communication is a key architecture skill
-   Consider the context of who you are communicating too and how it would be best received or understood
-   Simple not simplistic
-   You must consider future teams and architects, years from now decisions will be questioned and problems revisited. Shortcut that future pain by making sure the past can be understood.

[Architecture Decision Records](https://www.google.com/url?q=https%3A%2F%2Fadr.github.io%2F&sa=D&sntz=1&usg=AOvVaw0F6q-5rF3DK-brst0WDqQH)
    
-   A framework for recording choices that are architecturally significant
-   Helps with knowledge transfer over the lifetime of a product
-   The process of filling in ADRs helps solidify thinking on a decision

## Reference Material

[Fundamentals of Software Architecture](https://www.google.com/url?q=https://app.learnerbly.com/resources/7eee7452-4cee-4b0b-a748-204ecf047307/&sa=D&sntz=1&usg=AOvVaw3n-_LHSEGjtdqftBL5X--v) 

[Just Enough Software Architecture](https://app.learnerbly.com/resources/058590f7-3f71-49a4-9fc7-8c499a60d925/?queryID=530b40ae0c648257d6f54e64cda05cc7&index=production_resources/)
