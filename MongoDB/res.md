Current Mongosh Log ID:	66047a8beec851b8ffca690b
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.1.5
Using MongoDB:		7.0.6
Using Mongosh:		2.1.5
mongosh 2.2.1 is available for download: https://www.mongodb.com/try/download/shell

For mongosh info see: [1mhttps://docs.mongodb.com/mongodb-shell/[0m

------
   The server generated these startup warnings when booting
   2024-03-27T22:57:05.890+03:00: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

test> Создание базы данных:

test> switched to db fitisov_db
fitisov_db> 
fitisov_db> Создание коллекции users:

fitisov_db> { ok: 1 }
fitisov_db> 
fitisov_db> Вывод списка коллекций:

fitisov_db> admin       40.00 KiB
config      60.00 KiB
fitisov_db   8.00 KiB
local       72.00 KiB
fitisov_db> 
fitisov_db> Добавление документов с данными о пользователях:

fitisov_db> {
  acknowledged: true,
  insertedId: ObjectId('66047a8ceec851b8ffca690c')
}
fitisov_db> ... ... {
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('66047a8ceec851b8ffca690d'),
    '1': ObjectId('66047a8ceec851b8ffca690e')
  }
}
fitisov_db> 
fitisov_db> Вывод всех данных коллекции users:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690c'), userId: 1, login: 'u1' },
  { _id: ObjectId('66047a8ceec851b8ffca690d'), userId: 2, login: 'u2' },
  { _id: ObjectId('66047a8ceec851b8ffca690e'), userId: 3, login: 'u3' }
]
fitisov_db> 
fitisov_db> Создание коллекции messages:

fitisov_db> { ok: 1 }
fitisov_db> 
fitisov_db> Вывод списка коллекций:

fitisov_db> admin       40.00 KiB
config      60.00 KiB
fitisov_db  16.00 KiB
local       72.00 KiB
fitisov_db> 
fitisov_db> Добавление данных в коллекцию messages:

fitisov_db> ... ... ... ... ... {
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('66047a8ceec851b8ffca690f'),
    '1': ObjectId('66047a8ceec851b8ffca6910'),
    '2': ObjectId('66047a8ceec851b8ffca6911'),
    '3': ObjectId('66047a8ceec851b8ffca6912'),
    '4': ObjectId('66047a8ceec851b8ffca6913')
  }
}
fitisov_db> 
fitisov_db> Вывод всех документов коллекции users:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690c'), userId: 1, login: 'u1' },
  { _id: ObjectId('66047a8ceec851b8ffca690d'), userId: 2, login: 'u2' },
  { _id: ObjectId('66047a8ceec851b8ffca690e'), userId: 3, login: 'u3' }
]
fitisov_db> 
fitisov_db> Создание курсора, содержащего значения из коллекций users и messages:

fitisov_db> ... ... ... ... ... ... ... ... ... [
  {
    _id: ObjectId('66047a8ceec851b8ffca690c'),
    userId: 1,
    login: 'u1',
    userMsg: [
      {
        _id: ObjectId('66047a8ceec851b8ffca690f'),
        userId: 1,
        msg: 'msg1'
      },
      {
        _id: ObjectId('66047a8ceec851b8ffca6912'),
        userId: 1,
        msg: 'msg4'
      }
    ]
  },
  {
    _id: ObjectId('66047a8ceec851b8ffca690d'),
    userId: 2,
    login: 'u2',
    userMsg: [
      {
        _id: ObjectId('66047a8ceec851b8ffca6911'),
        userId: 2,
        msg: 'msg3'
      }
    ]
  },
  {
    _id: ObjectId('66047a8ceec851b8ffca690e'),
    userId: 3,
    login: 'u3',
    userMsg: [
      {
        _id: ObjectId('66047a8ceec851b8ffca6910'),
        userId: 3,
        msg: 'msg2'
      },
      {
        _id: ObjectId('66047a8ceec851b8ffca6913'),
        userId: 3,
        msg: 'msg5'
      }
    ]
  }
]
fitisov_db> 
fitisov_db> Замена документа в коллекции messages, удовлетворяющего заданному условию:

fitisov_db> {
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
fitisov_db> 
fitisov_db> Вывод всех документов коллекции messages:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690f'), userId: 1, msg: 'msg1' },
  { _id: ObjectId('66047a8ceec851b8ffca6910'), userId: 3, msg: 'msg2' },
  { _id: ObjectId('66047a8ceec851b8ffca6911'), userId: 2, msg: 'msg3' },
  { _id: ObjectId('66047a8ceec851b8ffca6912'), userId: 1, msg: 'msg4' },
  {
    _id: ObjectId('66047a8ceec851b8ffca6913'),
    login: 'user_x',
    msg: 'Привет!'
  }
]
fitisov_db> 
fitisov_db> Изменение значения поля документа:

fitisov_db> {
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
fitisov_db> 
fitisov_db> Вывод всех документов коллекции users:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690c'), userId: 1, login: 'u1' },
  { _id: ObjectId('66047a8ceec851b8ffca690d'), userId: 2, login: 'u2' },
  {
    _id: ObjectId('66047a8ceec851b8ffca690e'),
    userId: 3,
    login: 'u3',
    age: 35
  }
]
fitisov_db> 
fitisov_db> Поиск документа со значением login, равным u2 и изменение значения поля age на 53:

fitisov_db> { _id: ObjectId('66047a8ceec851b8ffca690d'), userId: 2, login: 'u2' }
fitisov_db> 
fitisov_db> Вывод всех документов коллекции users:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690c'), userId: 1, login: 'u1' },
  {
    _id: ObjectId('66047a8ceec851b8ffca690d'),
    userId: 2,
    login: 'u2',
    age: 53
  },
  {
    _id: ObjectId('66047a8ceec851b8ffca690e'),
    userId: 3,
    login: 'u3',
    age: 35
  }
]
fitisov_db> 
fitisov_db> Удаление документа из коллекции messages:

fitisov_db> { acknowledged: true, deletedCount: 1 }
fitisov_db> 
fitisov_db> Вывод всех документов коллекции messages:

fitisov_db> [
  { _id: ObjectId('66047a8ceec851b8ffca690f'), userId: 1, msg: 'msg1' },
  { _id: ObjectId('66047a8ceec851b8ffca6910'), userId: 3, msg: 'msg2' },
  { _id: ObjectId('66047a8ceec851b8ffca6911'), userId: 2, msg: 'msg3' },
  {
    _id: ObjectId('66047a8ceec851b8ffca6913'),
    login: 'user_x',
    msg: 'Привет!'
  }
]
fitisov_db> 
fitisov_db> Удаление коллекции messages и содержащихся в ней документов из текущей базы данных:

fitisov_db> true
fitisov_db> 
fitisov_db> Удаление коллекции users и содержащихся в ней документов из текущей базы данных:

fitisov_db> true
fitisov_db> 
fitisov_db> Удаление всей информации из текущей базы данных:

fitisov_db> { ok: 1, dropped: 'fitisov_db' }
fitisov_db> 