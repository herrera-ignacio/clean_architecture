# Main Component

In every system, there is at least one __component that creates, coordinates, and oversees the others__. We call this component `Main`.

## Ultimate Detail

The `Main` component is the ultimate detail, the __lowest-level policy__. It is the __initial entry point of the system__. Nothing depends on it. Its job is to create all the Factories, Strategies, and other global facilities, and then hand control over to the high-level abstract portions of the system.

It is in the `Main` component that __dependencies should be injected__ by a Dependency Injection framework. `Main` should distribute those dependencies normally, without using the framework.

Think of `Main` as the dirtiest of all the dirty components.

---

# Conclusion

Think of `Main` as a plugin to the application. A plugin that sets up the initial conditions and configurations, gathers all the outside resources, and then hands control over to the high-level policy of the application. Since it is a plugin, it is possible to have many `Main` components, one for each configuration of your application.

You could also have `Main` plugin for each country or customer you deploy for example.