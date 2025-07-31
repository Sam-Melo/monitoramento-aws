# Configuração de Servidor EC2 com Nginx e Monitoramento via Discord

## 1. Conectar na instância EC2

- Acesse a instância EC2 usando o botão **"Conectar"** no console da AWS.
- O terminal será aberto no navegador automaticamente.

---

## 2. Atualizar o sistema

- Execute:
  - `sudo apt update && sudo apt upgrade -y`

---

## 3. Instalar o Nginx

- Execute:
  - `sudo apt install nginx -y`

---

## 4. Iniciar e habilitar o Nginx

- Execute:
  - `sudo systemctl start nginx`
  - `sudo systemctl enable nginx`

---

## 5. Criar a página HTML

- Execute:
  - `sudo nano /var/www/html/index.html`
