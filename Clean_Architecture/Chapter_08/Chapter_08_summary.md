# Chapter 8 - Open-Closed Principle

## Key Ideas
It should be easy to extend a piece of software. The author talks about an
example where the information needs to be shown in grid. Then the stakeholders
also want to display it in a print-friendly way. This should cause little to no
modifications. Only extensions. Otherwise the architecture is not that well
designed. 

This makes me think of the different layers in the applications that I have
build. Especially the relation between the frontend and the application layer.
The developer can just create a new page in the frontend and then get all the
data from a different query, but the same source. This way you also keep in
mind the other SOLID principles.

## Core Message
> Open for extension and closed for modification.
