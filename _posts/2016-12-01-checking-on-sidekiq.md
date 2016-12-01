---
layout: post
title: checking on sidekiq
---

I'm setting up [sidekiq](https://github.com/mperham/sidekiq) for a rails app, and I noticed that jobs were hanging in the queue. To learn more about why:

Check whether `sidekiq` is running: `ps aux | grep sidekiq`

In my case, it wasn't running, so on the dev server:

`bundle exec sidekiq -e development`

which told me what the problem was:

```
WARN: {"context":"Job raised exception",
       "job": {"class":"MyWorker","args":[arg],
       "retry":true,"queue":"default",
       "jid":"some_jid","created_at":148,
       "enqueued_at":148,"error_message":"undefined method `my_method'
```

For some reason, `my_method` wasn't found.
