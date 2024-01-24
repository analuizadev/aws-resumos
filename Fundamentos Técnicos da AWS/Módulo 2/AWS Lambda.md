- opção sem servidor (serverless);
- lambda executa sua função em um ambiente seguro e isolado;
- é mais adequado para processamentos rápidos;
- só é cobrado quando o código estiver em execução;

##### computação sem servidor

- nenhum servidor para provisionar ou gerenciar;
- escalas com uso;
- você nunca paga por recursos ociosos;
- disponibilidade e tolerância a falhas são incorporados;

##### AWS Fargate

- o Amazon ECS e o Amazon EKS permitem que você execute seus contêineres nos dois modos a seguir:
	- Amazon EC2;
	- AWS Fargate;
- é um mecanismo de computação sem servidor especialmente desenvolvido para contêineres;
- dimensiona e gerencia a infraestrutura, permitindo os devs trabalharem apenas com as aplicações;
- ele consegue com a alocação da quantidade certa de computação, com a eliminação da necessidade de escolher e lidar com instâncias do EC2 e a capacidade de cluster e dimensionamento;
- oferece suporte com a arquitetura Amazon ECS e Amazon EKS;
- fornece isolamento de workload e segurança aprimorada por projeto;
- abstrai a instância do EC2 para que você não seja obrigado a gerenciá-la;
- se integra nativamente ao AWS IAM e ao Amazon VPC;
- a integração nativa com a Amazon VPC permite que você inicie contêineres Fargate dentro de sua rede e controle a conectividade com suas aplicações;

##### Executar códigos no AWS Lambda

- implanta workloads e aplicações sem que o usuário precise gerenciar instâncias ou contêineres do EC2;
- pode executar código para praticamente qualquer tipo de aplicação ou serviço de backend;
- processamento de dados, processamento de stream em tempo real, machine learning, WebSockets, backends IoT, backends móveis e aplicações Web;
- não precisa ser administrada pelo usuário;
- você  faz upload do seu código-fonte e o Lambda se encarrega de todos os itens necessários para executar e alterar a escala do código com  alta disponibilidade;
- não há servidores para gerenciar, proporcionando escalabilidade contínua com medição de subsegundo e performance constante;




##### Como a AWS Lambda funciona

- uma função da lambda tem três componentes principais:
	- acionador (gatilho);
	- código;
	- configuração;
	![[Pasted image 20231205174731.png]]

###### código:
- o código é o código-fonte que descreve o que a função do Lambda deve ser executada;
- pode ser criado de três maneiras:
	- você cria o código do zero;
	- você usa um mapa que a AWS fornece;
	- você usa algum código do AWS Serverless Application Repository, um recurso que contém aplicações de amostra, como código "hello world", código exemplo do Amazon Alexa Skill, código de redimensionamento de imagens, codificação de vídeo e muito mais;
- ao criar a função, você específica o tempo de execução no qual você deseja que o código seja executado;
- tempos de execução integrados:
	- python;
	- go;
	- node.js
	- ruby;
	- java;
	- .NET core;
- ou pode implementar suas funções do Lambda para serem executadas em um tempo de execução personalizado;


###### configuração:
- consiste em informações que descrevem como a função deve ser executada;
- você específica o posicionamento da rede, variáveis de ambiente, memória, tipo de invocação, conjuntos de permissões, etc;

###### acionadores:
- descrevem quando uma função do Lambda deve ser executada;
- integra sua função do Lambda com outros recursos AWS, permitindo que você execute sua função do Lambda em resposta a determinadas chamadas de API que ocorrem em sua conta da AWS;
- aumenta sua capacidade de responder a eventos no console sem precisar executar ações manuais;


##### Handler de função do AWS Lambda
- é o método no código da função que processa eventos;
- quando sua função é invocada, o Lambda executa o método do manipulador;
- quando o manipulador é encerrado ou retorna uma resposta, ele se torna disponível para lidar com outro evento;

![[Pasted image 20231205175952.png]]

###### Nomeação:

- o nome do manipulador de função do Lambda especificado no momento em que você cria uma função do Lambda é derivado do seguinte:
	- nome do arquivo no qual a função de manipulador do Lambda está localizada;
	- nome da função do manipulador Python;
- um manipulador de função pode ser qualquer nome;
- o padrão no console do Lambda é ==lambda_function.lambda_handler== ;
- esse nome reflete o nome da função como lambda_handler e o arquivo em que o código do manipulador está armazenado em lambda_function.py;

###### Granularidade de faturamento

- permite que você execute código sem provisionar ou gerenciar servidores;
- você paga apenas por aquilo que você usa;
- você é cobrado pelo número de vezes que seu código é acionado (solicitações) e pelo tempo que o código é executado, com aproximação de 1ms (duração) mais próximo;
- pode ser econômico executar funções cujo tempo de execução é muito baixo;

