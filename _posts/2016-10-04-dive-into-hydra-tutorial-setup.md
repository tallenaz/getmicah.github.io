---
layout: post
title: dive into hydra tutorial setup
---

This week, I'm at HydraConnect 2016. I was trying to work through the [Dive into Hydra](https://github.com/projecthydra/hydra/wiki/Dive-into-Hydra) tutorial, and ran into a hiccup or two.

The problem started when I tried to start up solr with [solr_wrapper](https://github.com/cbeer/solr_wrapper), which threw a 404. Just to try something, I checked the version number of the gem, and noticed that a later version was released than was in the tutorial. So, I upped the version, which led me to upping the version of the [hydra](https://github.com/projecthydra/hydra) gem.

``` ruby
gem 'hydra', '10.0.1' # from '10.0.0'
gem 'solr_wrapper', '0.15.0' # from '>= 0.3'
```

At this point, `solr_wrapper` was still complaining, but this time in a way that made more sense to my brain: I could see that it was trying to download solr 6.1 from a non-existent url. I looked around and saw that solr 6.2 was out. `solr_wrapper` lets you configure which version of solr to look for, so in `.solr_wrapper`

``` ruby
version: 6.2.0
```
at which point I was able to start solr, and fedora, and move on to the next step of the tutorial.
