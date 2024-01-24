
##### Armazenamento de instâncias do Amazon EC2

- armazenamento de bloco **temporário**;
- é um armazenamento pré-configurado que existe no mesmo servidor físico que hospeda a instância do EC2 e **não pode ser separado** do Amazon EC2;
- funciona como um HD interno;
- adequado para armazenamento temporário de informações que estão em constante mudança, como buffers, caches e dados scratch;
- **não se destina a dados persistentes ou duradouros**;

##### Amazon EBS 

- destinado a dados que mudam com frequência e precisam **persistir** por meio de paradas de instância, encerramentos ou falhas de hardware;
- dois tipos de volumes:
	- volume com suporte SSD:
		- performance depende de IOPS (operações de entrada/saída por segundo);
		- ideal para workloads transicionais, como bancos de dados e volumes de inicialização;
	- volume com suporte HDD:
		- performance depende de MB/s;
		- ideal para workloads com intensa taxa de transferência, como big data, data warehouses, processamento de log e E/S de dados sequenciais;
- armazenamento em bloco;
- paga pelo que provisionar;
- os volumes EBS são replicados em vários servidores em uma única zona de disponibilidade;
- a maioria dos volumes do EBS somente pode ser anexa a uma única instância do EC2 por vez;

##### Amazon S3

- recomendado para dados que não mudam com frequência;
- ideal para armazenar conteúdo estático da web e mídia, backups, arquivamento e dados para análise;
- hospeda sites estáticos inteiros com nomes de domínio personalizados;
- armazenamento de objetos;
- paga pelo o que usa;
- replica seus objetos em várias zonas de disponibilidade;
- não está conectado ao armazenamento do computador;

##### Amazon Elastic File System (EFS) e Amazon FSx

- armazenamento de arquivos que pode ser montado em várias instâncias;
- paga pelo o que usa;

![[Pasted image 20231218200548.png]]