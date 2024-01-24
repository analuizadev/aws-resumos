
##### Como funciona

- monitora o estado e a utilização da maioria dos recursos que você pode gerenciar na AWS; 
- serviço gerenciado que pode ser usado para monitoramento, sem gerenciar a infraestrutura subjacente;
- monitoramento básico:
	- sete métrica pré-selecionadas em uma frequência de 5 minutos;
	- nível gratuito;
	- três métricas de verificação de status em um frequência de 1 minuto;
	- visibilidade sem custo extra;
	- adequado para muitas aplicações;
- monitoramento detalhado:
	- todas as métricas que estão disponíveis para o monitoramento básico em uma frequência de 1 minuto;
	- custo adicional;
	- fornecem agregação de dados pelo Amazon EC2, ID da AMI (amazon machine image) e tipo de instância;
- o agente do CloudWatch coleta métrica no **nível do sistema**
	- instâncias do EC2;
	- servidores locais;
- retém métrica por **15 meses** de forma **gratuita**;
- as métricas são compatíveis com as seguintes três programações de retenção:
	- pontos de dados de **1 minuto** estão disponíveis por **15 dias**;
	- pontos de **5 minutos** ficam disponíveis por **63 dias**;
	- pontos de dados de **1 hora** ficam disponíveis por **455 dias**;

![[Pasted image 20231220201611.png]]

##### Métricas do CloudWatch

- cada métrica tem um carimbo de data/hora;
- são organizadas em contêineres chamados **namespaces**;
- métricas em namespaces **diferentes** são **isoladas** umas das outras;
- os produtos da AWS que enviam dados para o CloudWatch anexam dimensões a cada métrica;
- **não é possível excluir métricas**, elas expirarão automaticamente depois de 15 meses de inatividade;
- uma dimensão é um **par de nome/valor**;
	- faz parte da identidade de uma métrica;
	- usa para filtrar os resultados retornados pelo CloudWatch;
	- exemplo, pode obter estatísticas para uma instância do EC2 ao especificar a dimensão InstanceId quando você pesquisa;
- *métricas padrão* :
	- agrupadas por *nome de serviço*;
	- exibi graficamente para que as métricas selecionadas possam ser comparadas;
	- só aparece se você tiver *usado o serviço no últimos 15 meses*;
	- é acessível programaticamente por meio da AWS Command Line Interface ou da Interface de Programação de Aplicativo (API);
	- alarme;
	- evento com base no tempo;
- *métricas personalizadas* :
	- agrupadas por **namespaces definidos pelo usuário**;
	- publique no CloudWatch usando a AWS CLI, uma API ou um agente do CloudWatch;
	- evento com base em eventos;
	- regra;

![[Pasted image 20231220221017.png]]

![[Pasted image 20231220221209.png]]

##### Métricas personalizadas

- permite que você publique suas próprias métricas no CloudWatch;
- visibilidade mais granular, usa métricas personalizadas de alta resolução;
	- permitem coletar métrica personalizadas até uma resolução de 1 segundo;
- pode começar a usar métricas personalizadas enviando programaticamente a métrica para o CloudWatch usando a API PutMetricData;
- exemplos de métricas personalizadas:
	- tempo de carregamento de página da web;
	- solicitações de taxa de erro;
	- número de processos ou threads em sua instância;
	- quantidade de trabalho realizado pela sua aplicação;

##### Painéis do CloudWatch

- pode visualizar e revisar os dados usando o console do CloudWatch com painéis;
- são páginas iniciais personalizáveis que você usa para **visualização** de dados de uma ou mais métricas por meio do uso de widgets, como um gráfico ou texto;
- pode criar muitos painéis personalizados;
- pode extrair dados de diferentes regiões em um único painel para criar uma visão global de sua arquitetura;
- pode escolher se os widgets de métrica exibirão dados em tempo real;
- dados em tempo real são dados publicados no **último minuto** que não forma totalmente agregados;
- **não é obrigado** a usar o CloudWatch exclusivamente para todas as suas necessidades de visualização;
- pode controlar quem tem acesso para visualizar ou gerenciar seus painéis por meio da IAM;

##### CloudWatch Logs

- pode ser o local centralizado para que os logs sejam armazenados e analisados;
- CloudWatch Logs pode **monitorar**, **armazenar** e **acessar** seus arquivos de log de aplicações que estão em execução em instâncias do EC2, Amazon Lambda, etc;
- permite **consultar** e **filtrar** seus dados de log;
- agente do CloudWatch permite que as instâncias do Amazon EC2 enviem **automaticamente** dados de log para o CloudWatch Logs;
- o agente inclui os seguinte componentes:
	- plug-in para a AWS CLI que envia dados de log para o CloudWatch Logs;
	- script que inicia o processo para enviar dados para o CloudWatch Logs;
	- tarefa cron que garante que o daemon esteja sempre em execução;

##### Amazon CloudWatch Events X Amazon CloudWatch Logs

- events:
	- pode acionar serviços, como o AWS Lambda, com base em eventos praticamente em tempo real;
- logs:
	- pode coletar logs de aplicativos por pontos de dados de métricas com base em eventos;
##### Terminologia do CloudWatch Logs

- os dados de log enviados para o CloudWatch podem vir de diferentes fontes;
- *evento de log :*
	- um registro da atividade registrada pela aplicação ou recurso que está sendo monitorado;
	- tem um carimbo de data/hora e uma mensagem de evento;
- *fluxo de log :*
	- os eventos de log são **agrupados** em fluxos de log;
	- são sequências de eventos de log que pertencem ao mesmo recurso que está sendo monitorado;
	- exemplo, os logs de uma instância do EC2 são agrupados em um fluxo de log que você pode filtrar ou consultar insights;
- *grupos de log :*
	- os fluxos de log são **organizados** em grupos de log;
	- é composto por fluxos de log que compartilhas as **mesmas configurações** de **retenção** e **permissões**;
	- exemplo, se você tiver várias instâncias do EC2 hospedando sua aplicação e estiver enviando dados de log da aplicação para o CloudWatch Logs, poderá agrupar os fluxo de log de cada instância em um grupo de logs;

##### Alarmes do CloudWatch

- testar uma métrica selecionada em relação a um limite específico (maior ou igual a, menor ou igual a)
- criar alarmes para iniciar ações automaticamente com base em mudanças de estado sustentadas de suas métricas;
- você configura quando os alarmes são acionados e a ação que é executada;
- deve decidir para qual métrica deseja definir um alarme;
- definir o threshold que acionará o alarme;
- define o período de tempo do threshold;
- um alarme tem três estados possíveis:
	- *ok :* a métrica está dentro do threshold definido, tudo está funcionando normalmente;
	- *alarm :* a métrica está fora do threshold definido, pode ser um problema operacional, (não sinaliza um estado de emergência imediata);
	- *insuficient_data :* o alarme acabou de iniciar, a métrica não disponível ou não há dados suficientes disponíveis para a métrica determinar o estado do alarme;
- um alarme pode ser acionado quando ele faz a transição de um estado para o outro;
- depois de acionado, pode iniciar uma ação;
- as ações pode ser:
	- uma ação do Amazon EC2, interromper, encerrar, reinicializar ou recuperar uma instância;
	- uma ação de escalabilidade, reduzir ou expandir um grupo do Auto Scaling;
	- uma notificação enviada ao Amazon Simples Notification Service (SNS);

![[Pasted image 20231220201037.png]]

![[Pasted image 20231220201826.png]]

- explicação diagrama:
	- o limite de alarme do CloudWatch é definido para 3 e a violação mínima é de 3 períodos;
	- o alarme invoca a sua ação somente quando o limite é violado por três períodos consecutivos;
	- essa situação ocorre do terceiro ao quinto período, e o estado alarme é definido como ALARM;
	- no nono período, o limite é violado novamente, mas não pelos três períodos consecutivos necessários, então o estado do alarme permanece OK; 
##### Prevenir e solucionar problemas com alarmes do CloudWatch

- usa **filtros de métrica** para transformar os dados de log em métricas com as quais você pode criar gráficos ou definir um alarme;
- pode configurar alarmes diferentes por diferentes motivos;
