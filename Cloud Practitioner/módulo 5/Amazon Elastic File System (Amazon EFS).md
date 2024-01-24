
##### Armazenamento de arquivos

- vários clientes podem acessar os dados armazenados em *pastas de arquivos compartilhadas*;
- nessa abordagem, um servidor de armazenamento usa armazenamento em bloco com um sistema de arquivos local para organizar os arquivos;
- os clientes acessam dados por meio de *caminhos de arquivo*;
- ideal para casos de uso em que um *grande número* de serviços e recursos precisam acessar *os mesmos dados ao mesmo tempo*;

##### Amazon EFS

- é um sistema de arquivos dimensionável usado com os AWS Cloud Services e recursos on-premises;
- à medida que você adiciona e remove arquivos, o EFS expande e retrai automaticamente;
- pode dimensionar sob demanda para petabytes sem interromper os aplicativos;

![[Pasted image 20231226162556.png]]

##### Amazon EBS X Amazon EFS

- *EBS :*
	- um volume do Amazon EBS armazena dados em *uma única* zona de disponibilidade;
	- para anexar uma instância do Amazon EC2 a um volume do EBS, tanto a instância quanto o volume *precisam residir na mesma Zona de Disponibilidade*;
- *EFS :*
	- o Amazon EFS é um *serviço regional*;
	- armazena dados em *várias* zonas de disponibilidade e entre elas;
	- o armazenamento duplicado permite que você *acesse dados simultaneamente* de todas as AZs na Região em que um sistema de arquivos está localizado;
	- os servidores on-premises podem acessar o Amazon EFS usando o AWS Direct Connect;
