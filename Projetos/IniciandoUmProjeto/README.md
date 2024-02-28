> ## Iniciando um projeto
>
> ![Docker](./images/StartingAProject.png)

> ### *Summary*

> - [Configuração inicial](#configuração-inicial)
> - [Criando banco de dados](#criando-banco-de-dados)
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

    ```bash
    /myProject/
    ├─ /src/
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
            "start": "nodemon --watch \"src/**\" --ext \"ts,json\" --exec \"ts-node ./src/index.ts\"",
            "build": "tsc"
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
                "start": "nodemon --watch \"src/**\" --ext \"ts,json\" --exec \"ts-node ./src/index.ts\"",
                "build": "tsc"
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

        A linha `"scripts": {...}` define um script que pode ser executado com o comando `npm run script`. A linha `"build": "tsc"` cria o arquivo de build.

        Agora, vamos entender o que cada parte do script faz:

        - **nodemon**: É uma ferramenta que reinicia automaticamente a aplicação Node.js quando detecta alterações nos arquivos.

        - **--watch \"src/**\"**: Esta opção configura o nodemon para observar alterações em todos os arquivos na pasta `src` e suas subpastas.

        - **--ext \"ts,json\"**: Esta opção diz ao nodemon para observar alterações em arquivos com as extensões `.ts` e `.json`.

        - **--exec \"ts-node ./src/server.ts\"**: Esta opção diz ao nodemon para executar o comando `ts-node ./src/server.ts` sempre que um arquivo é alterado. O `ts-node` é uma ferramenta que permite executar TypeScript diretamente, sem a necessidade de compilar os arquivos para JavaScript primeiro. `./src/server.ts` é o arquivo de entrada do seu aplicativo.

9. Instale as dependências que serão necessárias para o projeto:

    Instale os pacotes "express", "cors" e "dotenv" usando o NPM com o seguinte comando:

    ```bash
    npm install express cors dotenv
    ```

    Este comando instalará os pacotes como dependências do seu projeto. Agora você pode usar "express", "cors" e "dotenv" em seu projeto Node.js.

    Vamos entender o que cada pacote faz:

    - **Express**: É um framework para aplicativo de rede de aplicativos Node.js mínimo e flexível que fornece um conjunto robusto de recursos para aplicativos web e móvel.

    - **CORS (Cross-Origin Resource Sharing)**: É um pacote node.js para fornecer um middleware Connect/Express que pode ser usado para habilitar o CORS com várias opções.

    - **Dotenv**: É um módulo de dependência zero que carrega variáveis de ambiente de um arquivo `.env` para `process.env`. Manter o controle das configurações do seu aplicativo pode ser confuso. Dotenv gerencia tudo isso para você.

    Esses pacotes são comumente usados em muitos projetos Node.js para criar aplicações web robustas e seguras.

10. Instale as tipagens do TypeScript e o CORS:

    ```bash
    npm i --save-dev @types/express
    ```

    ```bash
    npm install --save-dev @types/cors
    ```

11. Acesse o arquivo `index.ts` e importe Express, o CORS:

    ```ts
    import express from 'express';
    import cors from 'cors';
    import dotenv from 'dotenv';
    ```

12. No mesmo arquivo `index.ts`, configure o Dotenv dando continuidade na escrita no código:

    ```ts
    dotenv.config();

    const app = express();

    app.use(cors());
    app.use(express.json());

    app.listen(3000, () => {
        console.log("Servidor rodando na porta 3000!");
    })
    ```

13. Start o servidor com o seguinte comando:

    ```bash
    npm start
    ```

    No console do seu terminal, será exibidas as informações indicando que o servidor está rodando na porta configurada.

    ```bash
    root@10:/home/userlinux/Documentos/Projects/myProject/api# npm start

    > api@1.0.0 start
    > nodemon --watch "src/**" --ext "ts,json" --exec "ts-node ./src/index.ts"

    [nodemon] 2.0.22
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching path(s): src/**
    [nodemon] watching extensions: ts,json
    [nodemon] starting `ts-node ./src/index.ts`
    Servidor rodando na porta 3000!
    ```

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Criando banco de dados

Vamos configurar um banco de dados.

1. Se você não tiver o **Docker** instalado em sua máquina, utilise as instruções seguintes para instalá-lo em algumas das distribuições Linux mais comuns:

    **Ubuntu:**

    ```bash
    # Atualize sua lista de pacotes
    sudo apt update

    # Instale alguns pacotes pré-requisitos
    sudo apt install apt-transport-https ca-certificates curl software-properties-common

    # Adicione a chave GPG para o repositório oficial do Docker
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    # Adicione o repositório do Docker às fontes do APT
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

    # Atualize o banco de dados do pacote com os pacotes do Docker do recém adicionado repositório
    sudo apt update

    # Instale o Docker
    sudo apt install docker-ce
    ```

    **Debian:**

    ```bash
    # Atualize sua lista de pacotes
    sudo apt-get update

    # Instale alguns pacotes pré-requisitos
    sudo apt-get install apt-transport-https ca-certificates curl gnupg2 software-properties-common

    # Adicione a chave GPG para o repositório oficial do Docker
    curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -

    # Adicione o repositório do Docker às fontes do APT
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

    # Atualize o banco de dados do pacote com os pacotes do Docker do recém adicionado repositório
    sudo apt-get update

    # Instale o Docker
    sudo apt-get install docker-ce
    ```

    Por favor, note que você pode precisar de privilégios de superusuário para executar esses comandos. Além disso, essas instruções assumem que você está usando a arquitetura amd64, que é comum na maioria dos sistemas modernos. Se você estiver usando uma arquitetura diferente, substitua "amd64" pela sua arquitetura no comando que adiciona o repositório do Docker.

    Você pode verificar se o Docker está instalado no seu sistema Linux usando o seguinte comando no terminal:

    ```bash
    docker --version
    ```

    Se o Docker estiver instalado, este comando retornará a versão do Docker. Se não estiver instalado, você receberá uma mensagem de erro indicando que o comando 'docker' não foi encontrado. Lembre-se de que você pode precisar de permissões de superusuário (sudo) para executar comandos do Docker, dependendo de como o Docker foi instalado no seu sistema.

2. Crie um arquivo chamado "`docker-compose.yml`" na raiz do seu projeto:

    **File: `docker-compose.yml`**

    Sua estrutura de arquivos ficará assim:

    ```bash
    /myProject/
    ├─ /src/
    │  └─ index.ts
    ├─ docker-compose.yml
    └─ package.json
    ```

    Crie uma imagem Docker dentro do arquivo:

    ```yaml
    version: "3"

    services:
        pgsql-db:
            image: postgres
            ports:
                - "5432:5432"
            container_name: "pgsql-db"
            restart: always
            volumes:
                - ./data-pgsql-db:/var/lib/postgresql/data
            environment:
                POSTGRES_USER: pguser
                POSTGRES_PASSWORD: pgpassword

    volumes:
        data-pgsql-db:
    ```

    **Explicando cada seção do arquivo `docker-compose.yml`:**

    ```yaml
    version: "3"
    ```
    Esta linha especifica a versão do formato do arquivo `docker-compose.yml`. A versão "3" é uma das mais recentes e suporta a maioria das opções de configuração.

    ```yaml
    services:
    ```
    Aqui começamos a definir os serviços, que são os contêineres que queremos executar.

    ```yaml
        pgsql-db:
    ```
    Este é o nome do serviço, neste caso, `pgsql-db`. Este nome será usado como prefixo para criar contêineres.

    ```yaml
            image: postgres
    ```
    Esta linha especifica a imagem Docker a ser usada para criar o contêiner. Neste caso, estamos usando a imagem oficial do PostgreSQL.

    ```yaml
            ports:
                - "5432:5432"
    ```
    Aqui estamos mapeando a porta 5432 do contêiner para a porta 5432 do host. Isso significa que o serviço PostgreSQL no contêiner estará disponível na porta 5432 do host.

    ```yaml
            container_name: "pgsql-db"
    ```
    Esta linha define o nome do contêiner. Se não for especificado, o Docker gerará um nome automaticamente.

    ```yaml
            restart: always
    ```
    Esta opção define a política de reinicialização do contêiner. No caso de `always`, o contêiner será reiniciado sempre que parar. Se parar manualmente, ele só será reiniciado quando o contêiner for manualmente reiniciado ou o Docker for reiniciado.

    ```yaml
            volumes:
                - ./data-pgsql-db:/var/lib/postgresql/data
    ```
    Aqui estamos montando um volume. Isso mapeia o diretório `./data-pgsql-db` do host para o diretório `/var/lib/postgresql/data` no contêiner. Isso é útil para persistência de dados.

    ```yaml
            environment:
                POSTGRES_USER: pguser
                POSTGRES_PASSWORD: pgpassword
    ```
    Aqui estamos definindo variáveis de ambiente que serão usadas pela imagem do PostgreSQL. Estas são usadas para criar um novo usuário `pguser` com a senha `pgpassword`.

    ```yaml
    volumes:
        data-pgsql-db:
    ```
    Finalmente, estamos definindo um volume chamado `data-pgsql-db`. Este volume pode ser usado por qualquer serviço na composição. Neste caso, está sendo usado pelo serviço `pgsql-db`.

    Após digitar o conteúdo da imagem, execute o seguinte comando no terminal:

    ```bash
    sudo docker-compose up -d
    ```

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

