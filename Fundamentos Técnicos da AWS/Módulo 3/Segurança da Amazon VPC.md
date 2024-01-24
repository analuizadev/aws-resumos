
- no nível básico qualquer nova VPC está isolada do tráfego de internet para evitar riscos;
- Network ACL: *tudo é permitido*, posso usar as regras de permissão e negação;
- Security Group: 
	- *bloqueia todo tráfego de entrada, permite todo o tráfego de saída*, posso criar regras para permissão;
	- protege o servidor virtual;
	- partes básicas de uma regra de security group: **endereço IP** e **número de porta**;

##### Sub-redes seguras com lista de controle de acesso à rede (network ACL)

- Network ACL: como um firewall no nível da sub-rede;
- permite qual tipo de tráfego tem permissão para entrar ou sair da sub-rede;
- você pode configurar isso configurando regras que definem o que você deseja filtrar;
- no exemplo, a Network ACL permite que os dados fluam livremente para a sub-rede;
- as Networks ACLs *são consideradas stateless*, você precisa *incluir as portas de entrada e saída* usadas para o protocolo;
- se não incluir o intervalo de saída, o servidor responderia, mas o tráfego nunca sairia da sub-rede;

![[Pasted image 20231207164304.png]]

- no exemplo, você permite 443 de entrada e intervalo de saída 1025-65535, o HTTP usa a porta 443 para iniciar uma conexão e responderá a uma porta efêmera;

![[Pasted image 20231207164459.png]]

##### Instâncias do EC2 seguras com grupos de segurança

- pode criar um firewall chamado de grupo de segurança;
- a configuração padrão de um grupo de segurança, bloqueia todo o tráfego de entrada e permite todo o tráfego de saída;
- Security Group são com estado, eles se lembrarão se uma conexão foi originalmente iniciada pela instância do EC2 ou de fora e permitirá temporariamente que o tráfego responda sem modificar as regras de entrada;
- se quiser que sua instância do EC2 aceite o tráfego da internet, deve abrir portas de entrada;

![[Pasted image 20231207170016.png]]

- da mesma forma que as sub-redes podem ser usada para segregar (isolar) o tráfego entre computadores em sua rede; o security group também pode ser usado da mesma maneira;
- um padrão de design comum, é organizar recursos em diferente grupos e criar grupos de segurança para cada um controlar a comunicação de rede entre eles;

![[Pasted image 20231207170758.png]]

- este exemplo define três camadas e isola cada camada com regras de grupo de segurança definidas;
-  o tráfego da internet para a camada Web é permitido por HTTPS;
- o tráfego da camada da Web para camada de aplicação é permitido por HTTP;
- o tráfego da camada de aplicação para o banco de dados é permitido por MySQL;
- em ambientes on-premises tradicionais, você isola grupos de recursos por meio de uma configuração VLAN;
- na AWS, os grupos de segurança permitem que você obtenha o mesmo isolamento sem vinculá-lo à sua rede;