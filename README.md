# Projeto: Infraestrutura Web com Monitoramento na AWS

## Objetivo

Este projeto tem como finalidade a criação de uma infraestrutura em nuvem utilizando a AWS. O ambiente foi configurado para hospedar uma aplicação web simples e realizar o monitoramento automatizado da sua disponibilidade. O objetivo é garantir que o serviço esteja disponível continuamente e que falhas sejam detectadas e notificadas.

## Etapas do Projeto

### 1. Configuração da Infraestrutura de Rede (VPC)

- Criação de uma VPC personalizada 
- Criação de:
  - Duas sub-redes públicas 
  - Duas sub-redes privadas
- Criação e associação de um Internet Gateway para permitir acesso à internet nas sub-redes públicas.
- Criação de um NAT Gateway em uma zona de disponibilidade, permitindo que as sub-redes privadas tenham acesso à internet de forma segura.

### 2. Instância EC2

- Lançamento de uma instância EC2 do tipo `t2.micro`.
- Utilização da AMI Ubuntu Server 24.04 LTS.
- Associação da instância à sub-rede pública com atribuição de IP público.
- Configuração de um grupo de segurança com as seguintes regras:
  - Porta 22 (SSH) liberada para acesso remoto.
  - Porta 80 (HTTP) liberada para o servidor web.
- Geração e uso de par de chaves SSH (`XXX.pem`) para autenticação e acesso via terminal.
- Acesso realizado tanto pelo PowerShell local quanto pelo recurso "Conectar" do console da AWS.

### 3. Servidor Web com Nginx

- Instalação do servidor web Nginx por meio do gerenciador de pacotes `apt`.
- Criação de uma página HTML simples no diretório `/var/www/html/index.html`.
- Configuração padrão do Nginx utilizada para exibir a página HTML.
- Testes realizados utilizando o IP público da instância EC2.

### 4. Monitoramento com Script Bash

- Desenvolvimento de um script de monitoramento que:
  - Realiza requisições HTTP para verificar a disponibilidade do site.
  - Registra os resultados em um arquivo de log localizado em `/var/log/monitoramento.log`.
  - Envia notificações para um canal do Discord utilizando webhook, quando a aplicação estiver indisponível.
    
### 5. Automação com Crontab

- O script foi adicionado ao agendador de tarefas do Linux (crontab), com execução a cada 1 minuto.
- O cron é responsável por garantir que o monitoramento ocorra de forma contínua.
- O comportamento foi validado ao interromper o serviço Nginx manualmente e observar os registros de log e alertas.

