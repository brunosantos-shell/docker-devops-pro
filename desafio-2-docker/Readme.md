# Desafio 02 - Banco de Dados MySQL
Agora que a equipe tem como criar o banco de dados Postgres, crie o comando pra criar o banco de dados MySQL usando os requisitos abaixo:

O nome do banco de dados deve ser docker_db
O usuário de acesso ao banco deve ser docker_usr
A senha do usuário deve ser docker_pwd
Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual.

Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados MySQL com esses requisitos:

***

**Resolução**

```shell 
docker run -itd -p 3306:3306 --name desafio02-docker -e MYSQL_DATABASE=docker_db -e MYSQL_USER=docker_usr -e MYSQL_PASSWORD=docker_pwd -e MYSQL_ROOT_PASSWORD="ZG9ja2VyX3Bhc3N3b3JkXzIwMjQK" mysql:latest
```

Testando conexão com o banco de dados via console interativa do docker.

```shell
[root@poc-docker ~]# docker exec -it desafio02-docker /bin/bash
bash-5.1# mysql -u docker_usr -pdocker_pwd
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 9
Server version: 9.0.1 MySQL Community Server - GPL

Copyright (c) 2000, 2024, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| docker_db          |
| information_schema |
| performance_schema |
+--------------------+
3 rows in set (0.01 sec)
```

**Obs: Lembrando que os desenvolvedores não especificaram versão do banco, portanto está sendo usado a tag latest.**