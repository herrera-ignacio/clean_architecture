# Frameworks are Details

> Frameworks are not architectures, though some try to be.

## Asymmetric Marriage

The relationship between you and the framework author is extraordinarily asymmetric. You must make a huge commitment to the framework, but the framework author makes no commitment to you whatsoever.

Think about this point carefully. When you use a framework, you read through the documentation that the author of that framework provides. In that documentation, the author, and other users of that framework, advise you on how to integrate your software with the framework. Typically, this means wrapping your architecture around that framework. The author recommends that you derive from the framework’s base classes, and import the framework’s facilities into your business objects. The author urges you to couple your application to the framework as tightly as possible.

In effect, the author is asking you to marry the framework—to make a huge, long- term commitment to that framework. And yet, under no circumstances will the author make a corresponding commitment to you. It’s a one-directional marriage. You take on all the risk and burden; the framework author takes on nothing at all.

## The Risks

* Architecture of the framework is often not very clean. They ask you to inherit their code into your business objects, thus coupling their framework into that innermost circle.
* Framework may help you with some early features of your application, but as your product matures, it may outgrow the facilities of the framework and you'll find the framework fighting you more and more as time passes.
* Framework may evolve in a direction that you don't find helpful. You may be stuck upgrading to new versions that don't help you, and may even find old features disappearing or changing.
* New and better framework may come along that you wish you could switch to.

## Solution

__Don't marry the framework.__

You can _use_ the framework, just _don't couple to it_. Treat the framework as a detail that belongs in one of the outer circles of the architecture.

Don't derive your business objects from its base classes. Derive proxies instead, and keep those proxies in components that are plugins to your business rules.

Don't let frameworks into your core code. Instead, integrate them into components that plug in to your core code, following the _Dependency Rule_.

---

# Conclusion

When faced with a framework, try not to marry it right away. See if there aren’t
ways to date it for a while before you take the plunge. Keep the framework behind
an architectural boundary if at all possible, for as long as possible.