> ## Docker Compose
>
> ![Docker](./images/docker_compose.png)

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Visão Geral de Docker Compose](#compose-overview "Visão Geral de Docker Compose")
> - [Compose Installation](#compose-installation "Compose Installation")
> - [Compose Usage](#compose-usage "Compose Usage")

----

### Visão Geral de Docker Compose

#### O que é Docker Compose?

Docker Compose é uma ferramenta que permite definir e gerenciar multi-contêineres Docker para aplicações. Utilizando um arquivo YAML, é possível configurar todos os serviços necessários e, com um único comando, iniciar e gerenciar todos esses serviços.

#### Componentes Principais

1. **Arquivo `docker-compose.yml`**:
   - **Definição**: Um arquivo YAML onde você define todos os serviços, redes e volumes que sua aplicação precisa.
   - **Estrutura**:
     - **Version**: Especifica a versão do arquivo Compose.
     - **Services**: Define os serviços (contêineres) que compõem a aplicação.
     - **Volumes**: Define volumes persistentes para armazenamento de dados.
     - **Networks**: Define redes para comunicação entre contêineres.

2. **Serviços**:
   - Cada serviço representa um contêiner que executa uma parte da aplicação. Pode ser um banco de dados, um servidor web, etc.
   - Os serviços são definidos com base em imagens Docker, que podem ser customizadas diretamente no arquivo `docker-compose.yml`.

#### Comandos Básicos do Docker Compose

1. **Subir os Serviços**:
   - Inicia todos os contêineres definidos no arquivo `docker-compose.yml`:
     ```bash
     docker-compose up
     ```
   - Inicia os contêineres em segundo plano (modo "detached"):
     ```bash
     docker-compose up -d
     ```

2. **Parar os Serviços**:
   - Para todos os contêineres definidos no arquivo `docker-compose.yml`:
     ```bash
     docker-compose down
     ```

3. **Verificar o Status dos Serviços**:
   - Lista os contêineres em execução definidos no arquivo `docker-compose.yml`:
     ```bash
     docker-compose ps
     ```

4. **Logs dos Serviços**:
   - Visualiza os logs de todos os serviços:
     ```bash
     docker-compose logs
     ```

5. **Escalar Serviços**:
   - Escala um serviço específico para múltiplas instâncias:
     ```bash
     docker-compose up -d --scale <serviço>=<número_instâncias>
     ```

#### Exemplo de Arquivo `docker-compose.yml`

Aqui está um exemplo simples de um arquivo `docker-compose.yml` que define uma aplicação web com um serviço de banco de dados:

```yaml
version: '3'

services:
  web:
    image: my-web-app
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - db

  db:
    image: postgres:13
    volumes:
      - db-data:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: mydatabase
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password

volumes:
  db-data:
```

#### Estrutura do Exemplo

1. **version**:
   - Define a versão do formato do arquivo Compose.

2. **services**:
   - **web**:
     - **image**: Especifica a imagem Docker a ser usada.
     - **build**: Constrói a imagem a partir de um Dockerfile no diretório atual.
     - **ports**: Mapeia a porta 5000 do contêiner para a porta 5000 do host.
     - **depends_on**: Define dependências entre serviços. Aqui, `web` depende do serviço `db`.
   - **db**:
     - **image**: Utiliza a imagem oficial do PostgreSQL.
     - **volumes**: Monta um volume para persistência de dados.
     - **environment**: Define variáveis de ambiente necessárias para o banco de dados.

3. **volumes**:
   - Define volumes persistentes que podem ser compartilhados entre contêineres.

#### Benefícios do Docker Compose

1. **Simplicidade**:
   - Facilita a definição e execução de ambientes multi-contêiner com um único arquivo YAML.
   
2. **Automação**:
   - Automatiza a criação, inicialização e parada de contêineres, simplificando o fluxo de trabalho de desenvolvimento.

3. **Reprodutibilidade**:
   - Garante que o ambiente de desenvolvimento seja consistente e replicável em diferentes máquinas e ambientes.

4. **Escalabilidade**:
   - Permite escalar serviços facilmente, ajustando o número de contêineres em execução.

5. **Isolamento**:
   - Cada serviço é executado em seu próprio contêiner, isolado dos outros, o que melhora a segurança e a estabilidade.

Docker Compose é uma ferramenta essencial para desenvolver, testar e implementar aplicações complexas que envolvem múltiplos serviços, tornando a gestão de contêineres Docker mais eficiente e organizada.

Conteúdo do assunto

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

