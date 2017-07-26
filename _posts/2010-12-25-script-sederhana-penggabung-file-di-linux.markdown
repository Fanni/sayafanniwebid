---
author: saya
comments: true
date: 2010-12-25 13:29:13+00:00
layout: post
link: http://sayafanni.web.id/?p=241
slug: script-sederhana-penggabung-file-di-linux
title: script sederhana penggabung file di Linux
wordpress_id: 241
categories:
- Programming
- Python
tags:
- python
---

kemaren-kemaren saya posting tentang script sederhana pemecah file besar menjadi beberapa file kecil,,nah di postingan ini saya akan menuliskan script sederhana yang menggabungkan file-file pecahan tadi..dengan bahasa python...sekali lagi ini cuman script sederhana yang punya banyak sekali kelemahan...jadi bisa dikembangkan lagi oleh pembaca. Ini dia kodenya :
<!-- more -->
[code language="python"]
#!/usr/bin/env python

#script sederhana penggabung file

import sys

def main():
    if len(sys.argv) &gt; 2:
        try:
            #pertama buka file, file pertama akan menjadi file hasil penggabungan
            fout = open(sys.argv[1],'wb')

            #untuk setiap parameter ke dua dan seterusnya akan dibuka satu per satu, lalu dibaca, kemudian ditulis dan digabungkan dengan
           #file pertama

           for i in sys.argv[2:]:
               fin = open(i,'rb')
               while 1:
                   #membaca file per 8kb
                     buffer = fin.read(8*1024)
                     fout.write(buffer)
                     if not buffer:
                         break
               #tutup tiap file yang digabung setelah selesai dibaca
               fin.close()
           fout.close()
       except IOError, msg:
           sys.exit(msg)
    else:
        sys.exit('wew ga ngelakuin apa-apa')

if __name__ == '__main__':
    main()
[/code]

**kelemahan :**
script ini menggabungkan file berdasarkan urutan , hal ini mengakibatkan kesalahan dalam memberikan urutan akan berujung pada salah penggabungan.

terimakasih telah membaca :)

