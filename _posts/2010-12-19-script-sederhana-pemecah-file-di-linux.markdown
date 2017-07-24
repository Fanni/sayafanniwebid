---
author: saya
comments: true
date: 2010-12-19 10:06:11+00:00
layout: post
link: http://sayafanni.web.id/?p=249
slug: script-sederhana-pemecah-file-di-linux
title: Script sederhana pemecah file di Linux
wordpress_id: 249
categories:
- Programming
- Python
tags:
- python
---

malam ini saya pusing...pusing yang teramat sangat..(halah berlebihan), ngutak-ngatik Twitter API buat dapetin mention pake kode php, ribet karena saya baru kali ini berurusan ma API-nya Twitter..hehehe,,(maklum pemula dengan kemampuan koding yang terbatas). Oleh karena itu daripada berpusing-pusing ria dan akhirnya jadi gila, saya berniat nonton film ajah (film hasil donlotan...hhheheheee),,, dari situ saya agak penasaran dengan file yang bisa dipecah-pecah seperti ini..misalnya sayaganteng.rar.part1, sayaganteng.rar.part2 dan seterusnya....dari sana terpancarlah ilham untuk ngebuat script sederhana yang bisa memecah file ke ukuran-ukuran lebih kecil...keren kali yah kalo bisa bikin program kayak gitu...jadi saya urungkan niat untuk nonton film, lalu membuka Kate (text editor) ama konsole tentunya..karena saya bakal nyoba bikin pake Python Man!!!! heheheheee... hayoh kita mulai..

buat script kali ini kita harus mengimport module os dan sys, cek this code out :
<!-- more -->
[code language="python"]
#!/usr/bin/env python
#script pemecah file sangat sederhana
#17 Desember 2010

import sys
import os

def main():
    if len(sys.argv) == 3:
        try:
            # untuk pemecahan tiap file,akan dilakukan penambahan ekstensi (ext) berupa nomor,yang dimulai dari 0
            ext = 0
            # penentuan ukuran pembagian file,dimasukkan ke dalam splitSize
            splitSize = int(sys.argv[2])
            if os.stat(sys.argv[1])[6] <= splitSize:
                sys.exit('splitSize lebih besar atau sama dengan ukuran file')
            # membuka file yang akan dipecah
            fin = open(sys.argv[1],'rb')
            # selanjutnya melakukan perulangan,baca sebesar splitSize,kemudian tulis ke file pecahan dengan nama file+ekstensi urutan
            while 1:
                buffer = fin.read(splitSize)
                if not buffer:
                    break
                fout = open(sys.argv[1]+'.'+str(ext),'wb')
                fout.write(buffer)
                fout.close()
                # menambah urutan
                ext = ext + 1
        except (IOError,ValueError), msg:
            sys.exit(msg)
    else:
        sys.exit('Tidak ada yang dilakukan')
if __name__ == '__main__':
    main()
[/code]

Oh iya, ini hanyalah script, script ini mempunyai masalah, diantaranya masalah pembacaan file utama sebesar splitSize. Ini sedikit agak berbahaya jika ukuran splitSize sangat besar, tapi bisa diakali dengan pembacaan yang sedikit demi sedikit.
Oleh karena itu, mohon maaf kalo banyak kekurangannya, nanti lah kalo tugas-tugas kuliah sudah beres, insyaAllah saya akan memperbaiki dan membuat program lengkap dengan GUI-nya...hehehe doain aja..

Terimakasih udah baca :)
