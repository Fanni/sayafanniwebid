---
author: saya
comments: true
date: 2011-04-01 03:47:30+00:00
layout: post
link: http://sayafanni.web.id/?p=225
slug: inputantanpaech
title: inputan tanpa echo
wordpress_id: 225
categories:
- Programming
- Python
tags:
- python
---

kadang kepikiran juga sih gimana caranya nangkep inputan user tapi apa yang diketikin user itu tidak tampak di layar monitor..kayak wakti kita input password di shell. Untung bisa nemu caranya..hehe, caranya bisa pake module _getpass_ yang ada di Python.
Ayo kita coba mulai 

[code language="python"]
>>>import getpass
>>> p = getpass.getpass(getpass.getuser() + ''s password: ')
ontel's password:
>>> p
'apaan tuh'
>>>
[/code]

keterangan : getpass.getuser() itu buat nangkep nama user yang sedang "berkeliaran" di shell yang aktif
mungkin kode di atas bisa dikembangkan lagi jadi semacam fake login mungkin ( :D )

selamat mencoba.. CMIIW :)
