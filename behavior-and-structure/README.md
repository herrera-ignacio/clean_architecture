# Tale of Two Values

Every software system provides two different values to the stakeholders: _behavior_ and _structure_. Software developers are responsible for ensuring that both those values remain high.

## Behavior

Programmers are hired to make machines behave in a way that makes or saves money for stakeholders. We do this by helping the stakeholders develop a _functional specification_ or _requirements document_. Then we write the code that causes the stakeholder's machines to satisfy those requirements.

Many programers believe that is the entirety of their job, make the machine implement rhe requirements and fix any bugs. They are sadly mistaken.

## Structure (Architecture)

Software was invented to be "soft". It was intended to be a way to _easily change the behavior of machines_.

When the stakeholders change their minds about a feature, the difficulty in making such a change should be proportional only to the scope of the change, and not to the shape of the change.

It is this different between scope and shape that often drives the growth in software development costs. It is the reason that costs grow out of proportion the size of the requested changes (and why the first year of development is much cheaper than the second, and so on).

From the stakeholder's point of view, they are simply providing a stream of changes of roughly similar scope. From the developers' point of view, the stakeholders are giving them a stream of jigsaw puzzle pieces that they must fit into a puzzle of ever-increasing complexity. Each new request is harder to fit than the last, because the _shape of the system does not match the shape of the request_.

The problem, of course, is the architecture of the system. The more this architecture prefers one shape over another, the more likely new features will be harder and harder to fit into that structure. There fore __architectures should be as shape agnostic as possible__.

## The Greater Value 

> Is it more important for the software system to work, or to be easy to change?

* If you give me a program that works perfectly but is impossible to change, then it won't work when the requirements change and I won't be able to make it work. Therefore the program will become uselss.

* If you give me a program that does not work but is easy to change, then I can make it work, and keep it working as requirements change. Therefore the program will remain continually useful.

There are systems that are _practically_ impossible to chagne, because the cost of change exceeds the benefit of change.

#### Developers Dilemma

Business managers are not equipped to evaluate the importance of architecture. _That's what software
developers were hired to do_. Therefore it is the responsibility of the software development team to __assert the importance of architecture over the urgency of features__.

#### The Struggle

Fullfilling this responsibility means struggling. Effective software development teams tackle that struggle head on. They discuss with all the other stakeholders as equals. Remember, as a software developer, _you are a stakeholder_. __You have a stake in the software that you need to safeguard__.

If architecture comes last, then the system will become ever more costly to develop, and eventually change will become practically impossible for part or all of the system.