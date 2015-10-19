---
layout: post
status: publish
published: true
title: HTTP Archive (har)
author:
  display_name: davidmataro
  login: admin
  email: jo@davidmataro.com
  url: http://www.davidmataro.com
author_login: admin
author_email: jo@davidmataro.com
author_url: http://www.davidmataro.com
wordpress_id: 468
wordpress_url: http://www.davidmataro.com/?p=468
date: !binary |-
  MjAxMi0wOC0zMCAyMzozMDoxMSArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wOC0zMCAyMTozMDoxMSArMDAwMA==
tags:
- wpo
- tiempo de carga
- http archive
- har
comments: []
---
<p>Para de analizar los tiempos de carga de una página web hay utilidades como PageSpeed ​​de Google o YSlow de Yahoo que instalados en Chrome o Firefox permiten ver los tiempos de carga de todos los elementos de una página. Para ver cómo evolucionan los cambios que vamos haciendo en la página y el impacto que tienen este en el tiempo de carga, es conveniente guardar un histórico de los análisis hechos.</p>
<p>Tanto Page Speed ​​como YSlow permiten guardar los análisis en formato HTTP Archive (HAR). HAR es una especificación para capturar la información de los tiempos de carga de una página web en un fichero en formato JSON.</p>
<p>Una vez guardado el archivo HAR se puede visualizar la información de forma gráfica mediante una herramienta online tipo <a title="HAR Viewer" href="http://www.softwareishard.com/har/viewer/" target="_blank">HAR Viewer</a> o descargar la versión opensource e instalar en un servidor local.</p>
<p>Una manera de ver de forma rápida un archivo HAR local se instale el visualizador hecho en ruby har (har Ruby gem)</p>
<p><code lang="bash"><br />
sudo gem install har<br />
</code></p>
<p>al ejecutarlo arranca un pequeño servidor local con har viewer y se abre el navegador para mostrar el análisis.</p>
<p><code lang="bash"><br />
har www.webbambu.com.har<br />
</code><a href="http://www.davidmataro.com/wp-content/uploads/2012/08/www.webbambu.com_.har_.png"><img src="http://www.davidmataro.com/wp-content/uploads/2012/08/www.webbambu.com_.har_-300x187.png" alt="" title="www.webbambu.com.har" width="300" height="187" class="aligncenter size-medium wp-image-465" /></a></p>
