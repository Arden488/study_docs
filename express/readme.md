# Express web server

### Установка express
Создаём папку проекта, делаем npm init (стартовая точка для приложения - app.js), и устанавливаем express как зависимость (версия 4.х+)
```sh
npm install express -S
```

### Шаги по настройке и запуску сервера на express
1. Внутри app.js подключаем express.
    ```js
    const express = require('express')
    ```
2. Вызываем express и присваиваем переменной app
    ```js
    const app = express()
    ```
3. Добавляем вызов метода для прослушивания порта. В callback пишем сервисное сообщение (через console.log) о том, что сервер работает и слушает (как товарищ :ear: Майор)
    ```js
    app.listen(PORT, callback)
    ```
4. Запускаем сервер через
    ```sh
    nodemon app.js
    ```
5. Добавим обработчик для корневой директории с помощью метода
    ```js
    app.get(PATH, callback(req, res))
    ```
6. В обработчике отдаём сообщение через 
    ```js
    res.send('TEXT')
    ```
7. Пробуем добавить другие различные обработчики post / patch / put / delete
8. Ставим Postman для удобного тестирования - [скачать](https://www.getpostman.com/downloads/)
9. Пробуем отправить разные запросы на разные узлы и получаем разные ответы
10. Пробуем добавить обработчик промежуточных событий ДО вызова обработчика пути (app.get и других)
    ```js
    app.use((req, res, next) => {
        ...
        next();
    })
    ```
   