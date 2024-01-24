
##### Armazenamento de objetos

- cada objeto consiste em *dados, metadados e uma chave*;
- os dados podem ser:
	- imagem;
	- vídeo;
	- documento de texto;
	- qualquer tipo de arquivo;
- os metadados :
	- contem informações sobre *o que são os dados*;
	- como eles *são usados*;
	- o tamanho do objeto;
- a chave:
	- é o identificador exclusivo de um objeto;
- quando um arquivo no armazenamento de objetos é modificado, *todo o objeto é atualizado*;

![[Pasted image 20231226154720.png]]

##### Amazon Simples Storage Service

- fornece armazenamento em nível de objeto;
- armazena dados como objetos e buckets;
- possível fazer upload de qualquer tipo de arquivo;
- oferece espaço de armazenamento ilimitado;
- o tamanho *máximo* de arquivo para um objeto no Amazon S3 é de *5TB*;
- é possível definir permissões para controlar a visibilidade e o acesso a um arquivo;
- pode usar o recurso de versionamento do Amazon S3 para rastrear alterações em seus objetos ao longo do tempo;

##### Storage classes do Amazon S3

- paga somente pelo o que usar;
- pode escolher dentre diversas storage classes;
	- *S3 Standard*: mais caro, dados com frequência, mais rápido;
	- *S3 Standard Infrequent Access (IA)*: mais barato, pouco acesso, mais rápido;
	- *S3 One Zone-IA*: mais barato, uma zona de disponibilidade;
	- *S3 Intelligent-Tiering*: monitora quais serviços usados, mais usados em cima, menos usado embaixo;
	- *S3 Glacier Instant Retrieval*: mais barato, objetos recuperados em milissegundos, dados arquivos que requerem acesso imediato;
	- *S3 Glacier Flexible Retrieval*: mais barato, recuperação de objetos em poucos minutos;
	- *S3 Glacier Deep Archive*: mais barato, dados acessados uma ou duas vezes por ano, recupera objetos em 12 horas;
	- *S3 Outposts*: cria buckets do S3 no Amazon S3 Outposts, torna mais fácil recuperar, armazenar e acessar dados no AWS Outposts (on-premises);

