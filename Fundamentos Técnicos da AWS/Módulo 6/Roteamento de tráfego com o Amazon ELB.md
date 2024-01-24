
- Amazon ELB = Amazon Elastic Load Balancing

##### Balanceadores de carga

- se refere ao processo de distribuição de tarefas em um conjunto de recursos;
- *exemplo*, diretório de funcionários:
	- os recursos são instâncias do EC2 que hospedam a aplicação;
	- as tarefas são as solicitações que estão sendo enviadas;
	- pode usar o balanceador para distribuir as solicitações em todos os servidores que hospedam a aplicação;
- é possível instalar sua própria solução de balanceamento de carga de software em instâncias EC2;
- a AWS fornece o serviço Elastic Load Balancing;

##### Recursos do ELB

- não precisa gerenciá-lo ou operá-lo;
- ele pode distribuir o tráfego da aplicação de entrada entre:
	- instâncias do EC2;
	- contêineres;
	- endereços IP; 
	- funções do AWS Lambda;
- outros recursos principais:
	- como ele pode balancear a carga para endereços IP, ele pode funcionar me um *modo híbrido*, fazendo balanceamento de carga para servidores on-premises também;
	- é *altamente disponível*, deve-se garantir apenas que o balanceador de carga seja implantado em várias AZs;
	- escalabilidade, é *dimensionado automaticamente* para atender à demanda do tráfego de entrada, lida com o tráfego de entrada e o envia para a aplicação de back-end;

##### Verificações de integridade

- deve validar todos os elementos;
- *exemplo :*
	- a aplicação do diretório de funcionários depende um banco de dados e do Amazon S3;
	- para a verificação de integridade validar todos os elementos, podemos criar uma página da web de monitoramento, como /monitor, que fará uma chamada para o banco de dados para garantir que ele possa conectar e obter dados e fazer uma chamada para o Amazon S3;
	- depois, você aponta a verificação de integridade no balanceador de carga para a página /monitor;
	- depois de determinar a disponibilidade de uma nova instância do EC2, o balanceador de carga começa a enviar o tráfego para ela;
	- se o ELB determinar que uma instância do EC2 não está mais funcionando, ele interrompe o envio de tráfego para ela e permite que o EC2 Auto Scaling saiba disso;
	- o tráfego somente é enviado para a nova instância se ela passar na **verificação de integridade**;

![[Pasted image 20231221151617.png]]

- **diminuição de conexão :**
	- o ELB impede que o EC2 Auto Scaling encerre uma instância do EC2 (redução de escala) até que todas as conexões à instância terminem, ao mesmo tempo que evita novas conexões;

##### Componentes ELB

- é composto por **três componentes** principais:
	- *regras :*
		- deve ser usada uma regra para associar um grupo de destino a um listener;
		- são compostas por uma condição que pode ser o **endereço IP de origem do cliente** e uma condição para decidir **qual grupo de destino enviar o tráfego**;
	- *listeners :*
		- o cliente se conecta ao listener;
		- para definir um listener **uma porta deve ser fornecida** além do **protocolo**, dependendo do tipo de balanceador de carga;
		- pode haver **muitos listeners** para **um** balanceador de carga;
	- *grupos de destino :*
		- os servidores de back-end são definidos em **um ou mais grupos de destino**;
		- define o **tipo** de back-end para o qual deseja direcionar o tráfego, como: 
			- instâncias do EC2, funções do AWS Lambda ou endereços IP;
		- uma *verificação de integridade* deve ser definida para **cada** grupo de destino;

![[Pasted image 20231221152645.png]]

##### Application Load Balancer (ALP)

- *roteia o tráfego com base nos dados da solicitação*;
	- toma decisões de roteamento com base no protocolo HTTP, como o caminho do URL (/upload) e host, cabeçalhos e método HTTP, além do endereço IP de origem do cliente;
	- isso permite o roteamento granular para grupos de destino;
- *envia respostas diretamente ao cliente*;
	- tem capacidade de responder diretamente ao cliente com uma resposta fixa, como um página HTML personalizada;
	- pode enviar um redirecionamento para o cliente, o que é útil quando você redirecionar para um site específico ou redirecionar uma solicitação de HTTP para HTTPS, removendo esse trabalho de seus servidores back-end;
- *usa o descarregamento TLS*;
	- para passar o tráfego HTTPS por meio do ALB, um certificado SSL é fornecido pela importação de um certificado por meio de serviços do IAM ou AWS Certificate Manager (ACM) ou pela criação de um de forma gratuita usando o ACM;
	- isso garante que o tráfego entre o cliente e o ALB seja criptografado;
- *autentica usuários*;
	- pode autenticar usuários antes que eles possam passar pelo balanceador de carga;
	- usa o protocolo OpenID Connect e se integra a outros produtos da AWS para oferecer suporte a protocolos, como SAML, LDAP, Microsoft Active Directory, etc;
- *protege o tráfego*;
	- para evitar que o tráfego atinja o balanceador de carga, configura um grupo de segurança para especificar os intervalos de endereços IP suportados;
- *usa o algoritmo de roteamento de solicitações menos pendente*;
	- solicitação pendente é quando uma solicitação é enviada para o servidor de back-end e ainda não recebeu uma resposta;
	- é o algoritmo de roteamento certo para usar se os destinos variarem nos recursos de processamento;
	- solicitações para o back-end que variam em complexidade, em que uma pode precisar de muito mais tempo de CPU do que a outra, é mais apropriado usar o algoritmo de solicitação menos pendente, pois garantia um uso igual entre os destinos que também tenham solicitações mais pendentes;
- *usa sticky sessions*;
	- se as solicitações precisarem ser enviadas para o mesmo servidor de back-end, porque a aplicação é com estado, use o recurso de sticky session;
	- usa um cookie HTTP para se lembrar, entre conexões, para qual servidor enviar o tráfego;
- **especificamente para tráfego HTTP e HTTPS**;

##### Network Load Balancer

- *oferece suporte a protocolos TCP, UDP e TLS*;
	- NLB opera na camada de conexão, **não entende** o que é uma solicitação HTTP e HTTPS;
- *usa um algoritmo de roteamento hash de fluxo*;
	- o algoritmo é baseado em:
		- protocolo;
		- endereço IP de origem e porta de origem;
		- endereço IP de destino e porta de destino;
		- número de sequência TCP;
	- se todos os parâmetros são os mesmo, os pacotes são enviados para o mesmo destino;
	- se for diferente, a solicitação poderá ser enviada para um destino diferente;
- *tem sticky sessions*;
	- diferente do ALB;
	- essas sessões são baseadas no endereço IP de origem do cliente, em vez de cookie;
- *oferece suporte ao descarregamento TLS*;
	- entende o protocolo TLS;
	- pode descarregar o TLS dos servidores de back-end, semelhante ao ALB;
- *lida com milhões de solicitações por segundo*;
	- pode lidar instantaneamente com milhões de solicitações por segundo;
	- o ALB precisaria de escalamento;
- *oferece suporte a endereços IP estáticos e elásticos*;
	- em solicitações que o cliente de aplicação precisa enviar solicitações diretamente para o endereço IP do balanceador de carga em vez de usar o DNS, o NLB é o tipo certo de balanceador de carga a ser usado;
- *preserva o endereço IP de origem*;
	- preserva o endereço IP de origem do cliente ao enviar o tráfego para o back-end;
	- no ALB o endereço IP de origem das solicitações, será visto como o IP do balanceador de carga;
	- no NLB é mantido o endereço IP real do cliente, que é exigido pela aplicação de back-end em alguns casos;

##### Selecione entre tipos de ELB

![[Pasted image 20231221160617.png]]