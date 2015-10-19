---
layout: post
status: publish
published: true
title: How to add search form in Magento header template?
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 501
wordpress_url: http://www.davidmataro.com/?p=501
date: !binary |-
  MjAxMi0xMS0wMSAwMDowNjowNiArMDAwMA==
date_gmt: !binary |-
  MjAxMi0xMC0zMSAyMjowNjowNiArMDAwMA==
tags:
- magento
comments: []
---
<p>To add search form in Magento header, you need modify the header layout. To do it, you need edit the file app/design/frontend/default/<your theme>/layout/catalogsearch.xml and add next code:</p>
<p><code width="550"><br />
<reference name="header"><br />
            <block type="core/template" name="top.search" as="topSearch" template="catalogsearch/form.mini.phtml"/><br />
        </reference><br />
</code></p>
<p>Remember clear Magento caches to view the changes.</p>
