# Humble Objects

Presenters are a form of the __Humble Object__ pattern, which helps us identify and protect architectural boundaries.

## Humble Object Pattern

Split behaviors into two modules/classes. One of those modules is humble, it __contains all the hard-to-test behaviors stripped down to their bearest essence__. The other module contains all the testable behaviors that were stripped out of the humble object.

For example, GUIs are hard to unit test. However, most of the behavior of the GUI is, in fact, easy to test. Using the _Humble Object_ pattern, we can separate these two kinds of behaviors into two different classes called the `Presenter` and the `View`.

## Presenters and Views

The `View` is the humble object that is hard to test. The code in this object is kept as simple as possible. It moves data into the GUI but does not process that data.

The `Presenter` is the testable object. Its job is to accept data from the application and format it for presentation so that the View can simply move it to the screen.

For example, if the application wants a date displayed in a field, it will hand the Presenter a `Date` object. Then the Presenter will format that data into an appropriate string and place it in a simple data structure called the `View Model`, where the View can find it.

Anything and everything that appears on the screen, and that the application has some kind of control over, is represented in the `View Model` as a string, or a boolean, or an enum. Nothing is left for the View to do other than to load data from the `View Model` into the screem. Thus the `View` is humble.

## Testing and Architecture

The separation of the behaviors into testable and non-testable parts often defines an architectural boundary. The `Presenter`/`View` boundary is one of these but there are many other.

* Presenter-View
* Database Gateways
* Data Mappers
* Service Listeners

#### Database Gateways

Between the Use Case Interactors and the Database, are the database gateways. These gateways are polymorphic interfaces that contain methods for every CRUD operation that can be performed by the application on the database.

For example, the `UserGateway` interface may have a method named `getLastNamesOfUsersWhoLoggedInAfter` that takes a `Date` as its argument and returns a list of last names.

Those gateways are implemented by classes in the database layer. That implementation is the humble object. The interactors, in contrast, are not humble because they encapsulate application-specific business rules BUT interactors are _testable_, because the gateways can be replaced with appropriate stubs and test-doubles.

#### Data Mappers

ORMs would be better named "data mappers" because they load data into data structures from relation database tables. They reside in the database layer.

ORMs form another kind of _Humble O bject_ boundary between the gateway interfaces and the database.

#### Service Listeners

If your application must communicate with another services or provides a set of services, the application will load data into simple data structures and then pass those structures across the boundary to modules that properly format the data and send it to external services. On the input side, the service listeners will receive data from the service interface and format it into a simple data structure that can be used by the application. That data structure is then passed across the service boudnary.

---

# Conclusion

At each architectural boundary, we are likely to find the _Humble Object pattern_ lurking somewhere nearby. The communication across that boundary will almost always involve some kind of simple data structure, and the boundary will frequently divide something that is hard to test from something that is easy to test.

The use of this pattern at architectural boundaries vastly increases the testability of the entire system.