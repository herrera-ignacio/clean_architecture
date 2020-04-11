# Components Principles

If the Design Principles, such as SOLID, tell us how to arrange the bricks into walls and rooms, then the component principles tell us how to arrange the rooms into buildings.

Large software systems, like large buildings, are build out of smaller components.

* [Components Cohesion](./components-cohesion.md)
    * __REP__: Reuse/Release Equivalence Principle
    * __CCP__: Common Closure Principle
    * __CRP__: Common Reuse Principle

## Components

__Components are the units of deployment__.

They can be linked together into a single executable, or aggregated together into a single archive. Or they can be independently deployed as separate dynamically loadad plugins.

Well-designed components always retain the ability to be independently deployable and, therefore, independently developable.

## Linkers

If a program called a library function, the compiler would emit that name as an _external reference_. If a program defined a library function, the compiler would emit that name as an _external definition_. Then the loader could __link__ the external references to the external definitions once it had determined where it had loaded those definitions.

Linking loader allowed programmers to divide their programs up onto separately compilable and loadable segments.

Eventually, the linking loaders were too slow to tolerate. Function libraries were stored on slow devices such a magnetic tape.

Loading and linking were separated into two phases. Programmers took the slow part (that did the linking) and put it into a separate application called the _linker_. The output of the linker was a linked relocatable that a relocating loader could load very quickly. This allowed programmers to prepare an executable using the slow linker, but then they could load it quickly, at any time.

Loading time remained fast, but _compile-link times were the bottleneck__.

Computers and devices had gotten so fast that we could, once again, do the linking at load time. And so, the __component plugin architecture was born__.

---

# Conclusion

Dynamically linked files, which can be plugged together at runtime, are the software components of our architectures.