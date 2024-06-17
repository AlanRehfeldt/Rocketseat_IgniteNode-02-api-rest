
# Rocketseat Ignite Node.js - Desafio 02: API REST

## Descrição

Este projeto é uma API REST desenvolvida como parte do curso Ignite da Rocketseat. A API permite gerenciar dados utilizando Node.js e TypeScript, com suporte a operações CRUD (Create, Read, Update, Delete). O projeto faz uso de várias [tecnologias modernas](#tecnologias-utilizadas) para garantir um desenvolvimento robusto e eficiente.

## Estrutura do Projeto

- **src/**: Contém o código-fonte da aplicação.
- **db/**: Contém as migrações de banco de dados.
- **test/**: Contém os testes da aplicação.

## Instalação

Para rodar este projeto, siga os passos abaixo:

1. Clone o repositório:
   ```sh
   git clone https://github.com/AlanRehfeldt/Rocketseat_IgniteNode-02-api-rest.git
   cd Rocketseat_IgniteNode-02-api-rest
   ```

2. Instale as dependências:
   ```sh
   npm install
   ```

3. Configure as variáveis de ambiente:
   - Copie o arquivo `.env.exemple` para `.env` e ajuste as variáveis conforme necessário.
   - Copie o arquivo `.env.test.exemple` para `.env.test` para configuração de testes.

## Uso

### Executando a Aplicação

Para iniciar a aplicação em modo de desenvolvimento, execute:
```sh
npm run dev
```

### Executando o Banco de Dados e Migrations

Para configurar e executar o banco de dados, siga os passos abaixo:

1. Crie as tabelas no banco de dados rodando as migrations:
```sh
npm run knex -- migrate:latest
```

2. Para desfazer as migrations (caso necessário):
```sh
npm run knex -- migrate:rollback
```

3. Para criar uma nova migration:
```sh
npm run knex -- migrate:make migration_name
```

### Rodando Testes

Para executar os testes, use o comando:
```sh
npm test
```

Os testes incluem:
- **Testes end-to-end**: Simulam o uso da aplicação de ponta a ponta para garantir que todos os fluxos funcionam corretamente.

## Tecnologias Utilizadas

- Node.js
- TypeScript
- Knex.js
- SQLite (pode ser alterado para outro banco de dados conforme configuração)
- Zod
- Cookies
- Tsx
- Dotenv
- vitest
- Supertest

## Licença

Este projeto está licenciado sob a Licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
