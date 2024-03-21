Команды и результаты их выполнения:

Команда:
mongosh

Ответ системы:
(base) aleksei@192:~/Yandex.Disk/Алексей/IT/ИТМО/Дисциплины/Взаимодействие с БД/
Практические задания$ cd MongoDB/
(base) aleksei@192:~/Yandex.Disk/Алексей/IT/ИТМО/Дисциплины/Взаимодействие с БД/
Практические задания/MongoDB$ pluma MongoDB_tasks.md 

(pluma:1832): Gtk-CRITICAL **: 22:39:04.148: gtk_notebook_get_tab_label: assertion 'list != NULL' failed

(pluma:1832): Gtk-CRITICAL **: 22:39:04.253: gtk_notebook_get_tab_label: assertion 'list != NULL' failed

(pluma:1832): Gtk-CRITICAL **: 22:39:04.347: gtk_notebook_get_tab_label: assertion 'list != NULL' failed
(base) aleksei@192:~/Yandex.Disk/Алексей/IT/ИТМО/Дисциплины/Взаимодействие с БД/
Практические задания/MongoDB$ pluma MongoDB_tasks.md&
[1] 1866
(base) aleksei@192:~/Yandex.Disk/Алексей/IT/ИТМО/Дисциплины/Взаимодействие с БД/
Практические задания/MongoDB$ mongosh
Current Mongosh Log ID:	65fb3ba38ebc958a78db83af
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.2.0
MongoNetworkError: connect ECONNREFUSED 127.0.0.1:27017
(base) aleksei@192:~/Yandex.Disk/Алексей/IT/ИТМО/Дисциплины/Взаимодействие с БД/
Практические задания/MongoDB$ 

Команда:
show dbs

use test

show tables

db.createCollection("users")

db.users.countDocuments()

let name="userName";

console.log(name)

db.users.insertOne({ "name": "Ivan"})

db.users.find({})

db.users.findOneAndUpdate({}, { $set: { name: "Алексей Фитисов" } })

db.users.aggregate([
   {
     $lookup:
       {
         from: "big",
         localField: "name",
         foreignField: "name",
         as: "inventory_Big"
       }
  }
])

