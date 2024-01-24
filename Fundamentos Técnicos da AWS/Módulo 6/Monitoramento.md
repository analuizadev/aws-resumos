
- coleta, analisa e usa dados para tomar decisões ou responder perguntas sobre seus recursos e sistemas de TI;
- fornece um pulso quase em tempo real em seu sistema;
- pode usar os dados coletados para observar problemas operacionais causados por eventos;
	- uso excessivo de recursos;
	- falhas de aplicação;
	- configuração incorreta de recursos;
	- eventos relacionados à segurança;
- funciona como saídas do sistema ou métricas;

##### Use métricas para resolver problemas

- os recursos AWS que hospedam suas soluções criam várias formas de dados que podem ser coletados;
- cada ponto de dados **individual** que um recurso cria é uma **métrica**;
- as métricas coletadas e analisadas ao longo tempo tornam-se **estatísticas**;
- exemplos de métricas que as instâncias EC2 têm:
	- utilização de rede;
	- performance do disco;
	- utilização da memória;
	- logs criados pela aplicações em execução no Amazon EC2;
	- utilização de CPU;

##### Tipos de métricas

- recursos diferentes da AWS criam **diferentes tipos** de métricas;
- um bucket do Amazon S3, por exemplo, cria métrica relacionadas:
	- aos objetos armazenados em um bucket;
	- tamanho geral;
	- número de objetos em um bucket;
	- às solicitações feitas ao bucket, leitura, gravação de objetos;
- o Amazon RDS cria métricas:
	- conexão de banco de dados;
	- utilização de CPU de uma instância;
	- consumo de espaço em disco;

##### Benefícios do monitoramento 

- oferece visibilidade de seus recursos;
- responda a problemas operacionais de forma proativa antes que os usuários finais estejam cientes deles;
	- acompanha taxa de resposta a erros;
	- latência de solicitações;
	- sinaliza quando ocorrerá uma interrupção;
- melhore a performance e confiabilidade seus recursos;
	- pode identificar gargalos e arquiteturas ineficientes;
- reconheça ameaças à segurança e eventos;
	- identifica anomalias como picos de tráfego incomuns;
	- endereços IP incomuns que acessam seus recursos;
- tome decisões orientadas por dados para seu negócio;
	- exemplo de site, pode visualizar o número de usuários que usam o novo recurso;
- crie soluções mais econômicas;

##### Visibilidade

- Amazon CloudWatch:
	- serviço de monitoramento e observabilidade que coleta dados;
	- fornece insights acionáveis sobre suas aplicações;
	- permite que você responda a mudanças de performance em todo o sistema;
	- otimize o uso de recursos;
	- obtenha uma visão unificada da integridade operacional;
- CloudWatch pode ser usado para:
	- detectar comportamento anômalo em seus ambientes;
	- definir alarmes para avisar quando algo não estiver certo;
	- visualizar logs e métricas com o Console de Gerenciamento da AWS;
	- tomar ações automatizadas, como escalabilidade;
	- solucionar problemas;
	- descobrir insights para manter a integridade das aplicações;
