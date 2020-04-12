# Test Boundary

> Tests are part of the system, and they participate in the architecture just like every other part of the system does.

## Test as System Components

From an architectural point of view, all tests are the same. Whether they are the tiny little tests created by TDD, or large Cucumber, SpecFlow or JBehave tests, they are architecturally equivalent.

Test, by their very nature, follow the _Dependency Rule_. They are very detailed and concrete, and always depend inward toward the code being tested. In fact, you can think of the tests as the outermost circle in the architecture. Nothing within the system depends on the tests, and they always depend inward on the components of the system.

## Design for Testability

Tests that are not well integrated into the design of the system tend to be fragile, and they make the system rigid and difficult to change.

The issue, of course, is coupling. Tests that are strongly coupled to the system must change along with the system. Even the most trivial change to a system component can cause many coupled tests to break or require changes.

This is known as the __Fragile Tests Problem__.

Fragile tests often have the perverse effect of making the system rigid. When developers realize that simple changes to the system can cause massive test failures, they may resist making those changes.

Solution is __design for testability__. The first rule of software design, whether for testability or for any other reason, is always the same:

> Don't depend on volatile things.

## The Testing API

To accomplish design for testability, create specific API that tests can use to verify all the business rules. API should have superpowers that allow the tests to avoid security constraints, bypass expensive resources (such as databases), and force the system into particular testable states.

This API will be a superset of the suite of _interactors_ and _interface adapters_ that are used by the user interface.

The purpose of the testing API is to decouple the tests from the application. This decoupling encompasses more than just detaching the tests from the UI. The goal is to decouple the _structure_ of the tests from the _structure_ of the application.

#### Structural Coupling

Imagine a test suite that has a test class for every production class, and a set of test methods for every production method. Such a test suite is deeply coupled to the structure of the application.

When one of those production methods or classes changes, a large number of tests must change as well.

The role of the testing API is to hide the structure of the application from the tests.

Thus allowing the production code to be refactored and evolved in ways that don't affect the tests. It also allows the tests to be refactored and evolved in ways that don't affect the production code.

This separation of evolution is necessary, because as time passes, the tests tend to become increasingly more concrete and specific. In contrast, the production code tends to become increasingly more abstract and general.

#### Security

Testing API, and dangerous parts of its implementation, should be kept in a separate, independently deployable component.

---

# Conclusion

Tests are parts of the system that must be well designed if they are to provide the desired benefits of stability and regression, otherwise, they tend to be fragile and difficult to maintain.

