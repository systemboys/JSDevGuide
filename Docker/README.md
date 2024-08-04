> ## Docker
>
> ![Docker](./images/docker.png)

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Visão Geral do Docker](#vis%C3%A3o-geral-do-docker "Visão Geral do Docker")
> - [Guia Completo para Instalação do Docker no Debian Linux](#guia-completo-para-instala%C3%A7%C3%A3o-do-docker-no-debian-linux "Guia Completo para Instalação do Docker no Debian Linux")
> - [Noções básicas do Docker](#docker-basics "Noções básicas do Docker")
> - [Docker Compose](./DockerCompose/README.md#docker-compose "Docker Compose")

----

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Visão Geral do Docker

#### O que é o Docker?

Docker é uma plataforma de código aberto que automatiza a implantação de aplicações em contêineres de software, proporcionando uma camada adicional de abstração e automação de virtualização de nível de sistema operacional no Windows e no Linux.

#### Conceitos Fundamentais

1. **Contêineres**:
   - **Definição**: Unidades de software que empacotam o código e todas as suas dependências para que a aplicação possa ser executada de maneira rápida e confiável de um ambiente computacional para outro.
   - **Isolamento**: Cada contêiner é isolado, executando sua própria instância de uma aplicação ou serviço, mas compartilha o mesmo kernel do sistema operacional.

2. **Imagens**:
   - **Definição**: Uma imagem Docker é um arquivo de sistema de arquivos somente leitura que contém todas as informações necessárias para criar um contêiner. Isso inclui o sistema operacional, o código da aplicação, bibliotecas, e dependências.
   - **Reusabilidade**: Imagens podem ser reutilizadas para criar múltiplos contêineres, garantindo consistência entre ambientes de desenvolvimento, teste e produção.

3. **Dockerfile**:
   - **Definição**: Um arquivo de texto simples que contém instruções sobre como construir uma imagem Docker. Ele define as etapas que o Docker deve seguir para empacotar a aplicação e suas dependências em uma imagem.
   - **Exemplo**:
     ```dockerfile
     FROM ubuntu:20.04
     RUN apt-get update && apt-get install -y python3
     COPY . /app
     CMD ["python3", "/app/app.py"]
     ```

4. **Docker Hub**:
   - **Definição**: Um registro de contêineres público onde os usuários podem armazenar e compartilhar imagens Docker. É como um repositório de código, mas para imagens Docker.
   - **Uso**: Os desenvolvedores podem puxar (pull) imagens pré-construídas do Docker Hub ou enviar (push) suas próprias imagens para compartilhar com a comunidade.

#### Benefícios do Docker

1. **Portabilidade**:
   - Contêineres Docker podem ser executados em qualquer lugar, desde o laptop de um desenvolvedor até servidores físicos, máquinas virtuais, na nuvem, e até mesmo em ambientes de produção.
   
2. **Eficiência de Recursos**:
   - Os contêineres compartilham o kernel do sistema operacional e usam recursos de maneira mais eficiente do que máquinas virtuais, permitindo uma melhor utilização dos recursos de hardware.

3. **Consistência e Reprodutibilidade**:
   - O uso de contêineres garante que a aplicação funcione da mesma forma em todos os ambientes, reduzindo problemas de inconsistência entre desenvolvimento, teste e produção.

4. **Isolamento**:
   - Contêineres fornecem isolamento entre diferentes aplicações e serviços, o que melhora a segurança e facilita a manutenção e a escalabilidade.

5. **Rapidez**:
   - Contêineres iniciam rapidamente em comparação com máquinas virtuais, pois não precisam inicializar um sistema operacional completo.

#### Casos de Uso

1. **Desenvolvimento e Teste**:
   - Facilita a criação de ambientes de desenvolvimento consistentes e reprodutíveis.
   
2. **Implementação Contínua**:
   - Integra-se bem com pipelines de CI/CD, permitindo que as equipes de desenvolvimento entreguem código de maneira mais rápida e confiável.

3. **Microserviços**:
   - Ideal para arquiteturas de microserviços, onde cada serviço pode ser executado em seu próprio contêiner, facilitando a escalabilidade e o gerenciamento.

4. **Migração para a Nuvem**:
   - Simplifica a movimentação de aplicações entre diferentes ambientes de nuvem.

Docker revolucionou a maneira como as aplicações são desenvolvidas, implantadas e executadas, proporcionando uma plataforma eficiente, portátil e confiável para a modernização dos processos de desenvolvimento e operações de TI.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Guia Completo para Instalação do Docker no Debian Linux

Para instalar o Docker no Debian Linux, você pode seguir os passos abaixo:

### Passo 1: Atualizar o Sistema

Abra o terminal e atualize o índice de pacotes do sistema:

```bash
sudo apt update
sudo apt upgrade
```

### Passo 2: Instalar Dependências

Instale os pacotes necessários para permitir o uso de repositórios sobre HTTPS:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### Passo 3: Adicionar o Repositório Docker

Adicione a chave GPG oficial do Docker:

```bash
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Adicione o repositório Docker ao seu sistema:

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Passo 4: Instalar o Docker

Atualize o índice de pacotes e instale o Docker:

```bash
sudo apt update
sudo apt install docker-ce
```

### Passo 5: Verificar a Instalação do Docker

Verifique se o Docker foi instalado corretamente executando:

```bash
sudo systemctl status docker
```

Você também pode verificar a versão do Docker instalada:

```bash
docker --version
```

### Passo 6: Adicionar Seu Usuário ao Grupo Docker

Para evitar a necessidade de usar `sudo` ao executar comandos Docker, adicione seu usuário ao grupo `docker`:

```bash
sudo usermod -aG docker $USER
```

Depois, saia e entre novamente na sua sessão para que as mudanças tenham efeito.

### Passo 7: Testar a Instalação do Docker

Teste se o Docker está funcionando corretamente executando o comando:

```bash
docker run hello-world
```

Se tudo estiver funcionando corretamente, você verá uma mensagem de confirmação informando que o Docker foi instalado com sucesso e está funcionando.

Pronto! O Docker deve estar instalado e funcionando no seu sistema Debian Linux.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Noções Básicas do Docker

#### O que é o Docker?
Docker é uma plataforma de código aberto projetada para automatizar a implantação de aplicações como contêineres portáteis e autossuficientes que podem ser executados em qualquer lugar.

#### Componentes Principais

1. **Docker Engine**:
   - **Definição**: O Docker Engine é o coração do Docker, responsável por criar, executar e gerenciar contêineres.
   - **Componentes**:
     - **Daemon (dockerd)**: O servidor que gerencia os contêineres, imagens, redes e volumes Docker.
     - **CLI (docker)**: A interface de linha de comando que os usuários interagem para executar comandos do Docker.
     - **API**: A interface de programação de aplicativos que permite a comunicação entre o daemon Docker e outras ferramentas.

2. **Imagens Docker**:
   - **Definição**: Imagens são arquivos de sistema de arquivos somente leitura que contêm tudo o que é necessário para executar uma aplicação, incluindo código, bibliotecas e dependências.
   - **Construção**: Criadas a partir de um Dockerfile e armazenadas no Docker Hub ou em registros privados.

3. **Contêineres Docker**:
   - **Definição**: Instâncias em execução de imagens Docker que isolam aplicações e suas dependências em um ambiente autossuficiente.
   - **Isolamento**: Cada contêiner possui seu próprio sistema de arquivos, rede, espaço de processo, e outros recursos do sistema.

4. **Dockerfile**:
   - **Definição**: Um script de texto que contém um conjunto de instruções para construir uma imagem Docker.
   - **Estrutura**:
     - **FROM**: Especifica a imagem base.
     - **RUN**: Executa comandos durante a construção da imagem.
     - **COPY/ADD**: Copia arquivos e diretórios para a imagem.
     - **CMD**: Especifica o comando padrão a ser executado quando um contêiner é iniciado.

5. **Docker Hub**:
   - **Definição**: Um repositório público onde as imagens Docker podem ser armazenadas, compartilhadas e distribuídas.
   - **Uso**: Puxar (pull) imagens públicas ou enviar (push) imagens personalizadas.

#### Comandos Básicos do Docker

1. **Instalar Docker**:
   - No Debian:
     ```bash
     sudo apt update
     sudo apt install docker-ce
     ```

2. **Iniciar o Docker**:
   - Iniciar o serviço Docker:
     ```bash
     sudo systemctl start docker
     ```
   - Habilitar o Docker para iniciar na inicialização do sistema:
     ```bash
     sudo systemctl enable docker
     ```

3. **Verificar a Instalação do Docker**:
   - Verificar a versão do Docker:
     ```bash
     docker --version
     ```
   - Executar um contêiner de teste:
     ```bash
     docker run hello-world
     ```

4. **Gerenciar Imagens**:
   - Listar imagens disponíveis:
     ```bash
     docker images
     ```
   - Baixar uma imagem do Docker Hub:
     ```bash
     docker pull <imagem>
     ```
   - Remover uma imagem:
     ```bash
     docker rmi <imagem>
     ```

5. **Gerenciar Contêineres**:
   - Listar contêineres em execução:
     ```bash
     docker ps
     ```
   - Listar todos os contêineres (incluindo os parados):
     ```bash
     docker ps -a
     ```
   - Iniciar um novo contêiner:
     ```bash
     docker run -it <imagem> /bin/bash
     ```
   - Parar um contêiner em execução:
     ```bash
     docker stop <container_id>
     ```
   - Remover um contêiner:
     ```bash
     docker rm <container_id>
     ```

6. **Usar Dockerfile para Criar uma Imagem**:
   - Criar uma imagem a partir de um Dockerfile:
     ```bash
     docker build -t <nome_imagem> .
     ```

7. **Executar Comandos em um Contêiner em Execução**:
   - Executar um comando em um contêiner em execução:
     ```bash
     docker exec -it <container_id> <comando>
     ```

#### Exemplo de Dockerfile

```dockerfile
# Usar uma imagem base oficial do Python
FROM python:3.8-slim

# Definir o diretório de trabalho dentro do contêiner
WORKDIR /app

# Copiar os arquivos do projeto para o contêiner
COPY . /app

# Instalar as dependências necessárias
RUN pip install --no-cache-dir -r requirements.txt

# Especificar o comando padrão a ser executado
CMD ["python", "app.py"]
```

#### Vantagens do Docker

1. **Portabilidade**: Contêineres podem ser executados em qualquer ambiente que suporte Docker, garantindo que a aplicação funcione da mesma forma em diferentes ambientes.
2. **Eficiência**: Contêineres compartilham o kernel do sistema operacional, utilizando recursos de maneira mais eficiente do que máquinas virtuais.
3. **Isolamento**: Aplicações e suas dependências são isoladas em contêineres, reduzindo conflitos entre pacotes e bibliotecas.
4. **Escalabilidade**: Facilita a escalabilidade de aplicações, permitindo o gerenciamento de várias instâncias de contêineres de maneira simplificada.

Docker é uma ferramenta poderosa que está revolucionando a forma como desenvolvedores e operadores de TI criam, distribuem e executam aplicações. Compreender suas noções básicas é fundamental para aproveitar todo o potencial dessa tecnologia.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

