---
author: saya
comments: true
date: 2010-04-25 02:07:34+00:00
layout: post
link: http://sayafanni.web.id/?p=146
slug: detail-informasi-arsip-paket-tar-gz-ke-dalam-html
title: Detail informasi arsip paket tar.gz ke dalam HTML
wordpress_id: 146
categories:
- Programming
- Shell
tags:
- shell
---

Dengan bantuan shell script sama tool sistem,banyak hal menarik yang bisa dibuat di Linux. Salah satunya adalah menampilkan detil file paket tar.gz ke dalam format HTML. Langsung saja, buat uji cobanya saya pakai paket wget-1.9.tar.gz (bisa pake paket apa saja asal tar.gz). Setelah itu saya coba liat informasi paketnya dengan perintah berikut :
[code language="bash"]
ls -l wget-1.9.tar.gz
[/code]<!-- more -->
maka akan keluar output seperti ini :
[code language="bash"]
-rw-r--r-- 1 fanni users 1315995 2010-04-12 21:35 wget-1.9.tar.gz
[/code]

Setelah itu kita coba melihat informasi lainnya mengenai file tersebut dengan menggunakan perintah berikut :
[code language="bash"]
file -z wget-1.9.tar.gz
[/code]
akan mengeluatkan output seperti ini :
[code language="bash"]
wget-1.9.tar.gz: POSIX tar archive (GNU) (gzip compressed data, from Unix, last modified: Wed Oct 22 04:48:09 2003, max compression)
[/code]

dari informasi tersebut kita mengetahui kalo file wget-1.9.tar.gz adalah data kompresi gzip yang telah dikompresi secara maksimal dan terdapat paket tar di dalamnya.

Selanjutnya saya coba untuk menampilkan isi dari paket tersebut tanpa mengekstraknya terlebih dahulu dengan menjalankan perintah berikut :
[code language="bash"]
tar ztf wget-1.9.tar.gz
[/code]
dengan keluaran adalah isi dari paket wget tersebut.

setelah itu bagaimana jika kita menampilkan hal-hal yang lebih mendetail tentang file tersebut seperti ukuran terkompresi,metode kompresi dan lain-lain? jawabannya cukup dengan menjalankan perintah berikut :
[code language="bash"]
gzip -vl wget-1.9.tar.gz
[/code]
maka akan menampilkan output informasi tentang file tersebut seperti metode kompresi,crc,waktu dan tanggal terakhir dimodif,ukuran file ketika terkompres dan sebelum di kompres, rasio kompresi dan nama file sebelum terkompresi dengan gzip.

Selanjutnya adalah kita coba untuk menyimpan informasi itu ke dalam format html dengan menggunakan shell scipt berikut :

[code language="bash"]
#!/bin/sh

if [ -z "$1" ] 
then
 echo "usage: $0 <file.tar.gz>";
 exit 1
fi 

FHTML="$1.html";

echo "<HTML>
 <HEAD><TITLE>Informasi paket $1</TITLE></HEAD>;
 <BODY><H3>$1</H3>
 <PRE>
$(gzip -vl $1)
 <BR>
 Isi Paket <HR>
 $(tar tzf $1)<HR>
 Digenerate Oleh $(basename $0) pada $(date)</PRE>
 </BODY></HTML>"> "$FHTML"
[/code]

setelah itu simpan dengan nama (misalkan) paketinfo.sh, lalu ubah menjadi eksekutable dengan perintah berikut :
[code language="bash"]chmod +x paketinfo.sh[/code]

lalu jalankan dengan perintah berikut diikuti dengan nama paket yg akan ditampilkan infonya:
[code language="bash"]./paketinfo.sh wget-1.9.tar.gz[/code]

apabila tidak ada pesan yang tampil, maka proses telah selesai dan akan terbentuk sebuah file bernama wget-1.9.tar.gz di direktori aktif. Tampilan akhirnya seperti berikut:

[caption id="attachment_148" align="aligncenter" width="150" caption="Isi file wget-1.9.tar.gz"][![](http://sayafanni.files.wordpress.com/2010/04/snapshot2.png?w=150)](http://sayafanni.files.wordpress.com/2010/04/snapshot2.png)[/caption]

selamat mencobaa..terimakasih
