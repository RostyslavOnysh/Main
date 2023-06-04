# Switch Expressions:
Java 12 introduced a new form of the switch statement that allows the use of expressions. Prior to Java 12, the switch statement could only be used as a statement, but now it can also be used as an expression. Some features of switch expressions include:
* Simplified syntax: Switch expressions have a more concise and simplified syntax compared to traditional switch statements. They use the -> operator instead of the case and break keywords.
* Return values: Switch expressions can return a value directly, which allows for more compact and expressive code.
* Pattern matching: Switch expressions can use pattern matching to match against multiple cases in a single expression, making it easier to handle complex scenarios.
Here's an example of using switch expressions in Java 12:

```java
public class SwitchExample {
    public static void main(String[] args) {
        int dayOfWeek = 3;

        String dayType = switch (dayOfWeek) {
            case 1, 2, 3, 4, 5 -> "Weekday";
            case 6, 7 -> "Weekend";
            default -> throw new IllegalArgumentException("Invalid day of the week: " + dayOfWeek);
        };

        System.out.println("Day type: " + dayType);
    }
}
```
In this example, the switch expression matches the value of dayOfWeek and returns the corresponding day type as a string.

