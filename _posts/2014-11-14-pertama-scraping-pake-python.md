---
layout: post
title: "Pertama Scraping pake Python"
description: "Karena hidup itu indah pada waktunya"
modified: {}
category: articles
tags: 
  - python
image: 
  feature: "so-simple-sample-image-1.jpg"
  credit: Michael Rose
  creditlink: "http://mademistakes.com"
comments: true
share: true
published: true
---

Kemaren iseng mau niru2 scraping kayak temen-temen yang sudah biasa manen. Karena lagi bosen dengan php, coba mencari-cari scraping yang memakai python. Dan alhamdulilah akhirnya ketemu juga scapy (framework scraping pake python). Sebenernya ga bisa-bisa banget pemrograman python, tapi ya ga pa-pa. Asal running dan jadi saja.


Setelah saya implemen dan saya jalankan di server gratisan digital ocean(kemaren register paket student yang dapet $100 credit di digital ocean dan beberapa gratisan lainya), saya mendapatkan beberapa kendala. Saya pengen menggunakan mongodb untuk menyimpan data hasil scraping, ya walaupun saya pernah sekilas baca mongodb tidak cocok untuk penyimpanan hasil scraping. Tapi tidak mengapa lah, dari pada saya memakai mysql db. Yang saya ambil dari scraping kebetulan tidak hanya data text nya saja, saya menyimpan file gambarnya juga.


Tentu storage di digitalocean menjadi sebuah masalah, maka dari itu saya mencari cloud storage yang murah, servernya local di indonesia, dan terjamin supportnya. Mutusin pake cloudkilat yang 50gb/bulan harganya 99rb sudah termasuk pajak. Dan akhirnya sekarang sudah saya upgrade ke 100gb/bulan dengan harga 165rb karena gambarnya membludak juga.


Masalah lainya adalah dari domain yang tak scrape, ternyata aksesnya dibatesin juga. Setelah coba mencoba, amanya adalah delay 1 detik per aksesnya. Ternyata lama juga kalau ngandelin 1 spider saja. Mencoba pakai scrpyd untuk management jobsnya, saya jalankan beberapa spider sekali waktu dan untuk server digital ocean yang 1core/1gbram hanya kuat 3 proses *cari aman*.


Selain masalah delay, ada masalah spider saya diblok ip nya. Solusinya saya beli dedicated proxy, per ip $1 (saya beli 10). Sebenarnya tidak perlu yang dedicated proxy, tp sekalian nyobain ga papa =)).

sekian terima kasih, yang hobi manen memanen monggo komentar.
