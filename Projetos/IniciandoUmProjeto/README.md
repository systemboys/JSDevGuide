> ## Iniciando um projeto
>
> ![Docker](./images/StartingAProject.png)

> ### *Summary*

> - [Configuração inicial](#configuração-inicial)
> - [Estrutura de pastas](#estrutura-de-pastas)
> - [Configuração do TypeScript](#configuração-do-typescript)

----

## Configuração inicial

1. Abra o terminal.
2. Navegue até o diretório onde você deseja criar o projeto.
3. Digite o seguinte comando:

    ```bash
    npm init -y
    ```

    Este comando criará um novo arquivo `package.json` com as configurações padrão. O `-y` é usado para preencher automaticamente as opções padrão.

    ```json
    {
        "name": "backend",
        "version": "1.0.0",
        "main": "index.js",
        "license": "MIT"
    }
    ```

    > O arquivo `package.json` é um documento fundamental em qualquer projeto Node.js. Ele serve para várias funções:
    > 
    > 1. **Gerenciamento de dependências**: Lista todas as dependências do projeto, permitindo que qualquer pessoa possa instalar todas as dependências necessárias com um único comando: `npm install`.
    > 
    > 2. **Scripts**: Define "scripts" que você pode rodar com `npm run <nome_do_script>`. Isso pode incluir coisas como iniciar o servidor, rodar testes, ou qualquer outra tarefa automatizada.
    > 
    > 3. **Informações do projeto**: Inclui metadados sobre o projeto, como o nome, a versão, a descrição, o autor e a licença.
    > 
    > 4. **Configurações de ambiente**: Pode incluir configurações específicas para o ambiente de desenvolvimento.
    > 
    > Em resumo, o `package.json` é uma maneira conveniente de organizar e gerenciar as configurações do seu projeto Node.js. É um dos primeiros arquivos que você deve criar ao iniciar um novo projeto Node.js.

    Após esse comando, você pode adicionar pacotes ao seu projeto com `npm install <nome_do_pacote>`.

4. Crie sua estrutura de diretório:

    ```tex
    /myProject/
    ├─ /src/
    │  ├─ /controllers/
    │  ├─ /repositories/
    │  ├─ /routes/
    │  ├─ /services/
    │  └─ index.ts
    └─ package.json
    ```

    > A estrutura acima, é um exemplo de uma estrutura padrão.

5. Configurações do "TypeScript".

    Você pode instalar o "Nodemon", "ts-node" e "sucrase" como dependências de desenvolvimento usando o NPM com o seguinte comando:

    ```bash
    npm install --save-dev nodemon ts-node sucrase
    ```

    Agora, vamos entender o que cada pacote faz:

    - **Nodemon**: É uma ferramenta que ajuda a desenvolver aplicativos baseados em node.js ao reiniciar automaticamente a aplicação de node quando detecta alterações de arquivo no diretório.

    - **ts-node**: É uma ferramenta que permite executar TypeScript diretamente, sem a necessidade de compilar os arquivos para JavaScript primeiro. É muito útil durante o desenvolvimento, quando você quer testar rapidamente seu código.

    - **Sucrase**: É um compilador de código super rápido que permite que você escreva código em sintaxes modernas (como ES6, JSX, TypeScript, etc.) e o compila para versões mais antigas do JavaScript que podem ser executadas em ambientes mais antigos.

    Esses três pacotes são comumente usados em conjunto para criar um ambiente de desenvolvimento eficiente para projetos Node.js.

6. Instale o TypeScript usando o NPM com o seguinte comando:

    ```bash
    npm install typescript
    ```

    Este comando instalará o TypeScript como uma dependência do seu projeto. Agora você pode usar o TypeScript em seu projeto Node.js!

7. Inicialize um novo projeto TypeScript usando o NPM com o seguinte comando:

    ```bash
    npx tsc --init
    ```

    Este comando cria um novo arquivo `tsconfig.json` na raiz do seu projeto. O arquivo `tsconfig.json` é usado para configurar o compilador TypeScript para o seu projeto. Ele permite que você especifique várias opções de compilação, como o diretório de saída para os arquivos compilados, quais versões do JavaScript devem ser suportadas, quais recursos experimentais devem ser habilitados, entre outras coisas.

    O comando `npx` é uma ferramenta que vem com o NPM e permite executar pacotes Node.js que foram instalados localmente em seu projeto. Neste caso, estamos usando `npx` para executar o compilador TypeScript (`tsc`) com a opção `--init` para inicializar um novo projeto TypeScript.

8. No arquivo `package.json`, altere ...

    ```json
    {
        "name": "backend",
        "version": "1.0.0",
        "main": "index.ts",
        "license": "MIT",
        "devDependencies": {
            "nodemon": "^2.0.22",
            "sucrase": "^3.32.0",
            "ts-node": "^10.9.1"
        }
    },
    "dependencies": {
        "typescript": "^5.0.4"
    }
    ```

    - Abaixo de `"licence": "MIT",`, acima das dependências de desenvolvimento `"devDepencencies": {...}`, adicione as seguintes linhas:

        ```json
        "scripts": {
            "start": "nodemon --watch \"src/**\" --ext \"ts,json\" --exec \"ts-node ./src/index.ts\""
        },
        ```

        Deverá ficar da seguinte forma:

        ```json
        {
            "name": "backend",
            "version": "1.0.0",
            "main": "index.ts",
            "license": "MIT",
            "scripts": {
                "start": "nodemon --watch \"src/**\" --ext \"ts,json\" --exec \"ts-node ./src/index.ts\""
            },
            "devDependencies": {
                "nodemon": "^2.0.22",
                "sucrase": "^3.32.0",
                "ts-node": "^10.9.1"
            }
        },
        "dependencies": {
            "typescript": "^5.0.4"
        }
        ```

        Analisando essa linha no arquivo `package.json`:

        ```json
        "scripts": {
            "start": "nodemon --watch \"src/**\" --ext \"ts,json\" --exec \"ts-node ./src/index.ts\""
        }
        ```

        Esta linha define um script que pode ser executado com o comando `npm run script`.

        Agora, vamos entender o que cada parte do script faz:

        - **nodemon**: É uma ferramenta que reinicia automaticamente a aplicação Node.js quando detecta alterações nos arquivos.

        - **--watch \"src/**\"**: Esta opção configura o nodemon para observar alterações em todos os arquivos na pasta `src` e suas subpastas.

        - **--ext \"ts,json\"**: Esta opção diz ao nodemon para observar alterações em arquivos com as extensões `.ts` e `.json`.

        - **--exec \"ts-node ./src/server.ts\"**: Esta opção diz ao nodemon para executar o comando `ts-node ./src/server.ts` sempre que um arquivo é alterado. O `ts-node` é uma ferramenta que permite executar TypeScript diretamente, sem a necessidade de compilar os arquivos para JavaScript primeiro. `./src/server.ts` é o arquivo de entrada do seu aplicativo.

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

