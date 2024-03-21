-- Вводимые команды:

-- Создание таблицы users:
CREATE TABLE users (userId SERIAL PRIMARY KEY, 
userName VARCHAR(100), userLastname VARCHAR(100));

-- Добавление 1 пользователя в таблицу users:
INSERT INTO users (userName, userLastname) VALUES ('Иван', 'Иванов');

-- Добавление 2 пользователя в таблицу users:
INSERT INTO users (userName, userLastname) VALUES ('Пётр', 'Петров');

-- Создание таблицы chats:
CREATE TABLE chats (chatId SERIAL PRIMARY KEY, 
chatName VARCHAR(100));

-- Добавление 1 строки в таблицу chats:
INSERT INTO chats (chatName) VALUES ('Личный чат');

-- Добавление 2 строки в таблицу chats:
INSERT INTO chats (chatName) VALUES ('Рабочий чат');

-- Создание таблицы messages:
CREATE TABLE messages (lastMessageId SERIAL PRIMARY KEY, 
lastMessageText VARCHAR(100),
userId integer NOT NULL,
chatId integer NOT NULL,

CONSTRAINT user_fk FOREIGN KEY (userId)
        REFERENCES users (userId),

CONSTRAINT chat_fk FOREIGN KEY (chatId)
        REFERENCES chats (chatId));

-- Добавление строк в таблицу messages:
INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Доброе утро.', 1, 2);

INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Добрый день.', 1, 2);

INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Добрый вечер.', 2, 1);

INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Привет!', 2, 1);

INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Здоров!', 1, 1);

INSERT INTO messages (lastMessageText, userId, chatId) VALUES ('Приветствую!!!', 2, 1);

-- Деление на группы производится по чатам.

-- Сколько сообщений послал каждый пользователь?
-- Группировка:
SELECT userId, COUNT(*) FROM messages GROUP BY userId;

-- то же с именем пользователя:
SELECT userName, COUNT(*) FROM (SELECT userName, lastMessageId FROM messages JOIN  users ON messages.userId = users.userId) AS T1 GROUP BY T1.userName;

-- Напечатать все сообщения первого чата,
-- затем второго и так далее.
SELECT chatName, lastMessageText FROM messages JOIN  chats ON messages.chatId = chats.chatId ORDER BY chatName;

-- Вывод:

INSERT 0 1
 userid | count 
--------+-------
      2 |     3
      1 |     3
(2 строки)

 username | count 
----------+-------
 Пётр     |     3
 Иван     |     3
(2 строки)

  chatname   | lastmessagetext 
-------------+-----------------
 Личный чат  | Добрый вечер.
 Личный чат  | Привет!
 Личный чат  | Здоров!
 Личный чат  | Приветствую!!!
 Рабочий чат | Доброе утро.
 Рабочий чат | Добрый день.
(6 строк)

test=# 

