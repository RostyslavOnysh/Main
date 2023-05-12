# Enums
An enum is a special "class" that represents a group of constants (unchangeable variables, like final variables).
To create an enum, use the enum keyword (instead of class or interface), and separate the constants with a comma. Note that they should be in uppercase letters:
```java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
```
###You can access enum constants with the dot syntax:
Level myVar = Level.MEDIUM;
