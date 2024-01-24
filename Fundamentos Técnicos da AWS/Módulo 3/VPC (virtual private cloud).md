
- uma rede isolada que você cria na Nuvem AWS, semelhante a uma rede tradicional em um datacenter;
- ao criar uma VPC, deve escolher três fatores principais:
	- nome da VPC;
	- região em que a VPC ficará ativa; (cada VPC abrange várias zonas de disponibilidade dentro da região selecionada);
	- intervalo de IP para a VPC na notação CIDR (determina o tamanho da rede, cada VPC pode ter até **quatro intervalos de IP** /16);

![[Pasted image 20231206181957.png]]

##### Criar uma sub-rede

- após a criação da VPC, deve criar sub-redes dentro da rede;
- sub-redes são como redes menores dentro da sua rede base;
- na AWS as sub-redes são usadas para fornecer opções de alta disponibilidade e conectividade para seus recursos;
- ao criar uma sub-rede é necessário especificar o seguinte:
	- a VPC na qual deseja que sua sub-rede fique ativa; (nesse caso VPC: 10.0..0.0/16);
	- zona de disponibilidade na qual você deseja que sua sub-rede fique ativa; (nesse caso AZ1)
	- bloco CIDR para sua sub-rede, que deve ser um subconjunto do bloco CIDR da VPC; (nesse caso 10.0.0.0/24)
- ==quando você executa uma instância EC2, você a executa dentro de uma sub-rede, que estará localizada dentro da zona de disponibilidade escolhida;==

![[Pasted image 20231206182544.png]]

##### Alta disponibilidade com uma VPC

- ao criar sub-redes considere a alta disponibilidade;
- para manter redundância e tolerância a falhas, crie pelo menos duas sub-redes configuradas em duas zonas de disponibilidade;
- se uma das AZs falhar, você ainda terá seus recursos disponíveis em outra AZ como backup;

![[Pasted image 20231206183457.png]]

##### IPs reservados

- para a AWS fazer a configuração da sua VPC de forma adequada, ela reserva **cinco endereços IP** em cada sub-rede;
- eles são usados para roteamento, Domain Name System (DNS) e gerenciamento de rede;
- exemplo:
	- considere uma VPC com o intervalo de IP 10.0.0.0/22; a VPC inclui 1.024 endereços IP totais; isso é dividido em quatro sub-redes de tamanho igual, cada uma com um intervalo de IP /24 com 256 endereços IP; de cada um desses intervalos de IP, existem apenas *251* endereços IP que podem ser usados, porque a AWS *reserva cinco*;
	- os cincos endereços IP reservados podem afetar a forma como você projeta sua rede;
	![[Pasted image 20231206224407.png]]

##### Gateways

###### Gateway da internet

- deve criar um gateway da internet para habilitar a conectividade com a internet para sua VPC;
- semelhante ao modem, o gateway conecta sua VPC à internet;
- um gateway é altamente disponível e escalável;
- depois de criar, você o anexa à sua VPC;

###### Gateway privado virtual

- gateway privado virtual conecta sua AWS VPC a outra rede privada;
- depois de criar e anexar um gateway privado a uma VPC, o gateway atua com âncora no lado da AWS da conexão;
- do outro lado da conexão, você precisará conectar um gateway do cliente à outra rede privada;
- um dispositivo de gateway do cliente é um dispositivo físico ou aplicação de software no seu lado da conexão;
- ==depois de ter dois gateways, você pode estabelecer uma conexão **VPN** criptografada entre os dois lados;==
