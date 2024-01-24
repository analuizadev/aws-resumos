
- um serviço totalmente gerenciado que permite *avaliar, analisar e fazer auditoria da configuração dos seus recursos da AWS*;
- *rastrear alterações de configuração de recursos* e responder perguntas sobre elas, *demonstrar conformidade* e *detectar e solucionar problemas de vulnerabilidade de segurança*; 
- ele fornece:
	- monitoramento quase contínuo;
	- avaliação quase contínua;
	- gerenciamento de alterações;
	- solução de problemas operacionais;
- fornece o inventário de recursos da AWS, o histórico de configurações e notificações de alteração de configuração para proporcionar *segurança e governança;
- fornece detalhes sobre as alterações de configuração;
- combina-se com o *CloudTrail*;
- com o AWS Config, *você pode*:
	- descobrir os recursos existentes da AWS;
	- exportar um inventário completo de seus recursos da AWS com todos os detalhes de configuração;
	- determinar como um recursos foi configurado em qualquer momento;
- esses recursos permitem *auditoria de conformidade*, *análise de segurança*, *rastreamento de alterações de recursos* e *solução de problemas*; 
	- de valor específico são:
		- **detecção :** 
			- crie controles de detecção e identifique e analise anomalias;
		- **conformidade :** 
			- crie regras que avaliam a conformidade de recursos e auxiliem no alinhamento com as certificações SOC (conformidade com a segurança); 
			- revise as alterações nas configurações e nas relações entre os recursos da AWS;
		- **controle de acesso :**
			- crie funções do IAM que concedam permissões do AWS Config para acessar recursos como buckets do S3;
			- crie funções vinculadas ao serviço ligadas ao AWS Config que incluam todas as permissões que o Config exige para chamar outros serviços em nome do usuário;
		- **criptografia/dados em repouso :**
			- o AWS Config cria um item de configuração sempre que detecta uma alteração em um tipo de recurso que está registrando;
				- os componentes de um item de configuração incluem *metadados*, *atributos*, *relações*, *configuração atual* e *eventos relacionados*;

![[Pasted image 20231231114720.png]]
##### Gerenciamento de configuração usando o AWS Config

- monitora e registra de forma quase contínua suas configurações de recursos da AWS;
- é possível automatizar a avaliação das configurações registradas em relação às configurações desejadas;
- todos os recursos permitem :
	- simplificar a auditoria de conformidade;
	- a análise de segurança;
	- o gerenciamento de mudanças;
	- a solução de problemas operacionais;

![[Pasted image 20231231115301.png]]

##### Regras do AWS Config

- pode usar as regras existentes da AWS e de parceiros da AWS;
- pode definir suas próprias regras personalizadas usando o AWS Lambda;
- é possível direcionar regras a recursos *específicos*, *tipos específicos* de recursos ou a recursos *marcados* de uma forma particular;
	- as regras são executadas quando esses recursos *são criados* ou *alterados* e também podem ser avaliadas periodicamente (*por hora, diariamente e assim por diante*);
- pode configurar regras para verificar se as alterações de configuração são gravadas;
	- depois de configurar o AWS Config, ele fornece um painel para visualizar a conformidade;
	- você também pode usar o painel para *identificar alterações* nos recursos que possam ser *preocupantes*;
- o AWS Config é invocado *automaticamente* para que as configurações sejam avaliadas de forma quase contínua;

![[Pasted image 20231231120034.png]]

---
**exemplo : regras do AWS Config**

as regras podem procurar qualquer condição *desejável* ou *indesejável*;

por exemplo, você pode definir regras que garantem que:

	- os volumes do Amazon Elastic Block Store (Amazon EBS) sejam criptografados;
	- as instâncias estejam sendo criadas apenas de imagens de máquina da Amazon (AMIs) aprovadas;
	- os endereços IP elásticos estão anexados a instâncias;
	- as instâncias do Amazon EC2 estejam sendo marcadas corretamente;
