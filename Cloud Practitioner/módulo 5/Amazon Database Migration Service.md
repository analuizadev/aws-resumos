
- permite migrar bancos de dados relacionais e não relacionais e outros tipo de armazenamento de dados;
- *move dados entre bancos de dados* de origem e de destino;
- os bancos de dados de origem e de destino podem ser do *mesmo tipo* ou de *tipos diferentes*;
- durante a migração, o banco de dados de *origem* permanece *operacional*, reduzindo o tempo de inatividade em qualquer aplicativo que dependa do banco de dados;

##### Casos de uso

1. **MySQL :**
	1. você tem um banco de dados MySQL armazenado on-premises em uma instância EC2 ou no Amazon RDS. 
	2. Pense no banco de dados MySQL como seu banco de dados de origem. 
	3. Usando o AWS DMS, você pode migrar seus dados para um banco de dados de destino, por exemplo, um banco de dados do Amazon Aurora;
2. **Desenvolvimento e teste de migrações de banco de dados :**
	1. os desenvolvedores conseguem testar as aplicações com os dados de produção sem afetar os usuários de produção;
3. **Consolidação de banco de dados :**
	1. combinação de vários bancos de dados em um único banco de dados;
4. **Replicação contínua :**
	1. envio de cópias contínuas dos dados para outras fontes de destino em vez de fazer uma migração única;