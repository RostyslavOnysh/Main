# Масив (array) – 
### це набір комірок зберігання даних, кожна з яких має той же тип. Окрема комірка має назву елемента масиву (array item). На відміну від інших складених типів даних, масиви завжди розташовуються в цілісному блоці пам'яті. 
### Оскільки всі елементи займають однакові за розміром комірки пам'яті, адреса конкретного елемента завжди може бути обчислена за його номером. Номери елементів називаються індексами. Звернення до конкретних елементів здійснюють через індекс.

Як і в *С++*, масиви в Java індексуються починаючи з нуля. Під час опису масиву квадратні дужки ставляться після імені типу, а не імені змінної. Розміщення квадратних дужок після імені змінної допускається, але не рекомендується.

* *int[] a;*
У цьому прикладі описується *посилання на масив*, який буде створений пізніше. Розмір масиву не є частиною типу, як це реалізовано в C++. Це дозволяє визначити масив необхідного розміру під час виконання програми


```java
int[] numbers;           // посилання на масив цілих чисел довільної довжини
numbers = new int[10]; // numbers складається з 10 елементів
numbers = new int[20]; // numbers складається з 20 елементів
```

У Java підтримуються ***одно*** і ***багатовимірні масиви (масиви масивів)***. Наприклад, так можна визначити посилання на двовимірний масив:

* *byte[][] scores;*
Наступні приклади показують, як створити різні масиви:
```java
int[] numbers = new int[5];           // одновимірний масив
double[][] matrix = new double[5][4]; // прямокутний масив
byte[][] scores = new byte[5][];      // двовимірний масив з різною довжиною рядків
for (int i = 0; i < 5; i++) {
    scores[i] = new byte[i + 4];
}
```
Останній приклад показує як можна створити двовимірний масив з різною довжиною рядків. Розмір масиву може бути визначений як за допомогою констант, так і за допомогою змінних і виразів, що дають цілий результат.

У Java масиви містять елементи разом з їх кількістю.
* Кількість елементів масиву завжди можна отримати за допомогою спеціального поля length. Це поле доступне тільки для читання:

```java 
int[] a = new int[10];
System.out.println(a.length); // 10
````
* У Java передбачений простий спосіб ініціалізації масиву списком початкових значень: 
```java
int[] numbers = new int[] {1, 2, 3, 4, 5};
```
* ***Можна опустити операцію new:***
```java
int[] numbers = {1, 2, 3, 4, 5};
```
* Аналогічно ініціалізуються багатовимірні масиви:
```java
int[][] b = {{1, 2, 3},
             {0, 0, 1},
             {1, 1, 11},
             {0, 0, 0}};
```
У наведеному прикладі створюється двовимірний масив з чотирьох рядків і трьох стовпців.

* Так виглядає типовий цикл для обходу масиву:
```java
for (int i = 0; i < a.length; i++) {
    a[i] = 0;
}
```
* Аналогічно обхід усіх елементів двовимірного масиву зазвичай здійснюється так:
```java
for (int i = 0; i < c.length; i++) {
    for (int j = 0; j < c[i].length; j++) {
        c[i][j] = 0;
    }
}
```
Як видно з останнього прикладу, для отримання розміру i-го рядка двовимірного масиву використовують конструкцію ***c[i].length.***

Альтернативна форма циклу for (починаючи з JDK 1.5) дозволяє спростити повний обхід масивів. Наприклад, замість
```java
int[] nums = {1, 2, 3, 4, 5, 6};
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}
```

***можна написати :***
```java
int[] nums = {1, 2, 3, 4, 5, 6};
for(int n : nums) {
    System.out.println(n);
}
```
Альтернативна форма може бути застосована. лише для читання значень елементів, а не для їхньої модифікації.

Масиви читають з клавіатури поелементно. Наведений нижче приклад демонструє читання кількості та значень елементів з клавіатури.
```java
package ua.inf.iwanoff.labs.fifth;

public class ArrayTest {

    public static void main(String[] args) {
        System.out.println("Уведіть кількість елементів масиву:");
        java.util.Scanner s = new java.util.Scanner(System.in);
        int size = s.nextInt();
        double[] a = new double[size];
        System.out.println("Уведіть елементи масиву:");
        for (int i = 0; i < a.length; i++) {
            a[i] = s.nextDouble();
        }
        // Робота з масивом
        // ...
    }

}
```
Присвоювання імені масиву іншому імені масиву приводить тільки до копіювання посилання,
але не самого масиву. Для копіювання елементів масиву необхідно організувати цикл або скористатися стандартними функціями.

#  Масиви як параметри та результат функцій
* ***Масиви-параметри передаються у функції за посиланням. Після повернення з функції елементи можуть містити змінені значення:***
```java
package ua.inf.iwanoff.labs.fifth;

public class SwapElements {

    static void swap(int[] a) {
        int z = a[0];
        a[0] = a[1];
        a[1] = z;
    }

    public static void main(String[] args) {
        int[] b = {1, 2};
        swap(b);
        System.out.println(b[0]); // 2
        System.out.println(b[1]); // 1
    }

}
```
Якщо параметр описано як одновимірний масив, то можна фактичним параметром вказати рядок двовимірного масиву.
* ***Також можна використовувати параметри типу багатовимірних масивів. Наприклад:***
```java
package ua.inf.iwanoff.labs.fifth;

public class ArraysTest {

    static double sum(double[] arr1D) {
        double s = 0;
        for (double elem : arr1D) {
            s += elem;
        }
        return s;
    }

    static double sum(double[][] arr2D) {
        double s = 0;
        for (double[] line : arr2D) {
            for (double elem : line) {
                s += elem;
            }
        }
        return s;
    }

    public static void main(String[] args) {
        double[][] arr = {{1, 2},
                          {3, 4},
                          {5, 6}};
        System.out.printf("Сума елементів рядка з індексом 1: %f%n", sum(arr[1]));
        System.out.printf("Сума всіх елементів: %f%n", sum(arr));
    }
}
```

У Java *1.5* з'явилася додаткова можливість створення функцій зі змінним числом параметрів визначеного типу (Variable Arguments List, varargs).
* ***Всередині функції такі параметри інтерпретуються як масив:***
```java
static void printIntegers(int... a) {
    for (int i = 0; i < a.length; i++) {
        System.out.println(a[i]);
    }
}    
```
* ***Викликати таку функцію можна у два способи: передаючи список аргументів типу елемента масиву, або передаючи масив цілком:***
```java
public static void main(String[] args) {
    printIntegers(1, 2, 3);
    int[] arr = {4, 5};
    printIntegers(arr);
}
```
Такий параметр може бути лише один і обов'язково розташований останнім в списку.

* ***Функція може повертати посилання на масив. Найчастіше такий масив створюється всередині функції. Наприклад, створюємо масив цілих, заповнений одиницями:***
```java
static int[] arrayOfOnes(int n) {
    int[] arr = new int[n];
    for (int i = 0; i < arr.length; i++) {
        arr[i] = 1;
    }
    return arr;
}
```
* ***Тепер можна створити масив за допомогою нашої функції:***

int[] a = arrayOfOnes(6);
Якщо потрібен тільки один елемент, для нього можна не створювати масив з ім'ям і поєднати створення масиву з його використанням:

System.out.println((arrayOfOnes(2)[0]));
Можна також повертати посилання на багатовимірні масиви.

Посилання на масиви передаються за значенням.

static void resize(int[] arr, int newSize) {
    // збереження існуючих елементів
    arr = new int[newSize];
    // копіювання
}
Нове посилання слід повертати, інакше новий масив буде втрачено:

static int[] resize(int[] arr, int newSize) {
    // збереження існуючих елементів
    arr = new int[newSize];
    // копіювання;
    return arr;
}
2.2.3 Стандартні функції для роботи з масивами
Клас System надає найпростіший шлях копіювання одного масиву в іншій – використання статичного методу arraycopy():

System.arraycopy(a, a_from, b, b_from, size);
Це еквівалентно такому циклу:

for (int i = a_from, j = b_from; i < size + a_from; i++, j++) {
    b[j] = a[i];
} 
Масив, у який здійснюється копіювання, повинен мати необхідні розміри. Функція arraycopy() не створює нового масиву.
Весь масив a можна скопіювати в b таким викликом:

System.arraycopy(a, 0, b, 0, a.length);
Для заповнення масивів можна використовувати статичні методи класу Arrays, реалізованого в пакеті java.util.

# Статичний метод класу Arrays	
## Опис :
* void fill(тип[] a, тип val)	заповнює масив вказаними значеннями
* void fill(тип[] a, int fromIndex, int toIndex, тип val)	заповнює частину масиву вказаними значеннями
* String toString(тип[] a)	повертає список елементів масиву у вигляді рядка
* String deepToString(тип[][] a)	подає багатовимірний масив у вигляді рядка
* тип[] copyOf(тип[] a, int len)	створює новий масив довжини len з копіями елементів
* тип[] copyOfRange(тип[] a, int from, int to)	створює новий масив з копіями елементів діапазону
* boolean equals(тип[] a, тип[] a2)	перевіряє еквівалентність елементів двох масивів
* boolean deepEquals(тип[][] a, тип[][] a2)	перевіряє еквівалентність елементів багатовимірних масивів
* void sort(тип[] a)	здійснює сортування елементів за зростанням
* void sort(тип[] a, int fromIndex, int toIndex)	здійснює сортування частини елементів за зростанням
* int binarySearch(тип[] a, тип key)	здійснює пошук у відсортованому масиві
*У таблиці тип означає один з фундаментальних (примітивних) типів або тип Object.*

Перший варіант функції fill() використовується для заповнення всього масиву, другий – частини, 
при чому елемент з номером toIndex не включається в послідовність. Наприклад:
```java
public class FillArray {

    public static void main(String[] args) {
        int[] a = new int[6];
        java.util.Arrays.fill(a, 0, 4, 12); // Інші елементи дорівнюють 0
        for (int x : a) {
            System.out.print(x + " ");
        }
        System.out.println();
        java.util.Arrays.fill(a, 100);      // Всі елементи дорівнюють 100
        for (int x : a) {
            System.out.print(x + " ");
        }
        System.out.println();
    }

}
```
У попередньому прикладі для виведення елементів масиву на екран був використаний цикл.
Альтернативний спосіб – використання функції toString() класу Arrays. Ця функція повертає представлення масиву у вигляді рядка,
яке є зручним для більшості застосувань:

java.util.Arrays.fill(a, 100);
System.out.println(Arrays.toString(a)) // [100, 100, 100, 100, 100, 100];
Примітка: для виведення в рядок багатовимірних масивів слід використовувати функцію deepToString().

Клас Arrays надає альтернативний шлях копіювання масивів. Функція copyOf() створює новий масив копій елементів.
Перший параметр – вихідний масив, другий параметр – довжина результуючого масиву. Елементи, які не помістилися, відкидаються,
відсутні заповнюються нулями. Функція copyOfRange(тип[] a, int from, int to) копіює в новий масив частину масиву,
включаючи початок інтервалу і не включаючи кінця інтервалу:
```java
import java.util.Arrays;

public class CopyOfTest {

    public static void main(String[] args) {
        int[] a = { 1, 2, 3, 4 };
        int[] b = Arrays.copyOf(a, 3); 
        System.out.println(Arrays.toString(b));// [1, 2, 3]
        int[] c = Arrays.copyOf(a, 6); 
        System.out.println(Arrays.toString(c));// [1, 2, 3, 4, 0, 0]
        int[] d = Arrays.copyOfRange(a, 1, 3);
        System.out.println(Arrays.toString(d));// [2, 3]
    }

}
```
Порівняти два масиви чи частину їх можна за допомогою функцій групи equals(). Масиви порівнюються поелементно.
Два масиви також вважаються еквівалентними, якщо обидва посилання – null. Наприклад:
```java
import java.util.Arrays;
public class ArraysComparison {

    public static void main(String[] args) {
        double[] a = null, b = null;
        System.out.println(Arrays.equals(a, b)); // true
        a = new double[] { 1, 2, 3, 4 };
        b = new double[4];
        System.out.println(Arrays.equals(a, b)); // false
        System.arraycopy(a, 0, b, 0, a.length);
        System.out.println(Arrays.equals(a, b)); // true
        b[3] = 4.5;
        System.out.println(Arrays.equals(a, b)); // false
    }

}
```
Є також метод deepEquals(), використання якого аналогічне. Різниця є істотною для багатовимірних масивів. Здійснюється більш "глибока" перевірка:

int[][] a1 = { { 1, 2 } , { 3, 4 } };
int[][] a2 = { { 1, 2 } , { 3, 4 } };
System.out.println(Arrays.equals(a1, a2));    // false
System.out.println(Arrays.deepEquals(a1, a2));// true    
За допомогою функції sort() можна здійснити сортування масиву чисел за зростанням. Наприклад:
```java
import java.util.Arrays;

public class ArraySort {

    public static void main(String[] args) {
        int[] a = new int[] { 11, 2, 10, 1 };
        Arrays.sort(a);            // 1 2 10 11
        for (int x : a) {
            System.out.print(x + " ");
        }
        System.out.println();
    }

}
```
Функція sort() реалізована для масивів усіх примітивних типів та рядків. Рядки впорядковуються за алфавітом. Можна також сортувати частину масиву.
Як і для функції fill(), вказується початковий і кінцевий індекси послідовності, яку слід відсортувати. Кінцевий індекс не включається в послідовність. Наприклад:

int[] a = {7, 8, 3, 4, -10, 0};
java.util.Arrays.sort(a, 1, 4); // 7 3 4 8 -10 0    
У відсортованих масивах можна виконати пошук за допомогою методів класу Arrays. Група функцій binarySearch(),
реалізована для всіх примітивних типів і типу Object, повертає індекс знайденого елемента або від'ємне значення, якщо елемент відсутній.
