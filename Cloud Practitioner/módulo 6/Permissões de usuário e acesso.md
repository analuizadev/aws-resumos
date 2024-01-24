
##### IAM

- permite que você gerencie o acesso aos serviços e recursos da AWS com segurança;
- oferece flexibilidade  de configurar o acesso com base nas necessidades operacionais e de segurança especificas da sua empresa;
- recursos do IAM:
	- usuários, grupos e perfis do IAM;
	- políticas do IAM;
	- autenticação multifator;

##### Usuário raiz da conta AWS

- usuário inicial ao criar uma conta AWS;
- é acessado ao entrar com endereço de e-mail e a senha;
- tem acesso completo a todos os serviços e recursos AWS na conta;

![[Pasted image 20231227165518.png]]

##### Usuários do IAM

- uma identidade que você cria na AWS;
- representa a pessoa ou o aplicativo que interage com os serviços e recursos AWS;
- consiste em um nome e credenciais;
- deve conceder permissões necessárias ao usuário do IAM;
- *prática recomendada :* 
	- crie usuários individuais do IAM para cada pessoa que precisa acessar a AWS;

##### Políticas do IAM

- um documento que concede ou nega permissões para serviços e recursos AWS;
- permite que você personalize os níveis de acesso dos usuários aos recursos;
- *prática recomendada :*
	- siga o princípio de segurança de *menor privilégio* ao conceder permissões.;
	- conceda apenas permissões necessárias, nada além;
---
exemplo:

concedendo permissões a um usuário. No caso, será concedido permissão de acessar recibos mantidos em um bucket do Amazon S3 com o ID: AWSDOC-EXAMPLE-BUCKET;

no exemplo, a política do IAM permite uma ação específica do S3 : ListObject;
a política também menciona o ID de bucket específico;

```
{
	"Version":"2012-10-17",
	"Statement":{
		"Effect":"Allow",
		"Action":"s3:ListObject",
		"Resource":"arn:aws:s3:::AWSDOC-EXAMPLE-BUCKET"
	}
}
```
##### Grupos do IAM

- é um conjunto de usuários do IAM;
- ao atribuir uma política do IAM a um grupo, todos os usuários do grupo recebem as permissões da política;

![[Pasted image 20231227171509.png]]

##### Perfis do IAM

- uma identidade que você pode assumir para obter acesso temporário a permissões;
- antes que um usuário, aplicação ou serviço do IAM, possa assumir um perfil do IAM, ele precisa receber permissões para alterar para o perfil;
- quando alguém assume uma função do IAM, ele abandona todas as permissões anteriores que tinha em uma função anterior e assume as permissões da nova função;
- *prática recomendada :* 
	- os perfis do IAM são ideais para situações em que o acesso a serviços ou recursos precisa ser concedido *temporariamente*, em vez de por longo prazo;

##### Autenticação com multifator (MFA)

- camada extra de segurança para sua conta AWS;