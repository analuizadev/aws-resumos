
#### Banco de dados relacional

- [*] organiza os dados em **tabela**;
- [*] os dados em uma tabela **podem ser vinculados a dados em outras tabelas** para criar relacionamentos;
- [*] uma tabela armazena dados em linhas e colunas;
- [*] linhas contém todas as informações sobre uma entrada específica;
- [*] colunas descrevem atributos de uma entrada;
- [*] as tabelas, linhas, colunas e relacionamentos entre eles são chamados de **esquema lógico**;
- [*] com bancos de dados relacionais, um esquema é corrigido;
- [*] quando o banco estiver **operacional**, fica difícil alterar o esquema;
- [*] requer que a maioria da modelagem de dados seja feita antes que o banco fique ativo;

##### Sistema de gerenciamento de banco de dados relacional (RDBMS)

- [!] permite criar, atualizar e administrar um banco de dados relacional;
- exemplos de RDBMS:
	- MySQL;
	- PostgreSQL;
	- Oracle;
	- SQL server;
	- Amazon Aurora;
- você se comunica com m RDBMS usando consultas SQL (linguagem de consulta estruturada):
	- `SELECT * FROM table_name`

##### Benefícios de banco de dados relacional 

- *junções* : pode unir tabelas;
- *redundância reduzida* : pode armazenar dados em uma tabela e referenciá-los em outras tabelas em vez de salvar os mesmos dados em locais diferentes;
- *familiaridade* : profissionais têm familiaridade e experiência com esse tipo de banco de dados;
- *precisão* : garantem que seus dados persistam com alta integridade e estejam de acordo com o princípio de atomicidade, consistência, isolamento e durabilidade (ACID);

##### Casos de uso de bancos relacional 

- aplicações que têm um esquema sólido que **não muda com frequência**:
	- lift-and-shift elevam uma aplicações de on-premises e a move para a nuvem, com poucas ou nenhuma mudança;
- aplicações que precisam de **armazenamento persistente** que seguem o princípio ACID:
	- planejamento de recursos empresariais (ERP);
	- aplicações de gerenciamento de relacionamento com o cliente (CRM);
	- aplicações financeiras e comerciais;

##### Escolha entre banco de dados não gerenciados e gerenciados

- se quiser executar um banco de dados relacional na AWS, deve selecionar como deseja executá-lo: gerenciado ou não gerenciado;
- o gerenciado versus o não gerenciado funciona como a responsabilidade compartilhada;
- o modelo de responsabilidade compartilhada distingue as responsabilidades de segurança da AWS e as responsabilidades de segurança do cliente;
- da mesma forma, gerenciado versus não gerenciado pode ser entendido como uma troca entre conveniência e controle;

##### Banco de dados on-premises

- [!] se você opera um banco de dados relacional on-premises, você é responsável por:
	- os aspectos de operação;
	- a segurança;
	- a eletricidade do datacenter;
	- o gerenciamento de máquina host;
	- o gerenciamento do banco de dados;
	- a otimização de consultas;
	- o gerenciamento de dados do cliente;
- [!] responsabilidade por tudo, controle sobre tudo;

##### Banco de dados não gerenciado 

- [!] se você hospedar seu banco de dados no Amazon EC2, a AWS cuida:
	- da implementação;
	- da manutenção da infraestrutura física e do hardware;
	- da instalação do sistema operacional da instância do EC2;
- [!] você ainda seria responsável por:
	- gerenciar a instância do EC2;
	- gerenciar o banco de dados nesse host;
	- otimizar consultas;
	- gerenciar dados do cliente;
- [*] A AWS é **responsável e tem controle sobre o hardware e a infraestrutura subjacente**;
- [*] você é **responsável e tem controle sobre o gerenciamento do host e do banco de dados**;

![[Pasted image 20231219160616.png]]

##### Banco de dados gerenciado

- para transferir mais partes do trabalho para a AWS, usa-se o serviço de banco de dados gerenciado;
- [!] esses serviços fornecem:
	- configuração da instância do EC2 e do banco de dados;
	- sistemas para alta disponibilidade, escalabilidade, aplicações de patches e backups;
- [!] você ainda é responsável por:
	- ajuste no banco de dados;
	- otimização de consultas;
	- garantir que os dados do cliente estejam seguros;
- [*] essa opção fornece **maior conveniência**, mas a **menor quantidade de controle** em comparação com o banco de dados não gerenciado e banco de dados on-premises;

![[Pasted image 20231219161608.png]]

