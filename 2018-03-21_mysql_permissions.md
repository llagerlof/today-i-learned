# Permissões para usuários do MySQL

Além de adicionar e remover permissões, é conceder permissões para um usuário acessar o servidor do MySQL com uma senha específica para cada máquina cliente que ele estiver usando, e uma senha geral para todas as outras. 

Uma das vantagens é que no computador do trabalho ou de casa o usuário pode querer acessar o banco sem ter que digitar a senha, e ser obrigado a digitar a senha em todos os outros.

Obs: Se o seu usuário não tiver GRANT, acesse o MySQL como root para poder configurar as permissões.

## Como conceder permissões

Dar todas as permissões para um usuário acessar todas as tabelas de todos os bancos de dados de um servidor a partir de qualquer computador:

```grant all on *.* to 'usuario'@'%' identified by 'senha';```


Dar todas as permissões para um usuário acessar todas as tabelas de um banco de dados especifico de um servidor a partir de qualquer computador:

```grant all on database.* to 'usuario'@'%' identified by 'senha';```


Dar apenas a permissão de SELECT para um usuário acessar todas as tabelas de um banco de dados especifico de um servidor a partir de qualquer computador:

```grant SELECT on database.* to 'usuario'@'%' identified by 'senha';```


Dar as permissões de SELECT e UPDATE para um usuário acessar todas as tabelas de um banco de dados especifico de um servidor a partir de qualquer computador:

```grant select,update on database.* to 'usuario'@'%' identified by 'senha';```


Dar as permissões de SELECT para um usuário acessar todas as tabelas de um banco de dados especifico de um servidor a partir de um IP específico:

```grant select on database.* to 'usuario'@'1.2.3.4' identified by 'senha';```


Dar todas as permissões para um usuário acessar o banco de dados a partir do próprio computador, sem senha. 

Também dar todas as permissões para que o banco possa ser acessado de qualquer outro computador, com senha.

```grant all on database.* to 'usuario'@'1.2.3.4' identified by '';```

```grant all on database.* to 'usuario'@'%' identified by 'senha';```


## Como verificar as permissões de um usuário

Listar as permissões:

```show grants for usuario;```

Listar os IPs de origem e os hashes das senhas de um usuário:

```select host, user, password from user where user = 'usuario';```


## Como trocar a senha de um usuário, por origem (host):

O usuário pode ter uma senha diferente para cada IP de origem. Se quiser que o usuário acesse sem senha para um host específico, basta passar uma string vazia para a função PASSWORD:

 ```SET PASSWORD FOR 'usuario'@'1.2.3.4' = PASSWORD('senha');```

Como remover uma entrada da tabela user (remover o acesso de um usuário para um host específico, lembrando que o host % são todos):

```drop user 'usuario'@'1.2.3.4';```

---

*keywords: mysql, permissions, database, banco de dados, tutorial*
