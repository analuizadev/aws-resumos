
- modelos de pagamento conforme o uso;
- três categorias:
	- pague somente o que usar;
		- paga exatamente a quantidade de recursos que realmente usa;
	- pague menos ao fazer reserva;
		- alguns serviços oferecem opções de reserva com desconto significativo em comparação com as definições de preço da instância sob demanda;
	- pague menos com descontos baseados em volume, quando usar mais;
		- alguns serviços oferecem definição de preço em camadas, portanto, o custo por unidade é incrementalmente menor com o aumento do uso;

##### Calculadora de preços da AWS

- permite explorar os serviços da AWS e gera uma estimativa de custo de seus casos de uso na AWS;
- pode organizar as suas estimativas da AWS por grupos que definir;

##### Exemplos de definição de preços da AWS

###### AWS Lambda

- a cobrança é feita com base no número de solicitações das funções no tempo necessário para serem executadas;
- permite *1 milhão de solicitações gratuitas* e até *3,2 milhões de segundos* de tempo de computação por mês;
- pode economizar nos custos cadastrando-se em um *Compute Savings Plan*;
- Compute Savings Plan : oferece custos de computação mais baixos em troca do compromisso com uma quantidade consistente de uso durante um período de um ou três anos;
	- *reserve e pague menos*;

###### Amazon EC2

- paga apenas pelo tempo de computação que usar enquanto suas instâncias estão em execução;
- pode reduzir os custos usando instâncias spot;
- pode economizar ainda mais considerando o saving plans e as instâncias reservadas;

###### Amazon S3

- armazenamento:
	- paga apenas pelo armazenamento usado;
	- taxa de armazenamento de objetos é cobrada com base nos tamanhos, storage classes e quanto tempo você armazenou cada objeto durante o mês;
- solicitações e recuperação de dados: 
	- paga por solicitações feitas ao seus objetos no bucket;
- transferência de dados:
	- não há custo para transferir os dados entre diferentes buckets do S3 ou do S3 para outros serviços dentro da mesma Região AWS;
	- você paga pelos dados que transfere para dentro e para fora do S3;
	- *não há custos* para os dados transferidos para o S3 da internet ou para o CloudFront;
	- *não há custo* para os dados transferidos para uma instância do EC2 na *mesma* Região AWS que o bucket S3;


