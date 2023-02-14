
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

### [Code design principles](code_design_principles.md)

### [Responsive Architecture Approaches](responsive_architecture_approaches.md)

### [Software Architecture Principles we believe are important](../principles.md)

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
