# Deploy no Amazon EC2: Alta disponibilidade e escalabilidade de uma aplicação

## Primeiros passos na AWS

Add Storage: existe a máquina virtual (questão de processamento, memória, etc) e existe o disco, são serviços separados.

**Security group**: a máquina tá dentro da AWS. Como que eu acesso essa máquina? O security group é como se fosse o firewall. Para eu acessar, preciso do acesso SSH. 

- Essa parte de autenticação por SSH é feita através de **chaves**. Por default o AWS não vai deixar você usar usuário e senha para fazer o acesso. Tem que ter uma chave. Se você perder essa chave, perde o acesso à maquina virtual. 



## Gerenciando instâncias EC2

Temos várias **regiões** da AWS pelo mundo (ex: Ohio, N. Virginia, etc) e dentro dessas regiões existem **zonas de disponibilidade**.  

Para acessar a máquina criada (EC2), uso o IPv4 Public IP, por SSH. Se eu clicar em 'Connect', na página da instância, o site me disponibiliza o comando para eu usar no terminal.

O IP da máquina é dinâmico. Se eu parar com ela e voltar, esse IP vai ser alterado. Tem como alterar essa configuração.

Mudar a chave para somente leitura pelo dono:

```bash
chmod 400 aws-amanda.pem
```

- Na instância, em 'Actions', 'Change Termination Protection' : você inibe que a máquina seja terminada (destruída)
- Essas máquinas (EC2) são todas criadas dentro de uma mesma sub-rede
  - Para ver essa comunicação entre elas, posso dar um ping. Mas para fazer isso, preciso dar autorização à máquina
  - Em 'Security Groups', adicionar o grupo 'default'  àquelas máquinas que querem se comunicar



## Automatizando a instância EC2

- AWS Marketplace: imagens prontas para você escolher
- Você pode também criar a sua própria imagem
  - User data: permite que eu coloque, linha a linha, o script que eu quero fazer
    - script.sh:

```shell
#!/bin/bash
yum update -y
amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2
yum install -y httpd mariadb-server
systemctl start httpd
systemctl enable httpd
systemctl start mariadb
systemctl enable mariadb
usermod -a -G apache ec2-user
chown -R ec2-user:apache /var/www
```

- Posso usar a instância para generar uma imagem



## Imagens e Elastic IP

- Para criar uma imagem com a instância que você tem, basta selecionar a instância, clicar em 'Actions' -> 'Image' -> 'Create Image'
- Para depois usar essa imagem, é necessário ir no painel de instâncias, clicar em 'Launch Instance' e ir em 'My AMIs'

Para criarmos uma imagem a partir de uma instância, o que devemos fazer? Parar a instância e criar a imagem. Desta forma, garantimos a integridade dos dados.

**Elastic IP**:

O uso do **Elastic IP** garante que a sua máquina mantenha um IP único, mesmo que seja desligada, ou mesmo reiniciada

O IP muda se eu, por exemplo, desligo a máquina as 22h e ligo ela no outro dia de manhã. Para lidar com isso, vou até a área de Elastic IP e na opção 'Allocate Elastic IP address'. O IP criado não é associado automaticamente com a sua máquina, você deve fazer isso.

**Cobrança**: se a máquina estiver no ar, você pode ter um IP estático associado à ela, para ser gratuito. Se a máquina estiver parada, embora o IP esteja associado, ele não está em uso. 

Um IP por EC2 é gratuito, caso a máquina mantenha-se ligada



## Banco de dados no Amazon RDS

O RDS vai preparar uma máquina rodando o MySQL ou outro SGBD da sua escolha. Você não precisa administrar. Para isso, vai ser criada uma instância com o SGBD.

- Create database

Você pode programar o RDS para fazer backups automáticos.

- Para a conexão, o host seria o endpoint



## Infraestrutura para alta disponibilidade

Tenho que deixar a imagem certinha, com tudo o que quero nela (permissões, por exemplo) para que quando eu precisar disponibilizar ela em grande quantidade, já esteja tudo configurado corretamente.

- Para criar a imagem, precisamos parar a imagem que vai ser usada como base

```bash
sudo shutdown -h now
```



## Escalabilidade e alta disponibilidade

- **Load Balancing**: é onde chega o tráfego de entrada. Esse tráfego é então distribuído para as instâncias. 

Application Load Balancer: HTTP e HTTPS

Network Load Balancer: TCP, TLS, UDP

Para que o Load Balancer funcione, é necessário escolher pelo menos duas zonas de disponibilidade. O load balancing vai olhar para as intâncias, mas essas instâncias devem estar agrupadas em um Target Group. Na hora de registrar esses targets, relacionar o load balancing com as instâncias, não vou fazer isso com as instâncias em si, mas sim com um grupo de instâncias com auto scaling que vai ser criado.

- **Auto Scaling**: primeiro criar uma configuração e depois lançar o serviço. Marcar a opção que o Auto Scaling vai receber tráfego do Load Balancer e selecionar o Target Group.

Para criarmos grupos de auto scaling para as instâncias EC2, é necessário:

- Definir pelo menos duas sub-redes. Lembrando ainda que as sub-redes devem coincidir com o ELB (Elastic Load Balancing)
- Criar primeiro um templante de configuração (launch config)

Agora, o IP de chegada não é mais o da instância e sim o do Load Balancer. 

Para adicionar ou remover instâncias dentro do grupo de *auto scaling*, são utilizados como referência:

- Estado da EC2 (*stopping*, *terminated*, etc)
- Aplicação, por exemplo se a porta 80 (HTTP) está respondendo

**Nas configurações do grupo, você pode definir ELB (teste da aplicação) ou EC2 (estado da instância)



## AWS Command Line Interface

### Instalando a AWS CLI

- https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html
- Seguir a documentação
- Adicionar ao path 
- Rodar:

```bash
./aws configure
```

 Vai pedir a chave. Você pode criar um user com o IAM do AWS
