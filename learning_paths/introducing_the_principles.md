
# Introducing the Principles

## Understanding Context

### [Playbook Part 1 - 'Holistic Thinking'](https://docs.google.com/presentation/d/1RwBxzT37oZNXWZzJBgZ9e-IzXfYOlf7FnGIPdjEZV-Q/edit?usp=sharing)

## Software Architecture

Once the context is understood and the architect knows (more or less) how to make decisions around trade offs and where value lies (e.g scaleability and performance is important but only up to a point and but not as important as correctness or use-ability) then they are better equipped to design the system.

Whether you are designing micro services or monoliths the basic principles remain.

 - The codebase needs to be easy to test in small chunks or as a whole
 - The code base needs to be easy to change and adapt
 - The codebase (and therefore design) is always changing and adapting
 - When a change is made the impact needs to be minimal (it should not trigger many subsequent changes through other components or even services causing developers pain)

So the goal is a responsive architecture. Architecture could be the design of classes and functions or services and systems, the goal and approach is always the same (it's just the scale you are looking at it from).

With that in mind it's worth looking at a number of well known approaches to attempt to solve this problem that we believe work well.

There is no *'one true way'* to design systems but good software developers would have a knowledge of many techniques and apply as needed.

You don't need to know all these (and other approaches not mentioned) inside out but have an awareness so when you see the problem space you might relate it back to a known pattern well suited to solve it.

### Code design principles

A good foundation (or place to start)  is the design of code and an understanding of best practice.

#### TDD

It's worth revisiting why we do TDD (Test Driven Development) as it's not just to ensure our code is tested but to promote good code design.

It is possible to recognise code written using TDD practices at is is intrinsically different from code which was written without TDD. You also find adding tests retrospectively is hard and frustrating and you end up leaning on BDD (behavioural tests).

Why is this ?

Code written using TDD has to be small, have a single purpose and therefore a single test. We compose these testable units together into more complex behaviours.

> TDD will force you to write testable code, i.e., *loosely coupled* and *highly cohesive,* which means your code has a higher quality. If the testing becomes difficult, it is a tell-tale sign your design could use improvement. Thus, TDD is an effective way to get feedback on your code’s *internal quality*.
> 
> https://www.codecraftr.nl/why-use-tdd/

#### SOLID

### Responsive Architecture Approaches

####  Onion Architecture

[Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)

#### Domain Driven Design

[Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)

#### Hexagonal Architecture

[Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))

####  DCI (Data, context, and interaction)  Architecture

[DCI Architecture](https://www.artima.com/articles/the-dci-architecture-a-new-vision-of-object-oriented-programming)

#### Clean Architecture

Clean architecture is an amalgamation of a number of architecture strategies. It is an attempt to create a separation of concerns. This separation is achieved by dividing the software into layers such as decoupling UI from the Business logic or external dependancies to increase testability and changeability of components increasing your softwares responsiveness to change.
  
The overriding rule that makes this architecture work is _The Dependency Rule_. This rule says that _source code dependencies_ can only point _inwards_.

A simple [explanation](https://www.youtube.com/watch?v=Ys_W6MyWOCw) - 15 minutes

### Principles we believe are important
#### Component principles
#### Setting Boundaries
#### Separating layers
#### Describing the purpose of a component

-   Aligns to single responsibility principle
-   Able to reason easily about the architecture
-   Inability to be able to do this implies complex / multi-responsibility component or other associated 'code smells'

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
