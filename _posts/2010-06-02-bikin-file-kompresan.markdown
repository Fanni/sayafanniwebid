---
author: saya
comments: true
date: 2010-06-02 23:11:28+00:00
layout: post
link: http://sayafanni.web.id/?p=194
slug: bikin-file-kompresan
title: Bikin file kompresan
wordpress_id: 194
categories:
- Slackware
tags:
- bash
---

Tadi malem saya amnesia.Lupa gimana caranya ngompress file jadi tar.bz2, untung amnesianya ga lama abis baca manualnya tar (hehehe)...jadi biar ga lupa saya tulis aja baris perintahnya di sini, jadi pas sewaktu-waktu lupa bisa liat blog buat liat perintahnya..hehehe..langsung aja ni perintahnya

[code language="bash"]tar cjf file.tar.bz2 file/[/code]

keterangan :  
kalo ga salah sih penjelasannya begini..CMIIW  
tar : perintah buat ngebungkus paket jadi file tar  
c : buat create paket atau file kompresan  
j : tipe kompresannya .bz2 klo "z" .gz  
f : nama file nya  
file.tar.bz : nama paket yang kita inginkan tentunya dengan akhiran .tar.bz2  
file/ : nama file atau folder yang akan dikompress

sekian saja...terimakasih
