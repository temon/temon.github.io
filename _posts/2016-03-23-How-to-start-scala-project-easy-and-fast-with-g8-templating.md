---
layout: post
title: "How to start scala project easy and fast with g8 templating"
description: "g8 templating for starting scala project, how to"
modified: {}
category: articles
tags: 
  - scala, g8 templating
image: 
  feature: "so-simple-sample-image-1.jpg"
  credit: temon ehm
  creditlink: "http://tmon.co"
comments: true
share: true
published: true
---

Banyak ide dikepala menuntut kamu untuk lebih cepat dalam memulai sebuah project scala. Jika kamu masih membuat folder2 satu per satu, memikirkan paket apa saja yang dipakai, dan gimana pattern2 yang sering kamu pakai, tentu akan terasa lambat dan ribet.

Ada yang membuat bash script untuk pembuatan struktur folder2 yang akan kita butuhkan. seperti di artikel berikut ini.

Namun ada cara yang lebih dinamis dan yang lebih cepat. Kita bisa munggunakan templating g8. Kamu bisa lihat detail nya disini : 


Ada list g8 template yang bisa kamu pakai langsung, tinggal dipilih saja yang mana yang sesuai kebutuhan kamu. Tapi bagi kamu yang ingin membuat template sendiri, gampang kok. (https://github.com/n8han/giter8/wiki/giter8-templates)

Pertama install cs, install g8 nya seperti dibawah ini : 

{% highlight bash linenos %}
$ curl https://raw.githubusercontent.com/n8han/conscript/master/setup.sh | sh

$ cs n8han/giter8
{% endhighlight %}

langkah pertama clone template default aja, habis itu kamu bisa modifikasi default.properties dan struktur folder sesuai dengan kemauan kamu.

{% highlight bash linenos %}
$ g8 n8han/giter8
{% endhighlight %}

saya coba buat template untuk internal project2 saya, disini (https://github.com/temon/griya-basic.g8)

thanks, semoga membantu.
