
- conceito de redes de entrega de conteúdo (CDN);
- na AWS CDN é chamada de Amazon CloudFront;
- locais de borda executam o Amazon CloudFront para aproximar o conteúdo dos clientes, globalmente;

##### Amazon CloudFront

- um serviço de entrega de dados, vídeos, aplicações e EPIs a clientes em **todo o mundo**;
- baixa latência e altas velocidades de transferência;
- usa os locais de borda em todo o mundo para **acelerar** a comunicação com os usuários;
- é possível mover o conteúdo de uma região para diversos locais de borda do mundo;

##### Locais de borda

- é um **site** que o Amazon CloudFront usa para **armazenar cópias em cache** do conteúdo mais próximo dos clientes para uma entrega **mais rápida**;
- executam um serviço de nome de domínio ou DNS, o Amazon Route 53;
	- direciona os clientes para os locais corretos da web com baixa latência constante;

##### Amazon Outposts

- executa infraestrutura em uma abordagem de nuvem híbrida;
- uma região reduzida totalmente operacional **dentro do datacenter da empresa**;
- essa região pertence à AWS, é operada por ela e usa 100% da funcionalidade da AWS, mas fica **isolada** dentro do **prédio** da empresa;