---
author: saya
comments: true
date: 2010-03-03 00:54:00+00:00
layout: post
link: http://sayafanni.web.id/?p=25
slug: modem-huawei-e-1550-di-slackware
title: Modem Huawei e 1550 di slackware
wordpress_id: 25
categories:
- Slackware
tags:
- Slackware
---

Beberapa hari yang lalu saya membeli modem baru dengan merek Huawei tipe e 1550 yang memiliki 3 mode pada satu perangkat, yaitu mode perangkat sebagai modem, mode perangkat sebagai microSD reader stick dan mode CD driver sebagai mode utama saat pertama kali dijalankan. Dengan harga yang murah dibandingkan dengan modem-modem sejenisnya, modem ini lumayan juga fitur-fitur yang dimilikinya (lho kok promosi..hehe)....
Langsung aja abis beli, terus dicoba di komputer rumah yang bernyawakan slackware 12.2 dengan kernel 2.6.29.6,pas dicolok... waduh..ko kedeteknya sebagai Memori storage sih??alias MicroSD card reader, padahal di Windows mah ga masalah, cuman pas saya colok di komputer dengan OS Slackware, masalahnya muncul, pas di jalanin perintah [code language="bash"]dmesg[/code]
modemnya itu malah kebaca sebagai sekeping CD plus media storage, mode perangkat sebagai modemnya itu ga ada...oh iya modem itu mempunyai 3 mode perangkat,
<!-- more -->
1.mode perangkat sebagai microSD reader
2.mode perangkat sebagai modem
3.mode perangkat sebagai sekeping CD driver(di autorun di Windows)

Nah karena udah tau masalah dasarnya akhirnya nyari (kalo udah jagoan kayaknya bisa bikin sendiri programnya..hehehe) program yang bisa nge-switch mode perangkat itu di linux..kebanyakan sih buat ubuntu (catatan : buat ubuntu install aja pake udev extras-nya terus tinggal tambahin rulenya..)

untung ketemu,, buat slackware langkah pertama donlot toolnya di [sini](http://www.draisberghof.de/usb_modeswitch/usb-modeswitch-1.1.0.tar.bz2) sebenernya di situsnya juga udah ada langkah-langkahnya..tapi saya coba jelasin disini
abis donlot, kita extrak paketnya misalkan donlotannya ada di /home/cheburashka
[code language="bash"]tar jxf usb-modeswitch-1.1.0[/code],
udah di ekstrak terus masuk ke direktori itu
[code language="bash"]cd usb-modeswitch-1.1.0[/code],
langkah 1 (di
terus sebagai root kita jalanin perintah
[code language="bash"]make install[/code],
ntar otomatis file usb-modeswitch.conf disimpen di /etc dan suatu rule yang namanya 80-usb_modeswitch.rules disimpen di /etc/udev/rules.d/, langkah selanjutnya
kita edit file usb_modeswitch, cari section huawei e1550 terus uncomment opsi-opsinya atau tambah opsi yang tidak ada sehingga section huawei e1550 di file usb-modeswitch.conf seperti ini
[code]
########################################################
# Huawei E1550
# Huawei E1750
#
# Contributor: Anders Blomdell, Ahmed Soliman

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

;TargetVendor=   0x12d1
;TargetProduct=  0x1001

# only for reference and 0.x versions
MessageEndpoint="0x01"

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

;DetachStorageOnly=1
;HuaweiMode=1
[/code]


terus file 80-usb_modeswitch.rules yang ada di /etc/udev/rules.d (pada kasus saya) dihapus saja karena walaupun saya menambahkan rule untuk huawei e1550, tetap saja huawei e1550 saya tidak terdetek sebagai modem,
sebagai gantinya saya membuat suatu rule baru dengan nama huawei-e1550.rules yang isinya sebagai berikut

[code]
ACTION=="add" SUBSYSTEM=="usb", SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1", RUN+="/usr/sbin/usb_modeswitch"
[/code]

terus simpan di /etc/udev/rules.d

setelah itu restart rc.udev-nya dengan perintah berikut
[code language="bash"]/etc/rc.d/rc.udev restart[/code]

saat dikonekkan, huawei e1550-nya terdeteksi sebagai modem, (potongan dikutip dari perintah dmesg sesaat setelah modem dikonekkan)
[code]
usb_storage: module is already loaded
usb_storage: module is already loaded
usb 1-1: new high speed USB device using ehci_hcd and address 4
usb 1-1: New USB device found, idVendor=12d1, idProduct=1001
usb 1-1: New USB device strings: Mfr=2, Product=1, SerialNumber=0
usb 1-1: Product: HUAWEI Mobile
usb 1-1: Manufacturer: HUAWEI Technology
usb 1-1: configuration #1 chosen from 1 choice
usb-storage: probe of 1-1:1.0 failed with error -5
usb-storage: probe of 1-1:1.1 failed with error -5
usb-storage: probe of 1-1:1.2 failed with error -5
usb-storage: probe of 1-1:1.3 failed with error -1
usb-storage: probe of 1-1:1.4 failed with error -1
usb_storage: module is already loaded
usb_storage: module is already loaded
usb_storage: module is already loaded
usb_storage: module is already loaded
usbcore: registered new interface driver usbserial
USB Serial support registered for generic
usbcore: registered new interface driver usbserial_generic
usbserial: USB Serial Driver core
usb_storage: module is already loaded
USB Serial support registered for GSM modem (1-port)
option 1-1:1.0: GSM modem (1-port) converter detected
usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
option 1-1:1.1: GSM modem (1-port) converter detected
usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
option 1-1:1.2: GSM modem (1-port) converter detected
usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
usbcore: registered new interface driver option
option: v0.7.2:USB Driver for GSM modems
usb_storage: module is already loaded
usb_storage: module is already loaded
[/code]

jika tampak keluaran diatas setelah melakukan perintah dmesg, maka prosesnya telah berhasil, selamat mencoba :^)
