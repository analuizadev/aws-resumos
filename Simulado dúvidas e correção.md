
#### Primeiro simulado udemy

- [?] Uma aplicação disponibiliza dados por meio de APIs REST para várias aplicações externas. Considerando possíveis cenários de manutenção e evolução futuras, qual serviço pode auxiliar na *gestão de múltiplas versões de uma API*, garantindo a compatibilidade contínua com todos os seus consumidores?
	- Resp : **API Gateway**;
	- [*]  o versionamento do API Gateway permite *criar versões separadas de suas APIs*, permitindo evolução controlada e gerenciamento de mudanças.

- [!] Uma startup necessita realizar a implementação do *armazenamento e sincronização de dados de uma aplicação entre diversos dispositivos móveis e interfaces web*. Qual serviço da AWS pode ser empregado para atender a essa necessidade?
	- Resp : **AWS Cognito** 
	- [*] o Amazon Cognito  é um serviço de autenticação e autorização que permite criar sistemas de login seguro para aplicativos. Ele gerencia identidades de usuários e fornece tokens para acessar recursos. O serviço oferece *sincronização de dados entre dispositivos*, permitindo que dados de aplicativos sejam mantidos consistentes em *diversas plataformas*. Simplifica a autenticação de usuários e o gerenciamento de dados compartilhados entre dispositivos.

- [?]  Uma empresa busca aprimorar a eficiência dos custos ao utilizar o serviço S3. Neste contexto identificou a presença de numerosos registros armazenados que poderiam ser *removidos após decorridos 30 dias* desde sua criação. Como seria possível otimizar essa situação?
	- Resp : **Configurando o S3 Lifecycle para que os objetos expirem em 30 dias para serem automaticamente excluídos**
	- [*] o Lifecycle do S3 envolve a criação, possível transição para classes de armazenamento mais baratas, acesso contínuo, expiração automática e *exclusão de objetos*, permitindo uma gestão eficiente do armazenamento;

- [?] O que é possível fazer com o *Amazon QuickSight*?
	- Resp : **Criar DashBoards de BI com uso de Aprendizado de Máquina**

- [?] A Chief Technology Officer (CTO) de uma rede hospitalar almeja incorporar o *AWS Data Exchange* em suas plataformas. Para que finalidades esse serviço pode ser utilizado nesse contexto?
	- Resp : **Para compartilhar dados de pacientes com outras organizações de saúde**
	- [*] AWS Data Exchange pode ser usado para compartilhar dados médicos e de saúde de maneira segura entre organizações de saúde, pois tem o objetivo de aumentar a velocidade da obtenção de valor de conjuntos de dados de terceiros na nuvem;

- [?] Qual o serviço serverless que permite a execução de *consultas utilizando padrão SQL para analisar dados no Amazon S3*?
	- Resp : **Athena**
	- [*] AWS Athena você pode criar consultas diretamente nos arquivos que estão no S3 e executá-las sem servidor;

- [!] Utilizando os serviços da AWS, qual é a *sequência esperada numa pipeline de CI/CD*?
	- Resp : **CodeCommit, CodeBuild, CodeDeploy**
	- [*] Essa é uma sequência lógica numa esteira de desenvolvimento:
		-  CodeCommit - Gerenciamento dos fontes através de funções do Git.
		- CodeBuild - Compilação e Testes automatizados.
		- CodeDeploy - Implantação.

- [?] Um arquiteto de soluções está em busca de um serviço capaz de identificar os *sentimentos expressos em textos digitados* durante conversas entre clientes e atendentes em um chat de sua instituição. Qual serviço pode ser utilizado para atender a essa necessidade?
	- Resp : **Comprehend**
	- [*] Amazon Comprehend usa machine learning e processamento de *linguagem natural* (NLP) para identificar o idioma do texto, extrair as frases principais, lugares, pessoas, marcas ou eventos, *entender o sentimento* em relação a produtos ou serviços e identificar os tópicos principais a partir de uma biblioteca de documentos;

- [?] Um banco precisa executar milhares de *tarefas de computação em lote* com eficiência. Qual é o serviço mais indicado para essa necessidade ?
	- Resp : **AWS Batch**

