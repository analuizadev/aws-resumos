
- serviço da web que inspeciona seu ambiente AWS;
- faz recomendações em tempo real de acordo com as práticas recomendadas;
- compara as descobertas com as práticas recomendadas da AWS em cinco categorias:
	- *otimização de custos*;
		- como você pode economizar dinheiro na AWS reduzindo recursos não utilizados e ociosos ou assumindo compromissos de capacidade reserva;
	- *desempenho*;
		- aprimore o desempenho do serviço verificando os limites de serviço, garantindo a utilização da taxa de transferência provisionada e monitorando instâncias com uso excessivo;
	- *segurança*;
		- aprimore a segurança eliminando lacunas, ativando vários recursos de segurança da AWS e analisando suas permissões;
	- *tolerância a falhas*;
		- aumente a disponibilidade e a redundância do aplicativo da AWS;
	- *limites de serviço*;
		- verifica o uso do serviço *acima de 80%* do limite de serviço;
- para as verificações em cada categoria, oferece uma lista de ações recomendadas e recursos adicionais para saber mais sobre as práticas recomendadas da AWS;
- as seguintes verificações estão disponíveis para todos os cliente *sem nenhum custo* :
	- limites de serviço;
	- security groups> postas específicas sem restrição;
	- uso do AWS IAM;
	- autenticação MFA em conta raiz;
	- snapshots públicos do Amazon EBS;
	- snapshots públicos do Amazon RDS;

##### Painel do Trusted Advisor 

- você pode analisar as verificações concluídas para otimização de custos, desempenho, segurança, tolerância a falhas e limites de serviço;
- para cada categoria:
	- a marca de verificação **verde** indica o número de itens para os quais *nenhum problema foi detectado*;
	- o triângulo **laranja** representa o número de *investigações* recomendadas;
	- o círculo **vermelho** representa o número de *ações* recomendadas;

![[Pasted image 20231228134008.png]]

