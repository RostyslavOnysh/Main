# JDBC (Java Database Connectivity) 
- це інтерфейс програмування, що дозволяє розробникам Java-програм взаємодіяти з реляційними базами даних, використовуючи мову SQL. JDBC надає набір класів та методів, які дозволяють здійснювати з'єднання з базою даних, виконувати SQL-запити, отримувати результати та керувати транзакціями.

Основні компоненти JDBC включають:

* ***DriverManager:*** Цей клас відповідає за з'єднання з базою даних. Він забезпечує можливість реєстрації драйвера бази даних та отримання з'єднання з базою.

* ***Connection:*** Цей інтерфейс представляє з'єднання з базою даних. Він дозволяє виконувати SQL-запити та керувати транзакціями.

* ***Statement та PreparedStatement:*** Ці інтерфейси дозволяють виконувати SQL-запити до бази даних. Statement використовується для створення статичних запитів, тоді як PreparedStatement дозволяє створювати параметризовані запити з підтримкою попередньої компіляції.

* ***ResultSet:*** Цей інтерфейс представляє результати SQL-запиту до бази даних. Він дозволяє отримувати та маніпулювати даними, поверненими з бази.

Процес взаємодії з базою даних через JDBC зазвичай включає наступні кроки:

1. Завантаження драйвера бази даних: Зазвичай, перед початком взаємодії з базою даних, необхідно завантажити драйвер JDBC, який відповідає конкретній базі даних, з якою ви плануєте працювати.

2. Встановлення з'єднання: Використовуючи DriverManager.getConnection(), ви можете створити з'єднання з базою даних, вказавши необхідні параметри підключення, такі як URL бази даних, ім'я користувача, пароль тощо.

3. Виконання SQL-запитів: Ви можете створити об'єкт Statement або PreparedStatement для виконання SQL-запитів до бази даних. Запити можуть бути SELECT, INSERT, UPDATE, DELETE або будь-які інші запити, підтримувані вашою базою даних.

4. Обробка результатів: Якщо ваш запит повертає результати, ви можете використовувати об'єкт ResultSet для отримання та обробки даних, отриманих з бази даних.

5. ***Закриття з'єднання:*** Після завершення роботи з базою даних необхідно закрити з'єднання та звільнити ресурси. Ви можете викликати метод close() на об'єктах Connection, Statement, PreparedStatement або ResultSet для закриття з'єднання та відповідної пам'яті.

Це загальний опис процесу взаємодії з базою даних через JDBC. Конкретні деталі та синтаксис можуть варіюватись залежно від бази даних, яку ви використовуєте та реалізації JDBC драйвера.

#  main class 

```java
public class Main {
    public static void main(String[] args) {
        LiteraryFormatDao literaryFormat = new LiteraryFormatDaoImpl();
        List<LiteraryFormat> allFormats = literaryFormat.getAll();
        for (LiteraryFormat format : allFormats) {
            System.out.println(format);
        }
    }
}
```
#  package util

```java
public class ConnectionUtil {
    static {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            throw new RuntimeException("Can`t load JDBC Driver for MySQL", e);
        }
    }

    public static Connection getConnection() {
        try {
            Properties dbProperties = new Properties();
            dbProperties.put("user", "root");
            dbProperties.put("password", "13289812");
          return   DriverManager.getConnection("jdbc:mysql://localhost:3306/library_db", dbProperties);
        } catch (SQLException throwables) {
            throw new RuntimeException("Can`t create connection to Database", throwables);
        }
    }
}
```

#  package model 

```java
public class LiteraryFormat {
    private Long id;

    private String format;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public void setFormat(String format) {
        this.format = format;
    }

    public String getFormat() {
        return format;
    }

    @Override
    public String toString() {
        return "LiteraryFormat{" +
                "id=" + id +
                ", format='" + format + '\'' +
                '}';
    }
}
```


#  package dao

```java
public interface LiteraryFormatDao {
     List<LiteraryFormat> getAll();
}
```


```java
public class LiteraryFormatDaoImpl implements LiteraryFormatDao {
    @Override
    public List<LiteraryFormat> getAll() {
        List<LiteraryFormat> allFormats = new ArrayList<>();
        try (Connection connection = ConnectionUtil.getConnection();
             Statement getAllFormatsStatment = connection.createStatement();) {
            ResultSet resultSet = getAllFormatsStatment
                    .executeQuery("SELECT * FROM literary_formats");
            while (resultSet.next()) {
                String format = resultSet.getString("format");
                Long id = resultSet.getObject("id", Long.class);
                LiteraryFormat literaryFormat = new LiteraryFormat();
                literaryFormat.setId(id);
                literaryFormat.setFormat(format);
                allFormats.add(literaryFormat);
            }
        } catch (SQLException e) {
            throw new RuntimeException("Can`t get all formats from DB", e);
        }
        return allFormats;
    }
}
```

