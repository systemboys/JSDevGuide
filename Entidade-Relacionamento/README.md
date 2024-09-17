> ## Símbolos e notação do diagrama de Entidade-Relacionamento
>
> ![img](./images/68747470733a2f2f636f72706f726174652d6173736574732e6c756369642e636f2f63686172742f32663263626436312d62.png)

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")

> ### *Summary*
>
> - [Símbolos de diagrama ER conceitual](#s%C3%ADmbolos-de-diagrama-er-conceitual "Símbolos de diagrama ER conceitual")
> 	- [Símbolos de entidade ERD](#s%C3%ADmbolos-de-entidade-erd "Símbolos de entidade ERD")
> 	- [Símbolos de relacionamento ERD](#s%C3%ADmbolos-de-relacionamento-erd "Símbolos de relacionamento ERD")
> 	- [Símbolos de atributo ERD](#s%C3%ADmbolos-de-atributo-erd "Símbolos de atributo ERD")
> - [Símbolos do diagrama ER físico](#s%C3%ADmbolos-do-diagrama-er-f%C3%ADsico "Símbolos do diagrama ER físico")
> 	- [Campos](#campos "Campos")
> 	- [Chaves](#chaves "Chaves")
> 		- [Chaves primárias](#chaves-prim%C3%A1rias "Chaves primárias")
> 		- [Chaves estrangeiras](#chaves-estrangeiras "Chaves estrangeiras")
> 	- [Tipos de](#tipos-de "Tipos de")
> - [Diagrama de RE notação](#diagrama-de-re-nota%C3%A7%C3%A3o "Diagrama de RE notação")
> 	- [A Cardinalidade e a ordinalidade](#a-cardinalidade-e-a-ordinalidade "A Cardinalidade e a ordinalidade")
>  - [Exemplos de código para construir bancos de dados relacionados](#exemplos-de-c%C3%B3digo-para-construir-bancos-de-dados-relacionados "Exemplos de código para construir bancos de dados relacionados")
>     - [Modelagem de Relacionamento Um-para-Muitos entre Estados e Cidades em Banco de Dados Relacional](#modelagem-de-relacionamento-um-para-muitos-entre-estados-e-cidades-em-banco-de-dados-relacional "Modelagem de Relacionamento Um-para-Muitos entre Estados e Cidades em Banco de Dados Relacional")
>     - [Alteração de Tabelas para Adicionar Chave Estrangeira e Estabelecer Relacionamento entre Entidades em Banco de Dados](#altera%C3%A7%C3%A3o-de-tabelas-para-adicionar-chave-estrangeira-e-estabelecer-relacionamento-entre-entidades-em-banco-de-dados "Alteração de Tabelas para Adicionar Chave Estrangeira e Estabelecer Relacionamento entre Entidades em Banco de Dados")

## Símbolos de diagrama ER conceitual

Os modelos de dados conceituais estabelecem uma visão ampla do que deve  ser incluído no conjunto de modelos. ERDs conceituais podem ser usados  como base para modelos de dados lógicos. Eles também podem ser usados  para formar relações de comunalidade entre modelos de emergência como  base para a integração do modelo de dados. Todos os símbolos mostrados  abaixo são encontrados na biblioteca de forma de Relacionamento de  Entidade e Entidade Relacionamento de Lucidchart.

### Símbolos de entidade ERD

Entidades são objetos ou conceitos que representam dados importantes. As entidades são tipicamente substantivos, como produto, cliente,  localização ou promoção. Existem três tipos de entidades comumente  usadas em diagramas de relacionamento de entidade.

| Símbolo da Entidade                                          | Nome                 | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | -------------------- | ------------------------------------------------------------ |
| ![Símbolo de Entidade Forte](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f456e746974792e504e47.png) | Uma entidade forte   | Essas formas são independentes de outras entidades e são  frequentemente chamadas de entidades-mãe, uma vez que muitas vezes têm  entidades fracas que dependem delas. Eles também terão uma chave  primária, distinguindo cada ocorrência da entidade. |
| ![Símbolo de Entidade Fraca](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f5765616b456e746974792e504e47.png) | Entidade fraca       | As entidades fracas dependem de outro tipo de entidade. Eles não  têm chaves primárias e não têm significado no diagrama sem sua entidade  controladora. |
| ![Símbolo da entidade associativa](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4173736f63696174697665456e746974792e504e47.png) | Entidade associativa | As entidades associativas  relacionam as instâncias de vários tipos de entidades. Eles também  contêm atributos específicos para a relação entre essas instâncias de  entidade. |

### Símbolos de relacionamento ERD

Dentro dos diagramas de relacionamento de entidades, as relações são  usadas para documentar a interação entre duas entidades. Relacionamentos geralmente são verbos como atribuir, associar ou rastrear e fornecer  informações úteis que não podem ser discernidas apenas com os tipos de  entidade.

| Símbolo do relacionamento                                    | Nome          | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | ------------- | ------------------------------------------------------------ |
| ![Símbolo do relacionamento](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f52656c6174696f6e7368697053686170652e504e47.png) | Relação       | Relacionamentos são associações entre ou entre entidades.    |
| ![Símbolo de relacionamento fraca](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f5765616b52656c6174696f6e736869702e504e47.png) | Relação fraca | Relacionamentos fracos são conexões entre uma entidade fraca e seu dono. |

### Símbolos de atributo ERD

Os atributos ERD são características da entidade que ajudam os  usuários a entender melhor o banco de dados. Os atributos são incluídos  para incluir detalhes das várias entidades que são destacadas em um  diagrama conceitual.

| Símbolo de atributo                                          | Nome                     | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | ------------------------ | ------------------------------------------------------------ |
| ![Símbolo de atributo](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4174747269627574652e504e47.png) | Atributo                 | Os atributos são características de uma entidade, um relacionamento de muitos para muitos ou um relacionamento individual. |
| ![Símbolo de Atributo Multivalorizado](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4d756c746976616c7565644174747269627574652e504e47.png) | Atributo multivalorizado | Atributos multivalorizados são aqueles que podem assumir mais de um valor. |
| ![Símbolo de Atributo Derido](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f446572697665644174747269627574652e504e47.png) | Atributo derramado       | Os atributos derivados são atributos cujo valor pode ser calculado a partir de valores de atributos relacionados. |
| ![Símbolo do relacionamento](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f52656c6174696f6e7368697053686170652e504e47.png) | Relação                  | Relacionamentos são associações entre ou entre entidades.    |

## Símbolos do diagrama ER físico

O modelo de dados físicos é o nível mais granular de diagramas de  relacionamento de entidade e representa o processo de adição de  informações ao banco de dados. Os modelos ER físicos mostram todas as  estruturas da tabela, incluindo o nome da coluna, o tipo de dados da  coluna, as restrições da coluna, a chave primária, a chave estrangeira e as relações entre tabelas.

Como mostrado abaixo, as tabelas são outra maneira de representar  entidades. As partes principais das tabelas de entidades-relacionamento  são:

### Campos

Os campos representam a parte de uma tabela que estabelece os  atributos da entidade. Os atributos são tipicamente pensados como  colunas no banco de dados que o ERD modela.

![Forma dos Campos](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4669656c642e504e47.png)

Na imagem acima, InterestRate e LoanAmount são ambos atributos da entidade que estão contidas como campos.

### Chaves

As chaves são uma maneira de categorizar atributos. Os diagramas de  ER ajudam os usuários a modelar seus bancos de dados usando várias  tabelas que garantem que o banco de dados seja organizado, eficiente e  rápido. As chaves são usadas para vincular várias tabelas em um banco de dados umas às outras da maneira mais eficiente possível.

#### Chaves primárias

As chaves primárias são um atributo ou combinação de atributos que  identificam exclusivamente uma e apenas uma instância de uma entidade.

#### Chaves estrangeiras

Chaves estrangeiras são criadas sempre que um atributo se relaciona  com outra entidade em um relacionamento um-para-um ou um-para-muitos.

![Exemplo de chave estrangeira](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4b6579732e504e47.png)

Cada carro só pode ser financiado por um banco, portanto, o banco  principal da tabela do Banco é usado como a chave estrangeira FinancedBy na tabela Carro.  Este BankID é capaz de ser usado como a chave  estrangeira para vários carros.

### Tipos de

Os tipos referem-se ao tipo de dados no campo correspondente em uma  tabela. Os tipos também podem se referir a tipos de entidade, que  descrevem a composição de uma entidade; por exemplo, os tipos de  entidade de um livro são autor, título e data publicados.

![Tabelas de ERD](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f506879736963616c2d4552442d53796d626f6c732e706e67.png)

## Diagrama de RE notação

Embora a notação de pé de corvo seja frequentemente reconhecida como o estilo  mais intuitivo, alguns usam a notação OMT, IDEF, Bachman ou UML, de  acordo com suas preferências. A notação do pé do Crow, no entanto, tem  um formato gráfico intuitivo, tornando-se a notação preferida de ERD  para o Lucidchart.

### A Cardinalidade e a ordinalidade

Cardinalidade refere-se ao número máximo de vezes que uma instância  em uma entidade pode se relacionar com instâncias de outra entidade. A  ordinadalidade, por outro lado, é o número mínimo de vezes que uma  instância em uma entidade pode ser associada a uma instância na entidade relacionada.

Carcarinalidade e ordinalidade são mostradas pelo estilo de uma linha e seu ponto final, de acordo com o estilo de notação escolhido.

![Notation ERD (IDR)](./images/68747470733a2f2f6432736c6377336b697036716d6b2e636c6f756466726f6e742e6e65742f6d61726b6574696e672f70616765732f63686172742f6572642d73796d626f6c732f4552442d4e6f746174696f6e2e504e47.png)

Aqui está o significado de cada uma das linhas representadas na imagem:

1. **Linha com um traço vertical simples (|)**:
   - **Significado**: Relacionamento **Um-para-um (1:1)**.
   - **Descrição**: Cada instância de uma entidade está associada a exatamente uma instância da outra entidade. 
   - **Exemplo**: Cada pessoa tem exatamente um número de segurança social.

2. **Linha com "pé de galinha" (\|<)**:
   - **Significado**: Relacionamento **Um-para-muitos (1:N)**.
   - **Descrição**: Uma instância de uma entidade pode estar associada a várias instâncias da outra entidade.
   - **Exemplo**: Um autor pode escrever muitos livros.

3. **Linha com dois traços verticais (||)**:
   - **Significado**: Relacionamento **Um (e somente um)**.
   - **Descrição**: Indica que a entidade associada deve ter exatamente uma instância correspondente, sem possibilidade de variação.
   - **Exemplo**: Cada carro tem exatamente um número de chassi.

4. **Linha com um círculo seguido de um traço vertical (O|)**:
   - **Significado**: Relacionamento **Zero ou um (0:1)**.
   - **Descrição**: Uma entidade pode não ter nenhuma instância relacionada ou pode ter uma única instância relacionada.
   - **Exemplo**: Uma pessoa pode ou não ter um carro.

5. **Linha com "pé de galinha" e um traço vertical (\|<) seguida de um círculo (O)**:
   - **Significado**: Relacionamento **Um ou muitos (1:N)**.
   - **Descrição**: Uma instância de uma entidade pode estar relacionada a uma ou várias instâncias de outra entidade.
   - **Exemplo**: Um cliente pode fazer uma ou várias compras.

6. **Linha com "pé de galinha" (\|<) seguida de um círculo (O)**:
   - **Significado**: Relacionamento **Zero ou muitos (0:N)**.
   - **Descrição**: Uma entidade pode não ter nenhuma instância relacionada ou pode ter muitas instâncias relacionadas.
   - **Exemplo**: Um autor pode não ter escrito nenhum livro ou pode ter escrito muitos.

Essas notações ajudam a definir claramente as regras de cardinalidade nos relacionamentos entre entidades em um diagrama ER, esclarecendo como os dados em diferentes tabelas estão conectados e quais são as restrições ou possibilidades para essas conexões.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

---

## Exemplos de código para construir bancos de dados relacionados

### Modelagem de Relacionamento Um-para-Muitos entre Estados e Cidades em Banco de Dados Relacional

![Relacionamento entre Cidades e Estados](./images/Relations_between_Cities_and_States.png)

```sql
-- Criando a tabela states
CREATE TABLE states (
    id INT AUTO_INCREMENT PRIMARY KEY,
    letters VARCHAR(2) NOT NULL,
    name VARCHAR(100) NOT NULL
);

-- Criando a tabela cities
CREATE TABLE cities (
    id INT AUTO_INCREMENT PRIMARY KEY,
    state_id INT NOT NULL,
    name VARCHAR(100) NOT NULL,
    FOREIGN KEY (state_id) REFERENCES states(id)
);
```

O modelo de Entidade-Relacionamento (ER) descrito pelo código SQL consiste em duas entidades principais: **Estados (states)** e **Cidades (cities)**, com um relacionamento do tipo **um-para-muitos** entre elas. Vamos detalhar cada parte:

### Entidades:

1. **states (Estados)**
   - **Atributos:**
     - `id`: Identificador único do estado, do tipo `INT`, que é auto incrementado (`AUTO_INCREMENT`), sendo também a **chave primária** da tabela.
     - `letters`: Código de duas letras que representam o estado, do tipo `VARCHAR(2)`, que não pode ser nulo (`NOT NULL`). Normalmente representa a sigla do estado.
     - `name`: Nome completo do estado, do tipo `VARCHAR(100)`, também não nulo.
   
   Esta entidade representa a tabela de **Estados**, armazenando o nome completo e a sigla de cada estado.

2. **cities (Cidades)**
   - **Atributos:**
     - `id`: Identificador único da cidade, do tipo `INT`, auto incrementado, sendo também a **chave primária** da tabela.
     - `state_id`: Chave estrangeira (`FOREIGN KEY`) que referencia a tabela `states`, mais especificamente o atributo `id`, garantindo que toda cidade esteja associada a um estado existente.
     - `name`: Nome da cidade, do tipo `VARCHAR(100)`, e também não nulo.

   Esta entidade representa a tabela de **Cidades**, que inclui o nome da cidade e uma chave estrangeira que a vincula ao estado correspondente.

### Relacionamento:

- O relacionamento entre **states** e **cities** é **um-para-muitos** (1:N), onde **um estado pode ter muitas cidades**, mas **cada cidade pertence a um único estado**. Esse relacionamento é implementado através da **chave estrangeira** `state_id` na tabela `cities`, que referencia a chave primária `id` da tabela `states`.

### Resumo:
- **Entidade 1 (states)**: Representa os estados, com atributos para a sigla (`letters`) e o nome (`name`).
- **Entidade 2 (cities)**: Representa as cidades, com atributos para o nome (`name`) e uma chave estrangeira (`state_id`) que relaciona cada cidade a um estado.
- **Relacionamento**: Um estado pode ter muitas cidades, mas cada cidade está associada a um único estado, caracterizando um relacionamento **um-para-muitos**.

Este modelo é simples e adequado para sistemas que precisam armazenar informações sobre cidades e seus estados de origem, como em um sistema de cadastros ou geolocalização.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

---

### Alteração de Tabelas para Adicionar Chave Estrangeira e Estabelecer Relacionamento entre Entidades em Banco de Dados

Para criar a relação de **chave estrangeira** entre as tabelas `cities` e `states` após a criação das tabelas, você pode usar o comando `ALTER TABLE`. Esse comando permite modificar uma tabela já existente, adicionando a restrição de chave estrangeira.

Aqui está como você pode fazer isso:

```sql
ALTER TABLE cities
ADD CONSTRAINT fk_state_id
FOREIGN KEY (state_id) REFERENCES states(id);
```

### Explicação:
- **`ALTER TABLE cities`**: Este comando indica que você está modificando a tabela `cities`.
- **`ADD CONSTRAINT fk_state_id`**: Aqui, estamos adicionando uma nova restrição com o nome `fk_state_id`. É uma boa prática nomear as chaves estrangeiras para facilitar o gerenciamento e entendimento.
- **`FOREIGN KEY (state_id)`**: Especifica o campo que será a chave estrangeira, no caso, o atributo `state_id` da tabela `cities`.
- **`REFERENCES states(id)`**: Define que a chave estrangeira `state_id` faz referência ao campo `id` da tabela `states`.

Esse comando criará o relacionamento **um-para-muitos** entre as tabelas `cities` e `states`, garantindo que todas as cidades cadastradas tenham um estado correspondente na tabela `states`.

[![Início](../imges/control/11273_control_stop_icon.png?raw=true "Início")](../README.md#jsdevguide "Início")
[![Voltar](../imges/control/11269_control_left_icon.png "Voltar")](../README.md#summary "Voltar")
[![Subir](../imges/control/11280_control_up_icon.png "Subir")](#summary "Subir")

---

