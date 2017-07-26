---
author: saya
comments: true
date: 2010-01-29 09:05:54+00:00
layout: post
link: http://sayafanni.web.id/?p=12
slug: code-php-untuk-validasi-via-email
title: Code PHP untuk validasi via email...
wordpress_id: 12
categories:
- PHP
- Programming
tags:
- php
---

Tulisan ini saya tulis sekedar untuk berbagi pengetahuan buat teman-teman, semoga bermanfaat...

Seringkali ketika saya mendaftar jadi member di sebuah situs (baik jejaring sosial maupun situs akademik formal) atau mendaftar menjadi member di suatu forum, saya selalu diberitahu untuk memverifikasi pendaftaran saya melalu link yang mereka kirimkan ke email saya, link tersebut akan membawa saya untuk mengaktifkan akun saya, sehingga saya bisa login dengan akun tersebut.
<!-- more -->
validasi via email, dengan mengirimkan kode-kode tertentu kepada suatu lamat e-mail seperti kasus di atas bisa dibuat dengan menggunakan fungsi mail di PHP. fungsi tersebut berformat seperti berikut :


[code language="php"]mail(alamat,subjek_pesan,isi_pesan,kepala/header_pesan);[/code]




- alamat diisi dengan alamat e-mail yang akan dikirmi e-mail oleh program kita
- subjek_pesan diisi dengan subjek atau judul e-mail atau perihal e-mail yang kita kirim melalui program kita
- isi_pesan diisi dengan isi pesan yang akan dikirmkan kepada alamat e-mail penerima
- kepala/header_pesan diisi dengan header tentang informasi e-mail tersebut seperti


[code]
"Dari:apa@dim.comrnbcc:sapa@dim.com"
[/code]


contoh header tersebut akan memberitahukan kepada penerima e-mail dari mana e-mail tersebut dikirim dan akan di BCC (Blind Copy Carbon) ke alamat email siapapun@dimanapun.com.

Berikut saya sajikan satu contoh penggunaan fungsi tersebut,


[code language="php"]
$ke = “tujuan@terminal.com”;
$subjek = “Tes”;
$isi = “Ngetes fungsi ngirim email di PHP”;
$header = bcc:apapun@dimanapun.comrn
$kirim = mail($ke,$subjek,$isi,$header);
[/code]


kode tersebut menyimpan fungsinya ke dalam variabel yang bernama $kirim yang bisa dipanggil pada fungsi lain dengan hanya mengetikkan nama variabelnya.

Sekian saja tulisan mengenai fungsi mengirim e-mail dengan PHP, berikut saya cantumkan potongan program saya yang berisi fungsi pengirim e-mail


[code language="php"]
/* mengirim email kepada member baru */
$pesan = “Akun member baru Anda telah berhasil dibuat. “;
$pesan.= “Member ID dan password Anda adalah: “;
$pesan.= “nnt$namabarunt$pasworbarunn”;
$pesan.= “Terima kasih telah bergabung bersama kami”;
$pesan.= “ di jualbelionline.co.id. nn”;
$pesan.= “Jika ada pertanyaan atau permasalahan tentang situs kami,”;
$pesan.= “ silahkan kontak kami di email webmaster@jualbelionline.co.id”;
$ehead=”Dari: memberadmin@jualbelionline.co.idrn”;
$sub = “Akun Baru Anda dari JualBeliOnline”;
$kirim=mail(“$email”,”$sub”,”$pesan”,”$ehead”);
header(“Location: Member_baru.php”);
[/code]
