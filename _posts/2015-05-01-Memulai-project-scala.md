---
layout: post
title: "Memulai Project Scala"
description: "SBT get started for scala project"
modified: {}
category: articles
tags: 
  - sample post
image: 
  feature: "so-simple-sample-image-1.jpg"
  credit: Michael Rose
  creditlink: "http://mademistakes.com"
comments: true
share: true
published: true
---

Karena ada partner baru dan project baru tentunya, maka sepertinya perlu nulis sedikit tentang sbt. Pertama install sbt, pake port aja enak.

sudo port install sbt

Misalkan koneksi terputus di tengah2 waktu installasi, pas mau install lagi kemungkinan akan error terus. harus di clean dulu port nya.

sudo port clean —all sbt 

Satu lagi biar kerja bersama partner berjalan seirama, editor pun harus sama. Milih kensana-kemari sepertinya intelj Idea paling cocok, untuk mempermuda build new projectnya pake sbt aja. Install plugin sbt dulu namanya sbt gen-idea. Tambahin baris ini ke ~/.sbt/0.13/plugins/build.sbt punyamu.

addSbtPlugin("com.github.mpeltonen" % "sbt-idea" % "1.6.0”)

Nah selesai, gampangkan tinggal buat folder project2nya, masuk ke foldernya, tinggal ketik 

sbt gen-idea

Buka intelj Idea mu, pilih open project. Yang blom punya editornya ada dimari pilih yg community edition aja yg gratisan. https://www.jetbrains.com/idea/download/
