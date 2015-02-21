---
layout: post
status: publish
published: true
title: Com obtenir la ip local i pública en un servidor EC2 de Amazon
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 357
wordpress_url: http://www.davidmataro.com/?p=357
date: !binary |-
  MjAxMi0wNi0wNiAyMzo0NzowMiArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNi0wNiAyMTo0NzowMiArMDAwMA==
tags:
- sysadmin
- aws
- ec2
comments: []
---
<p>Una manera d'optenir la ip local o la ip pública d'un servidor EC2 de AWS Amazon és des de la consola Web. Però com ho podem fer si necessitem obtenir aquestes IP per configurar els serveis que s'executen en el servidor?</p>
<p>Per obtenir al ip local o pública des de dins del servidor ho podem fer mitjançant una crida http des d'un script.</p>
<p>Per obtenir la IP local:</p>
<p><code lang="bash" width="558"><br />
curl http://169.254.169.254/latest/meta-data/local-ipv4<br />
</code></p>
<p>Per obtenir la IP pública:</p>
<p><code lang="bash" width="558"><br />
curl http://169.254.169.254/latest/meta-data/public-ipv4<br />
</code></p>
