POSTGRESQL - ALTERANDO SENHA DO USUÁRIO POSTGRES

Assim como eu, acredito que outros usuários também tiveram algum problema na instalação do PostgreSQL no Ubuntu Linux.

Realizei a instalação do SGBD via Synaptic acreditando que ele também criaria o modo visual. Engano meu, pois necessita também da instalação do pgadmin III, e nele, necessita de realizar a conexão com o banco, solicitando desde a porta até o tipo de criptografia que será feita.

Na instalação do PostgreSQL ele não te dá nenhuma oportunidade de criar a senha do usuário "postgres", sendo assim, o comando abaixo resolverá:

$ sudo -u postgres psql

Em seguida, insira a tua senha de root.

Agora você está no console do PostgreSQL. Sendo assim, agora vamos alterar a senha do usuário:

# alter user postgres with encrypted password 'senha';

Pronto, agora você já poderá conectar facilmente neste SGBD.