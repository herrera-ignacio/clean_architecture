# Database is a Detail

From an architectural point of view, the database is a non-entity, a detail that does not rise to the level of an architectural element.

Database does not mean data model.

The structure you give to the data within your application is highly significant to the architecture of your system. But the database is not the data model. Database is just a utility that provides access to the data.

From the architecture's point of view, that utility is irrelevant because its a low-level detail, a mechanism, which a good architecture won't allow to pollute the system architecture.

## Relational Databases

While relational tables may be convenient forms of data access, there is nothing architecturally significant about arranging data into rows within tables. The use cases of your application should neither know nor care about such matters. Indeed, knowledge of the tabular structure of the data should be restricted to the lowest-level utility functions in the outer circles of the architecture.

Many data access frameworks allow database rows and tables to be passed around the system as objects. Allowing this is an architectural error. It couples the use cases, business rules, and in some cases even the UI to the relational structure of the data.

## Details

It’s just a mechanism we use to move the data back and forth between the surface of the disk and RAM. The database is really nothing more than a big bucket of bits where we store our data on a long-term basis.

## What about Performance?

Isn’t performance an architectural concern? Of course it is—but when it comes to data storage, it’s a concern that can be entirely encapsulated and separated from the business rules.

---

# Conclusion

The organizational structure of data, the data model, is architecturally significant.
The technologies and systems that move data on and off a rotating magnetic surface
are not. Relational database systems that force the data to be organized into tables
and accessed with SQL have much more to do with the latter than with the former.
The data is significant. The database is a detail.