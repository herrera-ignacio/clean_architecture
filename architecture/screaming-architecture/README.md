# Screaming Architecture

* Theme
* Purpose
* About the web
* Frameworks as tools, not ways of life
* Testable Architecture

## Theme

Software architectures are __structures that support the use cases of the system__. Just as the plans for a house or a library scream about the use cases of those buildings, so should the architecture of a software application scream about the use cases of the application.

Architectures are not (or should not be) about frameworks. Architectures should not be supplied by framework. Frameworks are tools to be used, not architectures to be conformed to.

## Purpose

A good software architecture allows decisions about frameworks, databases, web servers, and other environmental issues and tools to be deferred and delayed. _Frameworks are options to be left open_. A good architecture makes it easy to change your mind about those decisions too. It emphasizes the use cases and decouples them from peripheral concerns.

---

## About the Web

The web is a __delivery mechanism (IO device)__, and your application architecture should treat it as such. The fact that your application is being delivered over the web is a detail and should not dominate your system structure. Indeed, the decision that your application will be delivered over the web is one that you should defer.

You should be able to deliver it as a console app, a web app, or a thick client app, or even a web service app, without undue complication or change to the fundamental architecture.

## Framework as tools, not ways of life

Look at each framework with a jaded eye, skeptically. Ask yourself how you should use it, and how you should protect yourself from it.

Think about __how can you preserve the use-case emphasis of your architecture__. Develop a strategy that prevents the framework from taking over that architecture.

## Testable Architectures

You should be able to unit-test all use-cases without any of the frameworks in place. You shouldn't need the web server running to run your tests. You shoudln't need the database connected to run your tests. Your _Entity_ objects should be plain old objects that have no dependencies on frameworks or databases or other complications.

Your use case objects should coordinate your Entity objects. Finally, all of them together should be testable in situ, without any of the complications of frameworks.

---

# Conclusion

Your architecture should tell readers about the system, not about the frameworks you used in your system.

If you are building a health care system, then when new programmers look at the source repository, their first impression should be, "Oh, this is a health care system.". Those new programmers should be able to learn all the use cases of the system, yet still not know how the system is delivered.