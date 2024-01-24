
- um produto AWS que ajuda a gerenciar o acesso à sua conta e aos recursos da AWS;
<br/>
- fornece uma visão centralizada de quem e o que tem autorização em sua conta da AWS (autenticação) e quem e o que tem permissão para usar e trabalhar com seus recursos da AWS (autorização);
<br/>
- permite o compartilhamento de conta sem a necessidade de compartilhar o conjuntos de chaves de acesso ou senha;
<br/>
- pode selecionar de forma granular quais ações e quais recursos de um produto, as pessoas podem ter acesso;

- função *permissão de serviços para serviços*;
	- exemplo: permite que o S3 acesse o EC2;


![[Pasted image 20231201160042.png]]
![[Pasted image 20231201161004.png]]
![[Pasted image 20231201161030.png]]
##### Recursos do IAM

- o IAM é global e não é específico para uma região, é possível ver e usar suas configurações de qualquer região;
- é integrado a muitos produtos da AWS por padrão;
- é possível estabelecer políticas de senha no IAM para especificar requisitos de complexidade e períodos de rotação obrigatórios para os usuários;
- oferece suporte a MFA;
- oferece suporte à federação de identidade; (que permite que usuários que já tem senhas em outro lugar, por exemplo, em sua rede corporativa ou com um provedor de identidade da internet, obtenham acesso temporário à sua conta da AWS);
- qualquer cliente AWS pode usar o IAM, o serviço é oferecido sem custo adicional;

##### Usuário do IAM

- representa uma pessoa ou um serviço que interage com a AWS;
- você define o usuário em sua conta da AWS;
- é possível adicionar mais de um usuário a conta;
- cada pessoa deve ter suas próprias credenciais;

##### Credenciais de usuário do IAM

um usuário do IAM é composto por um nome e um conjunto de credenciais.

- ao criar usuário é possível fornecer a ele os seguintes tipos de acesso:
	- acesso ao Console de Gerenciamento da AWS;
		-	para acessar forneça ao usuário um nome e senha;
	- acesso programático à AWS Command Line Interface (CLI) e interface de programação de aplicações da AWS (API);
		-  para acesso, a AWS gera um conjunto de chaves de acesso que pode ser usado com a AWS CLI e a API da AWS;

as credenciais do IAM são permanentes, a menos que haja uma rotação forçada pelos administradores;

ao criar é possível conceder permissões diretamente no nível do usuário;

##### Grupos do IAM

é uma coleção de usuários, todos os usuários em um grupo herdam as permissões atribuídas ao grupo, isso possibilita dar permissões a vários usuários de uma vez só;

é uma maneira mais conveniente e escalável de gerenciar permissões para usuários em sua conta da AWS, usar grupos é uma prática recomendada;

- os grupos podem ter muitos usuários;
- os usuários podem pertencer a muitos grupos;
- os grupos não podem pertencer a grupos;

##### Políticas do IAM

para gerenciar o acesso e fornecer permissões aos produtos e recursos da AWS, você cria políticas do IAM e as anexa a usuários, grupos e funções do IAM;

sempre que um usuário ou função faz uma solicitação, a AWS avalia as políticas associadas a ele;

a maioria das políticas é armazenada na AWS como documento JSON com vários elementos de política, exemplo:

![[Pasted image 20231129184728.png]]
![[Pasted image 20231129184810.png]]

##### Práticas recomendadas

- bloquear o usuário raiz:
	- não compartilhar as credenciais associadas ao usuário raiz;
	- considerar excluir as chaves de acesso do usuário raiz;
	- habilitar MFA (autenticação com multifator) na conta raiz;
- adotar o princípio de privilégio mínimo:
	- conceder apenas as permissões necessárias para fazer uma determinada tarefa;
- usar o IAM adequadamente:
	- não é usado para autenticação e autorização de sites;
	- não fornece suporte a controles de segurança para proteger SO e redes;
	- protege acesso à sua conta e aos recursos da AWS;
	- criar e gerencia usuário, grupos e funções para acessar recursos em uma única conta da AWS;
- usar funções do IAM quando possível:
	- manter funções é mais eficiente do que manter usuários;
	- as credenciais da função, fornecidas dinamicamente pelo IAM, expiram após um período definido, entre 15min a 36hrs;
- considere usar um provedor de identidade:
	- fornece uma única fonte de verdade para todas as identidades em sua organização;
	- não é necessário, mais, criar usuário do IAM diferentes na AWS;
	- pode usar funções do IAM para fornecer permissões para identidades federadas do IdP;
	- produto AWS com uso de um IdP: AWS Single Sign-On;
- considere o AWS Single Sign-On:
	- uma organização que abrange muitos funcionários e várias contas da AWS, talvez seja melhor os funcionários fazerem login com uma única credencial;
	- permite que os usuários façam login em um portal de usuários com um único conjunto de credenciais;
	- fornece acesso às contas e aplicações atribuídas em um local central;
	- semelhante ao IAM, criação de usuário, formação de grupos, permissões para grupos;