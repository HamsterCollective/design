# Design Vision

The vision that the design should strive for is an architecture that enables functional components to be freely added and replaced by different parties.

Architectural goals:
 * it should be *expandable* with new modules without affecting existing modules
 * it should be possible to parallelize *relevant parts*.
 * the programming language a module is written in should be left as an implementation detail for the module
 * the architecture should not limit the programing languages that can be mutation tested. It should be possible to use the architecture for mutation testing of any programming language.
 * enable reuse of components. A visualization component should be reusable independent of the programming language that is mutation tested.
