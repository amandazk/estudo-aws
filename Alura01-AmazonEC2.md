# Deploy no Amazon EC2: Alta disponibilidade e escalabilidade de uma aplicação

## Primeiros passos na AWS

Add Storage: existe a máquina virtual (questão de processamento, memória, etc) e existe o disco, são serviços separados.

Security group: a máquina tá dentro da AWS. Como que eu acesso essa máquina? O security group é como se fosse o firewall. Para eu acessar, preciso do acesso SSH. 

- Essa parte de autenticação por SSH é feita através de chaves. Por default o AWS não vai deixar você usar usuário e senha para fazer o acesso. Tem que ter uma chave. Se você perder essa chave, perde o acesso à maquina virtual. 



## Gerenciando instâncias EC2

Temos várias regiões da AWS pelo mundo (ex: Ohio, N. Virginia, etc) e dentro dessas regiões existem zonas de disponibilidade.  

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