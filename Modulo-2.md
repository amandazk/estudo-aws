# Módulo 2

## Economia e faturamento da nuvem

### Seção 1 - Fundamentos da definição de preço

Há três fatores fundamentais de custo com a AWS:

- Armazenamento: cobrado normalmente por GB

- Computação: Cobrado por hora/segundo e varia por tipo de instância

- Transferência de dados: A saída é agregada e cobrada. A entrada não tem cobrança (exceções). Cobrado normalmente por GB

  

Principais tópicos em relação ao preço

- Pague apenas pelos serviços que você consumir, sem grandes despesas iniciais
- Obtenha descontos baseados em volume:
  - Economias à medida que o uso aumenta
  - Definição de preço em camadas para serviços como Amazon S3, Amazon EBS ou Amazon EFS -> quanto mais você usar, menos você pagará por GB
  - Vários serviços de armazenamento oferecem custos de armazenamento mais baixos com base nas necessidades
- Pague ainda menos com o crescimento da AWS
- Definição de preço personalizada
- Nível gratuito da AWS
- Serviços sem curso:
  - Amazon VPC
  - Elastic Beanstalk
  - Auto Scaling
  - AWS Cloud Formation
  - AWS IAM



### Seção 2 - Custo total de propriedade

A diferença entre a Infraestrutura Tradicional e a da Nuvem AWS é como elas são implantadas. Em infraestruturas tradicionais existem diversos custos fixos, conhecidos também como despesas de capital.

O **custo total de propriedade (TCO)** é a estimativa financeira para ajudar a identificar custos diretos e indiretos de um sistema.

Para que usar o TCO?

- Comparar os custos da execução de um ambiente de infraestrutura inteiro ou de uma carga de trabalho específica no local em comparação com a AWS
- Criar orçamento de migração para a nuvem



### Seção 3 - AWS Organizations

É necessário um serviço que vincule contas separadas de um mesmo cliente -> diferentes times dentro de uma empresa podem ter diferentes contas, para ajudar nos relatórios, por exemplo.

O AWS Oganizations é usado para o faturamento consolidado de várias contas. É um serviço gratuito de gerenciamento de contas que permite consolidar várias contas da AWS em uma árvore organizacional com cada ramificação representando um departamento ou equipe.

**Configuração do Organizations:**

1. Criar organização
2. Criar unidades organizacionais
3. Criar políticas de controle de serviço
4. Restrições de teste

**Acessar o AWS Organizations:**

- Console de Gerenciamento da AWS
- Ferramentas da interface da linha de comando da AWS (ILC da AWS)
- Kits de desenvolvimento de software (SDKs)
- Interfaces de programação de aplicativos (APIs) para consulta HTTPS



### Seção 4 - AWS Billing and Cost Management

É um serviço usado para pagar sua fatura da AWS, monitorar seu uso e controlar suas despesas. Ele permite prever e ter uma ideia melhor de quais serão seus custos e uso no futuro, para você poder planejar com antecedência.



### Seção 5 - Suporte Técnico

**AWS Support**

- Fornece uma combinação única de ferramentas / especialização
  - AWS Support
  - Planos do AWS Support
- O suporte é fornecido para:
  - Experimentação com a AWS
  - Uso da AWS na produção
  - Processos de negócios que utilizam AWS

- **Orientações proativas**: Gerente técnico de conta (TAM)
- **Melhores práticas**: AWS Trusted Advisor
- **Assistência à conta**: AWS Support Concierge

O AWS Support oferece quatro planos de suporte:

- **Suporte básico**: acesso à central de recursos, painel de status do serviço, perguntas frequentes sobre produtos, fóruns de discussão e suporte a verificações de integridade
- **Suporte ao desenvolvedor**: suporte para desenvolvimento antecipado na AWS
- **Suporte comercial**: clientes que executam cargas de trabalho de produção
- **Suporte empresarial**: clientes que executam cargas de trabalho comerciais e essenciais à missão































