> ## Iniciando um projeto
>
> ![Docker](./images/StartingAProject.png)

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Configuração inicial](#configuração-inicial "Configuração inicial")
> - [Criando banco de dados](#criando-banco-de-dados "Criando banco de dados")
>   - [Docker e Docker Compose](#docker-e-docker-compose "Docker e Docker Compose")
>   - [ORM Prisma](#orm-prisma "ORM Prisma")
>   - [Repository de usuários (CRUD)](#repository-de-usu%C3%A1rios-crud "Repository de usuários (CRUD)")
>   - [Controller de usuário](#controller-de-usu%C3%A1rio "Controller de usuário")
>   - [Ajustando retornos](#ajustando-retornos)
> - [Configuração do TypeScript](#configuração-do-typescript "Configuração do TypeScript")

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

### Docker e Docker Compose

**Docker** é uma plataforma de código aberto que permite aos desenvolvedores automatizar o processo de implantação, escalabilidade e execução de aplicativos dentro de contêineres. Um contêiner Docker é uma unidade padrão de software que empacota o código e todas as suas dependências para que o aplicativo seja executado de maneira rápida e confiável de um ambiente de computação para outro.

Um **Dockerfile** é um documento de texto que contém todos os comandos/instruções que um usuário poderia chamar na linha de comando para montar uma imagem. A imagem Docker é um conjunto de recursos responsável pela execução de um código ou uma aplicação.

Aqui está um exemplo de um Dockerfile:

```dockerfile
FROM elixir:1.10
```

Neste exemplo, estamos criando uma imagem Docker que é capaz de interpretar a linguagem Elixir.

**Docker Compose**, por outro lado, é uma ferramenta para definir e executar aplicativos Docker de vários contêineres. Com o Docker Compose, você usa um arquivo YAML para configurar os serviços do seu aplicativo. Ele permite que você gerencie múltiplos contêineres como um único serviço.

Aqui está um exemplo de um arquivo Docker Compose:

```yaml
version: '3'
services:
  web:
    build: .
    ports:
     - "5000:5000"
  redis:
    image: "redis:alpine"
```

Neste exemplo, estamos definindo dois serviços, `web` e `redis`. O serviço `web` é construído usando o Dockerfile no diretório atual e mapeia a porta 5000 do contêiner para a porta 5000 do host. O serviço `redis` usa a imagem `redis:alpine`.

Portanto, Docker e Docker Compose são ferramentas complementares usadas para isolar, implantar e gerenciar aplicativos dentro de contêineres.

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

    Sua estrutura de arquivos ficará assim:

    > Estrutura de arquivos!

    ```bash
    /myProject/
    ├─ /src/
    │  └─ index.ts
    ├─ docker-compose.yml ">>> New file <<<"
    └─ package.json
    ```

    Crie uma imagem Docker dentro do arquivo:

    **File: `./docker-compose.yml`**

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

    Explicando o comando acima:

    - `sudo`: Este comando é usado para executar o comando seguinte com privilégios de superusuário (root). Isso é necessário porque algumas operações do Docker requerem esses privilégios.

    - `docker-compose up`: Este comando é usado para iniciar todos os serviços definidos em um arquivo `docker-compose.yml` na mesma pasta. Ele cria e inicia contêineres para cada serviço.

    - `-d`: Esta opção, também conhecida como "detached mode", faz com que os contêineres sejam executados em segundo plano. Sem essa opção, os logs dos contêineres seriam enviados para o terminal atual.

    Para visualizar a imagem criada, você pode usar o comando `docker images`. Este comando lista todas as imagens Docker disponíveis no seu sistema. Aqui está o comando:

    ```bash
    docker images
    ```

    Você verá uma lista de imagens com informações como o repositório, a tag, o ID da imagem, quando foi criada e o tamanho. A imagem do PostgreSQL que você usou no seu arquivo `docker-compose.yml` deve aparecer nesta lista. Lembre-se de que você pode precisar de permissões de superusuário (sudo) para executar comandos do Docker, dependendo de como o Docker foi instalado no seu sistema. Se você usou uma tag específica para a imagem do PostgreSQL no seu arquivo `docker-compose.yml`, você também verá essa tag na lista. Se nenhuma tag foi especificada, a tag padrão é `latest`.

    Você verá algo parecido com isto:

    ```bash
    root@10:/home/userlinux/Documentos/Projects/myProject/api# docker images
    REPOSITORY   TAG           IMAGE ID       CREATED         SIZE
    postgres     latest        eb634efa7ee4   7 days ago      431MB
    mysql        8             a88c3e85e887   5 weeks ago     632MB
    node         20-buster     5d384b4f9436   7 months ago    969MB
    node         20.5-buster   5d384b4f9436   7 months ago    969MB
    node         buster        5d384b4f9436   7 months ago    969MB
    mysql        8.0.30        dbaea59d1b41   16 months ago   449MB
    root@10:/home/userlinux/Documentos/Projects/myProject/api#
    ```

    Outro comando utilizado para visualizar as imagens:

    Explicando o comando abaixo:

    ```bash
    sudo docker ps
    ```

    - `sudo`: Este comando é usado para executar o comando seguinte com privilégios de superusuário (root). Isso é necessário porque algumas operações do Docker requerem esses privilégios.

    - `docker ps`: Este comando é usado para listar todos os contêineres Docker que estão atualmente em execução no seu sistema.

    A saída deste comando inclui várias colunas:

    - `CONTAINER ID`: Um identificador único para o contêiner.
    - `IMAGE`: A imagem Docker usada para criar o contêiner.
    - `COMMAND`: O comando que foi iniciado no contêiner.
    - `CREATED`: Quando o contêiner foi criado.
    - `STATUS`: O status atual do contêiner.
    - `PORTS`: As portas que estão expostas pelo contêiner.
    - `NAMES`: O nome do contêiner.

    Se você quiser ver todos os contêineres no seu sistema, não apenas os que estão em execução, você pode usar o comando `docker ps -a`. A opção `-a` significa "all" (todos). Lembre-se de que você pode precisar de permissões de superusuário (sudo) para executar comandos do Docker, dependendo de como o Docker foi instalado no seu sistema.

    Você verá algo parecido com isto:

    ```bash
    root@10:/home/userlinux/Documentos/Projects/myProject/api# docker ps
    CONTAINER ID   IMAGE      COMMAND                  CREATED      STATUS        PORTS                                       NAMES
    d1096018f728   postgres   "docker-entrypoint.s…"   2 days ago   Up 15 hours   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   pgsql-db
    root@10:/home/userlinux/Documentos/Projects/myProject/api#
    ```

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### ORM Prisma

3. Configure o ORM Prisma:

    Prisma ORM é um mapeador objeto-relacional (ORM) de código aberto e de próxima geração. Ele consiste nas seguintes partes:

    - **Prisma Client**: Um construtor de consultas autogerado e com tipagem segura para Node.js e TypeScript.
    - **Prisma Migrate**: Sistema de migração.
    - **Prisma Studio**: Interface gráfica para visualizar e editar dados no seu banco de dados.

    Cada projeto que usa uma ferramenta do conjunto de ferramentas Prisma ORM começa com um arquivo de esquema Prisma. O esquema Prisma permite que os desenvolvedores definam seus modelos de aplicação em uma linguagem intuitiva de modelagem de dados.

    Aqui está um exemplo de definição de modelo com tipos de dados:

    ```prisma
    model User {
    id     Int @id @default(autoincrement())
    name  String
    email String   @unique
    age    Int?
    createdAt DateTime  @default(now())
    role  Role     @default(USER)
    }

    enum  Role {
    USER
    ADMIN
    }
    ```

    No exemplo acima, temos uma entidade "User" com várias colunas, como "id" (inteiro), "name" (string), "email" (string único), "age" (inteiro opcional), "createdAt" (data e hora com valor padrão de agora) e "role" (enum com valores USER e ADMIN).

    Depois que o modelo de dados é definido, você pode gerar o Prisma Client, que expõe consultas CRUD e mais para os modelos definidos. Se você estiver usando TypeScript, obterá total segurança de tipo para todas as consultas (mesmo ao recuperar apenas os subconjuntos dos campos de um modelo).

    > Docs: [https://www.prisma.io/](https://www.prisma.io/ "Acessar a documentação do Prisma")

    ---

    Para instalar o Prisma via NPM, você pode usar o seguinte comando:

    ```bash
    npm install prisma @prisma/client
    ```

    Este comando instala o pacote `prisma` que contém o CLI do Prisma e o pacote `@prisma/client` que é o cliente do Prisma.

    Depois de instalar o Prisma, você pode gerar o cliente Prisma usando o seguinte comando:

    ```bash
    npx prisma generate
    ```

    Este comando lê o arquivo de esquema Prisma e gera o cliente Prisma. Agora você pode importar o cliente Prisma em seu código para acessar seu banco de dados. Por exemplo:

    ```javascript
    const { PrismaClient } = require('@prisma/client')

    const prisma = new PrismaClient()

    async function main() {
    const allUsers = await prisma.user.findMany()
    console.log(allUsers)
    }

    main()
    .catch(e => {
        throw e
    })
    .finally(async () => {
        await prisma.$disconnect()
    })
    ```

    Neste exemplo, estamos importando o `PrismaClient` do pacote `@prisma/client` e usando-o para buscar todos os usuários do banco de dados.

    > Toda vez que precisa se comunicar com o banco de dados, o Prisma precisa ser instanciado.
    >
    > Para não ser preciso fazer isso toda vez, faça o seguinte procedimento:

    - No diretório "`./src/services/`", crie um um arquivo com o nome "`prisma.ts`" para importar o Prisma/Cliente. Segue o código abaixo:

        > Estrutura de arquivos!

        ```bash
        /myProject/
        ├─ /src/
        │  ├─ /services/
        │  │  └─ prisma.ts    ">>> New file <<<"
        │  └─ index.ts
        ├─ docker-compose.yml
        └─ package.json
        ```

        **File: `./src/services/prisma.ts`**
        ```ts
        import { PrismaClient } from '@prisma/client';

        export const prisma = new PrismaClient();s
        ```

    - Digite no **terminal** o seguinte comando "`npx prisma init`":

        ```bash
        npx prisma init
        ```

        O comando `npx prisma init` é usado para inicializar um novo projeto Prisma. Ele cria um diretório chamado `prisma` no diretório atual do seu projeto. Dentro deste diretório, ele gera um arquivo chamado `schema.prisma`, que é um esqueleto do esquema do banco de dados.

        O arquivo `schema.prisma` é onde você define seus modelos de aplicação e configura seu banco de dados. Aqui está um exemplo de como pode ser o conteúdo inicial do arquivo `schema.prisma`:

        ```prisma
        datasource client {
            provider = "prisma-client-js"
        }

        generator db {
            provider = "postgresql"
            url      = env("DATABASE_URL")
        }
        ```

        Neste exemplo, estamos configurando uma fonte de dados (datasource) para usar o PostgreSQL e estamos configurando o gerador (generator) para gerar o Prisma Client em JavaScript.

        Depois de configurar o `schema.prisma`, você pode executar `npx prisma generate` para gerar o Prisma Client. O Prisma Client é um construtor de consultas autogerado e com tipagem segura para Node.js e TypeScript.

        Após a execução do comando "`npx prisma init`", o Prisma criou outro arquivo "`.env`" contendo o seguinte conteúdo:

        ```tex
        # Environment variables declared in this file are automatically made available to Prisma.
        # See the documentation for more detail: https://pris.ly/d/prisma-schema#accessing-environment-variables-from-the-schema

        # Prisma supports the native connection string format for PostgreSQL, MySQL, SQLite, SQL Server, MongoDB and CockroachDB.
        # See the documentation for all the connection string options: https://pris.ly/d/connection-strings

        DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"
        ```

        > Estrutura de arquivos!

        ```bash
        /myProject/
        ├─ /prisma/                    ">>> New folder <<<"
        │  ├─ /migrations/             ">>> New folder <<<"
        │  │  ├─ /20230522172022_init/ ">>> New folder <<<"
        │  │  │  └─ migration.sql      ">>> New file <<<"
        │  │  └─ migration_lock.toml   ">>> New file <<<"
        │  └─ schema.prisma            ">>> New file <<<"
        ├─ /src/
        │  ├─ /services/
        │  │  └─ prisma.ts
        │  └─ index.ts
        ├─ .env                        ">>> New file <<<"
        ├─ docker-compose.yml
        └─ package.json
        ```

        Configure os dados de acesso ao banco de dados, aqueles acessos que foram criados no arquivo "`docker-compose.yml`". Veja a variável `DATABASE_URL` abaixo:

        ```tex
        DATABASE_URL="postgresql://pguser:pgpassword@localhost:5432/dbsystem?schema=public"
        ```

    - Crie a tabela de dados do banco de dados, segue o código abaixo:

        ```prisma
        datasource client {
            provider = "prisma-client-js"
        }

        generator db {
            provider = "postgresql"
            url      = env("DATABASE_URL")
        }

        model User {
            id       Int     @id @default(autoincrement())
            name     String
            email    String
            password String
            phone    String
            address  String
            number   String
            city     String
            state    String
            cep      String
            status   Boolean @default(true)
            deleted  Boolean @default(false)
        }
        ```

    - Execute o seguinte comando para criar o banco de dados:

        ```bash
        npx prisma migrate dev --name init
        ```

        Agora, vamos entender o que esse comando faz:

        - `prisma migrate dev`: Este comando é parte do Prisma Migrate, que é uma ferramenta de migração de banco de dados declarativa. O comando `migrate dev` é usado durante o desenvolvimento e aplica as migrações de banco de dados no ambiente de desenvolvimento. Ele também gera e aplica uma nova migração se houver alterações no Prisma Schema.

        - `--name init`: A opção `--name` permite que você dê um nome personalizado para a migração. Neste caso, a migração é chamada de `init`.

        Portanto, o comando `npx prisma migrate dev --name init` irá gerar uma nova migração chamada `init` se houver alterações no Prisma Schema, e então aplicará essa migração no banco de dados de desenvolvimento. Se não houver alterações no Prisma Schema, ele simplesmente aplicará as migrações existentes.

        > Após digitar o comando, é criado um diretório com o nome `migrations`, dentro, está uma migration .sql.

        ![Migrations](./images/migrations.png)

        > Ele converteu a tabela que foi escrita para uma linguagem SQL.

        ![Migrations.SQL](./images/migrationSql.png)

    **Obs.:** Não esqueça de estar com o Docker rodando, se o Docker parar, o banco de dados não vai rodar!

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Repository de usuários (CRUD)

CRUD é um acrônimo que significa: **Create** (Criar), **Read** (Ler), **Update** (Atualizar) e **Delete** (Excluir). Essas são as quatro operações básicas que você pode realizar em qualquer banco de dados persistente.

No ORM Prisma, você pode realizar operações CRUD com a API do Prisma Client gerada. Aqui estão alguns exemplos de como você pode fazer isso:

- **Create (Criar)**: Você pode criar um único registro. Por exemplo, o seguinte código cria um único usuário com dois campos:

```javascript
const user = await prisma.user.create({
  data: {
    email: 'elsa@prisma.io',
    name: 'Elsa Prisma',
  },
})
```

- **Read (Ler)**: Você pode ler os registros de várias maneiras. Por exemplo, o seguinte código lê todos os usuários:

```javascript
const allUsers = await prisma.user.findMany()
```

- **Update (Atualizar)**: Você pode atualizar um registro existente. Por exemplo, o seguinte código atualiza um usuário existente:

```javascript
const updateUser = await prisma.user.update({
  where: { id: 1 },
  data: { email: 'elsa.updated@prisma.io' },
})
```

- **Delete (Excluir)**: Você pode excluir um registro existente. Por exemplo, o seguinte código exclui um usuário:

```javascript
const deleteUser = await prisma.user.delete({
  where: { id: 1 },
})
```

Esses são exemplos básicos. O Prisma Client oferece muitas outras opções para realizar operações CRUD.

**Vamos começar criando um arquivo, veja nossa estrutura abaixo e o novo arquivo:**

Crie o seguinte arquivo "`./src/repositories/user.repository.ts`":

> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /repositories/        ">>> New folder <<<"
│  │  └─ user.repository.ts ">>> New file <<<"
│  ├─ /services/
│  │  └─ prisma.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

Para seguirmos com nosso exemplo, iremos alterar nossa tabela no arquivo `./prisma/schema.prisma` de usuários, veja a alteração abaixo:

```prisma
model User {
    id       Int     @id @default(autoincrement())
    name     String
    email    String
    password String
    phone    String?
    address  String?
    number   String?
    city     String?
    state    String?
    cep      String?
    masterId Int?
    status   Boolean @default(true)
    deleted  Boolean @default(false)
}
```

Na tabela acima, o ponto de interrogação (?) após o tipo de campo indica que o campo é **opcional**. Isso significa que quando um novo registro é criado na tabela `User`, esses campos podem ser deixados em branco. Em outras palavras, não é necessário fornecer um valor para esses campos ao criar um novo `User`.

Quanto à coluna `masterId`, foi adicionada para definir a quem pertence. Ela serve para identificar a qual usuário mestre um determinado registro pertence. Isso é útil em cenários onde você tem uma relação de "muitos para um" entre registros e usuários mestres. Por exemplo, se vários registros na tabela `User` pertencem a um único usuário mestre, você pode usar o `masterId` para rastrear isso. Se `masterId` for opcional (como indicado pelo `?`), isso significa que nem todos os usuários precisam pertencer a um usuário mestre. Alguns registros `User` podem não ter um `masterId`.

Após essa alteração, é preciso dizer ao Prisma que houve alterações e ele tem que atualizar no banco de dados, segue o comando novamente:

```bash
npx prisma migrate dev --name init
```

> O Prisma vai lá no banco, verifica se houve alterações e atualiza.
>
> ![Docker](./images/migrateionSql_exc2.png)
>
> Após executado o comando `npx prisma migrate dev --name init`, o arquivo `.sql` foi criado novamente.

No arquivo "`user.repository.ts`" criado e mostrado anteriormente na estrutura de arquivos, deve-se importar o Prisma e exportar a variável `createrUser`, veja o código:

```ts
import { prisma } from '../services/prisma';

// Criar registro.
export const createrUser = async (data: any) => {
    const user = await prisma.user.create({
        data
    });
    return user;
};
```

Crie um diretório chamado "`./src/entities/`" e o arquivo "`user.ts`":



> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /entities/               ">>> New folder <<<"
│  │  └─ user.ts               ">>> New file <<<"
│  ├─ /repositories/
│  │  └─ user.repository.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

**File: `./src/entities/user.ts`**

```ts
export type User = {
    name:      string;
    email:     string;
    password:  string;
    phone?:    string | null;
    address?:  string | null;
    number?:   string | null;
    city?:     string | null;
    state?:    string | null;
    cep?:      string | null;
    masterId?: number | null;
}
```

Dentro do "`user.repository.ts`", deve ser importado o user.ts:

**File: `./repositories/user.prepository.ts`**

```ts
import { prisma } from "../services/prisma";
import { User } from "../entities/user";

// Criar registro.
export const createrUser = async (data: any) => {
    const user = await prisma.user.create({
        data
    });
    return user;
};

// Listar todos os registros.
export const getAll = async (masterId: number) => {
    const users = await prisma.user.findMany({
        where: {
            deleted: false,
            masterId
        },
    });
    return users;
}

// Listar um registro a partir do ID (registro único).
export const getById = async (id: number) => {
    const user = await prisma.user.findUnique({
        where: {
            id
        }
    });
    return user
}

// Atualizar registro a partir de um ID.
export const updateUser = async (id: number, data: any) => {
    const user = await prisma.user.update({
        where: {
            id
        },
        data
    });
    return user
}

// Deletar registro a partir de um ID.
export const deleteUser = async (id: number) => {
    const user = await prisma.user.update({
        where: {
            id
        },
        data: {
            deleted: true,
        },
    });
    return;
}
```

> Obs.: Na variável "user", para apagar o registro utilize "`delete({...})`" ao invés de "`update({...})`". O exemplo acima, é uma exclusão lógica apenas, isso quer dizer que a coluna "`deleted`" do usuário será apenas atualizada para "`true`".

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Controller de usuário

Crie o arquivo "`./src/controlers/user.controller.ts`", veja a estrutura de arquivos seguinte:

> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /controllers/            ">>> New folder <<<"
│  │  └─ user.controller.ts    ">>> New file <<<"
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /repositories/
│  │  └─ user.repository.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

Vamos importar o "Express" e seguir com o código no arquivo "`./user/controllers/user.controller.ts`".

**File: `./user/controllers/user.controller.ts`**

```jsx
import { Request, Response } from 'express';
import { userValidation } from '../validation/user.validation';
import bcrypt from 'bcrypt';
import {
    createrUser,
    deleteUser,
    getAll,
    getById,
    updateUser
} from '../repositories/user.repository';

// Criar registro.
export const create = async (req: Request, res: Response) => {
    try {
        req.body.password = await bcrypt.hash(req.body.password, 10);
        const data = await userValidation.parse(req.body);
        const user = await createrUser(data);
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
};

// Listar todos os registros.
export const get = async (req: Request, res: Response) => {
    try {
        const masterId = 1;
        const user = await getAll(masterId);
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
}

// Listar um registro a partir do ID (registro único).
export const getId = async (req: Request, res: Response) => {
    try {
        cosnt user = await getById(Number(req.params.id));
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
}

// Atualizar registro a partir de um ID.
export const update = async (req: Request, res: Response) => {
    try {
        const user = await updateUser(Number(req.params.id), req.body);
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
}

// Deletar registro a partir de um ID.
export const remove = async (req: Request, res: Response) => {
    try {
        await deleteUser(Number(req.params.id));
        return res.status(204).send();
    } catch (e) {
        return res.status(400).send(e);
    }
}
```

Utiliza a biblioteca "Bcrypt" para criptografar as senhas, utilize o comando seguinte:

```bash
npm install bcrypt @types/bcrypt
```

Crie um arquivo para retornar o erros, as validações. Veja a estrutura com o arquivo "`./src/validations/user.validation.ts`":

> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /controllers/
│  │  └─ user.controller.ts
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /repositories/
│  │  └─ user.repository.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  ├─ /validations/            ">>> New folder <<<"
│  │  └─ user.validation.ts    ">>> New file <<<"
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

Use uma biblioteca chamada "Zod", use o comando "``":

O comando NPM para instalar o Zod é:

```bash
npm install zod
```

Este comando instalará o pacote Zod no seu projeto. Lembre-se de executar este comando no diretório do seu projeto onde o arquivo `package.json` está localizado.

Importe no arquivo "`./src/validations/user.validation.ts`", segue o código abaixo:

**File: `./src/validations/user.validation.ts`**

```jsx
import { z } from 'zod';

export const userValidation = z.object({
    name:      z.string(),
    email:     z.string().email(),
    password:  z.string().min(6),
    phone:     z.string().nullable().optional(),
    address:   z.string().nullable().optional(),
    number:    z.string().nullable().optional(),
    city:      z.string().nullable().optional(),
    state:     z.string().nullable().optional(),
    cep:       z.string().nullable().optional(),
    masterId:  z.number().nullable().optional()
})
```

Crie o arquivo "`./src/routes/user.routes.ts`" para definir as rotas, segue abaixo a estrutura de arquivos com o novo arquivo e o conteúdo:

> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /controllers/
│  │  └─ user.controller.ts
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /repositories/
│  │  └─ user.repository.ts
│  ├─ /routes/                 ">>> New folder <<<"
│  │  └─ user.routes.ts        ">>> New file <<<"
│  ├─ /services/
│  │  └─ prisma.ts
│  ├─ /validations/
│  │  └─ user.validation.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

**File: `./src/routes/user.routes.ts`**

```jsx
import {
    create,
    get,
    getId,
    remove,
    update
} from '../controllers/user.controller';

// Rotas.
export const userRoutes = (app: any) => {
    app.post('/v1/user', create);
    app.get('/v1/user', get);
    app.get('/v1/user/:id', getId);
    app.put('/v1/user/:id', update);
    app.delete('/v1/user/:id', remove)
}
```

Dentro do diretório "`./src/routes/`", crie o arquivo "`index.ts`":

> Estrutura de arquivos!

```bash
/myProject/
├─ /prisma/
│  ├─ /migrations/
│  │  ├─ /20230522172022_init/
│  │  │  └─ migration.sql
│  │  └─ migration_lock.toml
│  └─ schema.prisma
├─ /src/
│  ├─ /controllers/
│  │  └─ user.controller.ts
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /repositories/
│  │  └─ user.repository.ts
│  ├─ /routes/
│  │  ├─ index.ts              ">>> New file <<<"
│  │  └─ user.routes.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  ├─ /validations/
│  │  └─ user.validation.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

As rotas devem ser importadas dentro do arquivo "`./src/routes/index.ts`":

**File: `./src/routes/index.ts`**

```ts
import { userRoutes } from './user.routes';

const routes = (app: any) => {
    userRoutes(app);
}

export default routes;
```

E dentro do "`./src/index.ts`" do diretório raiz, importe as rotas junto com as importações de "express, cors e dotenv" e passe o app para dentro:

**File: `./src/index.ts`**

```ts
import express from "express";
import cors from "cors";
import dotenv from "dotenv";
import routes from './routes';

dotenv.config();

const app = express();

app.use(cors());
app.use(express.json());

routes(app);

app.listen(3000, () => {
    console.log("Servidor rodando na porta 3000!");
})
```

Execute o comando "`npm start`" e veja se está rodando:

```bas
npm start
```

Para testar as rotas, utilize a extenção "`Thunder Client`" no VSCode ou o "`Insomnia`", use o de sua preferência, mas aqui o exemplo é com a extenção "Thunder Client":

![Thunder Client](./images/thunder_client.png)

Use as configurações seguintes para testar:

> Teste na requisição "`http://localhost:3000/v1/user`" usando o "`POST`":

![Testando a requisição 'user'](./images/localhost_3000_v1_user.png)

Nesse teste, ele apresenta um erro, uma exigência, isso era o erro esperado. A validação exige um email e uma senha. Para fazer novamente o teste e passar por este erro, informe o email e a senha:

![Testando novamente a requisição 'user' com o POST](./images/localhost_3000_v1_user_test_2.png)

Teste com a rota "user" passando o ID na requisição "GET":

> Teste na requisição "`http://localhost:3000/v1/user/1`" usando o "`GET`" onde a mesma passa um "ID":

![Testando novamente a requisição 'user' com o GET](./images/localhost_3000_v1_user_test_3_passing_id.png)

Teste com a rota "user" passando o ID na requisição "PUT":

> Teste na requisição "`http://localhost:3000/v1/user/1`" usando o "`PUT`" onde a mesma passa um "ID":

![Testando novamente a requisição 'user' com o PUT](./images/localhost_3000_v1_user_test_4_passing_id.png)

Teste com a rota "user" passando o ID na requisição "DELETE":

> Teste na requisição "`http://localhost:3000/v1/user/1`" usando o "`DELETE`" onde a mesma passa um "ID":

![Testando novamente a requisição 'user' com o PUT](./images/localhost_3000_v1_user_test_5_passing_id.png)

> ( i ) Observe que o registro foi apagado! Não haverá returno, o registro apenas foi apagado.

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Ajustando retornos

Ao criar um registro de um usuário, junto com todos os dados do registro, a senha está sendo retornada e isso não é uma boa ideia. Vamos ajustar para retornar apenas o ID, o que é necessário para o Frontend.

No arquivo "`./src/repositories/user.repository.ts`" faça a seguinte alteração, veja o trecho do código no "`user.repository.ts`":

**File: `./repositories/user.prepository.ts`**

```ts
// ...

// Criar registro.
export const createrUser = async (data: any) => {
    const user = await prisma.user.create({
        data,
        select: {
            id: true
        }
    });
    return user;
};

//  ...
```

Retorna somente o ID, deixando de apresentar todos os dados do registro:

![Ajustando o retorno da crição de registro obtendo apenas o ID](./images/Adjusting_returns_by_bringing_in_the_ID.png)

Ajuste o "`getById`", quando o registro for requisitado a partir de um ID:

```ts
// ...

// Listar um registro a partir do ID (registro único).
export const getById = async (id: number) => {
    const user = await prisma.user.findUnique({
        where: {
            id
        },
        select: {
            id: true,
            name: true,
            email: true,
            password: false,
            phone: true,
            address: true,
            number: true,
            cep: true,
            city: true,
            masterId: true
        }
    });
    return user
}

// ...
```

Ao chamar a requisição na criação de um registro, a senha não vem junto com os outros dados:

![Trazendo apenas dados específicos](./images/Bringing_only_specific_data.png)

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

