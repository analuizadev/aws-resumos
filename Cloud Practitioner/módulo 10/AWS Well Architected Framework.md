
- te ajuda a entender como projetar e operar sistemas confiáveis, seguros e econômicos na nuvem da AWS;
- é possível avaliar de maneira consistente suas arquiteturas em relação às praticas recomendadas e aos princípios de projeto e a identificar áreas para melhorias;
- se baseia em *seis pilares* :
	- excelência operacional;
	- segurança;
	- confiabilidade;
	- eficiência de desempenho;
	- otimização de custos;
	- sustentabilidade;

![[Pasted image 20240104144308.png]]

##### Excelência operacional

- capacidade de *executar* e *monitorar sistemas* para entregar valor comercial e melhorar continuamente os processos e procedimentos de apoio;
- os princípios de design para a excelência operacional na nuvem incluem:
	- executar operações como código;
	- anotar documentação;
	- antecipar falhas;
	- fazer com frequência alterações pequenas e reversíveis;

##### Segurança

- capacidade de proteger informações, sistemas e ativos e, ao mesmo tempo, entregar valor comercial por meio de avaliações de risco e estratégias de mitigação;
- práticas recomendadas:
	- automatizar as práticas recomendadas de segurança quando possível;
	- aplicar segurança em todas as camadas;
	- proteger os dados em trânsito e em repouso;

##### Confiabilidade

- capacidade de um sistema fazer o seguinte:
	- recuperar-se de interrupções na infraestrutura ou no serviço;
	- adquirir dinamicamente recursos de computação para atender à demanda;
	- reduzir interrupções, como configurações incorretas ou problemas de rede transitórios;
- inclui:
	- testes de procedimentos de recuperação;
	- scaling horizontal para aumentar a disponibilidade agregada do sistema;
	- recuperação automática de falhas;

##### Eficiência de desempenho

- capacidade de usar recursos computacionais com eficiência para cumprir requisitos do sistema e manter essa eficiência à medida que a demanda muda e as tecnologias evoluem;
- a avaliação da eficiência de desempenho de sua arquitetura inclui:
	- experimentar com mais frequência;
	- usar arquiteturas serverless;
	- projetar sistemas para ter alcance global em minutos;

##### Otimização de custos

- capacidade de executar sistemas para entregar valor comercial com o menor preço;
- a otimização de custos inclui:
	- adoção de um modelo de consumo;
	- análise e atribuição de despesas;
	- uso de serviços gerenciados para reduzir os custos de propriedade;

##### Sustentabilidade

- capacidade de melhorar continuamente os impactos da sustentabilidade, *reduzindo o consumo de energia* e aumentando a eficiência em todos os componentes de uma carga de trabalho, maximizando os benefícios dos recursos provisionados e minimizando o total de recursos necessários;
- um bom design para a sustentabilidade:
	- entenda seu impacto;
	- estabeleça metas de sustentabilidade;
	- maximize metas de sustentabilidade;
	- antecipe e adote novas ofertas de hardware e software mais eficientes;
	- use serviços gerenciados;
	- reduza o impacto downstream de suas cargas de trabalho na nuvem;

##### 6 princípios gerais de design:

- pare de adivinhar suas necessidades de capacidade;
- testar sistemas em escala de produção;
- automatize para facilitar a experimentação arquitetônica;
- permitir arquiteturas evolutivas;
- impulsione arquiteturas usando dados;
- melhore durante os dias de jogo;