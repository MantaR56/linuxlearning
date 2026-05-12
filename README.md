# Настройка сервера Linux
## Добавление пользователей
**`sudo adduser 'username'`**  
  
### Добавить в группу sudo  
**`sudo usermod -aG sudo 'username'`**  
  
### Проверка групп пользователя  
groups 'username'  
  
## Настройка SSH по ключам  
**`ssh-keygen -t ed25519  
cat ~/.ssh/id_ed25519.pub`**  
  
### Установка публичного ключа на сервере  
**`mkdir -p ~/.ssh  
echo "ssh-ed25519 AAAAC3... " >> ~/.ssh/authorized_keys  
chmod 600 ~/.ssh/authorized_keys`**  
  
## Настройка SSH-сервера для подключения  
**`sudo nano /etc/ssh/sshd_config`**  
  -PermitRootLogin no  
  -PasswordAuthentication no  
  -PubkeyAuthentication yes
