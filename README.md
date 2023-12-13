
# Final Project OS-Server (22.83.0907)

Repository ini berisikan dokumentasi yang menjelaskan tahapan dalam instalasi dan juga konfigurasi salah satu layanan server, yakni Web Server dan menambahkan pemonitoring di dalamnya. 

## Daftar Isi

 - [Instalasi dan Konfigurasi SSH]([https://awesomeopensource.com/project/elangosundar/awesome-README-templates](https://github.com/mochralf/UAS-OS-SEVER-0907-/blob/master/README.md#instalasi-dan-konfigurasi-web-server))
 - [Instalasi dan Konfigurasi Web Server](https://github.com/matiassingers/awesome-readme)
 - [Instalasi dan Konfigurasi Monitoring Server](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

 
## Instalasi dan Konfigurasi Web Server

Install Apache

```bash
  sudo apt update 
  sudo apt install apache2

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
```
