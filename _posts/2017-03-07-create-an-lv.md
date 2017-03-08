---
layout: post
title: create an lv
---

```bash
# pvcreate /dev/sda1 /dev/sdb1
# vgcreate foovg /dev/sda1 /dev/sdb1                                              
# lvcreate -L 2G -n foo foovg                                                  
# mkfs.ext3 /dev/foovg/foo                                                       
# mount /dev/foovg/foo /mount_point
```
