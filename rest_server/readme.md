# REST server (Express, mongoose)

Задача: создать API сервер для добавления/чтения/обновления/удаления двух типов объектов: кодеров и проектов. К каждому проекту привязан кодер, при чтении проекта необходимо отдавать не только ID кодера, но также и всю остальную информацию.
Готовый результат залить в git

### Структура данных
```js
Coder {
    firstName: String,
    lastName: String,
    email: String,
    birth_date: Date
}

Project {
    title: String,
    description: String,
    createdAt: Date,
    maintainer: Coder
}
```

### Заготовка сервера
Вручную прописываем инициализацию сервера и слушаем порт 3456 (см. https://github.com/Arden488/study_docs/tree/master/express)

### Полезные куски кода
Подключаем обработку json и URL encoded:
```js
app.use(express.json());
app.use(express.urlencoded({ extended: false }));
```

Отправка контента из экспресса к клиенту:
```js
res.send(text);
res.status(404).send('Not found');
res.sendStatus(200);
```

Получение параметров в экспресс:
```js
app.get('/projects/:id', ...); // domain.tld/projects/123
req.params.id // 123

app.get('/projects', ...); // domain.tld/projects?id=123
req.query.id // 123
```

Отдельный файл роутингов:
```js
const express = require("express");
const router = express.Router();
...

router
  .get("/", controller.method)
  ...

module.exports = router;
```

Подключение mongoose:
```js
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost/demo_projects", { useNewUrlParser: true });
const db = mongoose.connection;
db.once("open", () => console.log("DB connection established"));
```

Создание модели:
```js
const mongoose = require("mongoose");

const SomeSchema = mongoose.Schema({
  someField: {
      type: 'string',
      required: true, // необязательно
      unique: true // необязательно
  },
  otherField: Number
});

module.exports = mongoose.model("some", SomeSchema);
```

Контроллер:
```js
const Some = require("../models/Some");

exports.method = (req, res) => {};
```

Запись в mongo:
```js
const someObj = new Some({ ... });
someObj.save().then(() => ...).catch(...);
```

Чтение из mongo 1й записи:
```js
Some.findById(id).then(some => ...).catch(...);
```

Чтение из mongo всех записей:
```js
Some.find().then(somes => ...).catch(...);
```

Обновление записи:
```js
Some.findOneAndUpdate({ _id: id }, updateDataObj, { new: true }).then(some => ...).catch(...);
```

Удаление записи:
```js
Some.deleteOne({ _id: id }).then(() => ...).catch(...);
```
