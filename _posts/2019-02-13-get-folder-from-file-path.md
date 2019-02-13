---
layout: post
comments: ture
title: "[Shell] How to extract directory path and file name from file path using sed"
description: "[Shell] How to get directory from file path using sed"
categories: [Shell Script]
tags: [Script, Shell, Bash, sed, folder, file, path, directory]
redirect_from:
  - /2019/02/13/
---

* Kramdown table of contents
{:toc .toc}

# Extract directory path
``` bash
function extract_directory_path() {
    echo "${1}" | sed -r "s/(.+)\/.+/\1/"
}

FILE_PATH=/test/test/test/asdf.txt
RES=`extract_directory_path ${FILE_PATH}`

echo RES
```
# Extract file name
``` bash
function extract_file_name() {
    echo "${1}" | sed -r "s/.*\///"
}

FILE_PATH=/test/test/test/asdf.txt
RES=`extract_file_name ${FILE_PATH}`

echo RES
```