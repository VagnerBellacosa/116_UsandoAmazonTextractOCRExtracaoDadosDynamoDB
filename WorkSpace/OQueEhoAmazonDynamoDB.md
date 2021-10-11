# O que é o Amazon DynamoDB?

Bem-vindo ao Guia do desenvolvedor do Amazon DynamoDB

O Amazon DynamoDB é um serviço de banco de dados NoSQL totalmente gerenciado que fornece um desempenho rápido e previsível com escalabilidade integrada. O DynamoDB permite que você transfira os encargos administrativos de operação e escalabilidade de um banco de dados distribuído. Assim, você não precisa se preocupar com provisionamento, instalação e configuração de hardware, replicação, correção de software nem escalabilidade de cluster. Além disso, o DynamoDB oferece criptografia em repouso, o que elimina a carga e a complexidade operacionais envolvidas na proteção de dados confidenciais. Para obter mais informações, consulte [Criptografia do DynamoDB em repouso](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/EncryptionAtRest.html).

Com o DynamoDB, você pode criar tabelas de banco de dados que armazenam e recuperam qualquer quantidade de dados e atendem a todos os níveis de tráfego solicitados. Você pode aumentar ou diminuir a capacidade de taxa de transferência da tabela sem tempo de inatividade ou degradação da performance. Você pode usar o AWS Management Console para monitorar a utilização de recursos e as métricas de performance.

O DynamoDB oferece o recurso de backup sob demanda. Ele permite que você crie backups completos das suas tabelas para retenção e arquivamento de longo prazo de modo a atender às necessidades de conformidade regulamentar. Para obter mais informações, consulte [Backup e restauração sob demanda para DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/BackupRestore.html).

Você pode criar backups sob demanda e habilitar backups contínuos com a recuperação em um ponto anterior do tempo para as tabelas do Amazon DynamoDB. A recuperação point-in-time ajuda a proteger as tabelas do de operações acidentais de gravação ou exclusão. Com a recuperação em um ponto anterior do tempo, você pode recuperar a tabela para qualquer ponto durante os últimos 35 dias. Para obter mais informações, consulte [Recuperação point-in-time: como funciona](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/PointInTimeRecovery_Howitworks.html).

O DynamoDB permite excluir automaticamente os itens expirados das tabelas para ajudar você a reduzir o uso e o custo do armazenamento de dados que não são mais relevantes. Para obter mais informações, consulte [Itens expirados usando a vida útil (TTL) do DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/TTL.html).

## Alta disponibilidade e durabilidade

O DynamoDB distribui automaticamente os dados e o tráfego para as tabelas por um número suficiente de servidores para lidar com seus requisitos de taxa de transferência e armazenamento sem deixar de manter uma performance consistente e rápida. Todos os dados são armazenados em discos de estado sólido (SSDs) e automaticamente replicados entre várias zonas de disponibilidade em uma região da AWS, o que oferece alta durabilidade de dados e disponibilidade integradas. Você pode usar tabelas globais para manter as tabelas do DynamoDB sincronizadas em regiões da AWS. Para obter mais informações, consulte [Tabelas globais: replicação em várias regiões com o DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/GlobalTables.html).

## Conceitos básicos do DynamoDB

Recomendamos que você comece lendo as seguintes seções:

- **[Transações do Amazon DynamoDB: como funciona](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/HowItWorks.html)**: para aprender conceitos essenciais do DynamoDB.
- **[Configuração do DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/SettingUp.html)**: para saber como configurar o DynamoDB (versão para download ou serviço da Web).
- **[Como acessar o DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/AccessingDynamoDB.html)**: para saber como acessar o DynamoDB usando o console, AWS CLI ou API.

Para começar rapidamente com o DynamoDB, consulte [Conceitos básicos do DynamoDB e dos AWS SDKs](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/GettingStarted.html).

Para saber mais sobre o desenvolvimento de aplicações, consulte:

- [Programação com o DynamoDB e os AWS SDKs](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/Programming.html)
- [Trabalhar com tabelas, itens, consultas, varreduras e índices](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/WorkingWithDynamo.html)

Para localizar rapidamente recomendações para maximizar a performance e minimizar os custos de taxa de transferência, consulte [Práticas recomendadas para projetar e arquitetar com o DynamoDB](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/best-practices.html). Para saber como marcar recursos do DynamoDB consulte [Adicionar tags e rótulos a recursos](https://docs.aws.amazon.com/pt_br/amazondynamodb/latest/developerguide/Tagging.html).

Para obter melhores práticas, guias de como fazer e ferramentas, consulte [Recursos do Amazon DynamoDB](http://aws.amazon.com/dynamodb/resources/).

Você pode usar o AWS Database Migration Service (AWS DMS) para migrar dados de um banco de dados relacional ou MongoDB para uma tabela do Amazon DynamoDB. Para obter mais informações, consulte o [Guia do usuário do AWS Database Migration Service](https://docs.aws.amazon.com/dms/latest/userguide/).

Para saber como usar o MongoDB como uma fonte de migração, consulte [Uso do MongoDB como fonte para o AWS Database Migration Service](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Source.MongoDB.html). Para saber como usar o DynamoDB como um destino de migração, consulte [Uso de um banco de dados do Amazon DynamoDB como um destino para o AWS Database Migration Service](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.DynamoDB.html).