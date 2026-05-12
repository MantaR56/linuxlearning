# Настройка сервера Linux
## Добавление пользователей
sudo adduser 'username'  
sudo usermod -aG sudo 'username'  
  
<!-- Проверка групп пользователя  -->
groups 'username'

## Настройка SSH по ключам
ssh-keygen -t ed25519 -C "your_email@gmail.com"
