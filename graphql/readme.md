# GraphQL server (GraphQL, Express, mongoose)

Задача: создать API GraphQL сервер для добавления/чтения/обновления/удаления двух типов объектов: кодеров и проектов. К каждому проекту привязан кодер, при чтении проекта необходимо отдавать не только ID кодера, но также и всю остальную информацию.
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

### Ставим нужные библиотеки и модули для GraphQL
```sh
npm i express-graphql graphql -S
```

### Полезные куски кода
Подключаем GraphQL
```js
app.use(
  "/graphql",
  graphQLHttp({
    schema: buildSchema(schema),
    rootValue: resolvers,
    graphiql: true
  })
);
```

Схема:
```js
type Query {
    allProjects: [Project]
    getProjectById(ID: ID): Project
    allCoders: [Coder]
    getCoderById(ID: ID): Coder
}

input CoderInput {
    _id: ID!
}

input CreateProjectInput {
    title: String!,
    description: String,
    createdAt: Date!,
    maintainer: CoderInput!
}

input UpdateProjectInput {
    title: String,
    description: String,
    createdAt: Date,
    maintainer: CoderInput
}

input CreateCoderInput {
    firstName: String,
    lastName: String!,
    email: String!,
    birth_date: Date
}

input UpdateCoderInput {
    firstName: String,
    lastName: String,
    email: String,
    birth_date: Date
}

type Mutation {
    createProject(input: CreateProjectInput): Project
    updateProject(id: ID!, input: UpdateProjectInput): Project
    deleteProject(id: ID!): Project
    createCoder(input: CreateCoderInput): Coder
    updateCoder(id: ID!, input: UpdateCoderInput): Coder
    deleteCoder(id: ID!): Coder
}
```

Резолверы:
```js
module.exports = {
    createProject: args => { return ... },
    updateProject: args => { return ... },
    deleteProject: args => { return ... },
    createCoder: args => { return ... },
    updateCoder: args => { return ... },
    deleteCoder: args => { return ... },
}
```

Доступ к аргументам:
```js
createProject: args => {
    const { title } = args.input;
    return ...
}
```
