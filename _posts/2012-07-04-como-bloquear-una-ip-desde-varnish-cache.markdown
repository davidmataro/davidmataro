---
layout: post
status: publish
published: true
title: Como bloquear una IP desde Varnish Cache
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 374
wordpress_url: http://www.davidmataro.com/?p=374
date: !binary |-
  MjAxMi0wNy0wNCAxNTo1NToyMCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0wNCAxMzo1NToyMCArMDAwMA==
tags:
- sysadmin
- varnish cache
comments: []
---
<p>Hoy me he encontrado con un ataque de fuerza bruta para acceder a la administración de un Wordpress. El ataque estaba enviando repetidas peticiones POST a /wp-login para así acceder a la adinistración de Wordpess. </p>
<p>Como el Wordpress està bajo el acelerador de aplicaciones web <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish Cache</a>, para bloquear el ataque se ha tenido que configurar en <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish Cache</a> el bloqueo.</p>
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
<p>donde XXX.XXX.XXX.XXX es la IP que se desea bloquear.</p>
<p>De esta manera, el servidor responde con un "403 forbidden" a lad peticiones del cliente.</p>
