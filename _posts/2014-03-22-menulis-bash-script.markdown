---
author: saya
comments: true
date: 2014-03-22 07:20:41+00:00
layout: post
link: http://sayafanni.web.id/?p=464
slug: menulis-bash-script
title: Menulis Bash Script
wordpress_id: 464
categories:
- Hobi
- Kehidupan saya
- Programming
- Shell
- Slackware
tags:
- bash
- Bash Script
---

Ingin coba nulis skrip bash, saya pun menulis skrip bash sederhana untuk menjalankan service mysql dan apache di Slackware.
Skrip tersebut hanya dapat diproses jika dijalankan oleh root saja, skrip ini akan melakukan pemeriksaan apakah kedua service tersebut, mysql dan apache, telah berjalan atau tidak, untuk selanjutnya akan dilakukan beberapa proses berdasarkan hasil dari pemeriksaan tadi.

Berikut adalah skrip bash-nya
<!-- more -->

[code language="bash"]
#! /bin/bash

clear

if [ "$USER" != "root" ]; then
   echo "Harus root! :D";
else
   case "$(pidof mysqld | wc -w)" in
      0) echo "menjalankan servis mysqld"
         /usr/bin/mysqld_safe --user=mysql &
         ;;
      1) echo "servis mysqld sudah berjalan"
         ;;
      *) echo "menghentikan servis mysqld terakhir"
         kill $(pidof mysqld | awk '{print $1}') &
         ;;
   esac

   if ["$(pidof httpd | wc -w)" -eq 0]; then
      echo "menjalankan servis apache"
      apachectl start &
   else
      echo "menjalankan kembali servis apache"
      apachectl restart &
   fi
fi
[/code]


Seperti telah dijelaskan sebelumnya, pertama-tama akan dilakukan pemeriksaan apakah pengguna saat ini adalah root atau bukan, jika bukan maka akan ditampilkan pesan "Harus Root!"

[code language="bash"]
if [ "$USER" != "root" ]; then echo "Harus root! :D";
[/code]


selanjutnya adalah memeriksa apakah service mysql sudah berjalan atau belum. Untuk hal tersebut, maka dalam skrip ini saya menuliskan perintah berikut

[code language="bash"]
pidof mysqld | wc -w
[/code]


_pidof_ adalah perintah untuk mengetahui pid atau process id dari suatu servis dan _wc -w_ merupakan perintah untuk menuliskan hasil perhitungan kata dari file. Jadi hasil dari perintah _pidof_ akan dihitung jumlah katanya dengan _wc -w_ sehingga kita bisa menentukan apakah suatu proses sudah berjalan atau belum.

Selanjutnya ditentukan tiga kondisi yaitu jika terdapat satu proses mysqld, tidak ada proses mysqld dan terdapat beberapa proses mysqld.

[code language="bash"]
      0) echo "menjalankan servis mysqld
         /usr/bin/mysqld_safe --user=mysql &
         ;;
      1) echo "servis mysqld sudah berjalan"
         ;;
      *) echo "menghentikan servis mysqld terakhir"
         kill $(pidof mysqld | awk '{print $1}')
         ;;
[/code]


Pada kode di atas terdapat perintah _awk_ yang berfungsi untuk memproses data teks yang berupa kolom, seperti tabel dan _$1_ merupakan kolom pertama dari suatu data teks. Pada skrip di atas perintah _awk '{print $1}'_ berfungsi untuk mendapatkan data teks kolom pertama dari keluaran perintah _pidof_ yang nantinya akan menghasilkan keluaran hanya berupa pid dari servis mysqld terakhir yang dijalankan.

Proses selanjutnya adalah memeriksa apakah servis apache telah berjalan atau belum, pemeriksaan menggunakan perintah

[code language="bash"]
"$(pidof httpd | wc -w)" -eq 0
[/code]


_-eq_ merupakan operator pembanding yang sama dengan tanda "=="

Simpan skrip tersebut dengan ekstensi _.sh_ lalu ubah menjadi _executable_ dengan menjalankan perintah

[code language="bash"]
chmod +x namaskrip.sh
[/code]


lalu untuk menjalankannya cukup dengan perintah

[code language="bash"]
sh namaskrip.sh
[/code]

Untuk penjelasan dan tutorial bash script yang lengkap bisa berkunjung ke `http://www.tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_05.html`
