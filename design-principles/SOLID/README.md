# SOLID

Solid principles tell us how to arrange our functions and data structures into classes, and how those classes should be interconnected.

> A  class is simply a coupled groupoing of functions and data, and does not imply these principles are applicable only to object-oriented software.

We'll focus on the architectural implications of those principles instead of their details. You would be advised to further research them.

#### The Goal

The goal of the principles is the _creation of mid-level software structures_ that:

* Tolerate change
* Are easy to underdstand
* Are the basis of components that can be used in many systems

The term "_mid-level_" refers to the fact that these principles are applied by programmers working at the _module level_. Just above the level of the code and help to define the kinds of structures used within modules and components.

Just as it is possible to create a substantial mess with well-made bricks of code, so it is also possible to create a system-wide mess with well-designed mid-level components. For this reason, above SOLID principles, we have its counterparts in the component world, and then the principles of high-level architecture.

## The 5 Principles

#### [SRP - Single Responsibility Principle](./SRP.md)

The best structure for a software system is _heavily influenced by the social structure of the organization that uses it_ so that each software module has one, and only one, reason to change.

#### OCP - Open Close Principle

For software systems to be easy to change, they must be designed to allow the behavior to be changed by adding new code, rather than changing existing code.

#### LSP - Liskov Substitution Principle

To build software systems from interchangeable parts, those parts must adhere to a contract that allows those parts to be substituted one for another (Liskov's famous definition of subtypes).

#### ISP - Interface Segregation Principle

Software designers should avoid depending on things that they don't use.

#### DIP - Dependency Inversion Principle

The code that implements high-level policy should not depend on the code that implements low-level details. Rather, _details should depend on policies_.

---
