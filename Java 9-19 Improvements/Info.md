 # Sealed class 
 is a new feature introduced in Java 15 that provides a mechanism to control the inheritance hierarchy of classes. By declaring a class as sealed, you can specify which classes are allowed to be subclasses of the sealed class.

To define a sealed class, you use the sealed modifier before the class declaration. Here's an example:

```java
public sealed class Animal permits Dog, Cat {
    // Class definition
}
```
In this example, the Animal class is declared as sealed. The permits keyword is used to specify the subclasses that are allowed to extend the Animal class, which are Dog and Cat in this case.

The subclasses of a sealed class can be either declared as final or as sealed themselves. If a subclass is declared as final, it cannot have further subclasses. If a subclass is declared as sealed, it can permit additional subclasses, continuing the inheritance hierarchy.

The main benefits of sealed classes are:

Controlled inheritance: Sealed classes allow you to restrict which classes can extend them, providing more control over the inheritance hierarchy. This helps ensure that the subclasses adhere to certain rules or restrictions defined by the sealed class.

Enhanced pattern matching: Sealed classes work well with pattern matching in switch statements. With sealed classes, the compiler can determine exhaustiveness and completeness of pattern matching, providing better type checking and error detection.

Improved encapsulation: Sealed classes can encapsulate a specific set of related subclasses, making it easier to reason about the available subclasses and their behavior.

Sealed classes are useful when you want to define a finite and controlled set of subclasses that can extend a particular class. They promote a more maintainable and predictable inheritance hierarchy, ensuring that the subclasses conform to the design and restrictions defined by the sealed class.
