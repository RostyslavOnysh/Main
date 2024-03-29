В JDBC існують два основних інтерфейси для виконання SQL-запитів до бази даних: 
* Statement
* PreparedStatement.

## Ось основні відмінності між ними:

* ***Попередня компіляція:*** Statement виконує SQL-запити безпосередньо до бази даних при кожному виклику. З іншого боку, PreparedStatement використовує попередню компіляцію, тобто SQL-запит попередньо компілюється і оптимізується базою даних при першому виклику, а потім повторно використовується з параметрами.

* ***Параметризовані запити:*** PreparedStatement дозволяє створювати параметризовані запити, де значення параметрів можуть бути передані окремо від запиту. Це дозволяє уникнути проблем з екрануванням та покращує безпеку, а також дозволяє оптимізувати виконання запитів, оскільки база даних може кешувати план виконання.

* ***Безпека:*** Використання PreparedStatement допомагає запобігти SQL-ін'єкціям, оскільки значення параметрів передаються окремо від запиту і не змішуються з самим запитом. Використання Statement може бути менш безпечним, якщо дані, які використовуються у запиті, введені користувачем.

* ***Читабельність коду:*** PreparedStatement може сприяти поліпшенню читабельності коду, особливо якщо SQL-запити мають багато параметрів. Запити можуть бути написані з плейсхолдерами, що полегшує зміну або розширення запиту, не змінюючи структуру коду.

* ***Ефективність:*** PreparedStatement може бути ефективнішим у виконанні повторюваних запитів з різними наборами параметрів. База даних може кешувати плани виконання та використовувати їх повторно для подібних запитів з відмінними значеннями параметрів.

* ***Динамічна зміна запиту:*** Statement дозволяє динамічно змінювати сам SQL-запит, тоді як PreparedStatement передбачає попередню компіляцію та оптимізацію, тому запит не може бути змінений після створення.

Загалом, використання PreparedStatement рекомендується у більшості випадків, особливо коли маєте справу з параметризованими запитами або потребуєте покращеної безпеки. Проте, Statement може бути використаний у простих випадках, де немає необхідності в попередній компіляції або параметризації запитів.


## Використання інтерфейсу Statement:

Виконання простих запитів без параметрів: Якщо вам потрібно виконати прості запити без параметрів, наприклад, вибрати всі записи з таблиці або виконати простий UPDATE-запит, то інтерфейс Statement може бути зручним.

Динамічне формування запиту: Якщо SQL-запити формуються динамічно в процесі виконання програми (наприклад, на основі умов або даних з користувача), то інтерфейс Statement дозволяє додавати змінні частини запиту в процесі виконання.

## Використання інтерфейсу PreparedStatement:

Параметризовані запити: Коли ви маєте запити, які вимагають передачі параметрів, наприклад, вставка нового запису зі значеннями, що залежать від даних користувача, PreparedStatement дозволяє підготувати запит з плейсхолдерами для параметрів та передати значення окремо.

Запити, що виконуються багатократно з різними параметрами: Якщо ви маєте запити, які виконуються багатократно з різними наборами параметрів (наприклад, багато вставок або оновлень), PreparedStatement може бути більш ефективним, оскільки база даних може кешувати плани виконання та використовувати їх повторно.

Запобігання SQL-ін'єкціям: Використання PreparedStatement допомагає запобігти SQL-ін'єкціям, оскільки значення параметрів передаються окремо від запиту, і база даних розрізняє між запитом та даними.
