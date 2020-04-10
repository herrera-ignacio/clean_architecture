# Structured Programming

Dijkstra applied the mathematical discipline of _proof_. His vision was the construction of a Euclidian hierarchy of postulates, theorems, corollaries and lemmas. Dijkstra though that programmers could use that hierarchy the way mathematicians do. In other words, programmers would use proven structures, and tie them together with code that they would then prove correct themselves.

During his investigation, Dijkstra discovered that certain uses of `goto` statements prevent modules from being decompsed recursively into smaller and smaller units, thereby preventing use of the divide-and-conquer approach necessary for reasonable proofs.

However, Dijkstra realized that there were "good" uses of `goro` corresponded to simple selection and iteration control structures such as `if/then/else` and `do/while`. Modules that uses only those kind of structures could be recursively subdivided into provable units.

Böhm and Jacopini, proved before that all programs can be constructed from just three structures:
* Sequence
* Selection
* Iteration

This discovery was remarkable, the very control structures that made a module provable were the same minimum set of control structures from which all programs can be built. Thus structured programming was born.

Nowadays we are all structured programmers, through not necessarily by choice. It's just that our languages don't give us the option to use undisciplined direct transfer of control.

## Functional Decomposition

You can take large-scale problem statements and decompose them into high-level functions, which can also be decomposed into lower-level functions, ad infinitum. Moreover, each of those decomposed functions can be represented using the restricted control structures of structured programming.

Structured design became popular in the late 1970s and throughout the 1980s. Programmers could break down large proposed systems into modules and components that could be further broken down into tiny provable functions.

## Scientific Method and Tests

Science does not work by proving statements true, but rather by proving statement false. Those that we cannot prove false, after much effort, we deem to be true enough for our purposes.

> "Testing shows the presence, not the absence, of bugs." - Dijkstra

A program can be proven incorrect by a test, but it cannot be proven correct. Tests allow us to deem a program to be _correct enough_ for our purposes.

Software is like a science. We show correctness by failing to prove incorrectness, despite our best efforts. Such proofs of incorrectness can be applied only to _provable_ programs. Structured programming forces us to __recursively decompose a program into a set of small provable functions__.

## Conclusion

It is this ability to create falsifiable units of programming that makes structured programming valuable today. Moreover, at the architectural level, this is why we still consider _functional decomposition_ to be one of our best practices.

Software architects strive to define modules, components, and services that are _easily falsifiable (testable)_. To do so, they employ restrictive disciplines similar to structured programming, at a much higher level.

