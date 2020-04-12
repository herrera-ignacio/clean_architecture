# Architecture

* Introduction
    * The Definition
    * Development
    * Deployment
    * Operation
    * Maintenance
    * Keeping Options Open
    * Device Independence
* [Independence (decoupling)](./independence/README.md)
* [Boundaries and Plugin Architecture](./boundaries/README.md)
* [Boundary Anatomy](./boundary-anatomy/README.md)
* [Policy and Level](./policy-level/README.md)
* [Business Rules, Entities and Use Cases](./business-rules/README.md)
* [Screaming Architecture](./screaming-architecture/README.md)
* [Clean Architecture](./clean-architecture/README.md)
* [Humble Object Pattern](./humble-objects/README.md)
* [Partial Boundaries](./partial-boundaries/README.md)
* [Layers and Boundaries](./layers-and-boundaries/README.md)
* [Main Component](./main-component/README.md)
* [Services](./services/README.md)
* [Test Boundary](./test-boundary/README.md)
* [Clean Embedded Architecture](./clean-embedded/README.md)

## The Definition

The architecture of a software system is the shape given to that system by those who build it. The form of that shape is in __the division of that system into components, the arrangement of those components, and the ways in which those components communicate with each other__.

The purpose of that shape is to facilitate the development, deployment, operation and maintenance of the software system contained within it.

> The strategy behind that facilitation is to leave as many options open as possiblem, for as long as possible.

The architecture of a system has very little bearing on whether the system works. There are many systems out there, with terrible architectures, that work just fine. Their troubles do not lie in their operation, rather, they occur in the deployment, maintenance, and ongoing development.

Good architecture __makes the system easy to understand, develop, maintain and deploy__. The ultimate goal is to __minimize the lifetime cost of the system and maximize programmer productivity__.

## Development

Different team structures imply different architectural decisions.

Small teams for example, of five developers, can quite effectively work together to develop a monolithic system without well-defined components or interfaces. Such team would likely find the strictures of an architecture something of an impediment during the early days of development. This is likely _the reason why so many systems lack good architecture_. They were begun with none, because the team was small and did not want the impediment of a superstructure.

On the other hands, a system being developed by multiple teams, cannot make progress unless the system is divided into well-defined components with reliably stable interfaces. The architecture of that system will likely gravitate toward into a component-per-team architecture if they are driven solely by development schedule, which is not likely to be the best architecture for deployment, operation and maintenace of the system.

## Deployment

A software system must be deployable. The higher the cost of deployment, the less useful the system is. A goal of software architecture, then, should be to make a system that can be easily deployed _with a single action_.

Architects should considered deployment issues early on.

## Operation

The impact of architecture on system operation tends to be less dramatic. Almost any operational difficulty can be resolved by throwing more hardware without drastically impacting the software architecture.

Architectures that impede operation are not as costly as architectures that impede development, deployment and maintenance. 

__A good software architecture communicates the operational needs of the system__. It makes the operation of the system readily apparent to the developers. It should __elevate the use cases, features, and required behaviors of the system to first-class entities that are visible landmarks for the developers__.

## Maintenance

The most costly aspect of a software system. The never ending parade of new features and the inevitable trail of defects and corrections consume vast amounts of human resources.

The primary cost of maintenance is __spelunking__ and risk.

A good architecture vastly mitigates these costs. By separating the system into components, and isolating those components through stable interfaces, it is possible to illuminate the pathways for future features and greatly reduce the risk of inadvertent breakage.

#### Spelunking

_Spelunking_ is the cost of digging through the existing software, trying to determine the best place and the best strategy to add a new feature or to repair a defect.

#### Risk

While making such changes, the likelihood of creating inadvertent defects is always there, adding to the cost of risk.

---

## Keeping Options Open

We mentioned earlier that software has __two types of values__:

* Behavior
* Structure (greater, because makes software _soft_)

Software was invented because we needed a way to quickly and easily change the behavior of machines. That flexibility depends critically on the shape of the system, the arrangement and interconnection of its components.

Software systems can be decomposed into two major elements:
* _Policy_: embodies all the business rules and procedures, the true value of the system lays here
* _Details_: necessary to enable humans, other systems and programmers to communicate with the policy but do not impact the behavior of the policy at all (IO devices, databases, servers, etc).

The goal of the architect is to create a shape for the system that __recognizes policy as the most essential element of the system while making the details _irrelevant_ to that policy__. This allows decisions about those details to be _delayed_ and _deferred_.

The longer you wait to make those decisions, _the more information you have with which to make them properly_, and the more experiments you run.

What if the decisions have already been made by someone else like your company? __A good architect pretends that the decision has not been made__ and shapes the system such that those decisions can still be deferred or changed for as long as possible.

> A good architect maximizes the number of decisions not made.

---

## Device Independence

We write our programs without knowing or caring which device would be used. Our programs have a shape that disconnects policy from detail (devices). An example of this is IO devices, we communicate to them usually through our operating system abstractions.

---

# Conclusion

Good architects carefully separate details from policy, and then decouple the policy from the details so throughly that the policy has no knowledge of the details and does not depend on the details in any way.

Design the policy so that decisions about the details can be delayed and deferred for as long as possible.