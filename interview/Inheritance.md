# Наслідування (Inheritance) в Java 
- це механізм, який дозволяє створювати нові класи на основі вже існуючих класів, надаючи можливість успадковувати їх властивості та методи. Клас, який успадковується, називається підкласом або нащадком, а клас, від якого успадковується, називається батьківським класом або суперкласом.

Успадкування дозволяє створювати ієрархію класів, де підкласи можуть успадковувати властивості та методи батьківського класу, а також додавати нові властивості та методи. Це дозволяє використовувати загальні характеристики і функціональність батьківського класу в підкласах, що спрощує розробку та підтримку коду.

Inheritance в Java має кілька важливих аспектів:

Підклас успадковує всі не приватні властивості та методи батьківського класу. Це означає, що підклас може використовувати та змінювати ці властивості та методи.

Підклас може додавати нові властивості та методи, які не існують у батьківському класі. Це дозволяє розширювати функціональність та додавати специфічні характеристики для підкласів.

Підклас може перевизначати (override) методи батьківського класу, надаючи нову реалізацію. Це дозволяє змінити поведінку методу у підкласі, враховуючи його специфічні потреби.

Підклас може мати свої власні конструктори, але він також може викликати конструктор батьківського класу за допомогою ключового слова "super".

Наслідування є важливим засобом для створення загальних та організованих структур програм у Java. Воно сприяє повторному використанню коду, поліпшує читабельність та підтримку коду, а також дозволяє створювати більш гнучкі та масштабовані програми.

* ***Англійською:***

Inheritance in Java is a mechanism that allows creating new classes based on existing classes, enabling the inheritance of their properties and methods. The class being inherited from is called the superclass or parent class, while the class inheriting is called the subclass or child class.

Inheritance establishes a hierarchy of classes where subclasses can inherit the properties and methods of the parent class and can also add new properties and methods. This allows utilizing the common characteristics and functionality of the parent class in the subclasses, making code development and maintenance easier.

Inheritance in Java has several important aspects:

The subclass inherits all non-private properties and methods of the parent class. This means that the subclass can use and modify these properties and methods.

The subclass can add new properties and methods that are not present in the parent class. This enables extending functionality and adding specific characteristics to the subclasses.

The subclass can override methods of the parent class, providing a new implementation. This allows changing the behavior of a method in the subclass, considering its specific needs.

The subclass can have its constructors but can also call the constructor of the parent class using the "super" keyword.

Inheritance is an essential means of creating general and organized program structures in Java. It promotes code reuse, improves code readability and maintainability, and allows for the creation of more flexible and scalable programs.
