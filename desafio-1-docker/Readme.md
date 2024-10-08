# Desafio 01 - Banco de Dados PostgreSQL #
Você está dando os primeiros passos no uso de containers. E a melhor forma de iniciar no mundo de containers é usar em ambiente de desenvolvimento.

Sua missão é ajudar a equipe de desenvolvimento a ter mais autonomia no desenvolvimento de projetos. E uma das reclamações da equipe é o setup local.

Crie um comando para criar um banco de dados PostgreSQL no ambiente do desenvolvedor de uma forma que cumpra os seguintes requisitos:

O nome do banco de dados deve ser curso_docker
O usuário de acesso ao banco deve ser docker_usr
A senha do usuário deve ser docker_pwd
Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual.

Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados PostgreSQL com esses requisitos.

***

**Resolução**

```shell 
docker run -itd --rm -p 5432:5432 --name desafio01-docker -e POSTGRES_DB=curso_docker -e POSTGRES_USER=docker_usr -e POSTGRES_PASSWORD=docker_pwd postgres:latest
```

Testando conexão com o banco de dados via console interativa do docker.

```shell
[root@poc-docker ~]# docker exec -it desafio01-docker /bin/bash
root@9f6e53709d9b:/# psql -U docker_usr curso_docker
psql (16.4 (Debian 16.4-1.pgdg120+1))
Type "help" for help.

curso_docker-# \list
                                                           List of databases
     Name     |   Owner    | Encoding | Locale Provider |  Collate   |   Ctype    | ICU Locale | ICU Rules |     Access privileges
--------------+------------+----------+-----------------+------------+------------+------------+-----------+---------------------------
 curso_docker | docker_usr | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           |
 postgres     | docker_usr | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           |
 template0    | docker_usr | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | =c/docker_usr            +
              |            |          |                 |            |            |            |           | docker_usr=CTc/docker_usr
 template1    | docker_usr | UTF8     | libc            | en_US.utf8 | en_US.utf8 |            |           | =c/docker_usr            +
              |            |          |                 |            |            |            |           | docker_usr=CTc/docker_usr
(4 rows)
```

**Obs: Lembrando que os desenvolvedores não especificaram versão do banco, portanto está sendo usado a tag latest.**