# Jarkom-Modul-3-D13-2023
<table>
<tbody>
  <thead>
    <tr>
      <th>Name</th>
      <th>NRP</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Thalent Athalla Razzaq</td>
      <td>5025211101</td>
    </tr>
    <tr>
      <td> Jawahirul Wildan </td>
      <td> 5025211150 </td>
  </tbody>
</table>

Soal Dapat diakses pada [Soal Praktikum Modul 3](https://docs.google.com/document/d/1ST6INlp2SThwfF0GA5Ox7hD7yZqdc6BYcwmMkQmSqJU/edit?usp=sharing)

## Soal 0
Setelah mengalahkan Demon King, perjalanan berlanjut. Kali ini, kalian diminta untuk melakukan register domain berupa riegel.canyon.yyy.com untuk worker Laravel dan granz.channel.yyy.com untuk worker PHP (0) mengarah pada worker yang memiliki IP [prefix IP].x.1.
### Penyelesaian

## Soal 1
Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.
### Penyelesaian

## Soal 2
Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80
### Penyelesaian

## Soal 3
Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168
### Penyelesaian

## Soal 4
Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut 
### Penyelesaian

## Soal 5
Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit 
### Penyelesaian

## Soal 6
Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3
### Penyelesaian

## Soal 7
Kepala suku dari Bredt Region memberikan resource server sebagai berikut:
- Lawine, 4GB, 2vCPU, dan 80 GB SSD.
- Linie, 2GB, 2vCPU, dan 50 GB SSD.
- Lugner 1GB, 1vCPU, dan 25 GB SSD.<br>
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second.
### Penyelesaian

## Soal 8
Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:<br>
a. Nama Algoritma Load Balancer<br>
b. Report hasil testing pada Apache Benchmark<br>
c. Grafik request per second untuk masing masing algoritma. <br>
d. Analisis 
### Penyelesaian

## Soal 9
Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire.
### Penyelesaian

## Soal 10
Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/
### Penyelesaian

## Soal 11
Lalu buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman https://www.its.ac.id
### Penyelesaian

Menambahkan konfigurasi pada file ```/etc/nginx/sites-available/load-balancer``` sebagai berikut

```bash
location ~* /its {
                proxy_pass https://www.its.ac.id;
        }
```
Ketika mengakses ```http://load-balancer.canyon.yyy.com/its``` maka akan diarahkan ke ```https://www.its.ac.id```

![image](./images/11its.png)

## Soal 12
Selanjutnya LB ini hanya boleh diakses oleh client dengan IP [Prefix IP].3.69, [Prefix IP].3.70, [Prefix IP].4.167, dan [Prefix IP].4.168.
### Penyelesaian

Menambahkan konfigurasi ```allow``` pada file ```/etc/nginx/sites-available/load-balancer``` sebagai berikut

```bash
location / {
                proxy_pass http://myweb;
                auth_basic "Admin Area";
                auth_basic_user_file /etc/nginx/rahasiakita/.htpasswd;

                allow 10.28.3.69;
                allow 10.28.3.70;
                allow 10.28.4.167;
                allow 10.28.4.168;
        }
```

Menyesuaikan IP masing-masing client pada file ```/etc/dhcp/dhcpd.conf``` sebagai berikut

```bash
host Revolte {
        hardware ethernet b6:a7:5c:52:c2:22;
        fixed-address 10.28.3.69;
}

host Richter {
        hardware ethernet 86:71:c7:4c:c2:94;
        fixed-address 10.28.3.70;
}

host Sein {
        hardware ethernet 7e:bd:6b:4a:15:6e;
        fixed-address 10.28.4.167;
}

host Stark {
        hardware ethernet 6e:c2:ea:74:e6:e8;
        fixed-address 10.28.4.168;
}
```

## Soal 13
Karena para petualang kehabisan uang, mereka kembali bekerja untuk mengatur riegel.canyon.yyy.com. Semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern.
### Penyelesaian

Melakukan konfigurasi pada file ```/etc/mysql/my.cnf``` sebagai berikut

```bash
# my.cnf

# The MariaDB configuration file
#
# The MariaDB/MySQL tools read configuration files in the following order:
# 1. "/etc/mysql/mariadb.cnf" (this file) to set global defaults,
# 2. "/etc/mysql/conf.d/*.cnf" to set global options.
# 3. "/etc/mysql/mariadb.conf.d/*.cnf" to set MariaDB-only options.
# 4. "~/.my.cnf" to set user-specific options.
#
# If the same option is defined multiple times, the last one will apply.
#
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.

#
# This group is read both both by the client and the server
# use it for options that affect everything
#
[client-server]

# Import all .cnf files from configuration directory
!includedir /etc/mysql/conf.d/
!includedir /etc/mysql/mariadb.conf.d/

[mysqld]

skip-networking=0

skip-bind-address
```

Melakukan konfigurasi pada file ```/etc/mysql/mariadb.conf.d/50-server.cnf``` sebagai berikut dengan mengubah ```bind-address``` menjadi ```0.0.0.0```

```bash
#50-server.cnf

#
# These groups are read by MariaDB server.
# Use it for options that only the server (but not clients) should see
#
# See the examples of server my.cnf files in /usr/share/mysql

# this is read by the standalone daemon and embedded servers
[server]

# this is only for the mysqld standalone daemon
[mysqld]

#
# * Basic Settings
#
user                    = mysql
pid-file                = /run/mysqld/mysqld.pid
socket                  = /run/mysqld/mysqld.sock
#port                   = 3306
basedir                 = /usr
datadir                 = /var/lib/mysql
tmpdir                  = /tmp
lc-messages-dir         = /usr/share/mysql
#skip-external-locking

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 0.0.0.0

#
# * Fine Tuning
#
#key_buffer_size        = 16M
#max_allowed_packet     = 16M
#thread_stack           = 192K
#thread_cache_size      = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
#myisam_recover_options = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10

#
# * Query Cache Configuration
#
#query_cache_limit      = 1M
query_cache_size        = 16M

#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file       = /var/log/mysql/mysql.log
#general_log            = 1
#
# Error log - should be very few entries.
#
log_error = /var/log/mysql/error.log
#
# Enable the slow query log to see queries with especially long duration
#slow_query_log_file    = /var/log/mysql/mariadb-slow.log
#long_query_time        = 10
#log_slow_rate_limit    = 1000
#log_slow_verbosity     = query_plan
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
#max_binlog_size        = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = exclude_database_name

#
# * Security Features
#
# Read the manual, too, if you want chroot!
#chroot = /var/lib/mysql/
#
# For generating SSL certificates you can use for example the GUI tool "tinyca".
#
#ssl-ca = /etc/mysql/cacert.pem
#ssl-cert = /etc/mysql/server-cert.pem
#ssl-key = /etc/mysql/server-key.pem
#
# Accept only connections using the latest and most secure TLS protocol version.
# ..when MariaDB is compiled with OpenSSL:
#ssl-cipher = TLSv1.2
# ..when MariaDB is compiled with YaSSL (default in Debian):
#ssl = on

#
# * Character sets
#
# MySQL/MariaDB default is Latin1, but in Debian we rather default to the full
# utf8 4-byte character set. See also client.cnf
#
character-set-server  = utf8mb4
collation-server      = utf8mb4_general_ci

#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!

#
# * Unix socket authentication plugin is built-in since 10.0.22-6
#
# Needed so the root database user can authenticate without a password but
# only when running as the unix root user.
#
# Also available for other users if required.
# See https://mariadb.com/kb/en/unix_socket-authentication-plugin/

# this is only for embedded server
[embedded]

# This group is only read by MariaDB servers, not by MySQL.
# If you use the same .cnf file for MySQL and MariaDB,
# you can put MariaDB-only options here
[mariadb]

# This group is only read by MariaDB-10.3 servers.
# If you use the same .cnf file for MariaDB of different versions,
# use this group for options that older servers don't understand
[mariadb-10.3]
```

Menjalankan konfigurasi user dan database pada MySQL sebagai berikut

```bash
mysql -u root

CREATE USER 'kelompokd13'@'%' IDENTIFIED BY 'passwordd13';

CREATE USER 'kelompokd13'@'localhost' IDENTIFIED BY 'passwordd13';

CREATE DATABASE dbkelompokd13;

GRANT ALL PRIVILEGES ON *.* TO 'kelompokd13'@'%';

GRANT ALL PRIVILEGES ON *.* TO 'kelompokd13'@'localhost';

FLUSH PRIVILEGES;
```

![image](./images/13db.png)

## Soal 14
Frieren, Flamme, dan Fern memiliki Riegel Channel sesuai dengan quest guide berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer
### Penyelesaian

Menginstalasi PHP8.0 dan Composer sebagai berikut

```bash
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y

wget https://getcomposer.org/download/2.0.13/composer.phar

chmod +x composer.phar

mv composer.phar /usr/bin/composer
```

Menginstalasi git dan mengkloning repository sebagai berikut

```bash
apt-get install git -y

cd /var/www && git clone https://github.com/martuafernando/laravel-praktikum-jarkom
```

Melakukan konfigurasi pada repository sebagai berikut

```bash
cd /var/www/laravel-praktikum-jarkom && cp .env.example .env

cd /var/www/laravel-praktikum-jarkom && composer update

echo 'APP_NAME=Laravel

APP_ENV=local

APP_KEY=

APP_DEBUG=true

APP_URL=http://localhost



LOG_CHANNEL=stack

LOG_DEPRECATIONS_CHANNEL=null

LOG_LEVEL=debug



DB_CONNECTION=mysql

DB_HOST=10.28.2.2

DB_PORT=3306

DB_DATABASE=dbkelompokd13

DB_USERNAME=kelompokd13

DB_PASSWORD=passwordd13



BROADCAST_DRIVER=log

CACHE_DRIVER=file

FILESYSTEM_DISK=local

QUEUE_CONNECTION=sync

SESSION_DRIVER=file

SESSION_LIFETIME=120



MEMCACHED_HOST=127.0.0.1



REDIS_HOST=127.0.0.1

REDIS_PASSWORD=null

REDIS_PORT=6379



MAIL_MAILER=smtp

MAIL_HOST=mailpit

MAIL_PORT=1025

MAIL_USERNAME=null

MAIL_PASSWORD=null

MAIL_ENCRYPTION=null

MAIL_FROM_ADDRESS="hello@example.com"

MAIL_FROM_NAME="${APP_NAME}"



AWS_ACCESS_KEY_ID=

AWS_SECRET_ACCESS_KEY=

AWS_DEFAULT_REGION=us-east-1

AWS_BUCKET=

AWS_USE_PATH_STYLE_ENDPOINT=false



PUSHER_APP_ID=

PUSHER_APP_KEY=

PUSHER_APP_SECRET=

PUSHER_HOST=

PUSHER_PORT=443

PUSHER_SCHEME=https

PUSHER_APP_CLUSTER=mt1



VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"

VITE_PUSHER_HOST="${PUSHER_HOST}"

VITE_PUSHER_PORT="${PUSHER_PORT}"

VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"

VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"' > /var/www/laravel-praktikum-jarkom/.env

cd /var/www/laravel-praktikum-jarkom && php artisan key:generate

cd /var/www/laravel-praktikum-jarkom && php artisan config:cache

cd /var/www/laravel-praktikum-jarkom && php artisan migrate

cd /var/www/laravel-praktikum-jarkom && php artisan db:seed --class=AiringsTableSeeder

cd /var/www/laravel-praktikum-jarkom && php artisan storage:link

cd /var/www/laravel-praktikum-jarkom && php artisan jwt:secret

cd /var/www/laravel-praktikum-jarkom && php artisan config:clear

chown -R www-data.www-data /var/www/laravel-praktikum-jarkom/storage
```

![image](./images/14laravel.png)

## Soal 15
Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire.<br>
a. POST /auth/register
### Penyelesaian

Membuat file ```register_data.json``` sebagai berikut

```json
{
  "username": "kelompokd13",
  "password": "passwordd13"
}
```

Melakukan testing menggunakan Apache Benchmark sebagai berikut

```bash
ab -n 100 -c 10 -p register_data.json -T application/json http://10.28.4.1:8001/api/auth/register
```

![image](./images/15register.png)

## Soal 16
Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire.<br>
b. POST /auth/login
### Penyelesaian

Membuat file ```login_data.json``` sebagai berikut

```json
{
  "username": "kelompokd13",
  "password": "passwordd13"
}
```

Melakukan testing menggunakan Apache Benchmark sebagai berikut

```bash
ab -n 100 -c 10 -p register_data.json -T application/json http://10.28.4.1:8001/api/auth/login
```

![image](./images/16login.png)

## Soal 17
Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire.<br>
c. GET /me
### Penyelesaian

Mendapatkan token menggunakan curl sebagai berikut

```bash
curl -X POST -H "Content-Type: application/json" -d '{"username": "kelompokd13", "password": "passwordd13"}' http://10.28.4.1:8001/api/auth/login | jq -r '.token' > token.txt
```

![image](./images/17curl.png)

![image](./images/17token.png)

Melakukan testing menggunakan Apache Benchmark sebagai berikut

```bash
token=$(cat token.txt); ab -n 100 -c 10 -H "Authorization: Bearer $token" http://10.28.4.1:8001/api/me
```

![image](./images/17me.png)

## Soal 18
Untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern.
### Penyelesaian

Melakukan konfigurasi pada file ```/etc/bind/named.conf.local``` sebagai berikut

```bash
upstream laravel  {

        server 10.28.4.1:8001;

        server 10.28.4.2:8002;

        server 10.28.4.3:8003;

 }

 server {

        listen 80;

        server_name riegel.canyon.d13.com;

        location / {
                proxy_pass http://laravel;
        }
 }
```

## Soal 19
Untuk meningkatkan performa dari Worker, coba implementasikan PHP-FPM pada Frieren, Flamme, dan Fern. Untuk testing kinerja naikkan 
- pm.max_children
- pm.start_servers
- pm.min_spare_servers
- pm.max_spare_servers

sebanyak tiga percobaan dan lakukan testing sebanyak 100 request dengan 10 request/second kemudian berikan hasil analisisnya pada Grimoire.
### Penyelesaian

```bash
# Default setting

pm.max_children 5
pm.start_servers 2
pm.min_spare_servers 1
pm.max_spare_servers 3

# Percobaan 1
pm.max_children 10
pm.start_servers 5
pm.min_spare_servers 2
pm.max_spare_servers 7

# Percobaan 2
pm.max_children 20
pm.start_servers 10
pm.min_spare_servers 5
pm.max_spare_servers 15

# Percobaan 3
pm.max_children 40
pm.start_servers 20
pm.min_spare_servers 10
pm.max_spare_servers 30
```

**Default setting**

![image](./images/19default.png)

**Percobaan 1**

![image](./images/19coba1.png)

**Percobaan 2**

![image](./images/19coba2.png)

**Percobaan 3**

![image](./images/19coba3.png)

## Soal 20
Nampaknya hanya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa dari worker maka implementasikan Least-Conn pada Eisen. Untuk testing kinerja dari worker tersebut dilakukan sebanyak 100 request dengan 10 request/second.
### Penyelesaian

Menambahkan konfigurasi ```least_conn``` pada file ```/etc/nginx/sites-available/laravel-balancer``` sebagai berikut

```bash
upstream laravel  {
        least_conn;
        server 10.28.4.1:8001;

        server 10.28.4.2:8002;

        server 10.28.4.3:8003;

 }
```

![image](./images/20.png)

## Lampiran
File Grimoire dapat diakses pada link [D13_Grimoire](https://docs.google.com/document/d/16JQ0c2eIGqWhTHBZtcQcyUonNCugJguOvy14t86pvQ0/edit?usp=sharing)
