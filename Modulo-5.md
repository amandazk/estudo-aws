# Módulo 5

## Redes e entrega de conteúdo

### Seção 1 - Noções básicas de rede

Uma **rede de computadores** é duas ou mais máquinas conectadas juntas para se comunicar. Uma rede pode ser particionada logicamente em sub-redes. A rede requer um dispositivo de rede, como um roteador ou um switch. Isso conecta todas as máquinas e permite a comunicação entre elas.

Cada máquina na rede tem um endereço exclusivo de **Internet Protocol** atribuído a ela. Um endereço IP é um número exclusivo, atribuído a uma máquina para identificá-la de forma exclusiva.

Um formato comum para descrever redes e grupos de endereços IP é Classless Inter-Domain Routing (ou **CIDR**). Um endereço CIDR é expresso como um endereço IP, que é o primeiro endereço da rede. Em seguida, ele é seguido por um caractere ''/''. O numero após o ''/'' informa quantos bits do prefixo de roteamento devem ser estáveis e alocados para o identificador de rede.

 **Modelo OSI**: é um modelo conceitual usado para explicar dados à medida que percorrem uma rede. Consiste em sete camadas e mostra os protocolos e endereços comuns que são usados para enviar dados em cada camada.



### Seção 2- Amazon VPC (Amazon Virtual Private Cloud)

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





