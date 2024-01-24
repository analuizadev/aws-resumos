
##### Disponibilidade

- é expressa como uma porcentagem do tempo de atividade em um determinado ano ou como um número de noves;
- para aumentar a disponibilidade, precisa de redundância;
	- mais infraestrutura, mais datacenters, mais servidores, mais bancos de dados e mais replicação de dados;

 ![[Pasted image 20231220222549.png]]
##### Melhorar a disponibilidade das aplicações

- adicionar mais servidor, para caso a única instância disponível fique inativa, os clientes terão acesso a outra;

##### Segunda zona de disponibilidade

- para corrigir problema de **localização física**, implante uma segunda instância em uma AZ diferente;

##### Replicação, redirecionamento e alta disponibilidade

###### Processo de replicação

- necessário criar um processo de replicação de arquivos de configuração, patches de software e aplicações entre instâncias;
- o melhor método é **automatizar o máximo possível**;

###### Redirecionamento do cliente

- para os clientes saberem sobre diferentes servidores disponíveis há dois métodos:
	- usar o *DNS* em que o cliente usa um registro que aponta para o endereço IP de todos os servidores disponíveis;
		- leva um tempo para atualizar a lista, razão por ele não ser muito utilizado;
	- usar um *balanceador de carga*, que cuida das verificações de integridade e distribui a carga em cada servidor;
		- evita problemas de tempo de propagação;

##### Tipos de alta disponibilidade

- ao ter mais de um servidor, qual o tipo de disponibilidade que precisará:
	- *ativo-passivo :*
		- apenas uma das duas instância está disponível por vez;
		- vantagem, para aplicações com estado em que os dados sobre a sessão do cliente são armazenados no servidor, não haverá problemas, porque os clientes sempre são enviados para o servidor em que a sessão é armazenada;
		- desvantagem, escalabilidade;
	- *ativo-ativo :*
		- vantagem, escalabilidade;
		- tem ambos os servidores disponíveis;
		- o segundo servidor pode carregar alguma carga para a aplicação, o que permite que todo o sistema aceite mais carga;
		- se a aplicação fosse com estado, haveria um problema se a sessão do cliente não estivesse disponível em ambos os servidores;
		- aplicações stateless funcionam melhor para sistemas ativo-ativos;