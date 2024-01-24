
- os registro de logs do CloudTrail podem ser *consultados* no Amazon Athena;
- registra as chamadas de API realizadas na sua conta entre as regiões;
- as informações gravadas são:
	- identidade do chamador da API;
	- hora da chamada da API;
	- endereço de IP de origem do chamador da API;
	- etc;
- pensar no CloudTrail como uma trilha ou um log de ações que alguém criou;
- eventos são atualizados no CloudTrail dentro de *15 minutos* após uma chamada de API;
- pode filtrar eventos especificando :
	- a hora e a data em que uma chamada de API ocorreu;
	- o usuário que solicitou a ação;
	- o tipo de recurso envolvido na chamada de API;
	- etc;
- o CloudTrail simplifica :
	- a governança;
	- a conformidade;
	- a auditoria de riscos;

---
**exemplo** 

um novo usuário do IAM chamado Mary foi criado, mas não sabe quem, quando ou qual método foi usado para criar o usuário;

para responder essas perguntas, o proprietário navega até o AWS CloudTrail;

![[Pasted image 20231228133037.png]]

na sessão histórico de eventos do CloudTrail, o proprietário aplica um filtro para exibir somente os eventos da ação da API "CreateUser" no IAM;

ele localiza o evento para a chamada de API que criou um usuário do IAM para Mary;

##### CloudTrail insights

- recurso opcional;
- permite que o CloudTrail detecte automaticamente atividades de API incomuns em sua conta AWS;

##### Práticas recomendadas

- ative a validação de arquivos de log do CloudTrail;
- agregue arquivos de log a *um único* bucket S3;
- certifique-se de que o CloudTrail esteja ativado globalmente na AWS;
- restrinja o acesso aos buckets do S3 do CloudTrail;
- integração com o Amazon CloudWatch;
