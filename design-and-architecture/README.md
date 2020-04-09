# Design and Architecture

There is no difference between _Design_ and _Architecture_.

The word "_architecture"_ is often used in the context of something at a high level that is divorced from the lower-level details, whereas "_design_" more often seems to imply structures and decisons at a lower level. But this usage is nonsensical when you look at what a real architect does.

In short, in an architecture I see all the details that support all the high-level decisions. The low-level details and the high-level structure are all part of the same whole.

## The Goal

> The goal of software architecture is to minimize the human resources required to build and maintain the required system. - Robert C. Martin

The measure of design quality is simply the measure of the effort required to meet the needs of the customer. If that effort is low, and stays low throughout the lifetime of the system, the design os good. If that effort grows with each new release, the design is bad.

## Signature of a mess

When systems are thrown together in a hurry, when the sheer number of programmers is the sole driver of output, and when little or no thought is given to the cleanliness of the code or the structure of the design, then productivity will catastrophically drain the profit from the business model and drive the company into a stall, if not into a downright collapse. The code gets more expensive to produce through every new release.

From the developers' point of view, this is tremendously frustrating, because everyone is working _hard_. Nobody has decreased their effort.

## What usually goes wrong

Developers buy into a familiar lie: "We can clean it up later, we just have to get to market first!". Of course, things never do get clenead up later, because market pressures never abate. Getting to market first simply means that you've now got a horde of competitors on your tail, and you have to stay ahead of them by running as fast as you can.

And so, developers can't go back and clean things up because they've got to get the next feature done, and the next, and so on the mess builds, and productivity continues its asymptotic approach toward zero.

The bigger lie that developers buy into is the notion that writing messy code makes them go fast in the short term, and just slows them down in the long term. The fact is that _making messes is always slower that staying clean_.

> The only way go fast, is to go well.

---

# Conclusion

Start taking the quality of your software and architecture seriously. For this, you need to know what good software architecture is. To build a system with a __design/architecture that minimize effort and maximize productivity__, you need to know which attributes of system architecture lead to that end.

We want to build systems that will have __long profitable lifetimes__.