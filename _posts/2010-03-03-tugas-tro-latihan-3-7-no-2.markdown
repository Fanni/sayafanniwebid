---
author: saya
comments: true
date: 2010-03-03 07:03:44+00:00
layout: post
link: http://sayafanni.web.id/?p=65
slug: tugas-tro-latihan-3-7-no-2
title: Tugas TRO latihan 3.7 no. 2
wordpress_id: 65
categories:
- Kuliah
tags:
- tugas
---

Lanjutan dari Tugas TRO no.3....

soal:


<blockquote>
Persamaan matematis suatu program linier adalah sebagai berikut:
Minimasi: **Z = 6X1 + 7,5X2**
dengan pembatas:
**
7X1 + 3X2 ≥ 210
6X1 + 12x2 ≥ 180
4X2 ≥ 120
X1 , X2 ≥ 0
**
Carilah harga X1 , X2
</blockquote>



<!-- more -->
jawab :
`Z = 6X1 + 7,5X2` (minimasi)
` -Z = -6X1-7,5X2` (diubah menjadi maksimasi)
persamaan dalam bentuk kanonik:
`
Z - 6X1 - 7,5X2 = 0.....(baris 0)
7X1 + 3X2 - S1 = 210.....(baris 1)
6X1 + 12x2 - S2 = 180.....(baris 2)
4X2 - S3 = 120.....(baris 3)
`
nonBasisVariabel(nBV) yang paling kecil adalah X2,
rasio terkecil adalah persamaan pada baris ke-2 dengan rasio 15,
Konversi koefisien nBV X2 baris 2 menjadi 1:
`
6X1 + 12x2 - S2 = 180     |:12|     0,5x1 + x2 - 1/12s2 = 15
`
Konversi koefisien nBV X2 baris lainnya menjadi 0:
baris 0
`
Z - 6X1 - 7,5X2 = 0     |x8|     8Z - 48X1 - 60X2 = 0
6X1 + 12x2 - S2 = 180     |x5|     30X1 + 60x2 - 5S2 = 900
------------------------------------------------------------------------ +
8Z - 18X1 - 5S2 = 900
`
baris 1
`
7X1 + 3X2 - S1 = 210     |  |     7X1 + 3X2 - S1 = 210
6X1 + 12x2 - S2 = 180     |:4|     6/4X1 + 3X2 - 1/4S2 = 45
-------------------------------------------------------------- -
5,5X1 - S1 + 1/4S2 = 165
`
baris 3
`
6X1 + 12x2 - S2 = 180     |:3|     2X1 + 4X2 - 1/3S2 = 60
4X2 - S3 = 120     |  |     4X2 - S3 = 120
------------------------------------------------------------ -
-2X1 + 1/3S2 - S3 = 60
`
Bentuk kanonik baru :
`
8Z - 18X1 - 5S2 = 900.....(baris 0)
5,5X1 - S1 + 1/4S2 = 165.....(baris 1)
0,5x1 + x2 - 1/12s2 = 15.....(baris 2)
-2X1 + 1/3S2 - S3 = 60.....(baris 3)
`
nonBasisVariabel(nBV) yang paling kecil adalah X1,
rasio terkecil adalah persamaan pada baris ke-3 dengan rasio -30,
Konversi koefisien nBV X1 baris 3 menjadi 1:
`
-2X1 + 1/3S2 - S3 = 60     |:-2|    X1 - 1/6S2 - 1/2S3 = -30
`
Konversi koefisien nBV X1 baris lainnya menjadi 0:
baris 0
`
8Z - 18X1 - 5S2 = 900     |  |     8Z - 18X1 - 5S2 = 900
-2X1 + 1/3S2 - S3 = 60    |x9|    -18X1 + 3S2 - 9S3 = 540
------------------------------------------------------------ -
8Z - 8S2 + 9S3 = 360
`
baris 1
`
5,5X1 - S1 + 1/4S2 = 165     |x4|     22X1 - 4S1 + S2 = 660
-2X1 + 1/3S2 - S3 = 60     |x11|     -22X1 + 11/3-11S3 = 660
------------------------------------------------------------------- +
-4S1 + 14/3S2-11S3 = 1320
`
baris 2
`
0,5x1 + x2 - 1/12s2 = 15     |x4|     2X1 + 4X2 - 1/3S2 = 30
-2X1 + 1/3S2 - S3 = 60     |  |     -2X1 + 1/3S2 - S3 = 60
------------------------------------------------------------ +
4X2 - S3 = 90
`
Bentuk kanonik baru :
`
8Z - 8S2 + 9S3 = 360
-4S1 + 14/3S2-11S3 = 1320
4X2 - S3 = 90
X1 - 1/6S2 - 1/2S3 = -30
`

karena tidak ada nBV bernilai negativ di baris 0, maka persamaan diatas adalah solusi optimumnya


mohon maaf kalo salah, kalo salah tolong bantu memperbaiki..hehehehe..makasih,,
