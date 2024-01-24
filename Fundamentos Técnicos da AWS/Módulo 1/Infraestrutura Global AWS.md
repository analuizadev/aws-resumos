
a infraestrutura, como datacenters e conectividade de rede, ainda existe como a base de cada aplicação em nuvem. Na AWS, essa infraestrutura física compõe a infraestrutura global da AWS, na forma de regiões e zonas de disponibilidade;

- **a infraestrutura global da AWS foi projetada e criada para fornecer ESCALABILIDADE**

* ==regiões são clusters de zonas de disponibilidade. As zonas de disponibilidade são clusters de datacenters==

#### Regiões

> são locais geográficos em todo o mundo em que a AWS hospeda seus datacenters; 
> 
> as regiões da AWS têm o nome do local em que elas residem, por exemplo, nos Estados Unidos, a Região do Norte da Virgínia é chamada de Região do Norte da Virgínia;
>
> a AWS tem regiões na Ásia-Pacífico, Canadá, Europa, Oriente Médio e América do Sul;
>
> cada região da AWS está associada a um nome geográfico e a um código de região.

![84.png](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1701194400/r4kXSUuVcYUJImjx1pHqGg/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/Xzum07jFs4uhDBvc_UB1vzpgv31Y9lgIX.jpg)

* **us-east-1 :** a primeira região criada na área leste dos EUA; O nome desta região é o Norte da Virgínia;
* **ap-northeast-1 :** a primeira região criada na região nordeste da Ásia-Pacífico. O nome geográfico desta região é Tóquio;

==as regiões da AWS não dependem umas das outras; os dados não são replicados de uma Região para outra, sem consentimento e autorização explícitos do cliente==

##### Escolha a região certa da AWS

quando decidir qual região da AWS hospedar suas aplicações e workloads, considere quatro aspectos principais: latência, preço, disponibilidade do serviço e conformidade;

###### Latência
> se a aplicação for sensível à latência (o atraso entre uma solicitação de dados e a resposta), escolha uma Região próxima à sua base de usuários; ajuda a evitar longos tempos de espera para seus clientes;
> 
> aplicações síncronas, como jogos, telefonia, WebSockets e internet das Coisas (IoT), são significativamente afetadas pela alta latência;
> 
> Workloads assíncronas, como aplicações de comércio eletrônico, também podem sofrer atrasos na conectividade do usuário;

###### Preços
> devido à economia local e à natureza física dos datacenters operacionais, os preços variam de uma região para outra;
> 
> conectividade com a internet, custos de equipamentos importados, alfândega, imóveis e outros fatores afetam os preços de uma região;
> 
> em vez de cobrar uma taxa fixa em todo o mundo, a AWS cobra com base nos fatores financeiros específicos de cada região;

###### Disponibilidade de serviço
>alguns serviços podem não estar disponíveis em algumas regiões;
>
>a documentação da AWS fornece uma tabela que mostra os serviços disponíveis em cada região;

###### Conformidade de dados
>geralmente, as empresas corporativas precisam cumprir as regulamentações que exigem que os dados do cliente sejam armazenados em um território geográfico específico;
>
>se aplicável, escolha uma Região que atenda aos requisitos de conformidade;


#### Zonas de disponibilidade

>dentro de todas as regiões há um cluster de zonas de disponibilidade (AZs);
>
>uma Az consiste em um ou mais datacenters com energia, rede e conectividade redundantes;
>
>esses datacenters operam em instalações discretas em localizações não reveladas;
>
>eles são conectados usando links redundantes de alta velocidade e baixa latência;
>
>as AZs também têm um nome de código, como eles estão localizados dentro das Regiões, eles podem ser endereçados com o anexo de uma letra ao final do nome de código da Região;

* **us-east-1a :** uma AZ em us-east-1 (Região Norte da Virgínia);
* **sa-east-1b :** uma AZ em sa-east-1 (Região Norte de São Paulo);

==se você perceber que existe um recurso em us-east-1c, você pode inferir que o recurso está localizado em AZ c da região us-east-1==

![Image36.png](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1701194400/r4kXSUuVcYUJImjx1pHqGg/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/1EjU60kw_biSAfuG_4nau5Zp-mxB_YCxq.png)




#### Ponto de presença (PoPs)
>é uma infraestrutura de servidores, localizado próximo a uma AZ (zona de disponibilidade);


>armazena os dados mais solicitados em cache, para entregar uma menor latência a uma requisição de consulta;

#### Escopo dos produtos da AWS

dependendo do produto da AWS que você usa, seus recursos são implantados no nível de AZ, Região ou Global. Cada serviço é diferente, portanto, você deve entender como o escopo de um serviço pode afetar a arquitetura da aplicação;

quando você opera um serviço com escopo de região, você só precisa selecionar a Região que deseja usar. Se você não for solicitado a especificar uma AZ individual para implantar o serviço, esse é um indicador de que o serviço opera em um nível de escopo de região. Para serviços com escopo de região, a AWS executa automaticamente ações para aumentar a durabilidade e a disponibilidade dos dados.

por outro lado, alguns serviços pedem que você especifique uma AZ. Com esses serviços, você geralmente é responsável por aumentar a durabilidade dos dados e a alta disponibilidade desses recursos.

#### Manter a resiliência

para manter sua aplicação disponível, você deve manter alta disponibilidade e resiliência. Uma prática recomendada bem conhecida para a arquitetura de nuvem é usar serviços gerenciados com escopo da região. Esses serviços têm disponibilidade e resiliência incorporadas. Quando isso não for possível, verifique se sua workload está replicada em várias AZs. No mínimo, você deve usar duas AZs. Dessa forma, se uma AZ falhar, sua aplicação terá a infraestrutura em funcionamento em uma segunda AZ para assumir o tráfego.

![Image33.png](https://explore.skillbuilder.aws/files/a/w/aws_prod1_docebosaas_com/1701194400/r4kXSUuVcYUJImjx1pHqGg/tincan/954352_1676568571_p1gpdis23dphj1i0b12fk1vub1t4o4_zip/assets/8LuM5bDPPxjYO-mC_9hMPyZCzWVm0Z4l1.png)

![[Pasted image 20231128213503.png]]