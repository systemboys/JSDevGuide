> ## Docker
>
> ![Docker](./images/docker.png)

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*

> - [Docker Overview](#docker-overview "Docker Overview")
> - [Docker Installation](#docker-installation "Docker Installation")
> - [Docker Basics](#docker-basics "Docker Basics")
>   - [Docker Compose](./DockerCompose/README.md#docker-compose "Docker Compose")

----

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

Content...

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

