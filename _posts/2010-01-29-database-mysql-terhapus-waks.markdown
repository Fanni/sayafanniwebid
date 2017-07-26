---
author: saya
comments: true
date: 2010-01-29 06:52:17+00:00
layout: post
link: http://sayafanni.web.id/?p=27
slug: database-mysql-terhapus-waks
title: database MySQL terhapus…waks
wordpress_id: 27
categories:
- Slackware
tags:
- mysql
---

Judulnya aneh ya??moga tulisannya ngga aneh,langsung saja,

jadi ceritanya begini,waktu itu saya kepikiran buat ngisi postingan lagi di blog offline saya...ternyata eh ternyata, saya lupa password admin di wordpress offline itu... ya kepaksa dah saya drop database wordpressnya yang bernama myblog (knapa mesti di drop??ya itu pikiran pertama saya..hehehe)..ya sudahlah saya drop itu databasenya, ga tau ngantuk ga tau laper itu yang mestinya ngetik

`>drop database myblog;`

malah jadi begini

`>drop database mysql;`
<!-- more -->
ya sudahlah...eror aja itu mysql-nya, pas saya mau jalanin, malah ada peringatan seperti ini

`Can't connect to local MySQL server through socket '/var/run/mysql/mysql.sock'`

bingung lah saya, saya coba masuk ke direktori /var/run/mysql, terus saya liat isinya ternyata file yang mysql.sock nya tu ilang ga ada alias missing, terus saya coba cari di konsol dengan ngetik perintah berikut

`$ find / -name mysql`

dan hasilnya nihil..Gimana sih kalo begitu??(lagunya Warteg Boys),,ya sudah saya mencoba tenang lalu coba cari bantuannya di manual MySQL,ketemu lah kata manualnya install aja database MySQL yang baru, caranya ketik kode ini

`# mysql_install_db`

saya enter, wuis bisa!!! tapi tunggu dulu ini mah mesti diuji dulu, masuk ke MySQL commandnya

`# mysql`
Enter
`Can't connect to local MySQL server through socket '/var/run/mysql/mysql.sock'`

sama aja ternyata...da emang kalo diliat itu file mysql.sock-nya ga ada, ya sudah cz dah kepepet perlu banget MySQL buat ngerjain tugas, ya udah saya install ulang aja MySQL-nya biar cepet..hehe, (note:setiap paket MySQL udah ada di cd atau dvd instalasi slackwarenya..cari aja di folder slackware/ap namanya kalo ga salah mysql-5.0.84-i486-1.txz)...caranya

1.remove MySQL, masuk ke pkgtool z

`# pkgtool`

2.nanti pilih pilihan `remove` terus enter
3.cari paket MySQL nya(ingat jangan sampai salah lagi,,)
4.kalo sudah ketemu tandain pake tombol spacebar, terus enter OK
5.paket MySQL bakalan terhapus otomatis..
6.reboot komputernya.
7.Lalu setelah nyala kembali komputernya siapkan paket MySQL yang mau diinstal
8.change directory ke tempat paket MySQL itu misalkan paket MySQL ada di /home/user/paket/

`# cd /home/user/paket`

9.masuk lagi ke menu `pkgtool` seperti langkah pertama
dicara saya, saya menggunakan `pkgtool` lagi biar cepet..tapi sebenranya samaa aja sih ma perintah `installpkgnama_paket`
10.pilih pilihan Current terus enter,setelah itu akan muncul paket-paket yang bisa dan mau diinstal, pilih No untuk paket yang bukan MySQL dan pilih Yes untuk paket MySQL yang akan diinstalkan terus tekan Ok, maka MySQL akan segera terinstal..
11.setelah paket MySQL terinstall saatnya melakukan konfigurasi, pertama saya ketikkan perintah berikut di konsol

`# chmod +x /etc/rc.d/rc.mysqld`

terusjalanin perintahnya

`# /etc/rc.d/rc.mysqld start`

setelah dienter ternyata ada suatu kesalahan yang terjadi, itu tandanya ada yang mesti kita atur, dalam hal ini adalah master tabel yang belum terinstal
12.sekarang kita install master table MySQL nya (yang saya hapus secara tidak sengaja waktu itu), caranya

`# mysql_install_db`

lalu enter
13.karena saat melakukan penginstalan database master tersebut posisi saya sebagai root, maka kita perlu mengubah permission direktorinya dengan cara berikut

`# chown mysql.mysql /var/lib/mysql/ -R`

14.lalu saya coba jalankan lagi perintah berikut

`# /etc/rc.d/rc.mysqld start` enter

lalu kan muncul tampilan berikut

`nohup: redirecting stderr to stdout
Starting mysqld daemon with databases from /var/lib/mysql`

itu tandanya telah berhasil, lalu tekan kombinasi tombol ctrl+c untuk keluar
15.langkah terakhir adalah masuk ke MySQL nya, caranya ketik perintah berikut

`# mysql`

maka akan muncul tampilan konsol MySQL sebagai berikut

`Welcome to the MySQL monitor.  Commands end with ; or g.
Your MySQL connection id is 12
Server version: 5.0.84 Source distribution`

Type 'help;' or 'h' for help. Type 'c' to clear the current input statement.

mysql>

wah berhasil deh..hehehe,

makasih yah udah baca postingan ini, mohon maaf karena tulisan dan gaya bahasanya kacau dan campur aduk,,mohon maaf...
