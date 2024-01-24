
- permite que os clientes criem e gerenciem banco de dados relacionais na nuvem sem a carga operacional do gerenciamento de banco de dados tradicional;
- o Amazon RDS descarrega parte do trabalho não relacionado de criar e gerenciar um banco de dados;
- você se concentra nas tarefas que diferenciam sua aplicação como provisionamento, aplicação de patches, escalabilidade e restauração;
- mecanismo suportados do Amazon RDS são:
	- [*] comercial: Oracle, SQL Server;
	- [*] open source: MySQL, PostgreSQL, MariaDB;
	- [*] nativo da nuvem: Amazon Aurora;
- a opção nativa da nuvem, é compatível com MySQL e PostgreSQL construído para nuvem;
- é **mais durável**, **mais disponível** e oferece **performance mais rápida** do que a versão do Amazon RDS do MySQL e do PostgreSQL;
- deve ser usado para **transações ou consultas complexas**;
- **alta escalabilidade**, pode escalar elasticamente além das limitações da capacidade uma única instância de DB

##### Instâncias de banco de dados

- o Amazon RDS é baseado em computação e armazenamento;
- parte da computação é chamada de **instância de banco de dados**;
	- executa o mecanismo de banco de dados;
	- [!] dependendo do mecanismo da instância de banco de dados escolhido, ele terá diferentes recursos e configurações com suporte;
- uma instância de banco de dados **pode conter vários banco de dados** com o mesmo mecanismo, e cada banco pode conter várias tabelas;
- abaixo da instância do banco de dados há uma instância do EC2;
	- [!] essa instância é gerenciada por meio do **console do Amazon RDS** em vez do console do Amazon EC2;
- ao criar sua instância de banco de dados você escolhe o tipo e o tamanho da instância:
	- [*] standard (padrão) : inclui instâncias de uso geral;
	- [*] memory optimized : é otimizada para aplicações que usam muita memória;
	- [*] burstable performance : fornece um nível de performance de linha de base, com capacidade de intermitência para o uso total da CPU; 

![[Pasted image 20231219165316.png]]

- a instância de banco de dados escolhida afeta a **quantidade de capacidade e processamento e memória** que ela tem;
- as opções disponíveis dependem do mecanismo selecionado;
- uma instância de banco de dados, assim com uma do EC2, **usa volumes** do Amazon EBS (Elastic Block Store) como sua **camada de armazenamento**;
- pode escolher entre os seguintes tipos de armazenamento em volume do Amazon EBS:
	- [*] uso geral (SSD);
	- [*] IOPS provisionadas (SSD);
	- [*] armazenamento magnético (**não recomendado**);

![[Pasted image 20231219165625.png]]

##### Amazon RDS em uma Amazon Virtual Private Cloud


- ao criar uma instância de banco de dados, você seleciona a Amazon VPC em que ficarão seus bancos de dados;
- em seguida, as sub-redes em que deseja que as instâncias de banco de dados sejam colocadas;
	- [!] isso é chamado de **grupo de sub-redes de banco de dados**;
-  para criar uma sub-redes de banco de dados, especifique o seguinte:
	- zonas de disponibilidade (AZs) : incluem as sub-redes que você deseja adicionar;
	- sub-redes : na AZ em que estão suas instâncias de banco de dados;
- as sub-redes que você adicionar **devem ser privadas**, para que elas não tenham uma rota para o gateway da internet;
	- [!] garante que sua instância de banco de dados e os dados dentro dela somente possam ser acessados pelo back-end da aplicação;
- o acesso à instância de banco de dados pode ser ainda **mais restrito usando Network ACLs** (listas de controle acesso à rede) e **grupos de segurança**;
	- [!] o uso desses controles fornece camadas de segurança para sua infraestrutura;

##### Proteger Amazon RDS com AWS Identity and Access Management (IAM)

- as Network ACLs e os grupos de segurança ajudam os usuários a **ditar o fluxo de tráfego**;
- se quiser restringir as **ações** e os **recursos** que outros podem acessar, você pode usar políticas do IAM;

##### Fazer backup de dados

- para fazer backups regulares de sua instância do RDS, pode usar:
	- [*] backups automáticos;
	- [*] snapshots manuais;

###### Backups automáticos

- são ativados por padrão;
- faz backup de **toda a sua instância de banco de dados** (não apenas bancos de dados individuais na instância) e **seus logs de transações**;
- ao criar sua instância de banco de dados, você define uma **janela de backup** que é o período em que os backups automáticos ocorrem;
- é recomendado definir as janelas de backups em períodos que o banco de dados está com pouca atividade, pois isso pode causar **maior latência** e **tempo de inatividade**;
- você pode reter seus backups automatizados entre **0 e 35 dais**;
	- [!] a configuração de 0 dias **impede** os backups automáticos, e também **excluirá todos os backups automatizados existentes**;
- o benefício de ter backups automatizados é ter a capacidade fazer **recuperação point-in-time**;
- a recuperação point-in-time **cria uma nova instância** de banco de dados **usando dados restaurados** em momento específico;
- esse método de restauração fornece **mais granularidade** com a restauração do backup completo e reversão das transações até o intervalo de tempo específico;

![[Pasted image 20231219171817.png]]

###### Snapshots manuais

- mantem seus backups automatizados por **mais de 35 dias**;
- são como tirar snapshots do Amazon EBS, a diferença é que são gerenciados no console do Amazon RDS;
- esses são backups que pode iniciar a **qualquer momento**;
- eles existem até você excluí-los;
- se restaurar dados de um snapshot manual, ele **criará uma nova instância** de banco de dados **usando os dados do snapshot**;

![[Pasted image 20231219172127.png]]

##### Opções de backup

- é aconselhável implantar **as duas opções**;
- os backups automatizados são benéficos para a **recuperação point-in-time**;
- snapshots manuais permitem **reter backups por mais de 35 dais**;

##### Redundância com o Amazon RDS Multi-AZ

- quando habilita o Amazon RDS Multi-AZ, o Amazon RDS **cria uma cópia redundante do banco de dados em outra AZ**;
- acaba com duas cópias de bancos de dados:
	- [*] uma cópia primária em uma sub rede em uma AZ;
	- [*] uma cópia em standby (secundária) em uma sub-rede em uma segunda AZ;
- a cópia principal do banco de dados **fornece acesso aos dados** para que as aplicações possam **consultar e exibir informações**;
- os dados na cópia primária são replicados de forma síncrona para a cópia em standby;
- a cópia me standby **não é considerada um banco de dados ativo** e **não é consultada por aplicações**;
- para melhorar a disponibilidade o Amazon RDS Multi-AZ garante que você tenha duas cópias do banco de dados em **execução** e que **uma** delas esteja na **função principal**;
- se surgir um problema de disponibilidade, o Amazon RDS acionará um failover automático;
- quando você cria uma instância de banco de dados, um nome do Domain Name System (DNS) é fornecido;
- a AWS usa esse nome DNS para o failover para o banco de dados em standby;
- em um failover automático, o banco de dados em standby é **promovido para a função principal** e as consultas são **redirecionadas** para o novo banco de dados primário;
- para garantir que você não perca a configuração Multi-AZ, um novo banco de dados em standby é criado por qualquer um deles:
	- [*] rebaixar o primário anterior para standby se ele ainda estiver ativo e em execução;
	- [*] uma nova instância de banco de dados em standby;
- o motivo pelo qual você pode selecionar várias sub-redes para um banco de dados do Amazon RDS é devido à configuração Multi-AZ;
- você vai garantir que tenha usado sub-redes em diferentes AZs para suas cópias primárias e em standby;
