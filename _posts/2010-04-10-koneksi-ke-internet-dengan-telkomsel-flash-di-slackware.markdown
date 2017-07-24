---
author: saya
comments: true
date: 2010-04-10 00:26:31+00:00
layout: post
link: http://sayafanni.web.id/?p=122
slug: koneksi-ke-internet-dengan-telkomsel-flash-di-slackware
title: Koneksi ke Internet dengan Telkomsel Flash di Slackware
wordpress_id: 122
categories:
- Slackware
---

Terhitung dengan hari ini, saya sudah 105 hari koneksi internet dengan menggunakan Telkomsel Flash, lumayan juga sih buat browsing-browsing mah, oh iya saya ambil paket Unlimited kuota 1GB perbulan bayarnya 125rb (sesuai perjanjian). Awalnya sih bingung juga gimana cara settingnya di slackware, cz kartu Flash-nya termasuk locked simcard yang butuh masukin pin waktu diaktifin. Untungnya saya nemu tool namanya comgt, download di [sini](http://sourceforge.net/projects/comgt/files/comgt/0.32/comgt.0.32.tgz/download), comgt itu adalah command-line tool yang berguna untuk mengatur dan memungkinkan interaksi dengan Option Wireless 3G and 2G ( HSDPA, UMTS, EDGE, GPRS, GSM) data device di lingkungan linux. <!-- more -->
Cara konfigurasinya seperti berikut,
-setelah mendownload tool comgt, seperti biasa lakukan kompilasi dan instalasi seperti berikut
[code language="bash"]
 installpkg comgt.0.32.tgz
[/code]
-setelah instalasi...koneksikan atau colokkan modemnya (yang sudah berisi kartu telkomsel flash), 
-lalu masuk ke konsole,ketikkan perintah berikut (sebagai root)
[code language="bash"]
comgt
[/code]

setelah itu akan tampil tampilan untuk memasukkan pin kartu Flashnya..tinggal masukin pin lalu enter...sekarang modem+kartu flash-nya bisa dipakai internetan..hehehe

Catatan: jika terjadi error ketika melakukan perintah comgt, coba lagi saja sampai muncul inputan pin...

terimakasih..selamat mencoba...
