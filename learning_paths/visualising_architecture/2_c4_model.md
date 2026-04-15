# C4 Model
The [C4 Model](https://c4model.com/) focuses on the visual communication and documentation of software architecture. It doesn’t present a formalised, standardised method to communicate software architecture, it does however provide a collection of lightweight ideas and techniques that we've observed to be useful.

We've observed the use of the C4 Model with our active deliveries and found that it:
- Provides a lean approach to diagramming a software architecture at multiple levels
- Helps focus on providing clear and concise meaning
- Is useful as starting point for other techniques such as risk storming
- Has a wide range of diagram types that are easy to learn, create and understand
- Isn't mandatory to create versions of all of the diagrams, only use ones that appropriate. System Context and Container diagrams are the most widely used.
- Is a simple but not simplistic approach to visualising architecture

## C4 Diagram Types and Evolution

The C4 model provides four levels of abstraction for visualising software architecture. These diagrams should not be static; they must evolve alongside the software as the design matures.

| Level | Diagram Type | Focus | How it evolves |
| :--- | :--- | :--- | :--- |
| **1** | **System Context** | The system itself and its users/external systems. | Rarely changes after initial discovery; captures the "Big Picture." |
| **2** | **Container** | High-level technology choices (e.g., Web App, Database, API). | Evolves as major infrastructure decisions are made or changed. |
| **3** | **Component** | Internal structural building blocks within a container. | Changes frequently during active development as the internal design is refined. |
| **4** | **Code** | Low-level implementation details (e.g., Class diagrams). | Often generated from code or only used for complex logic; highly transient. |

### Example of Evolution

A **Container Diagram** might start during discovery with a simple "Backend API" and a "Database." As the project progresses and technical requirements become clearer, you might split that API into microservices or add a caching layer and a message queue. The diagram should be updated continuously to reflect this current state, ensuring it remains a reliable "map" for the team.

The creator of C4 Simon Brown has published a book called `Visualising Software Architecture`, which is part of our [recommended reading list](/resources.md)

## Watch
### Visualising Architecture CoP session (22nd November 2022)
[![Visualising Architecture](https://madetech.github.io/architecture-handbook/images/visualising_architecture.jpg)](https://drive.google.com/file/d/14R3OpBbcN0xbU_XeQQfG7ocehkw_U0w3/view)

**Made Tech internal only video**

Stuart McKee demonstrates how to create a common understanding and foster collaboration

- [Recording](https://drive.google.com/file/d/14R3OpBbcN0xbU_XeQQfG7ocehkw_U0w3/view)
- [Slides](https://docs.google.com/presentation/d/1wXXkyTgoNJIgyD9MDuIlvi85uGHWjIgQhvOPKTNsrHo/edit)

**Next** - [Structurizr](./3_structurizr.md)
