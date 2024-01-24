
- banco de dados serverless;
	- [!] não precisa gerenciar as instâncias que são utilizadas para o seu funcionamento ou a infraestrutura;
- banco de dados não relacional (NoSQL);
- o Amazon DynamoDB é totalmente gerenciado e fornece performance **alta** e **previsível** com **escalabilidade integrada**;
- **performático** tempos de respostas com latência de milissegundos;
- tem esquemas flexíveis, pode adicionar ou remover atributos ou itens a qualquer momento; 
- pode criar tabelas de banco de dados que podem armazenar e recuperar **qualquer quantidade de dados** e atender a **qualquer nível de tráfego** de solicitação;
- é possível aumentar e reduzir a escala na **vertical** da capacidade de taxa de transferência das tabelas sem tempo de inatividade ou degradação da performance;
- distribui **automaticamente** os dados e o tráfego de suas tabelas por um número suficiente de servidores para lidar com seus requisitos de taxa de transferência e de armazenamento;
- mantém performance **consistente** e **rápido**;
- todos os dados são armazenados em SSD;
- são **automaticamente replicados** entre várias AZs em uma região da AWS;
- oferecendo **alta durabilidade** de dados e **disponibilidade integradas**;

![[Pasted image 20231219184214.png]]

##### Como funciona

- os dados são armazenados em tabelas;
- uma tabela contém itens como atributos;
- itens como linhas;
- atributos como colunas;
- armazena os dados em **partições**;
- divide os itens da tabela em várias partições com base na chave-valor de partição;
- o DynamoDB processa o gerenciamento de partições;
- a chave de partição de um item também é conhecida como o seu **atributo de hash**;
- uma chave de classificação pode ser definida para armazenar todos os itens com a **mesma chave-valor** de partição fisicamente próximos;
	- ela pode ordená-los por chave-valor de classificação na partição;
	- apresenta uma relação de **um para muitos**, com base na chave de partição e permite a consulta no atributo de chave de classificação;

![[Pasted image 20231219201631.png]]

##### Componentes principais do Amazon DynamoDB

- tabelas, itens e atributos são os componentes principais com os quais trabalha;
- uma tabela é uma **coleção de itens**;
- cada item é uma **coleção de atributos**;
- DynamoDB usa chaves primárias para **identificar exclusivamente** cada item em uma tabela;
- usa índices secundários para fornecer mais **flexibilidade** de consulta;

- tabelas:
	- armazena dados em tabelas;
	- uma tabela é uma **coleção de dados**;
- itens:
	- cada tabela contém **zero ou mais** itens;
	- um item é um **grupo de atributos** que é **identificável exclusivamente** entre todos os outros itens;
	- **não há limite** para o número de itens que pode ser armazenado na tabela;
	- nem todos os itens precisam ter os mesmo atributos;
- atributos:
	- cada item é composto por **um ou mais atributos**;
	- um atributo é um **elemento de dados fundamental**, algo que não precisa ser dividido ainda mais;

![[Pasted image 20231219184159.png]]

![[Pasted image 20231219185120.png]]

##### Conceitos principais

- o DynamoDB é compatível com dois tipos diferentes de chaves primárias:
	- chaves de partição;
	- chaves de partição e classificação;
- chave de partição:
	- é uma **chave primária simples**, que é composta de **um atributo** chamado de chave de partição;
- chave de partição e a chave de classificação:
	- a chave de partição e a chave de classificação também são conhecidas como **chave primária composta**, que é composta de **dois atributos**;

###### Como o Amazon DynamoDB distribui dados

- como o DynamoDB armazena dados:
	- armazena dados em **partições**;
	- uma partição é uma **alocação de armazenamento para uma tabela**;
	- é baseada em unidades de estado sólido (SDD);
	- automaticamente replicada em várias AZs em uma região da AWS;
- como o DynamoDB armazena e recupera itens:
	- se a tabela tiver uma chave primária (uma chave de partição), o DynamoDB **armazenará** e **recuperará** cada item com base em sua **chave-valor de partição**;
- como o DynamoDB grava um item na tabela:
	- usa o valor da chave de partição como entrada para uma função de hash interna;
	- o valor de saída da função hash determina a partição na qual o item será armazenado;
- como o DynamoDB lê um item na tabela:
	- deve especificar a chave-valor de partição para o item;
	- o DynamoDB usa esse valor como entrada para sua função de hash, gerando a partição na qual o item pode ser encontrado;

##### Conceito de particionamento

- os dados da tabela são particionados e indexados por uma chave primária, à medida que os dados crescem;
- existem **duas maneiras** diferentes para recuperar dados de uma tabela do DynamoDB:
	- a *operação de consulta* usa o particionamento de tabela para localizar itens de forma eficaz usando a **chave primária**;
	- a *varredura* permite localizar itens na tabela correspondendo condições em atributos que não são chave;
		- oferece flexibilidade para localizar itens por outros atributos;
		- menos eficiente, lê todos os itens da tabela para encontrar o correspondente;

![[Pasted image 20231219202309.png]]

![[Pasted image 20231219220245.png]]

##### Tabelas globais

- oferece alta disponibilidade e escalabilidade entre regiões;
- é uma coleção de uma ou mais tabelas do DynamoDB, que devem todas pertencer a uma única conta da AWS;
- as tabelas na coleção também são conhecidas como **tabelas-réplica**;
- uma tabela-réplica é uma tabela única do DynamoDB que funciona como parte de uma tabela global;
- cada réplica armazena o mesmo conjunto de itens de dados;
- qualquer tabela global dada só pode ter **uma** tabela-réplica por região;
- cada réplica tem o **mesmo nome** de tabela e a **mesma definição de chave primária**;
- funcionam bem para aplicativos de grande escala com usuários dispersos pelo mundo;

##### Segurança no Amazon DynamoDB

- oferece **criptografia** em repouso;
	- elimina a carga e a complexidade operacionais envolvidas na proteção de dados confidenciais;

##### Benefícios técnicos do Amazon DynamoDB

- serviço totalmente gerenciado;
- consultas de baixa latência;
- controle de acesso refinado;
	- pode usar com o AWS IAM para obter controle de acesso refinado dos usuários da sua organização;
- flexibilidade;
	- oferece suporte ao armazenamento, à consulta e à atualização de dados na forma de documentos JSON; ideal para armazenar dados semiestruturados e manipulá-los usando consultas JSON;

