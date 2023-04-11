# Visualising Architecture
Helping to create a common understanding and foster collaboration.

## Recommended reading
Many of views expressed here align the views of Simon Brown in his book which is part of our [recommended reading list](/resources.md).

## Watch
Watch our recent visualising architecture CoP session [here](https://drive.google.com/file/d/14R3OpBbcN0xbU_XeQQfG7ocehkw_U0w3/view?usp=share_link)

## Introduction
Visualising architecture is about effectively and efficiently communicating the software architecture of the software that you’re building, with a view to:
- Help everybody understand the “big picture” of what is being built, and how this fits into the “bigger picture” of the organisation/environment in which it exists.
- Create a shared vision for the development team.
- Provide a “map” that can be used by software developers to navigate the source code.
- Provide a point of focus for technical conversations about new features, technical debt, risk reviews, etc.
- Fast-track the on-boarding of new software developers into the team.
- Provide a way to explain what’s being built to people outside of the development team, whether they are technical or non-technical.

## The problem to solve
Ask somebody in the building industry to visually communicate the architecture of a building and you’ll likely be presented with site plans, floor plans, elevation views, cross-section views, and detailed drawings. In contrast, ask somebody in the software industry to communicate the software architecture of a software system using diagrams, and you’ll likely get a confused mess of boxes and lines.

## Doesn't the code speak for itself?
We feel it is difficult to describe a code base perfectly without a lot of prior knowledge. We feel that different questions require different levels of granularity to answer them, which may not easily be possible from just looking at the code. The code doesn’t answer where components are deployed at runtime or how they communicate and it does not provide an overview of a system that can be used for group decision making.

## C4 Model
The [C4 Model](https://c4model.com/) focusses on the visual communication and documentation of software architecture. It doesn’t present a formalised, standardised method to communicate software architecture, it does provide a collection of lightweight ideas and techniques that we've observed to be useful.

We've observed the use of the C4 Model with our active deliveries and found that it:
- Provides a lean approach to diagramming a software architecture at multiple levels
- It helps focus on providing clear and concise meaning
- Is useful as starting point for other techniques such as risk storming
- Has a wide range of diagram types that are easy to learn, create and understand
- Isn't mandatory to create versions of all of the diagrams, only use ones that appropriate. System Context and Container diagrams are the most widely used.
- is a simple but not simplistic approach to visualising architecture

## Tools

See a list of potential [tools](../principles/tools.md) that are tried and tested.

However, we recommend the [C4 Model](https://c4model.com/) and the [Structurizr DSL](https://github.com/structurizr/dsl). See [here for a demo](https://github.com/madetech/structurizr-template) that you can try and explains why.
