---
layout: post
comments: ture
title: "[Shell] How to get directory from file path using sed"
description: "[Shell] How to get directory from file path using sed"
categories: [Shell Script]
tags: [Script, Shell, Bash, sed, folder, file, path]
redirect_from:
  - /2019/02/13/
---

* Kramdown table of contents
{:toc .toc}

``` bash
function get_dir() {
    echo "${1}" | sed -r "s/(.+)\/.+/\1/"
}

FILE_PATH=/test/test/test/asdf.txt
RES=`get_dir ${FILE_PATH}`

echo RES
```