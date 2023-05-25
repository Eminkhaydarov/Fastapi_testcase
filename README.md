# Сервис question:
В сервисе реализован POST REST метод, принимающий на вход запросы с содержимым вида {"questions_num": integer}.
После получения запроса сервис, в свою очередь, запрашивает с публичного API (англоязычные вопросы для викторин) 
https://jservice.io/api/random?count=1 указанное в полученном запросе количество вопросов.

## Пример:
![Снимок экрана от 2023-05-25 10-19-28](https://github.com/Eminkhaydarov/Fastapi_testcase/assets/115652686/83c3b3d8-0fd4-4536-84cc-87bad616ccb8)
## Запуск:
### Makefile:
* *make question*
### Docker:
* *docker-compose -f question/docker-compose.yml up --build -d*

# Сервис converting
Веб-сервис, выполняющий следующие функции:
Создание пользователя;
Для каждого пользователя - сохранение аудиозаписи в формате wav, преобразование её в формат mp3 и запись в базу данных и предоставление ссылки для скачивания аудиозаписи.
* Создание пользователя, POST:
  - Принимает на вход запросы с именем пользователя;
  - Создаёт в базе данных пользователя заданным именем, так же генерирует уникальный идентификатор пользователя и UUID токен доступа (в виде строки) для данного пользователя;
  - Возвращает сгенерированные идентификатор пользователя и токен.
* Добавление аудиозаписи, POST:
  - Принимает на вход запросы, содержащие уникальный идентификатор пользователя, токен доступа и аудиозапись в формате wav;
  - Преобразует аудиозапись в формат mp3, генерирует для неё уникальный UUID идентификатор и сохраняет их в базе данных;
  - Возвращает URL для скачивания записи вида http://host:port/api/record?id=id_записи&user=id_пользователя.
* Доступ к аудиозаписи, GET:
  - Предоставляет возможность скачать аудиозапись по ссылке http://host:port/api/record?id=id_записи&user=id_пользователя.
 ## Пример:
 ![Снимок экрана от 2023-05-25 10-20-53](https://github.com/Eminkhaydarov/Fastapi_testcase/assets/115652686/15bcbe23-e46c-4bdb-9573-fe9390b4180f)
 ![Снимок экрана от 2023-05-25 10-22-02](https://github.com/Eminkhaydarov/Fastapi_testcase/assets/115652686/57aa17fb-a7c0-431e-b1fd-ea6997a18322)
 ![Снимок экрана от 2023-05-25 10-22-41](https://github.com/Eminkhaydarov/Fastapi_testcase/assets/115652686/b73ba582-374c-44f3-8f30-0002d1c76d12) 

## Запуск:
### Makefile:
* *make converting*
### Docker:
* *docker-compose -f converting/docker-compose.yml up --build -d*

