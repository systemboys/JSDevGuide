> ## Docker
>
> ![Docker](./images/docker.png)

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Visão Geral do Docker](#vis%C3%A3o-geral-do-docker "Visão Geral do Docker")
> - [Docker Hub: A Plataforma Central de Distribuição e Gestão de Imagens Docker](#docker-hub-a-plataforma-central-de-distribui%C3%A7%C3%A3o-e-gest%C3%A3o-de-imagens-docker "Docker Hub: A Plataforma Central de Distribuição e Gestão de Imagens Docker")
> - [Guia Completo para Instalação do Docker no Debian Linux](#guia-completo-para-instala%C3%A7%C3%A3o-do-docker-no-debian-linux "Guia Completo para Instalação do Docker no Debian Linux")
> - [Noções básicas do Docker](#no%C3%A7%C3%B5es-b%C3%A1sicas-do-docker "Noções básicas do Docker")
> - [Docker Compose](./DockerCompose/README.md#docker-compose "Docker Compose")
> - [Comparação entre Virtualização com Hypervisor e Containerização com Docker: Eficiência e Utilização de Recursos](#compara%C3%A7%C3%A3o-entre-virtualiza%C3%A7%C3%A3o-com-hypervisor-e-containeriza%C3%A7%C3%A3o-com-docker-efici%C3%AAncia-e-utiliza%C3%A7%C3%A3o-de-recursos "Comparação entre Virtualização com Hypervisor e Containerização com Docker: Eficiência e Utilização de Recursos")

----

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

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

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

## Docker Hub: A Plataforma Central de Distribuição e Gestão de Imagens Docker

O **Docker Hub** é uma plataforma de registro central para imagens Docker, onde os desenvolvedores podem encontrar, compartilhar e armazenar essas imagens. É uma ferramenta essencial dentro do ecossistema Docker, que facilita o gerenciamento de imagens prontas para execução em containers. Aqui estão os principais aspectos do Docker Hub:

### Funcionalidades principais do Docker Hub:
1. **Repositórios de Imagens**:
   - O Docker Hub armazena imagens Docker em **repositórios**. Esses repositórios podem ser públicos ou privados. Repositórios públicos são acessíveis por qualquer pessoa, enquanto os privados são visíveis apenas para usuários autorizados.
   
2. **Imagens Oficiais e da Comunidade**:
   - O Docker Hub oferece uma vasta gama de **imagens oficiais** mantidas por empresas e pela própria equipe do Docker, como o Ubuntu, MySQL, Nginx, entre outras. Além disso, há imagens disponibilizadas por **contribuidores da comunidade**, que podem ser reutilizadas e customizadas.
   
3. **Push e Pull de Imagens**:
   - Você pode **fazer upload** ("push") de suas imagens locais para o Docker Hub para torná-las disponíveis em qualquer ambiente. Da mesma forma, é possível **fazer download** ("pull") de imagens já existentes no Docker Hub, para usá-las localmente ou em outros ambientes.

4. **Integração com CI/CD**:
   - O Docker Hub pode ser integrado a **pipelines de CI/CD (Continuous Integration/Continuous Deployment)**, permitindo o uso automatizado de imagens para testes e deploys em containers.

5. **Automated Builds**:
   - Oferece a funcionalidade de **builds automáticos**, onde uma imagem Docker é criada automaticamente a partir de um repositório de código fonte (como GitHub ou Bitbucket) e disponibilizada no Docker Hub.

### Vantagens do Docker Hub:
- **Distribuição fácil**: Permite que você compartilhe imagens rapidamente entre desenvolvedores e ambientes de produção.
- **Versatilidade**: Armazena tanto imagens para projetos simples quanto complexos, facilitando o desenvolvimento e a implantação de software em diversos ambientes.
- **Escalabilidade**: A utilização de imagens Docker a partir do Docker Hub garante consistência e portabilidade, o que é essencial em ambientes de produção escaláveis.

### Exemplo de uso:
- Quando você deseja executar um banco de dados MySQL, pode simplesmente executar o comando:
  ```bash
  docker pull mysql
  ```
  Isso irá baixar a imagem oficial do MySQL do Docker Hub, e você pode iniciar um container a partir dessa imagem.

Em resumo, o Docker Hub é uma plataforma fundamental para o uso eficiente de containers, permitindo o fácil compartilhamento e gerenciamento de imagens Docker.

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

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

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

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

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

### Comparação entre Virtualização com Hypervisor e Containerização com Docker: Eficiência e Utilização de Recursos

A imagem abaixo está comparando a virtualização tradicional com máquinas virtuais (VM) usando um "Hypervisor", e a containerização usando "Docker".

![](../images/Hypervisor_And_Containerization.png)

**Diferença entre Hypervisor e Docker:**

1. **Hypervisor**:
   - O Hypervisor é o software que permite que múltiplos sistemas operacionais (VMs) rodem em uma única máquina física. Ele abstrai o hardware da máquina física para que várias máquinas virtuais (VMs) possam compartilhar os recursos da máquina hospedeira.
   - Cada VM tem seu próprio sistema operacional completo, suas próprias bibliotecas, bins e aplicativos.
   - Exemplo: Você pode ter uma VM rodando **Debian** e outra rodando **Ubuntu**, cada uma com seus próprios recursos.
   - **O que utiliza da máquina hospedeira**: O Hypervisor interage diretamente com o hardware da máquina física, como CPU, memória e armazenamento, e aloca esses recursos para cada máquina virtual.

2. **Docker**:
   - O Docker, por outro lado, é uma plataforma de containers que compartilha o mesmo sistema operacional (kernel) da máquina hospedeira, mas isola os aplicativos em containers independentes. Cada container inclui apenas o necessário para rodar o aplicativo, como bins e bibliotecas, mas sem um sistema operacional completo, ao contrário das VMs.
   - Isso faz com que os containers sejam mais leves do que as VMs, pois todos os containers compartilham o mesmo kernel do SO da máquina hospedeira.
   - **O que utiliza da máquina hospedeira**: O Docker usa o sistema operacional da máquina hospedeira, incluindo o kernel, enquanto isola os aplicativos e suas dependências no nível de container. Ele não cria máquinas virtuais completas, apenas ambientes isolados para os aplicativos.

**Resumindo**:
- **Hypervisor**: cria e gerencia VMs, cada uma com seu próprio SO completo. Usa mais recursos, pois cada VM precisa de seu próprio SO.
- **Docker**: usa containers que compartilham o kernel do SO da máquina hospedeira. Containers são mais leves, pois não precisam de um SO completo.

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

