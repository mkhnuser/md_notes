# OOP

## OOP vs Functional Programming

Instead of creating a stream of data in case of Functional Programming,
you change state of objects, which is complex to track and test,
which is a drawback of object-oriented programming.

## Encapsulation

Encapsulation might refer to:

* Bundling of data and methods;
* Restriction of direct access to some of object's attributes.

      The above concept also known as information hiding.
      This allows one to preserve state invariance -
      an object won't end up in inconsistent state.

## Abstraction

Abstraction exposes a simple interface to the complex internal state of an object.

### Abstract Data Types

ADTs allow you to hide the internal implementation of an data structure
by declaring an interface.

## Inheritance

One might argue that inheritance trees should be wide, not deep,
which allows one to comprehend the code easily.

### Implementation Inheritance vs Interfaces

In many cases one should prefer interfaces to concrete inheritance
since changing the logic in the base class
can cause side effects in children.

### Inheritance vs Subtyping

Type Substitution can be used instead of inheritance.

# TODO: Investigate this concept in-depth.

## Polymorphism

Polymorphism ~= many forms, the same function signature across multiple types,
but different internal implementation.

There are many types of polymorphism.

## Conclusion

Refer to Wikipedia articles on each topic.
