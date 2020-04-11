# Independence

A good architecture must support:

* Use cases and operation of the system
* Maintenance of the system
* Development of the system
* Deployment of the system

How to do it ?
* Leaving Options Open
* Decoupling Layers
* Decoupling Use Cases
* Decoupling Mode
    * Source level
    * Deployment level
    * Service level
* Independent Develop-Ability
* Independent Deployability
* Duplication

## Use Cases

Architecture of the system must support the intent of the system. This is the first priority of the architecture.

The most important thing a good architecture can do to __support behavior__ is to __clarify and expose that behavior so that the intent of the system is visible at the architectural level__.

The use cases of that system will be plainly visible within the structure of that system. Developers will not have to hunt for behaviors, they will be first-class elements visible at the top level of the system.

## Operation

Architecture plays a more substantial role in supporting the operation of the system. If the system must handle 100,000 customers per second, the architecture must support that kind of throughput and response time for each use case that demans it.

As a strange as it may seem, the decisions on how to accomplish this, is one of the options that a good architect leaves open. An architecture than maintains the proper isolation of its component, and does not assume the means of communication between those components, will be much easier to transition through the spectrum of threads, processes, and services as the operaitonal needs of the system change over time.

## Development

> Any organization that designs a system will produce a design whose structure is a copy of the organization's communication structure.

Architecture seeks to facilitate actions by organization's teams, so that the teams do not interfere with each other during development.

This is accomplished by properly partitioning the system into well-siolated, independently developable components.

## Deployment

Architecture plays a huge role in determining the ease with which the system is deployed. The goal is "_immediate deployment_. A good architecture does not rely on dozens of little configuration scripts and property file tweaks. It does not require manual creation of directories or files that must be arranged just so.

Again, this is achieved by propery partitioning and isolation of the components of the system, including those master components that tie the whole system together and ensure that each component is properly started, integrated, and supervised.

--- 

## Leaving Options Open

A good architecture balances all of these concerns with a component structure that mutually satisfies them all (this is of course pretty hard).

Most of the times, __we don't know what all the uses cases are, nor do we know the operational constraints, team structure, or deployment requirements__. Worse, even if we did know them, they will __inevitable change as the system moves through its life cycle__.

That's why, a good architecture makes the system easy to change, in all the ways that it must change, by leaving options open.

## Decoupling Layers

The architect _does_ know the basic intent of the system. So the architect can employ the _Single Responsibility Principle_ and the _Common Closure Principle_ to separate those things that change for different reasons, and to collect those things that change for the same reasons.

What changes for different reasons? There are some obvious things. User interfaces change for reasons that have nothing to do with business rules. There are busines srules closely tied to the application itself, for example, validation of input fields. While others are more closely associated with the domain, for example calculation of interest on an account. These two different kinds of rules will change at different rates, and for different reasons.

Thus we find the system divided into decoupled horizontal layers:
* UI
* Application specific business rules
* Application independent business rules (domain)
* Database
* Etc...

## Decoupling Use Cases

Use cases change for different reasons and at different rates, then __use cases are a very natural way to divide the system__.

At the same time, use cases are narrow vertical slices that cut through the horizontal layers of the system. Each use case uses some UI, application-specific business rules, application-independent business rules, and some database functionality.

Thus, as we are dividing the system in to horizontal layers, we are also dividing the system into thin vertical use cases that cut through those layers.

## Decoupling Mode

The decoupling that we did for the sake of the use cases also helps with operations, but must have the appropriate mode. To run in separate servers, the separated components cannot depend on being together in the same address space of a processor, the must communicate over a network of some kind.

Many architects call such components "services" or "micro-services", depending upon some vague notion of line count. This is called __Service Oriented Architecture (SOA)__.

Sometimes, we have to separate our components all the way to the service level.

Remember, a good architecture leaves options open. _The decoupling mode is one of those options_.

There are many ways to decouple layers and use cases:

* Source level (Monolithic)
* Deployment level
* Service level

One popular solution at the moment, is to simply decouple at the service level by default. A problem with this approach is that it is expensive both in development time and in system resources, and encourages coarse-grained decoupling.

Another solution is to push the decoupling to the point where a service _could_ be formed, should it become necessary, but leave the components in the same address space as long as possible.

The project then can gradually shift the system in the services direction.

A good architecture will allow a system to be born as a monolith, deployed in a single file, but then to grow into a set of independent services. Later, as things change, it should allow for reversing that progression and sliding all the way back down into a monolith.

A good architecture protects the majority of the source code from those changes. It leaves the decoupling mode open as an option so that large deployments can use one mode, whereas small deployments can use another.

#### Source level - The monolithic structure

We can control the dependencies between source code modules so that changes to one module do not force changes or recompilation of others.

In this decoupling mode, all the components execute in the same address space, and comunicate with each other using simple function calls.

#### Deployment level

Control the dependencies between deployable units such as jar files, DLLs, or shared libraries, so that changes to the source code in one module do not force others to be rebuilt and redeployed.

Many components may still live in the same address space, and communicate through function calls. Other components may live in other processes in the same processor, and communicate through interprocess communications, sockets, or shared memory.

#### Service level

Reduce the dependencies down to the level of data structures, and communicate solely through network packets such that every execution unit is entirely independent of source and binary changes to others (e.g. _Service Oriented Architecture_).

## Independent Develop-Ability

When components are strongly decoupled, the interference between teams is mitigated. So long as the layers and use cases are decoupled, the architecture of the system will support the organization of the teams, irrespective of whether they are organized as feature teams, component teams, layer teams, or some other variation.

## Independent DDeployability

Decoupling of use cases and layers also affords a high degree of flexibility in deployment. It should be possible to _hot-swap layers_ and use cases in running systems. Adding a new use case could be as simple as adding a few new plugin files or services to the system while leaving the rest alone.

## Duplication

> Architects often fall into the trap that hinges on their fear of duplication.

There are different kinds of duplication. There is _true duplication_, in which every change to one instance necessitates the same change to every duplicate of that instance.

Then there is _false_ or _accidental duplication_. __If two apparently duplicated sections of code evolve along different paths__ (they change at different rates, and for different reasons), __then they are not true duplicates__. They will end up very different from each other.

Now imagine two use cases that have very similar screen structures. The architects will likely be strongly tempted to share the code for that structure. But should they? As time goes by, the odds are that those two screens will diverge and eventually look very different. For this reason, care must be taken to avoid unifying them. Otherwise, separating them later will be a challenge.

When you are vertically separating use cases from one another, you will run into this issue, and your temptation will be to couple the use cases because they have similar screen structures, or similar algorithms, or similar database queries and/or schemas. Be careful. Resist the temptation to commit the sin of _knee-jerk elimination of duplication_. Make sure the duplication is real. It's much more important to __keep the layers properly decoupled__.

---

# Conclusion

Decoupling mode of a system is one of those things that is likely to change with time, and a good architect __forsees and appropariately facilitate those changes__.