# Backup_automatizado
Este projeto foi criado para automatizar backup, direcionar os snapshots para camadas de armazenamentos mais baratos. 

#Descrição do projeto
- Criei uma instancia EC2 para que pudesse ter um cenário real e utilizar EBS para criar o plano de Backup 
- Esse projeto foi criado para automatizar a criação de backup de volumes EBS, RDS e podendo utlizar em outros recursos
- Utilizei o AWS Backup para ter um ambiente centralizado e aonde posso ter total visualização e controle dos meus backups
- Utilizei o EventBridge para desacoplar recursos e utiliza-lo para que ele fosse intermediador entre recursos
- Implementei o SNS para que eu pudesse recerber notificações de inicializações da criação dos Backups

  ###Arquitetura do projeto
  

