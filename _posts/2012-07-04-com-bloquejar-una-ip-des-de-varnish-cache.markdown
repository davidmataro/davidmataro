---
layout: post
status: publish
published: true
title: Com bloquejar una IP des de Varnish Cache
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 368
wordpress_url: http://www.davidmataro.com/?p=368
date: !binary |-
  MjAxMi0wNy0wNCAxNTo1MDoxMSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0wNCAxMzo1MDoxMSArMDAwMA==
tags:
- sysadmin
- varnish cache
comments: []
---
<p>Avui m'he trobat amb un atac de força bruta per accedir a la administració d'un Wordpress. L'atacant estava enviant repetidament peticions POST a /wp-login per tal d'accedir a la administració.</p>
<p>Com el Wordpress en questió està sota l'accelerador d'aplicacions web <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish Cache</a>, per bloquejar l'atac ha calgut feta una petita configuració a <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish Cache</a>.</p>
<p>vi /etc/varnish/default.conf</p>
<p><code lang="bash" width="558"><br />
# Forbidden IP ACL<br />
acl forbidden {<br />
"XXX.XXX.XXX.XXX"/32;<br />
}<br />
...<br />
# This function is used when a request is send by a HTTP client (Browser)<br />
sub vcl_recv {<br />
# Block the forbidden IP addresse<br />
if (client.ip ~ forbidden) {<br />
error 403 "Forbidden";<br />
}<br />
</code></p>
<p>on XXX.XXX.XXX.XXX es la IP que es vol bloquejar.</p>
<p>D'aquesta manera el servidor respon amb un "403 forbidden" a la petició del client.</p>
