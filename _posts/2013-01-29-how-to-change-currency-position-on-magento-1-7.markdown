---
layout: post
status: publish
published: true
title: How to change currency position on Magento 1.7
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 514
wordpress_url: http://www.davidmataro.com/?p=514
date: !binary |-
  MjAxMy0wMS0yOSAyMDo1NToyMyArMDAwMA==
date_gmt: !binary |-
  MjAxMy0wMS0yOSAxODo1NToyMyArMDAwMA==
tags:
- magento
comments: []
---
<p>Magento 1.7 use the currency format of Zend Framework. To change currency format, you have edit the locale xml file located into the directory lib/Zend/Locale/Data</p>
<p>For example, to pot the currency symbol after price, you have edit file es.xml and change:</p>
<p>&lt;currencyFormats&gt;<br />
&lt;currencyFormatLength&gt;<br />
&lt;currencyFormat&gt;<br />
&lt;pattern&gt;¤ #,##0.00&lt;/pattern&gt;<br />
&lt;/currencyFormat&gt;<br />
&lt;/currencyFormatLength&gt;<br />
&lt;unitPattern count="other"&gt;{0} {1}&lt;/unitPattern&gt;<br />
&lt;/currencyFormats&gt;</p>
<p>by:</p>
<p>&lt;currencyFormats&gt;<br />
&lt;currencyFormatLength&gt;<br />
&lt;currencyFormat&gt;<br />
<strong>             &lt;pattern&gt;#,##0.00 ¤&lt;/pattern&gt;</strong><br />
&lt;/currencyFormat&gt;<br />
&lt;/currencyFormatLength&gt;<br />
&lt;unitPattern count="other"&gt;{0} {1}&lt;/unitPattern&gt;<br />
&lt;/currencyFormats&gt;</p>
<div>The symbol ¤ represents the currency symbol.</div>
<div></div>
<div>Remember clear the magento caches after change de xml file.</div>
<p>&nbsp;</p>
