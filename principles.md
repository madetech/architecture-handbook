### The Big List of Principles

## Software Design

##  Designing Components so they are *stable*

Balancing cohesion and coupling

## Set Boundaries between software elements

Boundaries separate things that matter from things that don’t, i.e. high-level components from low-level components

## Separate layers and organise them using the *dependency rule*

Outer layers should depend on inner layers (at the source-level), and not vice versa.

## No Business Logic in the User Interface

No Business Logic in the UI *unless...*

If the UI has Business Logic in the UI the project **should** include an Architecture Decision Record explaining why.

## Avoid using JavaScript in the User Interface

If the UI has JavaScript it **should** include an Architecture Decision Record. Even if the project uses standard GOV.uk/local authorities' approved components.

## Behaviours

## Continually visualise the technical architecture

[Read more here](principles/continually_visualise_the_technical_architecture.md)

## Keep documentation close to code

[Read more here](principles/keep_documentation_close_to_code.md)

## Communicate into the future

[Read more here](principles/communicate_into_the_future.md)
