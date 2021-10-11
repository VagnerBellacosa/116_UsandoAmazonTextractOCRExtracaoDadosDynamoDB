# DynamoDB: tudo o que você precisa saber para começar

![Data Engineer](https://i2.wp.com/blog.andrefaria.com/wp-content/uploads/2019/06/database-developer.jpg?resize=1024%2C675&ssl=1)

O **Amazon DynamoDB** é um banco de dados NoSQL de documentos e chave/valor com alto desempenho de até 10ms mesmo nos mais intensos casos de uso, além disso é [serverless](https://blog.andrefaria.com/melhores-livros-sobre-serverless), criptografado, seguro, elástico e dá suporte a transações.

Ele é usado no e-commerce na Amazon, por exemplo, um dos maiores e mais acessados e-commerces do mundo. Outras grandes empresas e startups como Nike, Netflix, Airbnb, GE, Samsung, Toyota, e Capital One, também usam o Dynamo.

O banco de dados NoSQL pode processar mais de 10 trilhões de solicitações por dia e comportar picos de mais de 20 milhões de solicitações por segundo.

DynamoDB é um banco de dados serverless, gerenciado que opera em várias regiões e conta com recursos integrados de segurança, backup e restauração, bem como armazenamento em cache na memória.

O DynamoDB distribui automaticamente os dados e o tráfego para tabelas, entre um número suficiente de servidores, para lidar com seus requisitos de throughput e armazenamento, sem deixar de manter um desempenho consistente e rápido. É possível ainda utilizar tabelas globais (que são replicadas e acessíveis em diferentes regiões) se você precisar de baixa latência em diferentes regiões do globo.

Diferente de um banco de dados relacional, as interações com o DynamoDB são stateless, os aplicativos não precisam manter conexões de rede persistentes, mas apenas solicitações e respostas HTTPS.

Todos os dados são armazenados em discos de estado sólido (SSDs) e automaticamente replicados em diferentes data-centers.

Existe uma versão DynamoDB disponível para download que permite gravar e testar aplicativos sem acessar o serviço web.

## Modelagem NoSQL

Nos bancos de dados Relacionais, as consultas de dados são flexíveis, mas têm um custo relativamente alto e não escalam com facilidade em situações de grande volume de tráfego.

Em contra partida, bancos de dados NoSQL, oferecem formas limitadas de consultar dados com eficiência. As demais formas de consulta podem apresentar alto custo e baixo desempenho.

Ao usar um banco como o DynamoDB você precisar modelar os dados especificamente para fazer as consultas mais comuns e importantes do modo mais rápido e barato possível.

Em outras palavras, você não deve iniciar o design do seu esquema até que conheça as perguntas que ele precisará responder, nesse caso, entender bem os problemas de negócios e os casos de uso de aplicativo antecipadamente é essencial.

Você deve criar o mínimo de tabelas possível, muitos aplicativos bem-projetados exige somente uma tabela, isso porque você deve manter os dados relacionados juntos (aninhados).

## Características do DynamoDB

- **Alta Performance**: resposta consistentes abaixo de 10 milissegundos.
- **[Serverless](https://blog.andrefaria.com/melhores-livros-sobre-serverless)**: não há servidores para provisionar, aplicar patches, nem softwares para instalar, manter ou operar.
- **Elástico**: expande e reduz tabelas automaticamente para ajustar de acordo com a capacidade e manter o desempenho.
- **Alta disponibilidade**: A disponibilidade e a tolerância a falhas são incorporadas. SLA de 99,99999%
- [**ACID**](https://pt.wikipedia.org/wiki/ACID): Suporta os requisitos de atomicidade, consistencia, isolamento e durabilidade.
- **Segurança dos dados**: O DynamoDB criptografa todos os dados por padrão e oferece controle refinado de acesso e identidade em todas as suas tabelas.
- **Event Friendly**: É fácil de utilizar com programação orientada a eventos (*event driven programming*) porque, assim como outros serviços serverless, o DynamoDB dispara eventos que podem chamar funções Lambda, por exemplo.

## Componentes do DynamoDB

Em termos de estrutura o Dynamo é tem semelhanças com bancos relacionais contendo Tabelas, Itens (semelhante a registros), Atributos (semelhante a colunas), Chaves Primárias.

- **Tabelas** – como em outros sistemas de banco de dados, o DynamoDB armazena dados em tabelas.

- **Itens** – cada tabela contém zero ou mais itens. Um *item* é um grupo de atributos identificável exclusivamente entre todos os outros itens. Na tabela *PESSOAS* por exemplo, cada item representa uma pessoa. Os itens no DynamoDB são semelhantes de muitas formas a linhas ou registros em outros bancos de dados ou planilhas. Não há limite para o número de itens que você pode armazenar em uma tabela.

- **Atributos** – cada item é composto de um ou mais atributos. Um *atributo* é um elemento de dados fundamental, algo que não precisa ser dividido. Por exemplo, um item na tabela *PESSOAS* contém os atributos como *CPF*, *Nome*, *Sobrenome* etc. Atributos no DynamoDB são similares a colunas em banco de dados relacionais.

- **Atributos Aninhados**: O DynamoDB oferece suporte a atributos aninhados até 32 níveis de profundidade.

- **Schema**: as tabelas podem ou não ter *schemas*, o que significa que nem os atributos nem seus tipos de dados precisam ser necessariamente definidos previamente. Cada item pode ter seus próprios atributos distintos.

- **Chave** **primária**: pode ser chave primária simples, composta por um atributo conhecido como chave de partição, ou uma chave composta por dois atributos, sendo o primeiro atributo a chave de partição, e o segundo a chave de classificação.

- Índices secundários

  : permite consultar os dados na tabela usando uma chave alternativa, além de consultas com base na chave primária. O DynamoDB não exige que você use índices, mas eles conferem aos aplicativos mais flexibilidade durante a consulta de dados.

  - **Global secondary index**: índice com uma chave de partição e uma chave de classificação que podem ser diferentes das contidas na tabela (chave primária).
  - **Índice secundário local**? índice que possui a mesma chave de partição da tabela, mas uma chave de classificação diferente.

## DynamoDB Streams

O DynamoDB Streams é um recurso opcional que captura eventos de modificação de dados em tabelas do DynamoDB.

Os dados sobre esses eventos aparecem no stream praticamente em tempo quase real e na ordem em que os eventos aconteceram.

É análogo a uma trigger (gatilho) num banco de dados relacional. É acionado quando um item é adicional, alterado ou excluído de uma tabela.

Você pode usar o DynamoDB Streams junto com o AWS Lambda para criar um *gatilho* — código que é executado automaticamente sempre que um evento ocorrer.

Por exemplo, se você quiser enviar um e-mail de “boas-vindas” a cada novo cliente, basta habilitar um stream nessa tabela de Clientes e depois associá-lo a uma função Lambda.

Para qualquer item com um atributo *e-mail*, a função do Lambda invocaria o Amazon Simple Email Service (Amazon SES) para enviar um e-mail a esse endereço.

## Capacidade

O DynamoDB tem dois modos de capacidade de leitura/gravação para processar leituras e gravações em suas tabelas: **Sob demanda** ou **Provisionada** (padrão).

### Capacidade Provisionada

Para dimensionar provisionado a infraestrutura do Dynamo e definir o quanto deve cobrar pelo seu uso, a AWS utiliza o conceito de Capacity Units (CUs).

Para cada tabela no banco de dados, você precisa informar, os Capacity Units de leitura (Read Capacity Unit) e escrita (Write Capacity Unit).

Um **Read Capacity Unit** Representa uma leitura consistente ou duas leituras eventualmente consistente por segundo, para um item de 4 KB.

Já um **Write Capacity Unit** representa uma escrita por segundo, para um item de 1 KB.

Modo provisionado é uma boa opção quando você tem tráfego de aplicativos previsível, quando você executa aplicativos com tráfego consistente e que aumenta gradualmente ou quando você pode prever os requisitos de capacidade para controlar os custos.

### Capacidade On Demand

No modo **sob demanda** o faturamento é mais flexível, sendo capaz de servir centenas de solicitações por segundo sem planejamento prévio de de capacidade.

O modo sob demanda é elástico, e se adequa automaticamente ao crescimento e a redução das cargas de trabalho para qualquer nível de tráfego previamente registrado. Tabelas no modo sob demanda entregam a mesma baixa latência milissegundo, SLA e segurança do modo provisionado.

O modo sob demanda é uma boa opção quando você cria novas tabelas com cargas de trabalho desconhecidas, você tem tráfego de aplicativos imprevisível, você prefere a facilidade de pagar somente pelo que usar.

Quando você troca uma tabela de modo provisionado para sob demanda, o DynamoDB faz várias alterações na estrutura de sua tabela e partições. Esse processo pode levar alguns minutos.

### Auto Scaling do DynamoDB

O auto scaling do DynamoDB gerencia ativamente a capacidade de *throughput* de tabelas e índice secundário globais. Basta definir um intervalo (superior e inferior) para unidades de capacidade de leitura e gravação.

## Tipos de Dados

O DynamoDB oferece suporte a vários tipos de dados diferentes para atributos dentro de uma tabela:

- **Tipos escalares**: representa um valor, pode ser número, string, binário, booleano e nulo.
- **Tipos de documentos** – representa uma estrutura complexa com atributos aninhados, como aqueles que você encontra em um documento JSON. Os tipos de documentos são Lista e Mapa.
- **Tipos de conjuntos** – representa vários valores escalares. Os tipos de conjuntos são conjunto de strings, conjunto de números e conjunto de binários.

## Consistência

O DynamoDB oferece suporte a leituras *eventualmente consistentes* e *fortemente consistentes*.

**Leituras eventualmente coerentes**: A resposta de uma leitura pode não refletir os resultados de uma operação de gravação concluída recentemente, podendo incluir alguns dados obsoletos. Se você tentar novamente na sequência, a resposta deverá retornar os dados atualizados.

**Leituras fortemente consistentes**: Resposta sempre atualizada, refletindo as atualizações de todas as operações de gravação anteriores que foram bem-sucedidas. Esse tipo de leitura não é compatível com índices secundários globais (GSI).

## DynamoDB DAX

Na maioria dos casos, os tempos de resposta do DynamoDB podem ser medidos em poucos milissegundos.

Ainda assim, há certos casos de uso que exigem tempos de resposta em microssegundos.

Para esses casos de uso, o *Accelerator DynamoDB (DAX)* oferece tempos de resposta rápidos para acessar dados eventualmente consistentes.

Como um cache de memória, o DAX reduz ainda mais os tempos de resposta do Dynamo.