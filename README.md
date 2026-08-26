# API Connect

## Sobre o projeto

A **API Connect** é uma API REST desenvolvida como parte da Experiência Prática II da disciplina de Desenvolvimento Back-end.

O objetivo do projeto é implementar uma API para gerenciamento de usuários, permitindo realizar operações de cadastro, consulta, atualização e exclusão de registros por meio do protocolo HTTP.

A aplicação utiliza uma estrutura de dados em memória para simular a persistência das informações, sendo adequada ao desenvolvimento de um Produto Mínimo Viável (MVP).

## Tecnologias utilizadas

* Node.js
* Express
* JavaScript
* Nodemon
* JSON
* Git
* GitHub

## Estrutura do projeto

```text
api-connect/
│
├── server.js
├── package.json
├── .gitignore
├── README.md
│
└── src/
    ├── routes/
    │   └── usuariosRoutes.js
    ├── controllers/
    │   └── usuariosController.js
    └── data/
        └── usuarios.js
```

## Como executar o projeto

### 1. Clonar o repositório

```bash
git clone URL_DO_REPOSITORIO
```

### 2. Acessar a pasta

```bash
cd api-connect-pedro-simoes
```

### 3. Instalar as dependências

```bash
npm install
```

### 4. Iniciar o servidor

```bash
node server.js
```

Também é possível executar a aplicação utilizando o Nodemon:

```bash
npx nodemon server.js
```

O servidor será iniciado na porta `3000`.

```text
http://localhost:3000
```

## Endpoints

| Método | Endpoint        | Descrição                     | Status de sucesso |
| ------ | --------------- | ----------------------------- | ----------------- |
| GET    | `/usuarios`     | Lista todos os usuários       | 200 OK            |
| GET    | `/usuarios/:id` | Busca um usuário pelo ID      | 200 OK            |
| POST   | `/usuarios`     | Cadastra um novo usuário      | 201 Created       |
| PUT    | `/usuarios/:id` | Atualiza um usuário existente | 200 OK            |
| DELETE | `/usuarios/:id` | Remove um usuário             | 204 No Content    |

## Exemplo de cadastro

### POST `/usuarios`

Corpo da requisição:

```json
{
  "nome": "Pedro Simões",
  "email": "pedro@email.com"
}
```

Resposta de sucesso:

```json
{
  "data": {
    "id": 3,
    "nome": "Pedro Simões",
    "email": "pedro@email.com"
  }
}
```

**Status:** `201 Created`

Caso `nome` ou `email` não seja informado, a API retorna:

```json
{
  "error": "Os campos nome e email são obrigatórios."
}
```

**Status:** `400 Bad Request`

## Busca por ID

### GET `/usuarios/1`

Retorna os dados do usuário correspondente ao ID informado.

Caso o ID não exista, a API retorna uma mensagem de erro com o status:

`404 Not Found`

## Atualização

### PUT `/usuarios/1`

Exemplo de corpo:

```json
{
  "nome": "Pedro Simões Atualizado",
  "email": "pedro.atualizado@email.com"
}
```

Em caso de sucesso, a API retorna o usuário atualizado com o status `200 OK`.

## Exclusão

### DELETE `/usuarios/1`

Remove o usuário correspondente ao ID informado.

Em caso de sucesso, a API retorna o status `204 No Content`.

Caso o usuário não seja encontrado, é retornado o status `404 Not Found`.

## Códigos HTTP utilizados

* `200 OK` — Requisição realizada com sucesso.
* `201 Created` — Recurso criado com sucesso.
* `204 No Content` — Recurso excluído com sucesso.
* `400 Bad Request` — Dados enviados são inválidos ou incompletos.
* `404 Not Found` — Recurso solicitado não foi encontrado.

## Persistência dos dados

Por se tratar de um MVP, os usuários são armazenados em um array JavaScript em memória. Dessa forma, os registros criados durante a utilização da API permanecem disponíveis enquanto o servidor estiver em execução.

Ao reiniciar o servidor, os dados adicionados durante a execução são perdidos.
