---
layout: post
title: draining swap
---

On CentOS6, run this with `nohup` or `screen`, as it can take a while:

```bash
sync && /sbin/sysctl vm.drop_caches=3 && swapoff -a && swapon -a
```
