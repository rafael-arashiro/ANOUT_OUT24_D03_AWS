
# Processo de instalação do banco de dados no EC2

Seguem os passos para instalar o banco de dados no EC2 da AWS:

* no terminal, digite: **sudo apt update** e **sudo apt install postgresql** para instalar o Postgresql;

* digite **sudo nano /etc/postgresql/*/main/postgresql.conf** e troque a linha **listen_addresses =** de **'localhost'** para __'*'__, utilize *Ctrl + O* para salvar e *Ctrl + X* para sair;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/db_images/1dblisten.png)
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/db_images/1dblisten2.png)

* digite **sudo -u postgres psql template1** para entrar no Postgres e digite **ALTER USER postgres with encrypted password '*NOVO_PASSWORD*';** para alterar a senha de acesso do Postgres, digite **quit** para sair do Posgres;

* digite **sudo nano /etc/postgresql/*/main/pg_hba.conf** e em IPv4 local connections coloque o IP 0.0.0.0/0, utilize *Ctrl + O* para salvar e *Ctrl + X* para sair;

![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/db_images/3dbconfig.png)

* então digite **sudo systemctl restart postgresql.service** para reiniciar o postgres;

* digite **sudo -u postgres psql -c 'create database compasscar'** para criar ao banco de dados;
