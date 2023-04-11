[< Back](../introducing_the_principles.md)

# Code design principles

A good foundation (or place to start) is the design of code and an understanding of best practice.

## TDD

It's worth revisiting why we do TDD (Test Driven Development) as it's not just to ensure our code is tested but to promote good code design.

It is possible to recognise code written using TDD practices at is is intrinsically different from code which was written without TDD. You also find adding tests retrospectively is hard and frustrating and you end up leaning on BDD (behavioural tests).

*Why is this ?*

Code written using TDD has to be small, have a single purpose and therefore a single test. We compose these testable units together into more complex behaviours.

> TDD will force you to write testable code, i.e., *loosely coupled* and *highly cohesive,* which means your code has a higher quality. If the testing becomes difficult, it is a tell-tale sign your design could use improvement. Thus, TDD is an effective way to get feedback on your code’s *internal quality*.
>
> https://www.codecraftr.nl/why-use-tdd/

## SOLID

The SOLID principles for Object Oriented Programming are important to understand as their use cases can be scaled beyond classes and functions within a single codebase.

-   **S**  - Single-responsibility Principle
-   **O**  - Open-closed Principle
-   **L**  - Liskov Substitution Principle
-   **I**  - Interface Segregation Principle
-   **D**  - Dependency Inversion Principle

[SOLID Principles for Programming and Software Design](https://www.freecodecamp.org/news/solid-principles-for-programming-and-software-design/)

[< Back](../introducing_the_principles.md)
