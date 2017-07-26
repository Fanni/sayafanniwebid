---
author: saya
comments: true
date: 2008-11-28 16:44:39+00:00
layout: post
link: http://sayafanni.web.id/?p=9
slug: operasi-file
title: operasi file…..
wordpress_id: 9
categories:
- Slackware
tags:
- bash
---

tulisan ini dibuat berdasarkan pengalaman nyata (hehehe..) pas aku nyobain salah satu tutorial di majalah info linux bulan oktober 2008 tentang split join dan backup file,tutorial lumayan bermanfaat buat nyiasatin file gede yang ga muat di flashdisk n mau dipindahin...

**Split file**
Di linux (disini pake slackware 12.1) udah ada paket GNU Coreutils yang di dalamnya da perintah spilt buat nge-split atau buat membagi atau memecah atau memisahkan file...
sebagai contoh disini bakal di split file backtrack3 final.iso yang gedenya 695MB,
ayo kita mulaiiiii....
hehehe.....

<!-- more -->langkah pertama
[code language="bash"]ls -alh[/code]

langkah ini dipake buat ngelihat informasi hak akses user, gedenya file, trus buat liat
tanggal modifier file itu

langkah kedua
ini langkah penting kawan!!! karena kalo ngga nantinya kita bisa bingung apa ini file masih kayka aslinya atau ngga....oleh karena itulah kita bakalan buat dulu file md5sum file yang bakal kita split kawan....
[code language="bash"]
$ md5sum bt3-final.iso > MD5SUM-bt3-final.txt
$ cat MD5SUM-bt3-final.txt
f79cbfbcd25147df32f5f6dfa287c2d9  bt3-final.iso
[/code]
ini dia informasinya...ntar hasil join dari file splitan ini
mesti sama ma ini

langkah ketiga
[code language="bash"]
$ split -d -b 400m bt3-final.iso bt3-final.part
[/code]
perintah di atas digunakan untuk mensplit file, option -d untuk membuat nummeric suffix atau nomor akhiran untuk file hasil pecahan (misalkan part 1 dan part 2), opsi -b untuk menentukan ukuran maksimal untuk setiap file hasil pecahannya (ket. jika ditulis hanya angka, misal 400, maka perintah split ini akan mengira kita menentukan ukuran maksimal file-nya hanya 400byte, jika mau kilo maka diakhiri dengan huruf K, seperti 400K yang berarti 400 kilobyte, jika megabyte adalah maksud kita, maka pakai akhiran m seperti 400m, maka hal itu berarti 400 megabyte)

selesai deh..hehehe

**Join file**
nah.....setelah tadi kita memecah file bt3-final.iso menjadi dua bagian yaitu bt3-final.iso.part01 dan bt3-final.iso.part02, dan sesudah kita pindahin tu file (kan tadi ceritanya mau mindahin tu file tapi flashdisk kita ga cukup, makanya di split juga,,,nah udah di indahin kita mesti gabungin lagi).
Penggabungan file hasil split bisa dilakukan denga perintah cat, seperti begini
[code language="bash"]
$ cat bt3-final.iso.part01 bt3-final.iso.part02 &gt; bt3-final.iso
[/code]
nah selesei deh, sekarang tinggal kita cek md5sum-nya, apa sama ngga ma file yang aslinya tadi..heheh..mendebarkan ni..
[code language="bash"]
$ md5sum -c MD5SUM-bt3-final.txt
bt3-final.iso: OK
[/code]
nah jika oke, maka berhasil.

sekian dulu ya....moga bermanfaat..wassalam
