
- banco de dados não relacional;
- um tipo de abordagem estrutural para bancos de dados não relacionais é o uso de *pares de chave-valor*;
- os dados são organizados em itens (chaves) e cada item tem um atributo (valores);
- pode adicionar e remover atributos de itens na tabela a qualquer momento,
- nem todos os itens precisam ter os mesmo atributos;
- Amazon DynamoDB oferece um desempenho de um dígito de milissegundo em qualquer scaling;


![[Pasted image 20231226164626.png]]

- [*] Serverless: 
	- DynamoDB é sem servidor, você não precisa  provisionar, aplicar patches ou gerenciar servidores;
	- não precisa instalar, manter ou operar o software;

- [*] Auto Scaling:
	- à medida que o tamanho do banco de dados expande ou retrai, o DynamoDB é dimensionado automaticamente para se ajustar às alterações na capacidade e manter o desempenho consistente;
	- escolha adequada para casos de uso que exigem alto desempenho durante o scaling;