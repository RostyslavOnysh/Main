 # PECS is an abbreviation for :
 ## "Producer Extends Consumer Super".
 PECS principle is used with generics to achieve the inheritance hierarchy (covariance) because initially generics do not support the inheritance hierarchy (generics are invariant).

# Invariance, covariance, and contravariance
Variance refers to how subtyping between more complex types (for example, collections) relates to subtyping between their components (elements inside the collection).

Imagine that we have two types - Animal and Cow, and Cow is a subtype of Animal. Then:

List<Animal> is covariant if List<Cow> is a subtype of List<Animal>;
List<Animal> is contravariant if List<Animal> is a subtype of List<Cow>;
List<Animal> is invariant if neither List<Cow> is a subtype of List<Animal>, nor vice versa.
It is important to keep in mind that generics in Java are invariant, unlike arrays that are covariant. Let's look at the following code:
```java
String[] stringArray = new String[10];
Object[] objectArray = stringArray; // everything is OK
```
Because String extends Object and arrays are covariant, String[] is a subtype of Object[]. However, with generics everything is different:

Collection<String> stringCollection = new ArrayList<>();
Collection<Object> objectCollection = stringCollection; // compile-time error

Although String extends Object, Collection<String> is not a subtype of Collection<Object> because generics are invariant.

What is the wildcard?
So what is the supertype of all kinds of collections? It's written Collection<?> (pronounced collection of unknown), that is, a collection whose element type matches anything. The symbol ? is called a wildcard type for obvious reasons. It represents an unknown type. We can write the following code and call it with any type of collection:

```java
public void printCollection(Collection<?> collection) {
    for (Object element : collection) {
        System.out.println(element);
    }
}
```
  
# Bounded wildcards
There are two types of bounded wildcards - upper bounded and lower bounded:

You can use an upper bounded wildcard to relax the restrictions on a variable. For example, imagine that you want to write a method that works on List<Integer>, List<Double>, and List<Number>, but does not accept List<String or List<Object>. You can achieve this by using an upper bounded wildcard:
```java
public void processNumbers(List<? extends Number> numbers) {
    // method logic
}
```
# To declare an upper bounded wildcard, 
use the wildcard character ?,
 followed by the extends keyword, followed by its upper bound. The processNumbers() method can now accept List<Number> as well as lists of any type that extends Number.

Similarly, a lower bounded wildcard restricts the unknown type to be a specific type or a supertype of that type. A lower bounded wildcard is expressed using the wildcard character ?, followed by the super keyword, followed by its lower bound. Look at the following method:
```java
public void processNumbersButOnlyIntegers(List<? super Integer> numbers) {
    // method logic
}
```
It accepts only List<Integer>, List<Number> and List<Object> but does not allow List<Double> because Double is not a supertype of Integer.

# PECS principle (Producer Extends Consumer Super)
 PECS stands for Producer Extends Consumer Super. This principle is mostly used when defining method parameters in methods that accept some sort of collection.

If you want to use bounded wildcard as the type of your method parameter, you need to know what will be going on in this method. If the collection that you want to receive in your method is a producer (inside the method you will take values from it) - then you need to use <? extends E> (where E is an actual type).

On the other hand, if this collection will serve as a consumer (inside the method you will put some values inside it) - you should use <? super E>.

In fact, if you try to do the opposite, you will get a compilation error.

If your method is designed the way that it both writes into and takes values from the collection, then you need to use a generic type T rather than wildcard:
```java
public <T> T addToListAndGetFirstValue(List<T> list, T value) {
    list.add(value);
    // method logic
    return list.get(0);
}
```

# The principles behind this in computer science is called

* Covariance: ***? extends MyClass,***
* Contravariance: ***? super MyClass*** and
* Invariance/non-variance:***MyClass***
