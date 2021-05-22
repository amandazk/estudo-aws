# Módulo 8

## Bancos de dados

### Seção 1 - Amazon Relational Database Service 

**Serviços não gerenciados**: Escalabilidade, tolerância a falhas e disponibilidade são gerenciadas por você. São geralmente provisionados em partes discretas conforme especificado pelos usuários. Como proprietário do serviço, você gerencia como o serviço responde a alterações na carga, erros e situações em que os recursos se tornam indisponíveis.

Ao executar seu próprio banco de dados relacional, você é responsável por várias tarefas administrativas, como manutenção de servidor, consumo de energia, instalação e aplicação de patches de software e backups de banco de dados.

Para resolver os desafios da execução de uma banco de dados relacional autônomo não gerenciado, a AWS fornece o RDS, um serviço que configura, opera e dimensiona bancos de dados relacionais sem nenhuma administração contínua.

![image-20210520131546758](C:\Users\Amanda\Documents\AWS\imagens\imagem-14.png)

Casos de uso do Amazon RDS:

- Aplicativos web e móveis: alto vazão, escalabilidade de armazenamento massiva e alta disponibilidade.
- Aplicativos de comércio eletrônico: banco de dados de baixo custo, segurança de dados e solução totalmente gerenciada.
- Jogos para dispositivos móveis e online: aumente a capacidade rapidamente, escalabilidade automática e monitoramento do banco de dados 

O Amazon RDS fornece seis opções de mecanismos de banco de dados  familiares: Amazon Aurora, Oracle, Microsoft SQL Server, PostgreSQL,  MySQL e MariaDB.

As implantações **Multi-AZ** do Amazon RDS proporcionam disponibilidade e durabilidade melhores para instâncias de banco de dados, o que as torna a solução ideal para  cargas de trabalho de banco de dados de produção. Quando você provisiona uma instância de banco de dados Multi-AZ, o Amazon RDS cria automaticamente uma instância de banco de dados  principal e replica os dados de maneira síncrona para uma instância de  espera em uma zona de disponibilidade (AZ) diferente.

**Serviços gerenciados**: Normalmente, escalabilidade, tolerância a falhas e disponibilidade são incorporados ao serviço. 



### Seção 2 - Amazon DynamoDB 

Com o DynamoDB com transições de bancos de dados relacionais para bancos de dados não relacionais.

Um **banco de dados relacional** funciona com dados estruturados que são organizados por registros e colunas de tabelas. Eles criam relacionamentos entre tabelas para que você possa extrair dados de várias tabelas com consultas. Usam linguagem de consulta estruturada.

Um **banco de dados não relacional** é qualquer banco de dados que não segue o modelo relacional. Ele funciona com listas de pares de chave/valor.  

**Amazon DynamoDB**: Serviço de banco de dados NoSQL rápido e flexível para qualquer escala. Armazena dados de forma redundante em várias instalações em uma região de arquitetura tolerante a falhas.

- Tabelas de banco de dados NoSQL
- Armazenamento praticamente ilimitado
- Os itens podem ter atributos diferentes
- Consultas de baixa latência
- Vazão de leitura/gravação escalável

Tabelas, itens e atributos são os principais componentes do DynamoDB. Ele oferece suporte a dois tipos diferentes de chaves primárias: chave de partição e chave de partição e de classificação. 

![image-20210520143713851](C:\Users\Amanda\Documents\AWS\imagens\imagem-15.png)





### Seção 3 - Amazon Redshift 

O Amazon Redshift é um data warehouse rápido e gerenciado que torna simples e econômica a análise de todos os seus dados usando ferramentas SQL padrão e ferramentas de BI que você já tem. O serviço permite executar consultas complexas de análise em petabytes de dados estruturados.

Uma implementação do Amazon Redshift consiste em um cluster de nós líderes de computação. O nó líder gerencia a comunicação com programas cliente e toda a comunicação com nós de computação. Ele analisa e desenvolve planos de execução para executar a série de etapas necessárias para obter resultados de consultas complexas. O nó líder compila código de elementos individuais do plano de execução e atribui o código aos nós de computação individuais. Os nós de computação executam o código compilado e reenviam resultados intermediários ao nó líder para agregação final.

Casos de uso do Amazon Redshift:

- Data warehouse corporativo (EDW)
- Big data
- Software como serviço (SaaS)



### Seção 4 - Amazon Aurora

Amazon Aurora é um banco de dados relacional compatível com MySQL ou PostgreSQL criado para a nuvem. Como um serviço totalmente gerenciado, o Aurora foi projetado para automatizar tarefas demoradas. Ele é fácil de configurar e suporta linguagem de consulta estruturada padrão. Amazon Aurora atinge alta disponibilidade armazenando várias cópias de seus dados em diferentes zonas de disponibilidade. O backup é feito continuamente no Amazon S3.

