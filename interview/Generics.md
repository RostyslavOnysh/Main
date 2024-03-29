# Generics в Java - це механізм, який дозволяє створювати і використовувати параметризовані типи даних. Завдяки генерикам, ви можете створювати класи, інтерфейси і методи, які мають загальний тип даних, який може бути визначений під час використання.

Основна мета використання генериків - це забезпечення безпеки типів та підвищення повторного використання коду. Ось деякі важливі аспекти генериків:

1. Безпека типів: Генерики дозволяють вам визначати типи даних, з якими працює клас або метод, на етапі компіляції. Це забезпечує перевірку типів на етапі компіляції, що допомагає уникнути помилок виконання через неправильне використання типів.

2. Повторне використання коду: Генерики дозволяють створювати загальні класи, інтерфейси та методи, які можуть працювати з різними типами даних. Це збільшує повторне використання коду, оскільки ви можете використовувати однаковий код для різних типів даних без необхідності дублювання коду.

3. Параметризовані типи: Генерики дозволяють створювати класи, інтерфейси або методи, які приймають параметризовані типи даних. Наприклад, List<T> використовує параметризований тип T, який може бути замінений на будь-який тип даних при створенні екземпляра класу.

4. Забезпечення типової безпеки: За допомогою генериків ви можете визначати типові обмеження, які вказують, які типи даних можуть бути використані в генерик-коді. Наприклад, ви можете обмежити параметризований тип T лише на підкласи певного класу або інтерфейсу.

5. Автоупаковка та авторозпакування: Генерики автоматично виконують упаковку (автоупаковку) та розпакування (авторозпакування) примітивних типів даних. Наприклад, ви можете використовувати List<Integer> для зберігання цілих чисел без необхідності використовувати класи-обгортки.

# Генерики використовуються в різних сферах програмування, таких як колекції даних, алгоритми, фреймворки, сервлети, бази даних і багато інших. Деякі типові ситуації використання генериків включають:

1. Колекції даних: Генерики дозволяють використовувати параметризовані типи для зберігання і маніпулювання даними в колекціях, таких як List, Set і Map.

2. Алгоритми: Генерики можуть бути використані для створення загальних алгоритмів, які працюють з різними типами даних.

3. Фреймворки і бібліотеки: Багато фреймворків та бібліотек використовують генерики для створення загальних інтерфейсів та класів, які можуть бути використані з різними типами даних.

4. Бази даних: Генерики можуть бути використані для створення загальних класів або інтерфейсів, які спрощують взаємодію з базами даних та виконання запитів.

5. Кастомні типи даних: Ви також можете створювати свої власні класи або інтерфейси з використанням генериків для роботи зі специфічними типами даних.

При використанні генериків важливо вказувати правильні типові аргументи і типові обмеження, щоб забезпечити безпеку типів та ефективну роботу програми. Вони дозволяють створювати загальний і повторно використовуваний код, знижують ймовірність помилок та покращують читабельність програми.




# 1. Колекції даних: Генерики дозволяють створювати колекції, які працюють з різними типами даних. Наприклад:

```java

List<String> stringList = new ArrayList<>();
stringList.add("Hello");
stringList.add("World");
String firstElement = stringList.get(0); // отримуємо перший елемент зі списку
Тут List<String> вказує, що цей список приймає лише об'єкти типу String.
  ```

2. Класи з параметризованими типами: Генерики дозволяють створювати класи, які можуть працювати з різними типами даних. Наприклад, розглянемо клас Pair, який представляє пару значень:


```java
 
public class Pair<T, U> {
    private T first;
    private U second;

    public Pair(T first, U second) {
        this.first = first;
        this.second = second;
    }

    public T getFirst() {
        return first;
    }

    public U getSecond() {
        return second;
    }
}
```
Тепер ми можемо створити екземпляр Pair з будь-якими типами:


```java
 
Pair<String, Integer> pair = new Pair<>("Hello", 10);
String firstValue = pair.getFirst();
Integer secondValue = pair.getSecond();
Тут Pair<String, Integer> означає, що перший елемент буде типу String, а другий - типу Integer.
```
3. Методи з параметризованими типами: Генерики дозволяють оголошувати методи, які приймають та повертають різні типи даних. Наприклад, розглянемо метод printArray, який виводить елементи масиву:


```java
 
public <T> void printArray(T[] array) {
    for (T element : array) {
        System.out.println(element);
    }
}
```
Цей метод можна викликати з будь-яким масивом:

 
```java
Integer[] intArray = {1, 2, 3};
String[] stringArray = {"Hello", "World"};

printArray(intArray); // виведе: 1 2 3
printArray(stringArray); // виведе: Hello World
```
Тут <T> показує, що метод є параметризованим і може працювати з будь-яким типом T.

Це лише декілька прикладів використання Generics. Вони також широко використовуються в фреймворках, бібліотеках та інших аспектах розробки програмного забезпечення, де потрібна гнучкість та безпека типів.
