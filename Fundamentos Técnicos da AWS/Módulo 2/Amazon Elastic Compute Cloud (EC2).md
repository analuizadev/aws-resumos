
![[Pasted image 20231204211059.png]]

![[Pasted image 20231201160241.png]]

- é um serviço Web que disponibiliza capacidade computacional segura e redimensionável na nuvem;
- permite provisionar servidores virtuais chamados instâncias do EC2;
- não está limitado a executar apenas servidores Web em suas instâncias do EC2;
- é possível criar e gerenciar instâncias por meio do Console de Gerenciamento da AWS, da CLI, dos SDKs, das ferramentas de automação e dos serviços de orquestração de infraestrutura;

![[Pasted image 20231211210947.png]]

para criar uma **instância** do EC2, deve definir:
1. especificações de hardware, como CPU, memória, rede e armazenamento;
2. configurações lógicas, como localização de rede, regras de firewall, autenticação e sistema operacional de sua escolha;

![[Pasted image 20231204165138.png]]

ao executar uma instância do EC2,a primeira configuração definida é qual sistema operacional você deseja selecionando uma imagem de máquina da Amazon (AMI);

##### Tipos de instância

![[Pasted image 20231211212441.png]]

- large tamanho do poder computacional - denominação de instâncias;

![[Pasted image 20231201160518.png]]

![[Pasted image 20231201160458.png]]

![[Pasted image 20231213183819.png]]
##### Imagem de Máquina da Amazon (AMI)
- AMI é uma imagem de iso;
- na Nuvem AWS a instalação do SO não é de sua responsabilidade;
- o sistema operacional está incorporado à AMI que você escolhe;
- ao usar uma AMI, é possível selecionar o mapeamentos de armazenamento, o tipo de arquitetura (como ARM de 32 bits, 64 bits) e software adicional instalado;

![[Pasted image 20231211211358.png]]

![[Pasted image 20231211211539.png]]

##### Relação entre AMIs e instâncias do EC2
- as instâncias do EC2 são instanciações ao vivo do que é definido em uma AMI;
	- analogia: assim como um bolo é uma instanciação ao vivo de uma receita de bolo;
- a AMI é como você modela e define sua instância, enquanto a instância do EC2 é a entidade com a qual você interage, o local em que é possível instalar seu servidor Web e veicular seu conteúdo aos usuários;
<br />
- quando executa uma nova instância a AWS aloca uma máquina virtual que é executada em um hipervisor;
- a AMI selecionada é copiada para o volume raiz, que contém a imagem usada para inicializar o volume;
- no final, obtém um servidor no qual pode se conectar e instalar pacotes e software adicional;
<br />
- vantagem de usar AMIs, são reutilizáveis;
- é possível criar uma AMI da instância em execução e usar a AMI para iniciar uma nova instância, a nova instância teria as mesmas configurações da atual;

==o tamanho da instância determina quanta capacidade ela tem e o tipo determina a combinação desses recursos==



##### Encontre AMIs
- AMIs de início rápido, são criadas pela AWS para ajudar você a começar rapidamente;
- AMIs do AWS Marketplace, fornecem software comercial e de código aberto conceituados de fornecedores terceiros;
- Minhas AMIs, são criadas por meio de suas instâncias do EC2;
- AMIs da comunidade fornecidas pela comunidade de usuários da AWS;
- Crie suas própria imagem personalizada com o EC2 Image Builder;

==cada AMI no Console de Gerenciamento da AWS tem um ID de AMI, que é prefixadao por "ami-", seguido por um hash aleatório de números e letras. Os IDs são exclusivos para cada região da AWS;==

##### Configurações de rede
![[Pasted image 20231213183919.png]]

##### Função de IAM
![[Pasted image 20231213184046.png]]

##### Script de dados do usuário

![[Pasted image 20231213184144.png]]

##### Especificar armazenamento

![[Pasted image 20231213184228.png]]

![[Pasted image 20231213184447.png]]

![[Pasted image 20231213184528.png]]

##### Bastion Hosts

- oferecem acesso seguro a instâncias do Linux localizadas em sub-redes privadas e públicas de uma VPC;