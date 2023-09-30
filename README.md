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


## Update Perkembangan

- 28/09/2023 - Intalasi [Ubuntu Server 20](https://releases.ubuntu.com/focal/) di VirtualBox
- 30/09/2023 - Intalasi [Nginx](https://www.nginx.com/) di [Ubuntu Server 20](https://releases.ubuntu.com/focal/)

## Install Nginx

Nginx tersedia di repositori asali Ubuntu, maka kita dimungkinkan untuk menginstalnya dari repositori ini menggunakan sistem pengemasan `apt`.

Langkah 1 : Install Nginx

```sh
sudo apt update
sudo apt install nginx
```
Langkah 2 : Setting Firewall

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

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Nginx HTTP                 ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
```
Langkah 3 : Memeriksa Server Web

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


















