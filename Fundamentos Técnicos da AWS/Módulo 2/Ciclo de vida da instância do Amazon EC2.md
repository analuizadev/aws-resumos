- permite que interrompa e inicie as EC2 a vontade;
- paga apenas o que utilizar;
- as instâncias nascem a partir de uma AMI;
- termination protection, é uma proteção para caso termine uma instância acidentalmente;
##### Locais de instâncias do EC2:
- por padrão, as instâncias do EC2 são colocadas em na rede Amazon Virtual Private Cloud (Amazon VPC) padrão;
- qualquer recurso dentro da VPC padrão será ==público== e ==acessível== pela internet;

![[Pasted image 20231204211334.png]]

- instância fica dentro da VPC, conectada no HD virtual dentro de AZ;
- retângulo da AWS é o VPC;

##### Arquitetar para alta disponibilidade:
- duas instâncias são melhores que uma, e três são melhores que duas;
- a especificação do tamanho da instância oferece uma vantagem ao projetar sua arquitetura, pois você pode usar instâncias menores em vez de algumas maiores;
- se o front-end tiver apenas uma única instância e falhar, a aplicação será desativada;
- se ele tiver 10, e uma falhar, vai perder apenas 10% da sua frota e disponibilidade da aplicação dificilmente será afetada;
- ==ao arquitetar qualquer aplicação para alta disponibilidade, considere usar pelo menos duas instâncias do EC2 em duas zonas de disponibilidade separadas;==
![[Pasted image 20231204170056.png]]



##### Ciclo de vida da instância EC2
![[Pasted image 20231204170136.png]]

1.  ao executar uma instância ela entra no estado pendente;
	1. quando pendente, o faturamento não foi iniciado;
2. quando estiver em execução, ela estará pronta para uso e o faturamento começa;
	1. a partir da execução é possível realizar outras ações na instância, como reinicializar, encerrar, parar e hibernar;
3. reinicializar uma instância equivale a reinicialização de um sistema operacional;
	1. a instância permanece no mesmo computador host e mantém seu endereço de IP público e privado, além de quaisquer dados em seu armazenamento de instância;
4. quando uma instância é interrompida e iniciada, ela pode ser colocada em um novo servidor físico subjacente;
	1. perde todos os dados no armazenamento de instâncias que estavam no computador host anterior;
	2. quando interrompe uma instância, ela obtém um novo endereço de IP público, mas mantém o mesmo endereço IP privado;
5. encerrar uma instância, apaga os armazenamentos da instâncias e perde o endereço IP público e privado da máquina;
	1. o encerramento significa que não é mais possível acessar a máquina;

##### Parar X Hibernar:
- interrompe:
	- a instância entra no estado de parada até atingir o estado interrompido;
	- a AWS não cobra taxas de uso ou de transferência de dados para sua instância depois que a interrompe;
	- mas o armazenamento de qualquer volume do Amazon EBS é cobrado;
	- quando interrompida, é possível modificar alguns atributos, como o tipo de instância;
	- quando interrompida, os dados armazenados na memória (RAM) são perdidos;
<br />
- hibernar:
	- quando hiberna uma instância, a AWS sinaliza o sistema operacional para executar a hibernação (suspender para disco);
	- salva o conteúdo da memória da instância (RAM) no volume raiz do Amazon EBS;
	- equivale a fechar a tela do notebook e abrir novamente, com tudo que foi deixado aberto;
<br />
==exemplo==

Considere um cenário em que você constrói uma aplicação padrão de três camadas, no qual você tem servidores Web, servidores de aplicação e servidores de banco de dados. De repente, a aplicação que você construiu se torna extremamente popular. Para aliviar algum estresse no banco de dados que oferece suporte a sua aplicação, o ideal é implementar uma camada de back-end personalizada que armazena em cache as informações do banco de dados na ==memória (RAM)==. Você decide executar essa solução de cache de back-end personalizada no Amazon EC2.  
  
Nesse cenário, o recurso hibernar (stop-hibernate) seria fundamental para o armazenamento persistente. Isso impediria que você tenha que criar scripts manualmente para salvar os dados da RAM antes de desligar o servidor.

##### Preços

![[Pasted image 20231204213305.png]]

a AWS oferece três principais opções de compra para instâncias do EC2:
![[Pasted image 20231204172102.png]]

![[Pasted image 20231204211750.png]]

- instância sob demanda 
	- paga apenas pela capacidade computacional, sem compromissos de longo prazo;
	- o faturamento começa quando a instância está em execução e o faturamento é interrompido quando a instância está em um estado interrompido ou encerrado;
	- por hora se for windows e macOS, por segundo se for linux;
	![[Pasted image 20231204211854.png]]

- instância reservadas (RI):
	- ideal para servidores que não podem ser interrompidos, devem permanecer ligados 24/7;
	- oferece uma reserva por hora com desconto e uma reserva de capacidade opcional para instâncias do EC2;
	- necessário selecionar um período de 1 ou 3 anos para cada uma das seguintes opções
	- pode escolher entre três opções de pagamento:
		- **adiantamento integral :** oferece um desconto maior do que as instâncias de adiantamento parcial;
		- **instâncias de adiantamento parcial :** oferecem um desconto maior do que quando não há adiantamento;
		- **sem adiantamento :** oferece um desconto maior do que sob demanda;
	 ==sob demanda e sem adiantamento são semelhantes, porém mesmo interrompendo uma RI, você ainda paga por ela, porque se comprometeu com um período de um ou três anos;==
	 ![[Pasted image 20231204212109.png]]

- instâncias spot: 
	- permite aproveitar a capacidade não utilizada do EC2 na Nuvem AWS;
	- define um limite de quanto gostaria de pagar pela hora da instância;
	- se o valor pago for maior do que o preço spot atual e houver capacidade, você receberá uma instância;
	- a instância spot, pode ser interrompida;
		- se a AWS determinar que a capacidade não está mais disponível para uma determinada instância spot ou se o preço spot exceder quanto você está disposto a pagar, a AWS fornecerá um aviso de 2 minutos antes de interromper sua instância;
	- as workloads que são tolerantes a falhas de forma inerente, geralmente, são boas candidatas para usar com instâncias spot;
	- big data, worklodas em contêineres, integração contínua/entrega contínua (CI/CD), servidores Web, computação de alta performance (HPC), renderização de imagens e mídia, etc;
	- spot: usada para aumentar a capacidade computacional;
	- só é usada para picos de trabalho;
	![[Pasted image 20231204213059.png]]


- instância reservado **comprometimento de uso**; 
- saving plans **comprometimento de gasto por hora**;

![[Pasted image 20231204212351.png]]

- host dedicado: EC2 exclusivo pra você, um quarto só pra você;
- instância dedicada: hardware dedicado, andar inteiro pra você, podendo ter várias;

![[Pasted image 20231204212552.png]]
![[Pasted image 20231204212758.png]]
![[Pasted image 20231204212940.png]]