
- é uma tentativa deliberada de tornar um site ou aplicação indisponível para os usuários;
 
 ![[Pasted image 20231227190218.png]]

##### Ataques distribuídos de negação de serviço (DDoS)

- *várias origens* são usadas para iniciar um ataque que visa tornar um site ou aplicação indisponível;
- pode ser feito por um grupo de invasores ou ate mesmo um único invasor;

![[Pasted image 20231227191405.png]]

##### AWS Shield

- protege aplicações contra ataques DDoS e DoS;
- oferece dois níveis de proteção:
	- Standard;
		- protege automaticamente todos os clientes AWS, *sem nenhum custo*;
		- protege seus recursos AWS contra os tipos de ataques DDoS *mais comuns e frequentes*;
		- usa diversas técnicas de análise para detectar tráfego mal-intencionado em tempo real e mitigá-lo automaticamente;
	- Advanced;
		- serviço *pago* que fornece diagnósticos detalhados de ataques e a capacidade de detectar e mitigar ataques *elaborados* de DDoS;
		- se integra a outros serviços, como CloudFront, Amazon Route 53 e o Elastic Load Balancing;
		- pode integrar o AWS Shield ao AWS WAF (Web Application Firewall) escrevendo regras personalizadas para mitigar ataques complexos de DDoS;