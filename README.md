# Scala Auxiliary Constructor Subclass Bug

This repository demonstrates a subtle bug in Scala related to auxiliary constructors and subclassing.  When a subclass uses an auxiliary constructor, and that constructor attempts to call another constructor within the subclass, it can lead to unexpected compilation errors or runtime issues.

The main issue lies in the interaction between Scala's constructor initialization and the way auxiliary constructors are invoked in subclasses.  The standard approach of calling `this()` within the subclass's auxiliary constructor is insufficient when the superclass has an auxiliary constructor, as the superclass constructor needs explicit calling in the subclass.

## How to Reproduce

1. Clone this repository.
2. Compile and run `MyClass.scala`. This will compile and run fine.
3. Compile and run `MySubClass.scala`.  This will produce a compilation error.

## Solution

The solution is to explicitly invoke the superclass's constructor directly within the subclass's auxiliary constructor using `super()` to correctly initialize the superclass fields before initializing the subclass fields. See the corrected version in the solution file.

## Additional Notes

This issue highlights the importance of carefully considering the order of constructor calls and superclass initialization when working with inheritance and auxiliary constructors in Scala.