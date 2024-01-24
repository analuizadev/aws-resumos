
os serviços de armazenamento da AWS são agrupados em três categorias:
1. armazenamento de blocos;
2. armazenamento de arquivos;
3. armazenamento de objetos;

##### Armazenamento de arquivo

- trata os arquivos como uma unidade singular;
- os arquivos são organizados em uma hierarquia semelhante a uma árvores que é composta por pastas e subpastas;
- cada arquivo tem metadados, como nome do arquivo, tamanho do arquivo e a data em que foi criado;
- o arquivo também tem um caminho, por exemplo: computer/Application_files/Cat_photos/cats-03.png;
- o armazenamento de arquivos é **ideal** quando você **precisa de acesso centralizado a arquivos que precisam ser facilmente compartilhados e gerenciados por vários computadores host**;
- normalmente, esse armazenamento é montado em vários host e requer bloqueio de arquivos e integração com protocolos de comunicação do sistema de arquivos existentes;
- caso de uso comuns para armazenamento de arquivos incluem:
	- grandes repositórios de conteúdo;
	- ambiente de desenvolvimento;
	- diretórios iniciais do usuário;

![[Pasted image 20231211160546.png]]

##### Armazenamento de blocos

- **divide os arquivos em pedaços de dados de tamanho fixo** chamados blocos que **têm seus próprios endereços**;
- os blocos **podem ser recuperados de forma eficiente, pois cada bloco é endereçável**;
- quando os dados são solicitados, os endereços são usados pelo sistema de armazenamento para organizar os blocos na ordem correta para formar um arquivo completo para apresentar de volta ao solicitante;
- fora do endereço, nenhum metadado adicional está associado a cada bloco;
- quando quiser alterar um caractere em um arquivo, basta alterar o bloco que contém o caractere;
- essa facilidade de acesso é o motivo pelo qual as soluções de armazenamento em bloco **são rápidas** e **usam menos largura de banda**;
- é otimizado para operações de baixa latência;
- é uma **opção de armazenamento típica para workloads corporativos de alta performance**, como banco de dados ou sistemas de planejamento de recursos empresariais (ERP);

![[Pasted image 20231211161654.png]]

##### Armazenamento de objeto

- são tratados como uma única unidade de dados quando armazenados;
- esses objetos são armazenados em um estrutura plana em vez de uma hierarquia;
- cada objeto **é um arquivo com um identificador exclusivo**;
- esse identificador, juntamente com quaisquer metadados adicionais, é empacotado com os dados e armazenado;
- quando quiser alterar um caractere em um arquivo, todo o arquivo deve ser atualizado;
- **pode armazenar qualquer tipo de dados** e **não há limite para o número de objetos armazenados**, o que o torna **facilmente escalável**;
- geralmente é útil ao armazenar grandes conjuntos de dados, arquivos não estruturados, como ativos de mídia, e ativos estáticos, como fotos;

![[Pasted image 20231211162303.png]]

##### Relacionar de volta aos sistemas de armazenamento tradicionais

- o armazenamento em bloco na nuvem é análogo ao **direct-attached storage (DAS)** ou a uma rede de **storage area network (SAN)**;
- os sistemas de armazenamento de arquivos, geralmente, são suportados com um servidor de **network attached storage (NAS)**;
- adicionar armazenamento em um datacenter tradicional é um processo rígido:
	- as soluções de armazenamento devem ser compradas, instaladas e configuradas;
- com a computação em nuvem o processo é mais flexível:
	- você pode criar, excluir e modificar soluções de armazenamento em questões de minutos;