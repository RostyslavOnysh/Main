# Java - What is OOP?
## OOP stands for Object-Oriented Programming.

Procedural programming is about writing procedures or methods that perform operations on the data, 
while object-oriented programming is about creating objects that contain both data and methods.

### Object-oriented programming has several advantages over procedural programming:

* OOP is faster and easier to execute
* OOP provides a clear structure for the programs
* OOP helps to keep the Java code DRY "Don't Repeat Yourself", and makes the code easier to maintain, modify and debug
* OOP makes it possible to create full reusable applications with less code and shorter development time

## Tip:

### *The "Don't Repeat Yourself" (DRY)* principle is about reducing the repetition of code. 
You should extract out the codes that are common for the application, and place them at a single place and reuse them instead of repeating it.
  # Encapsulation                                                 
The meaning of Encapsulation, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:
declare class variables/attributes as private
provide public get and set methods to access and update the value of a private variable
 # Get and Set                      
You learned from the previous chapter that private variables can only be accessed within the same class (an outside class has no access to it). However, it is possible to access them if we provide public get and set methods.
*The get method returns the variable value, and the set method sets the value.*
Syntax for both is that they start with either get or set, followed by the name of the variable, with the first letter in upper case:
```java
public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String newName) {
    this.name = newName;
  }
}
```                                                   
## Why Encapsulation?
Better control of class attributes and methods
Class attributes can be made read-only (if you only use the get method), or write-only (if you only use the set method)
Flexible: the programmer can change one part of the code without affecting other parts
Increased security of data
