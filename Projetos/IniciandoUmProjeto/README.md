> ## Iniciando um projeto
>
> ![Docker](./images/StartingAProject.png)

[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")

> ### *Summary*
>
> - [Instalação Passo a Passo do Node.js e NPM no Linux](#instala%C3%A7%C3%A3o-passo-a-passo-do-nodejs-e-npm-no-linux "Instalação Passo a Passo do Node.js e NPM no Linux")
> - [Configuração inicial](#configuração-inicial "Configuração inicial")
> - [Criando banco de dados](#criando-banco-de-dados "Criando banco de dados")
>   - [Docker e Docker Compose](#docker-e-docker-compose "Docker e Docker Compose")
>   - [ORM Prisma](#orm-prisma "ORM Prisma")
>   - [Repository de usuários (CRUD)](#repository-de-usu%C3%A1rios-crud "Repository de usuários (CRUD)")
>   - [Controller de usuário](#controller-de-usu%C3%A1rio "Controller de usuário")
>   - [Ajustando retornos](#ajustando-retornos "Ajustando retornos")
>   - [Paginação de registros](#paginação-de-registros "Paginação de registros")
>   - [Pesquisa de registros](#pesquisa-de-registros "Pesquisa de registros")
>   - [Token JWT](#token-jwt "Token JWT")
>   - [Rota de Login](#rota-de-login "Rota de Login")
>   - [Decoded do Token](#decoded-do-token "Decoded do Token")
>   - [Adicionando Middleware](#adicionando-middleware "Adicionando Middleware")
> - [Começando nosso Frontend](#come%C3%A7ando-nosso-frontend "Começando nosso Frontend")
>   - [Como funciona o Redux e Redux-Saga](#como-funciona-o-redux-e-redux-saga "Como funciona o Redux e Redux-Saga")
>   - [Configurando o Redux](#configurando-o-redux "Configurando o Redux")

## Instalação Passo a Passo do Node.js e NPM no Linux

Para instalar o NPM (Node Package Manager) via terminal no Linux, você pode usar os seguintes comandos. Primeiro, você precisa instalar o Node.js, pois o NPM é distribuído com ele.

```bash
# Atualize o sistema
sudo apt update

# Instale o Node.js
sudo apt install nodejs

# Verifique a instalação do Node.js
node -v

# Instale o NPM
sudo apt install npm

# Verifique a instalação do NPM
npm -v
```

Esses comandos devem instalar o Node.js e o NPM no seu sistema Linux. Lembre-se de que você precisa ter privilégios de superusuário (ou seja, acesso `sudo`) para instalar pacotes no Linux. Se você encontrar algum problema durante a instalação, verifique se o seu sistema está atualizado e tente novamente. Se o problema persistir, você pode precisar procurar soluções específicas para a sua distribuição Linux. 

Por favor, note que esses comandos são para sistemas baseados em Debian, como Ubuntu. Se você estiver usando uma distribuição Linux diferente, os comandos podem variar. Por exemplo, para instalar o Node.js e o NPM no CentOS, você usaria `yum` em vez de `apt`. 

Espero que isso ajude! 😊

[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Configuração inicial

1. Abra o terminal.
2. Navegue até o diretório onde você deseja criar o projeto.
3. Digite o seguinte comando:

    > Terminal

    ```bash
    npm init -y
    ```

    Este comando criará um novo arquivo `package.json` com as configurações padrão. O `-y` é usado para preencher automaticamente as opções padrão.

    > Estrutura de arquivos

    ```bash
    /myProject/
    └─ package.json ">>> New file <<<"
    ```

    **File: `./package.json`**

    ```json
    {
    "name": "backend",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": [],
    "author": "",
    "license": "ISC"
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

    > Estrutura de arquivos

    ```bash
    /myProject/
    ├─ /src/        ">>> New folder <<<"
    │  └─ index.ts  ">>> New file <<<"
    └─ package.json
    ```

    > A estrutura acima, é um exemplo de uma estrutura padrão.

5. Configurações do "TypeScript".

    Você pode instalar o "Nodemon", "ts-node" e "sucrase" como dependências de desenvolvimento usando o NPM com o seguinte comando:

    > Terminal

    ```bash
    npm install --save-dev nodemon ts-node sucrase
    ```

    Agora, vamos entender o que cada pacote faz:

    - **Nodemon**: É uma ferramenta que ajuda a desenvolver aplicativos baseados em node.js ao reiniciar automaticamente a aplicação de node quando detecta alterações de arquivo no diretório.

    - **ts-node**: É uma ferramenta que permite executar TypeScript diretamente, sem a necessidade de compilar os arquivos para JavaScript primeiro. É muito útil durante o desenvolvimento, quando você quer testar rapidamente seu código.

    - **Sucrase**: É um compilador de código super rápido que permite que você escreva código em sintaxes modernas (como ES6, JSX, TypeScript, etc.) e o compila para versões mais antigas do JavaScript que podem ser executadas em ambientes mais antigos.

    Esses três pacotes são comumente usados em conjunto para criar um ambiente de desenvolvimento eficiente para projetos Node.js.

6. Instale o TypeScript usando o NPM com o seguinte comando:

    > Terminal

    ```bash
    npm install typescript
    ```

    Este comando instalará o TypeScript como uma dependência do seu projeto. Agora você pode usar o TypeScript em seu projeto Node.js!

7. Inicialize um novo projeto TypeScript usando o NPM com o seguinte comando:

    > Terminal

    ```bash
    npx tsc --init
    ```

    Este comando cria um novo arquivo `tsconfig.json` na raiz do seu projeto. O arquivo `tsconfig.json` é usado para configurar o compilador TypeScript para o seu projeto. Ele permite que você especifique várias opções de compilação, como o diretório de saída para os arquivos compilados, quais versões do JavaScript devem ser suportadas, quais recursos experimentais devem ser habilitados, entre outras coisas.

    O comando `npx` é uma ferramenta que vem com o NPM e permite executar pacotes Node.js que foram instalados localmente em seu projeto. Neste caso, estamos usando `npx` para executar o compilador TypeScript (`tsc`) com a opção `--init` para inicializar um novo projeto TypeScript.

8. No arquivo `package.json`, altere ...

    **File: `./package.json`**

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

        > Obs.: É provável que existirá o "`"scripts": {...}`", no entanto, apenas modifique-o!

        Deve ficar da seguinte forma:

        **File: `./package.json`**

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

        A linha `"scripts": {...}` define um script que pode ser executado com o comando `npm run script`. A linha `"build": "tsc"` cria o arquivo de build.

        Agora, vamos entender o que cada parte do script faz:

        - **nodemon**: É uma ferramenta que reinicia automaticamente a aplicação Node.js quando detecta alterações nos arquivos.

        - **--watch \"src/**\"**: Esta opção configura o nodemon para observar alterações em todos os arquivos na pasta `src` e suas subpastas.

        - **--ext \"ts,json\"**: Esta opção diz ao nodemon para observar alterações em arquivos com as extensões `.ts` e `.json`.

        - **--exec \"ts-node ./src/server.ts\"**: Esta opção diz ao nodemon para executar o comando `ts-node ./src/server.ts` sempre que um arquivo é alterado. O `ts-node` é uma ferramenta que permite executar TypeScript diretamente, sem a necessidade de compilar os arquivos para JavaScript primeiro. `./src/server.ts` é o arquivo de entrada do seu aplicativo.

9. Instale as dependências que serão necessárias para o projeto:

    Instale os pacotes "express", "cors" e "dotenv" usando o NPM com o seguinte comando:

    > Terminal

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

    > Terminal

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
    // ...Outras linhas...

    dotenv.config();

    const app = express();

    app.use(cors());
    app.use(express.json());

    app.listen(3000, () => {
        console.log("Servidor rodando na porta 3000!");
    })
    ```

13. Start o servidor com o seguinte comando:

    > Terminal

    ```bash
    npm start
    ```

    No console do seu terminal, será exibidas as informações indicando que o servidor está rodando na porta configurada.

    > Terminal

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

[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Criando banco de dados

### Docker e Docker Compose

> Conceito

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

    > Terminal

    ```bash
    curl -fsSL https://get.docker.com | bash
    ```

    Se o Docker estiver instalado, este comando retornará a versão do Docker. Se não estiver instalado, você receberá uma mensagem de erro indicando que o comando 'docker' não foi encontrado. Lembre-se de que você pode precisar de permissões de superusuário (sudo) para executar comandos do Docker, dependendo de como o Docker foi instalado no seu sistema.

2. Crie um arquivo chamado "`docker-compose.yml`" na raiz do seu projeto:

    Sua estrutura de arquivos ficará assim:

    > Estrutura de arquivos

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

    > Terminal

    ```bash
    sudo docker-compose up -d
    ```

    Explicando o comando acima:

    - `sudo`: Este comando é usado para executar o comando seguinte com privilégios de superusuário (root). Isso é necessário porque algumas operações do Docker requerem esses privilégios.

    - `docker-compose up`: Este comando é usado para iniciar todos os serviços definidos em um arquivo `docker-compose.yml` na mesma pasta. Ele cria e inicia contêineres para cada serviço.

    - `-d`: Esta opção, também conhecida como "detached mode", faz com que os contêineres sejam executados em segundo plano. Sem essa opção, os logs dos contêineres seriam enviados para o terminal atual.

    Para visualizar a imagem criada, você pode usar o comando `docker images`. Este comando lista todas as imagens Docker disponíveis no seu sistema. Aqui está o comando:

    > Terminal

    ```bash
    docker images
    ```

    Você verá uma lista de imagens com informações como o repositório, a tag, o ID da imagem, quando foi criada e o tamanho. A imagem do PostgreSQL que você usou no seu arquivo `docker-compose.yml` deve aparecer nesta lista. Lembre-se de que você pode precisar de permissões de superusuário (sudo) para executar comandos do Docker, dependendo de como o Docker foi instalado no seu sistema. Se você usou uma tag específica para a imagem do PostgreSQL no seu arquivo `docker-compose.yml`, você também verá essa tag na lista. Se nenhuma tag foi especificada, a tag padrão é `latest`.

    Você verá algo parecido com isto:

    > Terminal

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

    > Terminal

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

    > Terminal

    ```bash
    root@10:/home/userlinux/Documentos/Projects/myProject/api# docker ps
    CONTAINER ID   IMAGE      COMMAND                  CREATED      STATUS        PORTS                                       NAMES
    d1096018f728   postgres   "docker-entrypoint.s…"   2 days ago   Up 15 hours   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   pgsql-db
    root@10:/home/userlinux/Documentos/Projects/myProject/api#
    ```

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### ORM Prisma

3. Configure o ORM Prisma:

    > Conceito

    Prisma ORM é um mapeador objeto-relacional (ORM) de código aberto e de próxima geração. Ele consiste nas seguintes partes:

    - **Prisma Client**: Um construtor de consultas autogerado e com tipagem segura para Node.js e TypeScript.
    - **Prisma Migrate**: Sistema de migração.
    - **Prisma Studio**: Interface gráfica para visualizar e editar dados no seu banco de dados.

    Cada projeto que usa uma ferramenta do conjunto de ferramentas Prisma ORM começa com um arquivo de esquema Prisma. O esquema Prisma permite que os desenvolvedores definam seus modelos de aplicação em uma linguagem intuitiva de modelagem de dados.

    Aqui está um exemplo de definição de modelo com tipos de dados:

    ```prisma
    model     User {
    id        Int      @id @default(autoincrement())
    name      String
    email     String   @unique
    age       Int?
    createdAt DateTime @default(now())
    role      Role     @default(USER)
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

    > Terminal

    ```bash
    npm install prisma @prisma/client
    ```

    Este comando instala o pacote `prisma` que contém o CLI do Prisma e o pacote `@prisma/client` que é o cliente do Prisma.

    Depois de instalar o Prisma, você pode gerar o cliente Prisma usando o seguinte comando:

    > Terminal

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

        > Estrutura de arquivos

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

        > Terminal

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

        > Estrutura de arquivos

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

        > Terminal

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

> Conceito

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

> Estrutura de arquivos

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
    master   Boolean @default(false)
    status   Boolean @default(true)
    deleted  Boolean @default(false)
}
```

Na tabela acima, o ponto de interrogação (?) após o tipo de campo indica que o campo é **opcional**. Isso significa que quando um novo registro é criado na tabela `User`, esses campos podem ser deixados em branco. Em outras palavras, não é necessário fornecer um valor para esses campos ao criar um novo `User`.

Quanto à coluna `masterId`, foi adicionada para definir a quem pertence. Ela serve para identificar a qual usuário mestre um determinado registro pertence. Isso é útil em cenários onde você tem uma relação de "muitos para um" entre registros e usuários mestres. Por exemplo, se vários registros na tabela `User` pertencem a um único usuário mestre, você pode usar o `masterId` para rastrear isso. Se `masterId` for opcional (como indicado pelo `?`), isso significa que nem todos os usuários precisam pertencer a um usuário mestre. Alguns registros `User` podem não ter um `masterId`.

Após essa alteração, é preciso dizer ao Prisma que houve alterações e ele tem que atualizar no banco de dados, segue o comando novamente:

> Terminal

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



> Estrutura de arquivos

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
    master?:   boolean;
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
export const getAll = async (masterId: number | null) => {
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

> Estrutura de arquivos

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
        const masterId = null;
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

> Terminal

```bash
npm install bcrypt @types/bcrypt
```

Crie um arquivo para retornar o erros, as validações. Veja a estrutura com o arquivo "`./src/validations/user.validation.ts`":

> Estrutura de arquivos

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

> Terminal

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
    masterId:  z.number().nullable().optional(),
    master:    z.boolean().default(false).optional()
})
```

Crie o arquivo "`./src/routes/user.routes.ts`" para definir as rotas, segue abaixo a estrutura de arquivos com o novo arquivo e o conteúdo:

> Estrutura de arquivos

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

> Estrutura de arquivos

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
// ...Outras linhas...

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

// ...Outras linhas...
```

Retorna somente o ID, deixando de apresentar todos os dados do registro:

![Ajustando o retorno da crição de registro obtendo apenas o ID](./images/Adjusting_returns_by_bringing_in_the_ID.png)

Ajuste o "`getById`", quando o registro for requisitado a partir de um ID:

```ts
// ...Outras linhas...

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

// ...Outras linhas...
```

Ao chamar a requisição de criação de um registro, a senha não vem junto com os outros dados, observe que a coluna "`password:`" foi definida como "`false`":

![Trazendo apenas dados específicos](./images/Bringing_only_specific_data.png)

Ajuste o "`updateUser`", quando a atualização for requisitada a partir de um ID:

```ts
// ...Outras linhas...

// Atualizar registro a partir de um ID.
export const updateUser = async (id: number, data: any) => {
    const user = await prisma.user.update({
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
        },
        data
    });
    return user
}

// ...Outras linhas...
```

Ao chamar a requisição de atualização de um registro, a senha também não vem junto com os outros dados, observe que a coluna "`password:`" foi definida como "`false`":

![Trazendo apenas dados específicos](./images/Bringing_only_specific_data_-_updateUser.png)

Ajuste o "`getAll`", quando a seleção de todos os registros for solicitada:

```ts
// ...Outras linhas...

// Listar todos os registros.
export const getAll = async (masterId: number | null) => {
    const users = await prisma.user.findMany({
        where: {
            deleted: false,
            masterId
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
        },
    });
    return users;
}

// ...Outras linhas...
```

Ao chamar a requisição de seleção de todos os registros, a senha não vem junto com os outros dados, observe que a coluna "`password:`" foi definida como "`false`":

![Trazendo apenas dados específicos, com o 'getAll'](./images/Bringing_only_specific_data_-_getAll.png)

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Paginação de registros

> Conceito

O Prisma é um ORM (Object Relational Mapping) que tem como objetivo principal facilitar a interação entre o código da aplicação e os dados armazenados em um banco de dados relacional, eliminando a necessidade de escrever consultas SQL manualmente.

Embora a "Paginação de registros" não tenha sido explicitamente mencionada nossa documentação, é um conceito comum em muitos ORMs, incluindo o Prisma. A paginação é uma técnica usada para dividir um grande conjunto de dados em partes menores (ou páginas). Isso torna a manipulação de grandes conjuntos de dados mais eficiente e a experiência do usuário mais fluida.

No Prisma, você pode usar os operadores `take` e `skip` para implementar a paginação. O operador `take` define o número de registros que você deseja obter, enquanto o operador `skip` define quantos registros você deseja pular.

Aqui está um exemplo de como você pode implementar a paginação com Prisma:

```javascript
const posts = await prisma.post.findMany({
  take: 10, // Limita o número de posts retornados para 10
  skip: 5,  // Pula os primeiros 5 posts
});
```

Neste exemplo, o Prisma retornará 10 posts, começando do sexto post. Isso é útil quando você tem muitos registros e quer exibi-los em partes menores para melhorar a experiência do usuário.

> Vamos imaginar que temos 100 registros em uma tabela, mas ao invés de entregar 100 registro de uma vez para o Frontend, com a paginação, podendo entregar por exemplo, 20 registros a cada página. Veja o exemplo abaixo:
>
> |  De  | Até  |
> | :--: | :--: |
> |  1   |  20  |
> |  21  |  40  |
> |  41  |  60  |
> |  61  |  80  |
> |  81  | 100  |
>
> Dessa forma, os registros serão entregues por parte, a cada 10 registros.

Modifique o "`getAll`" no arquivo "`./src/repositories/user.repository.ts`" para então começar a fatiar os resultados:

```ts
// ...Outras linhas...

// Listar todos os registros.
export const getAll = async (
    masterId: number | null,
    skip: number,
    take: number
) => {
    const[users, total] = await prisma.$transaction([
        prisma.user.findMany({
            where: {
                deleted: false,
                masterId
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
            },
            skip,
            take
        }),
        prisma.user.count({
            where: {
                masterId,
                deleted: false
            },
        }),
    ]);

    // Retornar os registros.
    const totalPage = Math.ceil(total / take);
    return { total, totalPage, users }
};

// ...Outras linhas...
```

> Observe que temos duas variáveis (`users, total`) e duas funções (`findMany({...}), count({...})`):
> 
> ```ts
> // ...Outras linhas...
> 
> const[
>     users,
>     total
> ] = await prisma.$transaction([
>     prisma.user.findMany({...}),
>     prisma.user.count({...})
> ]);
> 
> // ...Outras linhas...
> ```
> O valor da primeira função (`findMany({...})`) vai definir a variável (`users`) e o valor da segunda função (`count({...})`) vai definir a variável (`total`).

Quem definirá qual será a página que exibirá os 20 resultados a cada fatia do total de registro, é o "`Frontend`" utilizando um "componente de paginação", veja o exemplo dos botões que indicam a aquantidade de páginas:

![Componente de paginação](./images/paginationComponent.png)

No arquivo "`./src/controllers/user.controller.ts`", será esperado os parâmetros "`skip, take`", veja a modificação no código:

**File: `./src/controllers/user.controller.ts`**

```jsx
// ...Outras linhas...

// Listar todos os registros.
export const get = async (req: Request, res: Response) => {
    try {
        const masterId = null;
        const skip = Number(req.query?.skip) || 0;
        const take = Number(req.query?.take) || 20;
        const user = await getAll(masterId, skip, take);
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
}

// ...Outras linhas...
```

> Linha alteradas:
>
> `const skip = Number(req.query?.skip) || 0;`
>
> `const take = Number(req.query?.take) || 20;`
>
> `const user = await getAll(masterId, skip, take);`

Para testar a requisição, vá no "Thunder Client" ou o "Insomnia" (sua preferência) no "`getAll`", na rota "`user`" e execute-a:

> Resultado:

![Execução de requisição com paginação](./images/requestTest1WithPagination.png)

> Observe que a resposta traz o total e a quantidade junto com os registros.
>
> ```json
> {
>     "total": 2,
>     "totalPage": 1,
>     "users": [
>         {...
> ```

Passando o parâmetro da paginação pelo "`GET`" na rota:

```tex
http://localhost:3000/v1/user?skip=0&take=20
```

Altere os parâmetros (`..?skip=0&take=20`) nos testes e verá o resultado.

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Pesquisa de registros

> Conceito

A "Pesquisa de registros" é um recurso importante em qualquer ORM, incluindo o Prisma. Ele permite que você encontre registros específicos em seu banco de dados com base em determinados critérios.

No Prisma, você pode usar o método `findMany` com um objeto de filtro para pesquisar registros. Este objeto de filtro pode incluir várias condições que os registros devem atender para serem retornados pela consulta.

Aqui está um exemplo de como você pode implementar a pesquisa de registros com Prisma:

```javascript
const users = await prisma.user.findMany({
  where: {
    OR: [
      { name: { contains: 'searchTerm' } },
      { email: { contains: 'searchTerm' } },
    ],
  },
});
```

Neste exemplo, o Prisma retornará todos os usuários cujo nome ou e-mail contém o termo de pesquisa. O operador `contains` é usado para pesquisar o termo dentro dos campos `name` e `email`. O operador `OR` é usado para retornar registros que atendem a qualquer uma das condições especificadas.

Por favor, note que 'searchTerm' deve ser substituído pelo termo de pesquisa real que você deseja usar. Além disso, este é apenas um exemplo e a estrutura exata da consulta pode variar dependendo do seu esquema de banco de dados e dos campos que você deseja pesquisar.

Vamos aplicar uma pesquisa de registros, vamos dar exeplos de usuários em uma tabela.

No arquivo "`./prisma/schema.prisma`", no "`generator client {...}`", adicione a linha "`previewFeatures = ["fullTextSearch"]`", veja o código do arquivo:

**File: `./prisma/schema.prisma`**

```prisma
// ...Outras linhas...
generator client {
    provider        = "prisma-client-js"
    previewFeatures = ["fullTextSearch"]
}
// ...Outras linhas...
```

> Atenção! Para MySQL, você também precisará incluir o sinalizador do recurso de visualização "`fullTextIndex`":
> 
> ```prisma
> // ...Outras linhas...
> generator client {
>     provider        = "prisma-client-js"
>     previewFeatures = ["fullTextSearch", "fullTextIndex"]
> }
> // ...Outras linhas...
> ```

Execute o Generate Prisma Client com o comando:

> Terminal

```bash
npx prisma generate
```

> Obs.: Não esqueça de parar a API para rodar o comando, após executar o Generate, start novamente a API.

Modifique o "`getAll`" no arquivo "`./src/repositories/user.repository.ts`" para receber o parâmetro da pesquisa como uma "`string`". Veja o código modificado:

```ts
// ...Outras linhas...

// Listar todos os registros.
export const getAll = async (
    masterId: number | null,
    skip: number,
    take: number,
    search: string | null
) => {
    if (!search) {
        const[users, total] = await prisma.$transaction([
            prisma.user.findMany({
                where: {
                    deleted: false,
                    masterId
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
                },
                skip,
                take
            }),
            prisma.user.count({
                where: {
                    masterId,
                    deleted: false
                },
            }),
        ]);

        // Retornar os registros.
        const totalPage = Math.ceil(total / take);
        return { total, totalPage, users }
    } else {
        const[users, total] = await prisma.$transaction([
            prisma.user.findMany({
                where: {
                    deleted: false,
                    masterId,
                    name: {
                        search
                    }
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
                },
                skip,
                take
            }),
            prisma.user.count({
                where: {
                    masterId,
                    deleted: false
                },
            }),
        ]);

        // Retornar os registros.
        const totalPage = Math.ceil(total / take);
        return { total, totalPage, users }
    }
};

// ...Outras linhas...
```

No arquivo "`./src/controllers/user.controller.ts`", será esperado os parâmetros "`search`" após "`skip, take`" que também virá por parâmetro, veja a modificação no código:

**File: `./src/controllers/user.controller.ts`**

```jsx
// ...Outras linhas...

// Listar todos os registros.
export const get = async (req: Request, res: Response) => {
    try {
        const masterId = null;
        const skip = Number(req.query?.skip) || 0;
        const take = Number(req.query?.take) || 20;
        const search = req.query?.search ? String(req.query?.search) : null;
        const user = await getAll(masterId, skip, take, search);
        return res.status(200).send(user);
    } catch (e) {
        return res.status(400).send(e);
    }
}

// ...Outras linhas...
```

Para testar, use o parâmetro "`&search=`" na execução da requisição da rota "`user`", veja o exemplo:

```tex
http://localhost:3000/v1/user?search=rafael
```

> "Rafael" é o termo da busca!

> Resultado:

![Execução de requisição da pesquisa na rota 'user'](./images/requestTest1WithResearch.png)

> Detalhe! Não precisa digitar palavras capitalizadas ou maiúscula em (`...?search=rafael`), a pesquisa não faz essa diferença.

A paginação pode continuar na rota, os parâmetros "`skip, take`" junto com o "`search`":

```tex
http://localhost:3000/v1/user?skip=0take=20&search=rafael
```

O Prisma receberá o termo pesquisado no Search "`...&search=rafael`".

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Token JWT

> Conceito

O JWT (JSON Web Token) é uma forma de autenticação que permite que um servidor verifique a identidade de um usuário sem precisar armazenar informações sobre ele. Ele é um padrão aberto para representar dados de forma compacta e segura entre as partes. 

O JWT é formado por três seções: Header, Payload e Signature. Ele é assinado usando uma chave secreta com algoritmo HMAC ou um par de chaves públicas e privadas RSA ou ECDSA. 

Os dados contidos no token são públicos e podem ser lidos por qualquer um que o possua, porém há um mecanismo de segurança que faz com que somente quem tenha a senha, possa modificá-lo.

O JWT é muito utilizado em cenários de autorização. Depois que o usuário estiver conectado, é possível observar cada solicitação e verificar se esta inclui o JWT, permitindo que o usuário acesse rotas, serviços e outros recursos. Além disso, os JWTs são úteis para trocas de informações pois, como eles são assinados, é possível ter certeza de que os remetentes são quem dizem ser quem são.

**Agora vamos trabalhar com a proteção de nossa API.**

> Vamos aplicar uma autenticação com o **Token JWT** ([https://jwt.io](https://jwt.io "Site do Token JWT")).
> ![Token JWT](./images/Token_JWT.png)

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Rota de Login

A primeira coisa que vamos fazer, é uma validação. Crie o arquivo "`./src/validation/auth.validation.ts`":

**File: `./src/validation/auth.validation.ts`**

```ts
import { z } from 'zod';

export const authValidation = z.object({
    email: z.string().email(),
    password: z.string().min(6)
});
```

Crie o arquivo "`./src/controllers/auth.controller.ts`":

**File: `./src/controllers/auth.controller.ts`**

```ts
import { authValidation } from '../validation/auth.validation';
import { getUser } from '../repositories/auth.repository';
import bcrypt from 'bcrypt';
import jwt from 'jsonwebtoken';

export const auth = async (req: any, res: any) => {
    try {
        const data = await authValidation.parse(req.body);
        const user = await getUser(data.email);
        if (!user) throw { message: "Usuário não existe!" };
        if (user && !user.status) throw { message: "Usuário bloqueado!" };
        if (user && bcrypt.compareSync(data.password, user.password)) {
            const token = jwt.sign(
                {
                    id: user.id,
                    name: user.name,
                    master: user.master,
                    masterId: user.masterId
                },
                String(process.env.TOKEN_KEY),
                { expiresIn: '24h' }
            );
            return res.status(200).send({ token });
        } else {
            return res.status(401).send({ message: "Não autorizado!" });
        };
    } catch (e) {
        return res.status(401).send(e);
    };
};
```

> Observação: Para gerar o token, é necessário uma biblioteca, instale com o comando abaixo:
>
> ```bash
> npm install jsonwebtoken
> ```
> 
> Este comando instalará o pacote `jsonwebtoken` no seu projeto. Lembre-se de executar este comando no diretório raiz do seu projeto onde o arquivo `package.json` está localizado.

> Ahh! Não esquecer também o pacote `@types/jsonwebtoken`:
> 
> ```bash
> npm install --save-dev @types/jsonwebtoken
> ```
> 
> Este comando instalará o pacote `@types/jsonwebtoken` como uma dependência de desenvolvimento no seu projeto. Lembre-se de executar este comando no diretório raiz do seu projeto onde o arquivo `package.json` está localizado. As dependências de desenvolvimento são pacotes que não são necessários para o aplicativo em execução, mas são necessários para o desenvolvimento, como pacotes de teste ou de tipos.

Crie o arquivo "`./src/repositories/auth.repository.ts`":

**File: `./src/repositories/auth.repository.ts`**

```ts
import { prisma } from "../services/prisma";

export const getUser = async (email: string) => {
    const user = await prisma.user.findFirst({
        where: {
            email
        },
    });
};
```

Crie uma variável de ambiente no arquivo "`.env`":

**File: `.env`**

```
# ...Outras linhas...

TOKEN_KEY="b9c9d7ee2bd3c0a4baa9b817de5d7d2fbc18db78d28db2374efd8d2c5a2e798a0f55feffd920759f54491ee8918fa4be52e5cef5756a9d020a695f832632fedf"
```

> Gerar um Hash: [Gerador de Hash](http://andti.com.br/tool/hash "Gerador de Hash")
> ![Gerador de Hash](./images/HashGenerator.png)

Crie uma rota no arquivo "`./src/routes/auth.routes.ts`":

**File: `./src/routes/auth.routes.ts`**

```ts
import { auth }  from '../controllers/auth.controller';

export const authRoutes = (app: any) => {
    app.post("/v1/login", auth);
};
```

No arquivo "`./src/routes/index.ts`", a nova rota tem que ser entendida:

**File: `./src/routes/index.ts`**

```ts
import { userRoutes } from './user.routes';
import { authRoutes } from './auth.routes';

const routes = (app: any) => {
    userRoutes(app);
    authRoutes(app);
}

export default routes;
```

Após essa modificação, dê um "`npm start`" para testar.

Use a nova rota "`http://localhost:3000/v1/login`" sem passar nada, como se o usuário tentasse entrar sem informar o email e senha:

![Tentar acessar sem passar nada](./images/accessWithoutPassingData.png)

> Observe que a resposta exige o email e a senha!

![Tentar acessar passando os dados](./images/accessByPassingData.png)

> Observe agora que ao passar os dados, a resposta vem com o TOKEN!

![Tentar acessar passando os dados](./images/passingWrongPassword.png)

![Tentar acessar passando os dados](./images/sendingWrongEmail.png)

> Observe a validação da senha e do email quando um ou ambos são informado erradamente!

> Estrutura de arquivos

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
│  │  ├─ auth.controller.ts    ">>> New file <<<"
│  │  └─ user.controller.ts
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /repositories/
│  │  ├─ auth.repository.ts    ">>> New file <<<"
│  │  └─ user.repository.ts
│  ├─ /routes/
│  │  ├─ auth.routes.ts        ">>> New file <<<"
│  │  ├─ index.ts
│  │  └─ user.routes.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  ├─ /validations/
│  │  ├─ auth.validation.ts    ">>> New file <<<"
│  │  └─ user.validation.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Decoded do Token

Vamos fazer a descriptografia do **Token**, para isso, vamos criar uma nova função no arquivo "`./src/controllers/auth.controller.ts`":

**File: `./src/controllers/auth.controller.ts`**

```ts
import { authValidation, tokenValidation } from '../validation/auth.validation';

// ...Outras linhas...

export const validate = async (req: any, res: any) => {
    try {
        const data = await tokenValidation.parse(req.body);
        const decode = await jwt.decode(data.token);
        return res.status(200).send(decode);
    } catch (e) {
        return res.status(400).send(e);
    };
};
```

Crie uma validação no arquivo "`./src/validation/auth.validation.ts`":

**File: `./src/validation/auth.validation.ts`**

```ts
// ...Outras linhas...

export const tokenValidation = z.object({
    token: z.string()
});
```

Na rota no arquivo "`./src/routes/auth.routes.ts`" importe o "`validate`" e criar mais uma rota:

**File: `./src/routes/auth.routes.ts`**

```ts
import { auth, validate }  from '../controllers/auth.controller';

export const authRoutes = (app: any) => {
    app.post("/v1/login", auth);
    app.post("/v1/validate", validate);
};
```

Teste no "Thunder Cliente" ou "Insomnia":

![Decoded do Token, imagem 1](./images/TokenDecoded_img_1.png)

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Adicionando Middleware

> Conceito

"Middleware" é um termo usado em programação com NodeJS e ORM Prisma para se referir a funções que têm acesso ao objeto de solicitação (request), ao objeto de resposta (response) e à próxima função de middleware no ciclo de solicitação-resposta do aplicativo.

Os middlewares atuam como ganchos de ciclo de vida em nível de consulta, permitindo que você execute uma ação antes ou depois que uma consulta é executada. Você pode usar o método `prisma.$use` para adicionar um middleware. Aqui está um exemplo de como você pode adicionar um middleware:

```javascript
const prisma = new PrismaClient()

// Middleware 1
prisma.$use(async (params, next) => {
  // Manipule os parâmetros aqui
  const result = await next(params)
  // Veja os resultados aqui
  return result
})

// Middleware 2
prisma.$use(async (params, next) => {
  // Manipule os parâmetros aqui
  const result = await next(params)
  // Veja os resultados aqui
  return result
})
```

Os parâmetros representam os parâmetros disponíveis no middleware, como o nome da consulta, e o próximo representa o próximo middleware na pilha ou a consulta original do Prisma Client.

Os casos de uso possíveis para o middleware incluem:
- Definir ou substituir um valor de campo - por exemplo, definir o idioma do contexto de um comentário de postagem de blog.
- Validar dados de entrada - por exemplo, verificar a entrada do usuário para linguagem inadequada por meio de um serviço externo.
- Interceptar uma consulta de exclusão e alterá-la para uma atualização para realizar uma exclusão suave.
- Registrar o tempo necessário para executar uma consulta.

Há muitos outros casos de uso para o middleware - esta lista serve como inspiração para os tipos de problemas que o middleware foi projetado para resolver.

**Vamos lá para entendermos o conceito!**

Crie o diretório e o arquivo "`./src/middlewares/auth.ts`":

**File: `./src/middlewares/auth.ts`**

```ts
import jwt from "jsonwebtoken";

export const verifyToken = async (req: any, res: any, mext: any) => {
    try {
        const token = req.headers.authorization;
        
        if (!token) throw { message: 'Necessário passar o token!' };

        const replace = token.replace('Bearer ', '');
        const decoded = jwt.verify(replace, String(process.env.TOKEN_KEY));
        req.user = decoded;
        next();
    } catch (e) {
        return res.status(401).send(e);
    }
};
```

> Atenção! Após o "Bearer" deve ter um espaço, veja: "`...ace('Bearer ', '...`"!

Nas rotas de usuários no arquivo "`./src/routes/user.routes.ts`" importe o "`verifyToken`" e modifique os:

> app.get('/v1/user', get);
> 
> app.get('/v1/user/:id', getId);
> 
> app.put('/v1/user/:id', update);
> 
> app.delete('/v1/user/:id', remove)

Para:

> app.get('/v1/user', verifyToken, get);
> 
> app.get('/v1/user/:id', verifyToken, getId);
> 
> app.put('/v1/user/:id', verifyToken, update);
> 
> app.delete('/v1/user/:id', verifyToken, remove)

Deve ficar da seguinte forma:

**File: `./src/routes/user.routes.ts`**

```jsx
// ...Outras linhas...
import { verifyToken } from '../middlewares/auth';

// Rotas.
export const userRoutes = (app: any) => {
    // ...Outras linhas...
    app.get('/v1/user', verifyToken, get);
    app.get('/v1/user/:id', verifyToken, getId);
    app.put('/v1/user/:id', verifyToken, update);
    app.delete('/v1/user/:id', verifyToken, remove)
};
```

> Obs.: Na linha "`app.post('/v1/user', create);`" não é necessário, porque é uma rota de criação de registro!

Faça o teste com o "Thunder Client" ou "Insomnia":

> Sem o "TOKEN"!

![Adicionando Middleware, testando...](./images/Adding_Middleware_test_1.png)

> Com o "TOKEN"!

![Adicionando Middleware, testando...](./images/Adding_Middleware_test_2.png)

> Atenção! O "Bearer" não é necessário ser passado, quando a autenticação for feita pelo Fronend o "Bearer" vai automaticamente!

![Adicionando Middleware, testando...](./images/Adding_Middleware_test_3.png)

> Estrutura de arquivos

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
│  │  ├─ auth.controller.ts
│  │  └─ user.controller.ts
│  ├─ /entities/
│  │  └─ user.ts
│  ├─ /middlewares/            ">>> New folder <<<"
│  │  └─ auth.ts               ">>> New file <<<"
│  ├─ /repositories/
│  │  ├─ auth.repository.ts
│  │  └─ user.repository.ts
│  ├─ /routes/
│  │  ├─ auth.routes.ts
│  │  ├─ index.ts
│  │  └─ user.routes.ts
│  ├─ /services/
│  │  └─ prisma.ts
│  ├─ /validations/
│  │  ├─ auth.validation.ts
│  │  └─ user.validation.ts
│  └─ index.ts
├─ .env
├─ docker-compose.yml
└─ package.json
```

[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Começando nosso Frontend

"Frontend", também conhecido como desenvolvimento de interface do usuário, é a parte do desenvolvimento web que lida com o que o usuário vê e interage em um site ou aplicativo da web. 

Os desenvolvedores frontend usam tecnologias como HTML, CSS e JavaScript para criar a interface do usuário. Eles são responsáveis por tudo o que você vê e interage em um site, incluindo layout, design, cores, fontes e formulários.

Aqui estão alguns conceitos-chave no desenvolvimento frontend:

- **HTML (HyperText Markup Language)**: É a linguagem de marcação usada para estruturar e dar significado ao conteúdo da web.

    ![HTML](./images/html_code.png)

- **CSS (Cascading Style Sheets)**: É a linguagem usada para estilizar as páginas da web, incluindo layout, cores e fontes.

    ![CSS](./images/css_code.png)

- **JavaScript**: É a linguagem de script usada para criar funcionalidades dinâmicas na web.

    ![JavaScript](./images/javascript_code.png)

Além disso, os desenvolvedores frontend podem usar várias ferramentas e frameworks para facilitar o desenvolvimento, como React, Angular, Vue.js, SASS, LESS, entre outros.

Em resumo, o frontend é a parte do site que os usuários veem e interagem, e é criado usando várias tecnologias de codificação, como HTML, CSS e JavaScript..

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Como funciona o Redux e Redux-Saga

> Conceito

Vamos explorar os conceitos de **Redux** e **Redux-Saga**:

1. **Redux**:
   - O **Redux** é uma biblioteca amplamente utilizada para gerenciamento de estado em aplicações **React**.
   - Ele centraliza o estado da aplicação em uma única **store**.
   - Os principais componentes do Redux são:
     - **Actions**: Representam eventos que ocorrem na aplicação. São objetos que descrevem o que aconteceu e são responsáveis por alterar o estado.
     - **Reducers**: Funções puras que atualizam o estado com base nas ações. Recebem o estado atual e uma ação como entrada e retornam um novo estado.
     - **Store**: Armazena o estado global da aplicação.
     - **Dispatch**: Método para disparar ações.
   - O Redux é excelente para gerenciar o estado síncrono da aplicação.

2. **Redux-Saga**:
   - O **Redux-Saga** é um middleware para lidar com efeitos colaterais assíncronos no Redux.
   - Ele utiliza **sagas**, que são padrões de design originados do mundo de transações distribuídas.
   - As sagas são como threads separadas na aplicação, responsáveis exclusivamente pelos efeitos colaterais.
   - Principais características do Redux-Saga:
     - Pode ser iniciado, pausado e cancelado a partir da aplicação principal usando ações Redux normais.
     - Tem acesso ao estado completo da aplicação Redux.
     - Pode despachar ações Redux.
   - As sagas gerenciam o fluxo de operações assíncronas e permitem lidar com tarefas complexas, como chamadas de API e manipulação de cookies.

Em resumo, o **Redux** é uma biblioteca para gerenciamento de estado síncrono, enquanto o **Redux-Saga** lida com operações assíncronas de maneira eficiente, tornando o código mais legível e controlável.

> Como funciona

**Redux** é uma biblioteca amplamente utilizada para gerenciamento de estado em aplicações **React**. Vamos explorar como ele funciona:

1. **Centralização do Estado**:
   - O Redux centraliza o estado da aplicação em uma única store.
   - Cada componente pode acessar e modificar esse estado compartilhado.

2. **Componentes do Redux**:
   - **Actions**: Representam eventos que ocorrem na aplicação. São objetos que descrevem o que aconteceu.
   - **Reducers**: Funções puras que atualizam o estado com base nas ações. Recebem o estado atual e uma ação como entrada e retornam um novo estado.
   - **Store**: Armazena o estado global da aplicação.
   - **Dispatch**: Método para disparar ações.

3. **Fluxo de Dados**:
   - Um componente dispara uma ação usando `dispatch`.
   - O reducer atualiza o estado com base na ação.
   - Os componentes interessados são notificados sobre a mudança no estado.

4. **Redux-Saga**:
   - É um middleware para lidar com efeitos colaterais assíncronos no Redux.
   - Utiliza funções geradoras do JavaScript para tornar o código mais legível e controlável.
   - Exemplos de efeitos colaterais: chamadas de API, manipulação de cookies, etc.

5. **Ciclo de Trabalho do Redux-Saga**:
   - O componente dispara uma ação.
   - O saga intercepta a ação e executa tarefas assíncronas.
   - Após a conclusão, o saga dispara uma nova ação para atualizar o estado.

6. **Benefícios do Redux-Saga**:
   - Separação clara entre lógica assíncrona e lógica de estado.
   - Facilita testes unitários.
   - Permite tratamento avançado de fluxos assíncronos.

Em resumo, o Redux e o Redux-Saga trabalham juntos para gerenciar o estado da aplicação, tornando-o previsível e escalável. O Redux cuida do estado síncrono, enquanto o Redux-Saga lida com operações assíncronas de maneira eficiente.

[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Configurando o Redux

Content...

[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

