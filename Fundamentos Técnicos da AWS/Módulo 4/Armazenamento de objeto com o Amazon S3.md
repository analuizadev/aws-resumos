- os dados são *armazenados como objetos em buckets*;
- armazenamento praticamente ilimitado
	- um único objeto pode ter até *5TB*;
	- *11 noves* significa que a *durabilidade de um arquivo no S3* é de 99,999999%;
	- acesso granular a buckets e objetos (controlar o acesso);
- pode armazenar virtualmente quantos objetos desejar;
- *os dados são privados* e tem opção de criptografá-los;
- os dados são armazenados de forma redundante (faz cópias para caso ocorra algum acidente);
- é possível recuperar dados a qualquer momento e em qualquer lugar pela internet;
- *os nomes de buckets devem ser exclusivos* entre todos os nomes de buckets existentes no Amazon S3;
- paga somente pelo o que usar;
- é possível acessar o Amazon S3 a qualquer momento e em qualquer lugar por meio de um URL;

![[Pasted image 20231211192431.png]]

![[Pasted image 20231211194632.png]]
##### Amazon S3 Standard

- projetado para oferecer armazenamento de objetos de **alta durabilidade, alta disponibilidade e de alto desempenho** para dados acessados com frequência;
- fornece **baixa latência** e **alta taxa de transferência**;
- é adequado para muitos casos de uso, como aplicativos na nuvem, sites dinâmicos, distribuição de conteúdo, aplicativos móveis e de jogos e análise de big data;

##### Amazon S3 Intelligent-Tiering

- projetada para **otimizar os custos**, movendo **automaticamente** os dados para o nível de acesso mais econômico, **sem impacto no desempenho**, **nem despesas operacionais gerais**;
- monitora os padrões de acesso dos objetos no Amazon S3 Intelligent-Tiering e move os objetos que não foram acessados por **30 dias consecutivos** para o nível de acesso infrequente, por uma pequena **taxa mensal** de automação e monitoramento por objeto;
- se um objeto no nível de acesso infrequente for acessado, ele será automaticamente movido de volta para o nível de acesso frequente;
- **não cobra taxa de recuperação** quando você a usa e **não cobra taxas adicionais** quando os objetos são movidos entre níveis de acesso;
- funciona bem para **dados de longa duração** com padrões de acesso desconhecidos ou imprevisíveis;

##### Amazon S3 Standard-Infrequent Access (Standard-IA)

- altamente disponível;
- é usada para **dados acessados com menos frequência**, mas que **exigem acesso rápido** quando necessário;
- foi criada para oferecer a alta durabilidade, a alta taxa de transferência e a baixa latência das categorias Amazon S3 Standard, com **taxas reduzidas por GB de armazenamento e GB de recuperação**;
- combinação de **custo baixo** e **alto desempenho**;
- ideal para armazenamento e backups de longo prazo e como um data-store para arquivos de recuperação de desastres (DR);

##### Amazon S3 One Zona-Infrequent Access (One Zone-IA)

- projetado para **dados acessados com menos frequência**, mas que **exigem acesso rápido** quando necessário;
- outras classes de armazenamento do Amazon S3, armazenam os dados no mínimo em **três Zonas de Disponibilidade**, o One Zone-IA armazena dados em **uma única Zona de Disponibilidade**
- custa menos que o Standard-IA;
- ideal para clientes que querem uma opção de custo mais baixo para dados acessados com menos frequência, mas que **não exigem** disponibilidade e a resiliência do Amazon S3 Standard ou Standard-IA;
- ótima opção para armazenar cópias de backup secundárias de dados no local ou dados que possam ser recriados com facilidade;
- é possível usar, também, como um armazenamento econômico para dados replicados de outra Região da AWS usando a replicação entre Regiões do Amazon S3;

##### Amazon Simple Storage Service Glacier (S3 Glacier)

- segura, durável e de custo baixo para arquivamento de dados;
- é possível armazenar com confiança **qualquer volume dados** por um custo competitivo ou inferior ao de soluções locais;
- para manter os custos baixos, mas com condições de suprir necessidades variáveis, o Glacier disponibilidade **três opções de recuperação**;
- podem demorar de alguns minutos a várias horas para recuperar;
- é possível fazer upload de objetos diretamente para o Amazon S3 Glacier;
- é possível usar as políticas do Ciclo de vida do Amazon S3 para transferir dados entre qualquer uma das classes de armazenamento do Amazon S3 para dados ativos;

##### Amazon S3 Glacier Deep Archive

- classe de armazenamento de **menor custo**;
- oferece retenção de longo prazo e preservação digital para dados que podem ser **acessados uma ou duas vezes por ano**;
- projetado para clientes em setores altamente regulamentados, como serviços financeiros, saúde e setores públicos, que retêm conjuntos de dados por sete a dez anos (ou mais) para atender à conformidade regulatória;
- pode ser usado para casos de uso de backup e recuperação de desastres;
- alternativa **econômica** e **fácil de gerenciar** para sistemas de fita magnética, quer esses sistemas de fita sejam bibliotecas locais ou serviços externos;
- Glacier Deep Archive completa o Amazon S3 Glacier;
- foi projetado para fornecer uma **durabilidade de 11 noves**;
- todos os objetos armazenados são **replicados** e armazenados em, pelo menos, **três zonas de disponibilidade** distribuídas geograficamente;
- esses objetos podem ser **restaurados em até 12 horas**;

##### Acesso de dados

![[Pasted image 20231213180930.png]]

- possível acessar o Amazon S3 por meio do console de gerenciamento da AWS, da AWS CLI e da AWS SDKs;
- é possível acessar os dados no bucket diretamente, usando endpoints baseados em REST, que são compatíveis com o acesso por HTTP ou HTTPS;

##### Estrutura da URL do objeto e do bucket do Amazon S3

![[Pasted image 20231211200046.png]]

- Amazon S3 refere-se a arquivos como objeto;
- um objeto é composto de dados e quaisquer metadados que descrevam esse arquivo;
- a propriedade que identifica um objeto é a **chave**;

##### Redundância no Amazon S3

![[Pasted image 20231213181819.png]]

- o bucket ao ser criado é associado a uma Região da AWS específica;
- os dados são sempre armazenados de forma redundante, ou seja, em várias instalações da AWS na Região selecionada;

##### Scaling ininterrupta

![[Pasted image 20231213182125.png]]

- Amazon S3 gerencia automaticamente o armazenamento por trás do bucket mesmo quando a quantidade de dados aumenta;
- você tem o armazenamento de dados aumentado de acordo com as necessidades do aplicativo;
- Amazon S3 se dimensiona para lidar com um alto volume de solicitações;


##### Casos comuns de uso

![[Pasted image 20231211201350.png]]

##### Preços

![[Pasted image 20231213182526.png]]

![[Pasted image 20231211203816.png]]