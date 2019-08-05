# Техническое задание - Бэкэнд блога Tech Magazine

Проект: Блог Tech Magazine размещает статьи о темах связанных с разработкой программного обеспечения и эффективности специалистов
Задача: сделать две версии бэкэнда для блога - одна для реализации REST API доступа к данным, другая GraphQL API. В рамках технического задания опущены требования к реализации авторизации и менеджмента пользователей.
Готовый результат залить в git и в heroku, предоставить ссылку на работающий API сервер.

### Структура данных
```sh
Author {
    id: ID,
    name: String
}

Source {
    id: ID,
    name: String
}

Article {
    id: ID,
    "source": Source,
    "author": Author,
    "title": String,
    "description": String,
    "url": String,
    "urlToImage": String,
    "publishedAt": DateTime,
    "content": String
}
```

### Код сервера
Для написания кода сервера использовать код из уроков по созданию REST и GraphQL API
https://github.com/Arden488/study_docs/tree/master/rest_server
https://github.com/Arden488/study_docs/tree/master/graphql

### Схема данных
https://github.com/study_docs/tree/master/blog/readme.md

### Размещение БД
БД будет размещена на облачном сервисе MongoDB - Atlas. Туториал по настройке сервера - https://docs.atlas.mongodb.com/getting-started/

### Размещение сервера
Сервер будет размещен на heroku. Туториал - https://devcenter.heroku.com/articles/deploying-nodejs
