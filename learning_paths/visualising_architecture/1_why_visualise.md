# Visualising Architecture
Helping to create a common understanding and foster collaboration.

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

## Recommended reading
Many of views expressed here align the views of Simon Brown in his book *(which book?)* which is part of our [recommended reading list](/resources.md).

## Solutions to visualise architecture
- [The C4 model](./2_c4_model.md)