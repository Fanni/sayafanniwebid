---
author: saya
comments: true
date: 2014-07-07 04:50:58+00:00
layout: post
link: http://sayafanni.web.id/?p=483
slug: openbox-dan-xmonad
title: OpenBox dan Xmonad
wordpress_id: 483
categories:
- Hobi
- Slackware
tags:
- Linux
- OpenBox
- Window Manager
- Xmonad
---

Beberapa hari ini, saya sedang tertarik dengan bermacam-macam Window Manager yang ada di linux. 2 WM yang menarik perhatian saya yaitu OpenBox dan Xmonad. Saya tertarik dengan keduanya karena melihat hasil modifikasi keduanya di internet :D

Keduanya sama-sama ringan dan simple. OpenBox merupakan floating WM, jenis Window Manager yang sudah sering saya gunakan di linux (ada dua yang sering sekali saya gunakan, yaitu kwin untuk kde dan xfwm untuk xfce) dan menggunakan xml pada file konfigurasinya.

<!-- more -->

Pada OpenBox terdapat 3 file konfigurasi yang utama, yaitu menu.xml yang berfungsi untuk mengatur list aplikasi dan layout list tersebut pada menu pop up, rc.xml yang lebih befungsi sebagai konfigurasi utama seperti pengaturan window, tema dan keybinding untuk aksi-aksi tertentu dan yang ketiga adalah autostart, file konfigurasi ini mengatur perintah apa saja yang akan dilakukan saat startup.

Berbeda dengan OpenBox, Xmonad merupakan window manager yang berjenis tiling. Window manager jenis ini baru saya "cicipi" :D . Tiling window manager merupakan jenis window manager yang akan mengatur layout window yang terbuka dengan otomatis.
Xmonad menggunakan bahasa pemrograman haskell pada file konfigurasinya, dan hal ini yang cukup menyulitkan saat pertama mengkonfigurasi window manager ini.

Untuk OpenBox, file konfigurasinya terletak di ~/.config/openbox sedangkan untuk Xmonad terletak di ~/.xmonad/xmonad.hs

Berikut hasil scrot dari slackware saya, pada OpenBox saya pakai conky, tint2 dan nitrogen. Sedangkan pada Xmonad saya memakai conky dan dzen2

-OpenBox-
[![OpenBoxSlackware](https://farm4.staticflickr.com/3861/14584960602_f2b9700d84.jpg)](https://www.flickr.com/photos/49546882@N06/14584960602)
-Xmonad-
[![XmonadSlackware](https://farm3.staticflickr.com/2937/14605786493_7872108cf5.jpg)](https://www.flickr.com/photos/49546882@N06/14605786493)

Untuk saat ini saya nyaman dengan Xmonad, karena saya tidak perlu mengatur posisi window-window yang terbuka, apalagi saat mengerjakan pekerjaan yang menggunakan banyak vim untuk ditampilkan di saat yang bersamaan :D

