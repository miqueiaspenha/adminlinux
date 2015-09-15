Liberando conexões remotas ao PostgreSQL

Os arquivos encontram-se em /etc/postgresql/versao/main

No postgresql.conf vamos editar a seguinte linha:

#listen_addresses = ‘localhost’ # what IP address(es) to listen on

Alterar para:

listen_addresses = '*' # what IP address(es) to listen on

Liberando as conexões no arquivo pg_hba.conf:

Por padrão o arquivo vem com a seguinte configuração:

# “local” is for Unix domain socket connections only


local all all trust


# IPv4 local connections:


host all all 127.0.0.1/32 trust


# IPv6 local connections:


host all all ::1/128 trust

Para liberar o acesso remoto basta criar uma nova regra seguindo o seguinte padrão:

Acesso liberado sem senha:

host all all 0.0.0.0/0 trust

Acesso liberado com senha:

host all all 0.0.0.0/0 md5

É possível também liberar o acesso apenas a uma rede específica:

host all all 192.168.0.0/32 md5

Ou também, informar qual usuário poderá conectar:

host all usuariodobanco 192.168.0.0/32 md5

Também informar qual o banco de dados a ser conectaro por este usuário:

host bancodedados usuariodobanco 192.168.0.0/32 md5

Na regra acima, o usuário usuariodobanco poderá conectar-se apenas ao banco bancodedados apenas se estiver dentro da rede 192.168.0.0.