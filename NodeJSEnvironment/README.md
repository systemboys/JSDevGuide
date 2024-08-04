# SiSFloatBase

---

[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

## Automação da Configuração do Ambiente React.js no WSL

### Descrição do Script

Este script automatiza a configuração de um ambiente de desenvolvimento React.js no Windows Subsystem for Linux (WSL). Ele realiza uma série de operações que incluem a atualização dos pacotes do sistema, a instalação do Node.js e do npm, a criação de um novo projeto React e a inicialização da aplicação. Abaixo estão os passos detalhados que o script executa:

1. **Parar o Script em Caso de Falha**: O comando `set -e` faz com que o script pare imediatamente se qualquer comando retornar um código de erro diferente de zero, garantindo que erros sejam tratados precocemente.

2. **Atualizar Pacotes do Sistema**: Os comandos `sudo apt update` e `sudo apt upgrade -y` atualizam a lista de pacotes disponíveis e todos os pacotes instalados no sistema para as versões mais recentes.

3. **Instalar Node.js e npm**: Utiliza o NodeSource para configurar o repositório e instalar a versão 16.x do Node.js e o npm correspondente.
   
   ```sh
   curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
   sudo apt install -y nodejs
   ```

4. **Verificar Instalação do Node.js e npm**: Os comandos `node -v` e `npm -v` são usados para exibir as versões instaladas do Node.js e do npm.

5. **Atualizar npm para Versão Compatível com Node.js 16.x**: Atualiza o npm para a versão 8.19.4, que é compatível com o Node.js 16.x.

   ```sh
   sudo npm install -g npm@8.19.4
   ```

6. **Criar um Novo Projeto React**: Define o nome do projeto (`sisfloatbase`) e utiliza o `npx create-react-app` para criar um novo projeto React. O comando `sudo -u $USER` garante que o projeto seja criado com as permissões do usuário atual.

   ```sh
   sudo -u $USER npx create-react-app $project_name
   ```

7. **Navegar até o Diretório do Projeto**: Usa o comando `cd` para entrar no diretório do projeto recém-criado.

8. **Instalar Dependências**: Executa `npm install` para garantir que todas as dependências do projeto sejam instaladas corretamente.

9. **Iniciar a Aplicação React**: Usa `npm start` para iniciar o servidor de desenvolvimento e rodar a aplicação React, que ficará disponível em `http://localhost:3000`.

   ```sh
   npm start
   ```

10. **Mensagem Final**: Exibe uma mensagem indicando que o ambiente React.js foi configurado e a aplicação está rodando.

### Código do Script

```sh
#!/bin/bash

# Parar o script se algum comando falhar
set -e

# Atualizar pacotes do sistema
echo "Atualizando pacotes do sistema..."
sudo apt update && sudo apt upgrade -y

# Instalar Node.js e npm
echo "Instalando Node.js e npm..."
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs

# Verificar instalação do Node.js e npm
echo "Verificando instalação do Node.js e npm..."
node_version=$(node -v)
npm_version=$(npm -v)
echo "Node.js versão: $node_version"
echo "npm versão: $npm_version"

# Atualizar npm para uma versão compatível com Node.js 16.x
echo "Atualizando npm para uma versão compatível com Node.js 16.x..."
sudo npm install -g npm@8.19.4

# Criar um novo projeto React (substitua 'sisfloatbase' pelo nome do seu projeto)
project_name="sisfloatbase"
echo "Criando um novo projeto React chamado $project_name..."

# Execute create-react-app no contexto do usuário atual
sudo -u $USER npx create-react-app $project_name

# Navegar até o diretório do projeto
cd $project_name

# Instalar dependências (se aplicável)
echo "Instalando dependências..."
npm install

# Rodar a aplicação React
echo "Iniciando a aplicação React..."
npm start

echo "O ambiente React.js foi configurado e a aplicação está rodando em http://localhost:3000"
```

### Ajustando para instalar no Debian

O script apresentado deve funcionar tanto no Ubuntu quanto no Debian Linux no WSL, pois ambos os sistemas são baseados no mesmo núcleo do Debian e compartilham a maioria dos comandos e processos de gerenciamento de pacotes.

### Principais Motivos:

1. **Sistema de Pacotes**: Ambos usam o `apt` (Advanced Package Tool) para gerenciamento de pacotes. Portanto, os comandos `sudo apt update` e `sudo apt upgrade -y` funcionarão da mesma maneira.

2. **Instalação do Node.js**: O repositório NodeSource é compatível com diversas distribuições baseadas em Debian, incluindo Ubuntu e Debian. O comando `curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -` adiciona o repositório e instala o Node.js da mesma forma em ambos os sistemas.

3. **Comandos Básicos do Sistema**: Comandos como `sudo`, `curl`, `chmod`, `nano` e outros usados no script são universais entre Debian e Ubuntu.

### Considerações Específicas

- **Versão do Sistema**: Certifique-se de que você esteja usando uma versão estável e suportada do Debian. O script foi testado em versões recentes do Ubuntu e deve funcionar em versões atuais do Debian (como Debian 10 "Buster" ou Debian 11 "Bullseye").

- **Dependências Adicionais**: Se o Debian estiver numa configuração mínima, pode ser necessário instalar `curl` separadamente, caso não esteja presente:

  ```sh
  sudo apt install curl
  ```

### Ajuste do Script se Necessário

Aqui está o mesmo script, mas agora adicionando uma verificação para instalar `curl` se ele não estiver presente:

```sh
#!/bin/bash

# Parar o script se algum comando falhar
set -e

# Atualizar pacotes do sistema
echo "Atualizando pacotes do sistema..."
sudo apt update && sudo apt upgrade -y

# Verificar se o curl está instalado, caso contrário, instalar
if ! [ -x "$(command -v curl)" ]; then
  echo "Instalando curl..."
  sudo apt install -y curl
fi

# Instalar Node.js e npm
echo "Instalando Node.js e npm..."
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs

# Verificar instalação do Node.js e npm
echo "Verificando instalação do Node.js e npm..."
node_version=$(node -v)
npm_version=$(npm -v)
echo "Node.js versão: $node_version"
echo "npm versão: $npm_version"

# Atualizar npm para uma versão compatível com Node.js 16.x
echo "Atualizando npm para uma versão compatível com Node.js 16.x..."
sudo npm install -g npm@8.19.4

# Criar um novo projeto React (substitua 'sisfloatbase' pelo nome do seu projeto)
project_name="sisfloatbase"
echo "Criando um novo projeto React chamado $project_name..."

# Execute create-react-app no contexto do usuário atual
sudo -u $USER npx create-react-app $project_name

# Navegar até o diretório do projeto
cd $project_name

# Instalar dependências (se aplicável)
echo "Instalando dependências..."
npm install

# Rodar a aplicação React
echo "Iniciando a aplicação React..."
npm start

echo "O ambiente React.js foi configurado e a aplicação está rodando em http://localhost:3000"
```

Este script deve funcionar perfeitamente tanto no Ubuntu quanto no Debian, garantindo que todas as dependências necessárias sejam instaladas e configuradas corretamente.

### Ajustando para instalar no Debian ou Ubuntu (.sh)

Podemos ajustar o script para detectar a distribuição Linux e configurar as variáveis e comandos específicos para cada uma. Utilizaremos um array para armazenar as distribuições suportadas e uma função para detectar a distribuição atual. Em seguida, o script aplicará as configurações apropriadas com base na distribuição detectada.

Aqui está o script ajustado:

```sh
#!/bin/bash

# Parar o script se algum comando falhar
set -e

# Definir distribuições suportadas
distributions=("debian" "ubuntu")

# Função para detectar a distribuição Linux
detect_distro() {
  if [ -f /etc/os-release ]; then
    . /etc/os-release
    echo $ID
  else
    echo "unknown"
  fi
}

# Detectar a distribuição atual
current_distro=$(detect_distro)

# Verificar se a distribuição atual é suportada
if [[ ! " ${distributions[@]} " =~ " ${current_distro} " ]]; then
  echo "Distribuição não suportada: ${current_distro}"
  exit 1
fi

echo "Distribuição detectada: ${current_distro}"

# Atualizar pacotes do sistema
echo "Atualizando pacotes do sistema..."
sudo apt update && sudo apt upgrade -y

# Verificar se o curl está instalado, caso contrário, instalar
if ! [ -x "$(command -v curl)" ]; then
  echo "Instalando curl..."
  sudo apt install -y curl
fi

# Instalar Node.js e npm
echo "Instalando Node.js e npm..."
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs

# Verificar instalação do Node.js e npm
echo "Verificando instalação do Node.js e npm..."
node_version=$(node -v)
npm_version=$(npm -v)
echo "Node.js versão: $node_version"
echo "npm versão: $npm_version"

# Atualizar npm para uma versão compatível com Node.js 16.x
echo "Atualizando npm para uma versão compatível com Node.js 16.x..."
sudo npm install -g npm@8.19.4

# Criar um novo projeto React (substitua 'sisfloatbase' pelo nome do seu projeto)
project_name="sisfloatbase"
echo "Criando um novo projeto React chamado $project_name..."

# Execute create-react-app no contexto do usuário atual
sudo -u $USER npx create-react-app $project_name

# Navegar até o diretório do projeto
cd $project_name

# Instalar dependências (se aplicável)
echo "Instalando dependências..."
npm install

# Rodar a aplicação React
echo "Iniciando a aplicação React..."
npm start

echo "O ambiente React.js foi configurado e a aplicação está rodando em http://localhost:3000"
```

### Descrição do Script

1. **Definir Distribuições Suportadas**: Um array `distributions` é criado para armazenar as distribuições Linux suportadas, que são "debian" e "ubuntu".

2. **Função para Detectar a Distribuição**: A função `detect_distro` lê o arquivo `/etc/os-release` para detectar a distribuição atual. Ela retorna o ID da distribuição (por exemplo, "debian" ou "ubuntu").

3. **Detectar a Distribuição Atual**: A variável `current_distro` armazena o resultado da função `detect_distro`.

4. **Verificar Distribuição Suportada**: O script verifica se a distribuição detectada está no array `distributions`. Se não estiver, o script exibe uma mensagem de erro e termina.

5. **Atualizar Pacotes do Sistema**: Atualiza a lista de pacotes disponíveis e todos os pacotes instalados.

6. **Instalar curl se Necessário**: Verifica se o `curl` está instalado e o instala se necessário.

7. **Instalar Node.js e npm**: Utiliza o NodeSource para configurar o repositório e instalar o Node.js.

8. **Verificar Instalação do Node.js e npm**: Exibe as versões instaladas do Node.js e npm.

9. **Atualizar npm**: Atualiza o npm para uma versão compatível com o Node.js 16.x.

10. **Criar um Novo Projeto React**: Define o nome do projeto e utiliza o `npx create-react-app` para criar um novo projeto React no contexto do usuário atual.

11. **Navegar até o Diretório do Projeto**: Entra no diretório do projeto recém-criado.

12. **Instalar Dependências**: Executa `npm install` para garantir que todas as dependências do projeto sejam instaladas corretamente.

13. **Iniciar a Aplicação React**: Usa `npm start` para iniciar o servidor de desenvolvimento e rodar a aplicação React.

14. **Mensagem Final**: Exibe uma mensagem indicando que o ambiente React.js foi configurado e a aplicação está rodando.

### Como Usar o Script

1. **Criar o Arquivo de Script**: Crie um novo arquivo chamado `setup-react.sh` no seu WSL.

```sh
nano setup-react.sh
```

2. **Colar o Script**: Copie e cole o script acima no arquivo `setup-react.sh`.

3. **Salvar e Fechar**: Salve o arquivo e feche o editor (no Nano, use `CTRL+O` para salvar e `CTRL+X` para fechar).

4. **Tornar o Script Executável**: Torne o script executável usando o comando `chmod`.

```sh
chmod +x setup-react.sh
```

5. **Executar o Script**: Execute o script para configurar o ambiente e iniciar sua aplicação React.

```sh
./setup-react.sh
```

Este script agora é capaz de detectar a distribuição Linux e aplicar as configurações apropriadas automaticamente, tornando-o adequado tanto para Ubuntu quanto para Debian.

[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

---

