# Responsive architecture approaches

Taking a step further back from the code and thinking more abstractly about designing software and services we encounter design patterns which attempt to make larger scale designs more responsive to change.

You don't need to know these in depth but being aware of their existence and what they are trying to achieve will help you in your design process.

The patterns below are some good starting points but you will find many more if you dig deeper.

##  Onion Architecture

The Onion Architecture is not well known but often implemented. It is a foundational part of the more popular clean architecture (discussed later).

This Architecture relies heavily on the _Dependency Inversion Principle_ and focuses on decoupling the business logic from other layers which is a recurring theme for building responsive architectures.

[Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/)

## Domain Driven Design

Domain Driven Design is a concept that models software based on a business domain and it's context, working closely with business experts.

[Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)

You might see how the DDD approach fits well with the Made Tech Playbook where we spend effort understanding the business context, working closely with subject matter experts.

[DDD Made Simple](https://www.youtube.com/watch?v=H5--9pMmuK4) - 8 minutes

However it's implementation can be complicated or overkill for smaller projects.

[Stop Dogmatic DDD](https://www.youtube.com/watch?v=8XmXhXH_q90) - 7 minutes

## Hexagonal Architecture

[Hexagonal Architecture](https://en.wikipedia.org/wiki/Hexagonal_architecture_(software))

##  DCI (Data, context, and interaction)  Architecture

A slightly different twist on the above approaches where users and their behaviour are moved to the fore.
> Objects are principally about people and their mental models—not polymorphism, coupling and cohesion
>  ... but in spite of capturing structure, OO fails to capture behavior


-   To improve the readability of  [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming")  code by giving system behavior first-class status;
-   To cleanly separate code for rapidly changing system behavior (what a system  _does_) versus slowly changing  [domain knowledge](https://en.wikipedia.org/wiki/Domain_knowledge "Domain knowledge")  (what a system  _is_), instead of combining both in one class interface;
-   To help software developers reason about system-level state and behavior instead of only object state and behavior;
-   To support an object style of thinking that is close to programmers' mental models, rather than the class style of thinking that overshadowed object thinking early in the history of object-oriented programming languages.

[DCI Architecture](https://www.artima.com/articles/the-dci-architecture-a-new-vision-of-object-oriented-programming)

## Clean Architecture

Clean architecture is an amalgamation of a number of architecture strategies. It is an attempt to create a separation of concerns. This separation is achieved by dividing the software into layers such as decoupling UI from the Business logic or external dependancies to increase testability and changeability of components increasing your softwares responsiveness to change.
  
The overriding rule that makes this architecture work is _The Dependency Rule_. This rule says that _source code dependencies_ can only point _inwards_.

A simple [explanation](https://www.youtube.com/watch?v=Ys_W6MyWOCw) that nicely explains when and when not to follow dogma based on trade offs. (15 minutes)
