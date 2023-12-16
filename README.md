[# Final Project OS-Server (22.83.0907)

Repository ini berisikan dokumentasi yang menjelaskan tahapan dalam instalasi dan juga konfigurasi Web Server dengan menambahkan Software Opensource sebagai pemonitoringnya. 

## Daftar Isi

 - [Instalasi dan Konfigurasi SSH](https://github.com/mochralf/UAS-OS-SEVER-0907-/blob/master/README.md#instalasi-dan-konfigurasi-ssh)
 - [Instalasi dan Konfigurasi Web Server](https://github.com/mochralf/UAS-OS-SEVER-0907-/blob/master/README.md#instalasi-dan-konfigurasi-web-server)
 - [Instalasi dan Konfigurasi Monitoring Server](https://github.com/mochralf/UAS-OS-SEVER-0907-/blob/master/README.md#instalasi-dan-konfigurasi-monitoring-server)

## Instalasi dan Konfigurasi SSH

Perbarui Paket data untuk peningkatan versi yang diperlukan
```bash
  sudo apt update
  sudo apt upgrade
```

Lakukan instalasi Paket SSH Server : 
```bash
  sudo apt install openssh-server
```
Penyesuaian Firewall, Aoakah firewall telah diaktifkan
```bash
  sudo ufw status
  sudo ufw allow 'Apache'
```
Memverifikasi perubahan dengan memeriksa status
```bash
  sudo ufw status
```
Mengecek service Apache apakah sudah siap digunakan
```bash
  sudo systemctl status 
```

## Instalasi dan Konfigurasi Web Server

Instalasi dan Konfigurasi Web Server

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
](https://github.com/)https://github.com/
