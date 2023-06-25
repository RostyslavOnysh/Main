# Dependency Injection (DI).
Inversion of Control (IoC), та Dependency Inversion Principle (DIP) є поняттями, які використовуються для створення модульного, гнучкого та легкозмінного коду. Давайте розглянемо їх детальніше:

# Dependency Injection (DI):

* DI є процесом надання залежностей об'єкту ззовні, замість того, щоб самому створювати ці залежності.
Це дозволяє використовувати інверсію керування для забезпечення, що класи залежать від абстракцій, а не від конкретних реалізацій.
DI полегшує тестування, зменшує залежність між класами та дозволяє легко змінювати реалізації залежностей без зміни самого класу.
Inversion of Control (IoC):

# IoC є концепцією, де контроль над виконанням програми передається контейнеру або фреймворку.
Замість того, щоб класи самостійно створювати і керувати своїми залежностями, вони отримують ці залежності зовні.
Це забезпечує більшу гнучкість, можливість переконфігурування та заміни залежностей без зміни коду.
Dependency Inversion Principle (DIP):

* DIP є одним з принципів SOLID і стверджує, що класи повинні залежати від абстракцій, а не від конкретних реалізацій.
Цей принцип підкреслює важливість розділення інтерфейсів від реалізацій, що дозволяє замінювати реалізації без впливу на код, який використовує ці інтерфейси.
Для використання DI та IoC в Java часто використовуються фреймворки, такі як Spring. Ці фреймворки надають контейнер, який керує створенням та внедренням залежностей.

# Основні переваги використання DI, IoC та DIP:

Зменшення залежності між класами.
Полегшення тестування та заміни залежностей під час тестування.
Більша гнучкість та легкість зміни реалізацій залежностей.
Підвищення читабельності та модульності коду.
Приклад використання DI в Java за допомогою фреймворку Spring:

```java
 
public interface MessageService {
    void sendMessage(String message);
}

public class EmailService implements MessageService {
    @Override
    public void sendMessage(String message) {
        // Логіка відправки повідомлення по електронній пошті
    }
}

public class SMSService implements MessageService {
    @Override
    public void sendMessage(String message) {
        // Логіка відправки повідомлення по SMS
    }
}

public class NotificationService {
    private MessageService messageService;

    // Внедрення залежності через конструктор
    public NotificationService(MessageService messageService) {
        this.messageService = messageService;
    }

    public void sendNotification(String message) {
        messageService.sendMessage(message);
    }
}

public class Application {
    public static void main(String[] args) {
        // Створення контексту Spring
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);

        // Отримання біна NotificationService з контексту
        NotificationService notificationService = context.getBean(NotificationService.class);

        // Використання NotificationService
        notificationService.sendNotification("Hello, World!");

        // Закриття контексту Spring
        ((AnnotationConfigApplicationContext) context).close();
    }
}

@Configuration
public class AppConfig {
    @Bean
    public MessageService emailService() {
        return new EmailService();
    }

    @Bean
    public MessageService smsService() {
        return new SMSService();
    }

    @Bean
    public NotificationService notificationService(MessageService messageService) {
        return new NotificationService(messageService);
    }
}
```
У цьому прикладі NotificationService залежить від абстракції MessageService, і реалізацію цієї залежності (EmailService або SMSService) вирішує контейнер Spring залежно від конфігурації. Це дозволяє легко змінювати спосіб надсилання повідомлень без необхідності зміни коду NotificationService.

Цей приклад демонструє використання DI, IoC та DIP для створення модульного та гнучкого коду, де залежності вводяться ззовні та можуть бути легко замінені або розширені.




