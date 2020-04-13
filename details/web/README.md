# Web is a Detail

At first we thought all the computer power would be in server farms, and the browsers would be stupid. Then we started putting applets in the browsers. But we didn’t like that, so we moved dynamic content back to the servers.

But then we didn’t like that, so we invented Web 2.0 and moved lots of processing back into the browser with Ajax and JavaScript. We went so far as to create whole huge applications written to execute in the browsers. And now we’re all excited about pulling that JavaScript back into the server with Node. 

## Endless Pendulum

This oscilattions didn't start with the web. Before the web, there was client–server architecture. Before that, there were central minicomputers with arrays of dumb terminals. Before that, there were mainframes with smart green-screen terminals (that were very much analogous to modern-day browsers). Before that, there were computer rooms and punched cards ... 

As architects, though, we have to look at the long term. Those oscillations are just short-term issues that we want to push away from the central core of our business rules.

## The Upshot

The upshot is simply this: __The GUI is a detail. The web is a GUI__. So the web is a
detail. And, as an architect, you want to put details like that behind boundaries that
keep them separate from your core business logic.

Think about it this way: The WEB is an IO device. In the 1960s, we learned the value of writing applications that were device independent. The motivation for that independence has not changed. The web is not an exception to that rule.

Or is it? The argument can be made that a GUI, like the web, is so unique and rich that it is absurd to pursue a device-independent architecture. When you think about the intricacies of JavaScript validation or drag-and-drop AJAX calls, or any of the plethora of other widgets and gadgets you can put on a web page, it’s easy to argue that device independence is impractical. To some extent, this is true. The interaction between the application and the GUI is “chatty” in ways that are quite specific to the kind of GUI you have. The dance between a browser and a web application is different from the dance between a desktop GUI and its application. Trying to abstract out that dance, the way devices are abstracted out of UNIX, seems unlikely to be possible.

But another boundary between the UI and the application can be abstracted. The business logic can be thought of as a suite of use cases, each of which performs some function on behalf of a user. Each use case can be described based on the input data, the processing preformed, and the output data.

The complete input data and the resultant output data can be placed into data structures and used as the input values and output values for a process that executes the use case. With this approach, we can consider each use case to be operating the IO device of the UI in a device-independent manner.

---

# Conclusions

This kind of abstraction is not easy, and it will likely take several iteratios to get just right. But it is possible. And since the world is full of marketing geniuses, it's not hard to make the case that it's often very necessary.