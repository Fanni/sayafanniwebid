---
author: saya
comments: true
date: 2008-11-28 20:43:33+00:00
layout: post
link: http://sayafanni.web.id/?p=10
slug: jalanin-mysql-di-slackware
title: jalanin mysql di slackware….
wordpress_id: 10
categories:
- Slackware
tags:
- mysql
---

bagi kawan-kawan pengguna linux yang biasa berurusan dengan database, mungkin tidak akan asing dengan DBMS yang satu ini, tiada lain dan tiada bukan, adalah MySQL....(wahahaha..), nah karena blog ini ditulis berdasarkan pengalaman pribadi (hehehe...), maka kali ini juga aku bakal bagi-bagi pengalaman tentang nyeting MySQL di slackware 12.1 (The Real Linux!!!!!!!!).check this out:

langkah pertama ubah mode rc.mysqld di /etc/rc.d menjadi executable

# chmod +x /etc/rc.d/rc.mysqld

nah udah itu coba tes dengan ngetikin

# /etc/rc.d/rc.mysqld start

pasti bakal keluar bacaan berikut ini

<!-- more --> # Starting mysqld daemon with databases from /var/lib/mysql
STOPPING server from pid file /var/run/mysql/mysql.pid
070628 13:15:40 mysqld ended

nah biar bisa jalan, kita mesti bikin satu database "induk" yang namanya mysql, database ini digunain buat nyimpen data - data tentang database server, misalnya pengguna/user, komputer pengakses, ampe hak akses dari user. Cara bikin database mysql itu, kita tinggal ketik perintah

# mysql_install_db

nah dari perintah di atas, pas kita enter, bakal muncul beberapa baris pesan. Tapi berita buruknya, kita masih belum bisa menjalankan mysql kita, ini disebabkan karena script rc.mysqld mengharuskan penggunanya adalah "mysql" dan dari group "mysql" juga, sedangkan tadi pas kita bikin itu database hak miliknya jatuh ke tangan root (hallah..kayak paan ja). Lalu bagaimana caranya????
tenang saja kawan..kita tinggal mengubah kepemilikannya kok,,mudah kan (hehehehe...geuleuh gtu!!). Di slackware file - file kepemilikan tersebut ada di /var/lib/mysql, jadi buat ngubahnya  perintah berikut biasanya berfungsi (biasanya...hehe):

# chown mysql.mysql /var/lib/mysql/ -R

coba kita jalanin lagi mysql servernya :

# /etc/rc.d/rc.mysqld start

bakal keluar pesan

# Starting mysqld daemon with databases from /var/lib/mysql
Tanpa pesan "mysql ended"
selanjutnya ketik perintah mysql buat masuk ke mysql server.

# mysql
Welcome to the MySQL monitor. Commands end with ; or g.
Your MySQL connection id is 1 to server version: 5.0.27-log
Type 'help;' or 'h' for help. Type 'c' to clear the buffer.
mysql>

Nah...kalo tulisan yang keluar mirip kayak yang di atas, maka mysql server kamu bisa dijalankan..........horeeeeeeee
(tapi kalo ngga???mmm..coba dari awal lagi ya, semangaaaat!!!)

nah ada cara singkat setelah experimen nih, tapi kayaknya sama aja ma yg tadi..hehehe

# cd /var/lib
# chown -R mysql mysql mysql
# chgrp -R root mysql mysql
# mysql_install_db
# mysql_safe &
# mysqladmin -u root password 'new_pass'

trus jalanin mysql

# mysql
Welcome to the MySQL monitor. Commands end with ; or g.
Your MySQL connection id is 1 to server version: 5.0.27-log
Type 'help;' or 'h' for help. Type 'c' to clear the buffer.

mysql>

sekian............semoga bermanfaat yaa, wassalam..
