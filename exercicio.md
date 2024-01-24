1. Em qual categoria de serviço o IAM está?
	R: security;
2. Em qual categoria de serviço o Amazon VPC está?
	R: networking;
3. a sub-rede que você selecionou existe no nível da Região ou no nível da zona de disponibilidade?
	R: zona de disponibilidade, pq seu nome indica a região us-west e sua AZ 2c;
	![[Pasted image 20231209182925.png]]
4. a VPC selecionada existe no nível da Região ou no nível da Zona de disponibilidade?
	R: no nível da região;
	![[Pasted image 20231209184530.png]]
5. quais serviços são globais em vez de regionais?
	R: IAM e o Router 53 são globais; Amazon EC2 e o Lambda são regionais;