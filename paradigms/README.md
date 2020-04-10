# Paradigms Overview

* [Structured Programming](./structured/README.md)
* Object-Oriented Programming
* Functional Programming

## Structured Programming

> Structured programming imposes discipline on direct transfer of control.

## Object-Oriented Progamming

Dahl and Nygaard, two programmers, discovered in 1966 that the function call stack frame in the `ALGOL` language could be moved to a heap, thereby allowing local variables declared by a function to exist long after the function returned.

The function became a class constructor, local variables became instance variables, and nested funcions became methods. This led inevitably to the discovery of _polymorphism_ through the disciplined use of function pointers.

> OOP imposes discipline on __indirect__ transfer of control.

## Functional Programming

Alonzo Church, in 1936 invented `l-calculus` while pursuing the same mathematical problem that was motivating Alan Turing at the same time, which is the foundation of the `LISP` language, invented in 1958 by John McCarthy.

A foundational notion of `l-calculus` is __immutability__, that is, the notion that the values of symbols do not change. This effectively means that a functional language has no assignment statement.

> Functional programming imposes discipline upon assignment.

---

# Why is it important?

* We use polymorphism as the mechanism to cross architectural boundaries
* We use functional programming to impose discipline on the location of and access to data
* We use structured programming as the algorithmic foundation of our modules

Those three align with the three big concerns of architecture:

* Function
* Separation of components
* Data management