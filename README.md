# JSDevGuide

![Capa](./imges/843ccc85-f4b9-4c45-b902-23555e497d1c.png)

Um guia abrangente para desenvolvedores JavaScript e TypeScript, cobrindo Node.JS, React.JS, Next.JS, Docker e outras tecnologias essenciais. Encontre instruções detalhadas, dicas práticas e exemplos de código para aprimorar suas habilidades de programação.

## Sumário

- [Docker](#docker)
    - [Docker Compose](#docker-compose)
- [Projetos](#projetos)
    - [Iniciando um projeto](#iniciando-um-projeto)
    - [Criando API com TypeScript](#criando-api-com-typescript)
    - [ORM Prisma](#orm-prisma)
        - [CRUD - Create, Read, Update e Delete](#crud---create-read-update-e-delete)
    - [Rotas](#rotas)
- [Conceitos Básicos](#conceitos-b%C3%A1sicos)
    - [Funções](#funções)
    - [Arrays](#arrays)
- [Componentes](#componentes)
- [Frameworks](#frameworks)
- [Bibliotecas](#bibliotecas)

---

> ## Docker
>
> - [Docker Overview](#docker-overview)
> - [Docker Installation](#docker-installation)
> - [Docker Basics](#docker-basics)

> ## Docker Compose
>
> - [Compose Overview](#compose-overview)
> - [Compose Installation](#compose-installation)
> - [Compose Usage](#compose-usage)

> ### Projetos
>
> - [Iniciando um projeto](#iniciando-um-projeto)
> - [Criando API com TypeScript](#criando-api-com-typescript)
> - [ORM Prisma](#orm-prisma)

> ### Iniciando um projeto
>
> - [Configuração inicial](#configuração-inicial)
> - [Estrutura de pastas](#estrutura-de-pastas)
> - [Configuração do TypeScript](#configuração-do-typescript)

> ### Criando API com TypeScript
>
> - [Configuração do ambiente](#configuração-do-ambiente)
> - [Definição de rotas](#definição-de-rotas)
> - [Integração com banco de dados](#integração-com-banco-de-dados)

> ### ORM Prisma
>
> - [Instalação do Prisma](#instalação-do-prisma)
> - [Definição de modelos](#definição-de-modelos)
> - [Execução de consultas](#execução-de-consultas)
> - [Controllers](#controllers)

> #### CRUD - Create, Read, Update e Delete
>
> - [Create](#create)
> - [Read](#read)
> - [Update](#update)
> - [Delete](#delete)

> ### Rotas
>
> - [Definição de rotas](#definição-de-rotas)
> - [Middleware](#middleware)
> - [Autenticação](#autenticação)

> ## Conceitos Básicos

> ### Funções
>
> - [Funções básicas](#funções-básicas)
> - [Funções avançadas](#funções-avançadas)

> ### Arrays
>
> - [Manipulação de arrays](#manipulação-de-arrays)
> - [Iteração de arrays](#iteração-de-arrays)

> ## Componentes
>
> - [Componentes básicos](#componentes-básicos)
> - [Componentes avançados](#componentes-avançados)

> ## Frameworks
>
> - [Next.js](#nextjs)
> - [Gatsby](#gatsby)
> - [React Router](#react-router)
> - [Material-UI](#material-ui)
> - [Chakra UI](#chakra-ui)
> - [Ant Design](#ant-design)
> - [Bootstrap](#bootstrap)
> - [Tailwind CSS](#tailwind-css)
> - [Styled Components](#styled-components)
> - [Redux](#redux)

> ## Bibliotecas
>
> - [Axios](#axios)
> - [React-Redux](#react-redux)
> - [Formik](#formik)
> - [Yup](#yup)
> - [React Hook Form](#react-hook-form)
> - [React Query](#react-query)
> - [React Router](#react-router)
> - [React Helmet](#react-helmet)
> - [React Icons](#react-icons)
> - [React-Bootstrap](#react-bootstrap)

> ## Controllers
>
> Os controllers no contexto do ORM Prisma são responsáveis por gerenciar a lógica de negócio da sua aplicação, principalmente em operações que envolvem a manipulação e interação com o banco de dados. Eles são responsáveis por receber requisições, processar os dados necessários e retornar as respostas apropriadas. Aqui estão algumas práticas recomendadas para trabalhar com controllers no contexto do Prisma:
> 
> - Organize seus controllers de forma a separar as responsabilidades da aplicação, por exemplo, criando controllers diferentes para cada recurso da sua API (usuários, posts, comentários, etc.).
> - Mantenha seus controllers o mais simples e coesos possível, evitando funções muito extensas ou com múltiplas responsabilidades.
> - Utilize serviços adicionais, se necessário, para abstrair a lógica de negócio mais complexa e manter seus controllers mais limpos e fáceis de dar manutenção.
