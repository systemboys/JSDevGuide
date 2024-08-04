> ## Docker Compose
>
> ![Docker](./images/docker_compose.png)

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Visão Geral de Docker Compose](#vis%C3%A3o-geral-de-docker-compose "Visão Geral de Docker Compose")
> - [Como Instalar Docker Compose](#como-instalar-docker-compose "Como Instalar Docker Compose")
> - [Compose Usage](#compose-usage "Compose Usage")

----

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

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

## Como Instalar Docker Compose

Para instalar Docker Compose no Linux (Debian, Ubuntu e outras distribuições baseadas em Debian), siga os passos abaixo:

#### Passo 1: Atualizar o Sistema

Primeiro, certifique-se de que seu sistema está atualizado:

```bash
sudo apt update
sudo apt upgrade
```

#### Passo 2: Baixar a Versão Mais Recente do Docker Compose

Acesse o site oficial do Docker Compose para verificar a versão mais recente. No momento da escrita deste guia, você pode usar o seguinte comando para baixar a versão estável mais recente:

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

#### Passo 3: Aplicar Permissões Executáveis

Aplique permissões executáveis ao binário Docker Compose:

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

#### Passo 4: Verificar a Instalação

Para verificar se o Docker Compose foi instalado corretamente, você pode verificar a versão instalada:

```bash
docker-compose --version
```

Você deve ver a versão do Docker Compose instalada, algo como:

```
docker-compose version 1.29.2, build 5becea4c
```

#### Passo 5: Configurar Autocompletar (Opcional)

Se você quiser habilitar o autocompletar para o Docker Compose, execute os seguintes comandos:

```bash
sudo curl -L https://raw.githubusercontent.com/docker/compose/1.29.2/contrib/completion/bash/docker-compose -o /etc/bash_completion.d/docker-compose
source /etc/bash_completion.d/docker-compose
```

### Nota sobre Atualizações

Para atualizar o Docker Compose no futuro, basta repetir os passos acima para baixar a versão mais recente e substituir o binário existente.

### Passo Adicional: Instalar Docker (se ainda não estiver instalado)

Se você ainda não tiver o Docker instalado, siga os passos abaixo para instalá-lo:

1. **Adicionar Repositório Docker**:
   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common
   curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

2. **Instalar Docker**:
   ```bash
   sudo apt update
   sudo apt install docker-ce
   ```

3. **Iniciar e Habilitar Docker**:
   ```bash
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

4. **Adicionar Seu Usuário ao Grupo Docker**:
   ```bash
   sudo usermod -aG docker $USER
   ```

   Saia e entre novamente na sua sessão para que as mudanças tenham efeito.

Com esses passos, Docker e Docker Compose estarão instalados e prontos para uso no seu sistema Debian Linux.

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

