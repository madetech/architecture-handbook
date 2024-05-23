
# Introducing the Principles

## Understanding Context

Before we embark on designing software we need to understand the context in which it will be both developed and used.

This understanding will inform our decision making later on. We could introduce significant risk if we committed to a language, frameworks or infrastructure without an understanding of expectations and constraints

### The Made Tech Architecture Playbook

Our current playbook focuses on these activities and making yourself familiar with the approach will help you get started on any project.

 [Playbook Part 1 - 'Holistic Thinking'](https://docs.google.com/presentation/d/1RwBxzT37oZNXWZzJBgZ9e-IzXfYOlf7FnGIPdjEZV-Q/edit?usp=sharing)

## Software Architecture

Once the context is understood and the architect knows (more or less) how to make decisions around trade offs and where value lies (e.g scaleability and performance is important but only up to a point and but not as important as correctness or use-ability) then they are better equipped to design the system.

Whether you are designing Microservices or monoliths (or something else entirely) the basic principles remain.

 - The codebase needs to be easy to test in small chunks or as a whole
 - The codebase needs to be easy to change and adapt to new requirements
 - The codebase (and therefore design) *is* always changing and adapting
 - When a change is made the impact needs to be minimal (it should not trigger many subsequent changes through other components or services causing developers pain)

So the goal is a responsive software design whether thats the design of classes and functions or services and systems. The goal is always the same (it's just the scale you are looking at it from might change).

With that in mind it's worth looking at a number of well known approaches to attempt to solve this problem that we believe work well.

There is no *'one true way'* to design systems but good software developers have a knowledge of many techniques and apply as needed.

You don't need to know all these (or the many other approaches not mentioned) inside out but have an awareness so when you see the problem space you might relate it back to a known pattern.

### [Code design principles](./software/code_design_principles.md)

### [Responsive architecture approaches](./software/responsive_architecture_approaches.md)

### [Software architecture principles we believe are important](./software/software_architecture_principles.md)

## Microservices vs Monoliths

The debate around how to layer a service - should you or should you not follow a microservice, service oriented or monolithic architecture is so common it's worth addressing now so... [A word on Microservices vs Monoliths](./software/monoliths_vs_microservices.md)

## Day to day Behaviours

This is also true for day to day behaviours, as an architect (or a software developer) what could you be doing on a regular basis that are likely to improve architectural outcomes ?

[Day to day Behaviours](./continuous_behaviours.md)

## Reading Material

[Fundamentals of Software Architecture](https://www.amazon.co.uk/dp/1492043451)

[Just Enough Software Architecture](https://www.amazon.co.uk/gp/product/0984618104)
