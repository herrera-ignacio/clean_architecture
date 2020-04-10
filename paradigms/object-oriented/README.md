# Object Oriented Programming

The three magic words that help us define object-oriented nature:
* Encapsulation
* Inheritance
* Polymorphism

Which lead to the true power of OOP: __Dependency Inversion__.

## Encapsulation

A line can be drawn around a choesive set of data and functions. Outside of that line, the data is hidden and only some of the functions are known. We can only access class/object data, through specific methods that were bundled with that data.

[Wikipedia: Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming))

## Inheritance

Mechanism of basing an object or class upon another object (prototype-based inheritance) or class (class-based inheritance), retaining similar implementation. You can also refer to subtyping for interface inheritance.

[Wikipedia: Inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))

## Polymorphism

Polymorphism is the provision of a single interface to entities of different types. There for, any of the entities can respond to a interface's request.

[Wikipedia: Polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science))

Polymorphism is an application of pointers to functions. Programmers have been using pointers to functions to achieve polymorphic behavior since Von Neumann architectures were first implemented in the late 1940s. 

OO languages have made it much safer and convenient. The problem with explicitly using pointers to functions to create polymorphic behavior is that pointers to functions are dangerous. OO languages makes polymorphism trivial.

#### The Power of Polymorphism

The plugin architecture was invented to support IO device independence. OO allows the plugin architecture to be used anywhere, for anything.

For example, programmers had written programs that read input data from decks of card, and then punched new decks of cards as output. Later, customers had stopped giving them decks of cards and had started giving them reels of magning tape instead. That was very inconvenient, because it meant rewriting large portions of the original program. It would be very convenient if the same program worked interchangeably with cards or tape.

---

## Dependency Inversion: Power of OOP

In software before a safe and convenient mechanism for polymorphism, there was a typical calling tree, where main functions called high-level functions, called mid-level functions, which called low-level functions.

In that calling tree, however, source code dependendecies inexorably followed the flow of control.

For `main` to call one of the high-level functions, it had to mention the name of the module that contained that function in C, this was a `#include`.

This requirement presented the software architect with a few, if any, options. The flow of control was dictated by the behavior of the system, and the source code dependencies were dictated by that flow of control.

When polymorphism is brought into play, however, something very different can happen.

We can call other functions through an interface. At runtime, the interface doesn't exist. The source code dependency points in the opposite direction compared to the flow of control.

OO, with safe and convenient polymorphism, means that __any source code dependency, no matter where it is, can be inverted__, by inserting an interface between them.

Now, in systems written in OO languages, software architects have _absolute control_ over the direction of all source code dependencies, not being constrained to align those dependencies with the flow of control. No matter which module does the calling and which module is called, the software architect can point the source code dependency in either direction.

Now you can arrange the source code dependencies of your system so that the database and UI depend on the business rules, rather than the other way around. UI and database can be plugins to the business rules. This means, the source code of business rules, never mentions the UI or the database.

As a consequence, the business rules, the UI, and the database can be compiled into three separate components or deployment units, that have the same dependencies as the source code. In turn, business rules can be _deployed independently_.

---

## Conclusion

To the software architect, OO is the __ability__ through the use of __polymorphism__, to gain __absolute control over every source code dependency in the system__.

It allows the architect to create a __plugin architecture__, in which modules that contain high-level policies are independent of modules that contain low-level details.

Plugin modules can be deployed and developed independently from the modules that contain high-level policies.