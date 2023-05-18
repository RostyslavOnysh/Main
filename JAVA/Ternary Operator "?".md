# Ternary Operator
```java
public int matchResult(int result1, int result2, int bet1, int bet2) {
    return result1 == bet1 && result2 == bet2 ? 2 :
           (result1 > result2 && bet1 > bet2 || result1 < result2 && bet1 < bet2 || result1 == result2 && bet1 == bet2) ? 1 : 0;
}
```
This code is using ***two nested ternary operators*** to determine the outcome of the user's bet based on the match result and the user's prediction.

* The first ternary operator checks if the user's prediction is a perfect match with the match result.
If the condition result1 == bet1 && result2 == bet2 is true, t
hen the result of the bet is 2, meaning the user's prediction was 100% accurate.
If this condition is false, the code moves on to the second ternary operator.

* The second ternary operator checks for two different conditions. First,
it checks if the user's prediction correctly guessed the winner, loser or draw. 
This is done by checking if result1 > result2 && bet1 > bet2 or result1 < result2 && bet1 < bet2 or result1 == result2 && bet1 == bet2.
If any of these conditions are true, the result of the bet is 1, meaning the user guessed the outcome of the match correctly, 
even if their prediction was not an exact match.
*Finally*, if both of the ternary operators evaluate to false, then the result of the bet is 0, meaning the user's prediction was completely wrong.

So in summary, this code is using the ternary operator to check the match result and the user's prediction, 
and determine whether the user's bet was correct, partially correct, or completely wrong based on those conditions.

### The ternary operator is a shorthand way of writing an if-else statement in Java.
It is a single line of code that evaluates a condition and returns one value if the condition is true and another value if it is false.
The ternary operator can be faster than an if-else block1. However, it can be less readable than an if-else block when used improperly2.

The ternary operator emphasizes what’s to be done over the selection of the values to do it with,
while an if-else statement emphasizes the branching first and what’s to be done is secondary2.
In different situations, either may better reflect the programmer’s “natural” perspective on the code and make it easier to understand, verify and maintain2.

### In terms of optimization and speed, ternary operators are faster than if-else blocks.

***Тернарний оператор*** - це скорочений спосіб написання умовного оператора в Java. Це один рядок коду, який оцінює умову і повертає одне значення,
якщо умова є істинною, і інше значення, якщо вона є хибною. Тернарний оператор може бути швидшим за блок if-else1. 
Однак він може бути менш зрозумілим за блок if-else при неправильному використанні2.
Тернарний оператор підкреслює те, що потрібно зробити над вибором значень для його виконання,
тоді як оператор if-else підкреслює розгалуження першим і те, що потрібно зробити - другорядне2. 
В різних ситуаціях будь-який з них може краще відображати “природну” перспективу програміста на код і полегшити його розуміння, перевірку та підтримку2.
З точки зору оптимізації та швидкості тернарні оператори швидші за блоки if-else.
``` java
int a = 10;
int b = 20;
int maxVal = (a > b) ? a : b;
```
У цьому прикладі ми порівнюємо два цілі числа, a і b. Якщо a більше за b, то змінній maxVal буде присвоєно значення змінної a. 
В іншому випадку їй буде присвоєно значення змінної b.

Тернарний оператор працює шляхом оцінки умови і повертає одне значення, якщо умова є істинною, і інше значення, якщо вона є хибною.
Синтаксис тернарного оператора наступний:

* змінна = (умова) ? виразІстина : виразХиба;
Тут змінна - це змінна, яка отримає значення на основі умови. 
Якщо умова є істинною, то змінній буде присвоєно значення виразуІстина. В іншому випадку змінній буде присвоєно значення виразуХиба2.

Символ ***?*** в тернарному операторі використовується для розділення умови від виразів, які будуть оцінені на основі того, чи є умова істинною чи хибною1.
Перший вираз, який з’являється після символу ?, буде оцінений, якщо умова є істинною, тоді як другий вираз, який з’являється після символу :, буде оцінений, якщо умова є хибною1.
Ось приклад:
```java
int a = 10;
int b = 20;
String result = (a > b) ? "a is greater than b" : "b is greater than a";
```
У цьому прикладі ми порівнюємо два цілі числа, a і b. Якщо a більше за b, то змінній result буде присвоєно рядок "a is greater than b".
В іншому випадку змінній буде присвоєно рядок "b is greater than a".

