# ArrayList в Java - це реалізація динамічного масиву, який зберігає об'єкти. Цей клас знаходиться в пакеті java.util і використовується для зберігання та маніпулювання даними.

*** Навіщо використовувати ArrayList?***

* ArrayList надає динамічне збереження даних. Він може автоматично збільшувати розмір масиву, коли потрібно додати новий елемент.
* ArrayList надає широкий набір методів для додавання, видалення, отримання та зміни елементів у списку.
* Використання ArrayList з Generics (ArrayList<E>) дозволяє вказати конкретний тип даних, які будуть зберігатися у списку, забезпечуючи безпеку типів і уникнення помилок під час виконання.
# Як використовувати ArrayList?
Перш за все, необхідно імпортувати пакет java.util та створити екземпляр ArrayList. Наприклад:

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        // Створення екземпляру ArrayList для зберігання рядків
        ArrayList<String> names = new ArrayList<>();

        // Додавання елементів до ArrayList
        names.add("John");
        names.add("Alice");
        names.add("Bob");

        // Отримання елементів ArrayList
        String firstElement = names.get(0);
        System.out.println("Перший елемент: " + firstElement);

        // Зміна елемента ArrayList
        names.set(1, "Mike");

        // Видалення елемента з ArrayList
        names.remove(2);

        // Розмір ArrayList
        int size = names.size();
        System.out.println("Розмір: " + size);

        // Ітерація по ArrayList
        for (String name : names) {
            System.out.println(name);
        }
    }
}
```
# Користь від використання ArrayList з Generics:

* ***Безпека типів:*** Завдяки використанню Generics, можна вказати конкретний тип даних, які будуть зберігатися у списку. Це дозволяє уникнути помилок типізації під час компіляції і забезпечити безпеку типів під час виконання програми.
* ***Перевага поліморфізму:*** За допомогою Generics, можна створити ArrayList з базовим типом і додавати до нього об'єкти підкласів. Це дозволяє використовувати поліморфізм для обробки різних типів об'єктів.
* ***Зручність та читабельність:*** Використання Generics дозволяє зазначити очікуваний тип даних у списку, що полегшує розуміння коду та поліпшує читабельність.
# Наприклад, можна створити ArrayList з Generics для збереження об'єктів класу Person:

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        // Створення екземпляру ArrayList для зберігання об'єктів класу Person
        ArrayList<Person> people = new ArrayList<>();

        // Додавання об'єктів Person до ArrayList
        Person person1 = new Person("John", 25);
        Person person2 = new Person("Alice", 30);
        people.add(person1);
        people.add(person2);

        // Отримання об'єктів Person з ArrayList
        Person firstPerson = people.get(0);
        System.out.println("Ім'я першої людини: " + firstPerson.getName());

        // Зміна властивостей об'єкта Person
        person2.setAge(35);

        // Видалення об'єкта з ArrayList
        people.remove(1);

        // Розмір ArrayList
        int size = people.size();
        System.out.println("Розмір: " + size);

        // Ітерація по ArrayList
        for (Person person : people) {
            System.out.println(person.getName() + ", " + person.getAge());
        }
    }
}

class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```
У цьому прикладі ArrayList<Person> дозволяє зберігати об'єкти типу Person, забезпечуючи безпеку типів і зручність роботи з даними.
