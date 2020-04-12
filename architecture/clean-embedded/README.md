# Clean Embedded Architecture

> Although software does not wear out, firmware and hardware become obsolte, thereby requireing software modifications.

> Although software does not wear out, it can be destroyed from within by unmanaged dependencies on firmware and hardware.

Non-embedded engineers also write firmware. You non-embedded developers essentially write firmware whenever you bury SQL in your code or when you spread platform dependencies throughout your code. Android app developers write firmware when they don’t separate their business logic from the Android API. 

## Target Hardware Bottleneck

There are many special concerns that embedded developers have to deal with that non-embedded developers do not—for example, limited memory space, real-time constraints and deadlines, limited IO, unconventional user interfaces, and sensors and connections to the real world. Most of the time the hardware is concurrently developed with the software and firmware. As an engineer developing code for this kind of system, you may have no place to run the code. If that’s not bad enough, once you get the hardware, it is likely that the hardware will have its own defects, making software development progress even slower than usual. 

One of the special embedded problems is the __target-hardware bottleneck__. When embedded code is structured without applying clean architecture principles and practices, you will often face the scenario in which you can test your code only on the target. If the target is the only place where testing is possible, the target-hardware bottleneck will slow you down.

## Clean embedded architecture is a testable embedded architecture

Apply some of the architectural principles to embedded software and firmware to help you eliminate the target-hardware bottleneck.

#### Layers

Parts become obsolete, new parts use less power or provide better performance or are cheaper. Whatever the reason, as an embedded engineer, I don’t want to have a bigger job than is necessary when the inevitable hardware change finally happens. 

There is nothing that keeps hardware knowledge from polluting all the code. If you are not careful about where you put things and what one module is allowed to know about another module, the code will be very hard to change. I’m not just talking about when the hardware changes, but when the user asks for a change, or when a bug needs to be fixed.

#### Hardware is a Detail

The line between software and firmware is typically not so well defined as the line between code and hardware.

One of your jobs as an embedded software developer is to firm up that line. The name of the boundary between the software and the firmware is the __hardware abstraction layer (HAL)__.

The same applies to _Processor_ and _Operating System_.