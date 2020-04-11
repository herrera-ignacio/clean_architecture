# Component Coupling

The next principles deal with the __relationships between components__.

Here again we will run into tension between develop-ability and logical design.

* ADP - Acyclic Dependencies Principle
* Top-Down Design

## ADP - Acyclic Dependencies Principle

> Allow no cycles in the component dependency graph.

Avoiding the "_morning after syndrome_" where next morning you find that your stuff no longer works because somebody changed something you depend on.

Two solutions:
* Weekly Build
* DAG - Directed Acyclic Graph
    * Applying dependency inversion principle
    * Break dependency structure with new components

#### Weekly Build

All developers ignore each other for the first four days of the week, working on private copies of the code and don't worry about integrating on collective bases. Then, on Friday, they integrate all their changes and build the system.

As project grows, it becomes less feasible to finish integrating the project on Friday. Integration burden grows until it starts to overflow into Staruday, and so on.

As the duty cycle of development versus integration decreases, the efficiency of the team decreases too. The build schedule has to be continually lengthened (increasing project risks). Integration and testing become intcreasingly harder to do, and the team loses the benefit of rapid feedback.

#### Eliminating Dependency Cycles - Directed Acyclic Graph

Solution to Weekly Build's problems is partition the development environment into releasable components. Components become units of works, that are released for use by others.

As new releases of a component are made available, other teams can decide whether they will immediately adopt the new release. 

Thus no team is at the mercy of the others. Changes made to one component do not need to have an immediate affect on other teams. Moreover, _integrations happens in small increments_.

To make it work successfully, you __must manage the dependency structure__ of the components. __There can be no cycles__.

Consider the following component diagram, it shows a rather typical structure of components assembled into an application. Notice that the structure is a _directed graph_. The components are the _nodes_ and the dependency relationships are the _directed edges_.

![component diagram](./component-diagram.png)

Regardless of which component you begin at, it is impossible to fllow the dependency relationships and wind up back at that component. This structure has no cycles. It is a __directed acyclic graph (DAG)__.

Now consider what happens then the team responsible for `Presenters` makes a new release of their components. It is easy to find out who is affected by this release, you just follow the dependency arrows backward (`View` and `Main`).

Notice also that when `Main` is released, it has utterly no effect on any of the other components in the system. They don't know about `Main`, and they don't care when it changes. This is nice.

When the developers working on the `Presenters` component would like to run a test of that component, they just need to build their version of `Presenters` with the versions of the `Interactors` and `Entities` they are currently using. None of the other components in the system need to be involved.

When it is time to release the whole system, the process proceeds from __the bottom up__.

#### Effect of a Cycle in the component dendency graph

Suppose a new requirement forces us to change one of the classes in `Entities` such that it makes use of a class in `Authorizer`.

![dependency cycle](./dependency-cycle.png)

This cycle creates some immediate problems. `Database` component must be compatible with `Entities`. However, with the cycle in place, it must _also_ be compatible with `Authorizer`. This makes `Database` more difficult to release.

This makes `Entities`, `Authorizer` and `Interactors` have become one large component. They will be stepping all over one another because they must all use exxactly the same release of one another's components.

Such cycles make it very difficult to isolate components. Unit testing and releasing become very difficult and error prone.

Morever, when there are cycles in the dependency graph, it can be __very difficult to work out the order in which you must build the components__. Indeed, there probably is no correct order.

#### Breaking the Cycle

1. __Apply the Dependency Inversion Principle (DIP)__

In our example, we could create an interface that has the methods that `User` needs. We could then put that interface into `Entities` and inherit it into `Authorizer`. This inverts the dependency between `Entities` and `Authoorizer`, thereby _breaking the cycle_.

![breaking the cycle 1](./breaking-the-cycle-1.png)

2. __Create a new component that both `Entities` and `Authorizer` depend on__

Move the class(es) that they both depend on into that new component.

![breaking the cycle 2](./breaking-the-cycle-2.png)

#### The "Jitters"

The __second solution implies__ that the component structure is __volatile in the presence of changing requirements__. Indeed, as application grows, the component dependency structure jitters and grows. Thus the dependency structure must always be monitored for cycles and broken somehow.

---

## Top-Down Design