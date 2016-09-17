---
layout: post
title: composite primary keys in rails
---

I'm working on a rails project where I have to model a search. Rails sits on top of a pre-existing database that many other things connect to, so we are trying to touch the db as little as possible. The table for searches has two primary keys: a user name, and the name of the search. The user name is always available once the user logs in, and the user names the search upon creation. Also, in the existing test data, more often than not, the search name distinguished one search from another. Because of those two reasons, I decided to start off by taking just the search name as the primary key:

``` ruby
  self.primary_key: 'search_name'
```

Everything went well untill I noticed that when I tried to delete a particular user's search that happened to have the same name as another user's search, rails would delete both searches.

After some research, I found a gem called [composite-primary-keys](https://github.com/composite-primary-keys/composite_primary_keys), which sharpened the vague thought I had that you couldn't have more than one primary key for an object in rails. Installing the gem gave me a way to configure multiple primary keys:

``` ruby
  self.primary_keys: :user_name, :search_name
```

and gave rails a way to reliably find the object by both keys:

``` ruby
  Search.find(['foo', 'bar'])
```

I'm guessing that the order of array elements matters for how the gem extends the `ActiveRecord` `find` method.

