
##### Armazenamento de instâncias

- os volumes de armazenamento a *nível de bloco* se comportam como *discos rígidos físicos*;
- é um meio *temporário* de armazenamento a nível de bloco para uma instância do EC2;
- é o armazenamento em disco *fisicamente anexo ao computador host* para uma instância do EC2;
- tem a mesma vida útil da instância, se a instância for terminada, perderá todos os dados armazenados nela;

##### Amazon Elastic Block Store (EBS)

- um serviço que fornece *volumes de armazenamento* a nível de bloco que pode ser usado com instâncias do EC2;
- todos os dados no volume do EBS *permanecem disponíveis*, após terminar uma instância;
- são para dados que precisam *durar*;

###### Snapshots do Amazon EBS

- é um backup incremental;
- o primeiro backup copia todos os dados, os próximos backups copiam somente os blocos de dados que foram alterados;

![[Pasted image 20231226154140.png]]