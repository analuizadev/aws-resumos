
- banco de dados *relacional*;
- banco de dados relacionais usam *linguagem de consulta estruturada (SQL)*;
- essa abordagem permite que os dados sejam armazenados de forma facilmente compreensível, consistente e dimensionável;
- tem inúmeras opções de segurança diferentes;
- muitos mecanismos de dados do Amazon RDS oferecem criptografia em repouso (protegendo os dados enquanto estão armazenados) e criptografia em trânsito (protegendo os dados enquanto estão sendo enviados e recebidos);

![[Pasted image 20231226163458.png]]

##### Mecanismos de banco de dados do Amazon RDS

- *seis* mecanismos de banco de dados, que otimizam memória, desempenho ou entrada/saída:
	- Amazon Aurora;
	- PostgreSQL;
	- MySQL;
	- MariaDB;
	- Oracle Database;
	- Microsoft SQL Server;

##### Amazon Aurora

- nível empresarial;
- compatível com o MySQL e PostgreSQL;
- até *cinco vezes mais rápido* do que os bancos de dados MySQL comuns;
- até *três vezes mais rápido* do que os bancos de dados PostgreSQL comuns;
- ajuda a reduzir custos do banco de dados *reduzindo operações* desnecessárias de entrada/saída;
- considere o Aurora se as cargas de trabalho exigem *alta disponibilidade*;
	- replica *seis cópias* de seus dados em três AZs e faz backup contínuo de seus dados para o Amazon S3;
