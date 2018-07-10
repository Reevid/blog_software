---
layout: post
comments: ture
title: "Remove all docker container"
description: "Remove all docker container"
categories: [Docker]
tags: [Docker, Container, Delete]
redirect_from:
  - /2018/07/10/
---

* Kramdown table of contents
{:toc .toc}

# 1. Remove all docker container
{% highlight docker %}
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
{% endhighlight %}