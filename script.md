Passo a passo projeto

ESTRUTURA DA APLICAÇÃO
- Criar pasta para projeto
    - npm init -y
    - npm i -D typescript
    - npm install -D @types/node
    - npm install tsx -D
        - Converte código TSX para JS
    - Criar arquivo de configuração do TypeScript
        - npx tsc --init
        - Criar arquivo tsconfig.json
            - alterar atributo target: "target": "es2020"
            - (OPCIONAL) converter arquivo: npx tsc src/index.ts
                - Criar um arquivo em JavaScript para o node rodar (arquivos .ts o node nao consegue rodar)
    - npm i fastify
    - npm i eslint @rocketseat/eslint-config -D
        - Padronizacao do projeto (Rockeseat)
        - Criar arquivo .eslintrc.json na raiz do projeto

    - Criar pasta src
        - criar arquivo server.ts

- No arquivo package.json criar script para rodar aplicacao em desenvolvimento e formatacao lint
    - "scripts": {"dev": "tsx watch src/server.ts"}
        - npm run dev
    - "lint": "eslint src --ext .ts --fix"
        - npm run lint 

BANCO DE DADOS:
AULA: CONFIGURANDO O KNEX
- SQLite
    - npm install sqlite3
- Knex
    - npm install knex
    - npx knex -h
        - Comando para abrir um menu help do knex
- Na pasta src
    - criar arquivo database.ts
        - arquivo de config com banco de dados
    - Na raiz do projeto criar pasta db
- No arquivo .gitignore, adicionar arquivo app.db
    - Esse arquivo NUNCA sobe pro repo remoto

AULA: CRIANDO PRIMEIRA MIGRATION
- Criando tabelas no banco de dados
- Migrations
    - Realizam um controle de versões do banco de dados

- Na raiz do prjeto, criar arquivo knexfile.ts
    - importar config do database.ts
- No arquivo package.json
    - Adicionar script para rodar migrations
        - "knex": "node --no-warnings --loader tsx ./node_modules/.bin/knex"
        - script para rodar o knex com typescript
    - npm run knex migrate:make create-transactions 
        - Cria uma pasta migration com o arquivo typescript vazio para escrever a criação da tabela
    - No arquivo criado pelo comando criar a migration
    - npm run knex -- migrate:latest
        - roda as migrations
    - Caso tenha errado na migration, pode-se rodar o comando abaixo para desfazer a migration
        - NÃO ALTERAR UMA MIGRATION DEPOIS DE TER SUBIDO PARA O REPOSITÓRIO REMOTO
        - npm run knex -- migrate:rollback

AULA: REALIZANDO QUERIES COM KNEX
- No arquivo server.ts, no método get
    - Criar queries
````
app.get('/hello', async () => {
  // const transaction = await knex('transactions')
  //   .insert({
  //     id: crypto.randomUUID(),
  //     title: 'Transação teste',
  //     amount: 1000,
  //   })
  //   .returning('*')

  const transaction = await knex('transactions')
    .where('amount', 1000)
    .select('*')

  return transaction
})
```

AULA: VARIAVEIS AMBIENTE
- Na raiz do projeto criar arquivo .env
- ADICIONAR ARQUIVO NO .gitignore
- npm i dotenv
- No arquivo database.ts
    - importar dotenv/config
    - substitiur o filename pela variaveis ambiente
- Na raiz do projeto criar arquivo .env.exemple
    - Utilizado para que outras pessoas possam saber quaias variais estão sendo utilizadas no projeto

AULA: TRATANDO ENV COM ZOD
- npm i zod
- Na pasta src, criar pasta env
    - criar arquivo index.ts
- O zod realiza uma verificação se as variaveis ambientes estão dentro do formato esperado