# DIP: Dependeny Inversion Principle

Most flexible systems are those in which __source code dependencies refer only to abstractions__, not to concretions.

In statically typed languages, this means that `import`/`include` statements should refer only to source modules containing interfaces/abstract classes.

In dynamically typed languages, source code dependencies should not refer to concrete modules (functions being called are implemented).

We tend to ignore the stable background of operating system and platform facilities when it comes to DIP, because we know we can rely on them not to change.

It is the _volatile_ concrete elements of our system that we want to avoid depending on. Those are the modules that we are actively developing, and that are undergoing frequent change.

## Stable Abstractions

Changes to concrete implementations do not always, or even usually, require changes to the interfaces they implement. Therefore interfaces are less volatile than implementations.

Indeed, good software designers and architects work hard to reduce the volatility of interfaces. They try to find ways to add functionality to implementations without making changes to the interfaces. This is Software Design 101.

* Don't refer to volatile concrete classes, refer to abstract interfaces instead.
* Don't derive from volatile concrete classes.
* Don't override concrete functions (you inherit its dependencies)
* Never mention the name of anything concrete and volatile

## Factories

To comply with these rules, the creation of volatile concrete objects requires special handling (_Abstract Factories_).

![dip factories](./dip-1.png)

The curved line is an __architectural boundary__, it divides the system into two components, abstract and concrete.

Abstract components contain all the high-level business rules of the application.

Concrete components contain all the implementation details that those business rules manipulate.

## Concrete Components

The concrete component from before, contains a single dependency, so it violates the DIP. DIP violations cannot be entirely removed, but they can be __gathered into a small number of concrete components and kept separate from the rest of the systems__.

Most systems will contain at least one such concrete component, often called `main` because it contains the `main` function. In the example above, the `main` function would instantiate the `ServiceFactoryImpl` and place that instance in a global variable of type `ServiceFactory`. The `Application` would then access the factory through that global variable.

---

# Conclusion

DIP will be the most visible organizing principle in our achitecture diagrams. The curved line will become the _architectural boundaries_. The way the dependencies cross that curved line in one direction, and toward more abstract entities, will become a new rule that we will call the _Dependency Rule_.