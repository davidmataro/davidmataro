---
layout: post
status: published
published: true
title: Backup elasticsearch with curator
excerpt: How to protect your Elasticsearch data with backups usgin curator.
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
tags: [elk,elasticsearch]
comments: []
dark: false
---

[Elasticsearch](https://www.elastic.co) have a snapshot and restore API to create snapshots of individual indices or an entire cluster into a remote repository.

Next, how to configure a [elasticsearch](https://www.elastic.co) repository and run backups with [curator](https://www.elastic.co/guide/en/elasticsearch/client/curator/index.html). [curator](https://www.elastic.co/guide/en/elasticsearch/client/curator/index.html) is an index management for [elasticsearch](https://www.elastic.co).



### Configure path.repo in elasticsearch.yml

Edit /etc/elasticsearch/elasticsearch.yml and add next configuration:

```bash
path.repo: ['/mnt/logbackup']
```


### Create repository in elasticsearch

Create repository using curator:

```bash
es_repo_mgr --debug --host 127.0.0.1 create fs --repository bck --location /mnt/logbackup --compression true
```

Create repository using curl:

```bash
curl -XPUT 'localhost:9200/_snapshot/logbackup' -d '
{
    "type": "fs",
    "settings": {
        "location": "/mnt/logbackup",
        "compress": true
    }
}'
```

### List elasticsearch repositories

List elasticsearch repositories using curator:

```bash
es_repo_mgr show
```

List elasticsearch repositories using curl:

```bash
curl -GET 'localhost:9200/_snapshot/_all?pretty'
```


### Create a snapshot with curator of all indices


```bash
curator snapshot --repository logbackup indices --all-indice
```
