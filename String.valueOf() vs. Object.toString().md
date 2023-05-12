# String.valueOf() vs. Object.toString().
According to the Java documentation, *String.valueOf()* returns:

if the argument is null, then a string equal to "null"; otherwise, the value of obj.toString() is returned.
So there shouldn't really be a difference except for an additional method invocation.
Also, in the case of Object#toString, if the instance is null, a NullPointerException will be thrown, so arguably, it's less safe.
```java
public static void main(String args[]) {  
    String str = null;
    System.out.println(String.valueOf(str));  // This will print a String equal to "null"        
    System.out.println(str.toString()); // This will throw a NullPointerException
    }
 ```
  Differences between ***String.valueOf(Object) and Object.toString()*** are:
  * If string is null,
String.valueOf(Object) will return "null", whereas Object::toString() will throw a null pointer exception.
```java
public static void main(String args[]){  
    String str = null;
    
    System.out.println(String.valueOf(str));  // it will print null        
    System.out.println(str.toString()); // it will throw NullPointerException        
}  
```
