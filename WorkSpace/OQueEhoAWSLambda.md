# O que é o AWS Lambda?

[PDF](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-dg.pdf#welcome)

[RSS](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-updates.rss)



O Lambda é um serviço de computação que permite que você execute o código sem provisionar ou gerenciar servidores. O Lambda executa seu código em uma infraestrutura de computação de alta disponibilidade e executa toda a administração dos recursos computacionais, inclusive a manutenção do servidor e do sistema operacional, o provisionamento e a escalabilidade automática da capacidade e o monitoramento e o registro em log do código. Com o Lambda, você pode executar código para praticamente qualquer tipo de aplicação ou serviço de backend. Tudo o que você precisa fazer é fornecer o código em uma das [linguagens compatíveis com o Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-runtimes.html).

**nota**

No Guia do desenvolvedor do AWS Lambda, assumimos que você tem experiência com codificação, compilação e implantação de programas usando uma das linguagens compatíveis.

Você organiza seu código em[Funções do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-function). O Lambda executa a função somente quando necessário e escala automaticamente, desde algumas solicitações por dia a milhares por segundo. Você paga apenas pelo tempo de computação consumido. Não haverá cobranças quando o código não estiver em execução.

Você pode chamar suas funções do Lambda usando a API do Lambda ou o Lambda pode executar suas funções em resposta a eventos de outros serviços da AWS. Por exemplo, você pode usar o Lambda para:

- Criar gatilhos de processamento de dados paraAWSServiços, como o Amazon Simple Storage Service (Amazon S3) e o Amazon DynamoDB.
- Processar dados de transmissões armazenadas no Amazon Kinesis.
- Criar seu próprio back-end que opera em escala, performance e segurança da AWS.

O Lambda é um serviço altamente disponível. Para obter mais informações, consulte o [Acordo de Nível de Serviço do AWS Lambda](http://aws.amazon.com/lambda/sla/).

**Seções**

- [Quando devo usar o Lambda?](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#when-to-use-cloud-functions)
- [Recursos do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#features)
- [Conceitos básicos do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#welcome-first-time-user)
- [Serviços relacionados](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#related-services)
- [Acesso ao Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#accessing)
- [Definição de preço do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html#pricing)

## Quando devo usar o Lambda?

O Lambda é o serviço de computação ideal para muitos cenários de aplicações, desde que você possa gravar o código da aplicação com o [ambiente do tempo de execução padrão](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/runtimes-context.html) do Lambda e dentro dos recursos fornecidos pelo Lambda.

Ao usar o Lambda, você é responsável apenas pelo seu código. O Lambda gerencia a frota de computação que oferece um equilíbrio de memória, CPU, rede e outros recursos para executar seu código. Como o Lambda gerencia esses recursos, não é possível fazer login para calcular instâncias ou personalizar o sistema operacional no[Tempo de execução fornecido](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-runtimes.html). O Lambda executa atividades operacionais e administrativas em seu nome, incluindo gerenciamento de capacidade, monitoramento e registro de suas funções do Lambda.

Se você precisar gerenciar seus próprios recursos de computação, o AWS tem outros serviços de computação para atender às suas necessidades. Por exemplo:

- O Amazon Elastic Compute Cloud (Amazon EC2) oferece uma grande variedade de tipos de instância do EC2. Ele permite personalizar sistemas operacionais, configurações de rede e segurança e toda a pilha de software. Você é responsável por provisionar a capacidade, monitorar a integridade e a performance da frota e usar zonas de disponibilidade para tolerância a falhas.
- O AWS Elastic Beanstalk permite implantar e dimensionar aplicações no Amazon EC2. Você mantém a propriedade e o controle total sobre as instâncias subjacentes do EC2.

## Recursos do Lambda

Os principais recursos a seguir ajudam você a desenvolver aplicações do Lambda escaláveis, seguras e facilmente extensíveis:

- **Controles de simultaneidade e escalabilidade**

  Os [controles de simultaneidade e escalabilidade](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/invocation-scaling.html), como limites de simultaneidade e simultaneidade provisionada, oferecem controle detalhado sobre a escalabilidade e a capacidade de resposta das aplicações de produção.

- **Funções definidas como imagens de contêiner**

  Use ferramentas, fluxos de trabalho e dependências de [imagem de contêiner](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-images.html) preferidos para criar, testar e implantar suas funções do Lambda.

- **Assinatura de código**

  A [assinatura de código](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/configuration-codesigning.html) do Lambda fornece controles de confiança e integridade que permitem verificar se apenas o código inalterado publicado pelos desenvolvedores aprovados foi implantado em suas funções do Lambda.

- **Extensões Lambda**

  É possível usar [extensões do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/runtimes-extensions-api.html) para aumentar as funções do Lambda. Por exemplo, use extensões para integrar mais facilmente o Lambda com suas ferramentas favoritas de monitoramento, observabilidade, segurança e governança.

- **Esquemas de funções**

  Um esquema de função fornece código de exemplo que mostra como usar o Lambda com outros serviços da AWS ou aplicações de terceiros. Os esquemas incluem predefinições de código de exemplo e configuração de funções para tempos de execução de Node.js e Python.

- **Acesso ao banco de dados**

  Um [proxy de banco de dados](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/configuration-database.html) gerencia um grupo de conexões de banco de dados e retransmite consultas provenientes de uma função. Isso permite que uma função atinja altos níveis de simultaneidade sem esgotar conexões de banco de dados.

- **Acesso aos sistemas de arquivos**

  Você pode configurar uma função para montar um[Amazon Elastic File System (Amazon EFS)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/configuration-filesystem.html)para um diretório local. Com o Amazon EFS, o código da função pode acessar e modificar os recursos compartilhados de forma segura e com alta simultaneidade.

## Conceitos básicos do Lambda

Para trabalhar de forma eficaz com o Lambda, você precisa de experiência em codificação e experiência nos seguintes domínios:

- SO Linux e comandos, bem como conceitos como processos, threads e permissões de arquivos.
- Conceitos de nuvem e conceitos de rede IP (para redes públicas e privadas).
- Conceitos de computação distribuída, como HTTP como um IPC, filas, mensagens, notificações e simultaneidade.
- Familiaridade com os serviços e conceitos de segurança: AWS Identity and Access Management (IAM) e princípios de controle de acesso, e AWS Key Management Service (AWS KMS) e infraestrutura de chave pública.
- Familiaridade com os principais serviços que interagem com o Lambda: Amazon API Gateway, Amazon S3, Amazon Simple Queue Service (Amazon SQS) e DynamoDB.
- Configuração de instâncias do EC2 com Linux.

Se você está usando o Lambda pela primeira vez, recomendamos que você comece com os seguintes tópicos para aprender o básico:

1. **Leia a [Visão geral do produto do Lambda](http://aws.amazon.com/lambda/) e explore a página [Conceitos básicos do Lambda](http://aws.amazon.com/lambda/getting-started/).**
2. **Para criar e testar uma função do Lambda usando o console do Lambda, teste o [exercício de introdução baseado no console](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/getting-started.html).** Esse exercício ensina sobre o modelo de programação do Lambda e outros conceitos.
3. **Se você estiver familiarizado com os fluxos de trabalho de imagem de contêiner, tente o exercício de introdução para [criar uma função do Lambda definida como uma imagem de contêiner](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/gettingstarted-images.html).**

A AWS também fornece os seguintes recursos para aprender sobre aplicações sem servidor e do Lambda:

- O [Blog de computação da AWS](http://aws.amazon.com/blogs/compute/) contém artigos úteis sobre o Lambda.
- O [AWS Serverless](https://serverlessland.com/) fornece blogs, vídeos e treinamento relacionados ao desenvolvimento sem servidor da AWS.
- O canal do YouTube [AWS Online Tech Talks](https://www.youtube.com/channel/UCT-nPlVzJI-ccQXlxjSvJmw) inclui vídeos sobre tópicos relacionados ao Lambda. Para obter uma visão geral sobre aplicações sem servidor e o Lambda, consulte o vídeo [Introduction to AWS Lambda & Serverless Applications](https://www.youtube.com/watch?v=EBSdyoO3goc).

## Serviços relacionados

O [Lambda integra-se a outros serviços da AWS](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-services.html) para invocar funções com base nos eventos que você especificar. Por exemplo:

- Use o [API Gateway](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-apigateway.html) para fornecer um gateway seguro e escalável para APIs da Web que roteiam solicitações HTTP para funções do Lambda.
- Para serviços que geram uma fila ou fluxo de dados (como [DynamoDB](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-ddb.html) e [Kinesis](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-kinesis.html)), o Lambda pesquisa a fila ou o fluxo de dados do serviço e invoca sua função para processar os dados recebidos.
- Defina os eventos do [Amazon S3](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-s3.html) que chamam uma função do Lambda para processar objetos do Amazon S3, por exemplo, quando um objeto é criado ou excluído.
- Usar uma função Lambda para processar[Amazon SQS](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-sqs.html)Mensagens ou[Amazon Simple Notification Service (Amazon SNS)](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/with-sns.html)Notificações do .
- Use o [AWS Step Functions](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-stepfunctions.html) para conectar funções do Lambda em conjunto em fluxos de trabalho sem servidor chamados máquinas de estado.

## Acesso ao Lambda

Você pode criar, invocar e gerenciar suas funções do Lambda usando qualquer uma das seguintes interfaces:

- **Console de Gerenciamento da AWS**: fornece uma interface da Web para você acessar suas funções. Para obter mais informações, consulte [Console do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/foundation-console.html).
- **AWS Command Line Interface (AWS CLI)**: fornece comandos para um amplo conjunto de serviços da AWS, incluindo o Lambda, e é compatível com o Windows, o macOS e o Linux. Para obter mais informações, consulte [Como usar o Lambda com o AWS CLI](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/gettingstarted-awscli.html).
- **AWS SDKs**: fornecem APIs específicas da linguagem e gerenciam muitos dos detalhes da conexão, como cálculo de assinatura, tratamento de repetições de solicitações e tratamento de erros. Para obter mais informações, consulte [AWS SDKs](http://aws.amazon.com/tools/#SDKs).
- **AWS CloudFormation**: permite criar modelos que definem suas aplicações do Lambda. Para obter mais informações, consulte [AWS LambdaAplicativos do ](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/deploying-lambda-apps.html). O AWS CloudFormation também é compatível com o [AWS Cloud Development Kit (CDK)](http://aws.amazon.com/cdk).
- **AWS Serverless Application Model (AWS SAM)**: fornece modelos e uma CLI para configurar e gerenciar aplicações sem servidor da AWS. Para obter mais informações, consulte [AWS SAM](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-settingup.html#lambda-settingup-awssam).



## Definição de preço do Lambda

Não há custo adicional para a criação de funções do Lambda. Há cobranças para executar uma função e para transferência de dados entre o Lambda e outros serviços da AWS. Alguns recursos opcionais do Lambda (como [simultaneidade provisionada](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/configuration-concurrency.html)) também incorrem em cobranças. Para obter mais informações, consulte [Definição de preço do AWS Lambda](http://aws.amazon.com/lambda/pricing/).