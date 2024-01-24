
![[Pasted image 20231226122155.png]]

##### ACLs de rede

- é um firewall virtual que controla o tráfego de entrada e saída no *nível de sub-rede*;
- *permite todo o tráfego de entrada e saída*, por padrão;

###### Filtragem de pacotes stateless

- ACLs de rede executam a filtragem de pacotes stateless;
- *não se lembram de nada* e verificam os pacotes que atravessam a fronteira da sub-rede em *todos os sentidos: entrada e saída*;

![[Pasted image 20231226121802.png]]

##### Grupos de segurança

- um firewall virtual que controla o tráfego de entrada e saída de uma *instância EC2*;
- *nega todo o tráfego de entrada e permite todo o tráfego de saída*, por padrão;

###### Filtragem de pacotes stateful

- grupos de segurança fazem a filtragem de pacotes stateful;
- *eles se lembram* de decisões anteriores tomadas para *pacotes recebidos*;

![[Pasted image 20231226122140.png]]