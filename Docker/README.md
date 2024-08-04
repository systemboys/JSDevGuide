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

