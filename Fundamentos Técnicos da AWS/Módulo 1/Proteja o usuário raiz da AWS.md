
quando é criado uma conta na AWS, ela se torna um usuário raiz, tendo acesso irrestrito a tudo na conta;

- o usuário raiz tem dois conjuntos de credenciais associados a ele:
	- um conjunto é o endereço de email e a senha usados para criar a conta, permite o acesso ao Console de Gerenciamento AWS;
	- o outro conjunto de credenciais é chamado de chaves de acesso, que permitem que faça solicitações programáticas do AWS CLI ou da API AWS;
<br/>
- as chave são compostas por duas partes:
	- ID da chave de acesso, exemplo  _**A2lAl5EXAMPLE**_
	- chave de acesso secreta, exemplo _**wJalrFE/KbEKxE**_

é necessário o ID da chave de acesso e da chave de acesso secreta para autenticar suas solicitações por meio da AWS CLI ou da API da AWS;

##### Práticas recomendadas para garantir a segurança do usuário raiz

- escolher uma senha forte;
- nunca compartilhar a senha ou chave de acesso;
- desativar ou excluir as chaves de acesso associadas ao usuário raiz;
- não usar o usuário  raiz para tarefas administrativas ou diárias;

##### MFA
é recomendado após a criação da conta, para proteção do usuário raiz, a autenticação com multifator (MFA), pois ela precisa de dois ou mais métodos de autenticação para verificar uma identidade;

==multifator também pode ser usada para controlar o acesso a APIs de serviço específicas da AWS==

- MFA usa três categorias de informações:
	- algo que você sabe, nome, senha ou PIN;
	- algo que você tem, senha única de um dispositivo de hardware ou aplicação móvel;
	- algo que você é, tecnologia de reconhecimento facial ou biometria;

★ dispositivos MFA compatíveis:

![[Pasted image 20231129180001.png]]

