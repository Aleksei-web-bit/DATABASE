/*
Создание таблицы users:
*/
CREATE TABLE users (userId integer PRIMARY KEY, 
userName VARCHAR(100), userLastname VARCHAR(100));

/* Добавление 1 пользователя в таблицу users:
*/
INSERT INTO users (userId, userName, userLastname) VALUES (1, 'Иван', 'Иванов');

/* Добавление 2 пользователя в таблицу users:
*/
INSERT INTO users (userId, userName, userLastname) VALUES (2, 'Пётр', 'Петров');

/* Создание таблицы chats:
*/
CREATE TABLE chats (chatId SERIAL PRIMARY KEY, 
chatName VARCHAR(100));

/* Добавление 1 строки в таблицу chats:
*/
INSERT INTO chats (chatName) VALUES ('Личный чат');

/* Добавление 2 строки в таблицу chats:
*/
INSERT INTO chats (chatName) VALUES ('Рабочий чат');

/* Создание таблицы messages:
*/
CREATE TABLE messages (lastMessageId SERIAL PRIMARY KEY, 
lastMessageText VARCHAR(100),
userId integer,

CONSTRAINT st_ex_fk FOREIGN KEY (userId)
        REFERENCES users (userId)
);

/* Добавление строк в таблицу messages:
*/
INSERT INTO messages (lastMessageText, userId) VALUES ('Доброе утро.', 1);

INSERT INTO messages (lastMessageText, userId) VALUES ('Добрый день.', 1);

INSERT INTO messages (lastMessageText, userId) VALUES ('Добрый вечер.', 2);

INSERT INTO messages (lastMessageText, userId) VALUES ('Привет!', 2);

INSERT INTO messages (lastMessageText, userId) VALUES ('Здоров!', 1);

INSERT INTO messages (lastMessageText, userId) VALUES ('Приветствую!!!', 2);

/* Деление на группы производится по чатам.
*/

/* Сколько сообщений послал каждый пользователь? Группировка.
*/

SELECT userId, COUNT(*) FROM messages GROUP BY userId;

/* то же с именем пользователя
*/

SELECT userName, COUNT(*) FROM messages JOIN  users ON messages.userId = users.userId GROUP BY userId;
