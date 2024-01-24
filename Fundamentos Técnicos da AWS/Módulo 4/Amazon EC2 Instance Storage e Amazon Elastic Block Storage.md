
##### Armazenamento de instância do Amazon EC2

- oferece armazenamento temporário no nível de bloco para uma instância;
- esse armazenamento está localizado em discos que estão anexados fisicamente ao computador host;
- isto vincula o ciclo de vida dos dados ao ciclo de vida da instância do EC2;
- **se você excluir a instância, o armazenamento de instância também é excluído**;
- é ideal se você hospedar aplicações que replicam dados para outras instâncias do EC2, como clusters do Hadoop;
- também é ideal para armazenar temporariamente informações que são alteradas com frequência, como buffers, caches, dados transitórios e outros conteúdos temporários;

##### Amazon Elastic Block Storage (Amazon EBS)

- dispositivo de armazenamento em **nível de bloco** que você pode anexar a uma instância do Amazon EC2;
- esses dispositivos de armazenamento são chamados de volumes do Amazon EBS;
- os volumes EBS são unidades de tamanho configurado pelo usuário conectadas a uma instância EC2 (tipo um HD externo);
- a maioria dos volumes do Amazon EBS **só pode ser conectado a um computador por vez**, eles tem um **relacionamento individual com instâncias do EC2, não podem ser compartilhados ou anexados a várias instâncias ao mesmo tempo**;
	- OBS: ==a AWS anunciou um recurso de multiconexão do Amazon EBS que permite que volumes sejam anexados a várias instâncias do EC2 ao mesmo tempo; esse recurso não está disponível para todos os tipos de instância e todas as instâncias devem estar na mesmo AZ;==
- você **pode desanexar um volume do EBS de uma instância do EC2 e anexá-lo a outra** instância do EC2 na mesma zona de disponibilidade, para acessar os dados nele;
- o volume EBS funciona como um HD externo, se algo acontecer com o computador seus dados estarão a salvo;
- **limitação máxima** de quanto conteúdo pode ser armazenado;

##### Escalar volume do Amazon EBS

- é possível dimensionar volumes EBS de duas maneiras:
	1. aumente o tamanho do volume, desde que ele não ultrapasse o limite máximo de tamanho; a **quantidade máxima de armazenamento** que você pode ter é de **16TB**; se você provisionar um volume do EBS de 5TB, poderá optar por aumentar o tamanho do volume até chegar a 16TB;
	2. anexe vários volumes a uma única instância do EC2; o EC2 tem um **relacionamento de um para muitos** com volumes do EBS; você pode adicionar esses volumes adicionais durante ou após a criação da instância do EC2 para fornecer mais capacidade de armazenamento para seus hosts;

##### Casos de uso do Amazon EBS

- útil quando precisa recuperar dados rapidamente e fazer com que os dados persistam a longo prazo;
- são comumente usados nos seguintes cenários:
	- **sistemas operacionais:** volumes de inicialização/raiz para armazenar um sistema operacional; o dispositivo raiz de uma instância executada por meio de uma imagem de máquina da Amazon (AMI), geralmente, é um volume do Amazon EBS; são comumente chamados de ==AMIs com suporte de EBS==;
	- **bancos de dados:** uma camada de armazenamento para bancos de dados em execução no Amazon EC2 que depende de leituras e gravações transacionais;
	- **aplicações corporativas:** o Amazon EBS fornece armazenamento em bloco confiável para executar aplicações essenciais aos negócios;
	- **aplicações com alta taxa de transferência:** aplicações que executam leituras e gravações longas e contínuas;

##### Tipos de volume do Amazon EBS

- os volumes EBS são organizados em duas categorias principais:
	- unidades de estado sólido (SSD):
		- alta performance para entrada/saída (E/S) aleatória;
	- unidades de disco rígido (HDD):
		- alta performance para E/S sequencial;

\* ==IOPS: operações de entrada e saída por segundo;==

![[Pasted image 20231211181611.png]]

##### Benefícios do Amazon EBS

- alta disponibilidade
	- quando você cria um volume do EBS, ele é replicado automaticamente em sua AZ para evitar a perda de dados de pontos únicos de falha;
- persistência de dados
	- o armazenamento persiste mesmo quando sua instância não;
- criptografia de dados
	- todos os volumes do EBS oferecem suporte a criptografia;
- flexibilidade
	- os volumes do EBS oferecem suporte a alterações instantâneas. Você pode modificar o tipo de volume, o tamanho do volume  e a capacidade das IOPS sem interromper a instância;
- backups
	- o Amazon EBS oferece a capacidade de criar backups de qualquer volume do EBS;

##### Snapshots do Amazon EBS

- como seus volumes do EBS são compostos por dados da instância do Amazon EC2, você deve fazer backups desses volumes, chamados snapshots;
- snapshots do EBS são backups incrementais que salvam apenas os blocos no volume que forma alterados após o snapshot mais recente;
- quando você tira um snapshot de qualquer um dos volumes do EBS, os backups são armazenados de forma redundante em várias zonas de disponibilidade usando o Amazon S3 (Amazon Simple Storage Service);
- o aspecto do armazenamento do backup no Amazon S3 é tratado pela AWS **você não precisará interagir com o Amazon S3 para trabalhar com seus snapshots do EBS**;
- você gerencia os snapshots no console do Amazon EBS;
- podem ser usados para criar vários novos volumes, estejam eles na mesma AZ ou em uma diferente;
- ao criar um novo volume por meio de um snapshot, ele será uma cópia exata do volume original no momento em que o snapshot foi tirado;