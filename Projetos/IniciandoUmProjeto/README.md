> ## Iniciando um projeto
>
> ![Docker](./images/StartingAProject.png)

> ### *Summary*

> - [Configuração inicial](#configuração-inicial)
> - [Estrutura de pastas](#estrutura-de-pastas)
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

    > ```tex
    > /myProject/
    > ├─ /src/
    > │  ├─ /controllers/
    > │  ├─ /repositories/
    > │  ├─ /routes/
    > │  ├─ /services/
    > │  └─ index.ts
    > └─ package.json
    > ```

[![Início](../../imges/control/11273_control_stop_icon.png?raw=true "Início")](../../README.md#jsdevguide "Início")
[![Voltar](../../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

