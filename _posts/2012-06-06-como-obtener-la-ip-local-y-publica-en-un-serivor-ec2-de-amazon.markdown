---
layout: post
status: publish
published: true
title: Como obtener la ip local y pública en un serivor EC2 de Amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 365
wordpress_url: http://www.davidmataro.com/?p=365
date: !binary |-
  MjAxMi0wNi0wNiAyMzo1MTo0MSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNi0wNiAyMTo1MTo0MSArMDAwMA==
tags:
- sysadmin
- aws
- ec2
comments: []
---
<p>Una forma de obtener la ip local o la ip pública de un servidor EC2 de AWS Amazon es desde la consola Web. Però como lo hacemos si necesitamos obtener estas IP para configurar los servicios que se ejecutan en el servidor?</p>
<p>Para obtener la ip local o pública desde dentro del servidor lo podemos hacer mediante una llamada http des de un script.</p>
<p>Para obtener la ip local:</p>
<p><code lang="bash"><br />
curl http://169.254.169.254/latest/meta-data/local-ipv4<br />
</code></p>
<p>Para obtener la ip pública:</p>
<p><code lang="bash"><br />
curl http://169.254.169.254/latest/meta-data/public-ipv4<br />
</code></p>
