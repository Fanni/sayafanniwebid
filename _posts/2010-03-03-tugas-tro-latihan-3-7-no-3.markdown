---
author: saya
comments: true
date: 2010-03-03 00:46:14+00:00
layout: post
link: http://sayafanni.web.id/?p=41
slug: tugas-tro-latihan-3-7-no-3
title: Tugas TRO latihan 3.7 no.3
wordpress_id: 41
categories:
- Kuliah
tags:
- tugas
---

sudah lama ga nulis di blog............ini juga karena ada tugas yang harus diposting di blog jadi saya nulis lagi..hehehe,,langsung saja, ini tugas TRO halaman 75 nomor 3 buku Operation Research karya ibu Tjutju dan bapak Ahmad.

Soal :


<blockquote>PT Unilever bermaksud membuat 2 jenis sabun, yakni sabun bubuk dan sabun batang. Untuk itu dibutuhkan 2 macam zat kimia, yakni A dan B. Jumlah zat kimia yang tersedia adalah A = 200kg dan B = 360kg. Untuk membuat 1 kg sabun bubuk diperlukan 2kg A dan 6kg B. Untuk membuat 1kg sabun batang diperlukan 5kg A dan 3kg B. Bila keuntungan yang akan diperoleh setiap membuat 1kg sabun bubuk = $ 3 sedangkan setiap 1kg sabun batang = $ 2, berapa kg jumlah sabun bubuk dan sabun batang yang sebaiknya dibuat?</blockquote>


<!-- more -->
Jawab:
Misalkan Sabun Bubuk = x dan Sabun Batang = y
Fungsi tujuannya adalah `Z = 3x + 2y`
dengan fungsi pembatasnya adalah
`2x + 5y ≤ 200
6x + 3y ≤ 360`

setelah itu kita ubah persamaan diatas menjadi persamaan kanonik

`Z - 3x - 2y                  = 0
2x + 5y + S1         = 200
6x + 3y         + S2 = 360`

selanjutnya adalah menentukan nonBasis Variabel(nBV) paling negatif pada baris 0, yaitu nBV `-3x`
langkah selanjutnya adalah kita cari rasio untuk masing-masing baris (kecuali baris 0)
baris 1 --> `rasio = 200/2 = 100`
baris 2 --> `rasio = 360/6 = 60`

rasio terkecil adalah 60 pada baris 2, maka persamaan di baris 2 dijadikan patokan, lalu jadikan nBV (x)-nya menjadi satu,
`
6x + 3y + S2 = 360 |:6| x + 1/2y + 1/6S2 = 60
`


<blockquote>keterangan --> operasi |:6| maksudnya adalah persamaan di sebelah kirinya dibagi 6, dan persamaan di sebelah kanan adalah hasilnya</blockquote>


langkah selanjutnya adalah mengeliminasi nilai x lainnya,
baris ke-0
`
Z - 3x - 2y          = 0.....................................................(Persamaan 1)
6x + 3y + S2 = 360   |:2|   3x + 3/2y + 1/2S2 = 180............(Persamaan 2)
`
Selanjutnya persamaan 1 + persamaan 2 hasilnya
`Z - 1/2y + 1/2S2 = 180`

lalu baris ke - 1
`
2x + 5y + S1 = 200.................................................................(Persamaan 3)
6x + 3y + S2 = 360   |:3|   2x + y + 1/3S2 = 120..........(Persamaan 4)
`
Selanjutnya persamaan 3 - persamaan 4 hasilnya
`4x + S1 - 1/3S2 = 80`

Kita mempunyai bentuk persamaan baru setelah proses di atas, yaitu
`
Z - 1/2y + 1/2S2 = 180
4y + S1 + 1/3S2 = 80
x + 1/2y + 1/6S2 = 60
`

Karena masih ada nBV negatif di bars ke-0, maka kita ulangi langkah-langkah di atas terhadap bentuk persamaan baru yang tadi, berikut langkahnya

rasio terkecil yaitu baris 1 dengan nilai rasio 20 ( 80/4.....4y, y sebagai nBV yang paling negatif)
baris 1 nBV menjadi 1
`4y + S1 + 1/3S2 = 80   |:4|   y + 1/4S1 + 1/12S2 = 20`

baris 0 nBV menjadi 0
`Z - 1/2y + 1/2S2 = 180
4y + S1 + 1/3S2 = 80   |:8|   1/2y + 1/8S1 + 1/24S2 = 10`
ditambahkan dan hasilnya
`Z + 1/8S1 + 13/24S2 = 190`
lalu baris 2 nBV menjadi 0
`
x + 1/2y + 1/6S2 = 60
4y + S1 + 1/3S2 = 80   |:8|   1/2y + 1/8S1 + 1/24S2 = 10
`
dikurangkan dan hasilnya
`x - 1/8S1 + 3/24S2 = 50`
Maka diketahui bentuk baru dan solusi maksimumnya yaitu
`
Z + 1/8S1 + 13/24S2 = 190
y + 1/4S1 + 1/12S2 = 20
x - 1/8S1 + 3/24S2 = 50
`





sekian..mohon maaf kalo salah, tolong kasih tahu saya dan bantu benerinnya karna saya juga belum terlalu paham banget sama metode simplex ini..hehehe..terimakasih,,
