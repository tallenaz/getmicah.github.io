---
layout: post
title: knowing when a puppet run is done
---

``` bash
$ puppet agent -t --noop --environment=my-env
Notice: Run of Puppet configuration client already in progress; skipping
(/var/lib/puppet/state/agent_catalog_run.lock exists)
$ tail -f /var/log/messages | grep 'Finished catalog run'
Nov 23 10:05:52 hostname puppet-agent[12345]: Finished catalog run in 123.45 seconds
```
