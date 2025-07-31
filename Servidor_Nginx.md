# Configuração de Servidor EC2 com Nginx e Monitoramento via Discord

## 1. Conectar na instância EC2
- Acesse sua instância EC2 pelo botão **"Conectar"** no console da AWS.

## 2. Atualizar o sistema
```bash
sudo apt update && sudo apt upgrade -y
```

## 3. Instalar o Nginx
```bash
sudo apt install nginx -y
```

## 4. Iniciar e habilitar o Nginx
```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

## 5. Criar a página HTML
```bash
sudo nano /var/www/html/index.html
```
Adicione seu conteúdo HTML personalizado.

## 6. Testar no navegador
Acesse:
```
http://SEU_IP_PUBLICO
```

## 7. Criar o script de monitoramento
```bash
sudo nano /usr/local/bin/monitoramento.sh
```
Cole seu script de monitoramento personalizado (com verificação do Nginx e envio para o Discord).

## 8. Dar permissão de execução ao script
```bash
sudo chmod +x /usr/local/bin/monitoramento.sh
```

## 9. Criar o arquivo de log
```bash
sudo touch /var/log/monitoramento.log
sudo chmod 666 /var/log/monitoramento.log
```

## 10. Agendar o script com cron
```bash
crontab -e
```
Adicione ao final do arquivo:
```
* * * * * /usr/local/bin/monitoramento.sh
```
Salve com `Ctrl + O` e saia com `Ctrl + X`.

## 11. Testar o monitoramento
```bash
sudo systemctl stop nginx
```
- Aguarde 1 minuto.
- Verifique `/var/log/monitoramento.log`.
- Confirme o recebimento da notificação no Discord.

## 12. Reiniciar o Nginx
```bash
sudo systemctl start nginx
```
