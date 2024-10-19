> ## Gerenciamento de Variáveis de Ambiente no React
>
> ![Descrição da imagem](./images/image.png)

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*
>
> - [Como utilizar o arquivo `.env` no React.js](#como-utilizar-o-arquivo-env-no-reactjs "Como utilizar o arquivo `.env` no React.js")

## Como utilizar o arquivo `.env` no React.js

No **React.js**, o arquivo `.env` é usado para definir variáveis de ambiente que podem ser acessadas no código da aplicação. Isso é especialmente útil para armazenar configurações ou dados sensíveis que não devem ser codificados diretamente no código-fonte, como URLs de APIs, chaves de API e outras configurações que podem variar entre os ambientes de desenvolvimento, teste e produção.

### Como usar o arquivo `.env` no React:

1. **Criação do arquivo `.env`**:
   - Na raiz do seu projeto **React**, crie um arquivo chamado `.env`. Exemplo:
     ```
     .env
     ```

2. **Prefixo obrigatório: `REACT_APP_`**:
   - Em **React.js**, todas as variáveis de ambiente devem começar com o prefixo **`REACT_APP_`**. Se você não usar esse prefixo, as variáveis não estarão disponíveis no código.
   - Exemplo de variáveis no arquivo `.env`:
     ```bash
     REACT_APP_API_URL=http://localhost:3333
     REACT_APP_GOOGLE_MAPS_API_KEY=your-google-maps-key
     REACT_APP_ENVIRONMENT=development
     ```

3. **Acessando as variáveis no código**:
   - Para acessar as variáveis de ambiente no código React, você usa o objeto `process.env`.
   - Exemplo:
     ```jsx
     const apiUrl = process.env.REACT_APP_API_URL;
     console.log('API URL:', apiUrl); // Irá mostrar: http://localhost:3333

     const googleMapsKey = process.env.REACT_APP_GOOGLE_MAPS_API_KEY;
     console.log('Google Maps Key:', googleMapsKey);
     ```

4. **Processamento das variáveis**:
   - As variáveis de ambiente definidas no arquivo `.env` são "injetadas" no código durante o **build** (compilação) da aplicação. Isso significa que as variáveis são acessadas no código de produção, mas seus valores serão "embutidos" no código final. Ou seja, elas não mudam dinamicamente depois que a aplicação React é compilada.

5. **Cuidados com a segurança**:
   - **Importante**: Como o React é uma aplicação frontend, **todas as variáveis de ambiente definidas no `.env` são visíveis no código do navegador**. Ou seja, **não coloque informações sensíveis**, como senhas, chaves privadas, ou dados confidenciais, no arquivo `.env` do React, pois elas estarão expostas para quem inspecionar o código da aplicação no navegador.
   - Se você precisa proteger dados sensíveis, faça isso no backend.

### Exemplo prático de uso no React:

1. **Arquivo `.env`**:
   ```bash
   REACT_APP_API_URL=http://localhost:3333
   REACT_APP_APP_NAME=SiS Float Base
   ```

2. **Usando no código React**:
   ```jsx
   import React from 'react';

   function App() {
     const apiUrl = process.env.REACT_APP_API_URL;
     const appName = process.env.REACT_APP_APP_NAME;

     return (
       <div>
         <h1>Bem-vindo ao {appName}!</h1>
         <p>A API está rodando em: {apiUrl}</p>
       </div>
     );
   }

   export default App;
   ```

3. **Executando a aplicação**:
   - Quando você executar sua aplicação com `npm start`, ou durante o build com `npm run build`, as variáveis do arquivo `.env` serão injetadas e substituídas no código.

### Outras dicas:

- **Múltiplos arquivos `.env`**:
  - Você pode criar diferentes arquivos `.env` para cada ambiente. O React suporta automaticamente arquivos como:
    - `.env.development`: para o ambiente de desenvolvimento.
    - `.env.production`: para o ambiente de produção.
    - `.env.test`: para o ambiente de testes.
  
  Exemplo:
  - `.env.development`:
    ```bash
    REACT_APP_API_URL=http://localhost:3333
    REACT_APP_ENVIRONMENT=development
    ```
  
  - `.env.production`:
    ```bash
    REACT_APP_API_URL=https://api.example.com
    REACT_APP_ENVIRONMENT=production
    ```

- **Reinicie o servidor**:
  - Sempre que você modificar o arquivo `.env`, é necessário reiniciar o servidor de desenvolvimento para que as novas variáveis sejam aplicadas.

[![Início](../images/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../images/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../images/control/11280_control_up_icon.png "Subir")](#summary "Subir")

---

