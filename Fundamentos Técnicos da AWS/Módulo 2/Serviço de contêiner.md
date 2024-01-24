-  contêineres fornecem portabilidade e eficiência;
- podem hospedar uma variedade de workloads diferentes, incluindo aplicações Web, migrações lift and shift, aplicações distribuídas e simplificação de ambientes em desenvolvimento, teste e produção;
- com contêineres, as workloads podem ser transportadas de um lugar para outro, como do desenvolvimento à produção ou de on-premises para a nuvem;

##### Docker:
- é um tempo de execução de contêiner popular que simplifica o gerenciamento de toda a pilha de sistemas operacionais necessária para o isolamento de contêineres, incluindo rede e armazenamento;
- ajuda os clientes a criar, empacotar, implantar e executar os contêineres;

##### Contêineres X VMs :
![[Pasted image 20231204182452.png]]

- as máquinas virtuais compartilham o mesmo sistema operacional e kernel (núcleo) que o host em que estão;
- contêiner contêm o próprio sistema operacional;
- cada VM deve manter uma cópia de um SO, o que resulta em um grau de espaço desperdiçado;
- contêiner é mais leve, gira mais rápido, quase instantaneamente;
- a diferença no tempo de startup se torna fundamental em aplicações que precisam ser escaladas rapidamente durante as intermitências de entrada/saída;
- apesar dos contêineres serem mais rápidos, as VMs oferecem toda a força de um SO e mais recursos, como instalação de pacotes, kernel dedicado e muito mais;

##### Orquestrar contêineres
- na AWS os contêineres são executados em instâncias do EC2;
- pode ter uma instância grande e executar alguns contêineres nessa instância;
- a maioria das empresas e organizações executa muitos contêineres em muitas instâncias do EC2 em várias zonas de disponibilidade;
- gerenciar computação em grande escala:
	1. como colocar seus contêineres em suas instâncias;
	2. o que acontece se o contêiner falhar;
	3. o que acontece se sua instância falhar;
	4. como monitorar implantações de seus contêineres;
- essa coordenação é tratada por um serviço de orquestração de contêineres;
- a AWS oferece dois serviços de orquestração de contêineres:
	- Amazon Elastic Container Service (ECS);
	- Amazon Elastic Kubernetes Service (EKS);

##### Gerenciar contêineres com ECS:
- AWS Fargate gerencia os contêineres;
- é um serviço de orquestração de contêineres completo que ajuda a criar novos contêineres e gerenciar em um cluster de instâncias do EC2;

![[Pasted image 20231204183649.png]]

- para fazer a execução e gerenciamento, é necessário instalar o agente de contêiner do Amazon ECS nas instâncias EC2;
- esse agente é de código aberto e é responsável por se comunicar com o Amazon ECS Service sobre detalhes de gerenciamento de cluster;
- pode executar o agente em AMIs Linux e Windows;
- uma instância com o agente de contêiner instalado, geralmente, é chamada de instância de contêiner;

![[Pasted image 20231204183936.png]]

- após as instâncias estarem ativas e em execução é possível executar diversas ações:
	- iniciar e interromper contêineres;
	- obter o estado do cluster;
	- aumentar a escala na horizontal e na vertical;
	- agendar o posicionamento de contêineres em todo o cluster;
	- atribuir permissões e reunir requisitos de disponibilidade;
- para preparar sua aplicação para ser executada, você cria uma definição de tarefa;
- a definição de tarefa é um arquivo de texto, no formato JSON, que descreve um ou mais contêineres;
- ==uma definição de tarefa é semelhante a um mapa que descreve os recursos necessários para executar um contêiner, como CPU, memória, portas, imagens, armazenamento e informações de rede==

no exemplo, a execução é realizada no servidor Web Nginx;

![[Pasted image 20231204185404.png]]

##### Usar o Kubernetes com o Amazon Elastic Kubernetes Service (EKS)
- kubernetes uma plataforma portátil, extensível e de código aberto para gerenciar workloads e serviços em contêineres;
- ao reunir o desenvolvimento de software e as operações por design, o Kubernetes criou um ecossistema em rápido crescimento, muito popular e bem-estabelecido no mercado;
- se já usa Kubernetes, poderá usar o Amazon EKS para orquestrar as workloads na Nuvem AWS;
- o Amazon EKS é conceitualmente semelhante ao Amazon ECS, mas as diferenças:
	- uma instância do EC2 com o agente ECS instalado e configurado é chamada de **instância de contêiner**; No Amazon EKS, ele é chamado de **nó de trabalho**;
	- um contêiner ECS é chamado de **tarefa**; No Amazon EKS, é chamado de **pod**;
	- enquanto o Amazon ECS é executado na **tecnologia nativa da AWS**, o Amazon EKS é executado sobre o **Kubernetes**;
- Se você tiver contêineres em execução no Kubernetes e quiser uma solução de orquestração avançada que possa fornecer simplicidade, alta disponibilidade e controle refinado sobre sua infraestrutura, o Amazon EKS pode ser a ferramenta para você;