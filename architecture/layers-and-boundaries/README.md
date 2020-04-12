# Layers and Boundaries

Some very smart people have told us, over the years, that we should not anticipate the need for abstraction.

> You aren't going to need it - YAGNI.

Over-engineering is often much worse than under-engineering. On the other hand, when you discover that you truly do need an architectural boundary where none exists, the costs and risks can be very high to add such a boundary.

As a Software Architecture you must guess _intelligently_. You must weight the costs and determine where the architectural boundaries lie, and which should be fully implemented, partially implemented or ignored.

But __this is not a one-time decision__. You don't simply decide at the start of a project which boundaries to implement and which to ignore. Rather, __you watch__. You pay attention as the system evolves. You note where boundaries may be required, and then carefully watch for the first inkling of friction because those boundaries don't exist.

You frequently review the decision of implement those boundaries versus the cost of ignoring them.