# API REST - Daily Diet

API do desafio Daily Diet, desenvolvida com Fastify, TypeScript e Knex.

## Front-end

O front-end deste projeto esta disponivel em:

https://github.com/jullianedipaula/front-daily-diet

## Tecnologias

- Node.js
- TypeScript
- Fastify
- Knex
- SQLite (padrao) ou PostgreSQL
- Zod
- Vitest + Supertest

## Requisitos

- Node.js
- npm

## Instalacao

1. Instale as dependencias:

```bash
npm install
```

2. Crie os arquivos de ambiente:

- `.env`
- `.env.test`

Exemplo:

```env
NODE_ENV=development
PORT=3333
DATABASE_CLIENT=sqlite
DATABASE_URL=./db/app.db
```

Para usar PostgreSQL:

```env
DATABASE_CLIENT=pg
DATABASE_URL=postgres://usuario:senha@localhost:5432/daily_diet
```

## Banco de dados

Rodar migracoes:

```bash
npm run knex migrate:latest
```

Reverter migracoes:

```bash
npm run knex migrate:rollback --all
```

## Executando o projeto

Modo desenvolvimento:

```bash
npm run dev
```

Build:

```bash
npm run build
```

Testes:

```bash
npm run test
```

A API sobe por padrao em `http://localhost:3333`.

## Fluxo de autenticacao por sessao

Ao criar um usuario, a API define um cookie `sessionId`. Esse cookie identifica o usuario e deve ser enviado nas rotas de refeicao.

## Rotas principais

### Usuarios

- `POST /users` - cria usuario

Body:

```json
{
  "name": "John Doe",
  "email": "johndoe@gmail.com"
}
```

### Refeicoes

- `POST /meals` - cria refeicao
- `GET /meals` - lista refeicoes do usuario
- `GET /meals/:mealId` - busca refeicao por id
- `PUT /meals/:mealId` - atualiza refeicao
- `DELETE /meals/:mealId` - remove refeicao
- `GET /meals/metrics` - retorna metricas do usuario

Exemplo de body para criar/atualizar refeicao:

```json
{
  "name": "Breakfast",
  "description": "Its a breakfast",
  "isOnDiet": true,
  "date": "2026-03-10T08:00:00.000Z"
}
```

## Scripts disponiveis

- `npm run dev` - inicia servidor em modo desenvolvimento
- `npm run knex` - executa comandos do Knex CLI
- `npm run format` - formata codigo com Biome
- `npm run build` - gera build em `build/`
- `npm run test` - executa testes com Vitest
