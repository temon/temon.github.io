---
layout: post
title: "Liftweb dan Mongodb Menggunakan Salatdao"
description: "Liftweb with mongodb using salatdao example"
modified: {}
category: articles
tags: 
  - liftweb
  - salatdao
  - mongodb
  - sbt
image: 
  feature: "so-simple-sample-image-1.jpg"
  credit: temonehm
  creditlink: "http://tmon.co"
comments: true
share: true
published: true
---

Sebelumnya hanya bicara soal start project scala menggunakan sbt, kali ini mencoba membuat simple apps yang memakai mongodb. Kebetulan saya sudah terbiasa memakai liftweb dari pada play framework yang sebenarnya malah di support langsung oleh typesafe. Typesafe adalah perusahaan besar yang dibangun oleh Martin (creator of scala).

Lift sendiri menawarkan mapper sebagai orm ke database termasuk mongodb. Namun kali ini mencoba salatdao yang terlihat lebih ciamik. Untuk liftweb + mongodb menggunakan mapper akan saya bahas lain kesempatan. :D

tambahkan dependency ini di build file anda, 

"com.novus"         %% "salat"                         % "1.9.9"

Langsung saja, kita buat model yang extend dari class salat punya.

{% highlight scala linenos %}
case class CategoryDAO (_id: ObjectId = new ObjectId,
                     name: String,
                     displayName: String,
                     parent: String) {
}
object CategoryDAO extends SalatDAO[CategoryDAO, ObjectId] (collection= MongoConnection()("simple")("category")) {
}
{% endhighlight %}

simple merupakan nama database sedangkan category adalah nama collectionnya. Simple kan, selanjutnya kita buat contoh untuk insert nya, menggunakan model yang sudah ada.

{% highlight scala linenos %}
    val entry = CategoryDAO(name = name,
      displayName = displayName,
      parent = parent
    )

    val id = CategoryDAO.insert(entry)
{% endhighlight %}

Untuk updatenya juga mudah.

{% highlight scala linenos %}
        val entry = CategoryDAO(new ObjectId(data._id), data.name, data.displayName, data.parent)

        val result = CategoryDAO.update(MongoDBObject("_id" -> new ObjectId(data._id)), entry, false, false, new WriteConcern)
{% endhighlight %}

Untuk query memang tidak secantik rogue punya, tp sudah lebih dari cukup.

{% highlight scala linenos %}
CategoryDAO.find(ref = MongoDBObject(filter))
        .skip(offset)
        .limit(limit)
        .toList, categoryCount
{% endhighlight %}

Dan yang terakhir kita coba untuk deletenya.

{% highlight scala linenos %}
CategoryDAO.removeById(new ObjectId(id))
{% endhighlight %}


Nah itu sedikit share saja, semoga bisa menjadi gambaran jika mau memilih salatdao dan liftweb.
