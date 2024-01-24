##### Redes definidas

- a rede é como você conecta computadores me todo o mundo e permite que eles se comuniquem uns com os outros;
- exemplo de rede: infraestrutura global da AWS;

##### Noções básicas de redes

- pensar em redes é pensar em enviar uma carta, precisa de um destinatária e um remetente, além das informações de endereço;
- em redes esse processo de envio e recebimento de cartas é chamado de **roteamento**;

##### Endereços IP

- para rotear corretamente suas mensagens para um local, você precisa de um endereço;
- cada computador tem um endereço IP;
- endereço IP de 32 bits:
	- 11000000 10101000 00000001 00011110

##### Notação IPV4

- normalmente, um endereço IP é convertido em formato decimal e anotado como um endereço IPV4/IPV6;
- IPV4 endereço IP de 32bit e IPV6 endereço IP de 128 bit;
- os 32 bits são agrupados em grupos de 8 bits, também chamados de **octetos**;
![[Pasted image 20231206173520.png]]

##### Notação CIDR

- notação CIDR: roteamento entre domínios sem classe;
- é uma maneira compactada de especificar um intervalo de endereços IP;
- a especificação de um intervalo determina quantos endereços IP estão disponíveis para você;

![[Pasted image 20231206174145.png]]

- começa com um endereço IP inicial e é separado por uma barra seguido por um número;
- o número do final específica quantos bits do endereço IP são fixos;
- no exemplo, os primeiros 24 bits do endereço IP são corrigidos, o resto é flexível;
- o total de 32 bits subtraídos por 24 bits fixos deixa 8 bits flexíveis;
- cada um dos bits flexíveis pode ser 0 ou 1, porque eles são binários;
- significa que tem duas opções para cada um dos 8 bits, fornecendo 256 endereços IP nesse intervalo de IP;
- ==quanto maior o número após a barra, menos o número de endereços IP em sua rede, um intervalo de 192.168.1.0/24 é menor que 192.168.1.0/16==;
- ao trabalhar com redes na Nuvem AWS, você escolhe o tamanho da rede usando a notação CIDR;
- na AWS **o menor intervalo de IP que você pode ter é /28**, que fornece 16 endereços IP;
- **o maior que você pode ter é 16**, que fornece 65.536 endereços IP;