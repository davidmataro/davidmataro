---
layout: post
status: publish
published: true
title: Como guardar la ip real del cliente con Varnish
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 407
wordpress_url: http://www.davidmataro.com/?p=407
date: !binary |-
  MjAxMi0wNy0xOCAxMToxNToxMiArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wNy0xOCAwOToxNToxMiArMDAwMA==
tags:
- sysadmin
- varnish cache
- nginx
comments: []
---
<p><a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> es un acelerador de aplicaciones Web.  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> normalmente se pone delante del servidor web para guardar las páginas web en memoria cache y servirlas al cliente de forma muy rápida. De modo que el servidor web sólo recibe peticiones de  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>Que el servidor web sólo reciba peticiones de  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> hace que por defecto en los logs del servidor web nse o guarde la IP real del cliente que se conecta, sino que sólo se guarda la IP del  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>En caso de utilizar un servicio de estadísticas local o en caso de necesidad de debug las conexiones al servidor web, es necesario que este registre en el log la IP real del cliente además de la del  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a>.</p>
<p>Para guardar la IP del cliente en ellog del  servidor web, es necesario configurar en el formato del log que registre la cabecera http X-Forwarded-For. La cabecera X-Forwarded-For la envía  <a title="Varnish Cache" href="https://www.varnish-cache.org/" target="_blank">Varnish</a> al servidor Web.</p>
<p>Ejemplo de configuración en un servidor <a title="Nginx web server" href="http://nginx.org/" target="_blank">nginx</a>:</p>
<p><code lang="bash"><br />
log_format main '$remote_addr - $remote_user [$time_local] '<br />
'"$request" $status $body_bytes_sent "$http_referer" '<br />
'"$http_user_agent" "$http_x_forwarded_for"' ;<br />
access_log /var/log/nginx/access.log main;<br />
</code></p>
