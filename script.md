Passo a passo projeto

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

