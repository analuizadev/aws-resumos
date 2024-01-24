
- é uma coleção de dispositivos físicos para *transporte físico* de até *exabytes* de dados para *dentro* e para *fora da AWS*;
- a AWS Snow Family consiste nos serviços AWS Snowcone, AWS Snowball e AWS Snowmobile;
- esses dispositivos oferecem diferentes pontos de capacidade e a maioria inclui recursos de computação integrados;
- a AWS é *proprietária* e *responsável* pelo gerenciamento da Snow Family;
	- que integra recursos de segurança, monitoramento, gerenciamento de armazenamento e computação da AWS;

![[Pasted image 20240103173002.png]]

##### AWS Snowcone

- um dispositivo pequeno, robusto e seguro para *transferência de dados* e *computação de borda*;
	- opções de computação de borda : instâncias do Amazon EC2 e AWS IoT (internet das coisas) Greengrass;
- ele tem *2 CPUs*, *4GB de memória* e até *14TB de armazenamento utilizável*;
- para receber um, você solicita pelo console de gerenciamento da AWS;
	- após receber os dispositivos, você o conecta e copia os dados e o envia de volta para a AWS;
	- em seguida, ela copia os dados para sua conta AWS, geralmente um bucket do Amazon S3, e os dados são disponibilizados para o uso;
- os clientes usam este dispositivo para enviar terabytes de informações, como :
	- dados de analytics;
	- bibliotecas de vídeo;
	- coleções de  imagens;
	- backups;
	- dados de substituição de fita;

##### AWS Snowball

- oferece dois tipos de dispositivos :
	- **Snowball Edge Storage Optimized :**
		- ideias para migrações de dados de *grande escala* e fluxos de trabalho de *transferência recorrentes*, em além da computação local com necessidades *maiores de capacidade*;
		- **armazenamento :** *80TB* de capacidade de disco rígido (HDD) para volumes de blocos e armazenamento de objetos compatível com o Amazon S3, além de unidade de estado sólido (SSD) do SATA de *1TB para volumes de blocos*;
		- **computação :** *40 vCPUs* (CPU virtual) e *80GB* de memória para dar suporte a instâncias sbe1 (Snowball Edge) do Amazon EC2 (equivalente a C5);
	- **Snowball Edge Compute Optimized :**
		- fornece *recursos de computação* poderosos para casos de uso, como machine learning, análise de vídeo em movimento completo, análise e pilhas de computação locais;
		- **armazenamento :** capacidade de HDD utilizável de *80TB* para armazenamento de objeto compatível com o Amazon S3 ou volumes de blocos compatível com o Amazon EBS e também *28TB* de capacidade de SSD NVMe utilizável para volumes de blocos compatíveis com o Amazon EBS;
		- **computação :** *104 vCPUs*, *416 GiB* de memória e uma GPU NVIDIA Tesla V100 opcional. Os dispositivos executam as instâncias sbe-c e sbe-g do Amazon EC2, que são equivalentes às instâncias C5, M5a, G3 e P3;

##### AWS Snowmobile

- um serviço de transferência de dados na escala de *exabytes* usado para mover *grande quantidades de dados para a nuvem AWS*;
- pode transferir até *100 petabytes* de dados por Snowmobile, um contêiner de transporte reforçado com 13,71 metros de comprimento puxado por um caminhão semirreboque;