# MongoDB и Mongoose

### Установка MongoDB
Ставим MongoDB локально - [гайды на англ](https://docs.mongodb.com/manual/administration/install-community/)

### Шаги по настройке mongoose и подключению к базе
1. Ставим mongoose
    ```sh
    npm install mongoose -S
    ```
2. Подключаем mongoose в express приложение
    ```js
    const mongoose = require('mongoose');
    mongoose.connect('mongodb://localhost/test', {useNewUrlParser: true});
    ```
3. Создаём демо схему данных (см. документацию для разных типов данных и настроек)
    ```js
    const testSchema = new mongoose.Schema({
        name: String
    });
    ```
4. Создаём модель на основе схемы данных
    ```js
    const TestModel = mongoose.model('TestModel', testSchema);
    ```
5. Создаём новый объект этого класса (модели)
    ```js
    const testItem = new TestModel({ name: 'MamboJambo' })
    ```
6. Сохраняем данные
    ```js
    testItem.save().then(() => {
        // ..
    });
    ```
7. Ищем все данные
    ```js
    TestModel.find((err, items) => {
        if (err) return console.error(err);
        console.log(items);
    });
    ```
7. Ищем данные по ID
    ```js
    TestModel.findById(ID, (err, item) => {
        if (err) return console.error(err);
        console.log(item);
    });
    ```
8. Удаляем данные по ID
    ```js
    TestModel.deleteOne({ _id: ID }).then(() => {
        // ..
    });
    ```
9. Удаляем все данные
    ```js
    TestModel.deleteMany({}).then(() => {
        // ..
    });
    ```

