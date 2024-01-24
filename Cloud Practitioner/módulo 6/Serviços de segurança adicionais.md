
##### AWS Key Management Service (AWS KMS)

- permite que você execute operações de criptografia usando *chaves de criptografia*;
- pode usar para criar, gerenciar e usar chaves de criptografia;
- também pode controlar o uso de chaves em uma ampla gama de serviços e em suas aplicações;
- pode escolher os níveis específicos de controle de acesso necessários para suas chaves;
	- exemplo, pode especificar quais usuários e funções do IAM podem gerenciar chaves;
- pode desativar as chaves temporariamente, para que não sejam mais usadas;
- *suas chaves nunca saem do KMS e você está sempre no controle delas*;

##### AWS WAF

- firewall de aplicação web que permite monitorar solicitações de rede que entram em aplicações web;
- trabalha em conjunto com o CloudFront e um Application Load Balancer;
- funciona de forma semelhante as listas de controle de acesso de rede, bloqueando ou permitindo tráfego;
	- no entanto, ele faz isso usando uma lista de controle de acesso (ACL) da web para proteger seus recursos da AWS;
- quando uma solicitação entra no AWS WAF, ele confere a lista de regras configurada na ACL da web;
	- se especificar o bloqueio de um IP na ACL, ele não permite o acesso a aplicação;

![[Pasted image 20231227193019.png]]

![[Pasted image 20231227193032.png]]

##### Amazon Inspector

- ajuda a melhorar a segurança e a conformidade das aplicações executando avaliações de segurança automatizadas;
- verifica os aplicativos quanto a vulnerabilidades de segurança e desvios das práticas recomendadas de segurança;
	- como acesso aberto a instâncias do Amazon EC2;
	- instalações de versões de software vulneráveis;
- depois da avaliação, ele apresenta uma lista de descobertas de segurança;
- a lista prioriza por *nível de gravidade*, com uma descrição detalhada de cada problema de segurança e uma recomendação sobre como corrigi-lo;
	- a AWS não garante que seguir as recomendações feitas resolverá todos os possíveis problemas de segurança;

##### Amazon GuardDuty

- serviço que realiza detecção inteligente de ameaças para sua infraestrutura e seus recursos AWS;
- identifica ameaças monitorando continuamente a atividade da rede e o comportamento da conta no seu ambiente AWS;
- após habilitado o GuardDuty começa a monitorar sua atividade de rede e conta;
- não precisa implantar ou gerenciar nenhum outro software de segurança;
- analisa continuamente dados de várias fontes da AWS, incluindo logs de fluxo de VPC e logs de DNS;
- se detectar ameaças, você poderá analisar as descobertas detalhadas no console de gerenciamento da AWS;
- as descobertas incluem etapas recomendadas para a correção;
- também pode configurar as funções do AWS Lambda para executar as etapas de correção automaticamente em resposta às descobertas de segurança do GuardDuty;

![[Pasted image 20231227194139.png]]

##### Amazon Detective

- serviço de segurança da AWS que permite *avaliar, investigar e identificar a origem de suspeitas de vulnerabilidades de segurança ou atividades suspeitas* em seu ambiente AWS;
- cria visualizações e modelos interativos do ambiente AWS usando aprendizado de máquina, análise estática e teoria de grafos;
- ao coletar e analisar dados de log de vários serviços da AWS como VPC Flow Logs, AWS CloudTrail e Amazon GuardDuty, ele permite que você tenha uma visão abrangente e centralizada da postura de segurança do seu ambiente AWS;

![[Pasted image 20240124151400.png]]