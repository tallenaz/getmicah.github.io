---
layout: post
title: grep minus el
---

``` bash
$ cat foo_file.txt
foo
$ cat bar_file.txt
bar
$ grep -L foo *_file.txt
bar_file.txt
$ grep -L bar *_file.txt
foo_file.txt
```
