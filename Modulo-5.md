# Módulo 5

## Redes e entrega de conteúdo

### Seção 1 - Noções básicas de rede

Uma **rede de computadores** é duas ou mais máquinas conectadas juntas para se comunicar. Uma rede pode ser particionada logicamente em sub-redes. A rede requer um dispositivo de rede, como um roteador ou um switch. Isso conecta todas as máquinas e permite a comunicação entre elas.

Cada máquina na rede tem um endereço exclusivo de **Internet Protocol** atribuído a ela. Um endereço IP é um número exclusivo, atribuído a uma máquina para identificá-la de forma exclusiva.

Um formato comum para descrever redes e grupos de endereços IP é Classless Inter-Domain Routing (ou **CIDR**). Um endereço CIDR é expresso como um endereço IP, que é o primeiro endereço da rede. Em seguida, ele é seguido por um caractere ''/''. O numero após o ''/'' informa quantos bits do prefixo de roteamento devem ser estáveis e alocados para o identificador de rede.

 **Modelo OSI**: é um modelo conceitual usado para explicar dados à medida que percorrem uma rede. Consiste em sete camadas e mostra os protocolos e endereços comuns que são usados para enviar dados em cada camada.



### Seção 2 - Amazon VPC (Amazon Virtual Private Cloud)

É um serviço que permite provisionar uma seção isolada logicamente da Nuvem AWS onde você pode executar recursos da AWS em uma rede virtual que você mesmo define. Fornece controle sobre seus recursos de rede virtual, incluindo:

- Seleção do intervalo de endereços IP
- Criação de sub-redes
- Configuração de tabelas de rotas e gateways de rede

Permite personalizar a configuração de rede para sua VPC e usar várias camadas de segurança.

Você pousa máquinas virtuais e outros recursos dentro de uma VPC.

A Amazon VPC permite provisionar **VPC**s. Uma VPC é uma rede virtual isolada logicamente de outras redes virtuais na Nuvem AWS. Elas são dedicadas à sua conta  e **pertencem a uma única região da AWS**. Podem abranger **várias zonas de disponibilidade**. Depois de criar uma VPC, você pode dividi-la em uma ou mais sub-redes. 

Uma **sub-rede** representa um segmento isolado de sua VPC com seu próprio intervalo de endereços IP. Elas **pertencem a uma única zona de disponibilidade**. Você pode criar sub-rede em diferentes zonas de disponibilidade para alta disponibilidade. Elas podem ser **públicas ou privadas**.

**Endereçamento IP**: habilitam recursos em sua VPC para se comunicarem entre si e também recursos na Internet. Ao criar uma VPC, você atribui um bloco CIDR IPv4, o que significa um intervalo de endereços IPv4 privados.

![image-20210508215955832](C:\Users\Amanda\Documents\AWS\imagens\imagem-2.png)

**Interface de rede elástica**:

- É uma interface de rede virtual que você pode:
  - Anexar a uma instância
  - Separar da instância e anexar a outra instância para redirecionar o tráfego
- Seus atributos a seguem quando são reanexadas a uma nova instância
- Cada instância em sua VPC tem uma interface de rede padrão que recebe um endereço IPv4 privado do intervalo de endereços IPv4 de sua VPC

**Tabela de rotas**: contém um conjunto de regras(ou rotas) que você pode configurar para direcionar o tráfego de rede da sub-rede. Cada rota especifica um destino e um 'alvo'. Por padrão, toda tabela de rotas contém uma rota local para comunicação dentro da VPC. Cada sub-rede deve estar associada a uma tabela de rotas (no máximo uma).



### Seção 3 - Redes VPC

Um **gateway** da Internet é um componente da VPC escalável, redundante e altamente disponível que permite a comunicação entre instâncias na VPC e a Internet pública. Um gateway da Internet tem duas finalidades:

1 -  Para fornecer um destino nas tabelas de rotas da VPC para tráfego de Internet

2 - Para executar a conversão de endereços de rede para instâncias que receberam endereços IPv4 públicos

Para tornar uma sub-rede pública, anexe um gateway da Internet à VPC e adicione uma entrada de rota à tabela de rotas associadas à sub-rede. Um **gateway de conversão de endereços de rede, ou NAT**, permite que instâncias em uma sub-rede privada se conectem à Internet ou a outros serviços da AWS. Mas isso impede que a Internet pública inicie uma conexão com essas instâncias.

**AWS Direct Connect**: permite estabelecer uma conexão privada dedicada entre a rede e um dos locais de conexão direta. Essa conexão privada pode aumentar a largura de banda e o throughput, além de fornecer uma experiência de rede mais consistente do que  as conexões baseadas na Internet ou as conexões VPN.

Um VPC **endpoint** é um dispositivo virtual que permite que você conecte sua VPC de forma privada a esses serviços da AWS compatíveis.

**AWS PrivateLink**: requer um endpoint de interface VPC. Simplifica a segurança dos dados compartilhados com aplicativos baseados na nuvem, eliminando a exposição dos dados à Internet pública.

![image-20210509104010813](C:\Users\Amanda\Documents\AWS\imagens\imagem-3.png)



**Laboratório - Crie sua VPC e execute um servidor web**

Nesta tarefa, você usará o assistente de VPC para criar uma  VPC, um gateway da Internet e duas sub-redes em uma única zona de  disponibilidade. Um **gateway da Internet (IGW)** é um componente da VPC que permite a comunicação entre instâncias na VPC e a Internet.

Depois de criar uma VPC, você poderá adicionar **sub-redes**. Cada sub-rede reside inteiramente dentro de uma zona de disponibilidade e não pode incluir outras zonas. Se o tráfego de uma sub-rede for  roteado para um gateway da Internet, a sub-rede será chamada de *sub-rede pública*. Se a sub-rede não tiver uma rota para o gateway da Internet, ela será chamada de *sub-rede privada*.

O assistente também criará um *gateway NAT*, que é usado para fornecer conectividade com a Internet para instâncias do EC2 nas sub-redes privadas.

O assistente provisionou uma VPC com uma sub-rede pública e uma  sub-rede privada na mesma zona de disponibilidade, com tabelas de rotas  para cada sub-rede:

![image-20210510150840265](C:\Users\Amanda\Documents\AWS\imagens\imagem-4.png)

A sub-rede pública tem o CIDR **10.0.0.0/24**, o que significa que contém todos os endereços IP que começam com **10.0.0.x**.

A sub-rede privada tem o CIDR **10.0.1.0/24**, o que significa que contém todos os endereços IP que começam com **10.0.1.x**.

- Você configurará as sub-redes privadas para rotear o tráfego  destinado à Internet para o gateway NAT de modo que os recursos na  sub-rede privada possam se conectar à Internet e se manter privados ao  mesmo tempo. Para fazer isso, configure uma *tabela de rotas*.

Sua VPC agora tem sub-redes públicas e privadas configuradas em duas zonas de disponibilidade:

![image-20210510152240059](C:\Users\Amanda\Documents\AWS\imagens\imagem-5.png)

A arquitetura completa que você implantou é:

![image-20210510160633116](C:\Users\Amanda\Documents\AWS\imagens\imagem-6.png)



### Seção 4 - Segurança da VPC

Você pode incorporar segurança em sua arquitetura de VPC de várias maneiras para ter controle total sobre o tráfego de entrada e saída. 

1 - **Grupos de segurança**

2 - **Lista de controle de acesso à rede**

Um grupo de segurança atua como um firewall virtual que controla o tráfego de entrada e saída de e para sua instância. Eles atuam no nível da instância.

Listas de controle de acesso à rede funcionam no nível da sub-rede e controlam o tráfego de entrada e saída da sub-rede.  

![image-20210510161438883](C:\Users\Amanda\Documents\AWS\imagens\imagem-7.png)



### Seção 5 - Amazon Route 53  

Resolução **DNS** é o processo de converter um nome interno para o endereço IP correspondente. Esse protocolo funciona como uma agenda telefônica em que os nomes da Internet são substituídos pelos endereços IP das máquinas correspondentes.

**Amazon Route 53** permite registrar um nome de domínio, como 'yourcompany.com', e fazer com que o serviço lide com os nomes e os hosts relacionados a esse domínio. Ele oferece suporte a vários tipos de políticas de roteamento. Eles determinam como ele responde às consultas de resolução de nomes.

O **failover de DNS** do Amazon Route 53 permite que você melhore a disponibilidade do seu aplicativo executado na AWS configurando cenários de backup e failover para seus aplicativos. 



### Seção 6 - Amazon CloudFront 

Uma rede de entrega de conteúdo é uma parte essencial de uma experiência de usuário sem problemas. **Amazon CloudFront** é um serviço de entrega de conteúdo rápido que entrega dados aos clientes com segurança e altas velocidades de transferência. Ele também oferece um ambiente amigável para desenvolvedores.

O CloudFront entrega arquivos aos usuários por meio de uma rede global de pontos de presença.

**Pontos de presença**: rede de datacenters que o CloudFront usa para fornecer conteúdo popular rapidamente aos clientes

**Cache de ponto regional**: localização do CloudFront que armazena em cache conteúdo que não é popular o suficiente para permanecer em um ponto de presença. Ele está localizado entre o servidor de origem e o ponto de presença global.



