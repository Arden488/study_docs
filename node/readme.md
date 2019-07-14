# Node web server

### Install Node
[Download and install](https://nodejs.org/en/download/)
Target version - 10+

### Steps to setup and run simple server
1. Создать папку проекта и файл index.js внутри
2. Написать в index.js любой тестовый js-код
3. Запустить код командой (если есть проблемы с запуском - переустановить node.js)
    ```sh
    node index.js
    ```
4. Очистить файл index.js и добавить подключение модуля http (присвоив переменной)
    ```js
    require("http");
    ```
5. Присвоить другой переменной результат метода createServer из модуля http (без аргументов) - это будет обработчик сервера
    ```js
    http.createServer()
    ```
6. Вызвать метод listen на объекте сервера с указанием одного аргумента - порта для прослушивания запросов (host не обязателен, по умолчанию будет - localhost)
    ```sh
    listen(PORT)
    ```
7. Добавить метод, который будет слушать событие request и запустит функцию принимающую два аргумента - req и res
    ```sh
    .on('eventName', callback)
    ```
8. Внутри этой функции вызвать код для выводы любого сообщения
    ```sh
    res.end('TEXT')
    ```

### Useful links
[Official website](https://nodejs.org/en/)
