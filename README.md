# Exercise Tracker API

Este é um projeto de API para rastreamento de exercícios físicos, desenvolvido como parte do desafio do FreeCodeCamp.

## Tecnologias Utilizadas

- Node.js
- Express.js
- UUID (para gerar IDs únicos)
- Cors
- Dotenv

## Instalação e Execução

1. Clone este repositório:
   ```sh
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```
2. Instale as dependências:
   ```sh
   npm install
   ```
3. Inicie o servidor:
   ```sh
   npm run start
   ```
   O servidor será iniciado na porta `3000` ou em uma porta definida na variável de ambiente `PORT`.

## Endpoints da API

### Criar um novo usuário

**POST /api/users**

**Parâmetros:**
- `username` (string) - Nome do usuário

**Exemplo de requisição:**
```sh
curl -X POST -d "username=exemplo" http://localhost:3000/api/users
```

**Exemplo de resposta:**
```json
{
  "username": "exemplo",
  "_id": "b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9"
}
```

---

### Obter todos os usuários

**GET /api/users**

**Exemplo de resposta:**
```json
[
  {
    "username": "exemplo",
    "_id": "b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9"
  }
]
```

---

### Adicionar um exercício

**POST /api/users/:_id/exercises**

**Parâmetros:**
- `description` (string) - Descrição do exercício
- `duration` (number) - Duração do exercício (em minutos)
- `date` (string, opcional) - Data do exercício (formato YYYY-MM-DD). Se não for fornecida, a data atual será usada.

**Exemplo de requisição:**
```sh
curl -X POST -d "description=corrida&duration=30&date=2023-10-10" http://localhost:3000/api/users/b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9/exercises
```

**Exemplo de resposta:**
```json
{
  "username": "exemplo",
  "_id": "b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9",
  "description": "corrida",
  "duration": 30,
  "date": "Tue Oct 10 2023"
}
```

---

### Obter o histórico de exercícios de um usuário

**GET /api/users/:_id/logs**

**Parâmetros opcionais:**
- `from` (string) - Filtrar os exercícios a partir de uma data (YYYY-MM-DD)
- `to` (string) - Filtrar os exercícios até uma data (YYYY-MM-DD)
- `limit` (number) - Limitar a quantidade de exercícios retornados

**Exemplo de requisição:**
```sh
curl http://localhost:3000/api/users/b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9/logs?from=2023-01-01&to=2023-12-31&limit=2
```

**Exemplo de resposta:**
```json
{
  "username": "exemplo",
  "count": 1,
  "_id": "b1d5f2e0-3f1b-4a79-9c13-ef0c0b63d6a9",
  "log": [
    {
      "description": "corrida",
      "duration": 30,
      "date": "Tue Oct 10 2023"
    }
  ]
}
```
