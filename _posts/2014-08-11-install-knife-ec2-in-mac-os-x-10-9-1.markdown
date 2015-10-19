---
layout: post
status: publish
published: true
title: Install knife-ec2 in Mac OS X 10.9.1
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 556
wordpress_url: http://www.davidmataro.com/?p=556
date: !binary |-
  MjAxNC0wOC0xMSAyMjozMjozMyArMDAwMA==
date_gmt: !binary |-
  MjAxNC0wOC0xMSAyMDozMjozMyArMDAwMA==
tags:
- ec2
- knife
- chef
comments: []
---
<p>To install knife-ec2 on Mac OS X 10.9.1 run the next command:</p>
<p><code><br />
sudo /opt/chef/embedded/bin/gem install knife-ec2<br />
</code><br />
and add in your .bash_profile<br />
<code><br />
export PATH=/opt/chef/embedded/bin:$PATH<br />
</code></p>
