---
layout: post
title: certs for tomcat
---

You can front tomcat with apache, but say you have a pure tomcat machine. Figuring out how to load certs onto it has been tricky, but it's basically a two-step.

First, create a certificate keystore from a key and bundle:

``` bash
openssl pkcs12 -export -in foo.bar.org.crt -inkey foo.bar.org.key -out foo.p12 -name tomcat -CAfile foo.bar.org.ca-bundle -caname root -chain

```

Convert the resulting p12 bundle into a PKCS12 file, and use the keytool tool to merge one keystore with another one:

``` bash
keytool -importkeystore -deststorepass changeit -destkeystore foo.jks -srckeystore foo.p12 -srcstoretype PKCS12 -srcstorepass changeit
```

I worked this out from [here](https://jamfnation.jamfsoftware.com/article.html?id=138) and [here](http://cunning.sharp.fm/2008/06/importing_private_keys_into_a.html)
