# В Java винятки (exceptions) використовуються для обробки помилок та несподіваних ситуацій, які виникають під час виконання програми. Їх наявність дозволяє програмі контролювати та відновлюватись після помилок, забезпечуючи надійність та стабільність.

У Java ієрархія винятків базується на класі 
***java.lang.Throwable***, який є батьківським класом для всіх винятків. Throwable має два основних підкласи:
* Error 
* Exception.

* Error: Класи помилок представлені класами, які вказують на серйозні проблеми, зазвичай пов'язані з недоліками в середовищі виконання або системними ресурсами. Наприклад, OutOfMemoryError виникає, коли немає достатньо пам'яті для виконання програми.

* Exception: Цей клас є батьківським для всіх винятків, що не відносяться до помилок. Він має декілька підкласів, які поділяються на дві групи:

1. Перша група це перевіряючі винятки ***(checked exceptions)***. Ці винятки виникають у випадках, коли програма взаємодіє з незапевненими умовами, такими як робота з файлами, мережеві операції або базами даних. Деякі приклади цих винятків включають IOException, SQLException тощо. При обробці перевіряючих винятків програма повинна або обробити ці винятки в блоках try-catch, або прокинути їх (throws) вище по стеку викликів.

2. Друга група це неперевіряючі винятки (unchecked exceptions), також відомі як runtime exceptions. Ці винятки виникають у випадках програмних помилок або некоректного використання API. Неперевіряючі винятки не вимагають обов'язкового оброблення або прокидання. Деякі приклади таких винятків включають NullPointerException, ArrayIndexOutOfBoundsException, IllegalArgumentException тощо.

Загалом, ієрархія винятків в Java дозволяє краще управляти та обробляти помилки в програмах. Правильна обробка винятків забезпечує надійність програми та допомагає уникнути неочікуваних ситуацій, забезпечуючи коректну роботу програми в усіх умовах.
