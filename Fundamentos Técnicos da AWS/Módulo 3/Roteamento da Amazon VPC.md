
- tabela de roteamento contém um conjunto de regras, chamadas rotas;

##### Tabela de rotas principal

- quando você cria uma VPC, a AWS cria uma tabela de rotas chamada tabela de rotas principal;
- as rotas são usadas para determinar o local em que o tráfego de rede é direcionado;
- a AWS pressupõe, que ao criar uma nova VPC com sub-redes, você deseja que o tráfego flua entre elas;
- a configuração padrão da tabela de rotas principal é permitir o tráfego entre todas as sub-redes na rede local;
- exemplo de tabela de rotas principal:
	![[Pasted image 20231207155944.png]]
	- destino: um intervalo de endereços IP para o local para o qual você deseja que seu tráfego vá; *o destino é o intervalo de IP da rede VPC*;
	- *target é a conexão pela qual você deseja enviar o tráfego*; nesse caso, o tráfego é roteado pela rede VPC local;

##### Tabelas de rotas personalizadas

- você pode criar sub-redes separadas para os recursos e fornecer rotas diferentes para cada uma delas;
- se você associar uma tabela de rotas personalizada a uma sub-rede, a sub-rede a usará em vez da tabela de rotas principal;
- cada tabela de rotas personalizada criada terá a rota local já dentro dela, permitindo que a comunicação flua entre todos os recursos e sub-redes na VPC;
- *a rota local não pode ser excluída*;

![[Pasted image 20231207161339.png]]