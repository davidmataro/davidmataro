---
layout: post
status: publish
published: true
title: How to list size of all tables of a mysql database
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 563
wordpress_url: http://www.davidmataro.com/?p=563
date: !binary |-
  MjAxNC0wOS0yMyAxNToyOTo0NyArMDAwMA==
date_gmt: !binary |-
  MjAxNC0wOS0yMyAxMzoyOTo0NyArMDAwMA==
tags:
- mysql
comments: []
---
<p>List the size of all tables for a mysql database:</p>
<p><code><br />
SELECT table_name AS "Table",  round(((data_length + index_length) / 1024 / 1024), 2) as TEST   FROM information_schema.TABLES  WHERE table_schema = "cellercandani"  order by TEST;<br />
</code></p>
