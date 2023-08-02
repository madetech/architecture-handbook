# Structurizr
We recommend using the [C4 Model](https://c4model.com/) in conjunction with the [Structurizr DSL](https://github.com/structurizr/dsl) as a way to automatically generate the C4 diagrams from code. This allows for the Structurizr code to be kept in the same repository as the code of the system, making it easier to keep the two up to date together.

A [Structurizr Lite quick start template](https://github.com/madetech/structurizr-template) has been created that you can use as a starting point in your own projects. 

## Quick overview
All the code to define the model, relationships and views are held in a single `workspace.dsl` file that Structurizr uses to build the visual diagams.
![Structurizr workspace](/images/structurizr_workspace.jpg)

The following code will generate a very simple diagram showing a basic relationship between a user and a software system
```
workspace {
  model {
    u = person "User"
    s = softwareSystem "Software System" 

    u -> s "uses"
  }
  views {
    container s {
       include *
       autoLayout
  }
}
```

## Watch
### Structurizr: Software architecture models as code CoP session (1st August 2023)
[![Software architecture models as code](/images/structurizr.jpg)](https://drive.google.com/file/d/1mJ2TpHPmiwDel0GhoIQdVv87cXfTwLCf/view)

Peter Bridger explains how to get up and running with Structurizr to create your own interactive diagrams, along with using the documentation and ADR abilities of Structurizr Lite using the quick start template mentioned previously.

- [Recording](https://drive.google.com/file/d/1mJ2TpHPmiwDel0GhoIQdVv87cXfTwLCf/view)
- [Slides](https://docs.google.com/presentation/d/1WDT0kEZoicyoUUp96QXznWwGv8lmvfAno0s_irAkXX0/edit#slide=id.g25db1f62abd_0_0)

### Futher reading
- [Structurizr](https://structurizr.com/) project website
- [Structurizr Lite](https://structurizr.com/help/lite) free version
- [Structurizr DSL language reference](https://github.com/structurizr/dsl/blob/master/docs/language-reference.md)
