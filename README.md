
# Web Server (Apache)

Berikut adalah langkah-langkah penginstalan Apache (web seerver) dan juga konfigurau yang akan dilakukan

## Installation

Install Apache

```bash
  sudo apt update -y
  sudo apt install apacMhe2
```
Penyesuaian Firewall
```bash
  sudo ufw app list
  sudo ufw allow 'Apache'
```
Memverifikasi perubahan dengan memeriksa status
```bash
  sudo ufw status
```
Mengecek service Apache apakah sudah siap digunakan
```bash
  sudo systemctl status apache2
## Demo

Insert gif or link to demo


## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

