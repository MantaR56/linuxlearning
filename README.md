# Настройка сервера Linux
## Добавление пользователей
```bash
sudo adduser 'username'  
```  
### Добавить в группу sudo  
```bash
sudo usermod -aG sudo 'username'
```  
### Проверка групп пользователя  
```bash
groups 'username'  
```  
## Настройка SSH по ключам  
```bash
ssh-keygen -t ed25519  
cat ~/.ssh/id_ed25519.pub  
```  
### Установка публичного ключа на сервере  
```bash
mkdir -p ~/.ssh  
echo "ssh-ed25519 AAAAC3... " >> ~/.ssh/authorized_keys  
chmod 600 ~/.ssh/authorized_keys  
```
## Настройка SSH-сервера для подключения  
```bash
sudo nano /etc/ssh/sshd_config  
  -PermitRootLogin no  
  -PasswordAuthentication no  
  -PubkeyAuthentication yes
```
## Настройка ufw
### Сначала разрешение ssh, чтобы не закрыть себе доступ к серверу
```bash
sudo ufw allow ssh
```
### Главное правило - запретить всё входящее, разрешить всё исходящее
```bash
sudo ufw default deny incoming  
sudo ufw default allow outgoing
```
### Открытие нужных портов 
```bash
sudo ufw allow port/tcp
```
### Включение фаервола и проверка статуса
```bash
sudo ufw enable  
sudo ufw enable verbose  
```
### Полезные команды  
| Задача                                  | Команда                                                 |
| --------------------------------------- | ------------------------------------------------------- |
| Посмотреть правила с нумерацией	        | sudo ufw status numbered                                |
| Удалить правило по номеру (например, 3)	| sudo ufw delete 3                                       |
| Заблокировать порт 25 (почта, спам)	    | sudo ufw deny 25/tcp                                    |
| Запретить IP (заблокировать бота)	      | sudo ufw deny from 1.2.3.4                              |
| Защита от брутфорса SSH (limit)	        | sudo ufw limit ssh (автоматически банит частые попытки) |
| Выключить фаервол (временно)	          | sudo ufw disable                                        |
