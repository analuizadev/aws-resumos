
##### Problemas de capacidade

- a disponibilidade e escalabilidade são melhoradas ao adicionar mais um servidor;
- porém, todo o sistema pode ficar indisponível novamente se houver um problema de capacidade;

##### Escalabilidade vertical

- se muitas solicitações forem enviadas para um único sistema ativo-passivo, o servidor ativo ficará indisponível e executará o failover para o servidor passivo;
- com **ativo-passivo** é necessário **escala vertical**, aumentar o tamanho do servidor;
	- no caso, aumentar a capacidade da instância EC2, quando tiver muitas solicitações;
	- diminuir,, quando o número de solicitações for reduzido;
- um servidor tem um limite para escalar verticalmente;
	- caso atingido o limite, teria que criar outro sistema ativo-passivo e dividir as solicitações e funcionalidades entre ele;
- no sistema **ativo-ativo**, pode haver **escalonamento horizontal** com adição de mais servidores;

##### Escalabilidade horizontal

- um sistema ativo-ativo já foi criado como stateless, não armazena um sessão do cliente no servidor;
- significa que ter dois ou mais servidores não exigira alterações na aplicação;
- seria apenas uma questão de criar mais instâncias quando necessário e desligá-las quando o tráfego diminuir;
- o Amazon EC2 Auto Scaling cuida dessa tarefa criando e removendo automaticamente instâncias EC2 com base em métricas do Amazon CloudWatch;

##### ELB com EC2 Auto Scaling

- o ELB se integra com o EC2 Auto Scaling;
- assim que uma nova instância é adicionada, o ELB é notificado;
- porém, só pode enviar tráfego para essa nova instância *após a verificação de integridade* do ELB, que valida se a aplicação em execução na instância do EC2 está disponível;
- o monitoramento é uma parte importante dos balanceadores porque eles *devem rotear o tráfego para instâncias íntegras do EC2*;
- o ELB suporta **dois tipos de verificações de integridade**:
	- estabelecimento de uma conexão com uma instância do EC2 de back-end com uso do TCP e marcação da instância como disponível se a conexão for bem sucedida;
	- fazer uma solicitação HTTP e HTTPS para uma página da Web especificada e validar se um código de resposta HTTP é retornado;

##### Amazon EC2 Auto Scaling

- adiciona e remove capacidade para manter uma performance estável e previsível com o menor custo possível;
- paga apenas por aquilo que sua aplicação precisa;
- em aplicações que tem uso constante, o auto scaling pode ajudar no gerenciamento de frotas;
- substitui instâncias automaticamente;
- ajuda a escalar sua infraestrutura e garante alta disponibilidade;

##### Configurar componentes do EC2 Auto Scaling

- *três principais componentes :*
	- modelo de lançamento ou configuração;
	- grupo do EC2 Auto Scaling;
	- políticas de escalabilidade;

###### Modelos de execução

- o EC2 Auto Scaling precisa saber as informações para criação da instância do EC2;
- essas informações são armazenadas em um *modelo de inicialização*;
- pode usar o modelo de execução para executar *manualmente* uma instância do EC2;
	- também pode ser usado com o EC2 Auto Scaling;
- oferece suporte ao versionamento;
	- permite reverte rapidamente se houver um problema ou uma necessidade de especificar uma versão padrão;

![[Pasted image 20231221164748.png]]

- pode criar um modelo de inicialização de *três maneiras* :
	- maneira **mais rápida** é usar uma instância do EC2 existente, todas as configurações já estão definidas;
	- outra opção é criar por meio de um modelo já existente ou de uma versão anterior de um modelo de inicialização;
	- última opção é criar um modelo do zero, definindo todos os parâmetros da instância do EC2;
- outra maneira de definir o que o Amazon Auto Scaling precisa dimensionar é usar uma *configuração de execução*;
	- é semelhante ao modelo de inicialização, mas *não permite* o versionamento usando uma configuração de execução criada anteriormente como modelo;
	- também não permite a criação por meio de uma instância EC2 já existente;

##### Grupos do EC2 Auto Scaling

- ajuda a definir o local em que o EC2 Auto Scaling implanta seus recursos;
- é nos grupos que você **especifica a VPC e as sub-redes em que a instância do EC2 deve ser executada**;
- o EC2 Auto Scaling cuida da criação de instâncias do EC2 nas sub-redes, portanto, selecione pelos menos duas sub-redes que estejam em **diferentes AZs**;
- pode especificar o tipo de compra para as instâncias do EC2;
- pode usar somente sob demanda, somente spot ou uma combinação dos dois;
	- permite que você aproveite as instâncias spot com o mínimo de sobrecarga administrativa;
- para especificar *quantas instâncias* do EC2 Auto Scaling deve iniciar, você tem *três configurações* de capacidade a serem definidas para o *tamanho do grupo*:
	- *mínimo :* número mínimo de instâncias em execução no grupo do Auto Scaling, mesmo que o threshold (limite) para diminuir a quantidade de instâncias seja atingido;
	- *máximo :* o número máximo de instâncias em execução no grupo do Auto Scaling, mesmo que o threshold (limite) para adicionar novas instâncias seja atingido;
	- *capacidade desejada :* a quantidade de instâncias que devem estar no seu Auto Scaling. esse número só pode estar no intervalo ou ser igual ao número mínimo ou máximo. o EC2 Auto Scaling *adiciona ou remove instâncias automaticamente para corresponder ao número de capacidade desejado*;

![[Pasted image 20231221170508.png]]


##### Disponibilidade com o EC2 Auto Scaling

- números diferentes para capacidade mínima, máxima e desejada são usados para ajustar dinamicamente a capacidade;
- se preferir usar o EC2 Auto Scaling para gerenciamento de frota, você poderá definir as três configurações para o mesmo número;
- *exemplo*
	- se ambos os três forem definidos para 4, o Auto Scaling garantirá que se uma instância não for íntegra, ele a substituirá para garantir que sempre quatro instâncias do EC2 estejam disponíveis;
- isso garante alta disponibilidade para suas aplicações;

![[Pasted image 20231221170947.png]]

##### Automação com políticas de escalabilidade

- por padrão um grupo de Auto Scaling será mantido na capacidade inicial desejada;
- é possível alterar a capacidade desejada manualmente ou através de políticas de escalabilidade;
- assim como em monitoramento, as políticas de escalabilidade usam alarmes e métricas para saber quando agir;
- **três tipos** de políticas de escalabilidade estão disponíveis:
	- *escalabilidade de rastreamento simples*;
	- *de etapas*;
	- *de destino*;

###### Política de escalabilidade simples

- usa um alarme do CloudWatch e especifica o que fazer quando ele é acionado;
- pode ser várias instâncias para adicionar ou remover, ou um número específico para definir a capacidade desejada;
- pode especificar uma *porcentagem do grupo* em vez de usar uma quantidade de instâncias do EC2, faz com que o grupo cresça ou diminua *mais rapidamente*;
- após acionada, a política de escalabilidade *aguarda um período de desaquecimento* antes de tomar qualquer outra ação;
	- leva tempo para que as instâncias sejam iniciadas e o alarme pode ser acionado enquanto a instância ainda estão inicializando;

###### Política de escalabilidade de etapas

- respondem a alarmes adicionais mesmo quando uma ação de escalabilidade ou substituição de verificação de integridade estiver em andamento;

###### Política de dimensionamento para monitoramento de targets

- cria automaticamente os alarmes necessários do CloudWatch;
	- você só precisa fornecer o valor de destino a ser rastreado;
- é bom para aplicações que são escaladas com base na utilização média da CPU, na utilização média da rede ou na contagem de solicitações;