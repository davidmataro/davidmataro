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
wordpress_id: 463
wordpress_url: http://www.davidmataro.com/?p=463
date: !binary |-
  MjAxMi0wOC0zMCAyMzoyMzo0NCArMDAwMA==
date_gmt: !binary |-
  MjAxMi0wOC0zMCAyMToyMzo0NCArMDAwMA==
tags:
- wpo
- http archive
- har
- pagespeed
- yslow
comments: []
---
<p>Alhora d'analitzar els temps de càrrega d'una pàgina web hi ha utilitats com PageSpeed de Google o YSlow de Yahoo que instal·lats a Chrome o Firefox permeten veure els temps de càrrega de tots els elements d'una pàgina. Per tal de veure com evolucionen els canvis que anem fent a la pàgina i l'impacte que tenen aquest en el temps de càrrega, es convenient guardar un històric dels anàlisis fets.</p>
<p>Tant Page Speed com YSlow permeten guardar els anàlisis en format HTTP Archive (HAR). HAR és una especificació per capturar la informació dels temps de càrrega d'una pàgina web en un fitxer en format JSON.</p>
<p>Un cop guardat el fitxer HAR es pot visualitzar la informació de forma gràfica mitjançant una eina online tipus <a title="HAR Viewer" href="http://www.softwareishard.com/har/viewer/" target="_blank">HAR Viewer</a> o descarregar la versió opensource i instal·lar-la en un servidor local.</p>
<p>Una manera de veure de forma ràpida un fitxer HAR local es instal·lant el visualitzador fet en ruby har (har Ruby gem)</p>
<p><code lang="bash"><br />
sudo gem install har<br />
</code></p>
<p>quant s'executa har s'arranca un petit servidor local amb har viewer i s'obre el navegador per mostrar l'anàlisi.</p>
<p><code lang="bash"><br />
har www.webbambu.com.har<br />
</code></p>
