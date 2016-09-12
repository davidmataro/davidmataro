---
layout: post
status: draft
published: true
title: Web performance testing with siege
excerpt: How to run a web performance test across all url's of your website using siege.
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: ['wpo']
comments: []
dark: false
---


Each website owner or manager should be the question: how many users can our website handler? To answer this question you need to run a *web performance testing* over your website. To run a *web performance testing* there are a lot tools and online services. For run the first web performance testings I use *siege*. Siege is an http load testing and benchmarking utility.



Siege permit to test a single url or a list of url's. I use siege to test a list of url randomly and with the benchmark option enable to stress the website infrastructure.


1.- Generate url list file

```bash
curl --silent http://test.superpop.es/sitemap.xml | grep \<loc\> | sed 's/.*<loc>//' | sed 's|</loc>||' > urllist.txt
```



2.- Run test with siege

```bash
siege -c5 -i -b -v -t60 -f urllist.txt
```

* -c CONCURRENT users, default is 10.
* -i INTERNET user simulation, hits URLs randomly.
* -b BENCHMARK: no delays between requests.
* -v VERBOSE, prints notification to screen.
* -t TIMED testing where "m" is modifier S, M, or H.
* -f FILE, select a specific URLS FILE.


If you have more than one sitemap.xml you can generate url list using the next script. This generate url list file from sitemap_index.xml.

```bash
#!/bin/bash

DOMAIN=test.superpop.es
SITEMAP_INDEX=sitemap_index.xml
URLLIST=urllist.txt

curl --silent http://$DOMAIN/$SITEMAP_INDEX | grep \<loc\> | sed 's/.*<loc>//' | sed 's|</loc>||' > /tmp/sitemap_index.txt

if [ -f $URLLIST ]
then
  rm $URLLIST
fi
touch $URLLIST

while read sitemap; do
  echo $sitemap
  curl --silent $sitemap | grep \<loc\> | sed 's/.*<loc>//' | sed 's|</loc>||' >> $URLLIST
done < /tmp/sitemap_index.txt

rm /tmp/sitemap_index.txt
```
