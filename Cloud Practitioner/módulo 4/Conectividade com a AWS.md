
- a VPC tem dois tipos de sub-redes: pública e privada;
- para conectar a *sub-rede pública* a internet, e as pessoas acessarem os conteúdos dela, conectamos o gateway de internet a sub-rede pública;
	- ![[Pasted image 20231226120449.png]]
- para manter a *sub-rede privada* com acesso privado, conectamos o gateway privado virtual, que cria uma conexão de VPN entre a VPC e uma rede privada;
	- ![[Pasted image 20231226120436.png]]

##### AWS Direct Connect

- um serviço que permite estabelecer **uma conexão privada dedicada** entre seu data center e uma VPC;
- ajuda a reduzir os custos de rede e aumentar a quantidade de largura de banda que pode trafegar pela rede;
- exemplo: cria uma rota privada para que seu conteúdo não tenha que passar pela rota pública, evitando lentidão e tendo mais segurança;

![[Pasted image 20231226120416.png]]