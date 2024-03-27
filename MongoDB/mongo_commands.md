console.log('Создание базы данных:');
use fitisov_db;

console.log('Создание коллекции users:');
db.createCollection('users');

console.log('Вывод списка коллекций:');
show dbs;

console.log('Добавление документов с данными о пользователях:');
db.users.insertOne({userId: 1, login:  'u1'});
db.users.insertMany([{userId: 2, login: 'u2'},
{userId: 3, login: 'u3'}
]);

console.log('Вывод всех данных коллекции users:');
db.users.find();

console.log('Создание коллекции messages:');
db.createCollection('messages');

console.log('Вывод списка коллекций:');
show dbs;

console.log('Добавление данных в коллекцию messages:');
db.messages.insertMany([{userId: 1, msg: 'msg1'},
{userId: 3, msg: 'msg2'},
{userId: 2, msg: 'msg3'},
{userId: 1, msg: 'msg4'},
{userId: 3, msg: 'msg5'}
]);

console.log('Вывод всех документов коллекции users:');
db.users.find();

console.log('Создание курсора, содержащего значения из коллекций users и messages:');
db.users.aggregate([
  {
    $lookup: {
      from: 'messages',
      localField: 'userId',
      foreignField: 'userId',
      as: 'userMsg'
    }
  }
]);

console.log('Замена документа в коллекции messages, удовлетворяющего заданному условию:');
db.messages.replaceOne({msg: 'msg5'}, {login: 'user_x', msg : 'Привет!'});

console.log('Вывод всех документов коллекции messages:');
db.messages.find();

console.log('Изменение значения поля документа:');
db.users.updateOne({userId: 3}, {$set: {age: 35}});

console.log('Вывод всех документов коллекции users:');
db.users.find();

console.log('Поиск документа со значением login, равным u2 и изменение значения поля age на 53:');
db.users.findOneAndUpdate({login: 'u2'}, { $set: {age: 53}});

console.log('Вывод всех документов коллекции users:');
db.users.find();

console.log('Удаление документа из коллекции messages:');
db.messages.deleteOne({msg: 'msg4'});

console.log('Вывод всех документов коллекции messages:');
db.messages.find();

console.log('Удаление коллекции messages и содержащихся в ней документов из текущей базы данных:');
db.messages.drop();

console.log('Удаление коллекции users и содержащихся в ней документов из текущей базы данных:');
db.users.drop();

console.log('Удаление всей информации из текущей базы данных:');
db.dropDatabase();