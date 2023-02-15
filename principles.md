### The Big List of Principles

## Software Design

##  Designing Components so they are *stable*

Balancing cohesion and coupling

## Set Boundaries between software elements

Boundaries separate things that matter from things that don’t, i.e. high-level components from low-level components

## Separate layers and organise them using the *dependency rule*

Outer layers should depend on inner layers (at the source-level), and not vice versa.

## Behaviours

## Continually visualise the technical architecture

-   Fosters common understanding of architecture to technical and non-technical stakeholders
-   Aligns to evolving architecture through techniques such as minimum viable architecture (MVA)
-   Provides value for enabling techniques such as risk storming
-   Can help with speeding up comprehension of architecture for new team members

[C4 model](https://www.google.com/url?q=https%3A%2F%2Fc4model.com%2F&sa=D&sntz=1&usg=AOvVaw37D_ZkAp1YMSvEpByhY17H)
    
-   C4 model provides a lean approach to diagramming a software architecture at multiple levels
-   Focus on providing clear meaning
-   Useful as starting point for other techniques such as risk storming

## Keep documentation close to code
We have observed that proximity of documentation to code leads to increased freshness of documentation     

 - Simplifies checking updates have been done as part of Definition of
   Done
 - Documentation / diagrams as code Change from static
 - diagrams done at the start/end of a delivery to living parts of the  
   delivery that add value in terms of domain context

[Risk Storming](https://www.google.com/url?q=https%3A%2F%2Friskstorming.com%2F&sa=D&sntz=1&usg=AOvVaw3BVCnFt1o6K9xYXddpDFY9)


## Communicate into the future

-   Communication is a key architecture skill
-   Consider the context of who you are communicating too and how it would be best received or understood
-   Simple not simplistic
-   You must consider future teams and architects, years from now decisions will be questioned and problems revisited. Shortcut that future pain by making sure the past can be understood.

[Architecture Decision Records](https://www.google.com/url?q=https%3A%2F%2Fadr.github.io%2F&sa=D&sntz=1&usg=AOvVaw0F6q-5rF3DK-brst0WDqQH)
    
-   A framework for recording choices that are architecturally significant
-   Helps with knowledge transfer over the lifetime of a product
-   The process of filling in ADRs helps solidify thinking on a decision
