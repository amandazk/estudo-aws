# Módulo 6

## Computação

### Seção 1 - Visão geral dos serviços de computação

![image-20210512103422048](C:\Users\Amanda\Documents\AWS\imagens\imagem-8.png)



### Seção 2 - Amazon EC2

A execução de servidores no local é cara: os servidores devem ser adquiridos, datacenters devem ser criados, instalados e mantidos. As organizações devem provisionar permanentemente hardware suficiente para lidar com picos de carga de trabalho. Depois que todo hardware estiver instalado, a capacidade do servidor geralmente fica ociosa para partes significativas de todos os dias, o que é um desperdício.

O **Amazon Elastic Compute Cloud (EC2)** fornece máquinas virtuais chamadas de instâncias do EC2 na nuvem, onde você pode hospedar as mesma aplicações que são utilizadas em sistemas 'on-premises'.  

- Você pode executar instâncias de qualquer tamanho em uma zona de disponibilidade em qualquer lugar do mundo.
  - Execute instâncias a partir de imagens de máquina da Amazon(AMIs)
- Você pode controlar o tráfego de e para instâncias usando **grupos de segurança**

Escolhas feitas usando o Assistente para executar instância:

- AMI: qual AMI executar  a instância do EC2
- Tipo de instância: determinará a RAM, CPU, armazenamento e performance de rede
- Configurações de rede
- Função do IAM
- Dados de usuário
- Opções de armazenamento
- Tags
- Grupo de segurança
- Par de chaves



### Seção 3 - Amazon EC2 Parte 2

Opções de armazenamento do Amazon EC2:

- Amazon Elastic Block Store (Amazon EBS)
  - Volumes de armazenamento em nível de bloco duráveis
  - Você pode interromper a instância e iniciá-la novamente; os dados ainda estarão lá
- Armazenamento de instâncias do Amazon EC2
  - O armazenamento é fornecido em discos anexados ao computador host em que a instância do EC2 está em execução
  - **Se a instância for interrompida, os dados armazenados aqui serão excluídos** 
- Outras opções de armazenamento (não para o volume raiz)
  - Monte um sistema de arquivos do Amazon Elastic File System (Amazon EFS)
  - Conecte-se ao Amazon Simple Storage Service (Amazon S3)



### Seção 4 - Amazon EC2 Parte 2

- Uma **tag** é um rótulo que você atribui a um recurso da AWS
  - Consiste um uma chave e um valor opcional
- A marcação é como você pode anexar metadados a uma instância do EC2
- Benefícios potenciais da marcação: filtragem, automação, alocação de custos e controle de acesso

- Um **grupo de segurança** é um conjunto de regras de firewall que controlam o tráfego para a instância
  - Ele existe fora do sistema operacional convidado da instância

- Na execução da instância, você especifica um **par de chaves** existente ou cria um novo par de chaves
- Um par de chaves consiste em:
  - Uma chave pública que a AWS armazena
  - Um arquivo de chave privada que você armazena
- Ele permite conexões seguras com a instância



