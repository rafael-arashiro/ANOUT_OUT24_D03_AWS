
# Processo de deploy da aplicação

Seguem os passos para fazer o deploy da API no EC2 da AWS:

* no terminal, digite **sudo yum check-update** para atualizar os pacotes da máquina;

* digite **sudo yum install git -y** para instalar o git;

* digite **curl -fsSL https://rpm.nodesource.com/setup_20.x | sudo bash -** e **sudo yum install nodejs -y**, para instalar o NodeJs;

* e digite **sudo npm install -g pm2** para instalar o pm2;

* clone o repositório da API com o comando **git clone https://github.com/rafael-arashiro/ANOUT24_D02_COMPASSCAR_PRIME_NODE** (é necessário a permissão e um token de acesso ao github);

* digite **cd ANOUT24_D02_COMPASSCAR_PRIME_NODE/** para entrar no diretório e **npm install** para instalar as dependências;

* digite **nano .env** e coloque as seguintes variáveis de ambiente:
    
    POSTGRES_HOST=Endereço IPv4 público da instância EC2 do banco de dados
    
    POSTGRES_DB=compasscar

    POSTGRES_USER=postgres

    POSTGRES_PASSWORD=Password do banco de dados

    JWT_SECRET=12345678

    JWT_EXPIRATION=1d

    ###USER

    DEFAULT_USER_NAME=rafael

    DEFAULT_USER_EMAIL=rafael@mail.com.br

    DEFAULT_USER_PASSWORD=rafael

    ###TEST

    POSTGRES_DB_TEST=compasscar-local

    POSTGRES_USER_TEST=root

    POSTGRES_PASSWORD_TEST=root

* utilize *Ctrl + O* para salvar e *Ctrl + X* para sair;

* digite **npm run build**;

* digite **pm2 start dist/main.js**;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/api_images/1apionline.png)

* digite **curl http://localhost:3000** para verificar se a API está rodando;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/api_images/2apionline2.png)

* utilize o **DNS IPv4 público**, na porta 3000 para acessar a api;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/api_images/3apiendereco.png)

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/api_images/3apiendereco2.png)

* coloque **/api** no fim do endereço para entrar na documentação da API;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/api_images/3apiendereco3.png)