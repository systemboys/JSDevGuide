> ## Símbolos e notação do diagrama de Entidade-Relacionamento
>
> ![img](https://corporate-assets.lucid.co/chart/2f2cbd61-b92c-4742-a126-82786e673bbe.svg?v=1707819374504)

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

## Símbolos de diagrama ER conceitual

Os modelos de dados conceituais estabelecem uma visão ampla do que deve  ser incluído no conjunto de modelos. ERDs conceituais podem ser usados  como base para modelos de dados lógicos. Eles também podem ser usados  para formar relações de comunalidade entre modelos de emergência como  base para a integração do modelo de dados. Todos os símbolos mostrados  abaixo são encontrados na biblioteca de forma de Relacionamento de  Entidade e Entidade Relacionamento de Lucidchart.

### Símbolos de entidade ERD

Entidades são objetos ou conceitos que representam dados importantes. As entidades são tipicamente substantivos, como produto, cliente,  localização ou promoção. Existem três tipos de entidades comumente  usadas em diagramas de relacionamento de entidade.

| Símbolo da Entidade                                          | Nome                 | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | -------------------- | ------------------------------------------------------------ |
| ![Símbolo de Entidade Forte](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/Entity.PNG) | Uma entidade forte   | Essas formas são independentes de outras entidades e são  frequentemente chamadas de entidades-mãe, uma vez que muitas vezes têm  entidades fracas que dependem delas. Eles também terão uma chave  primária, distinguindo cada ocorrência da entidade. |
| ![Símbolo de Entidade Fraca](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/WeakEntity.PNG) | Entidade fraca       | As entidades fracas dependem de outro tipo de entidade. Eles não  têm chaves primárias e não têm significado no diagrama sem sua entidade  controladora. |
| ![Símbolo da entidade associativa](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/AssociativeEntity.PNG) | Entidade associativa | As entidades associativas  relacionam as instâncias de vários tipos de entidades. Eles também  contêm atributos específicos para a relação entre essas instâncias de  entidade. |

### Símbolos de relacionamento ERD

Dentro dos diagramas de relacionamento de entidades, as relações são  usadas para documentar a interação entre duas entidades. Relacionamentos geralmente são verbos como atribuir, associar ou rastrear e fornecer  informações úteis que não podem ser discernidas apenas com os tipos de  entidade.

| Símbolo do relacionamento                                    | Nome          | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | ------------- | ------------------------------------------------------------ |
| ![Símbolo do relacionamento](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/RelationshipShape.PNG) | Relação       | Relacionamentos são associações entre ou entre entidades.    |
| ![Símbolo de relacionamento fraca](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/WeakRelationship.PNG) | Relação fraca | Relacionamentos fracos são conexões entre uma entidade fraca e seu dono. |

### Símbolos de atributo ERD

Os atributos ERD são características da entidade que ajudam os  usuários a entender melhor o banco de dados. Os atributos são incluídos  para incluir detalhes das várias entidades que são destacadas em um  diagrama conceitual.

| Símbolo de atributo                                          | Nome                     | Descrição do produto Descrição                               |
| ------------------------------------------------------------ | ------------------------ | ------------------------------------------------------------ |
| ![Símbolo de atributo](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/Attribute.PNG) | Atributo                 | Os atributos são características de uma entidade, um relacionamento de muitos para muitos ou um relacionamento individual. |
| ![Símbolo de Atributo Multivalorizado](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/MultivaluedAttribute.PNG) | Atributo multivalorizado | Atributos multivalorizados são aqueles que podem assumir mais de um valor. |
| ![Símbolo de Atributo Derido](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/DerivedAttribute.PNG) | Atributo derramado       | Os atributos derivados são atributos cujo valor pode ser calculado a partir de valores de atributos relacionados. |
| ![Símbolo do relacionamento](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/RelationshipShape.PNG) | Relação                  | Relacionamentos são associações entre ou entre entidades.    |

Quer fazer um ERD próprio? Tente o Lucidchart. É rápido, fácil e completamente gratuito.

[Faça um ERD](https://lucid.app/pricing/lucidchart?anonId=0.75b438b2191629b5e3f&sessionDate=2024-08-17T23%3A10%3A35.073Z&sessionId=0.8a9b4276191629b5e40&usecase=erd)

## Símbolos do diagrama ER físico

<iframe frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen=""></iframe>

O modelo de dados físicos é o nível mais granular de diagramas de  relacionamento de entidade e representa o processo de adição de  informações ao banco de dados. Os modelos ER físicos mostram todas as  estruturas da tabela, incluindo o nome da coluna, o tipo de dados da  coluna, as restrições da coluna, a chave primária, a chave estrangeira e as relações entre tabelas.

Como mostrado abaixo, as tabelas são outra maneira de representar  entidades. As partes principais das tabelas de entidades-relacionamento  são:

### Campos

Os campos representam a parte de uma tabela que estabelece os  atributos da entidade. Os atributos são tipicamente pensados como  colunas no banco de dados que o ERD modela.

![Forma dos Campos](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/Field.PNG)

Na imagem acima, InterestRate e LoanAmount são ambos atributos da entidade que estão contidas como campos.

### Chaves

As chaves são uma maneira de categorizar atributos. Os diagramas de  ER ajudam os usuários a modelar seus bancos de dados usando várias  tabelas que garantem que o banco de dados seja organizado, eficiente e  rápido. As chaves são usadas para vincular várias tabelas em um banco de dados umas às outras da maneira mais eficiente possível.

#### Chaves primárias

As chaves primárias são um atributo ou combinação de atributos que  identificam exclusivamente uma e apenas uma instância de uma entidade.

#### Chaves estrangeiras

Chaves estrangeiras são criadas sempre que um atributo se relaciona  com outra entidade em um relacionamento um-para-um ou um-para-muitos.

![Exemplo de chave estrangeira](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/Keys.PNG)

Cada carro só pode ser financiado por um banco, portanto, o banco  principal da tabela do Banco é usado como a chave estrangeira FinancedBy na tabela Carro.  Este BankID é capaz de ser usado como a chave  estrangeira para vários carros.

### Tipos de

Os tipos referem-se ao tipo de dados no campo correspondente em uma  tabela. Os tipos também podem se referir a tipos de entidade, que  descrevem a composição de uma entidade; por exemplo, os tipos de  entidade de um livro são autor, título e data publicados.

![Tabelas de ERD](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/Physical-ERD-Symbols.png)

## Diagrama de RE notação

Embora a notação de pé de corvo seja frequentemente reconhecida como o estilo  mais intuitivo, alguns usam a notação OMT, IDEF, Bachman ou UML, de  acordo com suas preferências. A notação do pé do Crow, no entanto, tem  um formato gráfico intuitivo, tornando-se a notação preferida de ERD  para o Lucidchart. Considere usar um dos nossos [modelos](https://www.lucidchart.com/pages/templates/erd/lucidchart-erd-crows-foot?usecase=erd) de [diagrama de Crow Foot ER](https://www.lucidchart.com/pages/templates/erd/lucidchart-erd-crows-foot?usecase=erd).

### A Cardinalidade e a ordinalidade

Cardinalidade refere-se ao número máximo de vezes que uma instância  em uma entidade pode se relacionar com instâncias de outra entidade. A  ordinadalidade, por outro lado, é o número mínimo de vezes que uma  instância em uma entidade pode ser associada a uma instância na entidade relacionada.

Carcarinalidade e ordinalidade são mostradas pelo estilo de uma linha e seu ponto final, de acordo com o estilo de notação escolhido.

![Notation ERD (IDR)](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/erd-symbols/ERD-Notation.PNG)

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

