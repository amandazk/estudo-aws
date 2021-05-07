# Módulo 3

## Visão geral da infraestrutura global da AWS

### Seção 1 - Infraestrutura global da AWS

A infraestrutura global da AWS foi projetada e criada para **oferecer um ambiente de computação em nuvem flexível, confiável, escalável e seguro com desempenho de rede global de alta qualidade**.

Uma região da AWS é uma área geográfica

- A **replicação de dados** entre regiões é controlada por você.
- A **comunicação** entre regiões usa a infraestrutura de rede backbone da AWS.

- Cada região fornece redundância total e conectividade com a rede.
- Uma região normalmente consiste em duas ou mais **zonas de disponibilidade**.
- Uma zona de disponibilidade consiste em um ou mais datacenters.
- Para ter **estabilidade e tolerância a falhas**, as regiões da AWS são **isoladas**. Os recursos em uma região não são replicados automaticamente para outra região.
  - Quando você armazena dados em uma região específica, eles não são replicados fora dessa região.
- O Console de Gerenciamento da AWS pode ser usado para habilitar ou desabilitar uma região.
- Algumas regiões têm **acesso restrito**.



Alguns fatores a se considerar ao selecionar a região ou regiões:

- Governança de dados e requisitos legais
- Proximidade com os clientes (diminuir a latência) -> para testar : Cloud Ping
- Serviços disponíveis na região
- Variação dos custos por região

**Zonas de disponibilidade**:

- Cada região tem várias zonas de disponibilidade
- Cada zona de disponibilidade é uma partição totalmente isolada da infraestrutura da AWS

**Datacenters da AWS**:

- São projetados para segurança
- Os datacenters são onde os dados residem e o processamento de dados ocorre
- Cada datacenter tem energia, redes e conectividade redundantes e está hospedado em uma instalação separada

**Amazon CloudFront** é uma rede de entrega de conteúdo usada para distribuir conteúdo para usuários finais a fim de reduzir a latência. 

- Amazon Route 53: serviço de roteamento para diminuir a latência
- **Pontos de presença**: medem a conectividade, o desempenho e a computação com internet para achar a melhor maneira de rotear solicitações de tráfego
  - São usados por muitos serviços da AWS, incluindo o Amazon CloudFront
  - **Pontos de presença de cache** são usados quando existe conteúdo que não é acessado frequentemente o suficiente para permanecer em um ponto de presença. Eles absorvem o conteúdo e fornecem uma alternativa para obter esse conteúdo diretamente do servidor origem

 

### Seção 2 - Visão geral dos serviços e das categorias de serviços da AWS

A infraestrutura global da AWS pode ser dividida em três elementos: **Regiões, Zonas de Disponibilidade e Pontos de Presença**. Essa infraestrutura fornece a plataforma para um amplo conjunto de serviços, como redes, armazenamento, serviços de computação e banco de dados.

Existem 23 categorias diferentes de produtos ou serviços e cada categoria consiste em um ou mais serviços.

**Categoria de serviço de armazenamento**:

- É representada pelo **Amazon Simple Storage Service, ou Amazon S3**, que é um serviço de armazenamento para segurança, disponibilidade e desempenho de dados de escalabilidade. 
- Em seguida temos o **Amazon Elastic Block Store, ou Amazon EBS**. Ele é um armazenamento de alto desempenho projetado para uso com o Amazon EC2 para cargas de trabalho com alto consumo de transações e throughput
- O **Amazon Elastic File System, ou Amazon EFS** oferece sistema de arquivos de rede escalável e gerenciado (também conhecido como NFS), para uso em serviços da Nuvem AWS e recursos locais
- Por fim, o **Amazon Simple Storage Service Glacier**, que é uma classe de armazenamento. É durável, seguro e de baixo custo, para arquivamento de dados e backup de longo prazo

**Categoria de serviço de computação**:

- **Amazon Elastic Compute Cloud (Amazon EC2)**: fornece capacidade computacional como máquinas virtuais na nuvem
- **Amazon EC2 Auto Scaling**: permite que você adicione ou remova automaticamente instâncias EC2 de acordo com as condições definidas
- **Amazon Elastic Container Service (Amazon ECS)**:  dá suporte a contêineres do Docker
- **Amazon Elastic Container Registry Service (Amazon ECR)**: é um registro de contêiner gerenciado do Docker que facilita o armazenamento, o gerenciamento e a implantação de imagens de contêineres do Docker
- **Amazon Elastic Beanstalk**: é um serviço para implantação / escalabilidade de aplicativos e serviços wev em servidores familiares, como Apache e outros
- **AWS Lambda**: permite executar código sem provisionar ou gerenciar servidores
- **Amazon Elastic Kubernetes Service (Amazon EKS)**: simplifica implantação, gerenciamento e escalabilidade de apps conteinerizados usando o Kubernetes na AWS
- **AWS Fargate**: permite executar conteineres sem gerenciar servidores / clusters

**Categoria de serviço de  banco de dados**:

- **Amazon Relational Database Service (Amazon RDS)**: um banco de dados relacional fácil de configurar e escalável na nuvem. Ele oferece capacidade redimensionável e automatiza tarefas de admin, provisão de hardware, configuração de bancos de dados / patches / backups
- **Amazon Aurora**: banco de dados relacional compatível com o MySQL e PostgreSQL
- **Amazon Redshift**: permite executar consultas analíticas em petabytes de dados armazenados localmente na Amazon
- **Amazon DynamoDB**: um banco de dados NoSQL de documentos e valor de chave

**Categoria de serviço de  rede e entrega de conteúdo**:

- **Amazon Virtual Private Cloud (Amazon VPC)**: permite provisionar seções da nuvem AWS isoladas logicamente para executar recursos da AWS em rede virtual
- **Elastic Load Balancing**: atribui automaticamente o tráfego de entrada de aplicativos entre diversos destinos
- **Amazon CloudFront**: rede de entrega de conteúdo rápida, também conhecida como CDN que entrega dados, vídeos, aplicativos, etc com segurança e baixa latência 
- **AWS Transit Gateway**: é um serviço que permite que clientes conectem suas Amazon VPCs e suas redes locais a um único gateway gerenciado de maneira centralizada
- **Amazon Route 53**: uma maneira confiável de rotear usuários finais para o aplicativo da Internet
- **AWS Direct Connect**: oferece uma maneira de estabelecer uma conexão de rede privada dedicada do datacenter ou escritório para a AWS -> diminui custos e aumenta o throughput
- **AWS VPN**: fornece um túnel privado e seguro para usa rede ou dispositivo para a rede global da AWS

**Categoria de serviços de segurança, identidade e conformidade**:

- **AWS Identity and Acess Management (IAM)**: permite gerenciar o acesso aos serviços e recursos da AWS com segurança
- **AWS Organizations**: permite restringir quais serviços e ações são permitidas em suas contas
- **Amazon Cognito**: permite adicionar autenticação e controle de acesso de usuários aos aplicativos web e móveis
- **AWS Artifact**: oferece acesso sob demanda aos relatórios de segurança e conformidade da AWS, bem como a contratos online selecionados
- **AWS Key Management Service (AWS KMS)**: permite criar e gerenciar chaves de criptografia. Você pode usar o KMS para controlar o uso da criptografia em uma grande variedade de serviços da AWS em seus aplicativos
- **AWS Shield**: um serviço gerenciado de proteção contra negação de serviço distribuída que protege aplicativos executados na AWS

**Categoria de serviços de gerenciamento de custos da AWS**:

- **Custo da AWS e Relatórios de uso**: contém o conjunto mais abrangente de dados de uso e custo da AWS disponível, incluindo metadados adicionais sobre serviços, definição de preço e reservas da AWS
- **Orçamentos da AWS**: onde você pode definir orçamentos personalizados para alertá-lo quando seus custos ou uso da AWS excederem ou estiverem previstos para exceder o valor orçado
- **Custo da AWS Explorer**: tem uma interface fácil de usar que permite visualizar e compreender e gerenciar seus custos e horas extras de uso da AWS

**Categoria de serviços de gerenciamento e governança**:

- **Console de Gerenciamento da AWS**: é uma interface de usuário baseada na web para acessar sua conta da AWS
- **AWS Config**: um serviço que ajuda a rastrear o inventário de recursos e as alterações
- **Amazon CloudWatch**: permite monitorar recursos e aplicativos
- AWS Auto Scaling: oferece recursos que permitem escalar vários recursos para atender a demanda
- **Interface de linha de comando da AWS**: fornece uma ferramenta unificada para gerenciar serviços da AWS
- **AWS Trusted Advisor**: uma ferramenta online que ajuda a otimizar a performance e a segurança usando as melhores práticas da AWS
- **AWS Well-Architected Tool**: fornece ajuda na revisão e melhoria das cargas de trabalho
- **AWS CloudTrail**: esse serviço rastreia a atividade do usuário e o uso da API em suas contas da AWS













