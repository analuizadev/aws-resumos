
##### Sistema de nomes de domínio (DNS)

- o cliente digita o endereço o web no navegador e tem acesso ao site graças ao DNS;
- na resolução de DNS, o resolvedor DNS do cliente se comunica com um servidor DNS;
- a resolução DNS é o processo de *conversão* de um nome de domínio para um *endereço IP*;

![[Pasted image 20231226150657.png]]

##### Amazon Route 53

- é um serviço da web de DNS;
- uma maneira confiável de rotear os usuários finais para aplicativos da internet hospedados na AWS;
- conecta solicitações de usuários à infraestrutura em execução na AWS (instâncias EC2 e balanceadores de carga);
- pode direcionar os usuários para a infraestrutura fora da AWS;
- capacidade de gerenciar registro DNS para nomes de domínio;
	- pode registrar *novos nomes* de domínio diretamente no Route 53;
	- também pode *transferir* registros DNS para nomes de domínio existentes gerenciados por outras empresas de registro de domínio;
	- permitindo que você gerencie todos os seus nomes de domínio em um *único local*;

##### Amazon CloudFront e Amazon Route 53

![[Pasted image 20231226151341.png]]

1. um cliente solicita dados da aplicação acessando o site da AnyCompany;
2. o Amazon Route 53 usa a resolução de DNS para identificar o endereço IP correspondente da AnyCompany.com, 192.0.2.0; Essas informações são enviadas de volta para o cliente;
3. a solicitação do cliente é enviada para o local de borda mais próximo por intermédio do Amazon CloudFront;
4. o Amazon CloudFront se conecta ao Application Load Balancer, que enviar o pacote de entrada para uma instância do EC2;
