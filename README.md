# Tugas Akhir Mata Kuliah
## OS SERVER & SISTEM ADMIN
- Nama : MUHAMMAD SAIFUL AJI
- Nim  : 22.83.0789



## WEB SERVER
Web server adalah perangkat lunak yang menyediakan layanan dalam bentuk data. Fungsi tersebut menerima permintaan HTTP atau HTTPS dari klien atau biasa kita sebut browser web  (Chrome, Firefox). Kemudian mengirimkan respons permintaan ke klien dalam bentuk halaman web.

## Resource

- [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- [Nginx](https://www.nginx.com/)
- [Mysql](https://www.mysql.com/)
- [Php](https://www.php.net/)
- [VirtualBox](https://www.virtualbox.org/)


## Update Perkembangan

- 28/09/2023 - Intalasi [Ubuntu Server 20](https://releases.ubuntu.com/focal/) di [VirtualBox](https://www.virtualbox.org/)
- 30/09/2023 - Instalasi [Nginx](https://www.nginx.com/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)
- 01/10/2023 - Instalasi [Php](https://www.php.net/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)

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

















