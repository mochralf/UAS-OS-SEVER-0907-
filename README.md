# Final Project OS-Server (22.83.0907)

Repositori ini berisikan dokumentasi yang menjelaskan tahapan dalam instalasi dan juga konfigurasi Web Server dengan menambahkan Software Opensource sebagai pemonitoringnya. 

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

Lakukan instalasi Paket SSH Server 
```bash
  sudo apt install openssh-server
```

Buka file konfigurasi SSH menggunakan teks editor yang diinginkan
```bash
  nano /etc/ssh/sshd.config 
  #(remove # on line port 22)
```

Penyesuaian Firewall, Apakah firewall telah diaktifkan, apabila belum maka diaktifkan (allow)
```bash
  sudo ufw status
  sudo ufw allow 22/tcp
```

Memverifikasi perubahan dengan memeriksa status firewall apakah sudah aktif atau belum
```bash
  sudo ufw status
```

Mengecek service Apache apakah sudah siap digunakan
```bash
  sudo systemctl status sshd
```

Buka Command Prompt (CMD) pada Windows untuk melakukan Test PING VM yang ingin di SSH terlebih dahulu 
```
  ping <IP VM yang ingin di SSH>
  #example : ping 192.168.20.20
```

Lakukan SSH pada Command Prompt (CMD) Windows
```bash
  ssh <username>@IP VM yang ingin di ssh / ssh -p <port ssh> root@IP VM ysng ingin di SSH
  #example : ssh riplabs@192.168.20.20 / ssh -p 22 root@192.168.20.20
```

## Instalasi dan Konfigurasi Web Server

Perbarui Paket data untuk peningkatan versi yang diperlukan dan dilanjut dengan penginstalan Web Server (Apache)
```bash
  sudo apt update 
  sudo apt install apache2

```

Penyesuaian Firewall dengan mengizinkan package Apache
```bash
  sudo ufw app list
  sudo ufw allow 'Apache'
```

Memverifikasi perubahan dengan memeriksa status
```bash
  sudo ufw status
```

Mengecek service Apache apakah sudah berjalan dan siap digunakan
```bash
  sudo systemctl status apache2
```

Apabila service sudah siap digunakan maka cek lah IP yang digunakan untuk mengakses Apache atau Default page apache pada Web Browser
```bash
  hostname -I
  #Output IP tersebut digunakan untuk mengakses Default page Apache
```

**Memodifikasi atau membuat Host Vitual baru dengan domain yang diinginkan (disini saya beri nama : riplabs)**

Membuat virtual baru didalam direktori /var/www/<nama domain>
``` bash
  sudo mkdir /var/www/riplabs
```

Ubah kepemilikan (Owbership) direktori /var/www/riplabs yang baru saja kita buat
```bash
  sudo chown -R $USER:$USER /var/www/riplabs
```

Atur hak akses menjadi chmod 755 agar semua user mendapatkan hak akses untuk mengeksekusi file atau direktori tersebut
```bash
  sudo chnod -R 755 /var/www/riplabs
```

Masuk dan buatlah satu contoh File html dan tambahkan keperluan lainnya sesuai dengan kebutuhan pada direktori /var/www/riplabs
```bash
  sudo nano /var/www/riplabs/index.html
  #masukkan contoh html sesaui kebutuhan anda
```

Tambahkan konfigurasi Apache agar ketika user mengakses IP VM tidak lagi menuju ke default page Apache, namun mengarah ke Virtual host dengan domain yang baru saja kita buat
```bash
  sudo nano /etc/apache2/sites-available/riplabs.config
  #ubahlah menjadi :
  <VirtualHost *:80>
    		ServerAdmin webmaster@localhost
    		ServerName your_domain
    		ServerAlias www.your_domain
    		DocumentRoot /var/www/your_domain
    		ErrorLog ${APACHE_LOG_DIR}/error.log
    		CustomLog ${APACHE_LOG_DIR}/access.log combined
	</VirtualHost>

  Simpan dan keluar dari teks editor
```

Aktifkan file Host virtual baru dengan alat a2ensite
```bash
  sudo a2ensite riplabs.conf
```

Nonaktifkan  situs default yang ditentukan di 000-default.conf
```bash
  sudo a2dissite 000-default.conf
```

Uji konfigurasi Apache barangkali terjadi kesalahan
```bash
  sudo apache2ctl configtest
  #Output
    . . .
    Syntax OK
```

Apabila tidak terjadi kesalahan, Restart service Apache untuk menerapkan perubahan yang ada 
```bash
  sudo systemctl restart apache2
```
