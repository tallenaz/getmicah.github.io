---
layout: post
title: disable puppet agent
---

Puppet runs as a service, and it maintains an agent. You can stop the service, or disable the agent if you need to quiet Puppet for a bit. Disabling the agent is advantageous, as it lets you send a message, which can help inform others as to why Puppet is off.

```bash
# puppet agent --disable 'Puppet is off for reasons'
# puppet agent --test
Notice: Skipping run of Puppet configuration client; administratively disabled (Reason: 'Puppet is off for reasons');
Use 'puppet agent --enable' to re-enable.
```
