---
layout: post
title: mount s3 bucket on mac
---

```bash
# brew update
# brew install Caskroom/cask/osxfuse
# brew install homebrew/fuse/s3fs
# touch ~/.passwd-s3fs # access_key:secret_key goes in here
# chmod 600 ~/.passwd-s3fs
# s3fs bucket-name ~/bucket-name -o uid=<yourid>,umask=077,gid=<yourid>
```
