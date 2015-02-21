---
layout: post
status: publish
published: true
title: Com guardar la ip real del client amb Varnish
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 405
wordpress_url: http://www.davidmataro.com/?p=405
date: !binary |-
  MjAxMi0wNy0xOCAxMTowOToyOSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xOCAwOTowOToyOSArMDAwMA==
tags:
- sysadmin
- varnish cache
- nginx
comments: []
---
<p><a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> és un accelerador d'aplicacions Web. <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> normalment es posa davant del servidor web per guardar les pàgines web en memòria cache i servir-les al client de manera molt ràpida. De manera que el servidor web sols rep peticions de <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>Que servidor web sols rebi peticions de <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> fa que per defecte en els logs del servidor web no guardi la IP real del client que es connecta, sinó que sols es guarda la IP del <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>En cas que utilitzem un servei d'estadístiques local o en cas de necessitat de debugar les connexions al servidor web, es necessari que aquest registri la IP real del client a més de la del <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>Per guardar la IP del client en el servidor web, cal configurar en el format del log que registri la capçalera http X-Forwarded-For. La capçalera X-Forwarded-For la envia <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> al servidor Web.</p>
<p>Per exemple de configuració en un servidor <a title="Nginx web server" href="http://nginx.org/" target="_blank">nginx</a>:</p>
<p><code lang="bash"><br />
log_format main '$remote_addr - $remote_user [$time_local] '<br />
'"$request" $status $body_bytes_sent "$http_referer" '<br />
'"$http_user_agent" "$http_x_forwarded_for"' ;<br />
access_log /var/log/nginx/access.log main;<br />
</code></p>
