# Backup_automatizado
Este projeto foi criado para automatizar backup, direcionar os snapshots para camadas de armazenamentos mais baratos. 

#Descrição do projeto
- Criei uma instancia EC2 para que pudesse ter um cenário real e utilizar EBS para criar o plano de Backup 
- Esse projeto foi criado para automatizar a criação de backup de volumes EBS, RDS e podendo utlizar em outros recursos
- Utilizei o AWS Backup para ter um ambiente centralizado e aonde posso ter total visualização e controle dos meus backups
- Utilizei o EventBridge para desacoplar recursos e utiliza-lo para que ele fosse intermediador entre recursos
- Implementei o SNS para que eu pudesse recerber notificações de inicializações da criação dos Backups

### Arquitetura do projeto
![diagrama.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/diagrama.png)


### Passo a Passo da criação

- Criei uma instância aonde irei utilizá-la para ter acesso ao EBS 

![server_test01(projeto backup).png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/server_test01(projeto%20backup).png)


- Criei um plano de backup onde ele será utilizado para criar, reter e enviar o backup para uma camada de armazenamento mais barata
- Criar um plano de backup reduz o trabalho manual e o gerenciamento, garantindo mais tempo para focar em outros serviços

### 1. Criando plano de backup

![Criação_ Backup_1.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/Cria%C3%A7%C3%A3o_%20Backup_1.png)


### 2. criação do plano de Backup

- Neste momento implementei armazenamento frio
- Habilitar o Armazenameneto Frio torna os backups mais baratos porque após o periodo de retenção no armazenamento quente, ele será armazenado em camadas mais baratas, que seria o S3 Glacier 


![Criação_Backup_2.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/Cria%C3%A7%C3%A3o_Backup_2.png)

- Escolhi o recurso e inseri o ID do recurso que iria ser implementado no Plano de Backup

![Recurso_Plano.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/Recurso_Plano.png)

- Meu próximo passo seria a criação de um tópico aonde as informações do backup(eventos) seriam direcionados
- Utilizei o SNS trazendo uma enorme facilidade em sua criação e direcionamento para onde o conteúdo seria enviado

![topico_sns.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/topico_sns.png)

- Para finalizar a criação, utilizei o EventBridge como um meio de intermediar esses recursos:Aws Backup e SNS
- Utilizado para cenários onde se tem uma arquitetura orientada para eventos, trazendo escalabilidade e eficiencia 

![EventBridge_Criação.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/EventBridge_Cria%C3%A7%C3%A3o.png)

- Utilizei o Padrão de "job State charge" para que ele faça o monitoramento de qualquer criação de Backup

### Criando um Backup manual

- Criei um backup manual para realizar um teste onde eu pudesse validar o fluxo de trabalho e o envio do e-mail corretamente 

![criando_backup_manual.png](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/criando_backup_manual.png)

- Não demorou muito tempo e recebi um e-mail informando o backup realizado
  
![Test_1.PNG](https://github.com/Jeff01875/Backup_automatizado/blob/ed6f9a6937414db5eb9a564f991ea81b07d45f88/Test_1.PNG)

- Peço desculpas pela imagem, não tive como acessar meu e-mail para conseguir captar a imagem pelo computador
- Acabei tendo que pegar essa captura pelo celular

### Benefícios desse Projeto
- Com o Aws Backup temos o benefício em ter um ambiente centralizado aonde podemos visualizar nossos planos de backup, automatizar essa tarefa, diminuindo a carga de trabalho manual
- Utilizar o EventBridge nos ajuda em desacoplar recursos e a integrações futuras 
- O SNS foi utilizado pois traz essa facilidade em enviar as notificações para e-mail e que pode ser integrado aos recusos de modo prático e fácil
- Esses recursos tornam a carga de trabalho mais eficiente e automatizada, permitindo que os colaboradores não se preocupem tanto em gerenciar os backup e os custos que eles trazem







  

