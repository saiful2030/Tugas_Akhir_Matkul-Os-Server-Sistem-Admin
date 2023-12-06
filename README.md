# Tugas Akhir Mata Kuliah
## OS SERVER & SISTEM ADMIN
- Nama : MUHAMMAD SAIFUL AJI
- Nim  : 22.83.0789



## WEB SERVER
Web server adalah perangkat lunak yang menyediakan layanan dalam bentuk data. Fungsi tersebut menerima permintaan HTTP atau HTTPS dari klien atau biasa kita sebut browser web  (Chrome, Firefox). Kemudian mengirimkan respons permintaan ke klien dalam bentuk halaman web.

## Resource

- [VirtualBox](https://www.virtualbox.org/)
- [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- [Nginx](https://www.nginx.com/)
- [Mysql](https://www.mysql.com/)
- [Php](https://www.php.net/)
- [Bind9](https://bind9.net/)
- [phpmyadmin](https://www.phpmyadmin.net/)
- [admin panel](https://github.com/yolanmees/Spikster)


## Update Perkembangan

- 28/09/2023 - Intalasi [Ubuntu Server 20](https://releases.ubuntu.com/focal/) di [VirtualBox](https://www.virtualbox.org/)
- 30/09/2023 - Instalasi [Nginx](https://www.nginx.com/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 01/10/2023 - Instalasi [Php](https://www.php.net/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 02/10/2023 - Instalasi [Mysql](https://www.mysql.com/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 03/10/2023 - Instalasi [Bind9](https://bind9.net/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 05/12/2023 - Instalasi [phpmyadmin](https://www.phpmyadmin.net/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 06/12/2023 - Instalasi [admin panel](https://github.com/yolanmees/Spikster) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)

## Install Nginx

Nginx tersedia di repositori asali Ubuntu, maka kita dimungkinkan untuk menginstalnya dari repositori ini menggunakan sistem pengemasan `apt`.

Langkah 1 : Update Ubuntu Server

```sh
sudo apt update
```
Langkah 2 : Install Nginx

```sh
sudo apt install nginx
```
Langkah 3 : Setting Firewall

```sh
sudo ufw app list
```
Akan mendapat daftar profil aplikasi:
```sh
Output
Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
```
Disarankan untuk mengaktifkan profil yang paling ketat yang masih akan mengizinkan lalu lintas yang telah Anda konfigurasikan. Saat ini hanya perlu mengizinkan lalu lintas pada porta 80.
```sh
sudo ufw allow 'Nginx HTTP'
```
Memverifikasi perubahan
```sh
sudo ufw status
```
Mengindikasikan lalu lintas HTTP mana yang diizinkan:
```sh
Output
Status: active
```
```sh
To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Nginx HTTP                 ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
```
Langkah 4 : Memeriksa Server Web

```sh
systemctl status nginx
```
```sh
Output
● nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2020-04-20 16:08:19 UTC; 3 days ago
     Docs: man:nginx(8)
 Main PID: 2369 (nginx)
    Tasks: 2 (limit: 1153)
   Memory: 3.5M
   CGroup: /system.slice/nginx.service
           ├─2369 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           └─2380 nginx: worker process
```
## Install Php

PHP adalah singkatan dari PHP: Hypertext Preprocessor adalah bahasa skrip sumber terbuka yang banyak digunakan oleh pengembang web untuk pengembangan web. PHP banyak digunakan untuk membuat banyak proyek seperti GUI, website dinamis, dan lain-lain..

Langkah 1 : Update & Upgrade Ubuntu Server

```sh
sudo apt update
```
```sh
sudo apt upgrade
```
Langkah 2 : Install PHP 7.4 
```sh
apt install php-phpdbg php-fpm php-curl php-gd php-imap php-interbase php-intl php-ldap php-readline php-pspell php-tidy php-xmlrpc php-json php-sybase php-mysql php-opcache php-bz2 php-mbstring php-xml php-enchant php-gmp php-soap php-zip php-bcmath php-pdo -y
```
Langkah 3 : Periksa versi PHP
```sh
php -v
```
Output
```sh
PHP 7.4.3 (cli) (built: May 26 2020 12:24:22) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.3, Copyright (c), by Zend Technologies
```
## Install Mysql

Merupakan sistem manajemen basis data open source yang menggunakan perintah dasar atau bahasa pemrograman  berupa Structured Query Language (SQL) yang sangat populer di dunia teknologi. MySQL sangat berguna sebagai database.

Langkah 1 : Update & Upgrade Ubuntu Server

```sh
sudo apt update
```
```sh
sudo apt upgrade
```
Langkah 2 : Instal MySQL

```sh
sudo apt install mysql-server
```
Jika Anda hanya ingin terhubung ke server MySQL jarak jauh daripada menghosting database di mesin Anda, instal Klien MySQL saja dengan menjalankan:
```sh
sudo apt install mysql-client
```
Periksa apakah MySQL berhasil diinstal dengan menjalankan:
```sh
mysql --version
```
Langkah 3 : Mengamankan MySQL
Amankan akun pengguna MySQL Anda dengan otentikasi kata sandi dengan menjalankan skrip keamanan yang disertakan:
```sh
sudo mysql_secure_installation
```
Masukkan kata sandi Anda dan jawab `Y` ketika ditanya apakah Anda ingin melanjutkan pengaturan `VALIDATE PASSWORD` komponen.
Pilih salah satu dari tiga tingkat validasi kata sandi:
- 0- Rendah . Kata sandi berisi minimal 8 karakter.
- 1- Sedang . Kata sandi berisi minimal 8 karakter, termasuk angka, karakter huruf campuran, dan karakter khusus.
- 2- Kuat . Kata sandi berisi setidaknya 8 karakter, termasuk angka, karakter huruf campuran, dan karakter khusus, dan membandingkan kata sandi dengan file kamus.

Langkah 4 : Periksa Layanan MySQL
Verifikasi bahwa server MySQL berjalan
```sh
sudo systemctl status mysql
```
Langkah 5 : Masuk ke Server MySQL
```sh
sudo mysql -u root
```
## Install Bind9

Berkeley Internet Name Domain versi 9 atau  disingkat  Bind9 adalah  aplikasi Linux yang dapat digunakan sebagai server DNS. Hingga artikel ini diterbitkan, Bind9 merupakan software yang paling banyak digunakan di Internet. Selain itu, Bind9 juga digunakan sebagai server DNS di sebagian besar distribusi Linux.

Langkah 1 : Update & Upgrade Ubuntu Server

```sh
sudo apt update
```
```sh
sudo apt upgrade
```
Langkah 2 : Instal Bind9

```sh
sudo apt install bind9
```
Memeriksa apakah BIND9 berfungsi.
```sh
nslookup google.com 127.0.0.1
```
Output
```sh
Server:		127.0.0.1
Address:	127.0.0.1#53
```
```sh
Non-authoritative answer:
Name: google.com
Address: 64.233.164.138
...
```
Langkah 3 : Konfigurasi Bind9
Mengkonfigurasinya sesuai dengan tujuan penggunaan
```sh
sudo ufw allow Bind9
```
File konfigurasi utama bernama.conf.options 
```sh
sudo nano /etc/bind/named.conf.options
```
Perintah "listen-on" memungkinkan untuk menentukan jaringan yang akan dilayani oleh server DNS.
```sh
listen-on {
10.10.10.0/24;
10.1.0.0/16;
...
};
```
Bind9 hanya mengizinkan kueri lokal secara default. Tambahkan alamat IP yang diperlukan ke direktif "izinkan kueri" atau "apa pun;" untuk mengizinkan semua permintaan.
```sh
allow-query { any; };
```
Forwarder berisi alamat IP server DNS yang menjadi tujuan pengalihan
```sh
forwarders {
8.8.8.8;
8.8.4.4;
};
```
Simpan dan tutup file. Periksa konfigurasinya:
```sh
sudo named-checkconf
```
Mulai ulang layanan agar perubahan diterapkan.
```sh
sudo systemctl restart bind9
```
Langkah 4 : Periksa Layanan Bind9
Untuk memeriksa apakah server DNS berfungsi dengan benar, masukkan perintah berikut di komputer jarak jauh lainnya. Ganti dns-server-ip-address dengan alamat IP server DNS.
```sh
nslookup ubuntu.com dns-server-ip-address
```
Output
```sh
Server:		dns-server-ip-address
Address:		dns-server-ip-address#53
```
```sh
Non-authoritative answer:
Name: ubuntu.com
Address: 91.189.88.181
...
```

## Install phpMyAdmin

PhpMyAdmin adalah salah satu software gratis yang ditulis dalam bahasa PHP dan merupakan software yang paling populer digunakan untuk mengelola tabel dan data pada database melalui web

Langkah 1 : Update Ubuntu Server

```sh
sudo apt update
```
Langkah 2 : Install phpMyAdmin

```sh
apt install phpmyadmin
```
Langkah 3 : Buat file baru untuk file konfigurasi phpmyadmin

```sh
nano /etc/nginx/snippets/phpmyadmin.conf
```
Paste script dibawah ini  ke dalam file phpmyadmin.conf
```sh
location /phpmyadmin {
     root /usr/share/;
     index index.php index.html index.htm;
     location ~ ^/phpmyadmin/(.+\.php)$ {
         try_files $uri =404;
         root /usr/share/;
         fastcgi_pass unix:/run/php/php8.0(php ver name)-fpm.sock;
         fastcgi_index index.php;
         fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
         include /etc/nginx/fastcgi_params;
     }

               location ~* ^/phpmyadmin/(.+\.(jpg|jpeg|gif|css|png|js|ico|html|xml|txt))$ {
         root /usr/share/;
     }

 }
```
Langkah 4 : buka file /etc/nginx/sites-available/default

```sh
nano /etc/nginx/sites-available/default
```
Tambahkan konfigurasi include snippets/phpmyadmin.conf; di dalam block server{}
```sh
include snippets/phpmyadmin.conf;
```
Langkah 5 : Restart nginx

```sh
systemctl restart nginx
```

## Install Admin Pannel

admin panel server biasanya berupa antarmuka pengguna grafis (GUI) atau antarmuka pengguna berbasis web yang memungkinkan administrator sistem atau pengelola server untuk mengelola dan mengendalikan server.
 Panel Administrasi Server menyediakan berbagai fitur  yang memungkinkan administrator  melakukan tugas manajemen, pemantauan, dan konfigurasi di server.



Langkah 1 : Update Ubuntu Server

```sh
sudo apt update
```
Langkah 2 : Install admin panel

```sh
wget -O - https://raw.githubusercontent.com/yolanmees/Spikster/master/go.sh | bash
```
pastikan ports: 22, 80 dan 443 telah terbuka








