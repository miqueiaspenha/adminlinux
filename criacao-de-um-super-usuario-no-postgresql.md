CRIAÇÃO DE 1° SUPER USUÁRIO NO POSTGRESQL

Depois de instalado seu SGBD postgres, como criar seu 1° usuário? Qual a senha de root? Qual a senha padrão?

Esta dica é para iniciantes.

Após a instalação dos seu PostgreSQL no Linux, como criar seu 1° usuário para administração do banco?

Simples, na máquina com o banco instalado siga os seguintes passos.

Logue-se como root, tecle "su root" ou "sudo -i" no Ubuntu (no terminal a mensagem padrão deve terminar com #).

Entre como usuário postgres comando:

# su postgres

Conecte no banco comando:

$ psql

Agora deve aparecer a frase de boas vindas (Bem vindo ao psql...) e você está no terminal do posgres.

Entre com o comando:

CREATE USER nomedousuario SUPERUSER INHERIT CREATEDB CREATEROLE;

e tecle enter.

Depois entre com o comando:

ALTER USER nomedousuario PASSWORD 'senha';

e tecle enter.

Pronto! Usuário criado.

Agora para este usuário acessar o banco de outras máquinas da rede devemos liberar se acesso no arquivo pg_hba.conf com o usuário root, siga os passos.

A localização deste arquivo varia segundo a distribuição Linux, no SUSE está em ~postgres/data/pg_hba.conf, no Ubuntu está em /etc/postgres/8.4/pg_hba.conf. Adicione a linha:

host    all         nomedousuario         0/0                   password

Para que seu usuário tenha acesso de qualquer máquina a todos os bancos de dados neste servidor.

Feito isso reinicie o postgres ou recarregue como o comando:

# /etc/init.d/posgresql restart
ou
# /etc/init.d/posgresql reload