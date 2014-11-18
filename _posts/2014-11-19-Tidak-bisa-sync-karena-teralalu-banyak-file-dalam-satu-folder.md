---
layout: post
title: "Tidak bisa sync karena teralalu banyak file dalam satu folder"
description: "Karena hidup itu indah pada waktunya"
modified: {}
category: articles
tags: 
  - cloud storate
  - s3cmd
image: 
  feature: "so-simple-sample-image-1.jpg"
comments: true
share: true
published: true
---

Melanjutkan dari proses scraping kemaren, kini waktunya memanen. Ternyata proses sync dari cloud storage (saya kemaren pake cloudkilat) tidak semudah biasanya. Karena ada kesalahan saat penyimpanan, saya menyimpan semua file hanya pada satu folder. dan...


Pertama saya tidak memakai s3cmd tapi dgsync. Saat memakai dgsync dapet error memoery leak di qtnya. Hijrah memakai s3cmd ternyata sama saja, errornya segmentation fault kalau ga gitu error karena aksesnya. Saya kurang tau apakah ini karena limitasi dari cloudkilatnya atau dari protokol s3nya, kemaren selalu error saat mencoba listing 280rb file dalam satu folder sebelum proses sync.


Tanya kesana kemari akhirnya, ada teman yang baik hati mau me mention kan temannya yg sering utakatik s3. Jadi ceritanya untuk mengakalinya, harus di sync satu2. Tapi sayang nya perlu kerja ekstra untuk ngelis nama2 file di sono. 


Maka solusinya saya pindah ke bebrapa folder, agar bisa di sync nantinya.

```bash
for i in {1000000..9999999}; do s3cmd ls s3://bucket/full/${i}-* | awk '{print $4 " s3://bucket/pisah/"}' | xargs s3cmd mv; done;
```

```bash
for i in {10000000..99999999}; do s3cmd ls s3://bucket/full/${i}-* | awk '{print $4 " s3://bucket/pisah/"}' | xargs s3cmd mv; done;
```

```bash
for i in {100000000..999999999}; do s3cmd ls s3://bucket/full/${i}-* | awk '{print $4 " s3://bucket/pisah/"}' | xargs s3cmd mv; done;
```



Nah begitu saja :D selamat pagi...
