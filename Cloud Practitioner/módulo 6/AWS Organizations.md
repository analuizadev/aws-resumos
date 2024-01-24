
- usar para consolidar e gerenciar *múltiplas* contas AWS em um *local central*;
- quando você cria uma organização, o AWS Organizations cria automaticamente uma *raiz*;
- raiz é o contêiner primário para todas as contas da organização;
- você pode controlar de maneira centralizada as permissões para as contas em sua organização usando as *políticas de controle de serviço (SCPs*;
- as SCPs permitem que você coloque restrições nos *serviços AWS, recursos e ações individuais de API* que os usuários e funções em cada conta podem acessar;
- os recursos SCPs podem ser aplicados as identidades:
	- uma conta membro individual;
	- uma unidade organizacional (UO);

##### Unidades organizacionais 

- você pode agrupar contas em unidades organizacionais (UO) para facilitar o gerenciamento de contas com requisitos de negócios ou segurança semelhantes;
- ao aplicar uma política a uma UO, todas as contas na UO herdam automaticamente as permissões especificadas na política;
- ao organizar contas separadas em UO, você pode *isolar* mais facilmente *cargas de trabalho* ou *aplicações com requisitos de segurança específicos*;
- ao agrupar suas contas em UOs, você pode conceder acesso facilmente aos serviços e recursos de que eles precisam;
	- também impede o acesso a qualquer serviço ou recurso desnecessário;

![[Pasted image 20231227175739.png]]

- os departamentos jurídicos e de RH precisam acessar os *mesmos serviços e recursos AWS*, por isso é preciso colocá-los em uma UO juntos;