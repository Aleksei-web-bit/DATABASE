# Выполнение практических заданий.

# Создание пользователя:
CREATE USER test WITH PASSWORD '12345';

# Вывод списка пользователей:
\du
                                          Список ролей
 Имя роли |                                Атрибуты                                 | Член ролей 
----------+-------------------------------------------------------------------------+------------
 postgres | Суперпользователь, Создаёт роли, Создаёт БД, Репликация, Пропускать RLS | {}
 test     |                                                                         | {}

# Создание базы данных:
CREATE DATABASE test OWNER test;

# Вывод списка баз данных:
\l
                                  Список баз данных
    Имя    | Владелец | Кодировка | LC_COLLATE  |  LC_CTYPE   |     Права доступа     
-----------+----------+-----------+-------------+-------------+-----------------------
 postgres  | postgres | UTF8      | ru_RU.UTF-8 | ru_RU.UTF-8 | 
 template0 | postgres | UTF8      | ru_RU.UTF-8 | ru_RU.UTF-8 | =c/postgres          +
           |          |           |             |             | postgres=CTc/postgres
 template1 | postgres | UTF8      | ru_RU.UTF-8 | ru_RU.UTF-8 | =c/postgres          +
           |          |           |             |             | postgres=CTc/postgres
 test      | test     | UTF8      | ru_RU.UTF-8 | ru_RU.UTF-8 | 
(4 строки)

(END)

# Создание таблицы:
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    email VARCHAR(255) NOT NULL,
    name VARCHAR(100),
    lastname VARCHAR(100)
);

# Вывод сообщения системы в ответ на ввод команды:
CREATE TABLE
test=# 

# Список таблиц, представлений, последовательностей, прав доступа к ним:
\dp
                                          Права доступа
 Схема  |        Имя        |        Тип         | Права доступа | Права для столбцов | Политики 
--------+-------------------+--------------------+---------------+--------------------+----------
 public | users             | таблица            |               |                    | 
 public | users_user_id_seq | последовательность |               |                    | 
(2 строки)

# Добавление строк в таблицу:
INSERT INTO users (email, name, lastname) VALUES ('ivan_ivanov@mail.ru', 'Ivan', 'Ivanov');

# Сообщение системы в ответ на ввод команды:
INSERT 0 1
test=# 

INSERT INTO users (email, name, lastname) VALUES ('Petr_Petrov@mail.ru', 'Petr', 'Petrov');

# Вывод всего содержимого таблицы:
SELECT * FROM users;

# Содержимое таблицы:
 user_id |        email        | name | lastname 
---------+---------------------+------+----------
       1 | ivan_ivanov@mail.ru | Ivan | Ivanov
       2 | Petr_Petrov@mail.ru | Petr | Petrov
(2 строки)

test=# 

# Вывод из таблицы адресов электронной почты:
SELECT email FROM users;

#Результат выполнения команды:
        email        
---------------------
 ivan_ivanov@mail.ru
 Petr_Petrov@mail.ru
(2 строки)

test=# 

# Вывод информации о пользователе/пользователях с именем 'Ivan':
SELECT * FROM users WHERE name = 'Ivan';

# Результат выполнения команды:
 user_id |        email        | name | lastname 
---------+---------------------+------+----------
       1 | ivan_ivanov@mail.ru | Ivan | Ivanov
(1 строка)

test=# 

# Изменение адреса электронной почты пользователя по фамилии 'Ivanov':
UPDATE users SET email = 'ivan_ivanov@yandex.ru' WHERE lastname = 'Ivanov';
UPDATE 1
test=# 

# Вывод данных пользователя по фамилии 'Ivanov' с изменённым адресом электронной почты:
SELECT * FROM users WHERE lastname = 'Ivanov';

# Результат выполнения команды:
 user_id |         email         | name | lastname 
---------+-----------------------+------+----------
       1 | ivan_ivanov@yandex.ru | Ivan | Ivanov
(1 строка)

test=# 

# Удаление строки, содержащей данные пользователя по фамилии 'Petrov':
DELETE FROM users WHERE lastname = 'Petrov';

# Сообщение системы в ответ на ввод команды:
DELETE 1
test=# DELETE FROM users WHERE lastname = 'Petrov';

# Вывод содержимого таблицы 'users' после удаления строки, содержащей данные пользователя по фамилии 'Petrov':
SELECT * FROM users;
 user_id |         email         | name | lastname 
---------+-----------------------+------+----------
       1 | ivan_ivanov@yandex.ru | Ivan | Ivanov
(1 строка)

test=# 

# Удаление таблицы 'users' из базы данных 'test':
DROP TABLE users;

# Список таблиц в базе данных 'test' после удаления из неё таблицы 'users':
\dp
                           Права доступа
 Схема | Имя | Тип | Права доступа | Права для столбцов | Политики 
-------+-----+-----+---------------+--------------------+----------
(0 строк)

test=# 
