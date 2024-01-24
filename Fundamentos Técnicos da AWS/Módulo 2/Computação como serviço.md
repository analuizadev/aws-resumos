
##### Servidores
- primeiro componente básico, necessário para hospedar uma aplicação;
- podem lidar com solicitações HTTP e enviar respostas aos clientes seguindo o modelo cliente-servidor;
- alimentam a aplicação fornecendo capacidade de CPU, memória e rede para processar as solicitações dos usuários e transformá-las em respostas;
- servidores HTTP comuns incluem:
	- opções do windows, IIS (internet information services);
	- opções do linux, Apache HTTP Web Server, Nginx e Apache Tomcat;

##### Escolha a opção de computação certa
- é necessário saber qual serviço de computação usar para qual caso de uso;
- três tipos de opções de computação estão disponíveis: máquinas virtuais, serviços de contêiner e sem servidor;
- VM geralmente é a opção mais fácil de entender, ela emula um servidor físico e permite que você instale um servidor HTTP para executar as aplicações;
- na AWS as VM são chamadas de Amazon Elastic Compute Cloud ou Amazon EC2;
- a AWS opera e gerencia as máquinas host e a camada do hipervisor;
- a AWS instala o Sistema Operacional da máquina virtual, chamado SO convidado;
- Alguns AWS Compute Services usam o Amazon EC2 ou conceitos de virtualização internos;

==para executar VMs, você instala um hipervisor em uma máquina host. O hipervisor provisiona os recursos para criar e executar suas VMs;==