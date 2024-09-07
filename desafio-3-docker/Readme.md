# Desafio 03 - Banco de Dados MongoDB
 
Pra finalizar essa etapa, crie o comando pra criar o banco de dados MongoDB usando os requisitos abaixo:

O usuário root do banco deve ser mongo_usr
A senha do usuário root deve ser mongo_pwd
Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual.

Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados MongoDB com esses requisitos:
***

**Resolução**

```shell 
docker run -itd -p 27017:27017 --name desafio03-docker -e MONGO_INITDB_ROOT_USERNAME=mongo_pwd -e MONGO_INITDB_ROOT_PASSWORD=mongo_pwd -e mongo:latest
```

Testando conexão com o banco de dados via console interativa do docker.

```shell 
root@9ac59b98bb9a:/# mongosh --host localhost --port 27017
Current Mongosh Log ID: 66dc851796d1d62da35e739b
Connecting to:          mongodb://localhost:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.3.0
Using MongoDB:          7.0.14
Using Mongosh:          2.3.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/
```

**Obs: Lembrando que os desenvolvedores não especificaram versão do banco, portanto está sendo usado a tag latest.**