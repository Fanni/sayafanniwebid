---
author: saya
comments: true
date: 2011-05-06 12:31:51+00:00
layout: post
link: http://sayafanni.web.id/?p=283
slug: merubah-volume-name-flashdisk-vfat-di-slackware
title: merubah volume name flashdisk (vfat) di slackware
wordpress_id: 283
categories:
- Kehidupan saya
- Slackware
tags:
- mlabel
---

Sekian lama pake slackware, baru hari ini,malam ini saya bisa mengubah nama flashdisk saya melalui slackware (agak berlebihan) :D . Okeh langsung saja, untuk mengubah volume name suatu flashdisk kita bisa menggunakan perintah _mlabel_,pertama-tama kita harus mengedit file mktools.conf di /etc dengan menambahkan drive baru, misal ketika tertancap flashdisk kita dipetakan di /dev/sda1 dan kita tentukan nama drivenya adalah z, maka kita tambahkan code berikut di file mktools-nya

```bash
drive z: file="/dev/sda1"
```

<!-- more -->
okey..setelah itu kita testing dengan menggunakan perintah (dijalankan sebagai root) berikut
[code language="bash"]#mlabel -s z:[/code]
untuk kasus komputer saya,maka setelah menjalankan perintah tersebut akan keluar peringatan seperti di bawah ini
```
Total number of sectors not a multiple of sectors per track!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test
```
nah, jika keluar peringatan seperti itu,tinggal kita tambahkan kode
[code language="bash"]#mtools_skip_check=1[/code]
di akhir file mktools.conf yang ada di /etc tadi,
setelah itu,maka jika saya melakukan perintah
```bash
#mlabel -s z:
```
maka akan tampil output seperti berikut
```
Volume label is USB_XP
```
jika tampil informasi nama volume label,maka perintah mlabel bisa dipergunakan dengan semestinya :p

berikut tambahan informasi tentang mlabel:

1. Untuk mengganti volume label
```bash
#mlabel z:"Nama_Baru"
```
2. Untuk menghapus volume label yang ada
```bash
#mlabel -c z:
```

untuk fungsi-fungsi lainnya bisa dilihat di manpage dari mlabel itu sendiri...

terimakasih telah berkunjung dan membaca tulisan ini :D
