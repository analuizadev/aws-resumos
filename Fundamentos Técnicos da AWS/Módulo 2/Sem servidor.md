- Serverless significa: não pode ver ou acessar infraestrutura subjacente ou instâncias que estão hospedando sua solução;
- só foca na aplicação;
- AWS Fargate, AWS Lambda exemplo de serverless;

<br />

- Amazon EC2:
	a AWS é responsável pelo hardware físico e você pelos controles lógicos, como sistema operacional convidado, segurança e patches, rede, segurança e escaçanoçodade;
<br/>
- Amazon ECS/EKS:
	executar o código em contêineres;
	a AWS é responsável por mais gerenciamento de contêineres, como implantar contêineres em instâncias do EC2 e gerenciar os cluster de contêineres;
	no entanto você ainda é responsável por manter as instâncias do EC2 subjacentes;
<br/>
- Sem Servidor:
	se quiser implantar suas workloads e aplicações sem precisar gerenciar instâncias do EC2, você pode fazer isso na AWS com computação sem servidor;